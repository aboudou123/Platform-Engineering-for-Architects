
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

### Bitte jetzt posten

Schick mir die Ausgabe von:

1. `kubectl get nodes`
2. `helm version` (nach Installation)
3. `kubectl -n backstage get pods` (nach Postgres install)

Dann gehen wir direkt zum Backstage-Deploy über.











## Nebenbei: dein aktuelles `koffitapp` bleibt erhalten

Du brauchst nichts zu löschen.
Wenn du später einen „neuen Namen“ für das K8s-Setup willst (z. B. `kuka-first-idp`), machen wir das als **separaten Ordner/Repo** mit Helm/Manifests, aber die Codebasis kann weiterhin `koffitapp` sein.

Wenn du mir die 4 Version-Outputs gibst, starten wir direkt mit dem Machbarkeits-Test.
