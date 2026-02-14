
---

## Was sich durch deine neuen Anforderungen ändert

### Zielbild (Track 1)

* Backstage (Frontend+Backend) läuft **containerisiert** auf K8s
* **PostgreSQL** statt SQLite
* **OIDC SSO** (Keycloak oder Entra ID) + Gruppen/Rollen
* Secrets sauber (später: External Secrets/Vault)
* Scaffolder triggert **ADO Pipelines**:

  * `repo-provisioning`
  * `permission-management`
* Audit Events werden geschrieben (Log sink oder DB)

### Wichtig für deinen aktuellen Stand

* Dein `koffitapp` ist weiterhin wertvoll: wir nutzen ihn als **Codebasis**.
* Für K8s brauchen wir zusätzlich:

  * Docker Image bauen
  * Helm/Manifeste
  * Postgres Config
  * Auth/Secrets

---

# Test auf deinem Ubuntu: Ist Track 1 möglich?

## Schritt A — Voraussetzungen prüfen (1 Terminal)

```bash
lsb_release -a
docker --version
docker compose version
kubectl version --client
```

Wenn `kubectl` fehlt: kein Problem, installieren wir.

<img width="1173" height="538" alt="image" src="https://github.com/user-attachments/assets/75f856d1-4cc0-4071-9835-ea9705553916" />



## Schritt B — Lokales Kubernetes (empfohlen: kind)

```bash
kind version
```

Falls `kind` fehlt, installieren wir es.

<img width="1237" height="264" alt="image" src="https://github.com/user-attachments/assets/15079c65-2af9-4105-b4a2-2c450d900b73" />


## Schritt C — Mini-Cluster starten (kind)

```bash
kind create cluster --name idp
kubectl cluster-info
kubectl get nodes
```

## Schritt D — Ingress installieren (für Zugriff wie „idp.local“)

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
kubectl -n ingress-nginx rollout status deployment/ingress-nginx-controller
```

## Schritt E — PostgreSQL installieren (Helm)

```bash
helm version
```

Dann (Bitnami Postgres):

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
kubectl create ns backstage || true

helm install backstage-postgres bitnami/postgresql -n backstage \
  --set auth.username=backstage \
  --set auth.password=backstagepw \
  --set auth.database=backstage
```

Warten bis ready:

```bash
kubectl -n backstage get pods
```

## Schritt F — Backstage als Docker Image bauen (aus deinem `koffitapp`)

Im Repo:

```bash
cd ~/idp/koffitapp
```

Build (wir nehmen später ein „prod-Dockerfile“; für den Test reicht erstmal Standard-Build — wenn du schon ein Dockerfile hast, nutzen wir das):

```bash
docker build -t backstage-idp:dev .
kind load docker-image backstage-idp:dev --name idp
```

## Schritt G — Minimal Deploy (Backstage + Service + Ingress)

Dann deployen wir ein kleines Manifest (gebe ich dir fix & fertig), und testen:

```bash
kubectl -n backstage get svc,ingress,pods
curl -I http://localhost
```

✅ Wenn wir bis hierhin kommen, ist Track 1 **auf deinem Ubuntu definitiv möglich**.

---

# Wie ADO Pipelines in Backstage „reinpassen“ (dein Modell)

Du willst:

* Scaffolder Form → validiert Inputs → triggert Pipeline → Backstage zeigt Run-Link/Status

Das ist in Backstage sauber umsetzbar mit:

1. **Template.yaml** (Form, Parameter, Output Links)
2. **Scaffolder Actions**:

   * entweder “generic” via `fetch:plain` + `http:backstage`/custom action
   * oder eigenes kleines Backend-Plugin/Action: `ado:pipeline:run`
3. **Audit**:

   * Action schreibt JSON Event in Log sink (HTTP collector) oder DB

**Dein Contract (requestId, requestor, repoName, …)** ist dafür sehr gut geeignet.

---

## Was ich jetzt von dir brauche (damit ich “mit deinem Ubuntu teste”)

Schick mir bitte die Ausgabe dieser Befehle (copy/paste):

```bash
docker --version
kubectl version --client 2>/dev/null || echo "kubectl missing"
kind version 2>/dev/null || echo "kind missing"
helm version 2>/dev/null || echo "helm missing"
```
<img width="1502" height="412" alt="image" src="https://github.com/user-attachments/assets/3a02f5df-fdfe-4fa6-b80f-03268fdddb26" />


<img width="1502" height="412" alt="image" src="https://github.com/user-attachments/assets/59bd7884-b498-465b-99c0-07338956fc25" />

Dann sage ich dir **exakt**:

* was du installieren musst (falls etwas fehlt),
* und wir starten den **kind-POC** Schritt für Schritt.

---


Top — **dein Ubuntu ist dafür geeignet.** ✅
Du hast alles, was wir für den Track-1-Prototyp brauchen: Ubuntu 24.04, Docker, Compose, **kubectl**. Das reicht, um **lokal Kubernetes (kind)** zu starten und Backstage + PostgreSQL zu deployen.

Was noch fehlt (oder noch nicht geprüft): **kind** (Cluster) und **helm** (Postgres-Chart/Deploy komfortabel). Das testen/installieren wir jetzt.

---

## 0) Wichtig: wir zerstören dein `koffitapp` nicht

Wir bauen **separat** eine K8s-Umgebung, z. B. unter:

* `~/idp/koffitapp` (Code bleibt)
* `~/idp/k8s/firstidp` (Manifeste/Helm – neu)

---

# Schritt 1 — Prüfen ob `kind` und `helm` da sind

Bitte führe aus:

```bash
kind version 2>/dev/null || echo "kind missing"
helm version 2>/dev/null || echo "helm missing"
```

---

# Schritt 2 — Falls „missing“: installieren (Ubuntu 24.04)

### 2a) kind installieren

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.27.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
kind version
```
<img width="1520" height="377" alt="image" src="https://github.com/user-attachments/assets/ffb4f0d8-ded5-4239-8ff9-b5340a7a88d6" />

### 2b) helm installieren

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
helm version
```
<img width="1714" height="389" alt="image" src="https://github.com/user-attachments/assets/7afa5c46-ee79-4a35-95c9-0ad923bed08e" />

---

# Schritt 3 — Lokalen Kubernetes-Cluster erstellen (POC)

```bash
kind create cluster --name idp
kubectl cluster-info
kubectl get nodes
```

<img width="1727" height="799" alt="image" src="https://github.com/user-attachments/assets/285bf764-4b00-478e-8ed7-e2502d657af8" />

# Ingress-NGINX installieren

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
kubectl -n ingress-nginx rollout status deployment/ingress-nginx-controller
```
<img width="1791" height="862" alt="image" src="https://github.com/user-attachments/assets/e42ce0a1-4525-4d43-934d-106f3b2e7216" />

Wenn das läuft, ist die Machbarkeit **bewiesen**. Danach machen wir:

* Ingress-NGINX für Zugriff
* PostgreSQL (Helm)
* Backstage Image build + deploy
* Danach: **Scaffolder Action → ADO Pipeline trigger** nach deinem Contract

---

Sehr gut ✅ — **Ingress-NGINX ist erfolgreich ausgerollt**. Das heißt: dein Kubernetes-Cluster läuft bereits und Ingress ist bereit.

Jetzt machen wir kontrolliert weiter, damit du wirklich sicher weißt, dass Track-1 auf deinem Ubuntu funktioniert.

---

## Schritt 0 — Kurz prüfen, dass der Cluster wirklich OK ist

Bitte ausführen:

```bash
kubectl get nodes
kubectl -n ingress-nginx get pods
```
<img width="1233" height="268" alt="image" src="https://github.com/user-attachments/assets/e40c7fde-7468-4266-ad56-4a1851f16621" />

Controller `Running` ist → perfekt
<img width="1233" height="268" alt="image" src="https://github.com/user-attachments/assets/28f0e065-a32d-47c4-93ab-8fc7dfd5cae4" />

---

## Schritt 1 — Helm installieren (du brauchst es gleich für PostgreSQL)

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
helm version
```
<img width="1501" height="264" alt="image" src="https://github.com/user-attachments/assets/e169a459-e44a-41a1-a1a8-3c9d6f48926c" />

---

## Schritt 2 — Namespace erstellen

```bash
kubectl create namespace backstage || true
```
<img width="1500" height="306" alt="image" src="https://github.com/user-attachments/assets/b5394c50-d558-4e93-820f-8c0e5982e8ab" />

---

## Schritt 3 — PostgreSQL per Helm installieren (Backstage DB)

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update

helm install backstage-postgres bitnami/postgresql -n backstage \
  --set auth.username=backstage \
  --set auth.password=backstagepw \
  --set auth.database=backstage
```
<img width="1311" height="866" alt="image" src="https://github.com/user-attachments/assets/68c84b7c-887d-4b76-b6d6-7d3143ac9f1f" />
<img width="1724" height="917" alt="image" src="https://github.com/user-attachments/assets/76508da8-28fa-491d-a449-2888147b3354" />

Warten bis ready:

```bash
kubectl -n backstage get pods
```
<img width="1246" height="216" alt="image" src="https://github.com/user-attachments/assets/89d1a90b-e214-45c4-8809-69a61706cddc" />

---
# Prüfen, ob Postgres wirklich “Running” ist

```bash
kubectl -n backstage get pods
kubectl -n backstage get svc
```

<img width="1182" height="257" alt="image" src="https://github.com/user-attachments/assets/0b1d26f5-b5e9-411e-a12e-cdc7e6f5660c" />

## DB-Passwort aus Secret holen (für Backstage-Config)

```bash
export POSTGRES_PASSWORD=$(kubectl get secret -n backstage backstage-postgres-postgresql -o jsonpath="{.data.password}" | base64 -d)
echo "$POSTGRES_PASSWORD"

```
<img width="1262" height="473" alt="image" src="https://github.com/user-attachments/assets/1064ae09-4194-451e-b4b5-f53011a5a80b" />

## DB-Verbindung testen

```bash
kubectl run pg-client --rm -it --restart=Never -n backstage \
  --image=bitnami/postgresql:latest \
  --env="PGPASSWORD=$POSTGRES_PASSWORD" \
  --command -- psql --host backstage-postgres-postgresql -U backstage -d backstage -p 5432 -c "SELECT version();"

```

# DB-Test (sicher, 1 Zeile Output)

```bash
kubectl run pg-client --rm -i --restart=Never -n backstage \
  --image=bitnami/postgresql:latest \
  --env="PGPASSWORD=$POSTGRES_PASSWORD" \
  --command -- psql --host backstage-postgres-postgresql -U backstage -d backstage -p 5432 -tAc "SELECT version();"
```
<img width="1256" height="232" alt="image" src="https://github.com/user-attachments/assets/feb947ef-c745-46a2-b0d3-42a2ec861269" />




# Docker Image aus koffitapp bauen und in kind laden


```bash
cd ~/idp/koffitapp
docker build -t backstage-idp:dev .
kind load docker-image backstage-idp:dev --name idp

```


## Schritt 4 — Nächster Meilenstein (danach)

* Backstage als Docker Image bauen aus `~/idp/koffitapp`
* Image in kind laden
* Deployment + Service + Ingress
* Test im Browser



---

### Backstage Backend “Skeleton” bauen (für Docker)

```bash
cd ~/idp/koffitapp
ls
```

<img width="1424" height="494" alt="image" src="https://github.com/user-attachments/assets/4797333a-91d1-45c6-ba52-9596df22e009" />



```bash
cd ~/idp/koffitapp
yarn --version
node -v
yarn install
yarn build:backend

```

<img width="1707" height="1095" alt="image" src="https://github.com/user-attachments/assets/a1c18e8c-6906-4392-93e5-709f5c70dbb7" />

<img width="1457" height="1124" alt="image" src="https://github.com/user-attachments/assets/ae920150-68d4-4fdc-9c90-41ea7ba0e68a" />

<img width="1263" height="1119" alt="image" src="https://github.com/user-attachments/assets/bfc479cd-7b5f-4326-926c-29d61ae30991" />

<img width="1297" height="1024" alt="image" src="https://github.com/user-attachments/assets/658eb7a0-06cf-4a18-bf70-4226a0757826" />


# Lösung

```bash
cd ~/idp/koffitapp
nvm use 22
node -v
```

# Sauber aufräumen (Projekt bleibt erhalten)

```bash
cd ~/idp/koffitapp
rm -rf node_modules
rm -rf .yarn/install-state.gz .yarn/unplugged .yarn/build-state.yml 2>/dev/null || true
yarn cache clean

```
<img width="1146" height="292" alt="image" src="https://github.com/user-attachments/assets/64f3465d-c7b3-4471-8dac-133069d0a943" />

# Neu installieren + Backend bauen
```bash
cd ~/idp/koffitapp
yarn install
yarn build:backend

```
# Fehler  + Lösung


<img width="1167" height="492" alt="image" src="https://github.com/user-attachments/assets/30a99e05-3463-4b7f-8b81-41698cc1a6d6" />


# Dockerfile erstellen=>Lösung

```bash
cd ~/idp/koffitapp

cat > Dockerfile <<'EOF'
# ---- Build Stage ----
FROM node:22-bookworm-slim AS build

WORKDIR /app

# System deps für native builds (z.B. better-sqlite3)
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 make g++ git \
  && rm -rf /var/lib/apt/lists/*

# Yarn via Corepack aktivieren (Yarn 4)
RUN corepack enable

# Nur manifests zuerst (bessere Docker-Caches)
COPY package.json yarn.lock .yarnrc.yml backstage.json tsconfig.json ./
COPY .yarn ./.yarn

# Workspaces
COPY packages ./packages
COPY plugins ./plugins

# Install (Fallback falls --immutable bei dir scheitert)
RUN yarn install --immutable || yarn install

# Build Backend Bundle (zieht App mit ins dist workspace)
RUN yarn build:backend

# ---- Runtime Stage ----
FROM node:22-bookworm-slim

WORKDIR /app
ENV NODE_ENV=production

# Dist Workspace übernehmen (enthält gebündeltes Backend)
COPY --from=build /app/dist ./dist

# Konfigurationen übernehmen
COPY app-config.yaml ./app-config.yaml
COPY app-config.production.yaml ./app-config.production.yaml
COPY app-config.local.yaml ./app-config.local.yaml

EXPOSE 7007

# Start: gebündeltes Backend
CMD ["node", "dist/packages/backend"]
EOF

```

<img width="771" height="1064" alt="image" src="https://github.com/user-attachments/assets/bccf45bd-955b-438f-9783-1dbd12675046" />


# dockerignore erstellen

```bash
cd ~/idp/koffitapp

cat > .dockerignore <<'EOF'
node_modules
.yarn/cache
.yarn/unplugged
dist
.git
EOF


```

# Sofort prüfen, ob die Dateien da sind

```bash
cd ~/idp/koffitapp
ls -la Dockerfile .dockerignore
head -n 5 Dockerfile

```

<img width="857" height="462" alt="image" src="https://github.com/user-attachments/assets/cf4cb92b-88e1-4db1-9cf8-fe86cd7e8ac2" />



# Docker Image bauen

```bash
cd ~/idp/koffitapp
ls -la Dockerfile .dockerignore
head -n 5 Dockerfile
```

<img width="1692" height="802" alt="image" src="https://github.com/user-attachments/assets/2147265c-ff13-4b65-91d0-cb389b194d60" />



# Dockerfile korrekt schreiben

```bash
cd ~/idp/koffitapp

cat > Dockerfile <<'EOF'
# ------------------------------------------------------------
# Build Stage
# ------------------------------------------------------------
FROM node:22-bookworm-slim AS build
WORKDIR /app

# Native build tools (für better-sqlite3, isolated-vm, etc.)
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 make g++ git \
  && rm -rf /var/lib/apt/lists/*

# Yarn über Corepack (Yarn 4)
RUN corepack enable

# Zuerst nur Config/Manifests (Docker Cache)
COPY package.json yarn.lock .yarnrc.yml backstage.json tsconfig.json ./
COPY .yarn ./.yarn

# Workspaces
COPY packages ./packages
COPY plugins ./plugins

# Install + Build
RUN yarn install --immutable || yarn install
RUN yarn build:backend

# ------------------------------------------------------------
# Runtime Stage
# ------------------------------------------------------------
FROM node:22-bookworm-slim
WORKDIR /app
ENV NODE_ENV=production

# Für sqlite/better-sqlite3 im Runtime-Container sinnvoll
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
  && rm -rf /var/lib/apt/lists/*

# Minimal notwendige Dateien zum Starten:
# - node_modules (weil dein Setup node-modules Linker nutzt)
# - backend dist
# - package.json (hilft einigen Backstage Plugins/Resolvern)
COPY --from=build /app/package.json ./package.json
COPY --from=build /app/yarn.lock ./yarn.lock
COPY --from=build /app/.yarnrc.yml ./.yarnrc.yml
COPY --from=build /app/.yarn ./.yarn

COPY --from=build /app/node_modules ./node_modules

COPY --from=build /app/packages/backend/dist ./packages/backend/dist
COPY --from=build /app/packages/backend/package.json ./packages/backend/package.json

# Konfigurationsdateien
COPY app-config.yaml ./app-config.yaml
COPY app-config.production.yaml ./app-config.production.yaml
COPY app-config.local.yaml ./app-config.local.yaml

EXPOSE 7007

CMD ["node", "packages/backend/dist/index.js", "--config", "app-config.yaml"]
EOF



```

<img width="1697" height="790" alt="image" src="https://github.com/user-attachments/assets/84aa3074-8a67-4637-9c4d-ff61994f6c4a" />



# Dockerfile prüfen


```bash
cd ~/idp/koffitapp
tail -n 20 Dockerfile

```
*der dockerfile* :

```bash
EXPOSE 7007
CMD ["node", "packages/backend/dist/index.js", "--config", "app-config.yaml"]


```


<img width="973" height="531" alt="image" src="https://github.com/user-attachments/assets/289408e7-9e9f-4924-810c-b29fa2f1fcd6" />


# Container starten (lokaler Test)


```bash
docker run --rm -p 7007:7007 --name backstage-idp backstage-idp:dev
```

# Container starten (lokaler Test)

<img width="1167" height="421" alt="image" src="https://github.com/user-attachments/assets/28fa3510-d0b8-4198-bbf8-c1fdc208a5c3" />

```bash
docker run --rm -p 7007:7007 --name backstage-idp backstage-idp:dev
```

<img width="958" height="509" alt="image" src="https://github.com/user-attachments/assets/69b1080a-8530-4faf-b787-6f9b42465e3e" />




## Nebenbei: dein aktuelles `koffitapp` bleibt erhalten

Perfekt – jetzt ist es glasklar ✅

In deinem Image gibt es **kein** `index.js` / `index.cjs`.
Backstage `yarn build:backend` hat stattdessen **nur diese zwei Artefakte** erzeugt:

* `packages/backend/dist/skeleton.tar.gz`
* `packages/backend/dist/bundle.tar.gz`

Das ist **normal** beim Backstage “backend-bundle” Build. Man startet das Backend dann **nicht** mit `node packages/backend/dist/index.js`, sondern man **entpackt** diese Tarballs in einen Runtime-Ordner und startet daraus.

---

## Lösung (professionell): Dockerfile so anpassen, dass es aus `skeleton` + `bundle` ein lauffähiges Backend baut

### 1) Dockerfile öffnen

```bash
cd ~/idp/koffitapp
nano Dockerfile
```
<img width="958" height="1059" alt="image" src="https://github.com/user-attachments/assets/f4377740-46e4-4c41-998f-040039741c0e" />

### 2) Ersetze deinen Dockerfile komplett durch diesen (sauber & robust)


```dockerfile
# ---------- BUILD STAGE ----------
FROM node:22-bookworm-slim AS build

WORKDIR /app

# Build-Tools (node-gyp, native deps)
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 make g++ git ca-certificates \
  && rm -rf /var/lib/apt/lists/*

# Yarn / Corepack aktivieren
RUN corepack enable

# Monorepo-Dateien kopieren
COPY package.json yarn.lock .yarnrc.yml backstage.json tsconfig.json ./
COPY .yarn ./.yarn
COPY packages ./packages
COPY plugins ./plugins

# Dependencies + Backstage Backend Bundle bauen
RUN yarn install --immutable || yarn install
RUN yarn build:backend


# ---------- RUNTIME STAGE ----------
FROM node:22-bookworm-slim AS runtime

WORKDIR /app
ENV NODE_ENV=production

# tar braucht man zum Entpacken der Backstage-Artefakte
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates tar \
  && rm -rf /var/lib/apt/lists/*

# Wir bauen uns ein lauffähiges "dist workspace" unter /app
# 1) skeleton.tar.gz entpacken (enthält node_modules + package skeleton)
COPY --from=build /app/packages/backend/dist/skeleton.tar.gz /tmp/skeleton.tar.gz
RUN mkdir -p /app && tar -xzf /tmp/skeleton.tar.gz -C /app && rm /tmp/skeleton.tar.gz

# 2) bundle.tar.gz entpacken (enthält den gebündelten Backend-Code)
COPY --from=build /app/packages/backend/dist/bundle.tar.gz /tmp/bundle.tar.gz
RUN tar -xzf /tmp/bundle.tar.gz -C /app && rm /tmp/bundle.tar.gz

# Configs ins Image (für Dev ok; später besser per Volume/ConfigMap)
COPY app-config.yaml /app/app-config.yaml
COPY app-config.production.yaml /app/app-config.production.yaml
COPY app-config.local.yaml /app/app-config.local.yaml

EXPOSE 7007

# Backstage backend starten (aus dem entpackten bundle)
# Standard: /app/packages/backend oder /app/packages/backend/dist je nach Bundle.
# In den Backstage Bundles liegt der Einstieg normalerweise hier:
CMD ["node", "packages/backend", "--config", "app-config.yaml"]
```

Speichern: **CTRL+O**, Enter, **CTRL+X**

---

## 3) Neu bauen

```bash
cd ~/idp/koffitapp
docker build --no-cache -t backstage-idp:dev .
```

<img width="1694" height="880" alt="image" src="https://github.com/user-attachments/assets/96c905d9-457c-4040-a399-5690310ba21d" />

---
```bash

cd ~/idp/koffitapp

cat > Dockerfile <<'EOF'
# -------- build stage --------
FROM node:22-bookworm-slim AS build
WORKDIR /app

# Build-Tools (für native Node-Module) + git
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 make g++ git ca-certificates \
  && rm -rf /var/lib/apt/lists/*

# Yarn über Corepack
RUN corepack enable

# Nur die Dateien kopieren, die Yarn fürs Install braucht
COPY package.json yarn.lock .yarnrc.yml backstage.json tsconfig.json ./

# Yarn 4 nutzt .yarn/
COPY .yarn ./.yarn

# Workspace-Quellcode
COPY packages ./packages
COPY plugins ./plugins

# Install + Build
RUN yarn install --immutable || yarn install
RUN yarn build:backend

# Production node_modules für Runtime erzeugen (wichtig!)
RUN yarn workspaces focus --all --production

# -------- runtime stage --------
FROM node:22-bookworm-slim AS runtime
WORKDIR /app
ENV NODE_ENV=production

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
  && rm -rf /var/lib/apt/lists/*

# Runtime: node_modules + minimal nötige Dateien
COPY --from=build /app/node_modules ./node_modules
COPY --from=build /app/package.json ./package.json
COPY --from=build /app/yarn.lock ./yarn.lock

# Backstage Backend Build-Output (bei dir: dist enthält bundle.tar.gz + skeleton.tar.gz)
COPY --from=build /app/packages/backend/dist ./packages/backend/dist
COPY --from=build /app/packages/backend/package.json ./packages/backend/package.json

# Optional: Configs ins Image (für Start ohne Volume-Mount)
COPY app-config.yaml ./app-config.yaml
COPY app-config.production.yaml ./app-config.production.yaml
COPY app-config.local.yaml ./app-config.local.yaml

EXPOSE 7007

# Start: Backstage backend mit deiner Config
# (Backstage lädt standardmäßig app-config.yaml, aber wir geben sie explizit mit)
CMD ["node", "packages/backend", "--config", "app-config.yaml"]
EOF
```

# @backstage/backend-defaults testen

```bash
docker run --rm backstage-idp:dev sh -lc 'node -p "require.resolve(\"@backstage/backend-defaults\")"'
```

<img width="1465" height="168" alt="image" src="https://github.com/user-attachments/assets/6dbca1d1-c819-4706-b33b-06bf2dc13f91" />





<img width="1447" height="389" alt="image" src="https://github.com/user-attachments/assets/fb0b9b52-b0ad-4500-bb42-83bc659da513" />




# Neue Datei start-backend.sh erstellen (Copy & Paste)


```bash
cd ~/idp/koffitapp

cat > start-backend.sh <<'EOF'
#!/usr/bin/env sh
set -eu

R=/app/runtime
rm -rf "$R"
mkdir -p "$R"

echo "== Extract skeleton =="
tar -xzf /app/packages/backend/dist/skeleton.tar.gz -C "$R"

echo "== Extract bundle =="
tar -xzf /app/packages/backend/dist/bundle.tar.gz -C "$R"

echo "== Start Backstage backend =="
cd "$R"

# Damit Node die Dependencies in /app/node_modules findet
export NODE_PATH=/app/node_modules

exec node packages/backend --config /app/app-config.yaml
EOF

chmod +x start-backend.sh

```
<img width="763" height="666" alt="image" src="https://github.com/user-attachments/assets/a3f8f0cb-a232-4368-9394-7234f0722bc7" />


# Kontrolle

<img width="873" height="245" alt="image" src="https://github.com/user-attachments/assets/1d2d3f9b-545e-49d8-af81-28780dece816" />


<img width="1313" height="1036" alt="image" src="https://github.com/user-attachments/assets/9653b011-f4d8-464b-aad5-5a14b8fa62ba" />




## 4) Start testen

```bash
docker run --rm -p 7007:7007 --name backstage-idp backstage-idp:dev
```

Wenn das läuft, dann in einem **zweiten Terminal**:

```bash
curl -I http://localhost:7007/healthcheck || true
curl -I http://localhost:7007/api/catalog/entities?limit=1 || true
```

---

## Falls CMD noch nicht passt (Plan B – 30 Sekunden Debug)

Wenn es immer noch meckert, schauen wir schnell, wo der “Entrypoint” im Bundle liegt:

```bash
docker run --rm backstage-idp:dev sh -lc '
ls -la /app/packages/backend || true
ls -la /app/packages/backend/dist || true
find /app -maxdepth 4 -type f \( -name "index.js" -o -name "index.cjs" \) -print || true
cat /app/package.json 2>/dev/null | head -n 40 || true
'
```

Dann passe ich dir die **exakte** CMD-Zeile an (je nachdem ob es `packages/backend` oder `packages/backend/dist/index.cjs` ist).

---

Wenn du willst, mache ich als nächsten Schritt direkt den **Kubernetes Track 1** weiter: Container ins kind-cluster laden, Deployment + Service + Ingress + Postgres-Connection in `app-config.production.yaml` setzen.

