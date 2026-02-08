
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

Wenn du möchtest, kann ich als nächsten Schritt **(a)** den Text in eine **Word-Datei im typischen FH-Layout** (Deckblatt, Abstract, Abbildungsverzeichnis-Platzhalter, Kapitelnummerierung) übertragen oder **(b)** Kapitel 7/8 stärker „handlungsanleitend“ machen (konkrete Prototyp-Artefakte, Evaluationsinstrumente, Fragebogenitems und Metrikdefinitionen) – weiterhin ausschließlich mit wissenschaftlicher Fundierung.

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
