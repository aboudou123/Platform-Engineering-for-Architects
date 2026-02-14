IDP-MVP Architektur- und Umsetzungsdesign
Inhaltsverzeichnis
• 1) Architekturvarianten
  - 1a) Track 1 — Backstage (OSS) auf Kubernetes
  - 1b) Track 2 — Port (SaaS) + ADO Pipelines Runner
• 2) Pipeline-Design (ADO)
  - 2a) Pipeline repo-provisioning
  - 2b) Pipeline permission-management
• 3) Action-Contracts (Textschema)
  - 3a) Contract: Repo-Provisioning
  - 3b) Contract: Permission-Management
• 4) Portal-Integration
  - 4a) Backstage (Templates/Scaffolder – High Level)
  - 4b) Port (Entities/Actions – High Level)
• 5) Minimaler Infrastruktur-Plan je Track
  - Track 1 — Backstage (priorisiert, mit Abhängigkeiten)
  - Track 2 — Port (kurz)
• 6) Empfehlung + nächste 2 Wochen (konkrete To-dos)
  - Empfehlung für „jetzt“
  - Nächste 2 Wochen (Backlog-fähig)

1) Architekturvarianten
1a) Track 1 — Backstage (OSS) auf Kubernetes

Komponenten

• Backstage Frontend/Backend (Portal, Catalog, Scaffolder)
• PostgreSQL (Backstage DB)
• Ingress + TLS (NGINX/Traefik + cert-manager/PKI)
• OIDC SSO (Entra ID oder Keycloak) + Gruppen/Rollen
• Secrets (Vault/External Secrets/KMS)
• ADO Pipelines als Execution Engine (2 Pipelines)
• API-Zugänge: ADO REST, Artifactory REST, SonarQube REST
• Logging/Monitoring: zentral (Backstage + Pipeline-Runs) + Alerts
• Audit Sink: Log-System oder dedizierte DB/Table (optional, empfohlen)

Datenflüsse

• Repo-Provisioning

  1. User authentifiziert via OIDC → Backstage.
  2. Scaffolder-Form sammelt Inputs, validiert (naming, owner, policy).
  3. Backstage Backend triggert ADO Pipeline repo-provisioning (Run mit Parametern).
  4. Pipeline nutzt ADO/Artifactory/SonarQube APIs → erzeugt Repo/Files/Pipeline/Integrationen.
  5. Pipeline schreibt Audit-Event (Log sink) + gibt Run-URL zurück.
  6. Backstage zeigt Status-Link (ADO Run), optional Polling auf Run-Status.

• Permission Management

  1. User → Backstage Form (target scope, role, subject).
  2. Backstage triggert ADO Pipeline permission-management.
  3. Pipeline ändert ADO (und optional Artifactory) Berechtigungen.
  4. Audit-Event + Rücklink zum Run/Change-Details.

Vor-/Nachteile (jetzt)

• Pro: maximaler Compliance-/On-Prem-Fit; volle Souveränität; später erweiterbar (Catalog/Doku/mehr Use-Cases).
• Contra: Setup-/Betriebsaufwand (K8s, DB, Auth, Secrets, Upgrades); MVP dauert länger.

1b) Track 2 — Port (SaaS) + ADO Pipelines Runner

Komponenten

• Port SaaS (Entities, Actions, RBAC)
• ADO Pipelines + Agent/Scale Set (Runner in eurer Umgebung)
• Secrets (bestehende Secret-Lösung)
• API-Zugänge: ADO/Artifactory/SonarQube
• Audit Sink: Log-System (empfohlen), plus Port Action History

Datenflüsse

• Repo-Provisioning

  1. User startet Port Action (Form).
  2. Port validiert Felder + RBAC.
  3. Port triggert ADO Pipeline repo-provisioning (über Token/Integration).
  4. Pipeline führt aus, schreibt Audit-Event, liefert Run-Link.
  5. Port zeigt Action-Status + Link zum ADO Run (Polling/Webhook je nach Integration).

• Permission Management

  1. User startet Action „Grant/Change Access“.
  2. Port triggert Pipeline permission-management.
  3. Pipeline setzt Rechte, schreibt Audit, liefert Ergebnis.

Vor-/Nachteile (jetzt)

• Pro: schnellster Time-to-Value; kaum Portal-Betrieb; Actions/RBAC “out of the box”.
• Contra: SaaS/Compliance prüfen; langfristig Vendor-Abhängigkeit; weniger „Framework-Freiheit“.

2) Pipeline-Design (ADO)

> Prinzipien für beide Pipelines: idempotent, nachvollziehbar, auditiert, dry-run optional, klarer Exit-Code, Links zu Artefakten/Logs.

2a) Pipeline repo-provisioning

Inputs (Portal-Felder)

• requestId (string, UUID) required
• requestor (string, UPN) required
• adoOrg (string) required
• adoProject (string) required
• repoName (string, regex: ^[a-z0-9-]{3,40}$) required
• serviceName (string, same rule oder alias) required
• ownerTeam (string) required
• repoVisibility (enum: private|internal) optional (default: internal)
• templateRef (string: git ref/branch/tag) required
• ciTemplate (enum: dotnet|node|java|python|generic) required
• artifactoryRepoKey (string) required
• sonarProjectKey (string, regex: ^[a-zA-Z0-9:_-]{3,80}$) required
• sonarQualityGate (string) optional (default: org standard)
• enableDocsStub (bool) optional, default true
• dryRun (bool) optional, default false

Ablauf (Step-Liste)

Validate Inputs (regex, allowlist projects, naming collisions).
Check idempotency: existiert Repo? existiert Sonar-Projekt? existiert Pipeline?
Create/ensure Repo (ADO REST):
   - falls nicht existiert: Repo anlegen
Seed Repository:
   - Template aus templateRef holen (z. B. git clone template repo)
   - Platzhalter ersetzen (serviceName, sonar key, artifactory key)
   - Push in neues Repo
Create/ensure Pipeline (Azure Pipelines YAML):
   - Pipeline YAML aus ciTemplate wählen
   - Service connection refs setzen
   - Pipeline im Projekt registrieren (falls nötig)
Artifactory publish config:
   - Standard config (JFrog CLI/gradle/npm settings) in Repo
   - Optional: Artifactory repo existence check (REST)
SonarQube integration:
   - Sonar project anlegen/prüfen
   - Quality Gate zuweisen (org standard)
   - Token/Service connection referenzieren (nicht im Repo speichern)
Docs Stub:
   - README + Onboarding (lokal, build, deploy, ownership, links)
Write audit event (siehe unten)
Output: Repo URL, Pipeline URL, Sonar URL, Artifactory target, ADO run URL.

API-Anbindung

• ADO REST: Repo create, permissions (optional), pipeline registration, variables/groups.
• Artifactory REST: repo verify, permissions optional, publish endpoints.
• SonarQube REST: project create, quality gate assign.

Audit Writing

• JSON Event in zentrales Log (HTTP Event Collector / syslog / log forwarder) oder DB.
• Enthält requestId, requestor, action, target, diffSummary, status, adoRunUrl.

2b) Pipeline permission-management

Inputs

• requestId (UUID) required
• requestor (UPN) required
• adoOrg (string) required
• adoProject (string) required
• scopeType (enum: project|repo|pipeline|artifactory) required
• scopeId (string: repoId/pipelineId/projectId/artifactoryRepoKey) required
• principalType (enum: user|group|serviceprincipal) required
• principalId (string: AAD objectId/descriptor) required
• role (enum: reader|contributor|admin|custom) required
• operation (enum: grant|revoke|change) required
• approvalId (string) optional (if approval flow)
• dryRun (bool) optional

Ablauf

Validate: allowlist (welche Projekte/Scopes dürfen self-service?), role mapping check.
Resolve principal:
   - UPN → AAD objectId → ADO descriptor (falls nötig)
Fetch current permissions (baseline snapshot).
Apply change:
   - ADO Security API / Permission endpoints je scope
   - Optional: Artifactory permission targets (REST)
Post-check: permissions erneut lesen, diff erzeugen.
Write audit event: baseline + diff + approval metadata.
Output: changed entities, links, run URL.

Audit Writing

• Pflicht: before/after oder mindestens diff + principal + scope.
• Link zum ADO Run + (wenn möglich) zu den ADO audit logs / change records.

3) Action-Contracts (Textschema)
3a) Contract: Repo-Provisioning

``yaml
action: repo-provisioning
required:
  requestId: UUID
  requestor: "String (UPN)"
  adoOrg: String
  adoProject: "String (allowlist)"
  repoName: "String (^[a-z0-9-]{3,40}$, unique in project)"
  ownerTeam: "String (must exist in team registry)"
  templateRef: "String (approved refs only)"
  ciTemplate: "Enum [dotnet,node,java,python,generic]"
  artifactoryRepoKey: "String (must exist OR auto-create flag allowed)"
  sonarProjectKey: "String (unique, regex validated)"
optional:
  sonarQualityGate: "String (default org standard)"
  enableDocsStub: "Boolean (default true)"
  repoVisibility: "Enum [private,internal] (default internal)"
  dryRun: "Boolean (default false)"

validation:
  - "Project allowlist / tenant guardrails"
  - "Naming + uniqueness checks"
  - "TemplateRef must match approved list"
  - "requestor must be authenticated + authorized (RBAC)"

successResponse:
  status: SUCCESS
  message: "Repository provisioned"
  links:
    repoUrl: string
    pipelineUrl: string
    sonarUrl: string
    adoRunUrl: string
  audit:
    auditEventId: string
    timestamp: string

errorResponse:
  status: "FAILED | REJECTED"
  message: "human readable"
  details:
    errorCode: string
    failingStep: string
    correlationId: string
  links:
    adoRunUrl: "string (if started)"
    logsUrl: string
`

3b) Contract: Permission-Management

`yaml
action: permission-management
required:
  requestId: UUID
  requestor: "String (UPN)"
  adoOrg: String
  adoProject: "String (allowlist)"
  scopeType: "Enum [project,repo,pipeline,artifactory]"
  scopeId: String
  principalType: "Enum [user,group,serviceprincipal]"
  principalId: "String"
  role: "Enum [reader,contributor,admin,custom]"
  operation: "Enum [grant,revoke,change]"
optional:
  approvalId: String
  dryRun: Boolean

validation:
  - "Scope allowlist (which scopes are self-service)"
  - "Role mapping allowed per scope"
  - "Separation of duties (e.g., cannot grant admin to self)"
  - "If approval required → must include approvalId"

successResponse:
  status: SUCCESS
  message: "Permissions updated"
  changes:
    summary: "before/after summary OR diff"
  links:
    adoRunUrl: string
    targetUrl: string
  audit:
    auditEventId: string
    timestamp: string

errorResponse:
  status: "FAILED | REJECTED"
  message: string
  errorCode: string
  failingStep: string
  correlationId: string
  links:
    adoRunUrl: "string (if started)"
    logsUrl: string
`

4) Portal-Integration
4a) Backstage (Templates/Scaffolder – High Level)

Struktur

• Template 1: repo-provisioning-template
  - parameters (Form)
  - steps:
    1. validate (regex + policy checks)
    2. trigger ADO pipeline (custom action / backend plugin)
    3. emit links + register component in Catalog
• Template 2: permission-management-template
  - parameters
  - steps:
    1. validate (RBAC + SoD)
    2. trigger ADO pipeline
    3. show result links

Trigger & Status

• Trigger: Backstage Backend ruft ADO Pipeline Run API auf (service connection/PAT).
• Status: simplest: Link zum ADO Run + optional Polling (Backstage backend fragt Run-Status ab).
• Audit: Backstage schreibt zusätzlich ein Event (request metadata) → Log sink.

4b) Port (Entities/Actions – High Level)

Entities

• Service / Application
• Repository
• Pipeline
• Artifact
• SonarProject
• AccessRequest (optional zur Nachvollziehbarkeit)

Actions

• Action „Create Repo + CI + Quality“
• Action „Grant/Change Access“

Trigger & Status

• Trigger: Port Action startet ADO Pipeline Run.
• Status: Port zeigt Action-Run Status + Link zu ADO Run; je nach Integration Polling/Webhook.

5) Minimaler Infrastruktur-Plan je Track
Track 1 — Backstage (priorisiert, mit Abhängigkeiten)
K8s Cluster bereitstellen (Namespaces, RBAC, NetworkPolicies)
Ingress + TLS (Ingress Controller, cert-manager/PKI)
OIDC/SSO (Entra ID/Keycloak App, Gruppen-Mapping)
PostgreSQL (DB, Backups optional, Credentials via Secrets)
Secrets Management (Vault/External Secrets; Rotationskonzept)
Backstage Deployment (Helm/Kustomize), Basiskonfig (Catalog, Auth)
CI/CD (ArgoCD/Flux oder ADO Pipeline) + Image Build
Logging/Monitoring (Dashboards: availability, error rate; Alerts)
ADO Integration (Service connection/PAT, pipeline trigger action)
Audit Sink (Log pipeline oder DB table) + Standard Event Schema

Track 2 — Port (kurz)
• Secrets festlegen: ADO token/connection, Artifactory token, Sonar token (in bestehender Secret-Lösung)
• ADO Service Connections: least privilege; getrennt pro Pipeline (repo vs perms)
• Network: outbound vom Runner zu ADO/Artifactory/Sonar; ggf. Port callbacks erlauben (falls genutzt)
• Port Setup: Entities + RBAC + Actions + Mapping auf Pipelines
• Audit: zentraler Log sink + Port Action History als zusätzlicher Nachweis

6) Empfehlung + nächste 2 Wochen (konkrete To-dos)
Empfehlung für „jetzt“

Für eine Masterarbeit/MVP mit maximaler Geschwindigkeit: Track 2 (Port) starten, weil ihr ohne Portal-Betrieb schnell zwei echte Self-Service-Flows liefern könnt und die Bewertung (Time-to-Value, Prozessqualität, Auditierbarkeit) früher möglich ist.  
Parallel legt ihr die Architektur so an, dass die Execution-Schicht (ADO Pipelines + Contracts + Audit) identisch auch unter Backstage funktioniert – damit bleibt Backstage später ein kontrollierbarer, souveräner Ausbaupfad.

Nächste 2 Wochen (Backlog-fähig)

Woche 1

• Action-Contracts finalisieren (Repo + Permission) inkl. Validierungsregeln & SoD  
• ADO Service Principals/Connections erstellen (least privilege, getrennt pro Use Case)  
• Audit Event Schema festlegen + Log sink anbinden (ein Endpoint/Collector)  
• Skeleton-Pipelines anlegen (Parameter, Stages, DryRun, Output)  

Woche 2

• repo-provisioning: Repo create + template seed + pipeline YAML + Sonar project + Artifactory config  
• permission-management: principal resolve + permission read/apply + diff + audit write  
• Port: Entities minimal + zwei Actions + Mapping auf Pipelines + Status links  
• Observability: Dashboard „Automation Runs“ (failures, duration, top errors) + 2 Alerts  

Wenn du mir sagst, ob ihr Entra ID nutzt und ob ADO Server oder ADO Services die Quelle ist, kann ich die Inputs/Rollenauflösung (principalId`/descriptor) und die least-privilege Rollen für die Service Connections direkt präzise als Tickettexte formulieren.