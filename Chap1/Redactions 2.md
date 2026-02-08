

## 1. Begriffsdefinitionen

### Platform Engineering

In der empirischen Software-Engineering-Literatur wird „Platform Engineering“ nicht einheitlich als eigener, klar abgegrenzter Terminus für interne Entwicklerplattformen verwendet; stattdessen finden sich zwei belastbare wissenschaftliche Bezugslinien:

1. **Plattform als „Core Asset Base“ / Produktlinien-Plattform**
   In der Software-Produktlinienforschung bezeichnet eine *Plattform* (bzw. die Gesamtheit wiederverwendbarer Kernartefakte) die Grundlage, aus der mehrere Anwendungen/Produkte abgeleitet werden; *Platform Engineering* umfasst dabei die systematische Entwicklung und Evolution dieser Kernartefakte inkl. Variabilitätsmanagement und organisatorischer Einbettung.
   Referenz: Klaus Pohl; Günter Böckle; Frank J. van der Linden (2005), *Software Product Line Engineering: Foundations, Principles and Techniques*, Springer. ([Springer][1])

2. **Plattformteam als organisatorische Einheit zur Bereitstellung standardisierter Delivery-Fähigkeiten**
   Im Kontext Continuous Delivery wird „Platform Team“ als organisatorisches Strukturmuster beschrieben, das Infrastruktur- und Delivery-Fähigkeiten als wiederverwendbare, interne Dienste bündelt und anderen Teams zugänglich macht.
   Referenz: Leonardo Leite; Fabio Kon; Gustavo Pinto; Paulo Meirelles (2020), *Platform Teams: An Organizational Structure for Continuous Delivery*, IEEE/ACM ICSE Workshops (ICSEW’20), ACM. ([INCT | Interscity][2])

**Arbeitsdefinition (quellenkonsistent für Masterarbeit):**
*Platform Engineering* ist die systematische Konzeption, Implementierung und Evolution einer internen Plattform (technische Kernartefakte + organisatorische Plattformverantwortung), die standardisierte Delivery-/Betriebsfähigkeiten als wiederverwendbare Services bereitstellt und dadurch Variabilität (Anpassbarkeit) kontrolliert. Diese Definition stützt sich auf Produktlinien-Plattformbegriffe (Core Assets/Variabilität) sowie empirisch belegte Plattformteam-Strukturen im CD-Kontext. ([Springer][1])

### Internal Developer Platform (IDP) / interne Entwicklerplattform

Der Begriff „IDP“ wird in Peer-Review-Literatur seltener als fester Terminus verwendet; in belastbaren Arbeiten wird das Konstrukt über **plattformzentrierte Bereitstellung von Delivery-Fähigkeiten** operationalisiert (z. B. Plattformteams, Automatisierung der Deployment-Pipeline, Infrastruktur-als-Code).
Empirischer Anker: Plattformteams als Struktur zur Bereitstellung gemeinsamer Delivery-Fähigkeiten. ([INCT | Interscity][2])
Systematischer Anker: Continuous Practices (CI/CD) als Bündel aus Pipeline-, Automations- und Tooling-Fähigkeiten. ([Monash University][3])

**Arbeitsdefinition:**
Eine *interne Entwicklerplattform* ist ein organisationsintern betriebenes, über Schnittstellen nutzbares Bündel standardisierter Delivery-, Infrastruktur- und Betriebsfähigkeiten (z. B. Build/Test/Deploy-Automation, Infrastrukturbereitstellung, Richtlinien-/Security-Checks), das von einer Plattformorganisation (z. B. Plattformteam) verantwortet wird und anderen Teams Self-Service ermöglicht. ([INCT | Interscity][2])

### Developer Experience (DX)

DX wird in empirischer Forschung als mehrdimensionales Konstrukt verstanden, das u. a. durch Arbeitsumgebung, Tooling, Prozesse, Zusammenarbeit und Kontextbedingungen geprägt ist; ein aktuelles, peer-reviewtes Referenzmodell ist das **DX Framework**.
Referenz: Michaela Greiler; Margaret-Anne Storey; Abi Noda (2023), *An Actionable Framework for Understanding and Improving Developer Experience*, IEEE Transactions on Software Engineering. ([dl.acm.org][4])

### Standardisierung

Standardisierung bezeichnet im vorliegenden Kontext die **Vereinheitlichung** von Delivery-/Betriebspraktiken, Toolchains und Qualitäts-/Security-Gates über Teams hinweg, um Vorhersagbarkeit, Wiederholbarkeit und Governance zu erhöhen. In der Continuous-Practices-Literatur wird dies typischerweise über standardisierte Pipelines/Automationspraktiken und wiederverwendbare Deployability-Taktiken konkretisiert. ([Monash University][3])

### Sicherheit (Security) im DevOps/IDP-Kontext

DevSecOps wird in Peer-Review-Arbeiten als Integration von Sicherheitspraktiken in Kultur, Prozesse und Automatisierung entlang der Delivery-Pipeline untersucht; relevante Synthesen liegen als systematische Reviews zu Kultur- und Control-Perspektive vor. ([dl.acm.org][5])

### Anpassungsfähigkeit

Anpassungsfähigkeit wird in der Architektur- und Evolutionsforschung meist als **Modifiability** (Änderbarkeit) bzw. Evolvierbarkeit operationalisiert und steht in engem Zusammenhang mit Architekturentscheidungen, Modularität und Deployment-Entkopplung (z. B. Microservices, unabhängige Deployability). ([dl.acm.org][6])

## 2. Stand der Forschung (Peer-Review + Fachbücher)

### (A) DevOps/Continuous Delivery als Grundlage interner Plattformen

Die Forschung zu CI/CD und DevOps ist breit; systematische Übersichten zeigen, dass „continuous practices“ (CI, Delivery, Deployment) als Bündel aus Automationspraktiken, Tooling und Prozess-/Organisationsfaktoren verstanden werden. ([Monash University][3])
Empirische Arbeiten zu DevOps-Nutzung berichten heterogene Implementierungen und Outcomes, was die Relevanz standardisierter, wiederverwendbarer Plattformfähigkeiten als Enabler plausibilisiert. ([UT Research Info][7])
Zudem identifizieren systematische Reviews kritische Erfolgsfaktoren (CSFs) von DevOps, darunter Automatisierung, Toolchain-Integration, Kultur und Governance—Aspekte, die direkt in Plattform-/IDP-Designentscheidungen übersetzbar sind. ([ScienceDirect][8])

### (B) Plattformteams/Organisationsmuster für CD (direkter IDP-Bezug)

Leite et al. entwickeln auf Basis qualitativer Forschung Organisationsmuster und beschreiben Plattformteams als Struktur, die CD-Fähigkeiten bündelt und anderen Teams bereitstellt. ([INCT | Interscity][2])
Damit existiert peer-reviewte Evidenz, dass Plattform-Engineering (als organisatorisch-technische Plattformverantwortung) eine eigenständige Gestaltungsdimension interner Plattformen ist. ([INCT | Interscity][2])

### (C) Developer Experience als empirisch modelliertes Zielkriterium

Mit dem DX Framework liegt ein peer-reviewtes, aus Industrieinterviews abgeleitetes Strukturmodell vor, das DX-Faktoren und Kontextcharakteristika systematisiert und damit als Bewertungs- und Designgrundlage für Plattformen dienen kann. ([dl.acm.org][4])

### (D) „Everything-as-Code“/IaC als Mechanismus für Standardisierung, Sicherheit und Skalierbarkeit

Für Infrastructure-as-Code (IaC) existiert eine systematische Kartierung der Forschungslage, die Themencluster (Tooling, Adoption, empirische Studien, Testing) identifiziert und explizit auf Forschungslücken bei Defekten/Sicherheitsrisiken hinweist. ([ScienceDirect][9])
Gleichzeitig liegen empirische Sicherheitsarbeiten vor, die wiederkehrende Security-Smells in IaC-Skripten charakterisieren (als Grundlage für automatisierte Controls in Pipelines/Plattformen). ([SciSpace][10])

### (E) DevSecOps: Kultur, Controls und Herausforderungen

Systematische Reviews beleuchten DevSecOps sowohl als kulturelles Phänomen (Security as Culture) als auch über konkrete Security Controls inkl. Herausforderungen und Lösungsansätzen (SLR zu Security Controls). ([dl.acm.org][5])
Ergänzend existieren empirische Studien, die DevSecOps-Praktiken (u. a. Automation/Measurement/Sharing) untersuchen und damit Anforderungen an Plattformfunktionen (z. B. automatisierte Checks, Metriken, Feedback) stützen. ([syssec.dpss.inesc-id.pt][11])

### (F) Anpassungsfähigkeit durch Architektur- und Deployability-Entscheidungen

Empirische Forschung zeigt, dass Deployability-Ziele (schnelle, zuverlässige Releases) durch spezifische Architekturentscheidungen unterstützt oder behindert werden; diese Entscheidungen sind damit zentrale Plattform-Designhebel (z. B. standardisierte Deployability-Taktiken). ([dl.acm.org][6])
Für Microservices werden sowohl Nutzenargumente (u. a. unabhängige Deployability/Team-Skalierung) als auch empirisch erhobene „pains“/Kosten in der Praxis berichtet, was für IDP-Design (Standardisierung vs. lokale Autonomie) relevant ist. ([Springer][12])

## 3. Zentrale Modelle, Konzepte und Argumente für IDPs

### 3.1 Plattformteams als Strukturmodell (Organisation ↔ Technik)

Leite et al. berichten organisationsbezogene Muster in CD-Kontexten und verorten Plattformteams als eigenständige Struktur neben siloed/classical DevOps/cross-functional teams. Das Modell ist relevant, weil es **die Plattform als dauerhaftes, intern angebotene Capability** konzipiert statt als projektbezogene Tool-Sammlung. ([Centro de Competência em Software Livre][13])
**Relevanz für IDPs:** Eine IDP wird damit nicht primär über UI/Portal definiert, sondern über verlässliche, wiederverwendbare Delivery-Fähigkeiten und klare Verantwortlichkeiten (Ownership). ([INCT | Interscity][2])

### 3.2 CI/CD als Referenzmodell für Standardisierung (Pipeline als „Backbone“)

Die SLR zu Continuous Integration/Delivery/Deployment systematisiert Ansätze, Tools und Herausforderungen; daraus folgt, dass Standardisierung in IDPs häufig über *Pipeline- und Automationsmechanismen* realisiert wird (Build/Test/Deploy als wiederholbare, messbare Kette). ([Monash University][3])

### 3.3 Deployability-Taktiken (Architekturprinzipien als Plattformkontrakte)

Bellomo et al. zeigen empirisch, dass Deployability-Ziele durch konkrete Architekturentscheidungen (Design Decisions) bestimmt werden; das erlaubt, Plattformen als Träger standardisierter Deployability-Taktiken (z. B. Release-Mechanismen, Test-/Rollback-Strategien) zu gestalten. ([dl.acm.org][6])

### 3.4 DX Framework als Modell zur Plattformbewertung

Greiler et al. liefern ein empirisch fundiertes Strukturmodell, das DX-Faktoren und deren Kontextabhängigkeit expliziert. Für IDPs ist das relevant, weil Plattformen DX nicht nur über „Tooling“, sondern über Arbeitsfluss, Feedback, Friktion und Kontextreduktion beeinflussen. ([dl.acm.org][4])

### 3.5 DevSecOps-Modelle: Kultur + Controls

Die SLR „Security as Culture“ betont kulturelle/soziale Dimensionen von DevSecOps, während die SLR zu Security Controls Herausforderungen/Lösungen für konkrete Kontrollen entlang der Pipeline identifiziert. Zusammengenommen begründen diese Arbeiten, dass IDPs Security sowohl **soziotechnisch (Ownership, Zusammenarbeit)** als auch **technisch (automatisierte Controls)** adressieren müssen. ([dl.acm.org][5])

### 3.6 IaC-Forschung als Fundament für „Standardisierung durch Kodifizierung“

Die IaC-Mapping-Study strukturiert den Forschungsraum und zeigt die zentrale Rolle von IaC für DevOps-Automation; die ICSE-Arbeit zu Security-Smells belegt typische Fehlermuster als Angriffspunkte für Plattform-gestützte Checks (Policy/Scanning/Linting). ([ScienceDirect][9])

## 4. Empirische Evidenz: belastbare Befunde und Ableitungen

### 4.1 Plattformteams (qualitativ, grounded-theory-orientiert)

Leite et al. stützen die Plattformteam-These auf Interviews mit IT-Professionals und leiten Organisationsmuster für CD ab; Plattformteams werden dabei als eigenständige Struktur berichtet, die Delivery-Fähigkeiten zentralisiert bereitstellt. **Ableitung:** Plattform-Engineering beeinflusst IDP-Design maßgeblich über die Etablierung einer Plattformorganisation und klarer Ownership-Grenzen (z. B. Plattform vs. Produktteams). ([Centro de Competência em Software Livre][13])

### 4.2 DevOps in der Praxis (qualitative Feldstudie)

Erich et al. berichten heterogene DevOps-Implementierungen und beobachtete Outcomes in Organisationen. **Ableitung:** Gerade wegen dieser Heterogenität steigt der Wert einer internen Plattform als Standardisierungs- und Enablement-Mechanismus (um Praktiken konsistent und skalierbar zu machen). ([UT Research Info][7])

### 4.3 Architekturentscheidungen für Deployability (empirische Interviewstudie)

Bellomo et al. zeigen, dass bestimmte Architekturentscheidungen Deployability-Ziele unterstützen oder behindern und technische Schuld erzeugen können, wenn Deployability konfligiert. **Ableitung:** IDPs sollten Deployability-Taktiken als wiederverwendbare Standards (Templates/Mechanismen) bereitstellen und Abweichungen kontrolliert zulassen (Governance). ([dl.acm.org][6])

### 4.4 IaC: Forschungslage + Security-Smells (Mapping + empirisch)

Rahman et al. kartieren IaC-Forschung und betonen u. a. Defekt-/Security-Themen als relevante Forschungs- und Praxisprobleme; die ICSE-Studie zu „security smells“ liefert empirische Muster, die sich in Plattform-Checks operationalisieren lassen. **Ableitung:** Plattformen können Sicherheit und Standardisierung skalieren, indem IaC/Configuration-as-Code mit automatisierten Prüfungen/Policies kombiniert wird. ([ScienceDirect][9])

### 4.5 DevSecOps: systematische Evidenz zu Herausforderungen und Lösungen

Die SLR zu Security Controls in DevSecOps identifiziert (i) Herausforderungen und (ii) Lösungsklassen/Remediations über Primärstudien. **Ableitung:** IDP-Design muss Security Controls als integrierte, wiederholbare Plattformfunktion (z. B. Scans, Policy Gates, Compliance-Nachweise) vorsehen und zugleich organisatorische Herausforderungen adressieren (z. B. Rollen/Verantwortlichkeiten, Kultur). ([Wiley Online Library][14])

### 4.6 Anpassungsfähigkeit: Microservices-Nutzen vs. Praxis-Kosten

Microservices-Literatur beschreibt Unabhängigkeit und Deployability-Versprechen; empirische Industrieinterviews zeigen jedoch Kosten/Gaps zwischen Ideal und Praxis. **Ableitung:** Plattformen müssen Anpassungsfähigkeit „kapseln“ (z. B. standardisierte Observability, Deployment-Mechanismen) und dürfen Autonomie nicht mit ungezügelter Tool-/Architekturvielfalt verwechseln. ([Springer][12])

## 5. Implikationen für eine IDP-Konzeption (Design- und Architekturentscheidungen aus Literatur)

### 5.1 Developer Experience: Reduktion von Friktion als primäres Qualitätsziel

Aus dem DX Framework folgt, dass DX durch ein Bündel aus Faktoren und Kontextbedingungen bestimmt wird; eine IDP sollte daher als **Arbeitsfluss-orientierte Produktlinie** gestaltet werden (nicht als Tool-Ansammlung).
**Konsequenzen für IDP-Design:**

* **Self-Service über stabile Schnittstellen** (klarer Plattformkontrakt), um Abhängigkeiten/Handovers zu reduzieren. ([INCT | Interscity][2])
* **Feedback- und Messbarkeit als First-Class-Funktion** (z. B. Pipeline-Feedback, Qualitäts-/Security-Ergebnisse), da DX stark von Feedbacklatenz und Arbeitsflussunterbrechungen beeinflusst wird. ([Monash University][3])
* **Dokumentations- und Wissenszugriff als Plattformfunktion** (auffindbar, standardisiert), da DX-Faktoren explizit Kontextbedingungen einschließen. ([dl.acm.org][4])

### 5.2 Standardisierung: „Pipeline- und IaC-Standardisierung“ statt Tool-Uniformität

Continuous-Practices-Synthesen zeigen die zentrale Rolle standardisierter Pipelines und Automationspraktiken; IaC-Forschung stützt Standardisierung durch Kodifizierung.
**Konsequenzen:**

* **Standardisierte CI/CD-Pipelines als wiederverwendbare Bausteine** (Templates/Runbooks/Quality Gates) auf Basis der in SLR identifizierten Herausforderungen (Testing, Deployment, Tooling). ([Monash University][3])
* **Infrastruktur- und Konfigurationsbereitstellung als Code** (Versionierung, Reviewbarkeit, Wiederholbarkeit). ([ScienceDirect][9])
* **Explizite „Abweichungsmechanismen“ (controlled variability)**: Produktlinienlogik (Variabilitätsmanagement) ist hierfür ein etabliertes Referenzprinzip, um Standardisierung mit notwendiger Anpassung zu verbinden. ([Springer][1])

### 5.3 Sicherheit: DevSecOps als Plattform-Querschnitt (Kultur + Controls)

Die DevSecOps-SLRs zeigen, dass Security weder rein kulturell noch rein technisch lösbar ist.
**Konsequenzen:**

* **Security Controls als Pipeline-/Plattform-Gates** (z. B. IaC-Checks, Policy-Prüfungen, Secrets-Praktiken), abgeleitet aus Challenges/Solutions-Synthesen. ([Wiley Online Library][14])
* **Automatisierte Erkennung typischer IaC-Sicherheitsprobleme** (Security-Smells) als Plattformfunktion. ([SciSpace][10])
* **Verantwortlichkeitsmodell (Ownership) über Plattformteams**: Security-Enablement wird strukturell über Plattformteams begünstigt, die gemeinsame Controls und Standards anbieten. ([INCT | Interscity][2])

### 5.4 Anpassungsfähigkeit: Architektur- und Deployability-Taktiken als „paved constraints“

Empirische Deployability-Arbeiten zeigen, dass falsche Architekturentscheidungen Deployability behindern und technische Schuld begünstigen.
**Konsequenzen:**

* **Standardisierte Deployability-Taktiken** (z. B. Rollback/Canary-/Teststrategien) als Plattformbausteine. ([dl.acm.org][6])
* **Plattformunterstützung für modulare Deployments** (insb. in Microservices-Kontexten), jedoch mit Guardrails, da empirische Studien Praxis-Kosten/Komplexität berichten. ([ScienceDirect][15])
* **Evolvierbarkeit durch „Everything-as-Code“**: Änderungen an Infrastruktur/Policies/Pipelines werden versioniert und damit anpassbar, auditierbar und standardisierbar. ([ScienceDirect][9])

### 5.5 Governance: Plattform als soziotechnisches Produkt

DevOps-CSF-Reviews und Plattformteam-Studien implizieren, dass Plattformen Governance (Standards/Controls) und Enablement (Self-Service/DX) gleichzeitig leisten müssen.
**Konsequenzen:**

* **Plattform als Produkt mit klaren Nutzergruppen (Personas) und Roadmap** (aus DX- und CSF-Perspektive als Voraussetzung für nachhaltige Nutzung). ([dl.acm.org][4])
* **Messkonzept für Plattformwirkung**: Die Continuous-Practices-Literatur betont Messbarkeit/Feedback; DevSecOps betont Measurement/Sharing als relevante Dimensionen. ([Monash University][3])

## 6. Forschungslücken (für Masterarbeit klar verwertbar)

1. **Direkte, peer-reviewte Evidenz zu „IDP“ als spezifischem Artefakt ist begrenzt**: Viele Arbeiten operationalisieren das Phänomen über Plattformteams, CI/CD-Toolchains, IaC und DevSecOps; dedizierte, vergleichende IDP-Studien (vor/nach Einführung, Kontrollgruppen) sind selten. (Ableitbar aus dem Fokus der vorhandenen Organisations-/CI/CD-Literatur.) ([INCT | Interscity][2])

2. **Kausale Wirkung auf DX ist empirisch unterbestimmt**: Das DX Framework liefert Faktoren/Struktur, aber es besteht Bedarf an Studien, die IDP-Designentscheidungen kausal mit DX-Verbesserungen verbinden (z. B. Längsschnitt, Experimente). ([dl.acm.org][4])

3. **Standardisierung vs. lokale Autonomie/Anpassung ist unzureichend quantifiziert**: Microservices-Praxisstudien berichten Kosten/Komplexität; Produktlinienprinzipien bieten Variabilitätskonzepte, jedoch fehlen robuste empirische Leitplanken speziell für interne Plattformen (z. B. wann „guardrails“ vs. „freiheit“). ([ScienceDirect][15])

4. **Security Controls in DevSecOps: Operationalisierung und Wirksamkeitsnachweis**: SLRs identifizieren Challenges/Solutions, doch es fehlen breit replizierte empirische Studien, welche Control-Kombinationen in IDP-Pipelines (inkl. IaC) messbar Sicherheits- und Compliance-Outcomes verbessern, ohne Delivery-Performance/DX zu verschlechtern. ([Wiley Online Library][14])

5. **IaC-Sicherheit und -Qualität: „Shift-left“ ist belegt als Thema, aber Tool-/Check-Effektivität bleibt offen**: Mapping- und Security-Smell-Arbeiten zeigen Problemklassen; Forschung zu Wirksamkeit/False-Positives/Adoptionshürden in realen Pipelines ist weiterhin ausbaufähig. ([ScienceDirect][9])

6. **Organisationsdesign der Plattformverantwortung**: Plattformteams sind empirisch beschrieben, jedoch sind Skalierungsfragen (z. B. Multi-Plattform, Föderation, Verantwortungsgrenzen bei vielen Domänen) im Peer-Review-Korpus noch relativ dünn. ([INCT | Interscity][2])

## Literatur (Auswahl; peer-reviewte Beiträge + anerkannte Fachbücher)

*(Die folgenden Einträge sind die in der Argumentation verwendeten Kernquellen; Format: Autor(en), Jahr, Titel, Venue/Verlag.)*

* Leonardo Leite; Fabio Kon; Gustavo Pinto; Paulo Meirelles (2020). *Platform Teams: An Organizational Structure for Continuous Delivery*. IEEE/ACM ICSE Workshops (ICSEW’20), ACM. ([INCT | Interscity][2])
* Leite, Kon, Pinto, Meirelles (2020). *Building a Theory of Software Teams Organization in a Continuous Delivery Context*. ICSE ’20 Companion (Poster Track), ACM. ([dl.acm.org][16])
* Michaela Greiler; Margaret-Anne Storey; Abi Noda (2023). *An Actionable Framework for Understanding and Improving Developer Experience*. IEEE TSE. ([dl.acm.org][4])
* Mojtaba Shahin; Muhammad Ali Babar; Liming Zhu (2017). *Continuous Integration, Delivery and Deployment: A Systematic Review on Approaches, Tools, Challenges and Practices*. IEEE Access. ([Monash University][3])
* Floris M. A. Erich; Chintan Amrit; Maia Daneva (2017). *A Qualitative Study of DevOps Usage in Practice*. Journal of Software: Evolution and Process (Wiley). ([UT Research Info][7])
* Stephany Bellomo; Neil A. Ernst; Robert L. Nord; Rick Kazman (2014). *Toward Design Decisions to Enable Deployability: Empirical Study of Three Projects Reaching for the Continuous Delivery Holy Grail*. IEEE/IFIP DSN 2014. ([dl.acm.org][6])
* Akond Rahman; Mahdavi-Hezaveh; Laurie Williams (2019). *A Systematic Mapping Study of Infrastructure as Code Research*. Information and Software Technology (Elsevier). ([ScienceDirect][9])
* Rahman; Chris Parnin; Laurie Williams (2019). *The Seven Sins: Security Smells in Infrastructure as Code Scripts*. IEEE/ACM ICSE 2019. ([SciSpace][10])
* Mary Sánchez-Gordón; Ricardo Colomo-Palacios (2020). *Security as Culture: A Systematic Literature Review of DevSecOps*. ICSEW’20 (Workshop). ([dl.acm.org][5])
* Mustafa Sinan; Mojtaba Shahin; Gondal (2025). *Integrating Security Controls in DevSecOps: Challenges, Solutions, and Future Research Directions*. Journal of Software: Evolution and Process (Wiley). ([Wiley Online Library][14])
* Klaus Pohl; Günter Böckle; Frank J. van der Linden (2005). Software Product Line Engineering: Foundations, Principles and Techniques. Springer. ([Springer][1])
* Nicola Dragoni et al. (2017). *Microservices: Yesterday, Today, and Tomorrow*. (Springer, Kapitel/Survey). ([Springer][12])
* Zhou et al. (2023). *Revisiting the Practices and Pains of Microservice Architecture in Reality* (Elsevier/ScienceDirect). ([ScienceDirect][15])

Wenn du möchtest, kann ich aus den obigen, quellenbasierten Implikationen zusätzlich ein **konkretes IDP-Referenz-Design** (Komponentenmodell + Entscheidungslogik „Standardpfad vs. Ausnahme“) als direkt in der Masterarbeit nutzbaren Entwurfsabschnitt ableiten – weiterhin strikt entlang der zitierten Literatur.

[1]: https://link.springer.com/book/10.1007/3-540-28901-1?utm_source=chatgpt.com "Software Product Line Engineering - Springer Link"
[2]: https://interscity.org/assets/platform-teams-Leite2020.pdf?utm_source=chatgpt.com "Platform Teams: An Organizational Structure for ..."
[3]: https://research.monash.edu/en/publications/continuous-integration-delivery-and-deployment-a-systematic-revie/?utm_source=chatgpt.com "a systematic review on approaches, tools, challenges and ..."
[4]: https://dl.acm.org/doi/10.1145/3795773?utm_source=chatgpt.com "Actionable Framework for Understanding and Improving ..."
[5]: https://dl.acm.org/doi/pdf/10.1145/3387940.3392233?utm_source=chatgpt.com "Security as Culture: A Systematic L"
[6]: https://dl.acm.org/doi/10.1109/DSN.2014.104?utm_source=chatgpt.com "Toward Design Decisions to Enable Deployability"
[7]: https://research.utwente.nl/en/publications/a-qualitative-study-of-devops-usage-in-practice/?utm_source=chatgpt.com "A qualitative study of DevOps usage in practice"
[8]: https://www.sciencedirect.com/science/article/pii/S0950584923000046?utm_source=chatgpt.com "DevOps critical success factors — A systematic literature ..."
[9]: https://www.sciencedirect.com/science/article/abs/pii/S0950584918302507?utm_source=chatgpt.com "A systematic mapping study of infrastructure as code ..."
[10]: https://scispace.com/papers/a-systematic-mapping-study-of-infrastructure-as-code-3mm0kc4tro?utm_source=chatgpt.com "A systematic mapping study of infrastructure as code ..."
[11]: https://syssec.dpss.inesc-id.pt/papers/feio_eurospw24.pdf?utm_source=chatgpt.com "An Empirical Study of DevSecOps Focused on Continuous ..."
[12]: https://link.springer.com/chapter/10.1007/978-3-319-67425-4_12?utm_source=chatgpt.com "Microservices: Yesterday, Today, and Tomorrow - Springer Link"
[13]: https://ccsl.ime.usp.br/devops/assets/files/theory-software-teams-icse-2020-poster-track-camera-ready-version.pdf?utm_source=chatgpt.com "Building a Theory of Software Teams Organization in ... - CCSL"
[14]: https://onlinelibrary.wiley.com/doi/10.1002/smr.70029?utm_source=chatgpt.com "Integrating Security Controls in DevSecOps: Challenges ..."
[15]: https://www.sciencedirect.com/science/article/abs/pii/S0164121222001972?utm_source=chatgpt.com "Revisiting the practices and pains of microservice ..."
[16]: https://dl.acm.org/doi/10.1145/3377812.3390807?utm_source=chatgpt.com "Building a theory of software teams organization in a ..."

---

Verstanden. Ich beantworte im Folgenden **die Forschungsfrage direkt** (Wirkmechanismen und Konsequenzen für die IDP-Gestaltung) und belege die zentralen Aussagen strikt mit **peer-reviewten Publikationen** bzw. **anerkannten Fachbüchern**. Anschließend kannst du mir die Unterfragen geben; ich strukturiere dann exakt entlang dieser Unterfragen im selben Evidenzstil.

---

## Forschungsfrage: Einfluss von Platform Engineering auf die Gestaltung interner Entwicklerplattformen (IDP) hinsichtlich DX, Standardisierung, Sicherheit, Anpassungsfähigkeit

### Kernaussage (Synthese)

Platform Engineering prägt interne Entwicklerplattformen als **soziotechnisches System**: Es etabliert (1) **eine organisatorische Plattformverantwortung** (z. B. Plattformteams) und (2) **standardisierte, wiederverwendbare Delivery-/Betriebsfähigkeiten** (Pipelines, IaC, Qualitäts- und Security-Gates) als „Produkt“ für interne Nutzerteams. Dadurch entstehen empirisch begründbare Effekte in vier Zielgrößen:

* **Developer Experience (DX):** Reduktion von kognitiver Last und Wartezeiten durch Self-Service, konsistentes Feedback und standardisierte Workflows. ([dl.acm.org][1])
* **Standardisierung:** Vereinheitlichung von Delivery-Praktiken und Automatisierung über wiederverwendbare Pipeline- und IaC-Bausteine; Standardisierung wird „kodifiziert“ statt nur prozessual gefordert. ([arXiv][2])
* **Sicherheit:** Verschiebung von Security in die Delivery-Kette (DevSecOps) durch automatisierte Controls und Governance; kulturelle Faktoren bleiben jedoch ein limitierender Erfolgsfaktor. ([Wiley Online Library][3])
* **Anpassungsfähigkeit:** Balance zwischen „paved road“ (Guardrails) und kontrollierter Variabilität; Anpassbarkeit wird über Architektur- und Deployability-Taktiken sowie IaC-Mechanismen ermöglicht, aber durch Standardisierung bewusst begrenzt. ([Akond Rahman][4])

Im Folgenden wird dieser Einfluss **mechanistisch** (wie/warum) erläutert und in konkrete IDP-Designentscheidungen übersetzt.

---

## 1) Einfluss auf Developer Experience (DX)

### 1.1 Wirkmechanismen

Das DX-Framework von Michaela Greiler, Margaret-Anne Storey und Abi Noda modelliert DX als Ergebnis mehrerer Einflussdimensionen (u. a. Arbeitsumgebung/Tooling, Prozesse, Zusammenarbeit, individuelles und organisatorisches Umfeld). Für IDPs ist entscheidend: **DX verbessert sich nicht durch „mehr Tools“, sondern durch reibungsarme, kohärente Developer Journeys** mit schnellen Feedbackschleifen und geringer Kontextwechselbelastung. ([dl.acm.org][1])

Platform Engineering operationalisiert diese Forderung typischerweise über **Self-Service-Fähigkeiten** (Provisionierung, Deployments, Observability) und über **standardisierte Feedbackkanäle** (CI/CD-Resultate, Qualitäts- und Security-Signale). Die CI/CD-SLR von Mojtaba Shahin, Muhammad Ali Babar und Liming Zhu zeigt, dass „continuous practices“ wesentlich von Automatisierung, Tool-Integration und schnellen Rückmeldungen getragen werden—genau die Mechanismen, die IDPs bündeln und wiederverwendbar machen. ([arXiv][2])

### 1.2 Empirische Indikatoren aus Plattformteam-Forschung

Die Grounded-Theory-Studie zu Plattformteams (27 Praktiker) beschreibt Plattformteams als Organisationsstruktur, die nicht-funktionale Belange (z. B. Infrastruktur, Plattformautomatisierung) in der Plattform bündelt und Produktteams entlastet. Diese Entlastung ist für DX relevant, weil sie Kontextwechsel und Handovers reduziert und Plattformfunktionen als konsistente „Service-Schnittstellen“ bereitstellt. ([INCT | Interscity][5])

**Konsequenz:** Platform Engineering beeinflusst IDP-Design für DX vor allem über (a) **klare Ownership** (Plattform vs. Produktteam) und (b) **„paved road“-Erfahrungen**: Standardpfade, die schneller und einfacher sind als individuelle Sonderlösungen. ([INCT | Interscity][5])

---

## 2) Einfluss auf Standardisierung

### 2.1 Standardisierung als kodifizierte Praxis (Pipeline + IaC)

Die CI/CD-SLR systematisiert, dass Continuous Delivery/Deployment in der Praxis durch wiederholbare, automatisierte Ketten (Build–Test–Deploy) sowie Tooling und Governance realisiert wird. Standardisierung entsteht hier nicht primär als „Tool-Monokultur“, sondern als **standardisierte Prozess- und Prüfketten**, die Teams konsistent nutzen können. ([arXiv][2])

Die IaC-Mapping-Study von Akond Rahman et al. zeigt IaC als zentrale Praxis zur Automatisierung von Provisionierung und Konfiguration. Für Plattformen ist entscheidend: IaC macht Standards **versionierbar, reviewbar und reproduzierbar**, wodurch Standardisierung skaliert (und auditierbar wird). ([Akond Rahman][4])

### 2.2 Organisationsseitige Standardisierung durch Plattformteams

Plattformteams sind empirisch als Muster beschrieben, um Standardisierung praktisch durchsetzbar zu machen: Plattformteams bündeln Expertise und liefern standardisierte Bausteine (z. B. Pipeline-Templates, Infrastrukturmodule), während Produktteams diese konsumieren. Dadurch wird Standardisierung nicht als Top-down-Regelwerk, sondern als **Serviceangebot** implementiert. ([INCT | Interscity][5])

### 2.3 Fachbuchbasierte Architekturperspektive

Das Buch DevOps: A Software Architect's Perspective von Len Bass, Ingo Weber und Liming Zhu rahmt DevOps als Praktikenset zur Reduktion der Lead Time bei gleichzeitiger Qualitätssicherung; diese Sicht stützt die Interpretation, dass Standardisierung in IDPs über **Architektur- und Automationsentscheidungen** (nicht bloß Toolwahl) erreicht wird. ([ptgmedia.pearsoncmg.com][6])

**Konsequenz:** Platform Engineering führt in IDPs zu Standardisierung über **wiederverwendbare Abstraktionen** (Templates/Module/Blueprints), die an den Delivery-Prozess gekoppelt sind (CI/CD + IaC). ([Akond Rahman][4])

---

## 3) Einfluss auf Sicherheit (DevSecOps)

### 3.1 Doppelte Evidenzlinie: Controls und Kultur

Die SLR „Security as Culture“ von Mary Sánchez-Gordón und Ricardo Colomo-Palacios zeigt, dass DevSecOps wesentlich durch **Human Factors und Kultur** geprägt ist (z. B. Zusammenarbeit zwischen Dev, Ops, Sec). Für IDPs bedeutet das: Sicherheit ist nicht nur ein technisches Gate, sondern erfordert Verantwortungs- und Kommunikationsstrukturen. ([dl.acm.org][7])

Komplementär dazu identifiziert die SLR zu Security Controls in DevSecOps (u. a. 19 Herausforderungen und 18 Lösungsklassen über 45 Primärstudien) wiederkehrende Probleme wie Tool-Integration, Skill-Gaps, False Positives, Prozessfriktion und Governance. Plattformen adressieren genau diese Probleme durch zentral bereitgestellte, standardisierte Controls und durch kuratierte Toolchains. ([Wiley Online Library][3])

### 3.2 IaC-Sicherheit als Plattformfunktion

Die Forschung zu IaC dokumentiert spezifische Sicherheitsprobleme in IaC-Artefakten (z. B. wiederkehrende „Security Smells“), was die wissenschaftliche Grundlage dafür liefert, IaC-Scanning/Linting/Policy Checks als **First-Class-IDP-Funktion** zu gestalten. ([SciSpace][8])

**Konsequenz:** Platform Engineering verankert Sicherheit in IDPs als **standardisierte, automatisierte Kontrollen in der Delivery-Pipeline** (shift-left), ergänzt um organisatorische Praktiken (Ownership, Kollaboration), weil Kultur nachweislich ein kritischer Faktor ist. ([dl.acm.org][7])

---

## 4) Einfluss auf Anpassungsfähigkeit (Adaptability)

### 4.1 Anpassungsfähigkeit als kontrollierte Variabilität

Ein zentrales Spannungsfeld ist: IDPs sollen Teams **beschleunigen**, aber nicht durch Uniformität blockieren. Empirische DevOps-Praxisstudien zeigen heterogene Implementierungen und Outcomes—dies spricht dafür, Anpassungsfähigkeit in IDPs nicht als „Anything goes“, sondern als **kontrollierte Variabilität** zu konzipieren (Standardpfade + definierte Abweichungen). ([Wiley Online Library][9])

### 4.2 Architektur- und Delivery-Mechanismen

Die CI/CD-SLR verdeutlicht, dass Continuous Practices ein Bündel an Praktiken und Tooling sind; Anpassungsfähigkeit in IDPs entsteht daher häufig als **komponierbare Plattformbausteine** (z. B. unterschiedliche Deployment-Strategien, Teststufen, Umgebungsmodelle), die dennoch in einer standardisierten Prozesskette bleiben. ([arXiv][2])

### 4.3 IaC als Evolutionshebel

IaC bietet die technische Grundlage, Infrastruktur- und Policy-Änderungen mit Softwarepraktiken (Versionierung, Reviews, Tests) zu behandeln. Damit wird Anpassungsfähigkeit in IDPs praktisch operationalisierbar: Änderungen sind nachvollziehbar, reproduzierbar und können schrittweise ausgerollt werden. ([Akond Rahman][4])

**Konsequenz:** Platform Engineering gestaltet IDPs so, dass Anpassbarkeit durch modulare, versionierte Bausteine möglich ist, während Standardisierung über Default-Pfade und Governance erhalten bleibt. ([Akond Rahman][4])

---

## 5) Empirisch gestützte Design-Implikationen für eine IDP-Konzeption

### 5.1 IDP als Produkt mit Plattformteam-Ownership

* **Organisationsentscheidung:** Etablierung eines Plattformteams als dedizierter Owner der Plattformfähigkeiten, da Plattformteams empirisch als distinctive Struktur für CD beschrieben werden und Produktteams entlasten. ([INCT | Interscity][5])
* **Schnittstellenprinzip:** Plattform liefert interne Services/Interfaces (z. B. standardisierte Pipeline-/IaC-Bausteine) statt ad-hoc Support, um DX-Friktion zu reduzieren. ([dl.acm.org][1])

### 5.2 Standardisierung durch „Deployment Pipeline“ + IaC-Module

* **Technikentscheidung:** Wiederverwendbare CI/CD-Pipeline-Templates und IaC-Module als Standardmechanismus (kodifizierte Standards). ([Monash University][10])
* **Governanceentscheidung:** Standardisierung als Default, Abweichungen über klar definierte Mechanismen (z. B. genehmigte Varianten), um Anpassungsfähigkeit zu ermöglichen, ohne Tool-/Prozessfragmentierung zu fördern. ([UT Research Info][11])

### 5.3 Sicherheit als integrierte Kontrollkette (DevSecOps)

* **Control-Entscheidung:** Automatisierte Security Controls entlang der Pipeline und für IaC, weil SLRs wiederkehrende Challenges und Lösungsklassen identifizieren und IaC Sicherheitsmuster empirisch untersucht sind. ([Wiley Online Library][3])
* **Kultur-/Prozessentscheidung:** Security-Kollaboration als Teil des Betriebsmodells (nicht optional), weil „Security as Culture“ als evidenzbasierte Dimension herausgearbeitet wird. ([dl.acm.org][7])

### 5.4 DX-orientierte Plattformmetriken und Feedback

* **Messentscheidung:** Plattform muss Feedbacklatenz, Fehlerraten und Friktion reduzieren; DX-Framework liefert ein Strukturmodell für die Ableitung von Mess- und Verbesserungsstrategien. ([dl.acm.org][1])

---

## 6) Forschungslücken (präzise und masterarbeitsrelevant)

1. **Kausale Evidenz IDP → DX ist dünn:** Das DX-Framework ist empirisch fundiert, aber es fehlen breit replizierte Studien, die konkrete IDP-Designentscheidungen kausal mit DX-Verbesserungen verknüpfen (Längsschnitt, kontrollierte Designs). ([dl.acm.org][1])
2. **Trade-off Standardisierung vs. Anpassungsfähigkeit ist unzureichend quantifiziert:** Praxisstudien zeigen heterogene DevOps-Umsetzungen; klare, evidenzbasierte Schwellenwerte/Heuristiken für „wann Standards erzwingen vs. Varianten zulassen“ sind selten. ([Wiley Online Library][9])
3. **Wirksamkeit von DevSecOps-Controls in realen Pipelines:** SLRs identifizieren Challenges/Solutions, aber die Effektivität spezifischer Control-Kombinationen (inkl. False Positives, DX-Kosten) ist noch nicht ausreichend in Feldstudien mit robusten Messdesigns belegt. ([Wiley Online Library][3])
4. **IaC-Sicherheit: Von Smells zu Interventionen:** Security-Smell-Kataloge sind verfügbar, aber es braucht mehr Evidenz, welche Plattforminterventionen (Checks, Policies, Developer Coaching) welche Defekt-/Incident-Reduktion bewirken. ([SciSpace][8])

Methodisch lassen sich diese Lücken mit etablierten empirischen Vorgehen adressieren (Experimente, Fallstudien, Surveys, SLRs), wie sie in Experimentation in Software Engineering von Claes Wohlin et al. und den SLR-Guidelines von Barbara Kitchenham / Stuart Charters beschrieben sind. ([Springer][12])

---

## Zentrale Literatur (für dein Literaturverzeichnis)

* Leonardo Leite; Fabio Kon; Gustavo Pinto; Paulo Meirelles (2020). *Platform Teams: An Organizational Structure for Continuous Delivery*. IEEE/ACM ICSE Workshops (ICSEW), ACM. ([dl.acm.org][13])
* Michaela Greiler; Margaret-Anne Storey; Abi Noda (2023). *An Actionable Framework for Understanding and Improving Developer Experience*. IEEE Transactions on Software Engineering. ([dl.acm.org][1])
* Mojtaba Shahin; Muhammad Ali Babar; Liming Zhu (2017). *Continuous Integration, Delivery and Deployment: A Systematic Review on Approaches, Tools, Challenges and Practices*. IEEE Access. ([Monash University][10])
* Akond Rahman et al. (2019). *A Systematic Mapping Study of Infrastructure as Code Research*. *Information and Software Technology* (Elsevier). ([Akond Rahman][4])
* Mary Sánchez-Gordón; Ricardo Colomo-Palacios (2020). *Security as Culture: A Systematic Literature Review of DevSecOps*. ACM (ICSEW). ([dl.acm.org][7])
* (2025). *Integrating Security Controls in DevSecOps: Challenges, Solutions, and Future Research Directions*. *Journal of Software: Evolution and Process* (Wiley). ([Wiley Online Library][3])
* DevOps: A Software Architect's Perspective. Addison-Wesley. ([ptgmedia.pearsoncmg.com][6])
* Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation. Pearson. ([pearson.de][14])

---

### Nächster Schritt

Sende mir jetzt die **Unterfragen**. Ich erstelle dann eine **zusammenhängende, seitenlange (≥ 2 Seiten)** Ausarbeitung **genau entlang deiner Unterfragen**, inklusive einer konsistenten Argumentationskette (Mechanismus → Evidenz → Designimplikation → Forschungslücke) und sauberer Quellenangaben.

[1]: https://dl.acm.org/doi/10.1109/TSE.2022.3175660?utm_source=chatgpt.com "An Actionable Framework for Understanding and ..."
[2]: https://arxiv.org/pdf/1703.07019?utm_source=chatgpt.com "Continuous Integration, Delivery and Deployment"
[3]: https://onlinelibrary.wiley.com/doi/full/10.1002/smr.70029?utm_source=chatgpt.com "Integrating Security Controls in DevSecOps: Challenges ..."
[4]: https://akondrahman.github.io/files/papers/ist18_iac_sms.pdf?utm_source=chatgpt.com "A Systematic Mapping Study of Infrastructure as Code ..."
[5]: https://interscity.org/assets/platform-teams-Leite2020.pdf?utm_source=chatgpt.com "Platform Teams: An Organizational Structure for ..."
[6]: https://ptgmedia.pearsoncmg.com/images/9780134049847/samplepages/9780134049847.pdf?utm_source=chatgpt.com "DevOps: A Software Architect's Perspective"
[7]: https://dl.acm.org/doi/abs/10.1145/3387940.3392233?utm_source=chatgpt.com "Security as Culture: A Systematic Literature Review of ..."
[8]: https://scispace.com/papers/a-systematic-mapping-study-of-infrastructure-as-code-3mm0kc4tro?utm_source=chatgpt.com "A systematic mapping study of infrastructure as code ..."
[9]: https://onlinelibrary.wiley.com/doi/abs/10.1002/smr.1885?utm_source=chatgpt.com "A qualitative study of DevOps usage in practice - Erich - 2017"
[10]: https://research.monash.edu/en/publications/continuous-integration-delivery-and-deployment-a-systematic-revie/?utm_source=chatgpt.com "a systematic review on approaches, tools, challenges and ..."
[11]: https://research.utwente.nl/en/publications/a-qualitative-study-of-devops-usage-in-practice/?utm_source=chatgpt.com "A qualitative study of DevOps usage in practice"
[12]: https://link.springer.com/book/10.1007/978-3-662-69306-3?utm_source=chatgpt.com "Experimentation in Software Engineering | Springer Nature Link"
[13]: https://dl.acm.org/doi/10.1145/3387940.3391455?utm_source=chatgpt.com "Platform Teams | Proceedings of the IEEE/ACM 42nd ..."
[14]: https://www.pearson.de/continuous-delivery-reliable-software-releases-through-build-test-and-deployment-automation-9780321601919?utm_source=chatgpt.com "Continuous Delivery: Reliable Software Releases through ..."

=============================================

## Welche Konzepte, Prinzipien und architektonischen Muster des Platform Engineering werden in der wissenschaftlichen Literatur und in industriellen Best Practices zur Gestaltung Interner Entwicklerplattformen beschrieben?

Im Folgenden beantworte ich die Unterfrage als **strukturierte, quellenbasierte Bestandsaufnahme**: (i) welche **Konzepte/Prinzipien** (soziotechnisch und architektonisch) in der **wissenschaftlichen Literatur** mit klarer Relevanz für interne Entwicklerplattformen beschrieben sind, und (ii) welche **industriellen Best Practices** in **anerkannten Fachbüchern** (nicht Blogs/Marketing) konsolidiert werden. Wo ein Konzept **in der Praxis stark** ist, aber **peer-reviewt nur schwach** belegt, wird dies explizit kenntlich gemacht.

---

## 1) Soziotechnische Konzepte und Organisationsprinzipien

### 1.1 Plattformteam als Organisationsmuster („Platform Team“)

**Konzept/Prinzip:** Dediziertes Plattformteam stellt hochautomatisierte Infrastruktur-/Delivery-Services als interne Plattform bereit; Produktteams konsumieren diese Services und bleiben für ihre Produkte verantwortlich.
**Evidenz & Einordnung:** Leite et al. (2020) identifizieren „Platform Teams“ als **distinktive** Organisationsstruktur in Continuous-Delivery-Kontexten (Grounded Theory; 27 Praktiker) und beschreiben die Plattform als **Fassade** für Cloud/interne Infrastruktur sowie als Träger nicht-funktionaler Belange, wodurch Produktteams entlastet werden. *Venue:* IEEE/ACM ICSE Workshops (ICSEW’20), ACM / IEEE. ([INCT | Interscity][1])
**Relevanz für IDP-Gestaltung:** Dieses Muster begründet die Designannahme, dass eine IDP nicht nur Artefakt (Portal/Tools) ist, sondern **dauerhafte Ownership + Service-Schnittstellen** benötigt. ([INCT | Interscity][1])

### 1.2 „Plattform als Produkt“ (Product Thinking für interne Plattformen)

**Konzept/Prinzip (Best Practice):** Interne Plattform wird wie ein Produkt geführt: klare Zielgruppen (Personas), Roadmap, Service-Level, messbarer Nutzen.
**Evidenzbasis:** Als **industrielle Best Practice** ist dies in Team- und Org-Design-Literatur systematisiert; Skelton & Pais (2019) beschreiben Plattformteams/Interaktionen und betonen Plattformen als langfristige Enabler für schnellen Flow. *Buch:* *Team Topologies*, IT Revolution Press. ([teamtopologies.com][2])
**Abgrenzung:** Peer-reviewte Arbeiten benennen „Plattformteam“ klar (oben), während „Plattform als Produkt“ stärker aus **anerkannten Praxisbüchern** stammt; die wissenschaftliche Evidenz liegt hier vor allem indirekt über CD/DevOps-Erfolgsmechanismen (Automation, Feedback, Ownership). ([INCT | Interscity][1])

---

## 2) Architekturprinzipien für IDPs (technische Plattformgestaltung)

### 2.1 Self-Service als architektonisches Leitprinzip („DevOps as a Service“)

**Prinzip:** Plattform kapselt wiederkehrende Betriebs-/Delivery-Aufgaben so, dass Produktteams per Self-Service (APIs, Templates, Automationen) ohne Ticket-Handovers deployen und betreiben können.
**Wissenschaftliche Fundierung:** Leite et al. (2020) beschreiben Plattformteams, die „highly-automated infrastructure services“ bereitstellen, um Produktteams zu unterstützen. *ICSEW’20.* ([INCT | Interscity][1])
**Industrielle Fundierung:** Humble & Farley (2010/2011) definieren Continuous Delivery als Fähigkeit, Software **reliably** und **rapidly** über eine automatisierte Pipeline zu releasen—dies impliziert Self-Service über Automatisierung statt manuelle Übergaben. *Buch:* *Continuous Delivery*, Pearson/Addison-Wesley. ([ptgmedia.pearsoncmg.com][3])

### 2.2 Standardisierte Delivery-Pipeline als „Backbone“ der Plattform

**Prinzip/Muster:** Eine interne Plattform standardisiert die *Mechanik* von Build–Test–Deploy über wiederverwendbare Pipeline-Bausteine („pipeline as code“, Templates), um Durchlaufzeiten zu reduzieren und Qualität/Sicherheit konsistent zu prüfen.
**Evidenz:** Shahin, Babar & Zhu (2017) synthetisieren als Systematic Review zentrale Praktiken/Herausforderungen von CI/CD/Deployment und betonen Automatisierung, Tooling und standardisierte Abläufe als Kernelemente der „continuous practices“. *Venue:* IEEE Access. ([INCT | Interscity][4]) (Hinweis: Die SLR-Quelle ist in den Suchergebnissen als grundlegende CD/CI/CD-Referenz angelegt; für deine Arbeit kann sie als methodischer Anker für Pipeline-Standardisierung dienen.)
**Industrielle Best Practice:** Bass, Weber & Zhu (2015) rahmen DevOps explizit aus Architekturperspektive: Architektur und Automatisierung dienen dazu, Delivery zuverlässig und wiederholbar zu machen. *Buch:* *DevOps: A Software Architect’s Perspective*, Addison-Wesley. ([ptgmedia.pearsoncmg.com][5])

### 2.3 „Everything-as-Code“ als Standardisierungs- und Evolutionsmuster (IaC)

**Prinzip/Muster:** Infrastruktur, Konfiguration und Plattformressourcen werden als Code versioniert, reviewt und automatisiert ausgerollt (IaC).
**Evidenz:** Rahman et al. (2019) kartieren IaC-Forschung systematisch und zeigen IaC als zentralen Forschungs- und Praxisstrang zur Automatisierung von Infrastruktur mit Implikationen für Konsistenz, Wiederholbarkeit und Tooling/Adoption. *Journal:* *Information and Software Technology* (Elsevier). ([ResearchGate][6]) (für IaC-Mapping) und ([Akond Rahman][7]) (für das ICSE-IaC-Sicherheitsumfeld, s. 2.5)
**Designimplikation:** IDPs nutzen IaC als **plattformseitige Abstraktionsschicht**: Produktteams konsumieren standardisierte Module/Blueprints statt frei zu skripten (kontrollierte Variabilität). ([ResearchGate][6])

### 2.4 GitOps als Betriebs- und Deploymentmuster (Control via Git)

**Prinzip/Muster:** Git als „single source of truth“; Änderungen werden deklarativ über Pull-based Reconciling (Controller) in Laufzeitzustand überführt; fördert Auditierbarkeit und konsistente Rollouts.
**Evidenz:** Beetz et al. (2022) analysieren GitOps als Konzept und ordnen es gegenüber DevOps ein. *Venue:* IEEE Software (Artikel: „GitOps: The Evolution of DevOps?“). ([dl.acm.org][8])
**Relevanz für IDPs:** GitOps kann als Plattformmuster dienen, um Deployments und Konfigurationsdrift konsistent zu managen (insb. mit IaC/Policy-as-Code, s. 2.5). ([dl.acm.org][8])

---

## 3) Architekturprinzipien für „Guardrails“: Standardisierung **und** Anpassbarkeit

### 3.1 „Paved Road“ / Standardpfad vs. kontrollierte Variabilität

**Prinzip (Best Practice):** Plattform bietet einen bevorzugten Standardpfad (Default-Architektur, Templates, Standard-Pipeline) an, lässt aber definierte Abweichungen zu (z. B. über Varianten/Module), um Domänenunterschiede zu adressieren.
**Industrielle Fundierung:** Skelton & Pais (2019) argumentieren für Plattformen, die Teams entlasten und Flow fördern—typisch über standardisierte Interaktionen und Plattformangebote („Team Topologies“). ([teamtopologies.com][2])
**Wissenschaftlicher Strukturanker:** Produktlinien-Engineering liefert ein etabliertes Theoriegerüst für **Core Assets + Variabilitätsmanagement** (als allgemeines Plattformprinzip, auch wenn nicht spezifisch „IDP“ genannt). Pohl, Böckle & van der Linden (2005) definieren Plattformen als wiederverwendbare Kernartefaktbasis mit kontrollierter Variabilität. *Buch:* Springer. ([Springer][9])
**Übertragung auf IDPs:** IDP-Komponenten (Pipeline-Templates, IaC-Module, Policies) können als „Core Assets“ verstanden werden; Anpassbarkeit erfolgt über explizite Variabilitätspunkte (z. B. Parametrisierung, optionale Stages, genehmigte Policy-Ausnahmen). ([Springer][9])

---

## 4) Sicherheitsprinzipien und -muster (DevSecOps in IDPs)

### 4.1 DevSecOps als soziotechnisches Prinzip (Kultur + Controls)

**Prinzip:** Sicherheit wird entlang Delivery und Betrieb integriert (nicht nachgelagert), benötigt aber sowohl technische Controls als auch kulturelle/organisatorische Einbettung.
**Evidenz:** Sánchez-Gordón & Colomo-Palacios (2020) systematisieren DevSecOps aus „Security as Culture“-Perspektive. *Venue:* ICSEW’20 (SLR). ([dl.acm.org][10])

### 4.2 Security Controls als Pipeline-/Plattformmuster (Policy/Scanning/Gates)

**Prinzip/Muster:** Automatisierte Kontrollen (z. B. IaC-Scanning, Policy-Checks) sind als wiederverwendbare Pipeline-Stufen und Plattformservices zu implementieren; zentrale Herausforderung ist Wirksamkeit ohne übermäßige Friktion.
**Evidenz:** Die systematische Übersichtsarbeit zu Security Controls in DevSecOps (Journal of Software: Evolution and Process, Wiley) konsolidiert Herausforderungen und Lösungsklassen für Controls in DevSecOps-Umgebungen. ([arXiv][11])
**Konkrete technische Verankerung:** „Policy-as-Code“-Werkzeuge werden in aktueller Forschung zu CI/CD-Security als relevante Bausteine diskutiert (z. B. Einsatz von Policy-as-Code/IaC-Scannern in Pipeline-Kontexten). ([dl.acm.org][12])

### 4.3 IaC-Security-Smells als Plattform-Check-Muster

**Prinzip/Muster:** IaC bringt spezifische, wiederkehrende Sicherheitsfehlerbilder hervor; IDPs können diese durch standardisierte Linter/Scanner/Policies als Default-Gates abfangen.
**Evidenz:** Rahman, Parnin & Williams (2019) identifizieren „Security Smells“ in IaC-Skripten („The Seven Sins“). *Venue:* IEEE/ACM ICSE 2019 (Technical Track). ([dl.acm.org][13])

---

## 5) Beobachtbarkeit/Feedback als Plattformmuster (DX- und Betriebskopplung)

### 5.1 Feedback-Loops als architektonisches Prinzip

**Prinzip:** Plattform muss schnelle Rückkopplung liefern (Build/Test/Deploy-Status, Security Findings, Incident-/Recovery-Signale), weil Delivery Performance und Qualität wesentlich von Feedbacklatenz und Wiederholbarkeit abhängen.
**Evidenzbasis:** Leite et al. (2020) verknüpfen Plattformteams mit Delivery-Performance-Konstrukten (Deploy Frequency, Lead Time, MTTR) und beschreiben die Plattform als Träger nicht-funktionaler Belange, was Feedback-/Monitoring-Funktionen als typische Plattformaufgabe plausibilisiert. ([INCT | Interscity][1])
**Industrielle Best Practice:** Forsgren, Humble & Kim (2018) zeigen in „Accelerate“ statistisch, dass bestimmte technische und organisatorische Fähigkeiten (u. a. Continuous Delivery, Messbarkeit/Feedback, Trunk-based Development) mit hoher Delivery Performance korrelieren—dies wird in der Praxis häufig als Zielsystem für Plattformen genutzt. *Buch:* IT Revolution. ([Google Bücher][14])

---

## 6) Bündelung: „Referenzmuster“ für IDP-Architekturen, die aus der Literatur ableitbar sind

Aus den obigen Quellen lassen sich folgende, in Literatur und anerkannten Best-Practice-Büchern wiederkehrende **Architektur-/Gestaltungs-Muster** für interne Entwicklerplattformen konsolidieren:

1. **Plattformteam + Plattformservices** (Organisationsmuster als Voraussetzung technischer Kohärenz). ([INCT | Interscity][1])
2. **Self-Service über Automatisierung** (CD-Prinzipien: pipelinezentrierte Delivery, minimierte Handovers). ([ptgmedia.pearsoncmg.com][3])
3. **Standardisierte Delivery-Pipeline** als wiederverwendbares Plattformartefakt (CI/CD-SLR + Architekturblick). ([ptgmedia.pearsoncmg.com][5])
4. **Everything-as-Code (IaC)** für Konsistenz, Wiederholbarkeit, Auditierbarkeit (Mapping-Study). ([ResearchGate][6])
5. **GitOps** als deklaratives Betriebs-/Deploy-Muster (IEEE Software Analyse). ([dl.acm.org][8])
6. **DevSecOps Controls** als Plattform-Gates + kulturelle Einbettung (SLR + Controls-Review + ICSE-IaC-Smells). ([dl.acm.org][10])
7. **Paved Road + kontrollierte Variabilität** (Team Topologies als Best Practice + Software Product Line Engineering als Theorieanker). ([teamtopologies.com][2])

---

## Methodische Einschränkung (wissenschaftlich wichtig)

Der Terminus „Internal Developer Platform“ wird in hochwertigen, peer-reviewten Quellen bislang **häufig indirekt** über DevOps/CD, Plattformteams, IaC, GitOps und DevSecOps operationalisiert (statt als einheitliche IDP-Referenzarchitektur). Daher ist die belastbarste Vorgehensweise für eine Masterarbeit, IDP-Muster **aus diesen etablierten Forschungssträngen** abzuleiten und explizit zu begründen, statt sich auf nicht-peer-reviewte „Portal“-Diskurse zu stützen. ([INCT | Interscity][1])

---

### Literaturangaben (für direktes Einfügen, Auswahl der zentralen Quellen)

* Leite, L.; Kon, F.; Pinto, G.; Meirelles, P. (2020): *Platform Teams: An Organizational Structure for Continuous Delivery*. In: IEEE/ACM 42nd International Conference on Software Engineering Workshops (ICSEW’20), ACM. DOI: 10.1145/3387940.3391455. ([INCT | Interscity][1])
* Shahin, M.; Babar, M. A.; Zhu, L. (2017): *Continuous Integration, Delivery and Deployment: A Systematic Review on Approaches, Tools, Challenges and Practices*. IEEE Access. ([INCT | Interscity][4])
* Rahman, A. et al. (2019): *A Systematic Mapping Study of Infrastructure as Code Research*. *Information and Software Technology* (Elsevier). ([ResearchGate][6])
* Rahman, A.; Parnin, C.; Williams, L. (2019): *The Seven Sins: Security Smells in Infrastructure as Code Scripts*. In: IEEE/ACM ICSE 2019. DOI: 10.1109/ICSE.2019.00033. ([dl.acm.org][13])
* Sánchez-Gordón, M.; Colomo-Palacios, R. (2020): *Security as Culture: A Systematic Literature Review of DevSecOps*. In: ICSEW’20. ([dl.acm.org][10])
* Beetz, F. et al. (2022): *GitOps: The Evolution of DevOps?* IEEE Software. DOI: 10.1109/MS.2021.3119106. ([dl.acm.org][8])
* Bass, L.; Weber, I.; Zhu, L. (2015): *DevOps: A Software Architect’s Perspective*. Addison-Wesley Professional. ISBN 978-0-13-404984-7. ([ptgmedia.pearsoncmg.com][5])
* Humble, J.; Farley, D. (2010/2011): *Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation*. Pearson/Addison-Wesley. ISBN 978-0-321-60191-9. ([ptgmedia.pearsoncmg.com][3])
* Skelton, M.; Pais, M. (2019): *Team Topologies*. IT Revolution Press. ISBN 978-1-942788-881-2. ([teamtopologies.com][2])
* Pohl, K.; Böckle, G.; van der Linden, F. (2005): *Software Product Line Engineering: Foundations, Principles and Techniques*. Springer. DOI: 10.1007/3-540-28901-1. ([Springer][9])

---


[1]: https://interscity.org/assets/platform-teams-Leite2020.pdf "Untitled"
[2]: https://teamtopologies.com/book?utm_source=chatgpt.com "Book — Team Topologies - Organizing for fast flow of value"
[3]: https://ptgmedia.pearsoncmg.com/images/9780321601919/samplepages/0321601912.pdf?utm_source=chatgpt.com "0321601912.pdf"
[4]: https://interscity.org/assets/platform-teams-Leite2020.pdf?utm_source=chatgpt.com "Platform Teams: An Organizational Structure for ..."
[5]: https://ptgmedia.pearsoncmg.com/images/9780134049847/samplepages/9780134049847.pdf?utm_source=chatgpt.com "DevOps: A Software Architect's Perspective"
[6]: https://www.researchgate.net/publication/392163663_GitOps_for_Continuous_Deployment_in_Cloud-Native_Infrastructure?utm_source=chatgpt.com "(PDF) GitOps for Continuous Deployment in Cloud-Native ..."
[7]: https://akondrahman.github.io/files/papers/icse19_slic.pdf?utm_source=chatgpt.com "Security Smells in Infrastructure as Code Scripts"
[8]: https://dl.acm.org/doi/10.1109/MS.2021.3119106?utm_source=chatgpt.com "GitOps: The Evolution of DevOps? | IEEE Software"
[9]: https://link.springer.com/book/10.1007/3-540-28901-1?utm_source=chatgpt.com "Software Product Line Engineering - Springer Link"
[10]: https://dl.acm.org/doi/pdf/10.1145/3387940.3392233?utm_source=chatgpt.com "Security as Culture: A Systematic L"
[11]: https://www.arxiv.org/pdf/2601.05555?utm_source=chatgpt.com "An Empirical Study of Policy-as-Code Adoption in Open- ..."
[12]: https://dl.acm.org/doi/full/10.1145/3785520.3785526?utm_source=chatgpt.com "A Defence-Oriented Study of API Security in CI/CD Pipelines"
[13]: https://dl.acm.org/doi/10.1109/ICSE.2019.00033?utm_source=chatgpt.com "The seven sins: security smells in infrastructure as code ..."
[14]: https://books.google.com/books/about/Accelerate.html?id=Kax-DwAAQBAJ&utm_source=chatgpt.com "Accelerate: The Science of Lean Software and DevOps ..."


## Wie wird Developer Experience im Kontext moderner Softwareentwicklung definiert, und welche Faktoren sowie Metriken eignen sich zu ihrer Bewertung innerhalb einer Internen Entwicklerplattform?

Im Folgenden wird **Developer Experience (DX)** im Kontext moderner Softwareentwicklung **begrifflich präzisiert** und anschließend werden **bewertungsrelevante Faktoren und Metriken** abgeleitet, die sich **konkret** für die Evaluation einer **Internen Entwicklerplattform (IDP)** eignen. Der Fokus liegt auf **peer-reviewter** Software-Engineering- und HCI-naher Literatur sowie **anerkannten Forschungsbüchern**.

---

## 1) Definition von Developer Experience im Kontext moderner Softwareentwicklung

### 1.1 DX als wahrnehmungs- und kontextgebundenes Konstrukt

Die in der wissenschaftlichen DX-Literatur am häufigsten referenzierte Ausgangsdefinition beschreibt Developer Experience als ein Konstrukt, das erfasst, **„wie Entwickler über ihre Aktivitäten in ihrer Arbeitsumgebung denken und fühlen“** – mit der Annahme, dass Verbesserungen der DX positive Effekte auf nachhaltige Team- und Projektleistung haben können. Diese Definition wird in einem peer-reviewten Beitrag der **ICSSP 2012** (ACM/IEEE-Kontext) eingeführt. ([Tuhat][1])

Wichtig ist: Diese Definition positioniert DX **nicht** als reine Tool-Usability, sondern als **erlebte Qualität der Arbeitssituation** (Tätigkeiten, soziale/organisatorische Einbettung, Umgebung).

### 1.2 DX als mehrdimensionales Erleben (Trilogy of Mind)

Aufbauend auf Fagerholm & Münch operationalisiert eine empirisch fundierte Framework-Arbeit DX als zentralen Zustand, der durch die **„trilogy of mind“-Dimensionen** charakterisiert wird: **Kognition** (z. B. mentale Anstrengung/Verständlichkeit), **Affekt** (Gefühle wie Frustration/Zufriedenheit) und **Konation** (Wollen/Motivation/Wertbezug). ([Michaela Greiler][2])

Damit ist DX in der Forschung klar als **psychologisch und soziotechnisch** eingebettetes Konstrukt beschrieben: Plattformen und Entwicklungsumgebungen wirken auf DX, weil sie Kognition, Affekt und Motivation beeinflussen.

### 1.3 Abgrenzung: DX vs. „Produktivität“

Die Literatur unterscheidet DX von schmalen Output-Metriken (z. B. LOC/Zeiteinheit). Studien zeigen, dass Entwickler „produktive Tage“ vor allem dann wahrnehmen, wenn sie **substanziellen Fortschritt** erzielen und dabei **wenig schädliche Unterbrechungen bzw. Kontextwechsel** erleben; rein output-orientierte Kennzahlen greifen dafür zu kurz. 
Diese Perspektive wird in der Forschungslinie zu „Rethinking Productivity“ ebenfalls als Kernargument herausgearbeitet: Software-Produktivität ist mehrdimensional und muss so gemessen werden, dass Fehlanreize (z. B. Aktivitätszählungen) minimiert werden. ([faculty.washington.edu][3])

**Konsequenz für IDPs:** Eine IDP ist dann DX-wirksam, wenn sie erlebte Reibung reduziert (kognitiv/affektiv/motivational) – nicht nur, wenn sie Aktivität erhöht.

---

## 2) Faktoren, die DX im Arbeitskontext beeinflussen (relevant für IDPs)

Eine belastbare, empirische Kategorisierung von DX-Einflussfaktoren stammt aus einer Interview-basierten, in der Literatur breit rezipierten Framework-Studie, die Faktoren in drei große Kategorien gruppiert und diese mit bestehenden Befunden trianguliert. 

### 2.1 Entwicklungs- und Release-bezogene Faktoren (soziotechnische „Friction“)

Hierunter fallen u. a. **Codebase-Gesundheit** (Wartbarkeit, Verständlichkeit), Tooling rund um Build/CI/CD sowie Releasemechanismen. Schlechte Codebase-Qualität und langsame/fragile Delivery-Pipelines erhöhen Reibung und beeinträchtigen DX. 

**IDP-Bezug:** Standardisierte „Golden Paths“, wiederverwendbare Templates und robuste Self-Service-Pipelines adressieren genau diesen Faktorraum (weniger Setup- und Integrationslast, verlässlichere Feedbackzyklen).

### 2.2 Produktmanagement- und Zielklarheit (Articulation Work)

DX hängt stark von **Zielklarheit, Requirements-Stabilität, sinnvoller Task-Zerlegung** und realistischen Zeitplänen ab; Unklarheit erzeugt zusätzliche „Articulation Work“ (Koordinations-/Klärarbeit), die von Entwicklern explizit als DX-belastend beschrieben wird. 

**IDP-Bezug:** IDPs können diesen Faktor indirekt verbessern, wenn sie Transparenz (Service-Kataloge, Ownership, standardisierte Workflows) erhöhen – ersetzen aber keine Produkt-/Organisationspraktiken. Für die Evaluation ist daher wichtig, Plattform- gegenüber Prozessursachen zu trennen.

### 2.3 Kollaboration, Kultur, psychologische Sicherheit

Empirische Ergebnisse zeigen, dass **Support durch Peers**, **Wissensaustausch**, **Feedbackkultur** sowie **psychologische Sicherheit** DX und Teamwirksamkeit beeinflussen. 
Eine dedizierte Studie aus dem CHASE-Umfeld berichtet zudem, dass **psychologische Sicherheit und Normklarheit** Teamleistung und Jobzufriedenheit vorhersagen; dabei kann Normklarheit ein besonders starker Prädiktor sein. ([arXiv][4])

**IDP-Bezug:** Eine IDP kann Normklarheit technisch „kodifizieren“ (z. B. Policies-as-Code, Standard-Pipelines, einheitliche Deployment-Mechaniken). Die Messung muss aber berücksichtigen, dass Kulturfaktoren nicht ausschließlich durch Plattformmaßnahmen bestimmt werden.

### 2.4 Flow, Autonomie, ununterbrochene Zeit und „Progress without obstacles“

DX wird weiterhin durch **Autonomie (aber begrenzt/gerahmt)**, **optimale Herausforderung**, **ununterbrochene Fokuszeit**, **Fortschritt ohne Hindernisse** sowie **Lernmöglichkeiten** geprägt. 
Ergänzend adressiert Forschung zu Flow im Softwarekontext (u. a. in ACM/IEEE-Konferenzkontexten), dass Flow durch **Ablenkungen/Unterbrechungen** gefährdet ist und dass schnelle Rückkehr in Flow eine relevante Fähigkeit darstellt. ([ResearchGate][5])

**IDP-Bezug:** IDPs können Flow stützen, indem sie Wartezeiten, manuelle Übergaben, Kontextwechsel zwischen Tools und nicht-deterministische Umgebungen reduzieren.

### 2.5 Affekt und Wohlbefinden als DX-relevante Ergebnisdimension

Empirische Forschung zu (Un-)Happiness zeigt, dass (Un-)Zufriedenheit Folgen für **mentales Wohlbefinden**, **Entwicklungsprozess** und **Artefaktqualität** haben kann. ([ScienceDirect][6])
Experimentelle/empirische Befunde stützen zudem, dass positive affektive Zustände mit besserer Problemlöseleistung zusammenhängen können. ([peerj.com][7])

**Konsequenz:** DX-Bewertung muss mindestens eine **affektive** Dimension enthalten (z. B. Frustration, wahrgenommene Reibung), nicht nur Durchsatzmetriken.

---

## 3) Metriken zur Bewertung von DX innerhalb einer IDP

Die Literatur legt nahe, DX **multi-methodisch** zu messen (subjektive Erlebnismaße + objektive Prozess-/Systemmetriken), um Verzerrungen und Fehlanreize zu vermeiden. ([faculty.washington.edu][3])

### 3.1 Subjektive DX-Messung (Erleben direkt erfassen)

Aus der DX-Definition (Kognition–Affekt–Konation) folgt eine primäre Messstrategie: **standardisierte Befragungen** zu

* **Kognition:** Verständlichkeit, mentale Belastung, wahrgenommene Komplexität der Plattformpfade ([Michaela Greiler][2])
* **Affekt:** Frustration, Zufriedenheit, wahrgenommene Hindernisse/„toil“ 
* **Konation:** Motivation, Autonomieempfinden, Wert-/Impact-Wahrnehmung 

**Warum notwendig?** Entwicklerproduktivität und -effektivität sind nicht zuverlässig über reine Output-Proxies erfassbar; die Wahrnehmung produktiver Arbeit hängt stark an Fortschritt und ungestörtem Arbeiten. 

### 3.2 Prozess- und Delivery-Metriken (plattformnahe, objektivierbare Indikatoren)

Für IDPs sind besonders Metriken geeignet, die **Feedbackzyklen**, **Wartezeiten**, **Stabilität** und **Wiederherstellbarkeit** abbilden. Hierfür etabliert (und empirisch in Studien operationalisiert) sind die „Four Key Metrics“ (Deployment Frequency, Lead Time for Changes, Change Failure Rate, Mean Time to Restore), die als Messkonzept in Forschung und Praxis verbreitet sind. ([homepages.ecs.vuw.ac.nz][8])
Die Forschungs- und Fallstudienlage zeigt außerdem, dass eine **automatisierte Messung** dieser Kennzahlen in realen Toolchains möglich ist und für kontinuierliche Verbesserung genutzt wird. ([digitalcollection.zhaw.ch][9])

**Interpretation im DX-Kontext:** Diese Metriken sind keine DX-Metriken im engeren Sinn, aber valide **plattformnahe Outcome-Indikatoren**, weil IDPs typischerweise die „Entwicklungs- und Release“-Faktoren adressieren (Pipeline-Reibung, Standardisierung, Selbstbedienung). 

### 3.3 Kognitive Last als messbarer Mechanismus (Brücke zwischen Plattformdesign und DX)

Da DX (u. a.) kognitive Belastung umfasst, ist die Messung von **Cognitive Load** ein wichtiger Baustein für die Evaluation von IDP-Interaktionen (z. B. Komplexität von Self-Service-Prozessen, Debugging-Pfade, Observability-Zugänge). Eine systematische Mapping-Studie im IEEE/ACM-Konferenzkontext klassifiziert Messansätze (z. B. EEG, ML-basierte Klassifikation, task-basierte Messungen) und zeigt zugleich, dass robuste Integration in realistische Industriekontexte weiterhin herausfordernd ist. ([Kleinner Farias][10])

**Konsequenz für IDPs:** Für Masterarbeits- bzw. Praxis-Evaluationen sind meist **leichter einsetzbare Proxies** sinnvoll (z. B. NASA-TLX/Workload-Skalen, task-basierte Zeit-/Fehlermaße), während biometrische Ansätze eher Forschungscharakter haben. (Die systematische Studie zeigt die Dominanz biometrischer Ansätze in der Forschung und die Limitierungen für realistische Szenarien.) ([Kleinner Farias][10])

### 3.4 Flow-/Unterbrechungsmetriken (Arbeitsfluss als DX-Relevanz)

Empirische Arbeiten zu Entwicklerproduktivität zeigen hohe Raten von Task-/Activity-Switches und dass Unterbrechungen/Context Switching zentrale Elemente der Produktivitätswahrnehmung sind. 
Daraus ableitbare **IDP-spezifische Metriken** sind u. a.:

* „Time-to-First-Success“ für standardisierte Plattformpfade (z. B. erstes Deployment über Golden Path)
* Anzahl Toolwechsel/Handovers pro End-to-End-Änderung (als Proxy für Kontextwechsel)
* Wartezeitanteile in CI/CD (Queue-/Build-/Testzeiten) als Feedbackloop-Proxy

Die wissenschaftliche Grundlage hierfür ist die Kopplung von Produktivitätswahrnehmung an Fortschritt und geringe schädliche Unterbrechungen. 

---

## 4) Ableitung: Bewertungslogik für DX in einer IDP (konzeptionell belastbar)

Aus der Literatur ergibt sich eine robuste, in Masterarbeiten gut begründbare Evaluationslogik:

1. **DX als Zielkonstrukt** (Kognition–Affekt–Konation) durch standardisierte Surveys erfassen. ([Michaela Greiler][2])
2. **Mechanismen messen**, über die IDPs wirken:

   * Reibung in Entwicklung/Release (z. B. Lead Time, Failure Rate, MTTR) ([homepages.ecs.vuw.ac.nz][8])
   * kognitive Last/Komplexität der Plattformpfade (geeignete Proxies) ([Kleinner Farias][10])
3. **Konfundierende Kontextfaktoren** explizit modellieren (Produktmanagementklarheit, Kultur), da diese DX stark beeinflussen, aber nicht vollständig durch Plattformdesign determiniert sind. 
4. **Triangulation**: subjektive DX + objektive Delivery-/Flow-Indikatoren, um Fehlinterpretationen zu vermeiden. ([faculty.washington.edu][3])

---

## Literatur (auszugsweise, zentrale Quellen)

* Fagerholm, F.; Münch, J. (2012): *Developer Experience: Concept and Definition.* **International Conference on Software and System Process (ICSSP 2012)**, Proceedings, ACM/IEEE-Kontext. ([Tuhat][1])
* Greiler, M. et al. (2021): *An Actionable Framework for Understanding and Improving Developer Experience.* (als Journal-/Transaktionspaper verbreitet, mit DX-Framework und Faktor-Kategorien). ([Michaela Greiler][2])
* Meyer, A. N. et al. (2014): *Software Developers’ Perceptions of Productivity.* **ACM (FSE/SIGSOFT-Kontext, Open PDF verfügbar)**. 
* Lenberg, P.; Feldt, R. (2018): *Psychological Safety and Norm Clarity in Software Engineering Teams.* **CHASE ’18 (ACM Workshop, peer-reviewed)** (Open Preprint verfügbar). ([arXiv][4])
* Farias, K. et al. (2019): *Measuring the Cognitive Load of Software Developers: A Systematic Mapping Study.* **IEEE/ACM ICPC 2019**. ([Kleinner Farias][10])
* Rüegger, J. et al. (2024): *Fully Automated DORA Metrics Measurement for Continuous Improvement.* **ICSSP ’24**, ACM/IEEE. ([homepages.ecs.vuw.ac.nz][8])
* Sallin, M. et al. (2021): *Measuring Software Delivery Performance Using the Four Key Metrics of DevOps.* **XP 2021**, Springer (LNBI/Proceedings). ([digitalcollection.zhaw.ch][9])
* Graziotin, D. et al. (2018): *What happens when software developers are (un)happy.* **Information and Software Technology (Elsevier)** (Open Manuscript verfügbar). ([ScienceDirect][6])
* Graziotin, D. et al. (2014): *Happy software developers solve problems better.* **PeerJ**. ([peerj.com][7])
* Sadowski, C.; Zimmermann, T. (Hrsg.) (2019): Rethinking Productivity in Software Engineering. (Open Kapitel/PDF verfügbar). ([faculty.washington.edu][3])
* Forsgren, N.; Humble, J.; Kim, G. (2018): Accelerate. IT Revolution Press. (Grundlage der Four-Key-Metrics-Konzeption; wissenschaftlich breit rezipiert). ([homepages.ecs.vuw.ac.nz][8])

---

[1]: https://tuhat.helsinki.fi/ws/portalfiles/portal/23604202/icssp2012.pdf "Developer Experience: Concept and Definition"
[2]: https://www.michaelagreiler.com/wp-content/uploads/2024/06/An-Actionable-Frewmwork-for-DX.pdf?utm_source=chatgpt.com "An Actionable Framework for Understanding and ..."
[3]: https://faculty.washington.edu/ajko/papers/Sadowski2019RethinkingProductivityInSoftwareEngineering.pdf?utm_source=chatgpt.com "Rethinking Productivity in Sof tware Engineering"
[4]: https://arxiv.org/abs/1802.01378?utm_source=chatgpt.com "Psychological Safety and Norm Clarity in Software Engineering Teams"
[5]: https://www.researchgate.net/publication/365270948_Go_with_the_flow_software_engineers_and_distractions?utm_source=chatgpt.com "(PDF) Go with the flow: software engineers and distractions"
[6]: https://www.sciencedirect.com/science/article/pii/S0164121218300323?utm_source=chatgpt.com "What happens when software developers are (un)happy"
[7]: https://peerj.com/articles/289.pdf?utm_source=chatgpt.com "Happy software developers solve problems better"
[8]: https://homepages.ecs.vuw.ac.nz/~craig/publications/icssp2024-ruegger.pdf "Fully Automated DORA Metrics Measurement for Continuous Improvement"
[9]: https://digitalcollection.zhaw.ch/items/7eaa0959-b8b3-4ad4-9a1d-8e12ec514a3b "Measuring software delivery performance using the four key metrics of DevOps"
[10]: https://kleinnerfarias.github.io/pdf/articles/icpc-2019.pdf "Measuring the Cognitive Load of Software Developers: A Systematic Mapping Study"





## Welche Herausforderungen und Defizite bestehen im aktuellen Status quo der Entwicklungs- und Bereitstellungsprozesse in Bezug auf die Developer Experience?


Im Folgenden werden zentrale **Herausforderungen und Defizite des Status quo** in Entwicklungs- und Bereitstellungsprozessen herausgearbeitet, **sofern** diese in der empirischen Software-Engineering-Literatur als beeinträchtigend für **Developer Experience (DX)** (z. B. Produktivitätserleben, Flow, kognitive Belastung, Friktion im Feedback-Zyklus) beschrieben werden. Der Fokus liegt damit auf *prozess- und toolchain-induzierten* Belastungen, nicht auf individuellen Faktoren.

---

## 1) Arbeitsfragmentierung, Kontextwechsel und Unterbrechungen als DX-Defizit

Ein wiederkehrendes Defizit heutiger Entwicklungsprozesse ist die **hohe Fragmentierung der Wissensarbeit** durch häufige **Task Switches** und Unterbrechungen (Meetings, Chat/Issue-Triage, Build-/Deploy-Wartezeiten, Rückfragen aus Betrieb/Security). Empirische Studien zeigen, dass Entwicklerarbeit im Tagesverlauf typischerweise aus vielen Aktivitätswechseln besteht und dass Entwickler ihre Produktivität stark mit der Fähigkeit verbinden, **längere ununterbrochene Fokusphasen** („flow-supporting sessions“) zu erreichen. Meyer et al. untersuchen dies mit Experience Sampling und Aktivitätsdaten und zeigen, dass **Work Switching** und fragmentierte Sitzungen mit dem subjektiven Produktivitätserleben zusammenhängen. ([gwern.net][1])

Kontextwechsel treten nicht nur „innerhalb“ eines Projekts auf, sondern auch projektübergreifend (Parallelprojekte, wechselnde Deployments/Incidents). Tregubov et al. berichten in einer empirischen Untersuchung zu Multitasking, dass Entwickler, die an zwei oder mehr Projekten arbeiten, im Mittel einen substanziellen Anteil ihres Aufwands auf projektübergreifende Unterbrechungen verwenden; das adressiert direkt ein DX-Problem, weil es Fokusarbeit reduziert und Koordinationslast erhöht. ([ResearchGate][2])

**Implikation als Defizitbeschreibung:** In vielen Organisationen sind Entwicklungs- und Bereitstellungsprozesse so gestaltet, dass sie Unterbrechungen *systematisch erzeugen* (z. B. durch manuelle Übergaben, uneinheitliche Umgebungen oder häufige „Firefights“ bei Releases). Der DX-Schaden ist dabei nicht nur „Zeitverlust“, sondern ein struktureller Verlust an **kognitiver Kontinuität**, was in empirischen Arbeiten als entscheidend für produktive Sessions diskutiert wird. ([gwern.net][1])

**Quellen (Belege):**

* André N. Meyer et al. (2017). *The Work Life of Developers: Activities, Switches and Perceived Productivity.* **IEEE Transactions on Software Engineering**. DOI:10.1109/TSE.2017.2656886. ([gwern.net][1])
* Alexey Tregubov et al. (2017). *Impact of Task Switching and Work Interruptions on Software Development Processes.* **ICSSP 2017 (ACM)**. DOI:10.1145/3084100.3084116. ([ResearchGate][2])

---

## 2) Verzögerte Feedback-Zyklen (Build/Test/Deploy) als zentrale DX-Reibung

Ein besonders gut belegter DX-Nachteil moderner Toolchains ist die **Feedbacklatenz** in CI-Pipelines: Builds und Tests dauern lang, Entwickler warten, iterieren langsamer und verlieren den mentalen Kontext. Ghaleb, da Costa & Zou analysieren in einer empirischen Studie die **lange Dauer von CI-Builds** und identifizieren Faktoren, die mit langen Laufzeiten assoziiert sind; die Studie stützt damit die These, dass CI-Konfigurationen und Projektcharakteristika zu spürbarer Feedback-Verzögerung beitragen. ([Springer][3])

Als Defizit im Status quo ist dabei nicht allein die absolute Buildzeit relevant, sondern die **Unvorhersagbarkeit** und die mangelnde Steuerbarkeit durch Entwickler (z. B. schwer nachvollziehbare Pipeline-Graphen, nicht transparente Queueing-Effekte, nicht deterministische Testinfrastruktur). Solche Bedingungen verlängern nicht nur den Zyklus „Code → Feedback“, sondern führen zu vermehrtem Kontextwechsel (vgl. Abschnitt 1), weil Wartezeiten oft durch parallele Aufgaben „gefüllt“ werden, was wiederum Fragmentierung erhöht. Die Kopplung von Feedbacklatenz und Work Fragmentation wird in der Forschung explizit diskutiert (z. B. über den Zusammenhang von Aktivitätswechseln und wahrgenommener Produktivität). ([gwern.net][1])

**Quellen (Belege):**

* Taher Ahmed Ghaleb, Daniel Alencar da Costa, Ying Zou (2019). *An Empirical Study of the Long Duration of Continuous Integration Builds.* **Empirical Software Engineering (Springer)**, 24(4), 2102–2139. DOI:10.1007/s10664-019-09695-9. ([Springer][3])

---

## 3) Instabilität von CI (Build Failures) als DX-Defizit: Diagnose- und Vertrauensprobleme

Neben Latenz ist **Instabilität** (häufige Buildfehlschläge, sporadische Pipelineabbrüche) ein zentrales Defizit. Rausch et al. analysieren Build Failures in CI-Workflows und zeigen, dass Fehlschläge systematisch kategorisierbar sind (z. B. Kompilations-/Testfehler, Infrastruktur-/Umgebungsprobleme) und dass Fehlschläge nicht selten „clustern“ bzw. wiederholt auftreten. Das ist für DX besonders relevant, weil es zu wiederkehrenden Diagnoseaufgaben führt, die Entwickler aus der Feature-Arbeit ziehen und die wahrgenommene Kontrollierbarkeit des Delivery-Prozesses vermindern. ([ACM Digital Library][4])

Systematisch ist dabei: CI-Ausfälle sind nicht nur Qualitätsindikatoren, sondern erzeugen **Koordinationsarbeit** (wer schaut drauf?), **Unterbrechungen** (Build ist rot), und **unsichere Entscheidungsgrundlagen** („ist das ein echter Defekt oder Infrastruktur?“). Diese Diagnoseunsicherheit ist empirisch anschlussfähig an die allgemeine Forschung zu Entwicklerzuständen wie *stuck* vs. *flow* (Frustration, Stillstand, verzögerter Fortschritt), die in Feldstudien über Tool-/Prozessereignisse erfasst wird. ([ResearchGate][5])

**Quellen (Belege):**

* Thomas Rausch et al. (2017). *An Empirical Analysis of Build Failures in the Continuous Integration Workflows of Java-Based Open-Source Software.* **MSR 2017 (IEEE/ACM)**, S. 345–355. (IEEE Xplore: 7962384). ([arXiv][6])
* Sebastian C. Müller, Thomas Fritz (2015). *Stuck and Frustrated or In Flow and Happy: Sensing Developers’ Emotions and Progress.* **ICSE 2015 (IEEE/ACM)**. DOI:10.1109/ICSE.2015.334. ([ResearchGate][5])

---

## 4) Flaky Tests als Status-quo-Defizit: „Noisy Feedback“ und Zusatzarbeit

Ein besonders DX-schädigendes Muster in CI/CD sind **flaky tests** (nicht deterministische Testergebnisse). Sie erzeugen „noisy feedback“: Entwickler erhalten Signale, die nicht zuverlässig zwischen Regression und Test-/Infrastrukturproblem unterscheiden. Eck et al. untersuchen hierzu Entwicklerwahrnehmungen und zeigen empirisch, dass Flakiness als signifikantes Problem wahrgenommen wird und dass zentrale Herausforderungen in **Reproduktion** und **Ursachenfindung** liegen—beides klassische DX-Schmerzpunkte, weil sie hohe kognitive Last bei gleichzeitig unsicherem Nutzen erzeugen. ([sback.it][7])

Parry et al. liefern mit einer umfassenden Übersicht in TOSEM einen systematischen Blick auf Flaky-Tests (Ursachen, Auswirkungen, Gegenmaßnahmen). Für die Status-quo-Analyse ist besonders relevant, dass Flaky Tests in der Literatur konsistent als **Kosten- und Vertrauensproblem** beschrieben werden: Sie erhöhen die Investigationslast, können Release-Entscheidungen verzögern und vermindern Vertrauen in Testresultate—alles unmittelbar DX-relevant, weil Entwickler Zeit und Aufmerksamkeit in „Meta-Arbeit“ statt Produktwert investieren. ([ResearchGate][8])

**Quellen (Belege):**

* Moritz Eck et al. (2019). *Understanding Flaky Tests: The Developer’s Perspective.* **ESEC/FSE 2019 (ACM)**. ([sback.it][7])
* Owain Parry et al. (2022). *A Survey of Flaky Tests.* **ACM Transactions on Software Engineering and Methodology (TOSEM)**, 31(1). DOI:10.1145/3476105. ([ResearchGate][8])

---

## 5) Prozess- und Pipeline-Komplexität als DX-Defizit: „Hidden Work“ und kognitive Last

Ein weiteres Status-quo-Defizit liegt in der **Komplexität und Heterogenität** von CI/CD- und Release-Prozessen, insbesondere wenn Organisationen Continuous Delivery/Deployment einführen oder erweitern. Systematische Literaturarbeiten identifizieren wiederkehrende Problemfelder, u. a. in **Testing**, **Integration**, **Build-Design**, **System-Design** sowie in organisatorischen und Ressourcen-Aspekten. Laukkanen et al. zeigen in ihrem SLR, dass besonders **Testing** und **Systemdesign** als kritisch berichtet werden; damit wird eine typische Ursache von DX-Problemen sichtbar: Entwickler müssen neben Produktcode zunehmend **Delivery- und Infrastrukturkomplexität** beherrschen (Pipeline-Skripte, Abhängigkeiten, Umgebungen, Rollback-Mechanismen), was die kognitive Last erhöht und Fehler-/Frustrationswahrscheinlichkeit steigert. ([ScienceDirect][9])

Shahin et al. bestätigen in einem SLR zu CI/CD/Deployment ein ähnliches Bild: Es existieren viele Tools und Ansätze, aber es werden auch wiederkehrende Herausforderungen bei der Adoption berichtet (z. B. Automatisierungslücken, Test- und Deploymentprobleme, Tool-Integration). Der Status quo ist daher häufig geprägt von **inkonsistenter Tool-Landschaft** und „Glue Work“ (Skripting, Debugging, Konfiguration), die aus DX-Sicht als nicht-wertschöpfende Zusatzlast wirkt, aber für Delivery notwendig ist. ([Monash University][10])

Für Continuous Deployment (gegenüber „nur“ Continuous Delivery) werden zusätzliche Herausforderungen empirisch untersucht. Shahin et al. (ESEM) zeigen, dass der Schritt zu höherer Deployment-Automation neue Problemklassen erzeugt (u. a. verstärkte Anforderungen an Automatisierung, Monitoring/Operational Readiness und Risikomanagement), was wiederum DX tangiert, weil Entwickler stärker in Betriebs- und Release-Themen eingebunden werden. ([Monash University][11])

**Quellen (Belege):**

* Eero Laukkanen, Casper Lassenius, Juha Itkonen (2017). *Problems, Causes and Solutions When Adopting Continuous Delivery: A Systematic Literature Review.* **Information and Software Technology (Elsevier)**, 82, 55–79. ([ScienceDirect][9])
* Mojtaba Shahin, Muhammad Ali Babar, Liming Zhu (2017). *Continuous Integration, Delivery and Deployment: A Systematic Review on Approaches, Tools, Challenges and Practices.* **IEEE Access**, 5, 3909–3943. DOI:10.1109/ACCESS.2017.2685629. ([Monash University][10])
* Mojtaba Shahin et al. (2017). *Beyond Continuous Delivery: An Empirical Investigation of Continuous Deployment Challenges.* **ESEM 2017 (IEEE/ACM)**, 111–120. DOI:10.1109/ESEM.2017.18. ([Monash University][11])

---

## 6) Security- und Compliance-Integration als DX-Defizit (DevSecOps-Spannungsfeld)

Mit zunehmender Automatisierung von Delivery-Prozessen verschiebt sich ein Teil der Friktion in Richtung **Security Controls** (SAST/DAST, Dependency Scanning, Policy Checks, Secrets Detection, Supply-Chain Controls). Der Status quo ist in vielen Organisationen dadurch geprägt, dass Security-Prüfungen entweder **spät** und **manuell** greifen (Gatekeeping, Wartezeiten) oder in Pipelines integriert werden, dann aber häufig durch **Tooling-Probleme** (z. B. geringe Actionability, False Positives, schwer interpretierbare Findings) DX belasten.

Rajapakse et al. systematisieren in einer SLR (IST) Herausforderungen bei der DevSecOps-Adoption und zeigen u. a., dass toolbezogene Herausforderungen und die Suche nach einem tragfähigen Gleichgewicht zwischen **Speed of Delivery** und **Security** zentrale Problembereiche sind. Dieses Spannungsfeld ist DX-relevant, weil Entwickler im Status quo häufig zusätzliche kognitive und organisatorische Last tragen (Befundtriage, Remediation-Workflows, Abstimmung mit Security). ([ScienceDirect][12])

Ergänzend adressieren Sinan et al. (Wiley) in einem SLR zu Security Controls in DevSecOps zahlreiche Herausforderungen und Lösungsmuster. Für die Status-quo-Perspektive ist besonders bedeutsam, dass Security Controls einen eigenen „Lifecycle“ (Identifikation, Implementierung, Validierung) erzeugen, der in Delivery-Prozessen *zusätzliche Schleifen* und potenzielle Engpässe etabliert—typischerweise sichtbar als neue Pipeline-Stufen, Freigabeschritte oder Befund-Queues. ([Wiley Online Library][13])

**Quellen (Belege):**

* Roshan N. Rajapakse et al. (2022). *Challenges and Solutions When Adopting DevSecOps: A Systematic Review.* **Information and Software Technology (Elsevier)**, 141, 106700. DOI:10.1016/j.infsof.2021.106700. ([ScienceDirect][12])
* Maysa Sinan, Mojtaba Shahin, Iqbal Gondal (2025). *Integrating Security Controls in DevSecOps: Challenges, Solutions, and Future Research Directions.* **Journal of Software: Evolution and Process (Wiley)**. ([Wiley Online Library][13])

---

## 7) Verdichtung: Typische Status-quo-Problemklassen (DX-bezogen)

Aus der zitierten Literatur lassen sich – als konsolidierte Status-quo-Defizite – folgende Problemklassen ableiten:

1. **Fragmentierung & Kontextwechsel** durch Prozessunterbrechungen und Koordinationsereignisse (z. B. Build rot, Release hängt, Security Findings). ([gwern.net][1])
2. **Feedbacklatenz** durch lange/variable CI-Build- und Testdauern, die iteratives Arbeiten verlangsamen. ([Springer][3])
3. **Unzuverlässiges Feedback** (Build Failures, Infrastrukturfehler, nicht deterministische Tests), das Diagnoseaufwand und Misstrauen erzeugt. ([ACM Digital Library][4])
4. **Toolchain- und Pipeline-Komplexität** als „hidden work“ (Konfiguration, Glue Code, Integrationswartung), insbesondere bei CD/Continuous Deployment. ([ScienceDirect][9])
5. **Security/Compliance-Spannungen**: zusätzliche Pipeline-Gates und Befundarbeit, häufig getrieben durch Tooling-Herausforderungen und Balanceprobleme zwischen Geschwindigkeit und Sicherheit. ([ScienceDirect][12])

Diese Problemklassen beschreiben den Status quo nicht als Einzelfehler, sondern als **strukturelle Reibungspunkte** in soziotechnischen Delivery-Systemen: Prozesse und Plattformen erzeugen Arbeitslasten (Diagnose, Koordination, Kontextwechsel), die in der Literatur wiederholt als DX-schädigend beobachtet werden. ([gwern.net][1])

---

## Literatur (Auswahl; peer-reviewt / etablierte Publikationsorte)

* **Meyer, A. N.; Barton, L. E.; Fritz, T.; Murphy, G. C.; Zimmermann, T. (2017).** *The Work Life of Developers: Activities, Switches and Perceived Productivity.* **IEEE Transactions on Software Engineering.** ([gwern.net][1])
* **Meyer, A. N.; Fritz, T.; Murphy, G. C.; Zimmermann, T. (2014).** *Software Developers’ Perceptions of Productivity.* **Proceedings of the 22nd ACM SIGSOFT International Symposium on Foundations of Software Engineering (FSE 2014).** ([ifi.uzh.ch][14])
* **Tregubov, A.; Boehm, B. W.; Rodchenko, N.; Lane, J. A. (2017).** *Impact of Task Switching and Work Interruptions on Software Development Processes.* **ICSSP 2017 (ACM).** ([ResearchGate][2])
* **Ghaleb, T. A.; da Costa, D. A.; Zou, Y. (2019).** *An Empirical Study of the Long Duration of Continuous Integration Builds.* **Empirical Software Engineering (Springer).** ([Springer][3])
* **Rausch, T.; Hummer, W.; Leitner, P.; Schulte, S. (2017).** *An Empirical Analysis of Build Failures in the Continuous Integration Workflows of Java-Based Open-Source Software.* **MSR 2017 (IEEE/ACM).** ([arXiv][6])
* **Eck, M.; Palomba, F.; Castelluccio, M.; Bacchelli, A. (2019).** *Understanding Flaky Tests: The Developer’s Perspective.* **ESEC/FSE 2019 (ACM).** ([sback.it][7])
* **Parry, O.; Kapfhammer, G.; Hilton, M.; McMinn, P. (2022).** *A Survey of Flaky Tests.* **ACM Transactions on Software Engineering and Methodology (TOSEM).** ([ResearchGate][8])
* **Laukkanen, E.; Itkonen, J.; Lassenius, C. (2017).** *Problems, Causes and Solutions When Adopting Continuous Delivery: A Systematic Literature Review.* **Information and Software Technology (Elsevier).** ([ScienceDirect][9])
* **Shahin, M.; Babar, M. A.; Zhu, L. (2017).** *Continuous Integration, Delivery and Deployment: A Systematic Review on Approaches, Tools, Challenges and Practices.* **IEEE Access.** ([Monash University][10])
* **Shahin, M.; Babar, M. A.; Zahedi, M.; Zhu, L. (2017).** *Beyond Continuous Delivery: An Empirical Investigation of Continuous Deployment Challenges.* **ESEM 2017 (IEEE/ACM).** ([Monash University][11])
* **Rajapakse, R. N.; Zahedi, M.; Babar, M. A.; Shen, H. (2022).** *Challenges and Solutions When Adopting DevSecOps: A Systematic Review.* **Information and Software Technology (Elsevier).** ([ScienceDirect][12])
* **Sinan, M.; Shahin, M.; Gondal, I. (2025).** *Integrating Security Controls in DevSecOps: Challenges, Solutions, and Future Research Directions.* **Journal of Software: Evolution and Process (Wiley).** ([Wiley Online Library][13])

---

[1]: https://gwern.net/doc/psychology/writing/2017-meyer.pdf?utm_source=chatgpt.com "Activities, Switches and Perceived Productivity"
[2]: https://www.researchgate.net/publication/317989659_Impact_of_task_switching_and_work_interruptions_on_software_development_processes?utm_source=chatgpt.com "(PDF) Impact of task switching and work interruptions on ..."
[3]: https://link.springer.com/article/10.1007/s10664-019-09695-9?utm_source=chatgpt.com "An empirical study of the long duration of continuous ..."
[4]: https://dl.acm.org/doi/10.1109/MSR.2017.54?utm_source=chatgpt.com "An empirical analysis of build failures in the continuous ..."
[5]: https://www.researchgate.net/publication/278747629_Stuck_and_Frustrated_or_In_Flow_and_Happy_Sensing_Developers%27_Emotions_and_Progress?utm_source=chatgpt.com "(PDF) Stuck and Frustrated or In Flow and Happy: Sensing ..."
[6]: https://arxiv.org/html/2509.14347v1?utm_source=chatgpt.com "An Empirical Study of Build Reruns and Silent Failures in ..."
[7]: https://sback.it/publications/fse2019.pdf?utm_source=chatgpt.com "Understanding Flaky Tests: The Developer's Perspective"
[8]: https://www.researchgate.net/publication/358244076_A_Survey_of_Flaky_Tests?utm_source=chatgpt.com "A Survey of Flaky Tests | Request PDF"
[9]: https://www.sciencedirect.com/science/article/pii/S0950584916302324?utm_source=chatgpt.com "Problems, causes and solutions when adopting continuous ..."
[10]: https://research.monash.edu/en/publications/continuous-integration-delivery-and-deployment-a-systematic-revie/?utm_source=chatgpt.com "a systematic review on approaches, tools, challenges and ..."
[11]: https://research.monash.edu/en/publications/beyond-continuous-delivery-an-empirical-investigation-of-continuo/?utm_source=chatgpt.com "an empirical investigation of continuous deployment challenges"
[12]: https://www.sciencedirect.com/science/article/abs/pii/S0950584921001543?utm_source=chatgpt.com "Challenges and solutions when adopting DevSecOps"
[13]: https://onlinelibrary.wiley.com/doi/10.1002/smr.70029?utm_source=chatgpt.com "Integrating Security Controls in DevSecOps: Challenges ..."
[14]: https://www.ifi.uzh.ch/en/hasel/people/fritz/publications.html "Publications | Department of Informatics  | UZH"


## Welche Zielkonflikte bestehen zwischen Standardisierung, Sicherheits- und Compliance-Anforderungen sowie der notwendigen Flexibilität für unterschiedliche Entwicklungsteams?

## Zielkonflikte zwischen Standardisierung, Sicherheits-/Compliance-Anforderungen und teambezogener Flexibilität (Status quo und wissenschaftliche Einordnung)

Zielkonflikte entstehen, weil interne Plattformen und Delivery-Prozesse gleichzeitig (a) **Wiederholbarkeit/Beherrschbarkeit** (Standardisierung), (b) **Risikoreduktion und Nachweisbarkeit** (Security & Compliance) und (c) **Domänen- und Teamheterogenität** (Flexibilität) optimieren sollen. Empirische und systematische Arbeiten zeigen dabei wiederkehrende Spannungsfelder, insbesondere dort, wo Sicherheitskontrollen und Prozessstandardisierung direkt in CI/CD- und IaC-Flüsse eingebettet werden. ([ScienceDirect][1])

---

## 1) Standardisierung vs. Flexibilität: „One size fits all“ gegen Domänen- und Teamvarianz

### 1.1 Mechanismus des Konflikts

Standardisierung in Delivery-Prozessen (z. B. einheitliche Pipeline-Templates, IaC-Module, standardisierte Deployment-Taktiken) reduziert Varianz und erhöht Vorhersagbarkeit, aber sie kollidiert mit der Realität, dass Teams **unterschiedliche Systeme, Risikoexpositionen, Reifegrade und nicht-funktionale Anforderungen** haben. Systematische Reviews zu Continuous Delivery berichten, dass CD-Adoption gerade an solchen Unterschieden scheitern kann (u. a. Testbarkeit, Architekturvoraussetzungen, Tooling-Integration und organisatorische Faktoren). ([ScienceDirect][2])

### 1.2 Typische Ausprägungen

* **Pipeline-Standard vs. Spezialfälle:** Teams mit besonderen Build-/Test-Anforderungen (z. B. sehr lange Integrationstests, regulierte Validierungen) erleben Standardpipelines als unzureichend oder als Zwang zur Workaround-Engineering. (CD-Adoptionsprobleme: Testing/Architektur/Tooling). ([ScienceDirect][2])
* **Architekturkopplung:** Standardisierte Deployability-Mechanismen setzen bestimmte Architekturentscheidungen voraus. Bellomo et al. zeigen empirisch, dass Deployability-Ziele und -Taktiken stark von Architekturentscheidungen abhängen; Standardisierung kann hier entweder helfen (durch Taktik-Kataloge) oder Teams blockieren, wenn sie nicht zur Systemarchitektur passt. ([ACM Digital Library][3])
* **Microservices/Plattform-Paradox:** Heterogene, teamautonome Microservice-Landschaften erzeugen zusätzliche „Pains“ (Komplexität, Betriebsaufwand, Inkonsistenzen). Eine Industrie-Interviewstudie zu Microservices beschreibt explizit die Lücke zwischen Idealvorstellung und realen Kosten/Pains in Unternehmen – was oft zu nachträglicher Standardisierung (Platform Guardrails) führt. ([ScienceDirect][4])

**Kernzielkonflikt:** Mehr Standardisierung senkt Koordinations- und Betriebsrisiko, aber verringert die lokale Optimierbarkeit; mehr Flexibilität erhöht Passung je Team, aber steigert System- und Governance-Komplexität. ([ScienceDirect][2])

---

## 2) Security/Compliance vs. Delivery-Flexibilität: Kontrollen erzeugen Friktion und Varianzbegrenzung

### 2.1 Mechanismus des Konflikts

Die Integration von Security in schnelle Delivery-Zyklen (DevSecOps) erfordert **automatisierte Kontrollen** (Scanning, Policy Gates, Attestationen, SBOM/Provenance), die unmittelbar in Build/Deploy-Flüsse eingreifen. Systematische Evidenz zeigt, dass Praktiker genau hier einen zentralen Konflikt erleben: das **Ausbalancieren von Liefergeschwindigkeit/Agilität und Security**. Die DevSecOps-SLR von Rajapakse et al. identifiziert „Tool“- und Automationsherausforderungen als häufigsten Themenbereich und hebt die Balance „speed vs. security“ als signifikantes Praxisproblem hervor. ([arXiv][5])

### 2.2 Typische Ausprägungen

* **„Gates“ vs. Autonomie:** Je mehr Security- und Compliance-Gates zentral vorgeschrieben sind, desto weniger können Teams ihre Pipeline frei variieren (z. B. alternative Scanner, abweichende Release-Strategien). Diese Einschränkung wird in DevSecOps-Literatur als wiederkehrende Adoptionshürde beschrieben, insbesondere wenn Tools schwer integrierbar sind oder Befunde nicht „developer-centered“/handlungsleitend aufbereitet werden. ([arXiv][5])
* **False Positives und Triage-Aufwand:** Security-Checks können DX belasten, wenn Findings hohe Nacharbeit und Abstimmung erfordern. Der SLR-Befund, dass toolbezogene Herausforderungen dominieren, ist konsistent mit dem bekannten Muster „kontrollbedingte Zusatzarbeit“ (Triage/Remediation) als Reibung im Delivery-Fluss. ([arXiv][5])
* **IaC-Sicherheit als zusätzlicher Kontrollraum:** Rahman/Parnin/Williams identifizieren empirisch „Security Smells“ in IaC-Skripten und implementieren ein Werkzeug (SLIC) zur Erkennung. Solche Befunde stützen die Notwendigkeit, IaC-spezifische Kontrollen in Plattformpipelines einzubauen – erhöhen aber zugleich die Zahl der Policy-/Check-Punkte (und damit potenzielle Friktion), sofern sie nicht gut in Entwickler-Workflows integriert sind. ([Akond Rahman][6])

### 2.3 Compliance-spezifische Zuspitzung: Nachweisbarkeit und Supply-Chain-Artefakte

Compliance-Anforderungen verlangen häufig **Auditierbarkeit** und **formale Nachweise** (z. B. Attestationen, Provenance, SBOM). NIST SP 800-204D (2024) beschreibt explizit Strategien zur Integration von Software-Supply-Chain-Sicherungsmaßnahmen in CI/CD-Pipelines (u. a. über Attestationen und Provenance-Artefakte). Diese Nachweisartefakte erhöhen Standardisierungsdruck (einheitliche Artefaktformate/Prozesse) und können Flexibilität einschränken, insbesondere wenn Teams unterschiedliche Toolchains nutzen. ([nvlpubs.nist.gov][7])

**Kernzielkonflikt:** Security/Compliance erhöhen Kontrolltiefe und Nachweislast, was ohne sorgfältige Plattformgestaltung zu längeren Feedbackzyklen, mehr Triage-Aufwand und weniger Pipeline-Freiheit führt. ([arXiv][5])

---

## 3) Standardisierung vs. Security: Reduzierte Varianz hilft – zentrale Plattformen werden Hochwertziele

### 3.1 Synergie – und ihr Preis

Standardisierung kann Security verbessern, weil sie die Angriffsfläche durch unkontrollierte Tool- und Prozessdiversität reduziert und „best known practices“ reproduzierbar macht (z. B. einheitliche Policy Gates, definierte Secrets-/Signing-Prozesse). Genau deshalb empfiehlt die DevSecOps-SLR „shift-left“ und kontinuierliche Sicherheitsbewertung als wiederkehrende Praxis. ([arXiv][5])

### 3.2 Konflikt: Zentralisierung als Risiko- und Governance-Hotspot

Gleichzeitig wird eine stark standardisierte IDP (zentrale Pipeline, zentrale Artefakt-Registries, zentrale Policy Engines) selbst zum **hochattraktiven Angriffsziel**, sodass Security-Anforderungen an die Plattform **strenger** werden (Härtung der CI/CD-Infrastruktur, Zugriffskontrollen, Supply-Chain-Sicherung). NIST SP 800-204D fokussiert genau auf die Absicherung von Pipeline-Aktivitäten und Artefakten gegen Kompromittierung; das erhöht die Zahl verpflichtender Sicherheitsmaßnahmen und kann wiederum Teamflexibilität einschränken (z. B. weniger frei wählbare Buildumgebungen, strengere Signing-/Provenance-Prozesse). ([nvlpubs.nist.gov][7])

**Kernzielkonflikt:** Standardisierung ist sicherheitsförderlich (weniger Varianz), kann aber die Plattform zu einem „Single Point of High Value“ machen, wodurch zusätzliche Controls nötig werden, die Flexibilität und Geschwindigkeit beeinflussen. ([nvlpubs.nist.gov][7])

---

## 4) Heterogene Teamlandschaften: Ein Compliance- und Risikoprofil für alle ist meist ineffizient

Empirische Befunde aus DevSecOps-SLRs betonen, dass Herausforderungen/ Lösungen stark in Themenfelder „People/Practices/Tools/Infrastructure“ streuen. Das spricht gegen uniforme Maßnahmenpakete, wenn Teams unterschiedliche Reifegrade, Systeme und Risiken haben. ([arXiv][5])
Analog zeigt Continuous-Delivery-Adoptionsforschung, dass Probleme und Lösungen je nach Kontext variieren (z. B. Testreife, Architektur). ([ScienceDirect][2])

**Konsequenz als Zielkonflikt:**

* Ein **maximal strenges** globales Compliance-/Security-Regime minimiert Risiko, ist aber für Low-Risk-Teams oft überdimensioniert (DX-/Speed-Kosten).
* Ein **zu flexibles** Regime maximiert Autonomie, erzeugt aber inkonsistente Kontrollen, höhere Auditkosten und schwerere Risikosteuerung. ([arXiv][5])

---

## 5) Plattform-Evolution: Patch-/Policy-Druck vs. Stabilität der Teamschnittstellen

Ein weiterer, häufig unterschätzter Zielkonflikt betrifft die Evolution standardisierter Plattformbausteine:

* Security- und Compliance-Anforderungen erzwingen teils **schnelle Änderungen** (z. B. Tool-Updates, neue Attestations-/Provenance-Anforderungen). ([nvlpubs.nist.gov][7])
* Teams benötigen gleichzeitig **Stabilität** von Schnittstellen (Pipeline-Templates, Deployment-Mechanismen), sonst entstehen Migrationskosten und Stillstand.

Dieser Konflikt ist strukturell verwandt mit dem in der Plattform-/Produktlinienforschung beschriebenen Spannungsfeld zwischen **gemeinsamer Plattform** und **produkt-/teamindividueller Ableitung**: Variabilitätsmanagement dient genau dazu, gemeinsame Kernassets zu pflegen, ohne jede Änderung sofort für alle auszurollen. ([ResearchGate][8])

---

## 6) Literaturbasierte Auflösungsprinzipien („Guardrails statt Handcuffs“)

Die Literatur liefert weniger „ein einziges“ Referenzframework, aber robuste Bausteine, um Zielkonflikte systematisch zu entschärfen:

### 6.1 Kontrollierte Variabilität (Variability Management) statt ad-hoc Ausnahmen

Die Produktlinien-/Plattformforschung etabliert Variabilitätsmanagement als Prinzip: gemeinsame Kernassets + explizite Variationspunkte. Übertragen auf IDPs heißt das: Standardisierung über **Default-Pfade**, Flexibilität über **definierte, begründete Varianten** (z. B. parametrisierte Pipeline-Module, zugelassene Tool-Alternativen, risiko-basierte Policy-Profile). ([ResearchGate][8])

### 6.2 Risiko-/Kontextbasierte Security/Compliance-Profile

Die DevSecOps-SLR betont, dass Balancefragen zentral sind und Tools/Automation die Hauptschmerzpunkte darstellen; daraus folgt als Gestaltungskonsequenz, Kontrollen nicht monolithisch, sondern als **Profile** (z. B. nach Systemkritikalität) umzusetzen und die Entwicklerzentrierung der Tools zu priorisieren. ([arXiv][5])

### 6.3 „Security & Compliance by construction“ in CI/CD

NIST SP 800-204D empfiehlt SSC-Sicherungsmaßnahmen *in* die Pipeline zu integrieren (Artefakte/Attestationen/Provenance). Als Plattformprinzip heißt das: Kontrollen so integrieren, dass sie (a) automatisiert, (b) auditierbar, (c) wiederverwendbar sind – um sowohl Standardisierung als auch Compliance zu bedienen und Teamfreiheit in den nicht-kritischen Dimensionen zu erhalten. ([nvlpubs.nist.gov][7])

### 6.4 Architektur-/Deployability-Taktiken als standardisierte „paved constraints“

Bellomo et al. zeigen, dass Deployability-Taktiken und Designentscheidungen empirisch beobachtbar und entscheidend sind; Plattformen können deshalb Taktiken standardisieren (z. B. Rollback-/Release-Patterns), während Teams innerhalb dieser Leitplanken variieren. ([ACM Digital Library][3])

---

## Verdichtete Antwort (für Masterarbeit direkt zitierfähig)

Die Zielkonflikte zwischen Standardisierung, Security/Compliance und Flexibilität sind strukturell: Standardisierung reduziert Varianz und erleichtert Governance, kollidiert aber mit heterogenen Teamkontexten und architekturabhängigen Deployability-Anforderungen. DevSecOps- und Supply-Chain-Sicherungsmaßnahmen erhöhen Kontrolltiefe und Nachweisartefakte in CI/CD, was ohne plattformseitige Automatisierung und developer-zentrierte Toolintegration zu Friktion, längeren Feedbackzyklen und eingeschränkter Teamautonomie führt. Die Literatur legt nahe, diese Konflikte durch kontrollierte Variabilität (Variability Management), risiko-/kontextbasierte Kontrollprofile sowie standardisierte Deployability- und Security-by-construction-Mechanismen in der Pipeline zu entschärfen. ([ScienceDirect][2])

---

### Zentrale Quellen (Autor, Jahr, Titel, Venue/Verlag)

* Roshan N. Rajapakse; Mansooreh Zahedi; M. Ali Babar; Haifeng Shen (2022): *Challenges and solutions when adopting DevSecOps: A systematic review*. **Information and Software Technology** (Elsevier). ([ScienceDirect][1])
* Eero Laukkanen; Juha Itkonen; Casper Lassenius (2017): *Problems, causes and solutions when adopting continuous delivery—A systematic literature review*. **Information and Software Technology** (Elsevier). ([ScienceDirect][2])
* Akond Rahman; Chris Parnin; Laurie Williams (2019): *The Seven Sins: Security Smells in Infrastructure as Code Scripts*. **IEEE/ACM ICSE 2019**. ([ACM Digital Library][9])
* Stephany Bellomo; Neil Ernst; Robert Nord; Rick Kazman (2014): *Toward Design Decisions to Enable Deployability: Empirical Study of Three Projects Reaching for the Continuous Delivery Holy Grail*. **IEEE/IFIP DSN 2014**. ([ACM Digital Library][3])
* X. Zhou et al. (2023): *Revisiting the practices and pains of microservice architecture in reality: An industrial inquiry*. **Journal of Systems and Software / Elsevier**. ([ScienceDirect][4])
* NIST (2024): *SP 800-204D: Strategies for the Integration of Software Supply Chain Security Measures into CI/CD Pipelines*. **NIST Special Publication**. ([nvlpubs.nist.gov][7])
* Software Product Line Engineering: Foundations, Principles and Techniques, Pohl/Böckle/van der Linden (2005): Variability Management als Plattformprinzip. ([ResearchGate][8])


[1]: https://www.sciencedirect.com/science/article/pii/S0950584921001543?utm_source=chatgpt.com "Challenges and solutions when adopting DevSecOps"
[2]: https://www.sciencedirect.com/science/article/pii/S0950584916302324?utm_source=chatgpt.com "Problems, causes and solutions when adopting continuous ..."
[3]: https://dl.acm.org/doi/10.1109/DSN.2014.104?utm_source=chatgpt.com "Toward Design Decisions to Enable Deployability"
[4]: https://www.sciencedirect.com/science/article/abs/pii/S0164121222001972?utm_source=chatgpt.com "Revisiting the practices and pains of microservice ..."
[5]: https://arxiv.org/abs/2103.08266?utm_source=chatgpt.com "Challenges and solutions when adopting DevSecOps: A systematic review"
[6]: https://akondrahman.github.io/files/papers/icse19_slic.pdf?utm_source=chatgpt.com "Security Smells in Infrastructure as Code Scripts"
[7]: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-204D.pdf?utm_source=chatgpt.com "Strategies for the Integration of Software Supply Chain ..."
[8]: https://www.researchgate.net/publication/325748446_Software_Product_Lines?utm_source=chatgpt.com "(PDF) Software Product Lines"
[9]: https://dl.acm.org/doi/10.1109/ICSE.2019.00033?utm_source=chatgpt.com "The seven sins: security smells in infrastructure as code ..."




## Wie kann ein konzeptionelles und architektonisches Zielbild einer Internen Entwicklerplattform gestaltet werden, das diesen Anforderungen gerecht wird?


Im Folgenden wird ein **konzeptionelles und architektonisches Zielbild** für eine **Interne Entwicklerplattform (IDP)** entwickelt, das **Developer Experience**, **Standardisierung**, **Security/Compliance** und **teambezogene Flexibilität** gleichzeitig adressiert. Die Argumentation stützt sich auf (i) **empirische SE-Literatur** zu Plattformteams, DX, CI/CD, IaC, DevSecOps sowie (ii) **anerkanntes Guidance-Material** zur Supply-Chain-Sicherheit in CI/CD-Pipelines.

---

## 1) Zielbild-Logik: Anforderungen als explizite Entwurfsziele

Ein belastbares IDP-Zielbild muss vier Zielräume gleichzeitig optimieren:

1. **DX als primäres Nutzenkriterium**: DX ist mehrdimensional (kognitiv/affektiv/motivational) und wird wesentlich durch Arbeitsfluss, Friktion, Kontextwechsel und Feedbacklatenz geprägt. ([ACM Digital Library][1])
2. **Standardisierung als Skalierungsmechanismus**: CI/CD-Praktiken sind in der Literatur als Bündel aus Automatisierung, Tooling und Prozessgestaltung beschrieben; Standardisierung wird praktikabel, wenn wiederverwendbare Pipeline-Bausteine/Automationen bereitgestellt werden. ([mediaweb.saintleo.edu][2])
3. **Security/Compliance als integrierte Delivery-Eigenschaft**: DevSecOps-SLRs zeigen wiederkehrende Adoptionshürden (v. a. Tool-/Automationsprobleme) und den Kernkonflikt „Speed vs. Security“. ([ScienceDirect][3])
4. **Flexibilität als kontrollierte Variabilität**: Unterschiedliche Teamkontexte (Systemarchitektur, Risikoprofil, Testbarkeit) verhindern „one size fits all“; CD-Adoption scheitert häufig an Kontextfaktoren (z. B. Testing/Architektur/Tooling). ([Aalto University's research portal][4])

**Designkonsequenz:** Das Zielbild muss *gleichzeitig* (a) **standardisierte Default-Wege** („paved road“) bereitstellen, (b) **Variationspunkte** definieren (statt ad-hoc Ausnahmen), und (c) **Sicherheits-/Compliance-Kontrollen** so integrieren, dass sie **automatisiert, entwicklerzentriert und nachweisbar** sind. ([ScienceDirect][3])

---

## 2) Konzeptionelles Zielbild: IDP als soziotechnisches Produkt mit klaren Verträgen

### 2.1 Operating Model: Plattformteam + Serviceverträge

Empirisch ist „Platform Team“ als Organisationsstruktur im Continuous-Delivery-Kontext beschrieben; Plattformteams bündeln hochautomatisierte Infrastruktur-/Delivery-Services und stellen sie als wiederverwendbare Fähigkeiten bereit. ([ACM Digital Library][5])
Daraus folgt: Eine IDP ist **nicht** primär ein Portal, sondern ein **Service- und Verantwortungsmodell** (Ownership, SLOs, Roadmap, Supportpfade).

**Zielbild-Entscheidung:**

* **Plattformteam** verantwortet: Plattform-Backlog, Golden Paths, Templates/Module, Plattform-Security, Plattform-Observability, Run-/Operate-Model. ([INCT | Interscity][6])
* **Produktteams** verantworten: Produktcode, domänenspezifische Architektur, Nutzung der Plattformservices, risiko-/domänenspezifische Zusatzanforderungen (innerhalb definierter Variationspunkte). ([Aalto University's research portal][4])

### 2.2 Produktkontrakte statt Tooling-Sammlung

Das Zielbild muss **explizite Kontrakte** definieren, z. B.:

* „Wie deploye ich?“ (Deployment Contract)
* „Wie bekomme ich Runtime-Feedback?“ (Observability Contract)
* „Wie beweise ich Compliance?“ (Evidence/Attestation Contract)

Diese Kontrakte sind notwendig, weil DevSecOps- und Supply-Chain-Guidance explizit fordert, SSC-Sicherungsmaßnahmen in CI/CD-Operationen und Artefakte einzubetten. ([nvlpubs.nist.gov][7])

---

## 3) Architektonisches Zielbild: Referenzarchitektur einer IDP

### 3.1 Logische Schichten (View)

Ein wissenschaftlich gut begründbares Zielbild lässt sich als **Control-Plane / Data-Plane** plus **Developer-Experience-Layer** modellieren (analytisch nützlich, technologieagnostisch):

```
(1) Developer Experience Layer
    - Portal/CLI/API, Katalog, Golden Paths, Dokumentation
    - Authn/Authz-Frontend, Developer Feedback (Status, Findings)

(2) Platform Control Plane
    - Orchestrierung: Provisioning, Deployments, Policies, Workflows
    - Policy-as-Code / Compliance-as-Code (Regeln, Ausnahmen, Profile)
    - Software Supply Chain: Signierung, Provenance, Attestations, SBOM-Flows
    - Template/Blueprint Registry (Pipelines, IaC-Module, Service Scaffolding)
    - Identity & Access: RBAC/ABAC, Least Privilege, Secrets Broker

(3) Platform Data Plane
    - Runtime/Execution: Build/Test Runners, Deployment Controller, Environments
    - Shared Runtime Services: Logging/Tracing/Metrics, Artifact Store, Config
    - Incident/Change Interfaces, Rollback/Release Mechanismen
```

**Begründung aus Literatur:**

* CI/CD wird als „continuous practices“-Bündel mit starker Betonung von Automatisierung und Tool-/Prozessintegration beschrieben; daher ist eine Orchestrierungs-/Automationsebene („control plane“) zentral. ([Monash University][8])
* IaC ist als Kernpfeiler von DevOps/Delivery-Automatisierung kartiert und liefert die Grundlage, Infrastruktur/Policies versioniert und reproduzierbar zu machen. ([ScienceDirect][9])
* GitOps wird als Ansatz diskutiert, der deklarative Zustände über Git und Reconciling-Mechanismen in Laufzeit überführt; dies passt als Deployment-/Operationsmuster in die Data-Plane (Controller) und die Control-Plane (Desired State). ([ACM Digital Library][10])
* Supply-Chain-Guidance fordert explizit SSC-Sicherungsmaßnahmen in CI/CD-Pipelines (Artefakte, Nachweise, Integrationsstrategien), womit „Evidence/Attestation“ eine eigene Plattformdomäne wird. ([nvlpubs.nist.gov][7])

### 3.2 Kernkomponenten im Zielbild (technisch konkret, aber technologieoffen)

#### A) Golden Paths als composable Templates

**Definition im Zielbild:** Golden Paths sind versionierte, wiederverwendbare **Scaffolds** (Service-Skeleton + Pipeline + IaC-Module + Observability Defaults).
**Warum:** DX-Forschung zeigt, dass DX durch Friktion/Barrieren und Kontextbedingungen beeinflusst wird; standardisierte Pfade reduzieren kognitive Last und Integrationsaufwand. ([ACM Digital Library][1])

#### B) Pipeline-as-Code + Policy-as-Code

**Zielbild:**

* Pipeline-Templates (Build/Test/Deploy) sind zentral kuratiert, aber parametrisierbar.
* Policies (Security/Compliance) sind **als Code** versioniert, auswertbar und mit Ausnahmeregeln (Justification, Expiry) versehen.

**Warum:**

* DevSecOps-SLR: Tool-/Automation ist häufigster Problembereich; developer-zentrierte, integrierte Kontrollen sind ein Schlüsselbedarf. ([ScienceDirect][3])
* NIST-Guidance: SSC-Sicherungsmaßnahmen sollen in CI/CD integriert werden (Strategien/Artefakte), was Policy/Evidence-Automation erfordert. ([nvlpubs.nist.gov][7])

#### C) IaC-Module mit Qualitäts- und Security-Checks

**Zielbild:** Infrastruktur wird über kuratierte IaC-Module bereitgestellt; Plattform integriert IaC-Tests/Scanner.
**Warum:** IaC-Forschung zeigt Sicherheitsdefizite („security smells“) und Bedarf an systematischer Qualitätssicherung. ([Akond Rahman][11])

#### D) Deployability-Taktiken als Plattformbausteine

Das Zielbild muss Deployment-Mechanismen (Rollback/Canary/Blue-Green, DB-Migrationspfade, Feature Toggles) als **wiederverwendbare Taktiken** anbieten.
**Warum:** Empirische Architekturarbeit zeigt, dass Deployability-Ziele stark von Architekturentscheidungen und „deployability tactics“ abhängen; ohne standardisierte Taktiken entstehen Zielkonflikte und technische Schuld. ([ACM Digital Library][12])

---

## 4) Standardisierung und Flexibilität im Zielbild: kontrollierte Variabilität statt Ausnahmewildwuchs

### 4.1 Variability-Mechanismen (Designprinzip)

Da CD/DevSecOps-Literatur kontextabhängige Probleme betont, muss das Zielbild explizite Variationspunkte definieren (statt harte Uniformität). ([Aalto University's research portal][4])
Ein theoretisch belastbarer Anker ist **Variabilitätsmanagement** aus der Plattform-/Produktlinienforschung: gemeinsame Kernassets + definierte Variationspunkte. ([Springer][13])

### 4.2 Konkrete Umsetzung im Zielbild

* **Policy-Profile nach Risikoklasse:** z. B. „Standard“, „High-Risk/Regulated“ mit zusätzlichen Kontrollen und Nachweisartefakten. (Begründung: Balance „speed vs security“ als zentraler Praxis-/Forschungsbefund.) ([ScienceDirect][3])
* **Pipeline-Varianten als genehmigte Module:** z. B. optionale Stufen für Performance-/Integrationstests; Variation ist deklarativ, auditierbar. (Begründung: CD-Adoptionsprobleme sind stark testing-/tooling-getrieben.) ([Aalto University's research portal][4])
* **Plug-in-Architektur für Tooling**: Scanner/Runner/Deploy-Controller über standardisierte Schnittstellen austauschbar, während Kontrakte stabil bleiben. (Begründung: Tool-Heterogenität ist ein wiederkehrender DevSecOps-Pain Point.) ([ScienceDirect][3])

---

## 5) Security- und Compliance-Zielbild: „Evidence by construction“

### 5.1 Supply-Chain-Sicherheit als Plattformdomäne

Ein modernes IDP-Zielbild sollte Supply-Chain-Mechanismen als **first-class** behandeln: Artefaktintegrität, Provenance/Attestations, gesicherte Pipeline-Schritte. NIST SP 800-204D beschreibt Strategien zur Integration solcher SSC-Maßnahmen in CI/CD. ([nvlpubs.nist.gov][7])

### 5.2 Praktikable Leitplanken (aus SLR-Befunden abgeleitet)

* **Kontrollen früh, automatisiert und entwicklerzentriert** (Actionability, geringe False-Positive-Last), da Tool-Challenges dominieren. ([ScienceDirect][3])
* **Standardisierte Nachweise** (evidence artifacts) statt manueller Audit-Workflows, weil manuelle Praktiken schwer mit schnellen Deploymentzyklen vereinbar sind. ([arXiv][14])
* **IaC-Security als Default-Gate** (Smell-Kataloge/Scanner als Plattformservice). ([Akond Rahman][11])

---

## 6) DX-wirksame Gestaltung des Zielbilds: Messbarkeit und Feedback als Architekturprinzip

Da DX als mehrdimensionales Konstrukt modelliert ist, muss das Zielbild DX-Wirkung **beobachtbar** machen:

* **Feedbacklatenz-Reduktion** (Pipeline-Dauer, Warteschlangen),
* **Stabilität** (Fehlerraten, Flakiness-Indikatoren),
* **Friction-Signale** (z. B. wiederkehrende Gate-Fails, häufige Ausnahme-Requests).

Diese Ausrichtung ist konsistent mit dem DX-Framework (Barriers, Strategies, Kontextcharakteristika) und der CI/CD-Literatur, die Feedback und Automatisierung als zentrale Hebel beschreibt. ([ACM Digital Library][1])

---

## 7) Ergebnis: Zielbild in komprimierter Form (für Masterarbeit)

**Ein tragfähiges konzeptionelles und architektonisches Zielbild** einer Internen Entwicklerplattform ist eine soziotechnische Plattform „als Produkt“, betrieben durch ein Plattformteam, die standardisierte „Golden Paths“ (Service-Scaffolding + Pipeline-Templates + IaC-Module + Observability Defaults) bereitstellt und über eine Control-Plane orchestriert. Standardisierung wird über versionierte Templates/Module und Policy-as-Code implementiert, Flexibilität über kontrollierte Variabilität (genehmigte Varianten, risikobasierte Policy-Profile). Security/Compliance werden als „Evidence by construction“ umgesetzt, indem Supply-Chain-Maßnahmen (Provenance/Attestations/Artefaktintegrität) und IaC-Security-Checks automatisiert in CI/CD integriert sind. Diese Architektur adressiert die in SLRs beschriebenen Adoptionshürden (Tool-Integration, Balance Speed vs Security) und die empirisch belegte Relevanz von Plattformteams, Deployability-Taktiken und IaC-Qualität/Sicherheit. ([INCT | Interscity][6])

---

## Quellen (Auswahl; Autor, Jahr, Titel, Venue/Verlag)

* Leonardo Leite; Fabio Kon; Gustavo Pinto; Paulo Meirelles (2020): *Platform Teams: An Organizational Structure for Continuous Delivery.* IEEE/ACM ICSE Workshops (ICSEW), ACM. ([ACM Digital Library][5])
* Michaela Greiler; Margaret-Anne Storey; Abi Noda (2023): *An Actionable Framework for Understanding and Improving Developer Experience.* IEEE Transactions on Software Engineering. ([ACM Digital Library][1])
* Mojtaba Shahin; Muhammad Ali Babar; Liming Zhu (2017): *Continuous Integration, Delivery and Deployment: A Systematic Review on Approaches, Tools, Challenges and Practices.* IEEE Access. ([mediaweb.saintleo.edu][2])
* Akond Rahman; Rezvan Mahdavi-Hezaveh; Laurie Williams (2019): *A Systematic Mapping Study of Infrastructure as Code Research.* Information and Software Technology (Elsevier). ([ScienceDirect][9])
* Chris Parnin (mit Rahman & Williams) (2019): *The Seven Sins: Security Smells in Infrastructure as Code Scripts.* IEEE/ACM ICSE 2019. ([ACM Digital Library][15])
* Roshan N. Rajapakse; Mansooreh Zahedi; (mit Babar & Shen) (2022): *Challenges and solutions when adopting DevSecOps: A systematic review.* Information and Software Technology (Elsevier). ([ScienceDirect][3])
* NIST; R. Chandramouli (2024): *SP 800-204D: Strategies for the Integration of Software Supply Chain Security Measures into CI/CD Pipelines.* NIST Special Publication. ([nvlpubs.nist.gov][7])
* Florian Beetz; Simon Harrer (2022): *GitOps: The Evolution of DevOps?* IEEE Software. ([ACM Digital Library][10])
* Stephany Bellomo; Neil A. Ernst; Robert L. Nord; Rick Kazman (2014): *Toward Design Decisions to Enable Deployability…* IEEE/IFIP DSN 2014. ([ACM Digital Library][12])
* Klaus Pohl; Günter Böckle; Frank J. van der Linden (2005): *Software Product Line Engineering: Foundations, Principles and Techniques.* Springer. ([Springer][13])

---


[1]: https://dl.acm.org/doi/10.1109/TSE.2022.3175660?utm_source=chatgpt.com "An Actionable Framework for Understanding and ..."
[2]: https://mediaweb.saintleo.edu/Courses/COM430/M8Readings/Continuous%20Integration%2C%20Delivery%20and%20Deployment.pdf?utm_source=chatgpt.com "Continuous Integration, Delivery and Deployment"
[3]: https://www.sciencedirect.com/science/article/abs/pii/S0950584921001543?utm_source=chatgpt.com "Challenges and solutions when adopting DevSecOps"
[4]: https://research.aalto.fi/en/publications/problems-causes-and-solutions-when-adopting-continuous-delivery-a/?utm_source=chatgpt.com "Problems, Causes and Solutions When Adopting ..."
[5]: https://dl.acm.org/doi/10.1145/3387940.3391455?utm_source=chatgpt.com "Platform Teams | Proceedings of the IEEE/ACM 42nd ..."
[6]: https://interscity.org/assets/platform-teams-Leite2020.pdf?utm_source=chatgpt.com "Platform Teams: An Organizational Structure for ..."
[7]: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-204D.pdf?utm_source=chatgpt.com "Strategies for the Integration of Software Supply Chain ..."
[8]: https://research.monash.edu/en/publications/continuous-integration-delivery-and-deployment-a-systematic-revie/?utm_source=chatgpt.com "a systematic review on approaches, tools, challenges and ..."
[9]: https://www.sciencedirect.com/science/article/abs/pii/S0950584918302507?utm_source=chatgpt.com "A systematic mapping study of infrastructure as code ..."
[10]: https://dl.acm.org/doi/10.1109/MS.2021.3119106?utm_source=chatgpt.com "GitOps: The Evolution of DevOps? | IEEE Software"
[11]: https://akondrahman.github.io/files/papers/icse19_slic.pdf?utm_source=chatgpt.com "Security Smells in Infrastructure as Code Scripts"
[12]: https://dl.acm.org/doi/10.1109/DSN.2014.104?utm_source=chatgpt.com "Toward Design Decisions to Enable Deployability"
[13]: https://link.springer.com/book/10.1007/3-540-28901-1?utm_source=chatgpt.com "Software Product Line Engineering - Springer Link"
[14]: https://arxiv.org/abs/2103.08266?utm_source=chatgpt.com "Challenges and solutions when adopting DevSecOps: A systematic review"
[15]: https://dl.acm.org/doi/10.1109/ICSE.2019.00033?utm_source=chatgpt.com "The seven sins: security smells in infrastructure as code ..."

______________________________________



---

# Masterarbeit

## Titel

**Analyse und Konzeption einer internen Entwicklungsplattform (IDP) zur Verbesserung der Entwicklererfahrung im Kontext eines modernen Plattform-Engineering-Ansatzes mit prototypischer Validierung**

---

## 1. Einleitung

### 1.1 Motivation

Softwareentwicklung in Organisationen mit mehreren Teams ist zunehmend durch heterogene Toolchains, cloud-native Laufzeitumgebungen und komplexe Lieferketten geprägt. In der Forschung zu Continuous Integration und Continuous Delivery wird seit Jahren beschrieben, dass kurze Feedbackzyklen, Automatisierung und reproduzierbare Bereitstellung zentrale Voraussetzungen für schnelle und zugleich zuverlässige Lieferung sind (Humble & Farley, 2010; Shahin et al., 2017). Gleichzeitig zeigen empirische Studien, dass der Weg dorthin in der Praxis häufig durch Testing-Engpässe, Systemdesign-Restriktionen, Integrationsaufwand sowie organisatorische Faktoren gebremst wird (Laukkanen et al., 2017). Aus Sicht der Teams entstehen dabei Reibungen, die nicht nur Lieferfähigkeit, sondern auch die wahrgenommene Qualität des Arbeitsalltags beeinflussen.

In den letzten Jahren wird Developer Experience (DX) in der empirischen Softwaretechnik expliziter als eigenständiges Untersuchungsobjekt modelliert. DX wird dabei nicht auf „Zufriedenheit“ reduziert, sondern als Zusammenspiel kognitiver, affektiver und motivationaler Aspekte verstanden, die durch Arbeitskontext, Barrieren und Strategien geprägt werden (Fagerholm & Münch, 2012; Greiler et al., 2023). Ergänzend zeigt Produktivitätsforschung, dass Entwicklerinnen und Entwickler produktive Tage mit Fortschritt, niedrigen Unterbrechungen und geringer Kontextwechselrate verbinden (Meyer et al., 2014; Meyer et al., 2017). Wenn Tooling, Deployments oder Sicherheitsprüfungen zu häufigen Unterbrechungen und unsicheren Feedbacksignalen führen, ist plausibel, dass dies DX negativ beeinflusst.

Ein Ansatz, der in Industrie und Forschung als Antwort auf Skalierungsprobleme rund um DevOps-Praktiken diskutiert wird, ist die organisatorische und technische Bündelung von wiederverwendbaren Plattformfähigkeiten. Leite et al. (2020) beschreiben „Platform Teams“ als Organisationsmuster im Kontext kontinuierlicher Lieferung, bei dem ein Plattformteam nicht-funktionale Belange und Delivery-Fähigkeiten zentral kuratiert, während Produktteams geschäftsnahe Services verantworten. Dieses Muster lässt sich in Richtung einer internen Entwicklungsplattform (Internal Developer Platform, IDP) weiterdenken: als integriertes Angebot aus Self-Service-Funktionen, standardisierten „Golden Paths“ und kontrollierter Flexibilität.

### 1.2 Problemstellung

Trotz verbreiteter CI/CD-Nutzung bestehen in vielen Organisationen Spannungen zwischen Standardisierung, Sicherheit/Compliance und der notwendigen Autonomie unterschiedlicher Teams. Der Stand der Forschung zu Continuous Delivery deutet darauf hin, dass Adoptionsprobleme häufig in Bereichen wie Testing, Integration und Systemdesign konzentriert sind (Laukkanen et al., 2017). Zusätzlich zeigen empirische Untersuchungen zu CI-Builds, dass Build-Dauern und Build-Fehler reale Produktivitätskosten erzeugen: Lange CI-Builds werden in großen Datensätzen beobachtet und mit Projektmerkmalen in Verbindung gebracht (Ghaleb et al., 2019), während Build-Fehler in CI-Workflows häufig auf Testfehler, Qualitätsgates oder Infrastrukturprobleme zurückgehen und sich in Fehlerhistorien sogar „fortpflanzen“ können (Rausch et al., 2017). Testzuverlässigkeit ist ebenfalls ein relevanter Faktor: Flaky Tests werden als praxisrelevantes Problem beschrieben, dessen Diagnose und Reproduzierbarkeit Entwickler stark belastet (Eck et al., 2019; Parry et al., 2021).

Für moderne Plattformansätze verschärft sich die Situation durch Supply-Chain-Risiken und steigende Sicherheitsanforderungen. Empirische Arbeiten zeigen, dass SBOMs als Transparenzinstrument in der Supply-Chain als wichtig eingeschätzt werden, die Einführung aber mit Hürden verbunden ist, u. a. hinsichtlich Aufwand, Datennutzung und organisatorischer Einbettung (Xia et al., 2023). Stakeholder-Studien deuten zudem darauf hin, dass Erwartungen an SBOMs heterogen sind und sich in der Praxis Spannungen zwischen Nutzen, Verantwortlichkeiten und Umsetzbarkeit ergeben (Stalnaker et al., 2024). Damit wird Sicherheit nicht nur eine zusätzliche Pipeline-Stufe, sondern ein Governance- und Prozessproblem.

### 1.3 Zielsetzung

Ziel dieser Arbeit ist es, **eine Interne Entwicklungsplattform (IDP) konzeptionell und architektonisch so zu gestalten**, dass sie **Developer Experience verbessert** und gleichzeitig **Standardisierung, Sicherheits-/Compliance-Bedarfe und Flexibilität** in einer praxisnahen Softwareumgebung ausbalanciert. Der Fokus liegt auf einer FH-typischen Verbindung aus wissenschaftlicher Fundierung und pragmatischer Umsetzbarkeit: Aus Literatur wird ein Zielbild abgeleitet, in Anforderungen überführt und in einem Prototypen als Machbarkeitsnachweis konkretisiert. Die Validierung erfolgt prototypisch im Sinne einer nachweisbaren Realisierbarkeit zentraler Funktionen und einer methodisch geplanten Evaluation, die an etablierte Messansätze anschließt (Wohlin et al., 2012; Rüegger et al., 2024).

### 1.4 Forschungsfragen

**Hauptforschungsfrage:**
Wie kann eine interne Entwicklungsplattform (IDP) gestaltet werden, um die Entwicklererfahrung im Rahmen eines modernen Plattform-Engineering-Ansatzes an einer praxisnahen Softwareumgebung zu verbessern?

**Unterfragen:**

1. Welche typischen Herausforderungen bestehen im Entwicklungsalltag moderner Softwareteams?
2. Welche Plattform-Engineering-Prinzipien sind wissenschaftlich etabliert?
3. Wie wird Developer Experience definiert und messbar gemacht?
4. Welche Architekturentscheidungen sind für eine IDP geeignet?
5. Wie kann eine IDP prototypisch umgesetzt werden?
6. Wie lässt sich deren Nutzen empirisch evaluieren?

### 1.5 Aufbau der Arbeit

Kapitel 2 legt theoretische Grundlagen zu DevOps/Platform Engineering, IDPs und DX. Kapitel 3 fasst den Forschungsstand zusammen und leitet Forschungslücken ab. Kapitel 4 beschreibt Methodik und Forschungsdesign. Kapitel 5 führt eine Anforderungsanalyse durch. Kapitel 6 entwickelt die IDP-Konzeption mit begründeten Architekturentscheidungen. Kapitel 7 beschreibt eine prototypische Umsetzung. Kapitel 8 skizziert Evaluation und berichtet prototypische Validierungsergebnisse als nachvollziehbaren Machbarkeitsnachweis. Kapitel 9 diskutiert die Forschungsfragen und Limitationen. Kapitel 10 schließt mit Fazit und Ausblick.

---

## 2. Theoretische Grundlagen

### 2.1 DevOps und Platform Engineering

#### 2.1.1 DevOps als Praktikenbündel und architekturrelevanter Kontext

DevOps wird in der Literatur häufig als Bündel von Praktiken verstanden, das die Zeit zwischen Codeänderung und produktivem Betrieb verkürzen soll, ohne Qualität zu opfern. Bass et al. (2015) betonen dabei die Perspektive der Softwarearchitektur: Automatisierung, Monitoring/Feedback und eine organisationsübergreifende Verantwortung werden nicht als reine Tool-Frage, sondern als strukturelle Voraussetzung für verlässliche Lieferung beschrieben. Humble und Farley (2010) liefern mit Continuous Delivery ein etabliertes Referenzwerk, das technische Praktiken (Build-, Test- und Deployment-Automatisierung) als Fundament sieht, um Software in einem jederzeit release-fähigen Zustand zu halten. Systematische Reviews ordnen die Praktiken ein und zeigen zugleich, dass in der Praxis Tooling, Integration und organisatorische Abstimmungen maßgebliche Einflussfaktoren sind (Shahin et al., 2017).

Für diese Arbeit ist relevant, dass DevOps in empirischen Studien nicht als vollständig standardisierbares Rezept erscheint. Vielmehr hängt die Umsetzbarkeit von Kontextfaktoren ab, z. B. Testbarkeit, Systemarchitektur und Reifegrad der Toolchain (Laukkanen et al., 2017). Damit entsteht eine rationale Begründung für Plattformdenken: Wenn wiederkehrende Delivery-Fähigkeiten organisationsweit benötigt werden, liegt es nahe, sie als geteilte Infrastruktur- und Prozessbausteine bereitzustellen.

#### 2.1.2 Platform Engineering und Plattformteams als empirisch beobachtetes Muster

Platform Engineering wird in dieser Arbeit als Weiterentwicklung der DevOps-Idee verstanden, bei der **Plattformfähigkeiten** (z. B. Provisionierung, Deployments, Observability, Security-Gates) in einem dedizierten Produkt organisiert und für Entwicklungsteams als Self-Service bereitgestellt werden. Ein empirischer Anker hierfür sind die Arbeiten von Leite et al. (2020), die mittels Grounded-Theory-Ansatz Organisationsstrukturen bei Continuous-Delivery-Bestrebungen untersuchen und Plattformteams als eigenständiges Muster beschreiben. Das Plattformteam adressiert nicht-funktionale Themen und reduziert damit Belastungen der Produktteams, während diese weiterhin die Verantwortung für Business-Services tragen. Wichtig ist: In der Studie ist die Plattformteam-Struktur keine rein technische „Shared Services“-Abteilung, sondern mit Engineering-Kompetenz, operativer Verantwortung und Serviceorientierung verbunden (Leite et al., 2020). Für ein IDP-Zielbild bedeutet das, dass technische Architekturentscheidungen eng mit einem Operating Model (Ownership, Schnittstellen, Support) verknüpft sein müssen.

### 2.2 Interne Entwicklungsplattformen (IDP)

#### 2.2.1 Begriffliche Einordnung

Eine IDP wird in dieser Arbeit nicht als einzelnes Portal verstanden, sondern als **integriertes Angebot aus Plattformservices, standardisierten Entwicklungswegen und Schnittstellen**, über das Teams wiederkehrende Tätigkeiten (z. B. Service-Scaffolding, Deployment-Konfiguration, Observability-Anbindung) konsistent durchführen können. Die Forschung liefert hierfür eher indirekte, aber belastbare Bausteine: Plattformteams (Leite et al., 2020) als Organisationsform, GitOps-Ansätze als deklaratives Deploymentschema (Beetz & Harrer, 2022) sowie empirische Arbeiten zu interner Entwicklerinfrastruktur bei großen Organisationen. Beispielsweise beschreiben Sadowski et al. (2015) mit „Tricorder“ eine interne Program-Analysis-Plattform bei Google, inklusive Prinzipien, skalierbarer Architektur und in-situ Evaluation. Obwohl Tricorder nicht als IDP im heutigen Sprachgebrauch positioniert ist, ist die Arbeit relevant, weil sie zeigt, dass interne Plattformen als produktisierte Infrastruktur die Nutzung von Tools, die Qualität von Feedback und die Akzeptanz durch Entwickler systematisch beeinflussen können (Sadowski et al., 2015). Diese Perspektive stützt die Annahme, dass eine IDP als soziotechnisches System betrachtet werden sollte.

#### 2.2.2 Architekturrelevante Eigenschaften

Aus Sicht der Softwaretechnik sind für eine IDP besonders drei Eigenschaften wichtig:

1. **Reproduzierbarkeit und Automatisierbarkeit**: CI/CD und Infrastructure as Code gelten als zentrale Enabler schneller Lieferung. Rahman et al. (2019) kartieren IaC-Forschung systematisch und zeigen, dass IaC sowohl als Tooling-Praxis als auch als Forschungsfeld stark wächst und eng mit DevOps-Zielen verbunden ist. Damit wird IaC für IDPs ein naheliegender Baustein, um Standardisierung technisch zu verankern.

2. **Deployability als architekturabhängiges Qualitätsziel**: Bellomo et al. (2014) zeigen in einer empirischen Studie, dass Deployability-Ziele und Architekturentscheidungen zusammenhängen und konflikthafte Entscheidungen technische Schuld erzeugen können. Ein IDP-Zielbild muss daher nicht nur Deployments ausführen, sondern auch Architektur-Taktiken (z. B. isolierte Deployments, Testautomatisierung, Rollback-Mechanismen) unterstützen.

3. **Kontrollierte Variabilität statt harter Uniformität**: Adoptionsstudien zu Continuous Delivery zeigen, dass Teams an unterschiedlichen Stellen scheitern und Lösungen kontextabhängig sind (Laukkanen et al., 2017). Daraus folgt, dass eine IDP standardisierte Wege anbieten sollte, aber mit definierten Variationspunkten, um Teams mit unterschiedlichen Risiko- und Domänenanforderungen nicht zu blockieren.

### 2.3 Developer Experience (DX)

#### 2.3.1 Definition und Abgrenzung

Fagerholm und Münch (2012) definieren Developer Experience als Konzept, das beschreibt, wie Entwickler ihre Tätigkeit im Arbeitsumfeld erleben – insbesondere, wie sie darüber denken, wie sie sich dabei fühlen und welchen Wert sie der Arbeit beimessen. Die Definition positioniert DX als analog zu User Experience, jedoch mit Fokus auf Entwicklungsaktivitäten und Arbeitskontext (Fagerholm & Münch, 2012). Greiler et al. (2023) erweitern diese Perspektive in einem empirisch abgeleiteten Rahmenwerk: DX entsteht aus Interaktionen zwischen **Barrieren**, **Kontextcharakteristika** und **Strategien** von Individuen und Teams. Damit wird DX nicht als eindimensionaler Score verstanden, sondern als Ergebnis von Arbeitsbedingungen und Bewältigungsmechanismen (Greiler et al., 2023).

Für eine IDP ist diese Sichtweise methodisch hilfreich: Plattformfunktionen wirken nicht automatisch positiv, sondern beeinflussen Barrieren (z. B. Setup-Aufwand, fehlende Transparenz, instabile Toolketten) und Strategien (z. B. Workarounds, Copy-Paste-Templates, Shadow-IT). Eine Verbesserung wäre demnach dann plausibel, wenn die Plattform Barrieren reduziert und produktive Strategien unterstützt.

#### 2.3.2 Faktoren und Messbarkeit

DX-Messung ist in der Forschung nicht vollständig konsolidiert; es existieren jedoch empirisch gestützte Indikatoren. Produktivitätsstudien zeigen, dass Entwickler produktive Arbeit mit Fortschritt bei Aufgaben, wenigen Unterbrechungen und niedriger Kontextwechselrate verbinden (Meyer et al., 2014; Meyer et al., 2017). CI/CD-Empirie ergänzt technische Indikatoren: Lange Build-Dauern und ineffiziente Feedbackzyklen sind dokumentierte Probleme (Ghaleb et al., 2019), und Build-Fehler sind häufig mit Testfehlern, Qualitätsgates und Infrastrukturproblemen verbunden (Rausch et al., 2017). In der Testforschung wird zudem beschrieben, dass Flaky Tests Vertrauen in Feedback untergraben und Diagnoseaufwand erzeugen (Eck et al., 2019; Parry et al., 2021).

Als FH-praktikabler Messansatz bietet sich daher eine Kombination aus:

* **prozessnahen Metriken** (z. B. Lead Time, Deploy-Frequenz, Change Failure Rate),
* **toolnahen Metriken** (z. B. CI-Dauer, Gate-Fehlerraten, Flaky-Test-Vorkommen),
* **subjektiven DX-Indikatoren** (z. B. wahrgenommene Friktion, Unterbrechungen, Vertrauen in Feedback).

Für die Automatisierung prozessnaher Metriken ist relevant, dass Rüegger et al. (2024) eine Lösung zur automatisierten Messung von DORA-Metriken aus DevOps-Tooling vorstellen und dabei zeigen, dass sich Unterschiede auf Service-Ebene sichtbar machen lassen. Diese Arbeit ist für IDP-Evaluation besonders wertvoll, weil sie eine Brücke zwischen Tooldaten und kontinuierlicher Verbesserung schlägt (Rüegger et al., 2024).

---

## 3. Stand der Forschung

### 3.1 Analyse relevanter Literatur

#### 3.1.1 CI/CD-Adoption und typische Engpässe

Die Literatur zu CI/CD ist umfangreich; systematische Übersichten zeigen wiederkehrende Herausforderungen: Tool-Integration, Testautomatisierung, Build-/Release-Design sowie organisatorische Ausrichtung (Shahin et al., 2017). Laukkanen et al. (2017) identifizieren in ihrer SLR zahlreiche Probleme und ordnen sie thematisch u. a. den Bereichen Testing, Integration, Systemdesign und Organisation zu. Für diese Arbeit ist entscheidend, dass viele Probleme nicht durch einzelne Tools gelöst werden, sondern durch konsistente Standardwege und architekturelle Voraussetzungen – ein Hinweis auf die Rolle einer Plattform.

#### 3.1.2 Empirische Befunde zu Feedbackqualität: Build-Dauer, Build-Fehler, Testzuverlässigkeit

Ghaleb et al. (2019) untersuchen in einer empirischen Studie, welche Merkmale mit langen CI-Build-Dauern zusammenhängen. Unabhängig von konkreten Toolstacks ist die Kernaussage für IDPs: Feedbacklatenz ist kein Randproblem, sondern ein messbares Phänomen mit relevanten Kosteneffekten. Rausch et al. (2017) analysieren Build-Fehler in CI-Workflows und zeigen typische Fehlerkategorien (u. a. Tests, Kompilierung, Infrastruktur). Besonders relevant ist die Beobachtung, dass instabile Buildhistorien künftige Fehlschläge wahrscheinlicher machen können, was den Wert stabiler Standardpipelines unterstreicht (Rausch et al., 2017).

Im Testbereich zeigen Eck et al. (2019), dass Flaky Tests von Entwicklern als signifikantes Problem wahrgenommen werden und Diagnose/Behebung in der Praxis anspruchsvoll ist. Parry et al. (2021) systematisieren Forschung zu Flaky Tests und verdeutlichen, dass das Phänomen sowohl technisch als auch prozessual wirkt: Es verschlechtert das Vertrauen in Testsuites und erhöht Rework-Aufwand. Für IDPs folgt daraus, dass Test-Stabilität und Feedbackqualität explizite Plattformziele sein sollten, nicht nur „Teamaufgabe“.

#### 3.1.3 Plattformteams, interne Infrastruktur und Produktisierung von Plattformfähigkeiten

Leite et al. (2020) liefern eine empirische Grundlage für Plattformteams als Organisationsmuster. Aus dieser Perspektive wird eine IDP weniger als „Toolkatalog“ plausibel, sondern als Produkt, das nicht-funktionale Anforderungen und wiederkehrende Delivery-Fähigkeiten bündelt. Sadowski et al. (2015) zeigen anhand einer internen Analyseplattform, wie Skalierung, Akzeptanz und Feedbackmechanismen zusammenhängen. Diese Arbeiten stützen die Annahme, dass Plattformen mit klaren Schnittstellen und Nutzenversprechen gestaltet werden müssen, damit sie im Entwickleralltag wirklich angenommen werden.

#### 3.1.4 Supply-Chain-Sicherheit und Transparenz als neue Plattformanforderung

Die Forschung zu Software Supply Chain Security ist stark gewachsen. Xia et al. (2023) untersuchen SBOMs empirisch und zeigen, dass SBOM-Einführung nicht nur ein technischer Export ist, sondern Wahrnehmungen, Anforderungen und Hürden in der Praxis berührt. Stalnaker et al. (2024) analysieren Stakeholder-Perspektiven auf SBOMs und verdeutlichen Zielkonflikte rund um Nutzen, Aufwand und Verantwortlichkeiten. Für IDPs ergibt sich daraus die Notwendigkeit, Sicherheits-Artefakte und Nachweise „by design“ in Standardwege zu integrieren, ohne Teams mit zusätzlicher manueller Last zu überfordern.

### 3.2 Vergleich bestehender Ansätze

Die Literatur beschreibt einzelne Bausteine (CI/CD-Automatisierung, IaC, GitOps, Plattformteams), aber selten ein einheitliches, empirisch validiertes IDP-Referenzmodell. GitOps wird in IEEE Software als Konzept diskutiert, das Git als „single source of truth“ für deklarative Zustände nutzt und damit Kontrollierbarkeit und Reproduzierbarkeit adressiert (Beetz & Harrer, 2022). IaC-Mapping-Studien zeigen eine große Bandbreite an Tools und Forschungsfragen, aber auch Lücken bei Defekt- und Sicherheitsforschung (Rahman et al., 2019). DevSecOps-Systematisierungen zeigen, dass „Tools“ und Automatisierung zentrale Engpässe sind und dass der Zielkonflikt zwischen Geschwindigkeit und Sicherheit praktisch relevant bleibt (Rajapakse et al., 2022). Zusammengenommen ergibt sich ein Bild, in dem eine IDP als Integrations- und Standardisierungsartefakt plausibel ist, allerdings unter der Bedingung kontrollierter Flexibilität.

### 3.3 Forschungslücken

Für eine FH-orientierte Konzeption lassen sich aus der Literatur mehrere Lücken ableiten:

1. **Begrenzte empirische Evidenz zu IDPs als integrierte Systeme**: Es existieren empirische Bausteinstudien (CI-Metriken, Plattformteams, interne Infrastrukturen), aber vergleichsweise wenige Arbeiten, die IDPs als Gesamtsystem mit DX-Wirkung evaluieren (Leite et al., 2020; Sadowski et al., 2015; Greiler et al., 2023).

2. **Operationalisierung von DX für Plattformentscheidungen**: DX-Frameworks sind konzeptionell stark, aber die Übersetzung in konkrete Plattform-Metriken und Designentscheidungen bleibt häufig eine offene Implementationsfrage (Fagerholm & Münch, 2012; Greiler et al., 2023).

3. **Supply-Chain-Transparenz in Standardwegen**: SBOM-Forschung zeigt Relevanz und Hürden, aber die Einbettung in IDP-„Golden Paths“ ist noch nicht breit empirisch abgesichert (Xia et al., 2023; Stalnaker et al., 2024).

Diese Lücken begründen die Zielsetzung der Arbeit: Eine integrierte IDP-Konzeption, die DX-basiert argumentiert und prototypisch demonstriert wird.

---

## 4. Methodik

### 4.1 Forschungsdesign

Die Arbeit folgt einem **Design-Science-orientierten Vorgehen**, das in Informationssystem-Forschung als etabliert gilt: Problemidentifikation, Zieldefinition, Artefaktentwurf, Demonstration, Evaluation und Kommunikation (Peffers et al., 2007; Hevner et al., 2004). Für eine FH-Masterarbeit ist dieser Rahmen hilfreich, weil er konstruktive Artefakterstellung mit wissenschaftlicher Begründung verbindet. Gleichzeitig wird anerkannt, dass die Generalisierbarkeit der Ergebnisse begrenzt sein kann, wenn Evaluation in einer spezifischen Umgebung erfolgt.

### 4.2 Literaturrecherche

Die Literaturbasis wird entlang von Guidelines für systematische Reviews strukturiert. Kitchenham und Charters (2007) formulieren dafür ein in der Softwaretechnik weit rezipiertes Vorgehen (Suchstrategie, Ein-/Ausschlusskriterien, Extraktion, Synthese). In dieser Arbeit wird kein vollständiger SLR im strengen Sinn behauptet; stattdessen wird ein **systematisches, nachvollziehbares Mapping** durchgeführt, um Kernaussagen zu CI/CD-Engpässen, Plattformteams, IaC/GitOps, DX-Frameworks und Evaluation zu sammeln (Kitchenham & Charters, 2007). Die Synthese erfolgt thematisch (z. B. Feedbacklatenz, Standardisierung, Governance), um Quellen nicht nur nacheinander zu referieren, sondern argumentativ zusammenzuführen.

### 4.3 Vorgehen der empirischen Untersuchung / prototypischen Validierung

Als prototypische Validierung werden zwei Ebenen unterschieden:

1. **Technische Demonstration (Machbarkeit)**: Ein Prototyp implementiert zentrale IDP-Funktionen (Self-Service-Provisionierung, standardisierte Pipeline, Observability-Anbindung, Evidence-Artefakte wie SBOM-Erzeugung). Die Validität liegt hier in der nachweisbaren Integration der Bausteine, nicht in statistischer Wirksamkeitsmessung.

2. **Evaluationskonzept für Wirksamkeit**: Aufbauend auf empirischer DX- und Produktivitätsforschung wird ein Evaluationsdesign vorgeschlagen, das subjektive und objektive Daten kombiniert (Wohlin et al., 2012; Meyer et al., 2014; Rüegger et al., 2024). Eine FH-typische Einschränkung ist, dass große Stichproben oft nicht realistisch sind; daher werden Mixed-Methods-Ansätze (z. B. Fragebogen + Toolmetriken) als pragmatische Option beschrieben.

Wohlin et al. (2012) dienen hier als Referenz für Validitätsüberlegungen (Konstrukt-, interne/externe Validität, Reproduzierbarkeit) und für die Wahl eines passenden Studiendesigns.

---

## 5. Anforderungsanalyse

### 5.1 Kontextbeschreibung (praxisnahe Referenzumgebung)

Für die Konzeption wird eine typische mittelgroße Unternehmensumgebung angenommen: mehrere Produktteams entwickeln Services (häufig Microservices oder modulare Systeme), Deployment erfolgt containerisiert in einer cloud-nahen Umgebung, und Teams nutzen CI/CD-Pipelines mit Qualitäts- und Sicherheitsprüfungen. Diese Annahme ist realistisch im Sinne der Literatur, die CI/CD-Praktiken stark mit cloud-native Tooling und IaC verbindet (Shahin et al., 2017; Rahman et al., 2019). Gleichzeitig werden heterogene Reifegrade erwartet: Manche Teams verfügen über stabile Tests und schnelle Pipelines, andere kämpfen mit langen Builds, instabilen Tests und wiederkehrenden Integrationsproblemen (Ghaleb et al., 2019; Eck et al., 2019).

### 5.2 Anforderungen an die IDP (funktional und nicht-funktional)

#### 5.2.1 Funktionale Anforderungen

**F1 – Self-Service für wiederkehrende Aufgaben:** Teams sollen neue Services oder Komponenten über standardisierte Templates erstellen und die notwendigen Plattformressourcen anfordern können. Dies folgt der Plattformteam-Logik, nicht-funktionale Belange zu entlasten und Engineering-Kompetenz in zentralen Bausteinen zu bündeln (Leite et al., 2020).

**F2 – Standardisierte CI/CD-Pfade („Golden Paths“):** Die Plattform stellt kuratierte Pipeline-Vorlagen bereit, die Build, Test, Packaging und Deployment konsistent abbilden. Dies adressiert Befunde, dass Testing und Integration zentrale CD-Hürden sind (Laukkanen et al., 2017) und dass Build-Fehler oft in wiederkehrenden Kategorien auftreten (Rausch et al., 2017).

**F3 – Observability-Default:** Jede über die IDP bereitgestellte Komponente wird mit Logging/Metrics/Tracing-Grundlagen ausgestattet, um Feedback in Betrieb zu ermöglichen. Dies ist indirekt durch DevOps-Ziele (Feedback und Betriebssicht) begründet (Bass et al., 2015; Humble & Farley, 2010).

**F4 – Supply-Chain-Transparenzartefakte:** Die Plattform erzeugt und verwaltet Evidence-Artefakte wie SBOMs und verknüpft sie mit Builds. Empirische SBOM-Studien zeigen, dass Transparenz gewünscht ist, die Einführung jedoch ohne Tool- und Prozessintegration schwerfällt (Xia et al., 2023; Stalnaker et al., 2024).

#### 5.2.2 Nicht-funktionale Anforderungen

**N1 – Developer Experience:** Die Plattform soll Barrieren reduzieren, z. B. Setup-Aufwand, Unterbrechungen durch instabile Pipelines und langes Warten auf Feedback. Diese Zielrichtung stützt sich auf DX-Frameworks und Produktivitätsstudien (Greiler et al., 2023; Meyer et al., 2014).

**N2 – Standardisierung mit Variabilität:** Standardwege sind Default, aber Teams benötigen definierte Abweichungsmöglichkeiten (z. B. zusätzliche Teststufen, strengere Policy-Profile). Die Notwendigkeit ergibt sich aus Kontextabhängigkeit von CD-Adoption (Laukkanen et al., 2017).

**N3 – Sicherheit/Compliance:** Sicherheitsanforderungen sollen „by default“ erfüllt werden, ohne die Pipeline zu einem schwergewichtigen Gate-System zu machen. DevSecOps-SLRs zeigen, dass toolbezogene Herausforderungen dominieren und „developer-centered“ Lösungen nötig sind (Rajapakse et al., 2022).

**N4 – Skalierbarkeit und Wartbarkeit der Plattform:** Plattformteams agieren als Produktteam; daher braucht es klare Schnittstellen, Versionierung und Betriebsverantwortung. Das ist in der Plattformteam-Empirie angelegt (Leite et al., 2020) und wird durch interne Plattformbeispiele gestützt, die Prinzipien und Architektur als Skalierungsfaktor betonen (Sadowski et al., 2015).

### 5.3 Ableitung aus Theorie und Praxis (Zusammenführung)

Die Anforderungen lassen sich als direkte Reaktion auf empirisch belegte Belastungen zusammenfassen: lange CI-Feedbackzyklen (Ghaleb et al., 2019), häufige Build-Fehler und instabile Buildhistorien (Rausch et al., 2017) sowie Testinstabilität (Eck et al., 2019; Parry et al., 2021) beeinträchtigen den Arbeitsfluss. Gleichzeitig zeigen DX-Arbeiten, dass Entwickler Barrieren nicht nur passiv erleiden, sondern Strategien entwickeln (Workarounds, Parallelprozesse), die kurzfristig helfen, langfristig aber Standardisierung und Qualität unterlaufen können (Greiler et al., 2023). Eine IDP muss daher nicht nur Toolzugänge bündeln, sondern die **Qualität von Standardwegen** und die **Verlässlichkeit von Feedback** verbessern.

---

## 6. Konzeption der IDP

### 6.1 Architekturprinzipien

#### 6.1.1 Plattform als Produkt mit klaren Verträgen

Ein zentrales Prinzip ist die Produktisierung: Plattformfähigkeiten werden nicht als „Betriebsservice“, sondern als evolutionäres Produkt verstanden, das aktiv genutzt werden soll. Leite et al. (2020) beschreiben, dass Plattformteams nicht-funktionale Belange zentral handhaben und so Produktteams entlasten können. Daraus folgt, dass Schnittstellen explizit definiert werden müssen: Was liefert die Plattform (z. B. Pipeline-Templates, Provisionierung), was bleibt Teamverantwortung (fachliche Logik, Servicequalität). Diese Form von Verträgen ist auch deshalb wichtig, weil DX-Frameworks betonen, dass unklare Verantwortlichkeiten und inkonsistente Prozesse Barrieren erzeugen können (Greiler et al., 2023).

#### 6.1.2 „Paved Road“ + kontrollierte Variabilität

Die IDP bietet Golden Paths als Default. Gleichzeitig zeigen CD-SLRs, dass Teams unterschiedliche Ursachen für Probleme haben; harte Uniformität würde Ausnahmen produzieren und Shadow-IT fördern (Laukkanen et al., 2017). Deshalb werden Variationspunkte geplant, z. B. Pipeline-Profile, optionale Stufen oder Security-Level. Wichtig ist, dass Variabilität nicht unkontrolliert geschieht, sondern deklarativ und auditierbar ist.

#### 6.1.3 Feedbackqualität als architektonisches Qualitätsziel

CI/CD-Literatur legt nahe, dass Geschwindigkeit ohne verlässliches Feedback riskant ist (Humble & Farley, 2010; Shahin et al., 2017). Empirische Befunde zu Build-Dauer und Build-Fehlern (Ghaleb et al., 2019; Rausch et al., 2017) sowie zu Flaky Tests (Eck et al., 2019) motivieren, Feedbackqualität als explizites Designziel zu formulieren. Daraus folgt: Plattformkomponenten müssen nicht nur Deployments ausführen, sondern auch Stabilitätsmechanismen (Caching, Testselektion, Quarantäne für Flaky Tests, klare Fehlerklassifikation) ermöglichen.

### 6.2 Referenzarchitektur (Zielbild)

#### 6.2.1 Schichtenmodell

Für ein verständliches und wartbares Zielbild wird eine Trennung in **Developer Interface**, **Control Plane** und **Execution/Data Plane** vorgeschlagen:

* **Developer Interface Layer:** konsistente Schnittstellen (CLI/API/UI), Servicekatalog, Dokumentations- und Onboardingpfade.
* **Control Plane:** Orchestrierung von Provisionierung und Deployments, Policy- und Templateverwaltung, Metrikerfassung.
* **Execution/Data Plane:** Build-Runner, Artifact-Registry, Deployment-Controller, Runtime-Observability-Stack.

Die Trennung orientiert sich an der Idee, dass Plattformen als skalierende Infrastrukturen stabile Schnittstellen brauchen, während Implementierungen ausgetauscht werden können. Diese Denkweise ist mit Plattform- und Infrastrukturbeispielen vereinbar, die Prinzipien und Architektur für Skalierung hervorheben (Sadowski et al., 2015) und mit GitOps-Diskussionen, die deklarative Zustände und Reconciliation betonen (Beetz & Harrer, 2022).

#### 6.2.2 Zentrale Komponenten

**(A) Golden-Path-Templates (Service-Scaffolding):**
Templates erzeugen Repositorystruktur, Standardpipeline, IaC-Moduleinbindung, Basiskonfiguration für Observability. Die Motivation folgt aus Plattformteam-Entlastung (Leite et al., 2020) und aus DX-Barrierenreduktion (Greiler et al., 2023).

**(B) Pipeline-as-Code + Quality Gates:**
Pipelines werden versioniert bereitgestellt. Quality Gates (Tests, Linting, Security Checks) werden als Standardstufen modelliert. Rausch et al. (2017) zeigen, dass Test- und Qualitätsgates häufige Fehlerquellen sind; durch zentral kuratierte Stufen kann Fehlerklassifikation verbessert und Wiederholbarkeit erhöht werden.

**(C) IaC-Module und IaC-Governance:**
IaC-Module kapseln bewährte Infrastrukturpatterns. Rahman et al. (2019) zeigen, dass IaC-Forschung häufig Tools und Nutzung fokussiert und Defekte/Security als wichtige Themen identifiziert. Eine IDP sollte daher IaC-Qualitätssicherung (Tests, Reviews, Scans) als Plattformfunktion bereitstellen.

**(D) Supply-Chain-Artefakte (SBOM-Pipeline):**
SBOM-Erzeugung wird als standardisierter Schritt in die Pipeline integriert, inklusive Ablage, Versionierung und Verknüpfung mit Releases. Die Relevanz ist empirisch begründet (Xia et al., 2023), während Stakeholder-Perspektiven Zielkonflikte sichtbar machen, die eine Plattform durch Standardisierung und klare Ownership zumindest organisatorisch abfedern kann (Stalnaker et al., 2024).

**(E) DX- und Delivery-Metriken:**
Die Plattform sammelt Metriken automatisiert aus Tooling. Rüegger et al. (2024) zeigen, dass automatisierte DORA-Messung möglich ist und Unterschiede auf Service-Ebene sichtbar macht, was für Plattformsteuerung und kontinuierliche Verbesserung relevant ist.

### 6.3 Designentscheidungen und Begründung anhand der Literatur

#### 6.3.1 Entscheidung 1: Plattformteam-Operating-Model mit klaren SLOs

Die IDP wird organisatorisch als Produkt betrieben. Plattformteam und Produktteams erhalten definierte Verantwortungen, um Barrieren durch unklare Zuständigkeiten zu reduzieren (Greiler et al., 2023). Empirische Evidenz für Plattformteams als Muster liefert Leite et al. (2020). Aus FH-Perspektive ist dabei wichtig, dass diese Entscheidung nicht als „Best Practice“ behauptet wird, sondern als plausible Reaktion auf wiederkehrende Integrations- und Standardisierungsprobleme in CD-Adoption (Laukkanen et al., 2017).

#### 6.3.2 Entscheidung 2: Standard-Pipelines mit Variationspunkten (Profile)

Statt individuelle Pipelines pro Team zuzulassen, werden Standardpipelines bereitgestellt. Variationspunkte werden als Profile modelliert (z. B. zusätzliche Integrationstests, strengere Compliance-Checks). Diese Entscheidung ist durch CD-SLR begründet: Testing und Systemdesign sind häufig kritische Problemquellen, und Lösungen müssen trotzdem kontextabhängig bleiben (Laukkanen et al., 2017). Zusätzlich adressiert das Profil-Modell DX-Barrieren, weil es Teams Ausnahmen ermöglicht, ohne Workarounds und Copy-Paste-Divergenz zu fördern (Greiler et al., 2023).

#### 6.3.3 Entscheidung 3: Feedbacklatenz minimieren als Plattform-KPI

CI-Build-Dauer wird als steuerungsrelevante Größe betrachtet, weil lange Builds empirisch verbreitet sind und Entwicklungszeit binden (Ghaleb et al., 2019). Diese Entscheidung wird mit Produktivitätswahrnehmungen verknüpft: Unterbrechungen und Wartezeiten erhöhen Kontextwechsel und verringern wahrgenommene Produktivität (Meyer et al., 2014; Meyer et al., 2017). In der Plattform bedeutet das konkret: Caching-Mechanismen, parallele Tests, klare Fehlertypisierung, sowie Maßnahmen gegen Flaky Tests werden vorgesehen (Eck et al., 2019; Parry et al., 2021).

#### 6.3.4 Entscheidung 4: Supply-Chain-Transparenz in Golden Paths integrieren

SBOM-Erzeugung wird nicht als optionales Add-on behandelt, sondern als Teil der Standardlieferkette. Die Begründung beruht auf empirischer SBOM-Evidenz (Xia et al., 2023) und Stakeholder-Analysen, die zeigen, dass Nutzenversprechen und Verantwortlichkeiten ohne klare Prozesse auseinanderlaufen können (Stalnaker et al., 2024). Eine Plattform kann hier Standardisierung liefern, ersetzt aber nicht die Notwendigkeit organisatorischer Regelungen; diese Einschränkung wird in der Diskussion wieder aufgegriffen.

---

## 7. Prototypische Umsetzung

### 7.1 Technologiewahl (begründete Auswahlkriterien)

Die konkrete Toolauswahl ist in einer Masterarbeit häufig organisationsabhängig. Für einen prototypischen Nachweis sind daher Kriterien wichtiger als Marken:

* **Deklarativität und Versionierung** (GitOps-Kompatibilität),
* **Automatisierbarkeit** (CI/CD-Schnittstellen, IaC-Integration),
* **Metrikzugriff** (Event-/Log-basierte Auswertung),
* **Erweiterbarkeit** (Templates/Module).

GitOps als Konzept wird als geeignet betrachtet, weil es deklarative Zustände und Reconciliation betont und damit nachvollziehbare Deployments erleichtern kann (Beetz & Harrer, 2022). IaC wird als unverzichtbar eingeschätzt, weil es Infrastruktur standardisierbar und testbar macht (Rahman et al., 2019). Für Metriken wird eine automatisierte Erhebung bevorzugt; Rüegger et al. (2024) zeigen, dass eine automatisierte Berechnung delivery-naher Metriken aus Tooling prinzipiell möglich ist.

### 7.2 Beschreibung des Prototyps (Funktionen)

Der Prototyp deckt einen minimalen, aber end-to-end nachvollziehbaren Golden Path ab:

1. **Service-Scaffolding:** Erzeugung eines Service-Repos mit Standardstruktur, Beispielservice, Pipeline-Definition und IaC-Referenzen.
2. **Provisionierung:** Anlegen einer Laufzeitumgebung über IaC-Module; Parameter (Team, Umgebung, Risiko-Profil) werden deklarativ übergeben.
3. **CI/CD-Pipeline:** Build, Unit-Tests, statische Checks, Container-Build, Deployment in eine Zielumgebung.
4. **Observability-Default:** Basiskonfiguration für Logging/Metriken; Ziel ist nicht Vollständigkeit, sondern standardisierte Anschlussfähigkeit.
5. **SBOM-Artefakt:** Erzeugung einer SBOM pro Build und Ablage gemeinsam mit Release-Artefakten. Empirische Arbeiten zeigen, dass SBOM-Akzeptanz u. a. von Toolintegration und Einbettung abhängt; daher wird die SBOM nicht „nebenbei“ erzeugt, sondern als sichtbarer, nachverfolgbarer Bestandteil des Golden Path implementiert (Xia et al., 2023; Stalnaker et al., 2024).

### 7.3 Grenzen der Umsetzung

Der Prototyp ist als Machbarkeitsnachweis konzipiert. Er ersetzt keine vollständige Produktreife, z. B. hinsichtlich Mandantenfähigkeit, Governance-Workflows oder umfassender Policy-Engine. Zudem bleibt die Wirksamkeit auf DX ohne Nutzerstudie nur begrenzt belegbar. Diese Einschränkung ist in Design-Science-Arbeiten üblich: Das Artefakt kann demonstriert und technisch evaluiert werden, während generalisierbare Wirkaussagen umfangreichere Studien erfordern (Hevner et al., 2004; Wohlin et al., 2012).

---

## 8. Evaluation

### 8.1 Evaluationsmethoden (Vorschlag für empirische Bewertung)

Für eine FH-praktische Evaluation wird ein Mixed-Methods-Vorgehen vorgeschlagen:

1. **Objektive Toolmetriken (vorher/nachher):**

   * CI-Build-Dauer (Ghaleb et al., 2019)
   * Build-Fehlerraten nach Kategorien (Rausch et al., 2017)
   * Auftreten und Behebungsaufwand für Flaky Tests (Eck et al., 2019; Parry et al., 2021)
   * Delivery-Metriken (DORA-ähnlich) mit automatisierter Messung (Rüegger et al., 2024)

2. **Subjektive DX-Indikatoren:**

   * Wahrgenommene Unterbrechungen/Kontextwechsel und produktive Tage (Meyer et al., 2014; Meyer et al., 2017)
   * DX-Barrieren und Strategien nach Greiler et al. (2023) (z. B. qualitative Kurzinterviews, thematische Codierung)

3. **Qualitative Validierung der Plattformkonzepte:**

   * Review-Workshops mit Teams, Fokus auf Verständlichkeit der Golden Paths, wahrgenommene Autonomie und Governance-Passung.
     Methodisch kann hier ein Fallstudien- oder Feldstudienansatz gewählt werden; Wohlin et al. (2012) bieten hierfür Leitlinien zur Validitätssicherung.

### 8.2 Ergebnisse der prototypischen Validierung (Machbarkeit)

Im Rahmen dieser Arbeit wird die Evaluation im engeren Sinn als **prototypische Validierung** verstanden: Der Prototyp zeigt, dass ein durchgängiger Golden Path technisch integrierbar ist und zentrale Anforderungen adressiert. Der Nachweis umfasst insbesondere:

* **Durchgängige Automatisierung von Scaffolding bis Deployment:** Dies reduziert manuellen Setup-Aufwand und passt zur Plattformteam-Logik der Entlastung (Leite et al., 2020).
* **Standardisierte Pipeline mit klarer Fehlerklassifikation:** Angesichts typischer Build-Fehlerkategorien (Rausch et al., 2017) ist dies ein realistischer Ansatz, um Debuggingaufwand zu reduzieren.
* **SBOM-Erzeugung als Standardartefakt:** Empirische SBOM-Arbeiten betonen die Bedeutung von Praxisintegration; der Prototyp demonstriert die Einbettung in den Delivery-Flow (Xia et al., 2023; Stalnaker et al., 2024).
* **Grundlegende Metrikerfassung:** Die Architektur ermöglicht prinzipiell die automatisierte Erhebung delivery-naher Kennzahlen, was durch Forschung zu automatisierter DORA-Messung gestützt wird (Rüegger et al., 2024).

Diese Validierung ist bewusst vorsichtig interpretiert: Sie belegt Realisierbarkeit, nicht automatisch eine DX-Verbesserung in einer realen Organisation.

### 8.3 Kritische Betrachtung

Die prototypische Validierung adressiert technische Risiken, aber nicht alle soziotechnischen Risiken. DX-Frameworks machen deutlich, dass Barrieren auch durch Organisation, Kommunikation und Prioritäten entstehen können (Greiler et al., 2023). Eine IDP kann Barrieren reduzieren, sie kann jedoch neue erzeugen, etwa wenn Standardwege zu rigide sind oder Governanceprozesse als Fremdbestimmung erlebt werden. Zudem ist die Messbarkeit von DX begrenzt, weil subjektive Wahrnehmungen kontextabhängig sind (Fagerholm & Münch, 2012; Meyer et al., 2014). Daher sollte die vorgeschlagene Evaluation als Mindeststandard verstanden werden, nicht als endgültiger Beweis.

---

## 9. Diskussion

### 9.1 Beantwortung der Forschungsfragen

**(1) Typische Herausforderungen im Entwicklungsalltag**
Die Literatur zeigt konsistent, dass Feedbacklatenz (z. B. lange CI-Builds), instabile Feedbacksignale (Build-Fehler, Flaky Tests) sowie Integrations- und Testingprobleme zentrale Belastungen sind (Ghaleb et al., 2019; Rausch et al., 2017; Eck et al., 2019; Laukkanen et al., 2017). Zusätzlich weist Produktivitätsforschung darauf hin, dass häufige Unterbrechungen und Kontextwechsel als unproduktive Treiber erlebt werden (Meyer et al., 2014; Meyer et al., 2017). Diese Befunde stützen die These, dass Verbesserungen im Tool- und Delivery-Ökosystem die Arbeitswahrnehmung beeinflussen können.

**(2) Wissenschaftlich etablierte Plattform-Engineering-Prinzipien**
Ein belastbarer Kern ist das Plattformteam-Muster als Organisationsstruktur im CD-Kontext (Leite et al., 2020), ergänzt durch Praktikenbündel aus DevOps/CD (Humble & Farley, 2010; Bass et al., 2015) sowie deklarative Deploymentschemata (GitOps) als Ansatz zur Reproduzierbarkeit (Beetz & Harrer, 2022). Die Forschung spricht weniger von „Platform Engineering“ als Label, aber die Bausteine sind klar: Zentral kuratierte, wiederverwendbare Delivery-Fähigkeiten, Self-Service, und standardisierte Wege mit Raum für Kontextvarianten.

**(3) Definition und Messbarkeit von DX**
DX ist in der Forschung als mehrdimensionales Konstrukt beschrieben, das Denken, Fühlen und Wertzuschreibung umfasst (Fagerholm & Münch, 2012) und über Barrieren/Kontext/Strategien erklärbar wird (Greiler et al., 2023). Für die Messung sind rein technische Metriken nicht ausreichend; sinnvoll ist eine Kombination aus Toolmetriken (Builddauer, Fehlerraten, Teststabilität) und subjektiven Indikatoren (Unterbrechungen, Vertrauen in Feedback) (Ghaleb et al., 2019; Meyer et al., 2014; Parry et al., 2021). Automatisierte Delivery-Metriken können als kontinuierliche Sicht genutzt werden (Rüegger et al., 2024), sollten aber nicht als vollständiger Ersatz für DX-Erhebung verstanden werden.

**(4) Geeignete Architekturentscheidungen**
Die IDP-Architektur sollte (i) klare Schichten (Interface/Control/Execution) trennen, (ii) Golden Paths als Standard definieren, (iii) Variationspunkte explizit modellieren und (iv) Feedbackqualität als Zielgröße behandeln. Empirische Ergebnisse zu Build-Fehlern und CD-Adoptionsproblemen stützen standardisierte Pipelinebausteine (Rausch et al., 2017; Laukkanen et al., 2017). IaC-Forschung begründet kuratierte Module plus Qualitätsabsicherung (Rahman et al., 2019). SBOM-Studien stützen die Integration von Transparenzartefakten in Standardwege (Xia et al., 2023; Stalnaker et al., 2024).

**(5) Prototypische Umsetzung**
Die prototypische Umsetzung ist plausibel, wenn deklarative Infrastruktur (IaC), deklaratives Deployment (GitOps-Prinzipien) und Pipeline-Automatisierung kombiniert werden. GitOps wird dabei als Konzept genutzt, nicht als spezifisches Produkt (Beetz & Harrer, 2022). Der Prototyp demonstriert, dass die Integration technisch realisierbar ist und zentrale Anforderungen abbildet.

**(6) Empirische Evaluation des Nutzens**
Für eine empirische Nutzenbewertung ist ein Mixed-Methods-Design geeignet, das Toolmetriken und subjektive DX-Indikatoren kombiniert (Wohlin et al., 2012; Greiler et al., 2023). Automatisierte Metriken bieten eine kontinuierliche Basis (Rüegger et al., 2024), während Interviews/Surveys helfen, DX-Barrieren und Strategien zu verstehen.

### 9.2 Einordnung der Ergebnisse

Die Konzeption ist eng an empirische Problemfelder gekoppelt (Testing/Integration, Feedbacklatenz, Instabilität). Sie ist damit weniger „visionär“ als bewusst pragmatisch. Das ist FH-typisch: Der Beitrag liegt in der **übersetzten Synthese** wissenschaftlicher Erkenntnisse in ein umsetzbares Zielbild. Gleichzeitig bleibt offen, wie stark DX in einem konkreten Unternehmen tatsächlich verbessert wird; dies hängt u. a. von Adoption, Governance und lokaler Kultur ab (Greiler et al., 2023; Leite et al., 2020).

### 9.3 Limitationen

1. **Begrenzte externe Validität:** Prototyp und Annahmen spiegeln eine typische, aber nicht universelle Umgebung wider. (Wohlin et al., 2012)
2. **DX-Operationalisierung:** DX ist mehrdimensional; technische Metriken sind nur Proxy-Indikatoren. (Fagerholm & Münch, 2012; Greiler et al., 2023)
3. **Supply-Chain-Aspekte:** SBOM-Integration wird technisch demonstriert, die organisatorische Einbettung (Verantwortlichkeiten, Nutzungsprozesse) muss in der Praxis weiter ausgestaltet werden. (Xia et al., 2023; Stalnaker et al., 2024)

---

## 10. Fazit und Ausblick

Diese Arbeit entwickelt ein begründetes Zielbild für eine interne Entwicklungsplattform, die Developer Experience verbessern soll, ohne Standardisierung, Sicherheit/Compliance und Teamflexibilität gegeneinander auszuspielen. Der Kernbeitrag ist eine Architektur- und Anforderungssynthese: Empirische Evidenz zu CI/CD-Engpässen (Laukkanen et al., 2017), Build-Dauer (Ghaleb et al., 2019), Build-Fehlern (Rausch et al., 2017), Testinstabilität (Eck et al., 2019; Parry et al., 2021), Plattformteams (Leite et al., 2020), DX-Modellen (Fagerholm & Münch, 2012; Greiler et al., 2023) und Supply-Chain-Transparenz (Xia et al., 2023; Stalnaker et al., 2024) wird in eine umsetzbare IDP-Konzeption überführt.

Als Ausblick sind drei Richtungen naheliegend:
(1) **Feldstudie zur DX-Wirkung** mit Mixed Methods und längerer Laufzeit (Wohlin et al., 2012).
(2) **Erweiterung um Governance-Mechanismen**, z. B. Policies als deklarative Profile und kontrollierte Ausnahmeprozesse.
(3) **Vertiefung Supply-Chain-Integration**, z. B. standardisierte Nutzung der SBOM in Vulnerability-Management und Release-Freigaben (Xia et al., 2023).

---

## 11. Literaturverzeichnis (APA-ähnlich)

Bass, L., Weber, I., & Zhu, L. (2015). *DevOps: A Software Architect’s Perspective*. Addison-Wesley. ([Google Bücher][1])

Beetz, F., & Harrer, S. (2022). GitOps: The Evolution of DevOps? *IEEE Software, 39*(4), 70–75. ([ACM Digital Library][2])

Bellomo, S., Ernst, N. A., Nord, R. L., & Kazman, R. (2014). Toward Design Decisions to Enable Deployability: Empirical Study of Three Projects Reaching for the Continuous Delivery Holy Grail. In *Proceedings of IEEE/IFIP DSN 2014*. ([sei.cmu.edu][3])

Eck, M., Palomba, F., Castelluccio, M., & Bacchelli, A. (2019). Understanding Flaky Tests: The Developer’s Perspective. In *Proceedings of ESEC/FSE 2019*. ([ACM Digital Library][4])

Fagerholm, F., & Münch, J. (2012). Developer Experience: Concept and Definition. In *Proceedings of ICSSP 2012*. ([ACM Digital Library][5])

Ghaleb, T. A., da Costa, D. A., Zou, Y., & Hassan, A. E. (2019). An Empirical Study of the Long Duration of Continuous Integration Builds. *Empirical Software Engineering*. ([Springer][6])

Greiler, M., Storey, M.-A., & Noda, A. (2023). An Actionable Framework for Understanding and Improving Developer Experience. *IEEE Transactions on Software Engineering*. ([ACM Digital Library][7])

Hevner, A. R., March, S. T., Park, J., & Ram, S. (2004). Design Science in Information Systems Research. *MIS Quarterly, 28*(1), 75–105. ([MISQ][8])

Humble, J., & Farley, D. (2010). *Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation*. Addison-Wesley. ([Google Bücher][9])

Kitchenham, B., & Charters, S. (2007). *Guidelines for Performing Systematic Literature Reviews in Software Engineering* (EBSE Technical Report EBSE-2007-01). Keele University. ([Legacy File Share][10])

Laukkanen, E., Itkonen, J., & Lassenius, C. (2017). Problems, causes and solutions when adopting continuous delivery—A systematic literature review. *Information and Software Technology, 82*, 55–79. ([ScienceDirect][11])

Leite, L., Kon, F., Pinto, G., & Meirelles, P. (2020). Platform Teams: An Organizational Structure for Continuous Delivery. In *Proceedings of IEEE/ACM ICSEW 2020*. ([ACM Digital Library][12])

Meyer, A. N., Fritz, T., Murphy, G. C., & Zimmermann, T. (2014). Software Developers’ Perceptions of Productivity. In *Proceedings of ESEC/FSE 2014*. ([ACM Digital Library][13])

Meyer, A. N., Barton, L. E., Murphy, G. C., Zimmermann, T., & Fritz, T. (2017). The Work Life of Developers: Activities, Switches and Perceived Productivity. *IEEE Transactions on Software Engineering, 43*(12), 1178–1193. ([ACM Digital Library][14])

Parry, O., Kapfhammer, G. M., Hilton, M., & McMinn, P. (2021). A Survey of Flaky Tests. *ACM Transactions on Software Engineering and Methodology*. ([ACM Digital Library][15])

Peffers, K., Tuunanen, T., Rothenberger, M. A., & Chatterjee, S. (2007). A Design Science Research Methodology for Information Systems Research. *Journal of Management Information Systems, 24*(3), 45–77. ([tandfonline.com][16])

Rahman, A., Mahdavi-Hezaveh, R., & Williams, L. (2019). A systematic mapping study of infrastructure as code research. *Information and Software Technology*. ([ScienceDirect][17])

Rajapakse, R. N., Zahedi, M., Babar, M. A., & Shen, H. (2022). Challenges and solutions when adopting DevSecOps: A systematic review. *Information and Software Technology, 141*, 106700. ([ScienceDirect][18])

Rausch, T., Hummer, W., Leitner, P., & Schulte, S. (2017). An Empirical Analysis of Build Failures in the Continuous Integration Workflows of Java-Based Open-Source Software. In *Proceedings of MSR 2017*. ([ACM Digital Library][19])

Rüegger, J., Kropp, M., Graf, S., & Anslow, C. (2024). Fully Automated DORA Metrics Measurement for Continuous Improvement. In *Proceedings of ICSSP 2024*. ([ACM Digital Library][20])

Sadowski, C., et al. (2015). Tricorder: Building a Program Analysis Ecosystem. In *Proceedings of ICSE 2015*. ([Lund University][21])

Shahin, M., Babar, M. A., & Zhu, L. (2017). Continuous Integration, Delivery and Deployment: A Systematic Review on Approaches, Tools, Challenges and Practices. *IEEE Access*. ([ACM Digital Library][22])

Stalnaker, T., Chaparro, O., et al. (2024). BOMs Away! Inside the Minds of Stakeholders … (SBOM-Stakeholder-Studie). In *Proceedings of ICSE 2024*. ([Oscar Chaparro][23])

Wohlin, C., Runeson, P., Höst, M., Ohlsson, M. C., Regnell, B., & Wesslén, A. (2012). *Experimentation in Software Engineering*. Springer. ([Springer][24])

Xia, B., et al. (2023). An Empirical Study on Software Bill of Materials: Where We Are and Where We Should Go. In *Proceedings of ICSE 2023*. ([ACM Digital Library][25])

---

[1]: https://books.google.com/books/about/DevOps.html?id=fcwkCQAAQBAJ&utm_source=chatgpt.com "DevOps: A Software Architect's Perspective"
[2]: https://dl.acm.org/doi/10.1109/MS.2021.3119106?utm_source=chatgpt.com "GitOps: The Evolution of DevOps? | IEEE Software"
[3]: https://www.sei.cmu.edu/documents/1445/2014_021_001_424904.pdf?utm_source=chatgpt.com "Toward Design Decisions to Enable Deployability"
[4]: https://dl.acm.org/doi/10.1145/3338906.3338945?utm_source=chatgpt.com "Understanding flaky tests: the developer's perspective"
[5]: https://dl.acm.org/doi/10.5555/2664360.2664372?utm_source=chatgpt.com "Developer experience: concept and definition"
[6]: https://link.springer.com/article/10.1007/s10664-019-09695-9?utm_source=chatgpt.com "An empirical study of the long duration of continuous ..."
[7]: https://dl.acm.org/doi/10.1109/TSE.2022.3175660?utm_source=chatgpt.com "An Actionable Framework for Understanding and ..."
[8]: https://misq.umn.edu/misq/article/28/1/75/261/Design-Science-in-Information-Systems-Research1?utm_source=chatgpt.com "Design Science in Information Systems Research 1"
[9]: https://books.google.de/books?id=6ADDuzere-YC&utm_source=chatgpt.com "Continuous Delivery: Reliable Software Releases through ..."
[10]: https://legacyfileshare.elsevier.com/promis_misc/525444systematicreviewsguide.pdf?utm_source=chatgpt.com "Guidelines for performing Systematic Literature Reviews in ..."
[11]: https://www.sciencedirect.com/science/article/pii/S0950584916302324?utm_source=chatgpt.com "Problems, causes and solutions when adopting continuous ..."
[12]: https://dl.acm.org/doi/10.1145/3387940.3391455?utm_source=chatgpt.com "Platform Teams | Proceedings of the IEEE/ACM 42nd ..."
[13]: https://dl.acm.org/doi/10.1145/2635868.2635892?utm_source=chatgpt.com "Software developers' perceptions of productivity"
[14]: https://dl.acm.org/doi/10.1109/TSE.2017.2656886?utm_source=chatgpt.com "The Work Life of Developers: Activities, Switches and ..."
[15]: https://dl.acm.org/doi/abs/10.1145/3476105?utm_source=chatgpt.com "A Survey of Flaky Tests | ACM Transactions on Software ..."
[16]: https://www.tandfonline.com/doi/abs/10.2753/MIS0742-1222240302?utm_source=chatgpt.com "A Design Science Research Methodology for Information ..."
[17]: https://www.sciencedirect.com/science/article/abs/pii/S0950584918302507?utm_source=chatgpt.com "A systematic mapping study of infrastructure as code ..."
[18]: https://www.sciencedirect.com/science/article/abs/pii/S0950584921001543?utm_source=chatgpt.com "Challenges and solutions when adopting DevSecOps"
[19]: https://dl.acm.org/doi/10.1109/MSR.2017.54?utm_source=chatgpt.com "An empirical analysis of build failures in the continuous ..."
[20]: https://dl.acm.org/doi/10.1145/3666015.3666020?utm_source=chatgpt.com "Fully Automated DORA Metrics Measurement for ..."
[21]: https://portal.research.lu.se/en/publications/tricorder-building-a-program-analysis-ecosystem/?utm_source=chatgpt.com "Tricorder: Building a Program Analysis Ecosystem"
[22]: https://dl.acm.org/doi/10.1016/j.jss.2017.02.013?utm_source=chatgpt.com "Continuous Delivery | Journal of Systems and Software"
[23]: https://ojcchar.github.io/files/27-icse24-sboms.pdf?utm_source=chatgpt.com "BOMs Away! Inside the Minds of Stakeholders - Oscar Chaparro"
[24]: https://link.springer.com/content/pdf/10.1007/978-3-642-29044-2.pdf?utm_source=chatgpt.com "Experimentation in Software Engineering - Springer Link"
[25]: https://dl.acm.org/doi/abs/10.1109/ICSE48619.2023.00219?utm_source=chatgpt.com "An Empirical Study on Software Bill of Materials: Where We ..."


