# Interne Entwicklerplattform (IDP) & Platform Engineering

## Inhaltsverzeichnis

- [Zentrale Forschungsfrage](#zentrale-forschungsfrage)
- [Forschungsfrage 1 – Konzepte, Prinzipien und Muster des Platform Engineering](#forschungsfrage-1--konzepte-prinzipien-und-muster-des-platform-engineering)
- [Forschungsfrage 2 – Developer Experience: Definition, Faktoren & Metriken](#forschungsfrage-2--developer-experience-definition-faktoren--metriken)
- [Forschungsfrage 3 – Herausforderungen & Defizite im Status quo](#forschungsfrage-3--herausforderungen--defizite-im-status-quo)
- [Forschungsfrage 4 – Zielkonflikte zwischen Standardisierung, Sicherheit, Compliance & Flexibilität](#forschungsfrage-4--zielkonflikte-zwischen-standardisierung-sicherheit-compliance--flexibilität)
- [Forschungsfrage 5 – Konzeptionelles & architektonisches Zielbild einer IDP](#forschungsfrage-5--konzeptionelles--architektonisches-zielbild-einer-idp)

---

## Zentrale Forschungsfrage

**Wie können moderne Plattform-Engineering-Ansätze zur Konzeption einer Internen Entwicklerplattform (IDP) beitragen, die die Developer Experience verbessert und gleichzeitig Standardisierung, Sicherheit und Compliance mit der notwendigen Flexibilität für heterogene Entwicklungsteams in Einklang bringt?**

### Folie 1 – Antwort auf die zentrale Forschungsfrage (Übersicht)

- **Plattform als Produkt**
  - Dediziertes Plattform-Team, das Entwickler als Kunden versteht  
  - Kontinuierliches Einholen von Feedback und Messung der Developer Experience

- **Self-Service und Automatisierung**
  - Standardisierte, automatisierte Provisionierung von Infrastruktur, CI/CD, Umgebungen  
  - Reduktion manueller Tickets und Wartezeiten

- **Golden Paths & Templates**
  - Vordefinierte, sichere Standardwege für typische Anwendungen  
  - Hohe Standardisierung und Sicherheit, ohne freie Wahl völlig zu verbieten

- **Eingebaute Security & Compliance (Shift Left)**
  - Policy as Code, Security-Scans, Audit-Logging direkt in Pipelines integriert  
  - Entwickler müssen Compliance nicht manuell organisieren – sie kommt über die Plattform

- **Klare Architektur mit Guardrails**
  - Einheitliche Basis-Services (Logging, Monitoring, Auth), erweiterbar über APIs  
  - Teams können innerhalb sicherer Leitplanken eigene Technologien ergänzen

**Kernaussage**  
Moderne Platform-Engineering-Ansätze ermöglichen eine IDP, die Developer Experience stark verbessert, indem sie Komplexität versteckt, Sicherheit standardisiert und kontrollierte Flexibilität durch Guardrails statt harter Verbote bietet.

---

## Forschungsfrage 1 – Konzepte, Prinzipien und Muster des Platform Engineering

**Frage:**  
*Welche Konzepte, Prinzipien und architektonischen Muster des Platform Engineering werden in der wissenschaftlichen Literatur und in industriellen Best Practices zur Gestaltung Interner Entwicklerplattformen beschrieben?*

### Folie 2 – Zentrale Konzepte & Prinzipien

- **Platform as a Product**
  - Plattform-Team mit Produktverantwortung, Roadmap und KPIs  
  - Fokus auf Nutzer: Entwickler sind primäre Zielgruppe

- **Self-Service & Automatisierung**
  - Self-Service-Portal oder API für:
    - Projekt-/Repo-Anlage  
    - CI/CD-Setups  
    - Umgebungen & Datenbanken
  - Hoher Automatisierungsgrad mit Infrastructure as Code & GitOps

- **Golden Paths & Standard-Blueprints**
  - Vordefinierte, getestete Standardwege:
    - z. B. „Standard-Webservice“, „Event-basierter Service“, „Datenpipeline“
  - Enthalten:
    - Build-, Test-, Deploy-Templates  
    - Security-Scans, Logging, Monitoring „out of the box“

- **You-build-it-you-run-it-Unterstützung**
  - IDP liefert alle Bausteine, damit Teams ihre Services selbst betreiben können  
  - Observability, Alerting, Runbooks als Standard

### Folie 3 – Architekturmuster & Best Practices

- **Typische Architekturmuster**
  - Mehrschichtige Architektur:
    - Infrastruktur-Layer (Cloud, Kubernetes, Netzwerk)  
    - Plattform-Layer (CI/CD, Observability, Security, Service-Katalog)  
    - Applikations-Layer (Fachbereichs-Services)
  - API-first & plugin-fähiges Developer-Portal

- **Best Practices aus der Industrie**
  - Dediziertes Plattform-Team, das mit Dev-Teams co-kreiert  
  - Policy as Code für Security & Compliance (z. B. OPA, Kyverno)  
  - Standardisierte Repository-Struktur & Templates  
    (z. B. über Cookiecutter, Backstage-Templates)
  - Enge Integration von:
    - CI/CD  
    - Container-Orchestrierung (z. B. Kubernetes)  
    - Observability (z. B. Prometheus, Grafana, OpenTelemetry)

**Kurzantwort F1**  
Moderne Platform-Engineering-Ansätze beschreiben produktorientierte, Self-Service-fähige Plattformen, die mit Golden Paths, hoher Automatisierung und klarer Schichtenarchitektur arbeiten, um IDPs nutzerzentriert, sicher und effizient zu gestalten.

---

## Forschungsfrage 2 – Developer Experience: Definition, Faktoren & Metriken

**Frage:**  
*Wie wird Developer Experience im Kontext moderner Softwareentwicklung definiert, und welche Faktoren sowie Metriken eignen sich zu ihrer Bewertung innerhalb einer Internen Entwicklerplattform?*

### Folie 4 – Definition & Faktoren von Developer Experience

- **Definition von Developer Experience (DX)**  
  Developer Experience ist die Gesamtheit der Erfahrungen, die Entwickler mit Tools, Prozessen, Plattformen und der Organisation machen, um Software über den gesamten Lebenszyklus hinweg zu entwickeln, zu testen, zu deployen und zu betreiben.

- **Wesentliche Faktoren in einer IDP**
  - **Einfachheit & Usability**
    - Klarer, verständlicher Service-Katalog  
    - Gute UX im Portal, saubere CLI-/API-Oberflächen
  - **Produktivität & Flow**
    - Schnelle Builds, kurze Feedback-Loops, automatische Tests  
    - Wenig Kontextwechsel zwischen Tools
  - **Autonomie**
    - Self-Service für Umgebungen, Deployments, Secrets, Datenbanken
  - **Transparenz**
    - Einfache Einsicht in Logs, Metriken, Pipelines, Kosten
  - **Support**
    - Gute Dokumentation, Beispiele, Supportkanäle, Schulungen

### Folie 5 – Metriken zur Bewertung von DX in einer IDP

- **Quantitative Metriken**
  - DORA-Kennzahlen:
    - Deployment-Frequenz  
    - Lead Time for Changes  
    - Change Failure Rate  
    - Mean Time to Recovery (MTTR)
  - Plattform-spezifische Kennzahlen:
    - Zeit bis zum ersten erfolgreichen Deployment auf der IDP  
    - Dauer typischer Workflows (z. B. neues Projekt → produktiver Betrieb)  
    - Anteil der Services, die Golden Paths/Templates nutzen  
    - Anzahl manueller Schritte in Deployments vs. automatisierte Schritte

- **Qualitative Metriken**
  - Regelmäßige DX-Surveys (z. B. vierteljährlich)  
  - Developer Net Promoter Score (DevNPS)  
  - Umfragen zur wahrgenommenen:
    - Komplexität der Plattform  
    - Autonomie  
    - Zufriedenheit mit Dokumentation & Support

**Kurzantwort F2**  
DX im Kontext einer IDP beschreibt, wie effizient, angenehm und autonom Entwickler mit der Plattform arbeiten können. Sie wird durch Faktoren wie Usability, Flow, Autonomie und Transparenz geprägt und lässt sich über DORA-Metriken, Plattform-Kennzahlen und regelmäßige Entwickler-Umfragen messen.

---

## Forschungsfrage 3 – Herausforderungen & Defizite im Status quo

**Frage:**  
*Welche Herausforderungen und Defizite bestehen im aktuellen Status quo der Entwicklungs- und Bereitstellungsprozesse in Bezug auf die Developer Experience?*

### Folie 6 – Technische & Prozess-Herausforderungen

- **Tool-Wildwuchs & Inhomogenität**
  - Unterschiedliche CI/CD-Tools, Monitoring-Lösungen, Deployment-Verfahren  
  - Keine einheitlichen Standards, jede Anwendung „tickt anders“

- **Manuelle Prozesse & Tickets**
  - Umgebungen und Ressourcen werden über Tickets bei Ops angefragt  
  - Lange Wartezeiten, Medienbrüche, hohes Fehlerpotenzial

- **Fehlende Automatisierung**
  - Viele manuelle Schritte in Build-, Test- und Deployment-Prozessen  
  - Hohe kognitive Last, da Entwickler Details der Infrastruktur kennen müssen

- **Geringe Transparenz**
  - Unklare Sicht auf Deployments, Logs, Metriken  
  - Schwierige Fehlersuche, besonders in produktiven Umgebungen

### Folie 7 – Auswirkungen auf Developer Experience

- **Lange Time-to-First-Value**
  - Onboarding neuer Entwickler oder Projekte dauert Wochen statt Tage

- **Frustration & Kontextwechsel**
  - Entwickler müssen sich ständig mit nicht-wertschöpfenden Aufgaben beschäftigen:
    - Tickets nachverfolgen  
    - manuelle Konfigurationsarbeiten  
    - Abstimmungen über mehrere Teams hinweg

- **Unzuverlässigkeit & Unsicherheit**
  - Unterschiedliche Qualität von Pipelines und Deployments  
  - Unsicherheit, ob Security- und Compliance-Anforderungen wirklich erfüllt sind

- **Organisatorische Defizite**
  - Plattform oder Tooling wird als „Nebenprodukt“ gesehen, kein klares Ownership  
  - Kein klarer Kanal, um DX-Probleme sichtbar zu machen und zu priorisieren

**Kurzantwort F3**  
Der aktuelle Status quo ist oft geprägt von Tool-Wildwuchs, manuellen Prozessen, fehlender Automatisierung und geringer Transparenz. Das führt zu langsamen Onboardings, Frustration, hoher kognitiver Last und unsicherer Einhaltung von Standards, was die Developer Experience deutlich verschlechtert.

---

## Forschungsfrage 4 – Zielkonflikte zwischen Standardisierung, Sicherheit, Compliance & Flexibilität

**Frage:**  
*Welche Zielkonflikte bestehen zwischen Standardisierung, Sicherheits- und Compliance-Anforderungen sowie der notwendigen Flexibilität für unterschiedliche Entwicklungsteams?*

### Folie 8 – Konkrete Zielkonflikte

- **Standardisierung vs. Flexibilität**
  - Standardisierte Pipelines, Technologien und Architekturen  
    ↔ Bedarf der Teams, neue Technologien und Patterns auszuprobieren

- **Security & Compliance vs. Geschwindigkeit**
  - Strenge Prüfungen, manuelle Freigaben, Dokumentationspflichten  
    ↔ Wunsch nach schnellen, häufigen Releases

- **Zentrale Kontrolle vs. Team-Autonomie**
  - Zentrale Governance und Policies  
    ↔ Selbstbestimmte Wahl von Tools und Deployment-Strategien

- **Effizienz/Kosten vs. technologische Vielfalt**
  - Konzentration auf wenige, gut unterstützte Plattform-Services  
    ↔ „Best-of-Breed“-Ansätze einzelner Teams

### Folie 9 – Wie diese Zielkonflikte adressiert werden können

- **Guardrails statt Gates**
  - Vordefinierte Leitplanken:
    - Sicherheits-Policies  
    - Standard-Terraform-Module  
    - geprüfte Container-Images
  - Automatisierte Checks in CI/CD statt manueller Abnahmen

- **Stufenmodelle für Freiheiten**
  - Standardweg (Golden Path) mit maximaler Unterstützung  
  - „Escape Hatches“: kontrollierte Ausnahmen mit klaren Bedingungen

- **Risikobasierte Governance**
  - Strengere Kontrollen für kritische Systeme  
  - Leichtere, automatisierte Kontrollen für weniger kritische Anwendungen

- **Transparente Kataloge & Freigaben**
  - Liste zugelassener Technologien & Patterns (Tech-Radar)  
  - Klar definierter Prozess, um neue Technologien über die IDP zu integrieren

**Kurzantwort F4**  
Die wesentlichen Zielkonflikte liegen zwischen Standardisierung/Sicherheit und Flexibilität/Geschwindigkeit. Diese lassen sich durch Guardrails, automatisierte Policies, risikobasierte Governance und klar definierte Freiheitsgrade so lösen, dass sowohl Sicherheit als auch Innovation möglich bleiben.

---

## Forschungsfrage 5 – Konzeptionelles & architektonisches Zielbild einer IDP

**Frage:**  
*Wie kann ein konzeptionelles und architektonisches Zielbild einer Internen Entwicklerplattform gestaltet werden, das diesen Anforderungen gerecht wird?*

### Folie 10 – Konzeptionelles Zielbild

- **Zielsetzung der IDP**
  - End-to-End-Unterstützung des Software-Lebenszyklus:  
    Ideation → Development → Testing → Deployment → Betrieb  
  - Deutliche Verbesserung der DX bei gleichzeitiger Einhaltung von Standards

- **Zentrale Designprinzipien**
  - Plattform als Produkt mit dediziertem Plattform-Team  
  - Self-Service für alle wiederkehrenden Aufgaben:
    - Repositories  
    - Umgebungen  
    - Pipelines  
    - Datenbanken  
    - Secrets
  - „Secure by Default“ und „Compliance by Design“  
  - Modular, erweiterbar, API-first

- **Kernfunktionen**
  - Developer-Portal (Service-Katalog, Golden Paths, Dokumentation)  
  - Einheitliche CI/CD-Pipelines  
  - Observability-Plattform (Logging, Metrics, Tracing)  
  - Security-Services (IAM, Secrets-Management, Scans, Policies)  
  - Kostentransparenz (FinOps-Features)

### Folie 11 – Architektonisches Zielbild (High Level)

- **Experience Layer**
  - Developer-Portal als zentrale Einstiegsoberfläche  
  - Self-Service-Katalog für:
    - neue Services  
    - Datenbanken  
    - Umgebungen  
    - Pipelines

- **Platform Services Layer**
  - Standardisierte CI/CD-Engine mit integrierten Qualitäts- und Security-Gates  
  - Service Registry, API-Gateway, ggf. Service Mesh  
  - Observability-Stack, zentraler Logging- und Monitoring-Service  
  - Policy-as-Code-Engine für Security- und Compliance-Regeln

- **Infrastructure Layer**
  - Cloud-/Kubernetes-Infrastruktur als standardisierte Basis  
  - Infrastructure as Code für alle Ressourcen

- **Operating Model**
  - Plattform-Team mit Roadmap, SLAs und DX-Metriken  
  - Regelmäßige Feedback-Schleifen mit Entwicklungsteams  
  - Kontinuierliche Weiterentwicklung von Golden Paths & Templates

**Kurzantwort F5**  
Ein geeignetes Zielbild einer IDP besteht aus einem Developer-Portal (Experience Layer), einem Set standardisierter Platform-Services (CI/CD, Observability, Security, Service-Katalog) und einer automatisiert verwalteten Infrastruktur-Layer. Getragen wird es von einem Plattform-Team, das die Plattform als Produkt betreibt, DX misst und kontinuierlich verbessert.
