# IDP-MVP Architektur- und Umsetzungsdesign

## Inhaltsverzeichnis

- [1) Architekturvarianten](#1-architekturvarianten)
  - [1a) Track 1 — Backstage (OSS) auf Kubernetes](#1a-track-1--backstage-oss-auf-kubernetes)
  - [1b) Track 2 — Port (SaaS) + ADO Pipelines Runner](#1b-track-2--port-saas--ado-pipelines-runner)
- [2) Pipeline-Design (ADO)](#2-pipeline-design-ado)
  - [2a) Pipeline repo-provisioning](#2a-pipeline-repo-provisioning)
  - [2b) Pipeline permission-management](#2b-pipeline-permission-management)
- [3) Action-Contracts (Textschema)](#3-action-contracts-textschema)
  - [3a) Contract: Repo-Provisioning](#3a-contract-repo-provisioning)
  - [3b) Contract: Permission-Management](#3b-contract-permission-management)
- [4) Portal-Integration](#4-portal-integration)
  - [4a) Backstage (Templates/Scaffolder – High Level)](#4a-backstage-templatesscaffolder--high-level)
  - [4b) Port (Entities/Actions – High Level)](#4b-port-entitiesactions--high-level)
- [5) Minimaler Infrastruktur-Plan je Track](#5-minimaler-infrastruktur-plan-je-track)
  - [Track 1 — Backstage (priorisiert, mit Abhängigkeiten)](#track-1--backstage-priorisiert-mit-abhängigkeiten)
  - [Track 2 — Port (kurz)](#track-2--port-kurz)
- [6) Empfehlung + nächste 2 Wochen (konkrete To-dos)](#6-empfehlung--nächste-2-wochen-konkrete-to-dos)
  - [Empfehlung für „jetzt“](#empfehlung-für-jetzt)
  - [Nächste 2 Wochen (Backlog-fähig)](#nächste-2-wochen-backlog-fähig)

---

## 1) Architekturvarianten

### 1a) Track 1 — Backstage (OSS) auf Kubernetes

**Komponenten**

- Backstage Frontend/Backend (Portal, Catalog, Scaffolder)
- PostgreSQL (Backstage DB)
- Ingress + TLS (NGINX/Traefik + cert-manager/PKI)
- OIDC SSO (Entra ID oder Keycloak) + Gruppen/Rollen
- Secrets (Vault/External Secrets/KMS)
- ADO Pipelines als Execution Engine (2 Pipelines)
- API-Zugänge: ADO REST, Artifactory REST, SonarQube REST
- Logging/Monitoring: zentral (Backstage + Pipeline-Runs) + Alerts
- Audit Sink: Log-System oder dedizierte DB/Table (optional, empfohlen)

**Datenflüsse**

- **Repo-Provisioning**

  1. User authentifiziert via OIDC → Backstage.
  2. Scaffolder-Form sammelt Inputs, validiert (naming, owner, policy).
  3. Backstage Backend triggert ADO Pipeline `repo-provisioning` (Run mit Parametern).
  4. Pipeline nutzt ADO/Artifactory/SonarQube APIs → erzeugt Repo/Files/Pipeline/Integrationen.
  5. Pipeline schreibt Audit-Event (Log sink) + gibt Run-URL zurück.
  6. Backstage zeigt Status-Link (ADO Run), optional Polling auf Run-Status.

- **Permission Management**

  1. User → Backstage Form (target scope, role, subject).
  2. Backstage triggert ADO Pipeline `permission-management`.
  3. Pipeline ändert ADO (und optional Artifactory) Berechtigungen.
  4. Audit-Event + Rücklink zum Run/Change-Details.

**Vor-/Nachteile (jetzt)**

- **Pro:** maximaler Compliance-/On-Prem-Fit; volle Souveränität; später erweiterbar (Catalog/Doku/mehr Use-Cases).
- **Contra:** Setup-/Betriebsaufwand (K8s, DB, Auth, Secrets, Upgrades); MVP dauert länger.

---

### 1b) Track 2 — Port (SaaS) + ADO Pipelines Runner

**Komponenten**

- Port SaaS (Entities, Actions, RBAC)
- ADO Pipelines + Agent/Scale Set (Runner in eurer Umgebung)
- Secrets (bestehende Secret-Lösung)
- API-Zugänge: ADO/Artifactory/SonarQube
- Audit Sink: Log-System (empfohlen), plus Port Action History

**Datenflüsse**

- **Repo-Provisioning**

  1. User startet Port Action (Form).
  2. Port validiert Felder + RBAC.
  3. Port triggert ADO Pipeline `repo-provisioning` (über Token/Integration).
  4. Pipeline führt aus, schreibt Audit-Event, liefert Run-Link.
  5. Port zeigt Action-Status + Link zum ADO Run (Polling/Webhook je nach Integration).

- **Permission Management**

  1. User startet Action „Grant/Change Access“.
  2. Port triggert Pipeline `permission-management`.
  3. Pipeline setzt Rechte, schreibt Audit, liefert Ergebnis.

**Vor-/Nachteile (jetzt)**

- **Pro:** schnellster Time-to-Value; kaum Portal-Betrieb; Actions/RBAC “out of the box”.
- **Contra:** SaaS/Compliance prüfen; langfristig Vendor-Abhängigkeit; weniger „Framework-Freiheit“.

---

## 2) Pipeline-Design (ADO)

> Prinzipien für beide Pipelines: idempotent, nachvollziehbar, auditiert, dry-run optional, klarer Exit-Code, Links zu Artefakten/Logs.

### 2a) Pipeline repo-provisioning

**Inputs (Portal-Felder)**

- `requestId` (string, UUID) **required**
- `requestor` (string, UPN) **required**
- `adoOrg` (string) **required**
- `adoProject` (string) **required**
- `repoName` (string, regex: `^[a-z0-9-]{3,40}$`) **required**
- `serviceName` (string, same rule oder alias) **required**
- `ownerTeam` (string) **required**
- `repoVisibility` (enum: `private|internal`) optional (default: `internal`)
- `templateRef` (string: git ref/branch/tag) **required**
- `ciTemplate` (enum: `dotnet|node|java|python|generic`) **required**
- `artifactoryRepoKey` (string) **required**
- `sonarProjectKey` (string, regex: `^[a-zA-Z0-9:_-]{3,80}$`) **required**
- `sonarQualityGate` (string) optional (default: org standard)
- `enableDocsStub` (bool) optional, default `true`
- `dryRun` (bool) optional, default `false`

**Ablauf (Step-Liste)**

1. **Validate** Inputs (regex, allowlist projects, naming collisions).
2. **Check idempotency**: existiert Repo? existiert Sonar-Projekt? existiert Pipeline?
3. **Create/ensure Repo** (ADO REST):
   - falls nicht existiert: Repo anlegen
4. **Seed Repository**:
   - Template aus `templateRef` holen (z. B. `git clone` template repo)
   - Platzhalter ersetzen (serviceName, sonar key, artifactory key)
   - Push in neues Repo
5. **Create/ensure Pipeline** (Azure Pipelines YAML):
   - Pipeline YAML aus `ciTemplate` wählen
   - Service connection refs setzen
   - Pipeline im Projekt registrieren (falls nötig)
6. **Artifactory publish config**:
   - Standard config (JFrog CLI/gradle/npm settings) in Repo
   - Optional: Artifactory repo existence check (REST)
7. **SonarQube integration**:
   - Sonar project anlegen/prüfen
   - Quality Gate zuweisen (org standard)
   - Token/Service connection referenzieren (nicht im Repo speichern)
8. **Docs Stub**:
   - README + Onboarding (lokal, build, deploy, ownership, links)
9. **Write audit event** (siehe unten)
10. **Output**: Repo URL, Pipeline URL, Sonar URL, Artifactory target, ADO run URL.

**API-Anbindung**

- ADO REST: Repo create, permissions (optional), pipeline registration, variables/groups.
- Artifactory REST: repo verify, permissions optional, publish endpoints.
- SonarQube REST: project create, quality gate assign.

**Audit Writing**

- JSON Event in zentrales Log (HTTP Event Collector / syslog / log forwarder) oder DB.
- Enthält `requestId`, `requestor`, `action`, `target`, `diffSummary`, `status`, `adoRunUrl`.

---

### 2b) Pipeline permission-management

**Inputs**

- `requestId` (UUID) **required**
- `requestor` (UPN) **required**
- `adoOrg` (string) **required**
- `adoProject` (string) **required**
- `scopeType` (enum: `project|repo|pipeline|artifactory`) **required**
- `scopeId` (string: repoId/pipelineId/projectId/artifactoryRepoKey) **required**
- `principalType` (enum: `user|group|serviceprincipal`) **required**
- `principalId` (string: AAD objectId/descriptor) **required**
- `role` (enum: `reader|contributor|admin|custom`) **required**
- `operation` (enum: `grant|revoke|change`) **required**
- `approvalId` (string) optional (if approval flow)
- `dryRun` (bool) optional

**Ablauf**

1. **Validate**: allowlist (welche Projekte/Scopes dürfen self-service?), role mapping check.
2. **Resolve principal**:
   - UPN → AAD objectId → ADO descriptor (falls nötig)
3. **Fetch current permissions** (baseline snapshot).
4. **Apply change**:
   - ADO Security API / Permission endpoints je scope
   - Optional: Artifactory permission targets (REST)
5. **Post-check**: permissions erneut lesen, diff erzeugen.
6. **Write audit event**: baseline + diff + approval metadata.
7. **Output**: changed entities, links, run URL.

**Audit Writing**

- Pflicht: `before`/`after` oder mindestens `diff` + `principal` + `scope`.
- Link zum ADO Run + (wenn möglich) zu den ADO audit logs / change records.

---

## 3) Action-Contracts (Textschema)

### 3a) Contract: Repo-Provisioning

```yaml
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
```


=======================================


=======================================



## 1) Architekturvariante (Backstage private auf AKS, ohne Entra)

### Komponenten

* **AKS (private access)**
* **Namespace `idp`**
* **Backstage (Frontend+Backend)** als Deployment
* **PostgreSQL (Managed Azure Database for PostgreSQL)** *(empfohlen, stabil & wenig Ops)*
* **Private Ingress**: NGINX Ingress **internal** (Private Load Balancer) oder interner App Gateway
* **TLS intern**: Unternehmens-PKI (Root/Intermediate) oder cert-manager mit internem Issuer
* **OIDC Provider**: **Keycloak** *(oder ein vorhandener interner IdP)*

  * Gruppen/Rollen: `idp-admin`, `platform`, `dev`
* **Secrets**: Key Vault + CSI Driver / External Secrets Operator
* **Execution Engine**: **Azure DevOps Pipelines** (2 Pipelines)
* **Audit/Logs**: zentraler Log-Sink (z. B. Log Analytics / ELK / Splunk) + Links zu ADO Runs

### Datenfluss (beide Use Cases, identisch)

1. User → Backstage (über internes Netz/VPN) → Login via Keycloak (OIDC)
2. Backstage Scaffolder Form → Validierung → Trigger ADO Pipeline Run (REST API)
3. Pipeline führt aus (ADO/Artifactory/Sonar APIs) → schreibt Audit Event → liefert Links zurück
4. Backstage zeigt Ergebnis: Repo/Pipeline/Sonar/Artifactory Links + ADO Run URL (Status)



## 2) Minimaler Infrastruktur-Plan (Track 1, priorisiert)

### 2.1 Netzwerk & Private Exposure (Blocker zuerst)

1. **Private Access bestätigen**

   * Zugriff nur via VPN/Corp-Netz (kein Public Endpoint).
2. **Private Ingress bereitstellen**

   * NGINX Ingress mit **internal Load Balancer** (Azure annotation) *oder* App Gateway Ingress (AGIC), intern.
3. **Interne DNS-Route**

   * z. B. `backstage.dev.<corp>.local` → private LB IP.

### 2.2 Identity (ohne Entra → Keycloak)

4. **Keycloak bereitstellen** *(kann auch extern existieren; falls nicht: in AKS)*

   * Realm `platform`
   * Client `backstage` (OIDC)
   * Gruppen: `idp-admin`, `platform`, `dev`
5. **RBAC-Mapping definieren**

   * `idp-admin` → Backstage Admin
   * `platform` → Templates/Actions verwalten
   * `dev` → Actions ausführen

### 2.3 Datenbank & Secrets

6. **Azure Database for PostgreSQL** bereitstellen

   * private connectivity (Private Endpoint) wenn möglich
7. **Secrets Management**

   * Key Vault + CSI Secrets Store (oder External Secrets)
   * Secrets: `POSTGRES_*`, `KEYCLOAK_CLIENT_SECRET`, `ADO_TOKEN`, `ARTIFACTORY_TOKEN`, `SONAR_TOKEN`

### 2.4 Backstage Deployment & Ops-Baseline

8. **Backstage deployen** (Helm/Kustomize)

   * Catalog aktivieren
   * Scaffolder aktivieren
   * Auth OIDC via Keycloak
9. **Logging/Monitoring MVP**

   * Container logs zentral
   * Alerts: Pod crashloop, 5xx rate, Ingress down


## 3) ADO Pipelines (MVP-Design, kurz & umsetzbar)

### 3.1 Pipeline `repo-provisioning` (idempotent)

**Inputs**

* `requestId` (UUID), `requestorUpn`
* `adoProject`, `repoName`, `serviceName`, `ownerTeam`
* `ciTemplate` (enum), `templateRef`
* `artifactoryRepoKey`, `sonarProjectKey`, optional `qualityGate`
* `dryRun` (bool)

**Steps**

1. Validate (naming, allowlist projects, collisions)
2. Ensure Repo exists (create if not)
3. Seed template → replace placeholders → push
4. Ensure pipeline YAML exists & pipeline configured
5. Ensure Sonar project + assign Quality Gate
6. Ensure Artifactory publish config present
7. Write audit event (JSON) + output links

### 3.2 Pipeline `permission-management` (idempotent)

**Inputs**

* `requestId`, `requestorUpn`
* `adoProject`, `scopeType` (project/repo/pipeline), `scopeId`
* `principalType` (user/group/sp), `principalId`
* `role` (reader/contributor/admin), `operation` (grant/revoke/change)
* `dryRun`

**Steps**

1. Validate (allowlist scopes, SoD: kein Admin für себя)
2. Resolve principal → ADO descriptor
3. Read current permissions (baseline)
4. Apply change
5. Read after state → diff
6. Write audit event + output

### Audit Event (für beide)

* Pflicht: `requestId`, `requestor`, `action`, `targets`, `timestamp`, `result`, `adoRunUrl`
* Für Permissions: `before/after` oder `diffSummary`


## 4) Action-Contracts (Textschema, knapp)

### Repo-Provisioning Contract

* Pflicht: `adoProject, repoName, ownerTeam, ciTemplate, templateRef, artifactoryRepoKey, sonarProjectKey`
* Validierung: naming regex, project allowlist, uniqueness, template allowlist
* Success: `repoUrl, pipelineUrl, sonarUrl, adoRunUrl, auditEventId`
* Error: `errorCode, failingStep, correlationId, adoRunUrl(if any)`

### Permission-Management Contract

* Pflicht: `scopeType, scopeId, principalType, principalId, role, operation`
* Validierung: SoD, allowed roles per scope, approval optional
* Success: `diffSummary, targetUrl, adoRunUrl, auditEventId`
* Error: `errorCode, failingStep, correlationId`



## 5) Portal-Integration (Backstage, private)

### Scaffolder Templates (High Level)

* Template `repo-provisioning`

  * parameters → validate → trigger ADO pipeline → output links → (optional) register entity in Catalog
* Template `permission-management`

  * parameters → validate (SoD) → trigger pipeline → output diff + run link

### Trigger & Status

* Trigger: Backstage Backend → ADO Runs API (PAT/Service Connection)
* Status: MVP-einfach **nur Link** zum ADO Run + optional Polling (später)
* Ergebnis: User sieht immer einen **korrelierbaren Run** + Audit Event



## 6) Empfehlung „jetzt“ + konkrete To-Dos für die nächsten 2 Wochen

### Empfehlung

Da ihr **bereits AKS habt**, Backstage **private** betreiben wollt und **kein Entra** nutzt, ist der sauberste Weg:
**Backstage MVP auf AKS + Keycloak OIDC + ADO Pipelines als Runner.**
Das bleibt compliance-fähig, intern kontrollierbar und exakt kompatibel mit eurem Infra-Only-Ansatz.

### Nächste 2 Wochen (konkret als Backlog)

**Woche 1**

1. Private Ingress (internal LB) + interne DNS
2. Keycloak bereitstellen/konfigurieren (Realm, Client, Gruppen)
3. Postgres (Managed) + Secrets in Key Vault
4. Skeleton ADO Pipelines anlegen + Parameter/Validation + DryRun

**Woche 2**
5) Backstage deployen (Auth + DB + Scaffolder)
6) Backstage → ADO Trigger Action implementieren/konfigurieren
7) `repo-provisioning` fertigstellen (Repo + Seed + Sonar + Artifactory + Audit)
8) `permission-management` fertigstellen (Resolve + apply + diff + Audit)
9) Logging/Alerting MVP (Backstage up + Pipeline failure/duration)
---


===========================================
# 19.0.2026
==========================================


Unten ist ein **konkreter IDP-Architekturvorschlag**, der die im Interviewmaterial sichtbar gewordenen Probleme **systematisch adressiert**, ohne die bestehende Toolchain zu ersetzen. 

---

## 1) Architekturprinzip: Portal-Layer + Execution-Layer + Governance-Layer

Die Interviews zeigen kein „Tool-Defizit“, sondern Defizite in **Standardisierung, Wiederverwendbarkeit, Transparenz und governance-naher Routinearbeit** (insb. Berechtigungen) sowie hohen Aufwand beim **Pipeline-Troubleshooting** und fehlenden **Guidelines**.
Daraus ergibt sich als geeigneter Architekturgrundsatz:

1. **Portal-Layer (Backstage)**: einheitlicher Einstiegspunkt („Frontdoor“) für Standardpfade, Dokumentation, Ownership und Self-Service-Auslösung.
2. **Execution-Layer (Azure DevOps Pipelines / IaC / Skripte)**: führt die fachliche Automatisierung aus; bleibt „Source of Execution“.
3. **Governance-Layer (Policies, RBAC, Audit, Approvals)**: erzwingt Leitplanken technisch und stellt Nachvollziehbarkeit sicher.

Diese Trennung adressiert direkt die im Korpus sichtbaren Spannungen aus **teamspezifischer CI/CD-Praxis**, hoher Varianz und kognitiver Last.

---

## 2) Zielarchitektur (komponentenbasiert)

### 2.1 Portal-Layer: Backstage als „Single Frontdoor“

**Komponenten**

* **Backstage (Frontend + Backend)** als zentrales Portal
* **Software Catalog**: Services/Repos/Pipelines/Ownership/Links
* **Scaffolder / Templates („Golden Paths“)**
* **TechDocs (Documentation-as-Code)** als strukturierte Wissensbasis

**Warum passt das zum Interview?**
Im Material werden wiederkehrend **fehlende Guidelines/Best Practices**, der Bedarf nach **Wissensbasis/Informationen** sowie **Template-/Script-Uneinheitlichkeit** sichtbar.  Backstage ist genau der Baustein, der Standards, Dokumentation und Self-Service-Einstiegspunkte **konsolidieren** kann, ohne Azure DevOps, Artifactory oder Sonar zu ersetzen.

### 2.2 Execution-Layer: Standardisierte Automationsschnittstellen über Azure DevOps Pipelines

**Komponenten**

* Zwei „MVP-Runner“ als ADO Pipelines:

  * **repo-provisioning**
  * **permission-management**
* Gemeinsame **Pipeline-Library** (shared scripts/modules) für wiederverwendbare Schritte (ADO-API, Artifactory-API, SonarQube-API, Scans)
* Optional: **Terraform Azure DevOps Provider** innerhalb dieser Pipelines für reproduzierbare ADO-Konfiguration (Repos/Projects/Permissions), wo sinnvoll

**Warum passt das zum Interview?**
Mehrere Aussagen beschreiben Pipeline-Komplexität und Troubleshooting als belastend („pipelines tricky“, Fehleranalyse, Abhängigkeiten zwischen Pipelines).  Eine standardisierte Execution-Schicht reduziert Varianz, indem sie „One way to do it“ (Golden Path) als reproduzierbare Pipeline etabliert, statt ad-hoc YAML-Varianten pro Team.

Zudem wird explizit **Repo-Erstellung/Einrichtung** und **Permission Management** als Automations-/Self-Service-Bedarf genannt.  Genau diese beiden Use-Cases werden im Execution-Layer als klare, versionierte „Platform-Capabilities“ umgesetzt.

### 2.3 Governance-Layer: RBAC, Policies, Audit & nachvollziehbare Änderungen

**Komponenten**

* **Backstage Permission Framework / RBAC** (wer darf welche Actions ausführen)
* **SoD-Regeln (Separation of Duties)**: z. B. keine Selbstvergabe von Admin-Rechten
* **Approval-Gate** (optional, aber empfehlenswert für privilegierte Changes)
* **Audit Trail**: pro Action ein strukturiertes Audit-Event (wer/was/wann + Links zum Run + ggf. Diff)

**Warum passt das zum Interview?**
Die Daten zeigen governance-nahe Routinearbeit als Belastung (insb. Berechtigungen) und den Bedarf an Wartbarkeit/Nachvollziehbarkeit.  Wenn Permissions heute „teuer“ sind, ist die Ursache häufig nicht nur fehlende Automation, sondern fehlende **kontrollierte** Automation (RBAC/Audit/Approval). Genau hier setzt der Governance-Layer an: Self-Service wird möglich, ohne Governance zu verlieren.

### 2.4 Observability-Layer: Status, Transparenz und Datenqualität

**Komponenten**

* Zentrales Logging/Monitoring für:

  * Backstage (Availability, Error Rate)
  * Pipeline Runs (Failure Rate, Duration, häufige Fehler)
* Strukturierte „Action Telemetry“: pro Request Korrelation (`requestId`) → Pipeline Run → Ergebnislinks
* Datenqualitätsfokus: „junk data“ wird als Problem erwähnt; daher braucht es definierte Events statt unstrukturierter Logs.

**Warum passt das zum Interview?**
Monitoring wird als uneinheitlich bzw. teils „basic“ beschrieben, und Datenqualität wird problematisiert.  Eine IDP-Architektur muss daher nicht nur „auslösen“, sondern auch **Status und Nachvollziehbarkeit** sauber liefern – sonst verlagert sich Troubleshooting nur an eine andere Stelle.

---

## 3) Konkrete „Golden Paths“ (direkt aus den Interviewproblemen abgeleitet)

### 3.1 Golden Path A: Repo-Provisioning (Standardisierung statt YAML-Wildwuchs)

**Portal (Backstage)**: Formular + Validierung + Start
**Execution (ADO Pipeline)** erzeugt:

* Repo in Azure DevOps + Standardstruktur
* Pipeline-Skeleton (vereinheitlichte CI/CD-Basis)
* Artifactory Publish Config (JFrog)
* SonarQube Projekt + Quality Gate
* optional: Black Duck/Compliance Schritt als Standard
* Doku-Stub (Onboarding, Build/Run/Deploy)

**Begründung durch Interviewdaten**

* Toolchain-Heterogenität und fehlende Guidelines/Best Practices sind wiederkehrend.
* Pipeline-Komplexität und Fehleranalyse belasten.
  Ein Golden Path reduziert Varianz, weil „das Standard-Setup“ technisch vorgegeben ist und nicht jedes Team neu „erfinden“ muss.

### 3.2 Golden Path B: Permission Management (governance-naher Routinepain)

**Portal (Backstage)**: Action „Grant/Change/Revoke Access“ (Scope/Role/Principal)
**Execution (ADO Pipeline)**:

* ADO Permission Änderungen (project/repo/pipeline)
* optional Artifactory Permission Targets
* Audit-Event + Diff/Before-After + Run Link

**Begründung durch Interviewdaten**
Permission Management wird explizit als Automations-/Self-Service-Bedarf und als Wartbarkeitsthema genannt.
Mit Audit/SoD wird der typische Zielkonflikt gelöst: Self-Service ohne Kontrollverlust.

---

## 4) Warum diese Architektur „die richtige“ ist (im Sinne des Materials)

### 4.1 Sie adressiert das Hauptproblem: Varianz + kognitive Last

CI/CD wird häufig teamspezifisch beschrieben; gleichzeitig werden Pipeline-Komplexität und Troubleshooting als belastend markiert.
Die Architektur reduziert Varianz, indem sie **Standardpfade** (Golden Paths) anbietet und die Ausführung in **wenigen, gut gepflegten Pipelines** bündelt.

### 4.2 Sie passt zur hybriden Realität

Workloads und Umgebungen erscheinen hybrid (Cloud/On-Premise).
Ein Portal-Layer ist hier sinnvoll, weil er Abhängigkeiten und heterogene Toolketten **abstrahiert**, ohne dass alle Entwickler Kubernetes direkt bedienen müssen (was im Korpus auch nicht durchgängig der Fall ist). 

### 4.3 Sie greift die konkret genannten Automationshebel auf

Repo-Einrichtung und Permission Management werden als Self-Service/Automationsthemen explizit genannt.
Das ist entscheidend: Die Architektur setzt nicht „irgendwo“ an, sondern an den im Material sichtbaren, wiederkehrenden Routinen.

### 4.4 Sie verbessert Transparenz dort, wo Monitoring/Datenqualität uneinheitlich sind

Monitoring wird teils als basic, teils als verbesserungswürdig beschrieben; Datenqualität wird problematisiert.
Durch Action-Events (requestId-Korrelation) und standardisierte Outputs (Links/Status) wird die Transparenz über Automationen erhöht, ohne in eine neue „Tool-Schicht ohne Sichtbarkeit“ zu laufen.

---

## 5) Erwartbare Effekte im Ist-Kontext (ohne „Roadmap“, nur Architekturwirkung)

* Reduktion der teamspezifischen Varianz durch Standardpfade (einheitliches Setup statt individuelle YAML-Interpretationen)
* Senkung kognitiver Last im Troubleshooting, weil Pipelines standardisiert und wiederverwendbar werden (statt „jede Pipeline anders“) 
* Entlastung governance-naher Routinen durch kontrollierte, auditierbare Automationen (Permissions)
* Verbesserte Transparenz über Status/Änderungen durch konsistente Links, Logs und Action-Events

---

Du hast recht — das war **kein echtes GIF**, sondern nur ein statisches Bild. Danke, dass du das klar ansprichst.

👉 Wichtig: Ich kann hier **keine echten animierten GIF-Dateien direkt erzeugen und senden**, sondern nur Bilder generieren.
Aber ich kann dir eine **ingenieurstaugliche Lösung** geben, mit der du in 2 Minuten ein echtes GIF bekommst — genau so, wie du es für deine Masterarbeit brauchst.

---

# ✅ Professionelle Lösung (empfohlen für Masterarbeit)

Ich erstelle dir **ein sauberes Animationskonzept + Frames**, die du direkt in ein GIF umwandeln kannst.

## 🎬 Animation (logisch korrekt für IDP)

Das GIF sollte **4 Schritte zeigen (Flow!)**:

### Frame 1 – User Interaction (Start)

* Developer → Backstage Portal
* „Request: Create Repo / Manage Permissions“

### Frame 2 – Portal Layer

* Backstage:

  * Form
  * Template
  * Validation
* Pfeil → Execution

### Frame 3 – Execution Layer (Kern!)

* ADO Pipeline läuft:

  * Repo wird erstellt
  * Pipeline wird generiert
  * Artifactory + Sonar integriert
* Terraform optional für ADO Setup

### Frame 4 – Governance + Observability

* RBAC / Approval
* Audit Log
* Monitoring + Status zurück an User

---

# ⚙️ Wie du daraus ein echtes GIF machst (2 Minuten)

## Option 1 – PowerPoint (beste für Uni)

1. Jede Phase = 1 Slide
2. „Morph“-Transition nutzen
3. Export → **Als GIF speichern**

👉 Ergebnis: **professionelles Architektur-GIF**

---

## Option 2 – Online Tool (noch schneller)

Gehe zu:

* [https://ezgif.com/maker](https://ezgif.com/maker)

Dann:

1. Lade 4 Bilder hoch (Frames)
2. Setze Delay: 800–1200 ms
3. „Make GIF“

---

## Option 3 – Draw.io / Miro (Engineering-Level)

* Diagramm erstellen
* States duplizieren
* Export als PNG-Serie
* → GIF

---

# 🔥 Wenn du willst (beste Option)

Ich kann dir jetzt direkt liefern:

✔ 4 **perfekt strukturierte Frames (Architektur-Level, sauber, Masterarbeit-ready)**
✔ exakt so aufgebaut, dass sie sofort als GIF funktionieren
✔ visuell wie ein echter Solution Architect Diagram

👉 Sag einfach:
**„mach mir die 4 Frames“**

Dann bekommst du eine **professionelle, animierbare IDP-Architektur**, die du 1:1 in deine Masterarbeit übernehmen kannst.

Alles klar — ich erstelle dir jetzt eine **durchgehend wissenschaftliche, kohärente und „aus deiner Perspektive“ formulierte Dokumentation**, die du direkt in deine Masterarbeit übernehmen kannst.

Ich beginne strukturiert. Aufgrund der Länge liefere ich dir **Teil 1 (Kapitel 1–6 + Beginn 7)** — sauber, professionell, ohne Fülltext.

---

# **1. Ziel und Nutzen eines Internal Developer Portals**

Im Rahmen dieser Arbeit verfolge ich das Ziel, einen funktionsfähigen Prototyp einer Internal Developer Platform (IDP) auf Basis von Backstage zu konzipieren und umzusetzen. Der Fokus liegt dabei nicht auf einer vollständigen Produktlösung, sondern auf einem realistischen Minimum Viable Product (MVP), das zentrale Self-Service-Funktionalitäten für Entwicklungsteams bereitstellt.

Ausgangspunkt der Implementierung sind die im Unternehmen identifizierten Herausforderungen, insbesondere hohe kognitive Last durch heterogene Toolchains, fehlende Standardisierung von CI/CD-Prozessen sowie ineffiziente, manuelle Abläufe im Bereich Berechtigungsmanagement und Repository-Provisionierung.

Ein Internal Developer Portal adressiert diese Probleme, indem es als zentrale Interaktionsschicht („Single Pane of Glass“) fungiert. Es bündelt Informationen, standardisiert Prozesse und ermöglicht es Entwicklerinnen und Entwicklern, wiederkehrende Aufgaben über Self-Service-Mechanismen auszuführen.

Im Kontext dieses Prototyps stehen insbesondere folgende Funktionen im Vordergrund:

* Erstellung neuer Repositories über standardisierte Templates
* Ausführung und Wiederholung von Build-Prozessen („Run/Retry Build“)
* Unterstützung bei Agent-bezogenen Problemen („Agent Recovery“)
* Bereitstellung eines zentralen Knowledge- und Troubleshooting-Hubs

Damit leistet das IDP einen wesentlichen Beitrag zur Reduktion operativer Reibung, zur Standardisierung von Entwicklungsprozessen sowie zur Verbesserung der Developer Experience (DX).

---

# **2. Einrichtung der lokalen Entwicklungsumgebung und erste Backstage-App**

Zur initialen Entwicklung des IDP-Prototyps habe ich zunächst eine isolierte lokale Umgebung auf einer virtuellen Maschine eingerichtet. Diese Entscheidung wurde bewusst getroffen, um eine kontrollierte und reproduzierbare Entwicklungsbasis zu schaffen, die unabhängig von produktiven Unternehmenssystemen betrieben werden kann.

Die Umgebung basiert auf Ubuntu 24.04 (WSL2) und umfasst folgende zentrale Komponenten:

* Node.js (Version 22, verwaltet über nvm)
* Yarn als Paketmanager
* Docker für Containerisierung
* Git für Versionsverwaltung

Nach erfolgreicher Einrichtung der Entwicklungsumgebung habe ich mittels der Backstage CLI eine erste Applikation erzeugt. Dieser Schritt dient dazu, ein initiales Verständnis für die Struktur und Funktionsweise von Backstage zu entwickeln.

Die erzeugte Anwendung konnte lokal gestartet werden und stellte die grundlegenden Module bereit:

* Software Catalog
* Scaffolder (Templates)
* TechDocs
* Administration

**Screenshot hier**

Die lokale Ausführung ermöglichte es mir, frühzeitig zentrale Konzepte wie Entitäten, Templates und Plugin-Integration praktisch zu erkunden.

---

# **3. Verständnis der Projektstruktur und Konfiguration**

Ein tiefgehendes Verständnis der Backstage-Projektstruktur ist essenziell für jede weiterführende Anpassung und Erweiterung.

Die generierte Anwendung folgt einer modularen Architektur mit klarer Trennung zwischen Frontend, Backend und Plugins:

* `packages/app` → Frontend (React-basierte UI)
* `packages/backend` → Backend-Services (APIs, Integrationen)
* Plugins → Erweiterungen für spezifische Funktionalitäten

Zentrale Konfigurationsdateien sind:

* `app-config.yaml`
* `app-config.local.yaml`

Diese definieren unter anderem:

* Integrationen (z. B. Azure DevOps)
* Authentifizierungsmechanismen
* Backend-Services
* Plugin-Konfigurationen

Die Konfiguration bildet die Grundlage für die spätere Integration in die Unternehmensumgebung sowie für die Anbindung externer Systeme.

---

# **4. Software-Templates und Scaffolder (Überblick)**

Ein zentrales Element des IDP ist der Backstage Scaffolder, der die Generierung neuer Softwarekomponenten über standardisierte Templates ermöglicht.

Software-Templates bestehen aus mehreren Komponenten:

* Metadaten (Beschreibung, Tags, Owner)
* Parameter (Benutzereingaben)
* Skelett (Dateivorlagen)
* Scaffolding-Schritte (Automatisierungslogik)

Der Scaffolder erlaubt es, wiederkehrende Prozesse – wie das Anlegen eines neuen Repositories inklusive CI/CD-Konfiguration – zu standardisieren und automatisiert auszuführen.

Dies adressiert direkt die im Interview identifizierte Problematik der inkonsistenten Pipeline-Konfigurationen und fehlenden Best Practices.

---

# **5. Template-Metadaten und Auffindbarkeit**

Die Metadaten eines Templates spielen eine entscheidende Rolle für dessen Auffindbarkeit und Nutzbarkeit innerhalb des Portals.

Ich habe besonderen Wert auf folgende Metadaten gelegt:

* Klarer Name und Beschreibung
* Tags (z. B. „backend“, „microservice“, „ci-cd“)
* Owner-Zuordnung
* Kategorien

Diese strukturierte Beschreibung ermöglicht es Entwicklern, relevante Templates schnell zu identifizieren und korrekt einzuordnen.

Darüber hinaus unterstützen konsistente Metadaten die Governance, indem sie Transparenz über verfügbare „Golden Paths“ schaffen.

---

# **6. Benutzereingaben und Parameterdefinition**

Die Parameterdefinition bildet die Schnittstelle zwischen Entwickler und Plattform.

Für das Repository-Provisioning-Template habe ich u. a. folgende Parameter definiert:

* Service Name
* Repository Name
* Programmiersprache
* CI/CD-Optionen
* Deployment-Ziel

Diese Parameter werden im Backstage-Frontend als Formular dargestellt und validiert.

Ziel war es, eine Balance zwischen:

* **Standardisierung** (vorgegebene Defaults)
* **Flexibilität** (konfigurierbare Optionen)

zu erreichen.

Dadurch wird sichergestellt, dass Entwickler nicht überfordert werden, gleichzeitig aber genügend Freiraum für unterschiedliche Anforderungen besteht.

---

# **7. Konzeption der IDP**

## **7.1 Zielsetzung und Designprinzipien**

Die Konzeption der IDP basiert auf der grundlegenden Zielsetzung, eine Plattform bereitzustellen, die Entwicklungsprozesse standardisiert, automatisiert und gleichzeitig flexibel genug bleibt, um heterogene Anforderungen abzubilden.

Dabei habe ich folgende Designprinzipien definiert:

* **Self-Service First**
* **Standardisierung vor Individualisierung**
* **Separation of Concerns (Portal vs. Execution)**
* **Security by Design**
* **Transparenz und Nachvollziehbarkeit**

Diese Prinzipien spiegeln direkt die im Interview identifizierten Problemfelder wider, insbesondere die fehlende Standardisierung, hohe Komplexität und mangelnde Transparenz.

---

## **7.2 Architektonisches Gesamtbild**

Die Architektur des entwickelten IDP-Prototyps folgt einem klaren Schichtenmodell:

1. **Portal Layer (Backstage)**
2. **Execution Layer (Azure DevOps Pipelines, Skripte, IaC)**
3. **Governance Layer (RBAC, Policies, Audit)**
4. **Observability Layer (Logging, Monitoring, Telemetrie)**

**Screenshot hier**

Das Portal fungiert dabei ausschließlich als Interaktionsschicht, während die eigentliche Ausführung der Prozesse in der bestehenden Toolchain erfolgt.

---

## **7.3 Zentrale Plattformkomponenten**

### **7.3.1 Developer Portal**

Backstage dient als zentrale Benutzeroberfläche, über die alle IDP-Funktionalitäten zugänglich sind.

### **7.3.2 Service Catalog und Ownership**

Der Software Catalog ermöglicht die zentrale Verwaltung von Services, inklusive Ownership und Metadaten.

### **7.3.3 Templates und Golden Paths**

Templates definieren standardisierte Entwicklungsprozesse und reduzieren Varianz.

### **7.3.4 CI/CD und GitOps Integration**

Azure DevOps Pipelines werden als zentrale Ausführungsinstanz genutzt.

### **7.3.5 Observability und Feedback-Loops**

Monitoring und Logging liefern Rückmeldungen über den Zustand der Plattform.

---

Unten ist ein **konkreter IDP-Architekturvorschlag**, der die im Interviewmaterial sichtbar gewordenen Probleme **systematisch adressiert**, ohne die bestehende Toolchain zu ersetzen. Die Begründung ist jeweils explizit an den im Korpus beschriebenen Pain Points ausgerichtet.

---

## 1) Architekturprinzip: Portal-Layer + Execution-Layer + Governance-Layer

Die Interviews zeigen kein „Tool-Defizit“, sondern Defizite in **Standardisierung, Wiederverwendbarkeit, Transparenz und governance-naher Routinearbeit** (insb. Berechtigungen) sowie hohen Aufwand beim **Pipeline-Troubleshooting** und fehlenden **Guidelines**.
Daraus ergibt sich als geeigneter Architekturgrundsatz:

1. **Portal-Layer (Backstage)**: einheitlicher Einstiegspunkt („Frontdoor“) für Standardpfade, Dokumentation, Ownership und Self-Service-Auslösung.
2. **Execution-Layer (Azure DevOps Pipelines / IaC / Skripte)**: führt die fachliche Automatisierung aus; bleibt „Source of Execution“.
3. **Governance-Layer (Policies, RBAC, Audit, Approvals)**: erzwingt Leitplanken technisch und stellt Nachvollziehbarkeit sicher.

Diese Trennung adressiert direkt die im Korpus sichtbaren Spannungen aus **teamspezifischer CI/CD-Praxis**, hoher Varianz und kognitiver Last.

---

## 2) Zielarchitektur (komponentenbasiert)

### 2.1 Portal-Layer: Backstage als „Single Frontdoor“

**Komponenten**

* **Backstage (Frontend + Backend)** als zentrales Portal
* **Software Catalog**: Services/Repos/Pipelines/Ownership/Links
* **Scaffolder / Templates („Golden Paths“)**
* **TechDocs (Documentation-as-Code)** als strukturierte Wissensbasis

**Warum passt das zum Interview?**
Im Material werden wiederkehrend **fehlende Guidelines/Best Practices**, der Bedarf nach **Wissensbasis/Informationen** sowie **Template-/Script-Uneinheitlichkeit** sichtbar.  Backstage ist genau der Baustein, der Standards, Dokumentation und Self-Service-Einstiegspunkte **konsolidieren** kann, ohne Azure DevOps, Artifactory oder Sonar zu ersetzen.

### 2.2 Execution-Layer: Standardisierte Automationsschnittstellen über Azure DevOps Pipelines

**Komponenten**

* Zwei „MVP-Runner“ als ADO Pipelines:

  * **repo-provisioning**
  * **permission-management**
* Gemeinsame **Pipeline-Library** (shared scripts/modules) für wiederverwendbare Schritte (ADO-API, Artifactory-API, SonarQube-API, Scans)
* Optional: **Terraform Azure DevOps Provider** innerhalb dieser Pipelines für reproduzierbare ADO-Konfiguration (Repos/Projects/Permissions), wo sinnvoll

**Warum passt das zum Interview?**
Mehrere Aussagen beschreiben Pipeline-Komplexität und Troubleshooting als belastend („pipelines tricky“, Fehleranalyse, Abhängigkeiten zwischen Pipelines).  Eine standardisierte Execution-Schicht reduziert Varianz, indem sie „One way to do it“ (Golden Path) als reproduzierbare Pipeline etabliert, statt ad-hoc YAML-Varianten pro Team.

Zudem wird explizit **Repo-Erstellung/Einrichtung** und **Permission Management** als Automations-/Self-Service-Bedarf genannt.  Genau diese beiden Use-Cases werden im Execution-Layer als klare, versionierte „Platform-Capabilities“ umgesetzt.

### 2.3 Governance-Layer: RBAC, Policies, Audit & nachvollziehbare Änderungen

**Komponenten**

* **Backstage Permission Framework / RBAC** (wer darf welche Actions ausführen)
* **SoD-Regeln (Separation of Duties)**: z. B. keine Selbstvergabe von Admin-Rechten
* **Approval-Gate** (optional, aber empfehlenswert für privilegierte Changes)
* **Audit Trail**: pro Action ein strukturiertes Audit-Event (wer/was/wann + Links zum Run + ggf. Diff)

**Warum passt das zum Interview?**
Die Daten zeigen governance-nahe Routinearbeit als Belastung (insb. Berechtigungen) und den Bedarf an Wartbarkeit/Nachvollziehbarkeit.  Wenn Permissions heute „teuer“ sind, ist die Ursache häufig nicht nur fehlende Automation, sondern fehlende **kontrollierte** Automation (RBAC/Audit/Approval). Genau hier setzt der Governance-Layer an: Self-Service wird möglich, ohne Governance zu verlieren.

### 2.4 Observability-Layer: Status, Transparenz und Datenqualität

**Komponenten**

* Zentrales Logging/Monitoring für:

  * Backstage (Availability, Error Rate)
  * Pipeline Runs (Failure Rate, Duration, häufige Fehler)
* Strukturierte „Action Telemetry“: pro Request Korrelation (`requestId`) → Pipeline Run → Ergebnislinks
* Datenqualitätsfokus: „junk data“ wird als Problem erwähnt; daher braucht es definierte Events statt unstrukturierter Logs.

**Warum passt das zum Interview?**
Monitoring wird als uneinheitlich bzw. teils „basic“ beschrieben, und Datenqualität wird problematisiert.  Eine IDP-Architektur muss daher nicht nur „auslösen“, sondern auch **Status und Nachvollziehbarkeit** sauber liefern – sonst verlagert sich Troubleshooting nur an eine andere Stelle.

---

## 3) Konkrete „Golden Paths“ (direkt aus den Interviewproblemen abgeleitet)

### 3.1 Golden Path A: Repo-Provisioning (Standardisierung statt YAML-Wildwuchs)

**Portal (Backstage)**: Formular + Validierung + Start
**Execution (ADO Pipeline)** erzeugt:

* Repo in Azure DevOps + Standardstruktur
* Pipeline-Skeleton (vereinheitlichte CI/CD-Basis)
* Artifactory Publish Config (JFrog)
* SonarQube Projekt + Quality Gate
* optional: Black Duck/Compliance Schritt als Standard
* Doku-Stub (Onboarding, Build/Run/Deploy)

**Begründung durch Interviewdaten**

* Toolchain-Heterogenität und fehlende Guidelines/Best Practices sind wiederkehrend.
* Pipeline-Komplexität und Fehleranalyse belasten.
  Ein Golden Path reduziert Varianz, weil „das Standard-Setup“ technisch vorgegeben ist und nicht jedes Team neu „erfinden“ muss.

### 3.2 Golden Path B: Permission Management (governance-naher Routinepain)

**Portal (Backstage)**: Action „Grant/Change/Revoke Access“ (Scope/Role/Principal)
**Execution (ADO Pipeline)**:

* ADO Permission Änderungen (project/repo/pipeline)
* optional Artifactory Permission Targets
* Audit-Event + Diff/Before-After + Run Link

**Begründung durch Interviewdaten**
Permission Management wird explizit als Automations-/Self-Service-Bedarf und als Wartbarkeitsthema genannt.
Mit Audit/SoD wird der typische Zielkonflikt gelöst: Self-Service ohne Kontrollverlust.

---

## 4) Warum diese Architektur „die richtige“ ist (im Sinne des Materials)

### 4.1 Sie adressiert das Hauptproblem: Varianz + kognitive Last

CI/CD wird häufig teamspezifisch beschrieben; gleichzeitig werden Pipeline-Komplexität und Troubleshooting als belastend markiert.
Die Architektur reduziert Varianz, indem sie **Standardpfade** (Golden Paths) anbietet und die Ausführung in **wenigen, gut gepflegten Pipelines** bündelt.

### 4.2 Sie passt zur hybriden Realität

Workloads und Umgebungen erscheinen hybrid (Cloud/On-Premise).
Ein Portal-Layer ist hier sinnvoll, weil er Abhängigkeiten und heterogene Toolketten **abstrahiert**, ohne dass alle Entwickler Kubernetes direkt bedienen müssen (was im Korpus auch nicht durchgängig der Fall ist). 

### 4.3 Sie greift die konkret genannten Automationshebel auf

Repo-Einrichtung und Permission Management werden als Self-Service/Automationsthemen explizit genannt.
Das ist entscheidend: Die Architektur setzt nicht „irgendwo“ an, sondern an den im Material sichtbaren, wiederkehrenden Routinen.

### 4.4 Sie verbessert Transparenz dort, wo Monitoring/Datenqualität uneinheitlich sind

Monitoring wird teils als basic, teils als verbesserungswürdig beschrieben; Datenqualität wird problematisiert.
Durch Action-Events (requestId-Korrelation) und standardisierte Outputs (Links/Status) wird die Transparenz über Automationen erhöht, ohne in eine neue „Tool-Schicht ohne Sichtbarkeit“ zu laufen.

---

## 5) Erwartbare Effekte im Ist-Kontext (ohne „Roadmap“, nur Architekturwirkung)

* Reduktion der teamspezifischen Varianz durch Standardpfade (einheitliches Setup statt individuelle YAML-Interpretationen)
* Senkung kognitiver Last im Troubleshooting, weil Pipelines standardisiert und wiederverwendbar werden (statt „jede Pipeline anders“) 
* Entlastung governance-naher Routinen durch kontrollierte, auditierbare Automationen (Permissions)
* Verbesserte Transparenz über Status/Änderungen durch konsistente Links, Logs und Action-Events

---



<img width="1536" height="1024" alt="Architekture" src="https://github.com/user-attachments/assets/bede4867-0f46-4868-86d1-4e97a7a6ebee" />


<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/fc3b8cd1-e067-4e3b-ac7f-2d9e02bb4e10" />

Wenn du möchtest, kann ich als nächstes (im gleichen Stil, weiterhin interviewbasiert) eine **kompakte Architekturtabelle** erstellen: *Interview-Pain Point → Architekturbaustein → Mechanismus → erwartete Wirkung* – ohne in Implementierungsanweisungen oder Roadmaps abzurutschen.

