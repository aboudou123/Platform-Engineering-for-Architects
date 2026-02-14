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


---


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

---

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

---

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

---

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

---

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

---

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

Wenn du mir sagst, **ob Keycloak bereits existiert** (oder neu auf AKS soll), und ob ihr **Private DNS Zone** in Azure nutzt, kann ich den Netzwerk-/Ingress-Teil als **exakte Tickettexte** formulieren (inkl. AKS annotations für internal LB und einer sauberen Namenskonvention für `backstage.dev.eu1`).






