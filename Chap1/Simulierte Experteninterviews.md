# 1. Einleitung

## 1.1 Motivation und Problemstellung

Die zunehmende Digitalisierung industrieller Wertschöpfungsprozesse sowie der verstärkte Einsatz cloud-nativer Architekturen, Microservices und automatisierter Bereitstellungsprozesse führen zu einer stetig wachsenden Komplexität moderner Softwareentwicklung. Entwicklungsteams sehen sich dabei nicht nur mit der fachlichen Umsetzung von Anforderungen konfrontiert, sondern müssen zunehmend auch infrastrukturelle, betriebliche und sicherheitsrelevante Aspekte berücksichtigen. Diese zusätzliche Verantwortung erhöht die kognitive Belastung der Entwicklerinnen und Entwickler und kann sich negativ auf Produktivität, Qualität und Zufriedenheit auswirken.

Insbesondere in großen, industriell geprägten Organisationen mit heterogenen Entwicklungsteams stellt die Bereitstellung konsistenter, sicherer und gleichzeitig flexibler Entwicklungsumgebungen eine zentrale Herausforderung dar. Historisch gewachsene Tool-Landschaften, unterschiedliche Deployment-Strategien sowie variierende Sicherheits- und Compliance-Anforderungen erschweren eine effiziente und standardisierte Softwarebereitstellung. Die Folge sind fragmentierte Entwicklungsprozesse, ein hoher manueller Aufwand sowie eine eingeschränkte Developer Experience.

Plattform-Engineering hat sich in den letzten Jahren als vielversprechender Ansatz etabliert, um diesen Herausforderungen zu begegnen. Durch die gezielte Abstraktion und Standardisierung wiederkehrender Entwicklungs- und Betriebsaufgaben sollen Entwicklungsteams entlastet und befähigt werden, sich stärker auf die eigentliche Wertschöpfung zu konzentrieren. Zentrales Element dieses Ansatzes ist die Interne Entwicklerplattform (Internal Developer Platform, IDP), die Self-Service-Funktionalitäten innerhalb klar definierter Governance-Rahmenbedingungen bereitstellt.

Obwohl interne Entwicklerplattformen zunehmend in der industriellen Praxis Anwendung finden, besteht weiterhin ein signifikanter Forschungsbedarf hinsichtlich ihrer konzeptionellen Ausgestaltung, architektonischen Prinzipien und organisatorischen Einbettung. Insbesondere ist bislang unzureichend untersucht, wie sich unternehmensweite Standardisierung, Sicherheits- und Compliance-Anforderungen mit der notwendigen Flexibilität für unterschiedliche Entwicklungsteams in Einklang bringen lassen. Vor diesem Hintergrund adressiert die vorliegende Masterarbeit diese Forschungslücke und leistet einen Beitrag zur strukturierten Einordnung von Plattform-Engineering-Ansätzen im Kontext der Developer Experience.

---

## 1.2 Zielsetzung der Arbeit

Ziel dieser Masterarbeit ist es, zu untersuchen, wie moderne Plattform-Engineering-Ansätze zur Konzeption einer Internen Entwicklerplattform beitragen können, die die Developer Experience verbessert und gleichzeitig Anforderungen an Standardisierung, Sicherheit, Compliance sowie CI/CD-Prozesse erfüllt.

Zu diesem Zweck werden zunächst bestehende Konzepte, Designprinzipien und architektonische Muster des Platform Engineering sowie deren Einfluss auf die Developer Experience analysiert. Darauf aufbauend wird der aktuelle Status quo relevanter Entwicklungs- und Bereitstellungsprozesse im industriellen Umfeld exemplarisch betrachtet, um zentrale Herausforderungen und Zielkonflikte zu identifizieren.

Basierend auf den gewonnenen Erkenntnissen wird ein konzeptionelles und architektonisches Zielbild einer Internen Entwicklerplattform entwickelt. Dieses Zielbild beschreibt zentrale Plattformkomponenten, Integrationsmechanismen sowie Governance- und Sicherheitsleitplanken und berücksichtigt sowohl unternehmensweite Standards als auch teamspezifische Anforderungen. Zur exemplarischen Validierung ausgewählter Konzepte wird ein prototypischer Plattformansatz entworfen, der der Veranschaulichung und Bewertung der entwickelten Konzeption dient.

Abschließend werden geeignete Kriterien und Kennzahlen zur Bewertung der Developer Experience diskutiert sowie Handlungsempfehlungen und Entwicklungsperspektiven für die Einführung und Weiterentwicklung einer Internen Entwicklerplattform abgeleitet.

---

## 1.3 Forschungsfrage und Unterforschungsfragen

Vor dem Hintergrund der dargestellten Motivation und Zielsetzung wird die folgende zentrale Forschungsfrage formuliert:

**Wie können moderne Plattform-Engineering-Ansätze zur Konzeption einer Internen Entwicklerplattform (IDP) beitragen, die die Developer Experience verbessert und gleichzeitig Standardisierung, Sicherheit und Compliance mit der notwendigen Flexibilität für heterogene Entwicklungsteams in Einklang bringt?**

Zur strukturierten Beantwortung dieser Forschungsfrage werden folgende Unterforschungsfragen herangezogen:

- Welche Konzepte, Prinzipien und architektonischen Muster des Platform Engineering werden in der wissenschaftlichen Literatur und in industriellen Best Practices zur Gestaltung Interner Entwicklerplattformen beschrieben?
- Wie wird Developer Experience im Kontext moderner Softwareentwicklung definiert, und welche Faktoren sowie Metriken eignen sich zu ihrer Bewertung innerhalb einer Internen Entwicklerplattform?
- Welche Herausforderungen und Defizite bestehen im aktuellen Status quo der Entwicklungs- und Bereitstellungsprozesse in Bezug auf die Developer Experience?
- Welche Zielkonflikte bestehen zwischen Standardisierung, Sicherheits- und Compliance-Anforderungen sowie der notwendigen Flexibilität für unterschiedliche Entwicklungsteams?
- Wie kann ein konzeptionelles und architektonisches Zielbild einer Internen Entwicklerplattform gestaltet werden, das diesen Anforderungen gerecht wird?

---

## 1.4 Aufbau der Arbeit

Die vorliegende Arbeit ist wie folgt aufgebaut: Kapitel 2 vermittelt die theoretischen Grundlagen zu moderner Softwareentwicklung, Platform Engineering, Internen Entwicklerplattformen und Developer Experience. Kapitel 3 beschreibt das methodische Vorgehen und das zugrunde liegende Forschungsdesign.

In Kapitel 4 wird der Status quo der betrachteten Entwicklungs- und Bereitstellungsprozesse analysiert und zentrale Herausforderungen sowie Zielkonflikte herausgearbeitet. Darauf aufbauend entwickelt Kapitel 5 ein konzeptionelles und architektonisches Zielbild einer Internen Entwicklerplattform. Kapitel 6 widmet sich der exemplarischen Validierung ausgewählter Konzepte anhand eines prototypischen Plattformansatzes.

Abschließend diskutiert Kapitel 7 die gewonnenen Ergebnisse im Kontext der Forschungsfrage und bestehender Literatur, bevor Kapitel 8 die Arbeit zusammenfasst und einen Ausblick auf zukünftige Forschungs- und Entwicklungspotenziale gibt.


# 2. Theoretische Grundlagen

## 2.1 Moderne Softwareentwicklung und steigende Komplexität

Die Softwareentwicklung hat sich in den vergangenen Jahren grundlegend verändert. Monolithische Anwendungen werden zunehmend durch verteilte, cloud-native Architekturen ersetzt, die auf Microservices, Containern und dynamischer Infrastruktur basieren. Diese Entwicklung ermöglicht eine höhere Skalierbarkeit, Flexibilität und Innovationsgeschwindigkeit, führt jedoch gleichzeitig zu einer erheblichen Zunahme der technischen und organisatorischen Komplexität.

Entwicklungsteams sind heute nicht mehr ausschließlich für die Implementierung fachlicher Logik verantwortlich, sondern müssen sich verstärkt mit Aspekten wie Infrastrukturprovisionierung, Deployment-Strategien, Monitoring, Sicherheit und Compliance auseinandersetzen. Insbesondere Continuous Integration und Continuous Delivery (CI/CD) erfordern ein hohes Maß an Automatisierung, Standardisierung und technischer Reife. Die Vielzahl an Werkzeugen, Technologien und Schnittstellen erhöht dabei die kognitive Belastung der Entwicklerinnen und Entwickler und erschwert effiziente Entwicklungsprozesse.

Diese Entwicklung stellt insbesondere große Organisationen mit heterogenen Teams vor die Herausforderung, Entwicklungsumgebungen konsistent, sicher und zugleich flexibel bereitzustellen. Vor diesem Hintergrund gewinnen strukturierte Ansätze zur Reduktion von Komplexität und zur Unterstützung von Entwicklungsteams zunehmend an Bedeutung.

---

## 2.2 Platform Engineering: Begriffe, Konzepte und Abgrenzung

Platform Engineering beschreibt einen organisationsweiten Ansatz zur systematischen Bereitstellung wiederverwendbarer Plattformdienste, die Entwicklungsteams in Form von standardisierten, selbstbedienbaren Funktionalitäten zur Verfügung gestellt werden. Ziel ist es, Entwicklungs- und Betriebsaufgaben zu abstrahieren und zu vereinheitlichen, um Entwicklungsteams von wiederkehrenden, nicht-wertschöpfenden Tätigkeiten zu entlasten.

Im Gegensatz zu klassischen DevOps-Ansätzen, die häufig stark team- oder projektbezogen umgesetzt werden, verfolgt Platform Engineering eine langfristige, produktorientierte Perspektive. Eine dedizierte Plattformorganisation übernimmt die Verantwortung für Design, Betrieb und Weiterentwicklung der Plattform, während Entwicklungsteams diese als Produkt konsumieren. Zentrale Prinzipien sind dabei Produktdenken, Wiederverwendbarkeit, Automatisierung sowie eine klare Trennung von Verantwortlichkeiten.

Platform Engineering grenzt sich zudem von reinen Infrastruktur- oder Tooling-Ansätzen ab, da der Fokus nicht auf einzelnen Technologien liegt, sondern auf der ganzheitlichen Gestaltung einer Entwicklerplattform, die technische, organisatorische und prozessuale Aspekte integriert.

---

## 2.3 Internal Developer Platforms (IDP)

Eine Interne Entwicklerplattform (Internal Developer Platform, IDP) stellt die konkrete Ausprägung des Platform-Engineering-Ansatzes dar. Sie umfasst eine kuratierte Menge an Tools, Services, Schnittstellen und Workflows, die Entwicklungsteams über Self-Service-Mechanismen nutzen können. Ziel einer IDP ist es, die Komplexität der zugrunde liegenden Infrastruktur zu verbergen und gleichzeitig konsistente, sichere und konforme Entwicklungsprozesse zu ermöglichen.

Typische Bestandteile einer IDP sind unter anderem CI/CD-Pipelines, Infrastruktur-Templates, Service-Kataloge, Deployment-Mechanismen, Observability-Werkzeuge sowie Governance- und Sicherheitsrichtlinien. Die Plattform fungiert dabei als vermittelnde Schicht zwischen Entwicklungsteams und der zugrunde liegenden Infrastruktur.

Ein zentrales Merkmal von IDPs ist die Balance zwischen Standardisierung und Flexibilität. Während unternehmensweite Standards und Compliance-Anforderungen eingehalten werden müssen, benötigen Entwicklungsteams ausreichend Freiraum, um unterschiedliche Anwendungsfälle effizient umzusetzen. Die konzeptionelle Gestaltung dieser Balance stellt eine der zentralen Herausforderungen bei der Entwicklung interner Entwicklerplattformen dar.

---

## 2.4 Developer Experience (DX)

Developer Experience bezeichnet die Gesamtheit der Wahrnehmungen, Erfahrungen und Interaktionen, die Entwicklerinnen und Entwickler im Umgang mit Entwicklungswerkzeugen, Plattformen und Prozessen machen. Eine positive Developer Experience gilt als wesentlicher Faktor für Produktivität, Codequalität, Innovationsfähigkeit und Mitarbeiterzufriedenheit.

Im Kontext von Platform Engineering und Internal Developer Platforms umfasst die Developer Experience insbesondere Aspekte wie Benutzerfreundlichkeit von Self-Service-Schnittstellen, Transparenz von Prozessen, Zuverlässigkeit und Konsistenz von Toolchains sowie die Geschwindigkeit von Feedback-Zyklen. Auch eine verständliche Dokumentation, klare Ownership-Strukturen und eine reduzierte kognitive Belastung tragen wesentlich zu einer positiven DX bei.

Zur Bewertung der Developer Experience werden sowohl qualitative als auch quantitative Metriken herangezogen. Neben subjektiven Wahrnehmungen wie Zufriedenheit oder wahrgenommener Autonomie spielen objektive Kennzahlen wie Durchlaufzeiten von Deployments, Fehlerquoten oder Time-to-Market eine zentrale Rolle. Die Auswahl geeigneter KPIs ist entscheidend, um den Einfluss von Plattform-Engineering-Initiativen messbar zu machen.

---

## 2.5 Platform Engineering im Spannungsfeld von Standardisierung und Flexibilität

Ein zentrales Gestaltungsproblem beim Aufbau Interner Entwicklerplattformen liegt im Spannungsfeld zwischen unternehmensweiter Standardisierung und der notwendigen Flexibilität für heterogene Entwicklungsteams. Einerseits sind standardisierte Prozesse, Architekturen und Sicherheitsmechanismen erforderlich, um Skalierbarkeit, Compliance und Wartbarkeit sicherzustellen. Andererseits benötigen Teams ausreichend Gestaltungsspielraum, um unterschiedliche fachliche Anforderungen, Technologien und Arbeitsweisen effizient umzusetzen.

Platform Engineering adressiert dieses Spannungsfeld durch modulare Architekturen, konfigurierbare Self-Service-Angebote und klar definierte Governance-Leitplanken. Anstatt individuelle Lösungen pro Team zuzulassen, werden standardisierte Bausteine bereitgestellt, die teamspezifisch kombiniert und angepasst werden können. Auf diese Weise wird sowohl Konsistenz als auch Autonomie gefördert.

Die erfolgreiche Ausbalancierung von Standardisierung und Flexibilität ist ein wesentlicher Erfolgsfaktor für die Akzeptanz einer IDP und wirkt sich unmittelbar auf die Developer Experience aus.

---

## 2.6 CI/CD als Kernbestandteil Interner Entwicklerplattformen

Continuous Integration und Continuous Delivery bilden das Rückgrat moderner Softwarebereitstellung und sind eng mit Platform-Engineering-Ansätzen verknüpft. In einer Internen Entwicklerplattform werden CI/CD-Funktionalitäten nicht isoliert betrachtet, sondern als integrierte Plattformservices angeboten.

Durch standardisierte CI/CD-Pipelines können wiederkehrende Aufgaben wie Build, Test, Sicherheitsprüfungen und Deployments automatisiert und vereinheitlicht werden. Gleichzeitig ermöglichen Self-Service-Mechanismen Entwicklungsteams, neue Services oder Änderungen eigenständig bereitzustellen, ohne tiefgehende Kenntnisse der zugrunde liegenden Infrastruktur besitzen zu müssen.

Die Integration von CI/CD in eine IDP trägt wesentlich zur Reduktion manueller Tätigkeiten, zur Erhöhung der Prozessqualität sowie zur Verbesserung der Developer Experience bei.

---

## 2.7 Kubernetes Experience (KX) und Infrastrukturabstraktion

Kubernetes hat sich als De-facto-Standard für den Betrieb containerisierter Anwendungen etabliert, bringt jedoch eine erhebliche Komplexität mit sich. Konzepte wie Pods, Services, Ingress, Helm oder Operatoren stellen hohe Anforderungen an das technische Know-how von Entwicklerinnen und Entwicklern.

Im Rahmen von Platform Engineering wird Kubernetes daher häufig nicht direkt exponiert, sondern über abstrahierende Plattformmechanismen zugänglich gemacht. Die sogenannte Kubernetes Experience (KX) beschreibt dabei die Art und Weise, wie Entwickler mit Kubernetes-basierten Plattformen interagieren. Ziel ist es, die Komplexität der Orchestrierungsplattform zu reduzieren und dennoch deren Vorteile nutzbar zu machen.

Eine gut gestaltete KX ist eng mit der Developer Experience verknüpft und stellt einen wesentlichen Baustein moderner Interner Entwicklerplattformen dar.

---

## 2.8 Zusammenfassung der theoretischen Grundlagen

Die in diesem Kapitel dargestellten theoretischen Grundlagen bilden das Fundament für die weitere Analyse und Konzeption einer Internen Entwicklerplattform. Moderne Softwareentwicklung ist durch steigende Komplexität gekennzeichnet, die neue organisatorische und technische Ansätze erforderlich macht.

Platform Engineering und Internal Developer Platforms stellen einen strukturierten Ansatz dar, um diese Komplexität zu adressieren und die Developer Experience nachhaltig zu verbessern. Die theoretischen Konzepte zu DX, CI/CD, Standardisierung und Infrastrukturabstraktion liefern zentrale Bezugsrahmen für die nachfolgenden Kapitel, insbesondere für die Analyse des Status quo sowie die Entwicklung eines konzeptionellen Zielbildes.


# 3. Methodik und Forschungsdesign

## 3.1 Forschungsmethodischer Ansatz

Ziel dieser Masterarbeit ist es, einen wissenschaftlich fundierten Beitrag zur Analyse und Konzeption einer Internen Entwicklerplattform (IDP) im Kontext moderner Plattform-Engineering-Ansätze zu leisten. Die Forschungsfrage adressiert ein sozio-technisches Problemfeld, in dem technische Architekturentscheidungen, organisatorische Rahmenbedingungen sowie die Wahrnehmung und Arbeitsweise von Entwicklerteams eng miteinander verknüpft sind. Vor diesem Hintergrund wird ein **gestaltungsorientierter Forschungsansatz** aus der Wirtschaftsinformatik herangezogen, der sich am Paradigma der **Design Science Research (DSR)** orientiert.

Design Science Research verfolgt das Ziel, durch die Entwicklung und Evaluation von Artefakten (z. B. Modelle, Methoden, Architekturen oder Prototypen) Erkenntnisfortschritt zu generieren und zugleich praxisrelevante Problemlösungen bereitzustellen. Im Rahmen dieser Arbeit besteht das zentrale Artefakt in einem **konzeptionellen Zielbild** (Architektur- und Designkonzeption) einer IDP, ergänzt um einen **prototypischen Plattformansatz** zur exemplarischen Veranschaulichung ausgewählter Konzepte.

Die Arbeit kombiniert dabei (1) eine **theoriegeleitete Analyse** (Literatur und Best Practices) mit (2) einer **kontextbezogenen Exploration** im industriellen Umfeld (Experteninterviews). Das Erkenntnisinteresse liegt nicht in einer statistischen Generalisierung, sondern in der nachvollziehbaren Herleitung von Designprinzipien, Architekturmuster und Erfolgsfaktoren, die im betrachteten Kontext anwendbar sind und zugleich in die wissenschaftliche Diskussion eingeordnet werden können.

---

## 3.2 Systematische Literaturrecherche

Die theoretische Fundierung der Arbeit erfolgt mittels **systematischer Literaturrecherche**, um den Stand der Forschung zu Platform Engineering, Internal Developer Platforms und Developer Experience strukturiert zu erfassen. Aufgrund der dynamischen Entwicklung des Themenfeldes werden neben peer-reviewter Literatur auch ausgewählte, qualitativ hochwertige Quellen aus der Praxis herangezogen, sofern deren Relevanz und Nachvollziehbarkeit gegeben ist.

Die Literaturrecherche folgt einem transparenten Vorgehen:

- **Datenbanken und Quellenräume:** Relevante wissenschaftliche Datenbanken (z. B. IEEE Xplore, ACM Digital Library, SpringerLink, ScienceDirect) sowie Suchmaschinen (Google Scholar) werden systematisch genutzt.
- **Suchstrategie:** Es werden Suchstrings aus Schlüsselbegriffen und Synonymen gebildet, u. a. *"platform engineering"*, *"internal developer platform"*, *"developer experience"*, *"self-service"*, *"golden path"*, *"developer portal"*, *"CI/CD platform"*, *"governance"*, *"compliance"*.
- **Ein- und Ausschlusskriterien:** Eingeschlossen werden insbesondere aktuelle Arbeiten mit klarer methodischer Herleitung und hoher thematischer Passung. Ausgeschlossen werden Quellen ohne nachvollziehbare Herkunft, mit rein werblichem Charakter oder ohne Bezug zur Forschungsfrage.
- **Screening und Auswahl:** Die Auswahl erfolgt stufenweise (Titel/Abstract → Volltextprüfung). Relevante Aussagen werden extrahiert und thematisch kodiert (z. B. Designprinzipien, Architekturmuster, organisatorische Erfolgsfaktoren, DX-Messansätze).

Die Ergebnisse der Literaturrecherche bilden die Grundlage für die Ableitung eines theoretischen Bezugsrahmens, der in die Status-quo-Analyse sowie in die Konzeption des Zielbildes einfließt.

---

## 3.3 Analyse industrieller Best Practices

Da Platform Engineering und IDPs stark durch industrielle Praxis geprägt sind, wird die wissenschaftliche Literatur um eine **strukturierte Analyse industrieller Best Practices** ergänzt. Ziel ist es, wiederkehrende Muster und Erfolgsfaktoren zu identifizieren, die in der Praxis etabliert sind, jedoch in wissenschaftlichen Publikationen teilweise noch nicht umfassend abgebildet werden.

Als Best-Practice-Quellen werden insbesondere herangezogen:

- technische Leitfäden, Architekturartikel und Whitepaper etablierter Technologieunternehmen,
- Referenzarchitekturen und Frameworks (z. B. Developer Portals, Service Catalogs, Golden Paths),
- Veröffentlichungen von Standardisierungs- und Community-Initiativen, sofern methodisch nachvollziehbar.

Die Analyse erfolgt anhand eines Bewertungsrasters, das u. a. folgende Dimensionen berücksichtigt:

- **Architektur- und Designprinzipien** (z. B. Modularität, Abstraktion, Wiederverwendbarkeit),
- **Self-Service-Mechanismen** und „Guardrails“ (Governance, Security, Compliance),
- **Adoption & Operating Model** (Produktdenken, Ownership, Plattformorganisation),
- **Messbarkeit** (DX-Metriken, Prozess- und Qualitätskennzahlen).

Die Best-Practice-Erkenntnisse werden kritisch eingeordnet (Übertragbarkeit, Kontextabhängigkeit, Limitationen) und mit der Literatur trianguliert, um eine robuste Grundlage für die Konzeption zu schaffen.

---

## 3.4 Qualitative Erhebungsmethoden (Experteninterviews)

Zur kontextbezogenen Ergänzung der theoretischen Analyse werden **leitfadengestützte Experteninterviews** durchgeführt. Ziel ist es, den Status quo im betrachteten Umfeld besser zu verstehen, zentrale Pain Points aus Sicht relevanter Stakeholder zu identifizieren und Anforderungen an eine IDP abzuleiten.

**Stichprobe und Auswahl:** Die Auswahl der Interviewpartner erfolgt gezielt (purposive sampling) auf Basis ihrer Rollen, Erfahrungen und ihres Bezugs zu Plattform-Engineering-Themen. Dazu zählen insbesondere Mitarbeitende aus DevOps/Platform Engineering, Softwareentwicklung sowie angrenzenden Bereichen (z. B. Architektur, Security/Compliance).

**Interviewdesign:** Es werden halbstrukturierte Interviews eingesetzt, um einerseits Vergleichbarkeit zwischen Interviews zu gewährleisten und andererseits Raum für kontextspezifische Vertiefungen zu lassen. Der Interviewleitfaden orientiert sich an den Unterforschungsfragen und umfasst u. a.:

- aktuelle Entwicklungs- und Bereitstellungsprozesse (CI/CD, Toolchain),
- wahrgenommene Developer Experience und kognitive Belastung,
- Herausforderungen bei Standardisierung, Sicherheit und Compliance,
- Anforderungen an Self-Service, Integrationsmechanismen und Governance,
- Erfolgsfaktoren und Risiken für Adoption.

**Auswertung:** Die Interviews werden protokolliert bzw. transkribiert (je nach organisatorischen Rahmenbedingungen) und mittels qualitativer Inhaltsanalyse ausgewertet. Hierbei wird ein gemischt induktiv-deduktives Kategoriensystem genutzt: deduktive Kategorien aus dem theoretischen Bezugsrahmen, induktive Kategorien aus dem empirischen Material. Die Ergebnisse fließen in die Status-quo-Analyse (Kapitel 4) sowie in die Ableitung der Designprinzipien und des Zielbildes (Kapitel 5) ein.

---

## 3.5 Methodische Limitationen

Die Arbeit unterliegt typischen Limitationen konzeptionell-gestaltungsorientierter Forschung im industriellen Kontext.

- **Kontextabhängigkeit:** Die Ergebnisse sind an den betrachteten organisatorischen und technischen Kontext gebunden. Eine vollständige Generalisierbarkeit ist nicht intendiert; vielmehr wird analytische Übertragbarkeit durch transparente Herleitung und Diskussion angestrebt.
- **Datenbasis der Interviews:** Umfang und Zusammensetzung der Interviews können die Perspektivenvielfalt begrenzen. Zudem können organisationaler Bias und soziale Erwünschtheit Einfluss auf Aussagen haben.
- **Best-Practice-Quellen:** Industrielle Best Practices sind teilweise nicht peer-reviewed. Ihre Nutzung erfordert daher eine kritische Bewertung hinsichtlich Nachvollziehbarkeit, Kontext und möglicher Interessenslagen.
- **Prototypischer Ansatz:** Die prototypische Validierung dient der Veranschaulichung und konzeptionellen Reflexion. Sie ersetzt keine produktive Implementierung oder umfassende empirische Wirkungsmessung.

Diese Limitationen werden im weiteren Verlauf der Arbeit reflektiert und bei der Interpretation der Ergebnisse berücksichtigt.


# Anhang A: Interviewleitfaden

## A.1 Ziel des Interviewleitfadens

Der Interviewleitfaden dient der strukturierten Durchführung leitfadengestützter Experteninterviews im Kontext dieser Masterarbeit. Ziel der Interviews ist es, qualitative Einblicke in den aktuellen Status quo, bestehende Herausforderungen sowie Anforderungen und Erwartungen im Zusammenhang mit Platform Engineering, Interner Entwicklerplattformen (IDP) und Developer Experience zu gewinnen.

Die Interviews richten sich an Expertinnen und Experten aus den Bereichen DevOps, Platform Engineering, Softwareentwicklung, IT-Architektur sowie angrenzenden Funktionen. Der Leitfaden ist bewusst halbstrukturiert aufgebaut, um sowohl Vergleichbarkeit zwischen den Interviews als auch Raum für kontextspezifische Vertiefungen zu ermöglichen.

---

## A.2 Struktur des Interviewleitfadens

Der Leitfaden gliedert sich in fünf thematische Blöcke:
1. Einordnung der Rolle und des Kontexts
2. Aktuelle Entwicklungs- und Bereitstellungsprozesse (Status quo)
3. Developer Experience und KX-Infrastruktur
4. Anforderungen und Erwartungen an eine Interne Entwicklerplattform
5. Einschätzung von Nutzen, Risiken und Erfolgsfaktoren

---

## A.3 Interviewfragen

### Block 1: Rolle und Kontext

1. Welche Rolle haben Sie aktuell im Unternehmen und in welchem Umfeld (z. B. DevOps, Entwicklung, Plattformbetrieb) sind Sie tätig?
2. In welchem Umfang sind Sie in Entwicklungs-, Build- oder Deploymentprozesse eingebunden?

### Block 2: Status quo der Entwicklungs- und Bereitstellungsprozesse

3. Wie sind die aktuellen Entwicklungs- und Bereitstellungsprozesse (z. B. CI/CD) in Ihrem Umfeld organisiert?
4. Welche Tools, Plattformen oder Infrastrukturen nutzen Sie regelmäßig für Build, Deployment und Betrieb?
5. Wo sehen Sie aktuell die größten Herausforderungen oder Ineffizienzen in diesen Prozessen?

### Block 3: Developer Experience und KX

6. Wie würden Sie die aktuelle Developer Experience in Ihrem Arbeitsumfeld beschreiben?
7. Welche Tätigkeiten empfinden Sie als besonders zeitaufwendig oder kognitiv belastend?
8. Inwiefern spielt Kubernetes bzw. die zugrunde liegende Infrastruktur eine Rolle in Ihrer täglichen Arbeit?
9. Welche Aspekte der aktuellen KX-Infrastruktur unterstützen Sie gut, und wo sehen Sie Verbesserungspotenzial?

### Block 4: Anforderungen an eine Interne Entwicklerplattform

10. Welche Funktionen oder Services sollte eine Interne Entwicklerplattform Ihrer Meinung nach unbedingt bereitstellen?
11. Welche Self-Service-Funktionalitäten würden Ihre tägliche Arbeit am stärksten erleichtern?
12. Wie wichtig sind aus Ihrer Sicht Standardisierung, Sicherheit und Compliance im Vergleich zur Flexibilität für individuelle Teamanforderungen?
13. Welche Governance- oder Leitplanken sind aus Ihrer Sicht notwendig, um eine Plattform sinnvoll nutzbar zu machen?

### Block 5: Nutzen, Akzeptanz und Erfolgsfaktoren

14. Welchen konkreten Nutzen erwarten Sie von einer Internen Entwicklerplattform?
15. Welche Faktoren würden die Akzeptanz und Nutzung einer solchen Plattform aus Ihrer Sicht fördern oder hemmen?
16. Welche Risiken oder Herausforderungen sehen Sie bei der Einführung einer Internen Entwicklerplattform?

---

## A.4 Mapping der Interviewfragen zu den Unterforschungsfragen

| Unterforschungsfrage (UFQ) | Inhaltlicher Fokus | Zugeordnete Interviewfragen |
|---------------------------|-------------------|-----------------------------|
| UFQ1 | Konzepte und Prinzipien des Platform Engineering | 10, 11, 13 |
| UFQ2 | Developer Experience und Bewertung | 6, 7, 14 |
| UFQ3 | Status quo und Herausforderungen | 3, 4, 5, 8, 9 |
| UFQ4 | Zielkonflikte Standardisierung vs. Flexibilität | 12, 16 |
| UFQ5 | Konzeption und Zielbild einer IDP | 10, 11, 13, 15 |
| UFQ6 | Exemplarische Validierung und Nutzen | 14, 15 |
| UFQ7 | Handlungsempfehlungen und Erfolgsfaktoren | 15, 16 |

---

## A.6 Simulation möglicher Interviewantworten (Erwartungshorizont)

*Hinweis: Die folgenden Antworten stellen eine realistische, verdichtete Simulation typischer Expertenaussagen dar. Sie dienen ausschließlich der Vorbereitung, Erwartungsklärung und späteren Kategorisierung im Rahmen der qualitativen Inhaltsanalyse.*

### Block 1: Rolle und Kontext

**Frage 1**  
Antwort A: „Ich arbeite als DevOps Engineer und bin hauptsächlich für CI/CD-Pipelines sowie den Betrieb containerbasierter Anwendungen verantwortlich.“  
Antwort B: „Meine Rolle liegt im Platform Engineering, insbesondere in der Bereitstellung zentraler Services für mehrere Entwicklungsteams.“

**Frage 2**  
Antwort A: „Ich bin stark in Build- und Deploymentprozesse eingebunden und unterstütze mehrere Teams bei Releases.“  
Antwort B: „Mein Fokus liegt eher beratend, ich definiere Standards und unterstütze Teams bei komplexeren Deployments.“

### Block 2: Status quo

**Frage 3**  
Antwort A: „CI/CD ist grundsätzlich etabliert, aber jedes Team nutzt eigene Pipelines und Konventionen.“  
Antwort B: „Viele Prozesse sind automatisiert, allerdings historisch gewachsen und wenig standardisiert.“

**Frage 4**  
Antwort A: „Wir nutzen GitLab CI, Kubernetes und verschiedene Skripte für Infrastrukturaufgaben.“  
Antwort B: „Neben zentralen Tools existieren viele teamindividuelle Lösungen.“

**Frage 5**  
Antwort A: „Der größte Aufwand entsteht durch manuelle Abstimmungen und fehlende Standards.“  
Antwort B: „Troubleshooting kostet viel Zeit, da Wissen stark verteilt ist.“

### Block 3: Developer Experience und KX

**Frage 6**  
Antwort A: „Die Developer Experience ist funktional, aber nicht besonders intuitiv.“  
Antwort B: „Viele Prozesse funktionieren, fühlen sich aber unnötig komplex an.“

**Frage 7**  
Antwort A: „Das Erstellen und Pflegen von CI/CD-Konfigurationen ist sehr zeitaufwendig.“  
Antwort B: „Der Umgang mit Kubernetes-Konfigurationen verursacht viel kognitive Last.“

**Frage 8**  
Antwort A: „Kubernetes ist zentral, aber nicht jeder Entwickler versteht die Konzepte vollständig.“  
Antwort B: „Wir versuchen, Kubernetes zu abstrahieren, was aktuell nur teilweise gelingt.“

**Frage 9**  
Antwort A: „Stabilität und Skalierbarkeit funktionieren gut.“  
Antwort B: „Die Benutzerfreundlichkeit und Dokumentation könnten deutlich verbessert werden.“

### Block 4: Anforderungen an eine IDP

**Frage 10**  
Antwort A: „Ein zentrales Developer Portal mit klaren Einstiegspunkten wäre sehr hilfreich.“  
Antwort B: „Standardisierte Templates und Services sollten zentral bereitgestellt werden.“

**Frage 11**  
Antwort A: „Self-Service für Deployments und Infrastruktur wäre ein großer Gewinn.“  
Antwort B: „Automatisierte Provisionierung mit vordefinierten Leitplanken.“

**Frage 12**  
Antwort A: „Standardisierung ist wichtig, darf aber nicht zu starr sein.“  
Antwort B: „Sicherheit und Compliance müssen immer gewährleistet sein, auch wenn das Flexibilität kostet.“

**Frage 13**  
Antwort A: „Klare Rollen, Verantwortlichkeiten und Freigabeprozesse sind notwendig.“  
Antwort B: „Technische Guardrails sind besser als manuelle Kontrollen.“

### Block 5: Nutzen und Erfolgsfaktoren

**Frage 14**  
Antwort A: „Schnellere Deployments und weniger manuelle Arbeit.“  
Antwort B: „Mehr Fokus auf fachliche Entwicklung statt Infrastruktur.“

**Frage 15**  
Antwort A: „Gute Dokumentation und sichtbarer Mehrwert fördern die Akzeptanz.“  
Antwort B: „Zu komplexe Plattformen werden schnell umgangen.“

**Frage 16**  
Antwort A: „Akzeptanzprobleme bei zu starker Einschränkung.“  
Antwort B: „Hoher initialer Aufwand bei Aufbau und Einführung.“

---

Diese simulierten Antworten dienen als Erwartungshorizont und Grundlage für die spätere Kategorisierung, Verdichtung und Analyse im Rahmen von Kapitel 4.


# 4. Analyse des Status quo

Ziel dieses Kapitels ist die strukturierte Analyse des aktuellen Zustands der Entwicklungs- und Bereitstellungslandschaft im betrachteten industriellen Kontext. Die Analyse basiert auf der Auswertung der Experteninterviews, den in Kapitel 2 definierten theoretischen Grundlagen sowie den in Kapitel 3 beschriebenen methodischen Ansätzen. Der Fokus liegt dabei auf der bestehenden KX-Infrastruktur, den CI/CD-Prozessen sowie der wahrgenommenen Developer Experience.

---

## 4.1 Einordnung des organisatorischen und technischen Kontexts

Das betrachtete Umfeld ist durch eine heterogene Softwarelandschaft geprägt, in der mehrere Entwicklungsteams parallel an unterschiedlichen Anwendungen und Services arbeiten. Die Organisation folgt einem DevOps-orientierten Ansatz, bei dem Entwicklung und Betrieb eng miteinander verzahnt sind. Gleichzeitig existieren zentrale Plattform- und Infrastrukturteams, die übergreifende Services und Standards bereitstellen.

Die zugrunde liegende Infrastruktur basiert maßgeblich auf containerisierten Anwendungen und Kubernetes als Orchestrierungsplattform. CI/CD-Prozesse sind grundsätzlich etabliert und bilden die Grundlage für automatisierte Build-, Test- und Deploymentabläufe. Dennoch zeigt sich, dass viele Prozesse historisch gewachsen sind und sich zwischen Teams in Ausprägung und Reifegrad unterscheiden.

---

## 4.2 Analyse der bestehenden CI/CD-Prozesse

Die Auswertung der Interviews zeigt, dass CI/CD als zentrales Element der Softwarebereitstellung fest verankert ist. Nahezu alle befragten Expertinnen und Experten nutzen automatisierte Pipelines für Build- und Deploymentprozesse. Allerdings unterscheiden sich die konkreten Implementierungen deutlich zwischen den Teams.

Während einige Teams weitgehend standardisierte Pipelines verwenden, existieren in anderen Bereichen stark individualisierte Konfigurationen. Diese Heterogenität führt zu erhöhtem Wartungsaufwand, erschwert teamübergreifende Zusammenarbeit und erhöht die Abhängigkeit von individuellem Expertenwissen. Zudem werden wiederkehrende Aufgaben wie Sicherheitsprüfungen oder Infrastrukturkonfigurationen nicht durchgängig automatisiert.

---

## 4.3 Analyse der KX-Infrastruktur

Die Kubernetes Experience (KX) stellt einen zentralen Bestandteil der aktuellen Entwicklungsumgebung dar. Kubernetes wird von den meisten Teams als leistungsfähige, jedoch komplexe Plattform wahrgenommen. Insbesondere Entwicklerinnen und Entwickler ohne tiefgehende Kubernetes-Kenntnisse empfinden die Vielzahl an Konzepten und Konfigurationsoptionen als herausfordernd.

Die Interviews verdeutlichen, dass bereits Ansätze zur Abstraktion der Kubernetes-Komplexität existieren, diese jedoch nicht konsistent umgesetzt sind. Während grundlegende Stabilität und Skalierbarkeit gewährleistet sind, fehlen häufig einheitliche Schnittstellen, verständliche Dokumentation sowie standardisierte Einstiegspunkte für neue Services.

---

## 4.4 Analyse der Developer Experience

Die wahrgenommene Developer Experience wird von den Befragten überwiegend als funktional, jedoch verbesserungswürdig beschrieben. Insbesondere die hohe kognitive Belastung durch infrastrukturelle Aufgaben wird als zentraler negativer Faktor genannt. Entwicklerinnen und Entwickler verbringen einen erheblichen Teil ihrer Zeit mit Konfigurations-, Abstimmungs- und Troubleshooting-Aufgaben.

Positiv hervorgehoben werden die grundsätzliche Automatisierung von Deployments sowie die technische Leistungsfähigkeit der Plattform. Negativ wirken sich hingegen fehlende Transparenz, uneinheitliche Toolchains und eine unzureichende Dokumentation auf die tägliche Arbeit aus.

---

## 4.5 Einordnung anhand von Developer-Experience-KPIs

Zur strukturierteren Bewertung der Developer Experience wird der Status quo entlang der in Kapitel 2.4 definierten KPIs eingeordnet. Die Interviewaussagen deuten darauf hin, dass insbesondere Prozess- und Durchlaufzeit-KPIs wie Time-to-Market und Deployment-Frequenz stark teamabhängig variieren.

Auch qualitative KPIs wie wahrgenommene Einfachheit, Transparenz und Zufriedenheit zeigen ein heterogenes Bild. Während erfahrene Teams mit hohem Automatisierungsgrad von bestehenden Lösungen profitieren, haben weniger spezialisierte Teams mit einer erhöhten Einstiegshürde zu kämpfen.

---

## 4.6 Zusammenfassung der Herausforderungen und Gap-Analyse

Zusammenfassend zeigt die Status-quo-Analyse mehrere zentrale Herausforderungen. Dazu zählen eine hohe Heterogenität der CI/CD-Prozesse, eine unzureichende Abstraktion der Kubernetes-Komplexität sowie eine eingeschränkte Developer Experience aufgrund fehlender Standardisierung und Transparenz.

Der Vergleich zwischen dem aktuellen Zustand und den in Kapitel 2 beschriebenen theoretischen Zielvorstellungen offenbart eine deutliche Lücke. Insbesondere fehlt eine zentrale, konsistente Plattformebene, die Self-Service-Funktionalitäten bereitstellt, Governance-Leitplanken integriert und die Developer Experience systematisch adressiert.

Diese identifizierten Defizite bilden die Grundlage für die im nächsten Kapitel entwickelte Konzeption einer Internen Entwicklerplattform.

# 5. Konzeption einer Internen Entwicklerplattform

Aufbauend auf den in Kapitel 4 identifizierten Herausforderungen und Defiziten wird in diesem Kapitel ein konzeptionelles Zielbild einer Internen Entwicklerplattform (Internal Developer Platform, IDP) entwickelt. Ziel ist es, eine Plattform zu konzipieren, die die Developer Experience nachhaltig verbessert und gleichzeitig unternehmensweite Anforderungen an Standardisierung, Sicherheit, Compliance und Skalierbarkeit berücksichtigt.

---

## 5.1 Zielsetzung und Designprinzipien der IDP

Die Konzeption der Internen Entwicklerplattform orientiert sich an klar definierten Zielsetzungen, die direkt aus der Status-quo-Analyse sowie aus den theoretischen Grundlagen abgeleitet sind. Zentrale Zielsetzung ist die Reduktion der kognitiven Belastung von Entwicklerinnen und Entwicklern durch Abstraktion infrastruktureller Komplexität, ohne dabei notwendige Flexibilität einzuschränken.

Aus dieser Zielsetzung lassen sich folgende übergeordnete Designprinzipien ableiten:

- **Self-Service statt Ticket-basierter Prozesse:** Entwicklerinnen und Entwickler sollen in die Lage versetzt werden, wiederkehrende Aufgaben eigenständig und standardisiert auszuführen.
- **Standardisierung mit konfigurierbarer Flexibilität:** Die Plattform stellt vordefinierte, geprüfte Bausteine bereit, die teamspezifisch angepasst werden können.
- **Security und Compliance by Design:** Sicherheits- und Compliance-Anforderungen sind integraler Bestandteil der Plattform und nicht nachgelagert.
- **Produktorientierung:** Die IDP wird als internes Produkt mit klarer Zielgruppe, Roadmap und Feedbackmechanismen verstanden.
- **Transparenz und Nachvollziehbarkeit:** Prozesse, Abhängigkeiten und Plattformfunktionen sind für Nutzerinnen und Nutzer verständlich dokumentiert.

---

## 5.2 Architektonisches Gesamtbild

Das architektonische Zielbild der Internen Entwicklerplattform basiert auf einer modularen Schichtenarchitektur, die eine klare Trennung von Verantwortlichkeiten ermöglicht. Die Plattform fungiert als vermittelnde Ebene zwischen Entwicklungsteams und der zugrunde liegenden Infrastruktur.

Auf unterster Ebene befindet sich die Infrastruktur- und Laufzeitumgebung, bestehend aus Cloud- oder On-Premise-Ressourcen sowie Kubernetes als Orchestrierungsplattform. Darauf aufbauend werden plattformnahe Basisdienste bereitgestellt, etwa für CI/CD, Observability, Logging und Sicherheitsprüfungen.

Die zentrale Plattformebene abstrahiert diese Dienste und stellt sie über standardisierte Schnittstellen, Templates und Workflows bereit. Auf oberster Ebene befindet sich das Developer Interface, beispielsweise in Form eines Developer Portals, über das Entwicklerinnen und Entwickler auf Self-Service-Funktionalitäten zugreifen.

---

## 5.3 Zentrale Komponenten der Internen Entwicklerplattform

Die konzipierte IDP setzt sich aus mehreren zentralen Komponenten zusammen:

- **Developer Portal:** Zentrale Einstiegspunkt für Entwicklerinnen und Entwickler mit Zugriff auf Services, Dokumentation und Self-Service-Funktionen.
- **Service- und Template-Katalog:** Bereitstellung standardisierter Applikations-, Infrastruktur- und Pipeline-Templates.
- **CI/CD-Services:** Standardisierte, wiederverwendbare Pipelines für Build, Test und Deployment.
- **Infrastructure Abstraction Layer:** Abstraktion der Kubernetes- und Infrastrukturkomplexität über deklarative Schnittstellen.
- **Observability- und Monitoring-Komponenten:** Einheitliche Sicht auf Logs, Metriken und Traces.

Diese Komponenten sind lose gekoppelt und können schrittweise erweitert oder angepasst werden.

---

## 5.4 Governance, Sicherheit und Compliance

Ein zentrales Element der Plattformkonzeption ist die Integration von Governance-, Sicherheits- und Compliance-Anforderungen. Anstatt diese Aspekte außerhalb der Plattform zu adressieren, werden sie direkt in die bereitgestellten Services und Workflows integriert.

Technische Guardrails stellen sicher, dass nur geprüfte Konfigurationen, Images und Deployments verwendet werden. Richtlinien werden automatisiert durchgesetzt, beispielsweise durch Policy-as-Code-Ansätze. Gleichzeitig behalten Entwicklungsteams innerhalb dieser Leitplanken ausreichend Handlungsspielraum.

---

## 5.5 Berücksichtigung teamspezifischer Anforderungen

Die IDP ist so konzipiert, dass sie heterogene Anforderungen unterschiedlicher Teams unterstützt. Durch konfigurierbare Templates, optionale Erweiterungen und modulare Services können Teams die Plattform an ihre spezifischen Bedürfnisse anpassen, ohne zentrale Standards zu unterlaufen.

Dieser Ansatz fördert sowohl Akzeptanz als auch nachhaltige Nutzung der Plattform und trägt wesentlich zur Verbesserung der Developer Experience bei.

---

## 5.6 Zusammenfassung der Konzeption

Die entwickelte Konzeption einer Internen Entwicklerplattform adressiert die in Kapitel 4 identifizierten Defizite systematisch. Durch klare Designprinzipien, eine modulare Architektur und integrierte Governance-Mechanismen schafft die IDP die Grundlage für konsistente, sichere und effiziente Entwicklungsprozesse.

Im nächsten Kapitel wird der konzeptionelle Ansatz exemplarisch validiert und anhand eines prototypischen Plattformansatzes weiter konkretisiert.

# 6. Prototypischer Plattformansatz und Evaluation

Ziel dieses Kapitels ist die exemplarische Validierung der in Kapitel 5 entwickelten Konzeption einer Internen Entwicklerplattform. Die prototypische Ausarbeitung dient nicht der produktiven Implementierung, sondern der Veranschaulichung zentraler Konzepte sowie der reflexiven Bewertung ihrer Eignung zur Verbesserung der Developer Experience.

---

## 6.1 Ziel und Umfang des prototypischen Ansatzes

Der prototypische Plattformansatz verfolgt das Ziel, ausgewählte Kernprinzipien der IDP – insbesondere Self-Service, Standardisierung mit Flexibilität sowie integrierte Governance – in vereinfachter Form darzustellen. Der Prototyp bildet einen repräsentativen Anwendungsfall ab, der typische Entwicklungs- und Deploymentaktivitäten umfasst.

Der Umfang des Prototyps ist bewusst begrenzt. Er fokussiert sich auf einen exemplarischen End-to-End-Prozess, beginnend bei der Bereitstellung eines neuen Services bis hin zum Deployment in eine Kubernetes-basierte Laufzeitumgebung. Aspekte wie Hochverfügbarkeit, Skalierung unter Last oder produktionsreifer Betrieb sind nicht Bestandteil des Prototyps.

---

## 6.2 Beschreibung des prototypischen Plattformansatzes

Der Prototyp orientiert sich an der in Kapitel 5 beschriebenen Architektur und besteht aus einem vereinfachten Developer Interface, einem Satz standardisierter Templates sowie einer integrierten CI/CD-Pipeline.

Über ein zentrales Einstiegselement – beispielsweise ein vereinfachtes Developer Portal oder ein deklaratives Konfigurationsartefakt – können Entwicklerinnen und Entwickler einen neuen Service initiieren. Die Plattform stellt hierfür vordefinierte Templates bereit, die grundlegende Applikationsstruktur, Build- und Deploymentlogik sowie Sicherheitsvorgaben enthalten.

Die CI/CD-Pipeline ist als wiederverwendbarer Plattformservice konzipiert und automatisiert Build-, Test- und Deployment-Schritte. Infrastruktur- und Kubernetes-spezifische Details werden dabei abstrahiert und über deklarative Schnittstellen gesteuert, sodass keine tiefgehenden Kenntnisse der zugrunde liegenden Plattform erforderlich sind.

---

## 6.3 Exemplarischer Anwendungsfall

Als exemplarischer Anwendungsfall dient die Bereitstellung eines neuen, containerisierten Services. Der Prozess beginnt mit der Auswahl eines geeigneten Templates aus dem Servicekatalog der Plattform. Anschließend werden projektspezifische Parameter, wie Service-Name oder Laufzeitkonfiguration, konfiguriert.

Nach Abschluss der Konfiguration wird der vollständige Build- und Deploymentprozess automatisiert angestoßen. Sicherheits- und Compliance-Prüfungen sind integraler Bestandteil der Pipeline und werden ohne zusätzliche manuelle Eingriffe durchgeführt. Der erfolgreiche Abschluss des Deployments resultiert in einer lauffähigen Anwendung innerhalb der vorgesehenen Kubernetes-Umgebung.

---

## 6.4 Evaluation anhand von Developer-Experience-KPIs

Die Evaluation des prototypischen Ansatzes erfolgt qualitativ entlang der in Kapitel 2.4 definierten Developer-Experience-KPIs. Ziel ist es, zu beurteilen, inwieweit der konzipierte Plattformansatz geeignet ist, die identifizierten Herausforderungen des Status quo zu adressieren.

Die Analyse zeigt, dass insbesondere Prozess- und Durchlaufzeit-KPIs wie Time-to-Market und Deployment-Dauer potenziell positiv beeinflusst werden können, da manuelle Schritte reduziert und standardisierte Workflows bereitgestellt werden. Ebenso wird eine Reduktion der kognitiven Belastung erwartet, da komplexe Infrastrukturdetails abstrahiert werden.

Wahrnehmungsbasierte KPIs wie Benutzerfreundlichkeit und Transparenz profitieren insbesondere von einem klar strukturierten Einstiegspunkt sowie von einheitlichen Templates und Dokumentationen. Gleichzeitig wird deutlich, dass der tatsächliche Nutzen stark von der Qualität der Plattformgestaltung und der Akzeptanz durch die Entwicklungsteams abhängt.

---

## 6.5 Reflexion und Limitationen des prototypischen Ansatzes

Die prototypische Validierung ermöglicht eine fundierte Reflexion der entwickelten Konzeption, ersetzt jedoch keine umfassende empirische Evaluation. Der Prototyp bildet lediglich einen vereinfachten Ausschnitt möglicher Plattformfunktionen ab und berücksichtigt keine langfristigen Betriebsaspekte.

Darüber hinaus basiert die Bewertung der Developer Experience primär auf qualitativen Einschätzungen und theoretisch abgeleiteten KPIs. Eine quantitative Messung unter realen Einsatzbedingungen ist nicht Bestandteil dieser Arbeit.

---

## 6.6 Zusammenfassung der Evaluation

Zusammenfassend zeigt die prototypische Ausarbeitung, dass die konzipierte Interne Entwicklerplattform geeignet ist, zentrale Herausforderungen des Status quo zu adressieren. Insbesondere die Verbesserung der Developer Experience durch Self-Service, Standardisierung und Abstraktion infrastruktureller Komplexität wird durch den prototypischen Ansatz plausibel untermauert.

Die gewonnenen Erkenntnisse bilden die Grundlage für die abschließende Diskussion der Ergebnisse sowie für die Ableitung von Handlungsempfehlungen im folgenden Kapitel.
====================================================


Alles klar — ich simuliere jetzt **realistische Experteninterviews** (aus Sicht eures interdisziplinären Teams) und mache anschließend eine **saubere qualitative Inhaltsanalyse nach Mayring** mit den Kategorien **DX, Standardisierung, Sicherheit, Flexibilität** (inkl. Codierung).

---

# Teil 1: Simulierte Interviewantworten (Team-Perspektive)

> **Hinweis zur Perspektive:** Die Antworten spiegeln jeweils typische Aussagen aus den Rollen **DevOps/Infrastruktur**, **IT-Sicherheit**, **Azure/Cloud** und **JFrog Artifactory** wider. Wo sinnvoll, sind Rollendifferenzen kurz markiert.

---

## Block 1: Rolle & Kontext

### 1) Welche Rolle haben Sie und in welchem Bereich arbeiten Sie?

**Antwort:**
Wir arbeiten als interdisziplinäres Team an einer zentralen Unternehmensanwendung. DevOps verantwortet CI/CD, Kubernetes/Runtime und Automatisierung. Security definiert Policies, Reviews und Freigaben. Azure kümmert sich um Cloud-Umgebungen, Netzwerke und Identitäten. JFrog verantwortet Artefaktmanagement, Images, Repos und teilweise Supply-Chain-Themen.

### 2) Wie stark sind Sie in Build/Deploy/Betrieb eingebunden?

**Antwort:**
Sehr stark. Auch Entwickler sind regelmäßig in Deployments, Troubleshooting und Hotfixes involviert. DevOps ist täglich in Pipelines und Plattformbetrieb. Security ist bei Releases, Findings und Ausnahmefällen eng dran. Azure ist stark bei Umgebungsbereitstellung/Netzwerk/Permissions. JFrog ist in jedem Build und Release indirekt beteiligt (Repos, Permissions, Scans).

### 3) Welche Anwendungen/Services betreuen Sie typischerweise?

**Antwort:**
Hauptsächlich die zentrale Unternehmensanwendung plus mehrere interne Services (APIs, Worker, UI) und Integrationen. Es gibt eine Mischung aus Legacy-Anteilen und neueren containerisierten Services.

### 4) Wie läuft der Weg von „Idee“ bis „Betrieb“ grob ab?

**Antwort:**
Idee → Ticket/Backlog → Entwicklung → Merge Request → CI → Image/Artefakt → Deployment in Test → Freigaben/Checks → Deployment Staging/Prod. In der Praxis gibt es viele manuelle Abstimmungen (Freigaben, Secrets, Netzwerk, Konfig), sodass der Flow nicht durchgängig „straight-through“ ist.

---

## Block 2: Status quo (Prozesse, Tools, Umgebungen)

### 5) Wie sind CI/CD und Releases organisiert (zentral vs. team-spezifisch)?

**Antwort:**
Es gibt zentrale Vorgaben (einige Pipeline-Templates, Naming, grobe Policies), aber viele Teams haben eigene Varianten. Releases sind teils standardisiert, teils historisch gewachsen. Ergebnis: unterschiedliche Pipeline-Qualität, unterschiedliche Checks, unterschiedliche „Definition of Done“.

### 6) Welche Tools nutzen Sie für Build, Deploy und Betrieb?

**Antwort:**
CI/CD läuft über mehrere Bausteine (teilweise ein zentrales CI-System, teils Skripte). Artefakte/Images liegen in JFrog. Deployments gehen Richtung Kubernetes, aber nicht immer gleich automatisiert. Betrieb/Monitoring ist vorhanden, aber nicht überall konsistent (Dashboards, Logs, Alerts je Team unterschiedlich).

### 7) Wo laufen eure Workloads (On-Prem, Cloud, Hybrid)?

**Antwort:**
Hybrid: Ein Teil on-prem, ein Teil auf Azure. Manche Umgebungen sind historisch und unterscheiden sich in Networking, Identity und Policy-Ebene.

### 8) Wie aufwendig ist es, neue Umgebung oder neuen Service bereitzustellen?

**Antwort:**
Eher aufwendig. Für einen neuen Service geht es, wenn man erfahren ist. Für neue Umgebungen oder neue Namespaces/Permissions braucht es oft Tickets, Abstimmung und mehrere Iterationen (Security/Azure/DevOps). Onboarding neuer Teammitglieder dauert entsprechend.

### 9) Wo entstehen die größten Reibungsverluste?

**Antwort:**
Typisch sind: manuelle Freigaben, unklare Zuständigkeiten, uneinheitliche Pipeline-Standards, Secrets/Permissions, Netzwerkfreigaben, sowie Troubleshooting bei „funktioniert in Test, nicht in Prod“. Zusätzlich: viel Zeit geht in „Glue Code“ und Pipeline-Fehler statt Produktlogik.

---

## Block 3: Developer Experience & KX

### 10) Wie bewerten Sie die aktuelle Developer Experience?

**Antwort:**
Funktional, aber schwergewichtig. Für routinierte DevOps-nahe Entwickler okay, für „normale“ Entwickler oft zu komplex. Viele Schritte sind nicht self-service-fähig; man braucht Kontextwissen und Kontakte.

### 11) Was kostet am meisten Zeit oder mentale Energie?

**Antwort:**
Pipeline-Fehleranalyse, Environment-Differences, Rechte/Secrets, „Wo ist die richtige Doku?“, und das Debugging von Deployment-/Runtime-Problemen. Oft muss man mehrere Tools und Logs zusammenführen, um die Ursache zu finden.

### 12) Welche Rolle spielt Kubernetes im Alltag?

**Antwort:**
Eine große. Kubernetes ist unsere Laufzeitbasis, aber viele Entwickler müssen Dinge verstehen, die eigentlich Plattformthemen sind (Namespaces, RBAC, Ingress, Ressourcenlimits, Helm/Kustomize). DevOps lebt darin, Entwickler stoßen regelmäßig an die Komplexität.

### 13) Was funktioniert in KX gut – und was nicht?

**Antwort:**
Gut: Skalierung, einheitliches Deployment-Ziel, grundsätzlich automatisierbar.
Nicht gut: zu viele Varianten, wenig „Golden Path“, unterschiedliche Cluster-/Namespace-Regeln, und fehlende Standard-Templates für Deployments/Observability.

### 14) Unterschiede zwischen Dev/Test/Prod?

**Antwort:**
Ja. Unterschiede in Policies, Secrets, Netzwerk und manchmal auch in Tooling-Versionen. Dadurch entstehen „Überraschungen“, die erst spät sichtbar werden. Das frustriert und verlängert die Durchlaufzeit.

---

## Block 4: Standardisierung, Governance & Transparenz

### 15) Wie klar sind Standards/Policies – und wie konsequent werden sie gelebt?

**Antwort:**
Teilweise klar, aber nicht durchgängig. Security-Standards existieren, werden aber nicht überall „by default“ technisch erzwungen. Dadurch entstehen Ausnahmen, Sonderwege und Diskussionen bei jedem Release.

### 16) Wo braucht ihr Freiraum – wo ist Standardisierung zwingend?

**Antwort:**
**Zwingend**: Security/Compliance, Logging/Monitoring-Basics, Image-Handling, Secrets-Management, RBAC, Netzwerkgrundlagen.
**Freiraum**: Framework-/Library-Wahl innerhalb Leitplanken, team-spezifische Deployment-Parameter, Release-Takt, gewisse Pipeline-Erweiterungen.

### 17) Wie gut seht ihr Betriebszustand (Health, Logs, Deploy-Status)?

**Antwort:**
Deploy-Status ist oft sichtbar, aber nicht zentral aggregiert. Logs/Metriken sind da, aber die Zugänge und Dashboards sind nicht überall gleich. DevOps hat mehr Überblick; Entwickler sehen oft nur einen Ausschnitt oder wissen nicht, wo sie suchen sollen.

### 18) Wo fehlt euch Sichtbarkeit oder Kontrolle?

**Antwort:**
End-to-end Transparenz: „Was läuft wo mit welcher Version?“, „Welche Policy hat blockiert?“, „Wer hat welche Freigabe gegeben?“, „Warum ist das Deployment anders als erwartet?“. Außerdem fehlt ein klarer Einstiegspunkt, der Links/Runbooks/Status bündelt.

---

## Block 5: Anforderungen an eine IDP

### 19) Welche 3 Funktionen müsste eine IDP unbedingt haben?

**Antwort:**

1. **Golden Path Templates** (Service + Pipeline + Deployment + Observability-Basics)
2. **Self-Service Provisioning** (Namespaces, Deployments, standardisierte Ressourcen)
3. **Governance/Guardrails by default** (Policy-as-Code, Scans, Freigabe-Workflows)

### 20) Größter Self-Service-Hebel?

**Antwort:**
Self-Service für Deployments und Umgebungen (inkl. Permissions/Secrets in definierten Grenzen). Wenn Entwickler in Minuten statt Tagen deployen können, reduziert das massiv Abstimmung und Wartezeit.

### 21) Welche Leitplanken müssen „by default“ drin sein?

**Antwort:**
Signierte Images/Scan-Pflicht, minimale Security-Baselines (RBAC, Netzwerk, Ressourcenlimits), Secrets-Handling, Auditierbarkeit (wer hat was wann deployed), und klare „allowed paths“ für Ausnahmen.

### 22) Welche Flexibilität sollte trotzdem erlaubt sein?

**Antwort:**
Flexibilität sollte **auf klaren Ebenen** erlaubt sein:

* innerhalb eines genehmigten Tech-Stacks (z. B. Sprache/Framework)
* Erweiterungspunkte in Pipelines (zusätzliche Tests)
* Konfigurationsparameter innerhalb Grenzen (Ressourcen, Feature Flags)
  Nicht flexibel sollte sein: Security-Baselines, Image-Quelle, kritische Policies.

---

## Block 6: Nutzen, Akzeptanz & Risiken

### 23) Welchen Nutzen erwartet ihr?

**Antwort:**
Kürzere Lead Times, weniger manuelle Abstimmung, weniger Fehler durch Standards, schnellere Fehlersuche, besseres Onboarding, und weniger kognitive Last. Außerdem: Compliance wird einfacher nachweisbar.

### 24) Was fördert Adoption – was führt zu Umgehung?

**Antwort:**
Adoption fördern: echte Zeitersparnis, gute Docs, klare Ownership, „happy path“ funktioniert zuverlässig, Feedback-Schleifen.
Umgehung passiert, wenn: Plattform langsam/rigide ist, Sonderfälle nicht abbildet, Fehler schwer zu debuggen sind oder Teams keinen Mehrwert sehen.

### 25) Größte Risiken?

**Antwort:**
„Zu schweres“ Plattformprojekt, fehlende Produktverantwortung, zu viele Ausnahmen, mangelnde UX, und Widerstand wegen Kontrollverlust. Außerdem Risiko von Tool-Wildwuchs, wenn IDP nicht integriert ist oder bestehende Standards nicht technisch durchgesetzt werden.

---

## Optional

### 26) Eine Sache sofort ändern?

**Antwort:**
Einen verbindlichen Golden Path mit Standard-Pipeline + Deployment + Observability-Basics, der für 80% der Services sofort funktioniert.

### 27) Woran merkt ihr in 3–6 Monaten, dass die IDP funktioniert?

**Antwort:**
Mehr Services folgen dem Standard, weniger Tickets für Deployments/Permissions, kürzere Durchlaufzeiten, weniger „Prod-Überraschungen“, und Entwickler können Deployments/Status schneller selbst erklären.

---

# Teil 2: Qualitative Inhaltsanalyse (Mayring) — Kategorien & Codierung

## 2.1 Vorgehen (kurz, „clean“)

* **Material**: Antworten Q1–Q25 (+ optional Q26–Q27)
* **Analyseeinheit**: Sinnabschnitte pro Antwort (1–3 Sätze)
* **Methode**: strukturierende Inhaltsanalyse nach Mayring (deduktive Kategorien + induktive Untercodes)
* **Ziel**: Extraktion zentraler Befunde zu DX, Standardisierung, Sicherheit, Flexibilität

---

## 2.2 Kategoriensystem (Codebook)

### K1 — Developer Experience (DX)

* **DX-PAIN**: kognitive Last, Reibungsverluste, Tool-Suche, Doku-Lücken
* **DX-TRANSP**: Transparenz/Status/Visibility/Observability
* **DX-ONB**: Onboarding/Time-to-First-Deploy
* **DX-SELF**: Self-Service als Entlastung

### K2 — Standardisierung

* **STD-HETER**: Varianten/Fragmentierung, team-spezifische Pipelines
* **STD-GOLDEN**: Golden Path, Templates, Standard-Workflows
* **STD-ENFORCE**: technische Durchsetzung statt „nur Regeln“
* **STD-TRADE**: Trade-off: Standard vs. team-spezifische Bedürfnisse

### K3 — Sicherheit (inkl. Compliance)

* **SEC-BASE**: Baselines (RBAC, Netzwerk, Secrets, Limits)
* **SEC-GATE**: Scans/Signierung/Gates, Auditierbarkeit
* **SEC-EXC**: Ausnahmen/Override-Prozesse
* **SEC-BYDES**: Security-by-default in Plattform/IDP

### K4 — Flexibilität / Anpassungsfähigkeit

* **FLEX-LEVEL**: Ebenen der Flexibilität (Stack, Pipeline-Erweiterung, Config-Parameter)
* **FLEX-ALLOW**: „allowed freedom“ innerhalb Leitplanken
* **FLEX-CONFL**: Konflikt/Spannung mit Standardisierung
* **FLEX-TEAM**: heterogene Teams/Reifegrade

---

## 2.3 Codierung (Auszug: Frage → Codes → Kernaussage)

> Ich gebe dir eine kompakte Codierübersicht; du kannst sie später problemlos in eine Tabelle im Dokument übertragen.

### Block 2/3 (Status quo + DX/KX)

* **Q5/Q6/Q9** → STD-HETER, DX-PAIN
  → *Historisch gewachsene, fragmentierte Toolchain/Pipelines erzeugen Abstimmung & Fehlerarbeit.*
* **Q8** → DX-ONB, DX-SELF, SEC-EXC
  → *Provisioning ist nicht self-service, abhängig von Tickets/Abstimmung (DevOps/Sec/Azure).*
* **Q11/Q12/Q13/Q14** → DX-PAIN, FLEX-TEAM, STD-HETER
  → *Kubernetes-Komplexität + Umgebungsunterschiede treiben kognitive Last und späte Überraschungen.*

### Block 4 (Governance/Transparenz)

* **Q15** → STD-ENFORCE, SEC-BYDES
  → *Policies existieren, sind aber nicht überall technisch erzwungen → Ausnahmen/Sonderwege.*
* **Q17/Q18** → DX-TRANSP, SEC-GATE
  → *Fehlende End-to-end Sichtbarkeit (Version/Policy/Status) erschwert Diagnose & Nachweisbarkeit.*
* **Q16** → STD-TRADE, FLEX-LEVEL
  → *Teams wollen Freiraum in Stack/Parametern, nicht in Security-Baselines.*

### Block 5 (IDP-Anforderungen)

* **Q19/Q20** → STD-GOLDEN, DX-SELF, DX-ONB
  → *Golden Path + Self-Service sind der größte Hebel für Time-to-Deploy und Entlastung.*
* **Q21** → SEC-BASE, SEC-GATE, SEC-BYDES
  → *Security muss „by default“ sein: Scan/Signierung/RBAC/Secrets/Audit.*
* **Q22** → FLEX-LEVEL, FLEX-ALLOW, STD-TRADE
  → *Flexibilität wird als „konfigurierbare Freiheit“ innerhalb Leitplanken definiert.*

### Block 6 (Nutzen/Adoption/Risiken)

* **Q23** → DX-SELF, STD-GOLDEN, SEC-BYDES
  → *Nutzen: Lead Time runter, weniger Fehler, bessere Compliance, weniger kognitive Last.*
* **Q24** → DX-PAIN, STD-ENFORCE, FLEX-CONFL
  → *Adoption hängt an UX/Mehrwert; Umgehung bei Rigidität/Fehlender Debugbarkeit.*
* **Q25** → STD-TRADE, FLEX-CONFL, SEC-EXC
  → *Risiken: Plattform wird zu schwer, zu viele Ausnahmen, fehlende Produkt-Ownership.*

---

## 2.4 Verdichtete Ergebnisse je Kategorie (kurz)

### DX

* Haupttreiber negativer DX: **Tool-/Pipeline-Fragmentierung**, **Kubernetes-Komplexität**, **fehlende Transparenz**, **Ticket-/Abstimmungsaufwand**.
* Hebel: **Self-Service + Golden Path + zentraler Einstiegspunkt** (Docs/Links/Status).

### Standardisierung

* Standardisierung ist vorhanden, aber **nicht konsistent** und **nicht durchgesetzt**.
* „Golden Path“ wird als sinnvoll gesehen, sofern **80% der Fälle** damit schnell lösbar sind.

### Sicherheit

* Security soll nicht „Diskussion pro Release“ sein, sondern **by default** im Prozess.
* Auditierbarkeit (wer/was/wann) wird als wichtig genannt; Ausnahmen müssen geregelt sein.

### Flexibilität

* Flexibilität wird **mehrdimensional** verstanden: Stack-/Parameter-/Pipeline-Erweiterung statt „alles frei“.
* Ziel ist **bewusste Allokation von Freiheitsgraden** (das passt exakt zur Professoren-Logik).

---

# Teil 3: Wie du das direkt in Kapitel 4/5 nutzen kannst (mini-leitend)

* **Kapitel 4 (Analyse)**: nutze Q5–Q18 als Evidenz für **Fragmentierung, kognitive Last, fehlende Transparenz, Governance-Lücken**.
* **Kapitel 5 (Konzeption)**: leite aus Q19–Q25 ab: **Golden Path, Self-Service, Guardrails, Adoption-Design**.
* **Trade-off-Argument (Prof)**: Q16, Q21, Q22 liefern dir die perfekte Basis, Flexibilität als **Ebenenmodell** zu definieren.

---

Wenn du willst, mache ich als nächsten Schritt **eine richtige Codiertabelle in Mayring-Form** (mit *Ankerbeispielen* + *Codierregeln*), die du 1:1 als Anhang in die Masterarbeit kopieren kannst.


Alles klar — ich erstelle dir jetzt ein sauberes Mayring-Codebuch mit Kategorien, Definitionen, Codierregeln und Ankerzitaten aus der Simulation plus eine kompakte Codiertabelle (Frage/Segment → Code → Begründung).


Super — hier ist eine **„saubere“ Mayring-Ausarbeitung** (Codebuch + Codierregeln + Ankerbeispiele + Codiertabelle), die du **1:1 als Anhang** in deine Masterarbeit übernehmen kannst.
(Die „Zitate“ sind **Ankerbeispiele aus dem simulierten Interviewmaterial**; das ist bei Simulationen methodisch ok, solange du es als *simuliert* kennzeichnest.)

---

# Anhang X: Qualitative Inhaltsanalyse nach Mayring (Codebuch & Codierung)

## X.1 Methodisches Vorgehen (nach Mayring, strukturierend)

* **Material:** Simulierte Experteninterviews (Q1–Q25, optional Q26–Q27) auf Basis eines realistischen Unternehmensszenarios
* **Ziel:** Strukturierte Verdichtung der Aussagen zu **DX, Standardisierung, Sicherheit/Compliance, Flexibilität**
* **Analyseeinheit:** Sinnabschnitt (1–3 Sätze pro Antwort)
* **Kontexteinheit:** Gesamte Interviewantwort je Frage
* **Auswertung:** Deduktive Hauptkategorien (aus Forschungslogik), induktive Subcodes (aus Material)
* **Abstraktionsniveau:** praxisnah, organisations- und prozessorientiert

> Hinweis zur Güte: Für eine besonders saubere Durchführung empfiehlt sich ein **zweiter Coder** und die Berechnung einer Intercoder-Übereinstimmung (optional, falls möglich).

---

## X.2 Kategoriensystem (Codebuch)

### K1 Developer Experience (DX)

**Definition:** Wahrgenommene Qualität der Entwicklungs- und Betriebsarbeit (Aufwand, Reibung, Orientierung, Transparenz).

| Subcode   | Definition                                                               | Codierregel                                                                                       | Abgrenzung                                                                       | Ankerbeispiel (simuliert)                                                         |
| --------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| DX-PAIN   | Reibungsverluste, kognitive Last, „Toil“, unnötige Komplexität           | Codieren, wenn Zeit/mentale Belastung durch Prozesse/Tools/Infra genannt wird                     | Nicht codieren, wenn rein technische Sicherheitsanforderung ohne Belastungsbezug | „Pipeline-Fehleranalyse, Rechte/Secrets, Tool-Suche kosten viel mentale Energie.“ |
| DX-TRANSP | Transparenz/Visibility/Observability über Status, Versionen, Deployments | Codieren, wenn fehlende Sichtbarkeit, verteilte Infos, fehlende zentrale Statussicht genannt wird | Nicht codieren, wenn es nur um Logging-Toolauswahl geht                          | „Was läuft wo mit welcher Version? – diese End-to-end Sicht fehlt.“               |
| DX-ONB    | Onboarding, Time-to-First-Deploy, Einstiegshürden                        | Codieren, wenn Bereitstellung/Onboarding als schwierig beschrieben wird                           | Nicht codieren, wenn nur Deployment-Automatisierung ohne Einstieg erwähnt wird   | „Onboarding dauert; für neue Umgebungen braucht man Tickets und Abstimmung.“      |
| DX-SELF   | Self-Service als Entlastung                                              | Codieren, wenn Self-Service explizit als Verbesserung genannt wird                                | Nicht codieren, wenn nur Standardisierung ohne Self-Service Bezug                | „Self-Service für Deployments/Umgebungen wäre der größte Hebel.“                  |

---

### K2 Standardisierung

**Definition:** Grad der Vereinheitlichung von Prozessen, Artefakten und Workflows (Templates, Golden Paths, Standards).

| Subcode     | Definition                                                   | Codierregel                                                                                      | Abgrenzung                                                                    | Ankerbeispiel (simuliert)                                                    |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| STD-HETER   | Fragmentierung/Varianten, historisch gewachsene Unterschiede | Codieren, wenn unterschiedliche Pipelines/Toolchains/Workflows zwischen Teams beschrieben werden | Nicht codieren, wenn es um unterschiedliche Umgebungen ohne Prozessbezug geht | „Viele Teams haben eigene Varianten; Pipeline-Qualität ist unterschiedlich.“ |
| STD-GOLDEN  | Golden Path, Templates, Standard-Workflows                   | Codieren, wenn Templates/Golden Path als Standardpfad genannt werden                             | Nicht codieren, wenn nur „Standards“ abstrakt erwähnt werden                  | „Ein verbindlicher Golden Path, der für 80% funktioniert.“                   |
| STD-ENFORCE | Technische Durchsetzung von Standards (statt nur Regeln)     | Codieren, wenn Standards als „nicht erzwungen“ oder „by default“ gefordert werden                | Nicht codieren, wenn nur Schulung/Kommunikation erwähnt wird                  | „Policies existieren, werden aber nicht überall technisch erzwungen.“        |
| STD-TRADE   | Trade-offs zwischen Standard und Team-Bedarf                 | Codieren, wenn Spannungen/Zielkonflikte explizit genannt werden                                  | Nicht codieren, wenn Standardisierung nur als Vorteil genannt wird            | „Freiraum bei Frameworks ja, aber nicht bei Security-Baselines.“             |

---

### K3 Sicherheit & Compliance

**Definition:** Anforderungen an Schutz, Nachweisbarkeit und Richtlinienkonformität (Baselines, Gates, Audit).

| Subcode   | Definition                                                 | Codierregel                                                                                 | Abgrenzung                                                              | Ankerbeispiel (simuliert)                                                         |
| --------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| SEC-BASE  | Sicherheitsbaselines (RBAC, Netzwerk, Secrets, Limits)     | Codieren, wenn Baseline-Forderungen genannt werden                                          | Nicht codieren, wenn es nur um Komfort/UX geht                          | „RBAC, Netzwerkgrundlagen, Ressourcenlimits müssen Standard sein.“                |
| SEC-GATE  | Prüf-/Freigabemechanismen (Scan, Signierung, Gates, Audit) | Codieren, wenn Scans/Signierung/prüfpflichtige Schritte oder Auditierbarkeit genannt werden | Nicht codieren, wenn es um manuelle Abstimmung ohne Security-Bezug geht | „Signierte Images/Scan-Pflicht und Auditierbarkeit sind wichtig.“                 |
| SEC-EXC   | Ausnahmen/Overrides und deren Behandlung                   | Codieren, wenn Sonderfälle, Ausnahmen, Ausnahmeprozesse erwähnt werden                      | Nicht codieren, wenn nur Standard-Policy erwähnt wird                   | „Zu viele Ausnahmen sind ein Risiko; Ausnahmen müssen geregelt sein.“             |
| SEC-BYDES | Security/Compliance „by default“ integriert                | Codieren, wenn Security als integrierter Bestandteil der Plattform gefordert wird           | Nicht codieren, wenn Security rein organisatorisch beschrieben wird     | „Security soll nicht Diskussion pro Release sein, sondern by default im Prozess.“ |

---

### K4 Flexibilität / Anpassungsfähigkeit

**Definition:** Erlaubte Freiheitsgrade für Teams (Technologie, Prozess, Parameter) innerhalb definierter Leitplanken.

| Subcode    | Definition                                                    | Codierregel                                                                  | Abgrenzung                                                                | Ankerbeispiel (simuliert)                                                               |
| ---------- | ------------------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| FLEX-LEVEL | Ebenen der Flexibilität (Stack, Pipeline-Erweiterung, Config) | Codieren, wenn Flexibilität konkret in Dimensionen/Ebenen beschrieben wird   | Nicht codieren, wenn nur „wir brauchen Flexibilität“ ohne Konkretisierung | „Flexibilität: Stack/Framework im erlaubten Rahmen, Pipeline-Erweiterungen, Parameter.“ |
| FLEX-ALLOW | „Allowed freedom“ innerhalb Leitplanken                       | Codieren, wenn Flexibilität explizit als „innerhalb Grenzen“ formuliert wird | Nicht codieren, wenn es um vollständige Freiheit geht                     | „Konfiguration innerhalb Grenzen, aber nicht bei Baselines.“                            |
| FLEX-CONFL | Konflikt mit Standardisierung                                 | Codieren, wenn Kollision Standard vs. Team-Bedarf benannt wird               | Nicht codieren, wenn beide nur nebeneinander erwähnt werden               | „Zu rigide Plattform führt zu Umgehung; zu viel Freiheit bricht Standards.“             |
| FLEX-TEAM  | Heterogene Teams/Reifegrade als Grund                         | Codieren, wenn unterschiedliche Team-Bedürfnisse/Reife genannt werden        | Nicht codieren, wenn rein technische Varianz ohne Teambezug               | „Für routinierte DevOps-nahe Entwickler okay, für andere zu komplex.“                   |

---

## X.3 Codierregeln (übergreifend)

1. **Mehrfachcodierung ist erlaubt**, wenn ein Sinnabschnitt mehrere Dimensionen adressiert (z. B. DX-PAIN + STD-HETER).
2. **Priorität**: Wenn ein Abschnitt sowohl Standardisierung als auch Sicherheit betrifft, wird **SEC** vergeben, wenn Security/Compliance das Hauptargument ist; andernfalls **STD**.
3. **DX vs. STD**: Wenn über Unterschiede/Varianten gesprochen wird, ist das **STD-HETER**; wenn die Folge als Belastung beschrieben wird, zusätzlich **DX-PAIN**.
4. **Flexibilität nur codieren**, wenn Freiheitsgrade oder deren Begrenzung konkret benannt werden (Ebenen/Leitplanken).

---

## X.4 Codiertabelle (kompakt) – Material → Code(s) → Begründung

> Tabelle als „Belegspur“ (Audit Trail). Du kannst sie bei Bedarf erweitern.

| Frage | Segment (Kurz)                                 | Code(s)                           | Begründung                                  |
| ----: | ---------------------------------------------- | --------------------------------- | ------------------------------------------- |
|     5 | Teams haben eigene Pipeline-Varianten          | STD-HETER                         | Fragmentierung im Prozessdesign             |
|     5 | Pipeline-Qualität/Checks unterschiedlich       | STD-HETER, STD-ENFORCE            | Standards nicht konsistent/erzwungen        |
|     8 | Neue Umgebungen brauchen Tickets/Abstimmung    | DX-ONB, DX-PAIN                   | Onboarding/Provisioning nicht self-service  |
|     9 | Reibung durch Freigaben/Secrets/Netzwerk       | DX-PAIN, SEC-BASE                 | Aufwand + Security-relevante Abhängigkeiten |
|    11 | Pipeline-Fehleranalyse, Tool-Suche belastet    | DX-PAIN                           | kognitive Last/Toil                         |
|    12 | Entwickler brauchen K8s-Detailwissen           | DX-PAIN, FLEX-TEAM                | Komplexität trifft heterogene Teams         |
|    14 | Dev/Test/Prod unterscheiden sich               | STD-HETER, DX-PAIN                | Inkonsistenzen erzeugen Überraschungen      |
|    15 | Policies existieren, nicht technisch erzwungen | STD-ENFORCE, SEC-BYDES            | Governance/Compliance nicht „by default“    |
|    16 | Freiraum bei Frameworks, nicht bei Baselines   | STD-TRADE, FLEX-LEVEL, SEC-BASE   | Trade-off & Ebenenmodell                    |
|    17 | Status sichtbar, aber nicht zentral            | DX-TRANSP                         | fehlende End-to-end Sicht                   |
|    18 | Unklar: Version/Policy/Freigabe                | DX-TRANSP, SEC-GATE               | Nachweisbarkeit/Transparenz                 |
|    19 | Golden Path Templates als Muss                 | STD-GOLDEN, DX-SELF               | Standardpfad + Self-Service                 |
|    20 | Self-Service für Deployments/Umgebungen        | DX-SELF, DX-ONB                   | Hebel für Speed/Onboarding                  |
|    21 | Scan/Signierung/Audit erforderlich             | SEC-GATE, SEC-BYDES               | Security-Checks „by default“                |
|    22 | Flexibilität nur in definierten Grenzen        | FLEX-ALLOW, FLEX-LEVEL, STD-TRADE | Leitplanken + definierte Freiheitsgrade     |
|    23 | Nutzen: kürzere Lead Times, weniger Last       | DX-PAIN, DX-SELF                  | erwartete DX-Verbesserung                   |
|    24 | Umgehung bei Rigidität/Debug-Hürden            | FLEX-CONFL, DX-PAIN               | Zielkonflikt + Negativeffekte               |
|    25 | Risiko: zu schwer, zu viele Ausnahmen          | SEC-EXC, STD-TRADE                | Governance-/Designrisiko                    |

---

## X.5 Ergebnisverdichtung (kurz, für Kapitel 4/5 nutzbar)

* **DX**: Hauptprobleme sind Fragmentierung, K8s-Komplexität, fehlende End-to-end Transparenz und hoher Abstimmungsaufwand.
* **Standardisierung**: Bedarf an Golden Paths hoch; entscheidend ist technische Durchsetzung (nicht nur Dokumente).
* **Sicherheit**: Fokus auf „by default“ Guardrails (Scans, Signierung, Audit, Baselines); Ausnahmen müssen kontrolliert werden.
* **Flexibilität**: wird als **mehrdimensional** verstanden und soll bewusst auf definierte Ebenen begrenzt werden (Leitplanken statt völliger Freiheit).

---

Wenn du willst, kann ich dir als nächsten Schritt auch noch:

* eine **Auswertungstabelle pro Kategorie** (Häufigkeit der Codes + wichtigste Aussagen) erstellen, oder
* einen **Textbaustein für Kapitel 3.4** („Durchführung & Auswertung der Interviews nach Mayring“) formulieren, der genau dieses Codebuch referenziert.
================================
Verstehe ich richtig, dass wir dank deiner Simulation der Antworten auf die Fragen kein IDP und keinen Self-Service benötigen? 


===========================Nein — so wäre das eine **falsche Schlussfolgerung**.

Die Simulation zeigt **nicht**, dass ihr *keine* IDP oder *keinen* Self-Service braucht. Sie zeigt eher das Gegenteil:
**Die größten Pain Points (Abstimmung, Provisioning, Inkonsistenzen, kognitive Last) sind genau die Probleme, die eine IDP mit Self-Service adressieren soll.**

Was die Simulation *wirklich* aussagt:

---

## Was man aus den simulierten Antworten ableiten kann

### 1) **Self-Service ist ein Kernhebel**

In den Antworten taucht immer wieder auf:

* Provisioning dauert wegen Tickets/Abstimmung
* Deployments hängen an Rollen (DevOps/Security/Azure)
* „Wäre der größte Hebel“

➡️ Das spricht **für** Self-Service, aber **innerhalb Leitplanken**.

---

### 2) **Ihr braucht keine „IDP als Monsterprojekt“**

Die Simulation legt nahe:

* Risiko: „zu schweres Plattformprojekt“
* Adoption scheitert bei zu viel Rigidität oder schlechter UX

➡️ Das bedeutet nicht „keine IDP“, sondern:

> **IDP iterativ als Produkt bauen (MVP, Golden Path, 80% Use Cases)**

---

### 3) **Wichtigster Punkt deines Professors wird bestätigt**

Standardisierung und Flexibilität sind ein **Trade-off**.

➡️ Eine IDP ist genau das Werkzeug, um diese Trade-offs **bewusst** umzusetzen:

* Was ist **zwingend standardisiert**? (Security Baselines, Scans, Audit)
* Wo gibt es **konfigurierbare Freiheit**? (Framework innerhalb Rahmen, Parameter, Pipeline-Erweiterungen)

---

## Richtige Interpretation (in einem Satz)

**Ihr braucht sehr wahrscheinlich eine IDP — aber in einer pragmatischen, schrittweisen Ausprägung mit Self-Service für die häufigsten Fälle und klaren Guardrails.**

---

## Was du in der Arbeit sauber schreiben kannst (prüferfest)

> Die Interviews deuten darauf hin, dass ein zentraler Nutzen einer IDP weniger in zusätzlicher Tool-Einführung liegt, sondern in der Reduktion manueller Abstimmung durch standardisierte Golden Paths und kontrollierten Self-Service. Gleichzeitig wird deutlich, dass Umfang und UX entscheidend sind, um Adoption zu erreichen und Umgehungsstrategien zu vermeiden.

---

Wenn du willst, formuliere ich dir daraus direkt:

* **eine Ergebnispassage für Kapitel 4 (Analyse)** und
* **eine Design-Entscheidung für Kapitel 5 (Konzeption)**
  inkl. 2–3 konkreter MVP-User-Stories (z. B. „Create service“, „Deploy to test“, „Request namespace/permissions“).
===============================================


Die Simulation der Antworten sollte dazu führen, dass wir das Problem finden, das uns daran hindert, die IDP-Plattform zu entwickeln. Wie viele Personen hast du in deiner Simulation befragt? ES MUSS MINDESTEN 6 PERSONNEN SEIN



Verstanden — ich erstelle jetzt eine neue Simulation mit **mindestens 6 Interview-Personas** (DevOps, Security, Azure, JFrog, Softwareentwicklung, IT-Architektur/Produkt) und leite daraus die zentralen „Blocker“ für die IDP-Entwicklung ab (organisatorisch, technisch, governance, Adoption).


Du hast völlig recht: Wenn die Simulation methodisch nützlich sein soll, muss sie (a) **mehrere Perspektiven** abdecken und (b) am Ende **klar benennen, was die IDP-Entwicklung blockiert**.

### Wie viele Personen waren es bisher?

In der letzten Simulation habe ich **keine klar getrennten Einzelpersonen** ausgewiesen, sondern eine **zusammengefasste Team-Perspektive** (DevOps/Security/Azure/JFrog implizit). Das ist **nicht ausreichend**, wenn du explizit „mindestens 6 Personen“ brauchst.

Unten bekommst du deshalb eine **neue, saubere Simulation mit 6 Interview-Personas** + eine **Blocker-Analyse**, die direkt auf deine IDP-Entwicklung zielt.

---

# Teil 1 — Simulierte Experteninterviews (mind. 6 Personen)

## Die 6 Interview-Personas

1. **P1 – DevOps / Plattformbetrieb** (CI/CD, Kubernetes, Automatisierung)
2. **P2 – IT-Sicherheit** (Policies, Risk, Compliance, Freigaben)
3. **P3 – Azure / Cloud Engineering** (Landing Zone, Netzwerk, Identity, Umgebungen)
4. **P4 – JFrog Artifactory / Supply Chain** (Repos, Images, Scans, Promotion)
5. **P5 – Softwareentwicklung (Feature-Team)** (Build/Deploy-Nutzer, DX)
6. **P6 – IT-Architektur / Applikationsverantwortung** (Zielarchitektur, Standards, Entscheidungsgremien)

> Ich gebe pro Frage kurze, realistische Antworten (1–3 Sätze), damit du sie später gut codieren kannst.

---

## Block 1: Rolle & Kontext (Q1–Q4)

### Q1 Rolle & Bereich

* **P1 DevOps:** Betreibe CI/CD, Kubernetes-Cluster, Deployment-Standards und Troubleshooting.
* **P2 Security:** Verantworte Security-Policies, Freigabeprozesse, Findings und Audit-Anforderungen.
* **P3 Azure:** Zuständig für Subscriptions, Netzwerk, Identity/RBAC, Landing Zones, Plattform-Services.
* **P4 JFrog:** Betreue Artifactory, Repos, Permissions, Image-Promotion und Artefakt-Richtlinien.
* **P5 Dev:** Entwickle Features, mache MRs, debugge Pipeline/Deployments bei Bedarf.
* **P6 Arch:** Definiere Zielarchitektur, Standards und unterstütze bei Technology Governance.

### Q2 Einbindung Build/Deploy/Betrieb

* **P1:** Täglich in Deployments, Pipeline-Fixes, Plattformänderungen.
* **P2:** Bei Releases/Incidents involviert, oft als Gatekeeper, wenn Findings auftreten.
* **P3:** Häufig, wenn neue Umgebungen/Netzwerk/Identity nötig ist.
* **P4:** Indirekt bei jedem Build/Release, direkt bei Repo-Struktur, Quotas, Scans, Promotion.
* **P5:** Täglich CI, regelmäßig Deployments; bei Störungen viel Kontextwechsel.
* **P6:** Bei größeren Änderungen/Standards, Eskalationen und Roadmap-Entscheidungen.

### Q3 Arten von Services

* **P1:** Mix aus Legacy + Microservices, Container-Workloads, einige Batch/Worker.
* **P5:** Services mit unterschiedlichen Tech-Stacks; nicht jeder passt in denselben Workflow.
* **P6:** Kritisch: mehrere Domänen, daher unterschiedliche Compliance-Profile.

### Q4 Lifecycle grob

* **P5:** Idee → Ticket → Implementierung → MR → CI → Test → Freigaben → Prod; aber Übergänge sind nicht standardisiert.
* **P1:** Der Flow bricht oft bei „Umgebung/Secrets/Policy“, weil das außerhalb des Teams liegt.
* **P2:** Sicherheitsprüfung kommt oft spät, dann wird es hektisch.

---

## Block 2: Status quo (Q5–Q9)

### Q5 CI/CD Organisation

* **P1:** Es gibt zentrale Pipeline-Bausteine, aber Teams forken sie; dadurch driftet alles auseinander.
* **P5:** Jede Repo sieht ein bisschen anders aus, man muss jedes Mal neu lernen.
* **P6:** Standardisierung existiert als Ziel, aber ohne konsequente Durchsetzung.

### Q6 Tools für Build/Deploy/Betrieb

* **P4:** Artefakte/Images laufen über Artifactory; Promotion-Regeln sind nicht überall gleich umgesetzt.
* **P1:** CI ist teilweise einheitlich, aber Deployments variieren (manuell, Skripte, unterschiedliche Manifeste).
* **P3:** Azure-Ressourcen werden teils IaC-basiert, teils ticketbasiert bereitgestellt.

### Q7 Infrastrukturmodell

* **P3:** Hybrid; Azure hat klare Strukturen, On-Prem ist historisch, Policies unterscheiden sich.
* **P1:** Unterschiedliche Cluster/Namespaces sind uneinheitlich gemanagt → Reibung.

### Q8 Aufwand neue Umgebung/Service

* **P3:** Subscriptions/RBAC/Netzwerk sind nicht self-service; das braucht oft Requests.
* **P2:** Für neue Services fehlen standardisierte Security-Baselines → viele Rückfragen.
* **P5:** Ich brauche oft 2–3 Personen, bis ich „deploybar“ bin.

### Q9 Größte Reibungsverluste

* **P5:** „Wer ist zuständig?“ + fehlende Doku + Umgebungsunterschiede.
* **P1:** Manuelle Abstimmung ist der Bottleneck, nicht das Coding.
* **P2:** Späte Security-Checks erzeugen Nacharbeit und Blockaden.
* **P4:** Unklare Promotion/Tagging/Repo-Standards führen zu Chaos bei Releases.

---

## Block 3: DX & KX (Q10–Q14)

### Q10 DX insgesamt

* **P5:** DX ist inkonsistent: manchmal schnell, manchmal frustrierend, je nach Service.
* **P1:** Für DevOps-affine Leute ok, für andere zu komplex.
* **P2:** Aus Security-Sicht fehlt „by default“-Sicherheit, was DX indirekt verschlechtert (mehr Gates, mehr Diskussion).

### Q11 Zeit/mentale Energie

* **P5:** Pipeline-Fehler, Secrets/Permissions, „wo sind Logs/Deploy-Infos?“.
* **P1:** Debugging über mehrere Tools, weil es keinen zentralen Einstiegspunkt gibt.
* **P3:** Viele „kleine“ Requests (RBAC/Netzwerk) fressen Zeit.

### Q12 Kubernetes Rolle

* **P5:** Ich muss K8s mehr verstehen, als ich will.
* **P1:** K8s ist unser Standard-Target, aber die Nutzersicht ist nicht abstrahiert.
* **P2:** Policies/RBAC in K8s sind wichtig, aber schwer konsistent umzusetzen.

### Q13 KX gut/schlecht

* **P1:** Gut: Skalierbarkeit, Plattformfähigkeit. Schlecht: fehlende Templates/Golden Paths, zu viele Varianten.
* **P5:** Gut: Wenn’s läuft. Schlecht: wenn’s nicht läuft, weiß ich nicht wo anfangen.

### Q14 Unterschiede Dev/Test/Prod

* **P3:** Unterschiede in Identity/Netzwerk sind real; das muss stärker vereinheitlicht werden.
* **P5:** „Works in Test, fails in Prod“ ist ein echter Frust-Faktor.

---

## Block 4: Standardisierung/Governance/Transparenz (Q15–Q18)

### Q15 Standards/Policies klar & konsequent?

* **P2:** Standards existieren, aber Ausnahmen sind häufig und nicht sauber geregelt.
* **P1:** Es fehlt technische Enforcement-Power: Policies stehen im Wiki, nicht in der Pipeline/Plattform.
* **P6:** Governance ist da, aber nicht in ein klares Operating Model übersetzt.

### Q16 Wo Freiraum vs Standardisierung zwingend?

* **P2:** Zwingend: Scans, Signierung, RBAC, Secrets, Netz. Freiraum: Frameworks innerhalb genehmigtem Stack.
* **P5:** Ich brauche Freiraum bei Libraries/Build-Tools, aber nicht bei Deploy-Regeln.

### Q17 Sicht auf Betriebszustand

* **P1:** DevOps hat Sicht, Devs oft nicht; Zugänge sind fragmentiert.
* **P5:** Ich brauche einen „Single Pane of Glass“ für Deployments/Logs/Versionen.
* **P4:** Artefakt-Traceability (welches Image wo?) ist nicht immer eindeutig.

### Q18 Wo fehlt Kontrolle/Sichtbarkeit?

* **P6:** End-to-end Ownership ist unklar: Wer ist Plattform-Owner? Wer entscheidet Standards?
* **P2:** Audit-Trail und Policy-Transparenz fehlen (warum blockiert etwas?).
* **P5:** Ich verliere Zeit, weil Infos verteilt sind.

---

## Block 5: Anforderungen an IDP (Q19–Q22)

### Q19 Top-3 IDP-Funktionen

* **P5:** „Create service“ + standard Pipeline + Standard-Deployments.
* **P1:** Golden Path Templates + Self-Service Deploy + Standard Observability.
* **P2:** Guardrails by default + klare Ausnahmeprozesse.
* **P3:** Self-Service für Standard-Umgebungen/Namespaces/RBAC innerhalb Grenzen.
* **P4:** Standardisierte Artefakt-Promotion/Tagging + Traceability.

### Q20 Größter Self-Service Hebel

* **P3:** Bereitstellung von Standard-Umgebungen ohne Tickets (mit Policy-Grenzen).
* **P1:** Deployment- und Rollback-Self-Service.
* **P5:** Ein Weg, deployen zu können, ohne 3 Teams anschreiben zu müssen.

### Q21 Leitplanken „by default“

* **P2:** Scans, Signierung, minimale Policies, Auditability, Secrets-Standards.
* **P4:** Immutable Tags/Digests, Promotion-Stages, Zugriffskontrollen.
* **P1:** Policy-as-Code + Pipeline Gates, damit Regeln nicht verhandelbar sind.

### Q22 Welche Flexibilität bleibt?

* **P6:** Flexibilität als „konfigurierte Wahlmöglichkeiten“ (Plugins, Parameter), nicht als freie Wildbahn.
* **P5:** Tech-Stack-Freiraum innerhalb Whitelist; Pipeline erweiterbar, nicht ersetzbar.

---

## Block 6: Nutzen/Adoption/Risiken (Q23–Q25)

### Q23 Erwarteter Nutzen

* **P5:** Weniger Kontextwechsel, schnellere Deployments, klarere Wege.
* **P1:** Weniger Betriebslast durch Standards, weniger Tickets.
* **P2:** Weniger Diskussionen, bessere Compliance-Nachweise.
* **P6:** Schnellere Entscheidungen, weniger Fragmentierung.

### Q24 Adoption fördern vs umgehen

* **P5:** Adoption, wenn der Standardweg wirklich schneller ist; Umgehung, wenn er bremst.
* **P1:** Produktdenken + Feedback-Schleifen sind Pflicht.
* **P2:** Security muss „enable“, nicht nur blocken; sonst entsteht Schatten-IT.
* **P3:** Wenn Self-Service fehlt, bleibt alles ticketgetrieben → keine Akzeptanz.

### Q25 Größte Risiken

* **P6:** Unklare Ownership/Operating Model → Plattform wird Projekt ohne Produktverantwortung.
* **P1:** Zu großer Scope, zu viele Sonderfälle, keine Priorisierung (kein MVP).
* **P2:** Zu viele Ausnahmen oder zu harte Regeln ohne UX → Umgehung.
* **P4:** Supply-Chain-Anforderungen werden zu spät integriert → spätere Rework-Kosten.

---

# Teil 2 — Ergebnis: Was blockiert die IDP-Entwicklung? (die „Problemfindung“)

Aus den 6 Perspektiven ergeben sich **5 Haupt-Blocker**. Das sind genau die Ursachen, die euch „daran hindern“, eine IDP erfolgreich zu entwickeln (nicht nur technisch, sondern organisatorisch und methodisch).

## Blocker B1: **Unklare Produkt-Ownership & Operating Model**

* Wer ist **Product Owner** der IDP?
* Wer entscheidet Standards, Prioritäten, Roadmap?
  **Evidenz:** P6 (Ownership unklar), P1 (kein klares Operating Model)

➡️ Ohne Ownership wird die IDP ein „Nebenbei-Projekt“ und scheitert an Priorität/Adoption.

---

## Blocker B2: **Fragmentierung (Pipeline-/Tool-/Umgebungs-Drift)**

* Teams forken Standards, alles driftet auseinander.
  **Evidenz:** P1/P5/P6 (Varianten, inkonsistent)

➡️ Ohne konsequente Standardisierung *und* technische Durchsetzung gibt es keinen stabilen Golden Path.

---

## Blocker B3: **Ticket-getriebenes Provisioning (kein Self-Service)**

* Azure/RBAC/Netzwerk/Secrets brauchen Abstimmung → lange Wartezeiten.
  **Evidenz:** P3/P2/P5

➡️ Solange das nicht „within guardrails“ self-service-fähig wird, bleibt IDP-Wert begrenzt.

---

## Blocker B4: **Security als spätes Gate statt „by default“**

* Security kommt spät, erzeugt Rework und Blockaden.
  **Evidenz:** P2/P1/P4

➡️ Wenn Guardrails nicht in Templates/Pipelines/Policies eingebaut sind, bremst Security (und Teams umgehen).

---

## Blocker B5: **Fehlende End-to-End-Transparenz**

* Kein „Single Pane“ für Version/Deploy/Policy/Artefakttrace.
  **Evidenz:** P5/P1/P4/P2

➡️ Ohne Transparenz leidet DX und Debugging/Compliance wird teuer.

---

# Teil 3 — Was du daraus in der Arbeit ableiten kannst (präzise)

## 3.1 Problemstatement (professorentauglich)

> Die zentrale Hürde für die Entwicklung einer IDP liegt weniger in der Toolauswahl, sondern in einem fehlenden Operating Model (Ownership), inkonsistenter Standardisierung (Drift), ticketgetriebenem Provisioning, nicht integrierter Security-by-default sowie mangelnder End-to-End-Transparenz.

## 3.2 Konsequenz für dein Prototyp/MVP

Ein realistischer MVP muss **genau einen Blocker adressieren**, sonst wird er zu groß.
Die naheliegendste MVP-Kombi (hoher Hebel, geringe Komplexität):

* **Golden Path Template + standard CI gates + standard Deployment in Test**
* plus minimaler Self-Service: **Namespace/Secrets/Permissions innerhalb Guardrails**

---

# Teil 4 — Mini-Mayring-Codierung (kurz, auf Blocker-Ziel)

Damit du es sauber in Kapitel 4/5 verankern kannst, hier das Mapping von Blockern zu Kategorien:

* **B1 Ownership/Operating Model** → Standardisierung (STD-ENFORCE/STD-TRADE), Flexibilität (FLEX-CONFL)
* **B2 Fragmentierung/Drift** → Standardisierung (STD-HETER), DX (DX-PAIN)
* **B3 Ticket-Provisioning** → DX (DX-ONB, DX-SELF), Flexibilität (FLEX-LEVEL)
* **B4 Security spät** → Sicherheit (SEC-BYDES, SEC-GATE, SEC-EXC), DX (DX-PAIN)
* **B5 Transparenz fehlt** → DX (DX-TRANSP), Sicherheit (SEC-GATE), Standardisierung (STD-ENFORCE)

---


### 1. Analyse des Status quo

#### 1.1 Methodischer Zugriff und Datenbasis

Die Status-quo-Analyse basiert auf **20 Interviewteilnahmen** aus dem Unternehmen: **17 englischsprachige** Rückläufe im Interviewframework „Platform engineering and developer experience“ sowie **3 deutschsprachige** Rückläufe im „Fachinterview-Framework“.  Beide Instrumente adressieren denselben Themenkomplex (Entwicklungsalltag, CI/CD, Tooling, Workloads, Templates, Self-Service, Observability) und wurden als **gemeinsamer Korpus** ausgewertet; englischsprachige Inhalte werden dabei sinngemäß in deutscher Sprache in die Analyse integriert. Die Auswertung folgt einer **qualitativen Inhaltsanalyse mit thematischer Verdichtung**: Aussagen wurden entlang wiederkehrender Beobachtungsfelder gebündelt (Praxis → Probleme → Ursachen → Folgen) und durch die im Material enthaltenen **deskriptiven Häufigkeiten/Anteile** ergänzt (z. B. Anzahl Nennungen pro Antwortfeld). 

#### 1.2 Aktuelle Entwicklungspraxis und Arbeitsrealität

Die Stichprobe ist stark entwicklungsnah geprägt: Im englischsprachigen Korpus ordnen sich **15 von 17** Befragten der **Softwareentwicklung** zu; zusätzlich werden Tätigkeitsfelder wie **CI/CD (6/17)**, **DevOps (4/17)** und **Platform Engineering (2/17)** genannt (Mehrfachnennungen).  Im deutschsprachigen Korpus dominieren **DevOps-Rollen (3/3)**, ergänzt um CI/CD-Anteile.  Inhaltlich zeigt sich eine Arbeitsrealität, in der ein relevanter Teil der Befragten zumindest teilweise mit Build/Deploy/Operations-Themen befasst ist, jedoch nicht zwingend als „Kernaufgabe“ (z. B. „not part of daily work, but…“, „~20% daily work“). 

Die Organisation der Delivery-Prozesse erscheint **heterogen**: CI/CD und Releases werden häufig als **team-spezifisch** beschrieben (im englischsprachigen Korpus sind **7 von 15 (47%)** explizit „team specific“ in diesem Antwortfeld).  Im deutschsprachigen Korpus wird CI/CD ebenfalls als „sehr team-spezifisch“ beschrieben, teils mit Rollen wie Release Manager.  Parallel existieren Hinweise auf **zentrale Elemente** (z. B. „release bundle“, „centrally organized“, „integration“), was auf ein **hybrides Organisationsmodell** schließen lässt: Teams verantworten Teile der Pipeline-Logik, während bestimmte Integrations-/Release-Schritte zentral gebündelt werden. 

Auch die Anwendungslandschaft ist nicht monolithisch einheitlich: Im englischsprachigen Korpus werden **hybride Architekturformen (9 Nennungen)** häufiger genannt als reine Monolithen (**4**) oder „Other“ (**3**); Microservices werden in dieser Frage nicht genannt.  Der deutschsprachige Korpus weist ebenfalls eine „Mischform“ aus. 

#### 1.3 Zentrale Probleme im Ist-Zustand

Über beide Korpora hinweg werden vor allem drei Problemachsen sichtbar:

**(1) Prozess- und Koordinationslast:** Im deutschsprachigen Korpus werden „langwierige Prozesse“ und „viel Bürokratie“ explizit als kognitiv belastend beschrieben; zudem werden „ungenau spezifizierte Tickets“ als Zeittreiber genannt.  Diese Beobachtungen deuten auf Reibung durch Abstimmung, unklare Eingaben und Nacharbeit hin. Im englischsprachigen Korpus erscheint ein analoger Befund indirekt über Hinweise auf fehlende „inputs“, wiederkehrende „common issues“ und den Bedarf nach best practices/guidelines in Toolnutzung und Pipelines. 

**(2) Komplexität und Fehleranfälligkeit in CI/CD-Konfigurationen:** Mehrere englische Antworten verweisen auf Schwierigkeiten beim Verständnis und Debugging von **Azure DevOps YAML-Pipelines** („tricky“, „understanding details…“, „error analysis“), und „pipeline“ ist in Wortwolken/Nennungen stark präsent.  Auch die Abhängigkeiten zwischen Pipelines werden als Herausforderung genannt („managing dependencies between pipelines…“). 

**(3) Governance-/Betriebsaufgaben als Belastung (insb. Berechtigungen):** In den deutschsprachigen Antworten werden Permission-Themen explizit als Self-Service-Wunsch und als Automatisierungsziel benannt („Permission Management (Setzen von Berechtigungen)“; „gute Pflege- und Wartbarkeit Permission Management“).  Im englischen Korpus tauchen „Permission settings“ und „rights management“ ebenfalls als wiederkehrende Punkte auf, wenn auch nicht bei allen Fragen dominierend. 

#### 1.4 Dev- und Deployment-bezogene Reibungspunkte

Als operative Reibungspunkte treten insbesondere **Toolkonfiguration, Pipeline-Fehleranalyse und Artefakt-/Compliance-Themen** hervor. In den Toolnennungen werden regelmäßig **Azure DevOps/Azure Pipelines**, **Artifactory**, **Black Duck** sowie Build-Werkzeuge (cmake/gcc/msbuild etc.) genannt.  In den Aussagen zu „time-consuming/cognitively demanding“ werden u. a. Probleme mit „key files“ aus Artifactory (inkl. Bezug zu Berechtigungen), Pipeline-Debugging sowie Code-Scan/Compliance-Kontexte sichtbar. 

Zusätzlich zeigt sich eine **hybride Infrastrukturrealität** bei den Workloads: Im englischsprachigen Korpus wird „cloud“ stark genannt (**10/15 = 67%** im entsprechenden Antwortfeld), zugleich erscheinen Hinweise auf „on-prem“ bzw. hybride Konstellationen; im deutschsprachigen Korpus werden Workloads explizit als „On-Prem, Cloud“ bzw. „Hybrid“ beschrieben.  Diese Hybridität verstärkt typischerweise Integrations- und Betriebsanforderungen (z. B. unterschiedliche Laufzeitumgebungen, Agenten, Netzwerkpfade), was sich in den Antworten zumindest indirekt durch Themen wie Agents/Scale Sets und unterschiedliche CI-Systeme (z. B. TeamCity on-prem + Azure Pipelines) widerspiegelt. 

#### 1.5 Herausforderungen in Tooling, Infrastruktur und Zusammenarbeit

**Tooling/Integrationen:** Die Toollandschaft ist funktional breit (ADO/Pipelines, Artifactory/JFrog Platform, Black Duck, TeamCity, Azure Portal, IaC/Ansible).  Gleichzeitig deuten mehrere Antworten auf fehlende oder inkonsistente Leitlinien hin („tools without guideline“, „pipelines guidelines“), was auf **Variabilität** in der Umsetzung und damit auf einen erhöhten Abstimmungs- und Supportbedarf schließen lässt. 

**Templates/Self-Service:** Wiederverwendbarkeit ist vorhanden, aber nicht flächendeckend: Im englischen Korpus geben **5 von 16 (31%)** „templates“ als wiederkehrendes Stichwort im Template-Kontext an; gleichzeitig wird in deutschsprachigen Antworten „sehr wenig bis gar nichts“ erwähnt, neben punktuellen IaC-/Terraform-/Ansible-Skripten.  Zudem ist bemerkenswert, dass bei der Frage nach der Rolle von Kubernetes im Alltag **6 von 15 (40%)** „none/no role“ angeben, was nahelegt, dass Kubernetes (als Plattformabstraktion) in Teilen der Entwicklerrealität nicht zentral ist oder nicht direkt konsumiert wird. 

**Observability/Transparenz:** Die Einschätzung der Monitoring-Möglichkeiten ist gemischt. Im englischen Korpus wird Monitoring teilweise nur als „basic Azure features“ beschrieben; gleichzeitig wird auf „junk data“ und Verbesserungspotenziale verwiesen.  Im deutschsprachigen Korpus wird der Betriebszustand als „verbesserungswürdig“ bzw. mit „Verbesserungspotenzial“ eingeschätzt, neben einzelnen positiven Einschätzungen.  Insgesamt deutet das Material auf **uneinheitliche Transparenz** und unterschiedlich reife Monitoring-Praktiken hin.

**Zusammenarbeit/Verantwortlichkeiten:** Der Befund „team-spezifische CI/CD“ (englisch) und „sehr team-spezifisch“ (deutsch) spricht für eine stark dezentralisierte Verantwortungsstruktur in der Delivery-Praxis, ergänzt durch zentrale Elemente (z. B. Release Manager/Integration).  Typische Folgen einer solchen Mischform (die in den Aussagen sichtbar werden) sind divergierende Pipeline-Logiken, variable Standards und erhöhte kognitive Last beim Wechsel zwischen Projekten/Teams.

#### 1.6 Verdichtung der zentralen Beobachtungen

Zusammenfassend zeigt der Status quo eine Organisation mit **hybrider Infrastrukturrealität (Cloud + On-Prem)**, **heterogener Toolchain** und einem **überwiegend team-spezifischen CI/CD-Zuschnitt**.  Die dominanten Reibungen entstehen weniger aus fehlenden Tools, sondern aus **inkonsistenter Standardisierung und Prozesslast** (u. a. Bürokratie, unklare Tickets), aus **Komplexität in Pipeline-Konfiguration und Fehleranalyse** (insbesondere YAML-basierte ADO-Pipelines) sowie aus **governance-nahen Routineaufgaben** wie Berechtigungsmanagement.  Wiederverwendbare Templates und Automationen existieren punktuell, sind aber nicht einheitlich etabliert, was die Varianz in der täglichen Praxis verstärkt.  Observability wird teils als ausreichend, teils als verbesserungswürdig beschrieben; in der Gesamtschau deutet dies auf eine inkonsistente Transparenz- und Datenqualität hin. 

---

### Kompakte analytische Verdichtung (Befunde des Ist-Zustands)

Der aktuelle Entwicklungs- und Bereitstellungsalltag ist durch **dezentral organisierte Delivery-Verantwortung**, **Tool- und Prozessheterogenität** sowie **hohe kognitive Last bei CI/CD-Konfiguration und Troubleshooting** geprägt.  Besonders sichtbar sind Reibungen durch **fehlende bzw. uneinheitliche Leitlinien/Standards** (Toolnutzung, Pipelines), durch **Koordinations- und Ticketlast** (inkl. unklarer Spezifikationen) sowie durch **governance-bezogene Routineaufgaben** (insb. Berechtigungen).  Der Status quo weist zugleich auf vorhandene, aber fragmentierte Wiederverwendbarkeit (Templates/Skripte/IaC) hin, während Kubernetes als Plattformkonzept in Teilen der täglichen Entwicklerpraxis keine direkte Rolle spielt. 

---

### Optionale Übersichtstabelle (Status-quo-Felder)

| Beobachtungsfeld     | Beschreibung des Status quo                                                   | Häufigkeit/Verbreitung (aus dem Material)                                           | Relevanz    |
| -------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------- |
| Rollen/Betroffenheit | Stark entwicklungsnah; CI/CD/DevOps relevant                                  | Softwareentwicklung 15/17 (engl.); DevOps 3/3 (dt.)                                 | Hoch        |
| CI/CD-Organisation   | Mischform; häufig team-spezifisch                                             | team specific 7/15 (47%) (engl. Fragefeld)                                          | Hoch        |
| Workloads            | Hybrid (Cloud + On-Prem)                                                      | „cloud“ 10/15 (67%); dt.: Hybrid/On-Prem+Cloud                                      | Hoch        |
| Wiederverwendbarkeit | Templates/Skripte punktuell, nicht flächig                                    | templates 5/16 (31%); dt.: „sehr wenig bis gar nichts“                              | Mittel–hoch |
| Pain Points          | Pipeline-Komplexität, Tool-/Guideline-Lücken, Tickets/Bürokratie, Permissions | wiederkehrend in Wortwolken/Antworten (pipeline, guidelines, tickets, permissions)  | Hoch        |
| Observability        | Uneinheitlich; teils nur basic, teils Verbesserungsbedarf                     | dt.: „verbesserungswürdig“; engl.: „basic Azure features“, „junk data“              | Mittel      |

Wenn Sie möchten, kann ich den Abschnitt noch stärker „masterarbeitstypisch“ glätten (z. B. mit einheitlichen Übergängen, weniger Tool-Nennung im Fließtext) – ohne in Richtung Requirements oder Lösungsteil abzurutschen.



=============================================================
# 19.03.2026

===========================================================


## 1. Analyse des Status quo

### 1.1 Methodischer Zugriff und Datenbasis

Die vorliegende Status-quo-Analyse basiert auf einem Interviewkorpus mit **20 Teilnehmenden** aus dem entwicklungs- und betriebsnahen Umfeld des Unternehmens.  Das Material liegt **zweisprachig** vor, wird jedoch als **einheitlicher, zusammenhängender Datenkorpus** behandelt; nicht-deutschsprachige Aussagen werden in der Auswertung sinngemäß in deutscher Sprache integriert, ohne sie als separate Teilmenge zu behandeln.  Die Analyse folgt einer **qualitativen Inhaltsanalyse mit thematischer Verdichtung**. Dazu wurden Aussagen entlang wiederkehrender Beobachtungsfelder gebündelt und systematisch in eine Kette aus **beobachtbarer Praxis**, **wahrgenommenen Problemen**, **organisationalen bzw. technischen Ursachen** sowie **Folgen für den Entwicklungsalltag** überführt.  Wo das Interviewmaterial strukturierte Auszählungen enthält (z. B. Anzahl von Nennungen pro Antwortfeld), werden diese deskriptiv genutzt, um die Verbreitung einzelner Befunde transparent einzuordnen, ohne daraus repräsentative Schlüsse abzuleiten. 

### 1.2 Aktuelle Entwicklungspraxis und Arbeitsrealität

Die Aussagen zeigen eine Arbeitsrealität, in der Softwareentwicklung im Zentrum steht, jedoch regelmäßig mit Aufgaben an der Schnittstelle zu Build-, Deploy- und Betriebsprozessen verbunden ist.  Der Grad der direkten Einbindung in Build/Deploy/Operations wird von den Befragten heterogen beschrieben: Einige berichten von punktueller Betroffenheit („nicht täglich, aber regelmäßig relevant“), andere von substanziellen Anteilen im Arbeitsalltag. 

Die Organisation von CI/CD und Releases wird häufig als **teamnah** und in Teilen **teamspezifisch** beschrieben; zugleich finden sich Hinweise auf übergreifende bzw. zentral koordinierte Elemente (z. B. Integration in Releases, Bündelung/Koordination).  Diese Mischform deutet auf eine Struktur hin, in der lokale Teamautonomie in der Umsetzung von Delivery-Logik mit zentralen Integrations- und Governanceanforderungen koexistiert, ohne dass daraus zwingend ein durchgängig einheitlicher Standardprozess entsteht. 

Die technische Landschaft erscheint ebenfalls nicht homogen. In den Angaben zur Anwendungsarchitektur werden Mischformen häufiger genannt als reine Monolithen; Microservices werden in diesem Antwortfeld nicht als dominierende Architekturform sichtbar.  Parallel verweisen die Angaben zu Workload-Standorten auf eine **hybride Infrastrukturrealität** (Cloud und On-Premise bzw. Mischformen), die im Alltag als Normalzustand vorkommt und damit zusätzliche Anforderungen an Toolzugriffe, Agenten/Runner, Konnektivität und Berechtigungsmodelle nahelegt. 

### 1.3 Zentrale Probleme im Ist-Zustand

Im Interviewkorpus verdichten sich drei Problemachsen, die wiederholt und mit erkennbarer Relevanz für den Arbeitsalltag auftreten.

Erstens zeigt sich eine **erhebliche Prozess- und Koordinationslast**. Der Korpus enthält explizite Hinweise auf langwierige Abläufe, Bürokratie sowie auf unklar spezifizierte Arbeitsaufträge, die zusätzliche Rückfragen und Nacharbeit nach sich ziehen.  Diese Reibung wirkt nicht nur als „organisationales“ Problem, sondern unmittelbar als Produktivitätsverlust: Kontextwechsel, Wartezeiten und erhöhte Fehleranfälligkeit begleiten den Übergang von Anforderung zu Umsetzung.

Zweitens wird **CI/CD-Konfiguration** als kognitiv anspruchsvoll und fehleranfällig sichtbar, insbesondere in Bezug auf YAML-basierte Pipeline-Definitionen und deren Fehleranalyse.  Zusätzlich wird die Abhängigkeitssteuerung zwischen Pipelines als Herausforderung benannt, was auf eine wachsende Komplexität in der Delivery-Topologie hinweist (mehrere Pipelines, Kopplungen, Integrationspfade). 

Drittens treten **governance-nahe Routinetätigkeiten** als Belastung hervor. Dazu zählen insbesondere Berechtigungs- und Zugriffsverwaltung sowie damit verbundene Wartungs- und Pflegeanforderungen.  Ergänzend wird unzureichende Nachvollziehbarkeit von Änderungen („wer hat was wann geändert“) als relevantes Problemfeld sichtbar, insbesondere dort, wo Änderungen nicht konsistent über standardisierte Automationspfade abgebildet werden. 

### 1.4 Dev- und Deployment-bezogene Reibungspunkte

Die operativen Reibungspunkte konzentrieren sich im Material auf wiederkehrende Schwierigkeiten entlang der Toolchain und des Release-/Deployment-Alltags. Besonders deutlich werden Herausforderungen in der **Fehleranalyse von Pipelines**, in der **korrekten Nutzung** von Werkzeugen ohne verbindliche Leitlinien sowie in compliance- und qualitätsbezogenen Prozessschritten (z. B. Scans, Quality Gates).

Die Werkzeugnennungen zeigen eine stark toolchain-orientierte Praxis: Als regelmäßig genutzte Plattformen und Werkzeuge werden insbesondere Azure DevOps/Azure Pipelines sowie ergänzende Komponenten wie Artifactory/JFrog Platform und Code- bzw. Compliance-Checks (z. B. Black Duck) genannt.  In einzelnen Aussagen werden konkrete Reibungspunkte wie Probleme mit artefaktbezogenen Schlüssel-/Zugriffsdateien und deren Berechtigungskontext sichtbar, was das Zusammenspiel aus Toolzugriffen, Credential-Management und Build/Release-Prozessen als wiederkehrende Fehlerquelle nahelegt. 

Auffällig ist ferner, dass Kubernetes als Plattformtechnologie im Alltag nicht durchgängig als direktes Arbeitsmittel erscheint. In einem Antwortfeld geben 6 von 15 Personen „keine Rolle“ bzw. „keine Nutzung“ an; gleichzeitig finden sich vereinzelte Hinweise auf indirekte Berührungspunkte (z. B. Orchestrierung als Hintergrundkonzept).  Diese Verteilung legt nahe, dass ein Teil der Entwicklungsarbeit Plattformkapazitäten eher **indirekt** (über Pipelines, standardisierte Umgebungen, bereitgestellte Services) konsumiert als über unmittelbare Interaktion mit Clusterobjekten. 

### 1.5 Herausforderungen in Tooling, Infrastruktur und Zusammenarbeit

Im Bereich Tooling zeigt der Korpus eine funktional breite Landschaft, in der mehrere Systeme parallel im Einsatz sind (CI-Systeme, Build-Tooling, Artefaktmanagement, Qualitäts-/Compliance-Checks, Infrastrukturwerkzeuge).  Gleichzeitig wird wiederholt sichtbar, dass die Nutzung dieser Werkzeuge nicht überall durch verbindliche Standards oder klare Guidelines gerahmt ist; einzelne Aussagen benennen explizit den Umstand, dass Tools „ohne Guideline“ genutzt werden, und verknüpfen dies mit wiederkehrenden Problemen.  Die Folge ist eine erhöhte Varianz in Konfigurationen, die sich in der Praxis als erhöhter Debugging-Aufwand, inkonsistente Qualität und zusätzlicher Abstimmungsbedarf niederschlägt. 

Infrastrukturbezogen tritt die hybride Betriebsrealität als struktureller Komplexitätsverstärker hervor. Hinweise auf „on-premise“, Cloud sowie Mischformen sind wiederkehrend; zudem werden Agenten/Scale Sets und unterschiedliche CI-Setups genannt, was auf verteilte Ausführungsumgebungen und damit verbundene Zugriffs- und Integrationsabhängigkeiten schließen lässt.  Solche Abhängigkeiten wirken im Alltag häufig als „unsichtbare“ Verzögerer, etwa wenn Konnektivität, Credentials oder Berechtigungen über Systemgrenzen hinweg konsistent funktionieren müssen, aber nicht standardisiert sind. 

Hinsichtlich Zusammenarbeit und Verantwortlichkeiten stützt der Korpus das Bild einer dezentralisierten Delivery-Praxis: CI/CD wird vielfach teamspezifisch organisiert, während einzelne Integrations-/Release-Aspekte zentral gebündelt werden.  In einer solchen Mischform entstehen typischerweise Schnittstellenkosten, die im Material indirekt sichtbar werden: divergierende Pipeline-Logiken, unterschiedliche Toolnutzung, variierende Standards und damit erhöhte kognitive Last beim Wechsel zwischen Projekten. 

Die Transparenz über den Betriebszustand (Health, Logs, Deployment-Status) wird im Korpus nicht einheitlich als ausgereift beschrieben. Während einzelne Aussagen grundlegende Monitoring-Möglichkeiten (z. B. über Plattformfeatures) als vorhanden beschreiben, werden zugleich Hinweise auf begrenzte Tiefe, „Basisfunktionalität“ und Datenqualitätsprobleme („junk data“) sichtbar.  Diese Spannbreite deutet auf uneinheitliche Observability-Reifegrade und auf fehlende Standardisierung in der Operationalisierung von Monitoring- und Statusinformationen hin. 

### 1.6 Verdichtung der zentralen Beobachtungen

In der Gesamtverdichtung beschreibt der Interviewkorpus einen Status quo, der durch eine **hybride Infrastrukturrealität**, eine **breite, aber heterogene Toolchain** sowie eine **dezentral geprägte Delivery-Praxis** gekennzeichnet ist.  Die dominanten Belastungen entstehen weniger aus einem Mangel an Technologien als aus fehlender Durchgängigkeit: Standards, Guidelines und wiederverwendbare Vorgehensweisen sind nicht flächendeckend etabliert, wodurch sich die tägliche Praxis zwischen Teams und Projekten merklich unterscheidet.

Als besonders prägende Strukturprobleme lassen sich (i) Prozess- und Koordinationslast (inklusive unklarer Arbeitsaufträge), (ii) Komplexität und Debugging-Aufwand in CI/CD-Konfigurationen sowie (iii) governance-nahe Routinetätigkeiten wie Berechtigungsverwaltung und die Nachvollziehbarkeit von Änderungen identifizieren.  Wiederverwendbarkeit (Templates/Skripte) ist im Korpus zwar sichtbar, erscheint jedoch nicht als durchgängiger Standard, sondern als fragmentiertes Element, das in Teilen vorhanden ist und in anderen Teilen fehlt oder stark variiert.

Insgesamt kennzeichnet der Status quo ein Spannungsfeld aus vorhandener Tool- und Plattformlandschaft einerseits und fehlender Standardisierung, Transparenzkonsistenz sowie hoher manueller Governance-Last andererseits.  Diese Konstellation führt im Alltag zu erhöhter kognitiver Belastung (insbesondere in Troubleshooting- und Integrationssituationen), zu variablen Prozessqualitäten zwischen Teams und zu wiederkehrenden, administrativ geprägten Tätigkeiten, die als zeitintensiv und wenig wertschöpfend beschrieben werden.

============================================================================
# 19.03.2026 ANALYSE II
============================================================================



Im Folgenden wird das bereitgestellte Interviewmaterial **integriert als ein gemeinsamer Datenkorpus** ausgewertet. Die Darstellung ist **vollständig auf Deutsch** verfasst; nicht-deutschsprachige Inhalte werden sinngemäß übertragen und in die Analyse eingearbeitet. Die Auswertung verbindet **qualitativ-inhaltliche Verdichtung** mit **deskriptiven Häufigkeitsangaben**, soweit diese im Material ausgewiesen sind.

---

## Einleitung zur Auswertungslogik

Die Analyse erfolgt in vier Schritten: (1) Rekonstruktion des Status quo entlang zentraler Praxisfelder (Rollen, CI/CD-Organisation, Tooling, Infrastruktur), (2) Verdichtung wiederkehrender Problemkonstellationen (technisch/organisational/prozessual), (3) Ableitung von Anforderungen als empirisch begründete Konsequenz aus den beobachteten Defiziten und Spannungen, (4) Bewertung der Einführungslogik einer IDP unter Berücksichtigung von Kontextbedingungen und im Abgleich zweier konkret benannter Ansätze (Backstage vs. Terraform-basierte Azure-DevOps-Automatisierung).

---

# 1. Analyse des Status quo

## 1.1 Methodischer Zugriff und Datenbasis

Die empirische Grundlage bildet ein Interviewkorpus mit **20 Teilnehmenden**.  Das Material umfasst strukturierte Antworten zu Arbeitsrolle und Einbindung in Build/Deploy/Betrieb, Organisation von CI/CD und Releases, Architektur- und Workloadkontext, Tooling-Nutzung, Wiederverwendbarkeit (Templates/Skripte/Self-Service), Belastungsfaktoren, Self-Service-Bedarf sowie Monitoring-/Observability-Einschätzungen.  Die Auswertung folgt einer qualitativen Inhaltsanalyse mit thematischer Verdichtung: Aussagen werden entlang wiederkehrender Themencluster gebündelt, innerhalb der Cluster nach typischen Ausprägungen strukturiert und – wo im Material vorhanden – mit Häufigkeiten/Anteilen ergänzt (z. B. „team specific“ bei CI/CD-Organisation oder „none“ bei Kubernetes-Rolle).

## 1.2 Aktuelle Entwicklungspraxis und Arbeitsrealität

Die Interviewdaten zeichnen ein Umfeld, in dem Entwicklungsarbeit eng mit Delivery- und Betriebsaspekten verschränkt ist. Bereits die Rollen- und Tätigkeitsangaben zeigen eine deutliche Nähe zu Build-, Deployment- und Integrationsaufgaben; zudem werden in den regelmäßig betreuten Anwendungen/Services und in der Toolnutzung wiederholt CI/CD-nahe Komponenten und Plattformdienste genannt.

Ein prägendes Strukturmerkmal ist die **Organisationsform von CI/CD und Releases**: In einem Teil der Antworten wird CI/CD explizit als **teamspezifisch** organisiert beschrieben; zugleich existieren Hinweise auf zentrale oder koordinierende Elemente (z. B. Integration in Releases, zentral organisierte Release-Bundles oder übergreifende Zuständigkeiten).  In der Summe entsteht das Bild einer Mischform aus dezentraler Umsetzung (teamnahe Pipeline-/Build-Logik) und partieller Zentralisierung (Integrations- oder Releasekoordination).

Die System- und Infrastrukturlandschaft wird als **heterogen** und **hybrid** sichtbar. In den Angaben zur Architektur werden Mischformen häufiger genannt als reine Monolithen; Microservices werden in diesem Antwortfeld nicht als dominierende Form ausgewiesen.  Gleichzeitig zeigen die Workload-Angaben eine deutliche Präsenz von Cloud sowie hybride bzw. on-premise-nahe Konstellationen, inklusive expliziter Hinweise, dass Teile von Systemen „in Azure“ und andere Teile „on-prem“ betrieben werden.

## 1.3 Status-quo-Charakteristika: technische und organisatorische Grundmuster

Drei Status-quo-Merkmale treten wiederkehrend hervor.

Erstens: **Hohe Varianz in Vorgehensweisen und Konfigurationen**. Diese Varianz wird sowohl durch die teamspezifische CI/CD-Organisation als auch durch die Streuung in Toolnutzung, Pipeline-Ausprägungen und Wiederverwendbarkeitsgrad gestützt.

Zweitens: **Werkzeug- und Plattformlandschaft als Patchwork**. Als regelmäßig genutzte Komponenten erscheinen u. a. Azure DevOps/Azure Pipelines, Artifactory/JFrog Platform, TeamCity (z. B. für interne CI) sowie weitere Build-/Scan-Tools.  Dies verweist auf parallel bestehende Toolstränge (z. B. „intern“ vs. „publishing/release“), die Koordination, Standardisierung und Schnittstellenkonsistenz erschweren. 

Drittens: **Kubernetes ist kein durchgängiges Alltagsinstrument**. In einem Antwortfeld wird Kubernetes von einem relevanten Anteil als „keine Rolle“ im täglichen Workflow beschrieben.  Das legt nahe, dass Plattformkapazitäten häufig indirekt (über CI/CD, bereitgestellte Umgebungen und standardisierte Services) konsumiert werden und eine „Portal“-Schicht daher eher als Abstraktion und nicht als „Kubernetes UI“ zu verstehen ist. 

---

# 2. Zentrale Probleme im Ist-Zustand

## 2.1 Technische Probleme

Im technischen Bereich treten vor allem Komplexitäts- und Stabilitätsprobleme entlang der Delivery-Kette auf. Wiederholt werden Pipeline-Themen als zeitaufwendig oder kognitiv belastend genannt, insbesondere das Verständnis von YAML-Pipeline-Details und die Fehleranalyse („pipeline problems“, „error analysis“, „pipelines is tricky“).  Ebenso wird die Abhängigkeitssteuerung zwischen Pipelines als Herausforderung benannt („managing the dependencies between pipelines“). 

Ein zweiter technischer Problembereich betrifft toolchain-nahe Integrationspunkte, insbesondere Artefakt- und Compliance-Kontexte. Im Material werden z. B. Schwierigkeiten im Umgang mit Artifactory (inkl. Schlüssel-/Zugriffsdateien) sowie Toolnutzung ohne klaren Leitfaden erwähnt; auch Scan-/Compliance-Werkzeuge werden als Teil der Alltagsrealität sichtbar.

Schließlich deutet der Korpus auf eine ungleichmäßige Transparenz über den Betriebszustand hin. Monitoring wird teils als nur „grundlegend“ beschrieben, teils als verbesserungswürdig; daneben erscheinen Hinweise auf Datenqualität („junk data“) und unklare Zustandsbilder.

## 2.2 Organisatorische und prozessuale Probleme

Prozessuale Friktionen werden explizit benannt: langwierige Prozesse, Bürokratie und ungenau spezifizierte Tickets mit nachgelagerter Klärung/Nacharbeit.  Solche Aussagen sind als strukturell bedeutsam zu interpretieren, weil sie eine wiederkehrende Form organisatorischer Ineffizienz markieren: fehlende Standardisierung der Eingaben (Anforderungen), fehlende klare Schnittstellen und daraus resultierende Schleifen zwischen Anfrage, Klärung und Umsetzung.

Ein weiterer organisationaler Engpass liegt in governance-nahen Routineaufgaben, insbesondere im Berechtigungsmanagement. Dieses wird im Material als Self-Service-Wunsch sowie als konkreter Automatisierungsbedarf formuliert („Permission Management (Setzen von Berechtigungen)“; „gute Pflege- und Wartbarkeit Permission Management“).  Das deutet darauf hin, dass Zugriffs-/Rechteprozesse als wiederkehrend und zugleich als belastend wahrgenommen werden, insbesondere wenn sie stark manuell und ticketgetrieben organisiert sind. 

---

# 3. Dev- & Deployment-Pain Points

## 3.1 Typische Reibungspunkte im Entwicklungsalltag

Die interviewbasierten Pain Points konzentrieren sich auf Tätigkeiten, die viel Zeit beanspruchen, aber als wenig wertschöpfend beschrieben werden: das Navigieren in Toollandschaften ohne klare Guidelines, das Debugging und Testen von Pipelines sowie wiederkehrende Standardprobleme („common issues“) im Build-Kontext.  Ergänzend werden Einarbeitung in neue Themen sowie die Einführung neuer Tools als kognitiv belastend genannt, insbesondere in Verbindung mit langwierigen Prozessen. 

Hinsichtlich Wiederverwendbarkeit ist ein ambivalentes Bild sichtbar: In einem Teil des Korpus werden Templates und Skripte genannt (z. B. „pipeline_templates“, „official templates“, „own scripts“), zugleich wird in anderen Aussagen „sehr wenig bis gar nichts“ an wiederverwendbaren Self-Service-Lösungen beschrieben.  Die Varianz deutet darauf hin, dass Wiederverwendbarkeit nicht organisationsweit standardisiert ist, sondern lokal unterschiedlich stark ausgeprägt sein kann.

## 3.2 Deployment-bezogene Engpässe und Risiken

Deployment-bezogene Engpässe zeigen sich weniger als einzelne „Deploy-Fehler“, sondern als systemische Belastungen entlang der Pipeline- und Governance-Kette: Abhängigkeiten zwischen Pipelines, fehlende Standardisierung der Pipeline-Logik und unzureichende Klarheit über Zustände/Logs im Betrieb.  Hinzu kommen Sicherheits- und Compliance-Schritte als feste Bestandteile der Delivery-Praxis (z. B. Scans, Toolketten für Qualitätsprüfungen), die bei fehlenden Leitlinien oder inkonsistenter Implementierung zu wiederkehrender Friktion beitragen. 

---

# 4. Herausforderungen in Tooling, Infrastruktur & Governance

## 4.1 Tooling und Integrationslandschaft

Die Tooling-Landschaft ist breit und umfasst parallel genutzte CI-/Delivery-Umgebungen (z. B. TeamCity für interne CI und Azure Pipelines für Publizierung), Artefaktmanagement (Artifactory/JFrog Platform) sowie weitere Entwicklungs- und Compliance-Werkzeuge.  Diese Parallelität ist als strukturelle Integrationsherausforderung zu werten: Je mehr Toolketten existieren, desto höher ist der Bedarf an konsistenten Standards, Wiederverwendung und klaren Schnittstellen – andernfalls entsteht Varianz, die unmittelbar in Debugging- und Abstimmungsaufwand übergeht.

## 4.2 Infrastrukturzugang, Standardisierung und Automatisierung

Die Workload-Angaben belegen einen hybriden Infrastrukturkontext (Cloud, On-Premise, Mischformen).  Solche Umgebungen erhöhen typischerweise die Komplexität von Zugriffen (Agenten/Runner, Netzwerkpfade, Credentials) und erfordern stärkere Standardisierung, um reproduzierbare Abläufe zu sichern. Hinweise auf Agenten/Scale Sets sowie auf die Notwendigkeit, neue Teams/Setups in bestehende Strukturen einzubinden („adding new teams…“, „project map“) unterstützen diesen Befund.

Zum Automationsgrad zeigt das Material eine Doppelperspektive: Einerseits wird „ein gutes Automationsniveau“ genannt, andererseits werden konkrete Automationswünsche formuliert (z. B. Git-Repos erstellen/einrichten, Infrastrukturprovisionierung, Permission Management).  Diese Koexistenz ist als Hinweis zu interpretieren, dass Automation vorhanden ist, aber nicht notwendigerweise organisationsweit als standardisierte, leicht konsumierbare Fähigkeit (Self-Service mit konsistenten Inputs/Outputs) etabliert ist.

## 4.3 Governance, Security, Compliance und Verantwortlichkeiten

Im Korpus sind Governance- und Security-Aspekte vor allem indirekt über Toolketten (Scans/Compliance) und über Berechtigungs- bzw. Rechtefragen präsent.  Die explizite Nennung von Permission Management als Self-Service/Automationsziel verweist auf ein Governance-Feld, das operativ belastend ist und zugleich eine erhöhte Fehler- und Risikosensitivität trägt.

Verantwortlichkeiten erscheinen in der Delivery-Praxis dezentralisiert (teamspezifische CI/CD-Organisation), ergänzt um koordinierende Rollen.  Daraus folgt ein Status quo, in dem Standards und Zuständigkeiten nicht immer als organisationsweit konsistent wahrgenommen werden, was wiederum mit den genannten Leitlinien-/Guideline-Lücken kompatibel ist. 

---

# 5. Abgeleitete Anforderungen und Erwartungen an eine IDP

## 5.1 Funktionale Anforderungen

Aus den wiederkehrenden Problemkonstellationen lassen sich Anforderungen ableiten, die im Material als Bedarf nach Standardisierung, Self-Service und Wissenskonsolidierung sichtbar werden. Als konkrete Automations-/Self-Service-Themen treten insbesondere die Einrichtung neuer Repositories, der Umgang mit Berechtigungen und die Vereinfachung wiederkehrender Pipeline-/Build-Aufgaben hervor.  Ebenso erscheinen Erwartungen an eine Wissensbasis bzw. ein zentrales Informationssystem („knowledge database“, „database with info“, „use cases“) im Zusammenhang mit kognitiver Last und fehlenden Guidelines. 

## 5.2 Nicht-funktionale Anforderungen

Nicht-funktionale Anforderungen ergeben sich vor allem aus Governance- und Betriebsaspekten: Nachvollziehbarkeit von Änderungen, klare Verantwortlichkeiten/Ownership sowie eine verlässliche Transparenz über Betriebszustand, Logs und Deployment-Status.  Zudem impliziert die hybride Infrastrukturrealität Anforderungen an robuste Integrationsfähigkeit und konsistente Zugriffskonzepte (Agenten/Runner, Credentials, Netzpfade).

## 5.3 Organisatorische und kulturelle Anforderungen

Organisatorisch weisen die Antworten auf einen Bedarf nach Standardisierung durch Guidelines, Best Practices und reduzierter Variabilität in der Toolnutzung hin.  Die wiederkehrende Problemform „Toolnutzung ohne Guideline“ verweist nicht allein auf technische Defizite, sondern auf fehlende organisatorische Rahmung und Wissenstransfermechanismen. 

---

# 6. Wiederkehrende Themencluster und Prioritäten

## 6.1 Themencluster

Übergreifend lassen sich sechs Cluster als strukturbildend identifizieren: (1) CI/CD-Komplexität und Pipeline-Debugging, (2) Toolchain-Fragmentierung und Integrationsbrüche, (3) Standardisierungslücken (Guidelines/Best Practices), (4) Governance-Routinearbeit (Permissions/Rights), (5) hybride Infrastruktur- und Ausführungsumgebungen (Cloud/On-Prem, Agents/Scale Sets), (6) ungleichmäßige Observability/Transparenz (Health/Logs/Status).

## 6.2 Priorisierung nach Relevanz und Dringlichkeit

Als besonders hochrelevant erscheinen diejenigen Themen, die zugleich häufig genannt werden und unmittelbar in Zeitverlust, Fehleranfälligkeit oder Koordinationsaufwand übergehen: Pipeline-Komplexität/Debugging, fehlende Guidelines in Toolnutzung sowie Berechtigungsmanagement.  Toolchain-Fragmentierung und hybride Infrastruktur wirken als Verstärker dieser Probleme, weil sie Standardisierung und Wiederverwendung erschweren.  Observability erscheint als gemischtes Feld: Es ist präsent, wird jedoch nicht einheitlich als ausreichend beschrieben, was auf inkonsistente Reifegrade und Datenqualitätsprobleme hindeutet.

---

# 7. Wissenschaftlich fundierte Schlussfolgerung

## 7.1 Einordnung der Ergebnisse

Die Interviewdaten belegen ein Umfeld mit funktional umfangreicher Tool- und Plattformlandschaft, in dem die zentrale Belastung weniger aus dem Fehlen von Technologien entsteht als aus fehlender Durchgängigkeit: Variabilität in CI/CD-Organisation und Pipeline-Logik, fehlende Guidelines und wiederkehrende governance-nahe Routinetätigkeiten führen zu kognitiver Last, Debugging-Aufwand und Koordinationskosten.

Gleichzeitig zeigen die Daten eine gewisse Ambivalenz: In einzelnen Antworten wird ein bereits gutes Automationsniveau beschrieben oder es werden keine nennenswert zeitfressenden Tätigkeiten gesehen.  Diese Streuung ist als Indikator zu interpretieren, dass Probleme nicht überall gleich stark ausgeprägt sind, sondern domänenspezifisch bzw. team-/kontextabhängig variieren können. 

## 7.2 Begründete Bewertung der IDP-Einführung

Die Einführung einer IDP ist im Korpus nicht als Selbstzweck legitimiert, sondern dort plausibel, wo sie empirisch beobachtbare Defizite adressiert: Standardisierungslücken (Guidelines/Best Practices), wiederkehrende Routinearbeit (z. B. Permissions), fehlende Konsistenz in wiederverwendbaren Templates sowie Transparenz-/Observability-Lücken.  Gleichzeitig sind im Material auch skeptische oder unklare Erwartungen sichtbar (z. B. „none“ bei erwarteten Benefits), was darauf hinweist, dass eine IDP nur dann als sinnvoll wahrgenommen wird, wenn sie konkrete, alltagsnahe Reibungen reduziert und nicht als zusätzliche Schicht ohne klaren Mehrwert erlebt wird.

## 7.3 Bedingungen, Grenzen und Risiken der Einführung

Als Bedingung für Sinnhaftigkeit ist aus dem Material ableitbar, dass Standardisierung und Wiederverwendbarkeit organisationsweit konsistent werden müssen; andernfalls reproduziert eine Plattform lediglich die bestehende Varianz.  Ein weiteres Risiko liegt in der Heterogenität der Ausgangslage (hybride Infrastruktur, mehrere CI-Stränge): Ohne klare Abgrenzung dessen, was „standardisiert“ wird, droht Komplexitätszuwachs statt Reduktion.

---

# 8. Vergleich von Backstage IDP und Terraform Azure DevOps Manager

## 8.1 Vergleich entlang der abgeleiteten Anforderungen

Das Interviewmaterial macht deutlich, dass ein relevanter Teil der Reibungspunkte **prozess- und toolchain-nah** ist (Repo-/Setup-Themen, Permissions/Rights, Guidelines/Best Practices, Wiederverwendung von Templates, Pipeline-Komplexität).  Daraus folgt, dass zwei unterschiedliche Klassen von Lösungen adressierbar sind:

Ein Backstage-basierter Ansatz zielt auf eine **zentral sichtbare und strukturierte Interaktionsschicht** (Portal) mit kuratierten Einstiegspunkten, Templates und Wissenskonsolidierung – also direkt auf die im Material sichtbaren Lücken bei Guidelines, Wissensbasis und Standardpfaden („templates“, „knowledge database“, „use cases“, „developer platform“).

Ein Terraform-basierter „Azure DevOps Manager“-Ansatz adressiert demgegenüber primär die **Konfiguration und Reproduzierbarkeit von Azure-DevOps-Objekten als Code** (z. B. Projekte, Repos, Service Connections, Autorisierungen). Das passt zu Automationswünschen wie „Erstellung und Einrichtung von Git Repos“ und zu wiederkehrenden „Rights/Permission settings“, sofern diese in ADO-nahen Ressourcen ausdrückbar sind.  Zudem ist dokumentiert, dass der Azure DevOps Terraform Provider zur Konfiguration von Azure DevOps Projekten über die REST API genutzt wird. ([registry.terraform.io][1])

## 8.2 Stärken, Schwächen und Eignung beider Ansätze

**Backstage** ist im Lichte der Daten dort besonders passend, wo die Probleme aus fehlender Standardisierung, fehlender Auffindbarkeit von Wissen/Standards und aus teamspezifischer Varianz entstehen: Ein Portalansatz kann die im Material mehrfach sichtbaren Themen „Guidelines“, „Best Practices“, „Templates“ und „Wissensbasis“ bündeln und als konsistente Oberfläche anbieten.  Die Eignung steigt, wenn die Organisation eine „Frontdoor“ benötigt, die über mehrere Tools hinweg Orientierung schafft (CI-Systeme, Artefakte, Scans), was im Tooling-Bild des Korpus plausibel ist.

**Terraform (Azure DevOps Provider)** ist im Vergleich dort besonders stark, wo der Kern der Reibung in wiederkehrender, standardisierbarer ADO-Konfiguration liegt: Projekte/Repos, definierte Strukturen, Pipeline-Autorisierungen und ähnliche Objekte lassen sich als Code reproduzieren und damit konsistent ausrollen. ([registry.terraform.io][1]) Dies adressiert die im Material sichtbaren Automationswünsche im Bereich Repo-Setup und (teilweise) Berechtigungs-/Autorisierungsthemen.  Allerdings liegt ein strukturelles Limit darin, dass Terraform als IaC-Werkzeug primär die **Provisionierung/Desired State** abbildet, aber nicht automatisch die im Material sichtbaren Bedürfnisse nach „Guidelines“, „Wissensbasis“ und einer konsistenten Nutzerinteraktion ersetzt.  Zudem zeigen provider-spezifische Themen (z. B. Autorisierungsressourcen), dass Berechtigungsthemen in ADO technisch anspruchsvoll und von privilegierten Rechten abhängig sein können, was die praktische Umsetzungskomplexität erhöht. ([registry.terraform.io][2])

## 8.3 Begründete Empfehlung für den Unternehmenskontext

Auf Basis des Materials ist die Eignungsfrage nicht als „entweder Portal oder IaC“ zu verstehen, sondern als Abgleich mit dem dominanten Problemprofil: Wenn die zentralen Belastungen in **Orientierung, Standardisierung, Wiederverwendung und konsistenter Interaktion** über eine heterogene Toollandschaft liegen (Guidelines/Best Practices, Wissensbasis, Template-Varianz, teamspezifische Prozesse), dann passt ein Backstage-Ansatz stärker zum im Korpus erkennbaren Bedarf an Struktur und Konsistenz.  Wenn der Schwerpunkt dagegen primär auf der **reproduzierbaren Konfiguration von ADO-Objekten** liegt (Repo-/Projektanlage, standardisierte ADO-Strukturen, bestimmte Autorisierungen), ist Terraform als „Manager“ der ADO-Konfiguration sachlogisch näher an der Ausführungs-/Provisionierungsebene.

Die Interviewdaten enthalten zugleich skeptische bzw. unklare Benefit-Erwartungen einzelner Teilnehmender („none“), was nahelegt, dass jede Plattforminitiative nur dann als gerechtfertigt wahrgenommen wird, wenn sie konkrete, häufige Reibungspunkte reduziert (z. B. Pipeline-Komplexität, Toolnutzung ohne Guidelines, Berechtigungsaufwand).  Vor diesem Hintergrund ist eine IDP-Einführung im betrachteten Umfeld dann belastbar begründbar, wenn sie unmittelbar auf die im Material dominanten Problemfelder einzahlt und nicht als zusätzliche Komplexitätsebene neben einer bereits heterogenen Toolchain erlebt wird.

---

## Prägnante Gesamtsynthese

Die Interviews beschreiben eine Entwicklungs- und Bereitstellungsrealität, die durch hybride Infrastruktur, parallele Toolketten und eine überwiegend teamnahe Organisation von CI/CD geprägt ist.  Die zentrale Belastung entsteht weniger aus fehlenden Werkzeugen als aus fehlender Durchgängigkeit: wiederkehrende Pipeline-Komplexität und Debugging-Aufwand, Toolnutzung ohne verbindliche Guidelines, fragmentierte Wiederverwendbarkeit sowie governance-nahe Routinetätigkeiten (insbesondere Berechtigungsmanagement) erhöhen kognitive Last und Koordinationskosten.  Aus diesen Mustern lassen sich Anforderungen ableiten, die entweder eine Portal-/Interaktionsschicht zur Standardisierung und Wissenskonsolidierung (Backstage) oder eine IaC-basierte Reproduzierbarkeit von ADO-Konfiguration (Terraform Azure DevOps Provider) adressieren; die stärkere Eignung hängt dabei davon ab, ob im konkreten Kontext primär Interaktions- und Standardisierungslücken oder primär ADO-nahe Provisionierungs-/Konfigurationsbedarfe dominieren.

[1]: https://registry.terraform.io/providers/Microsoft/azuredevops/latest/docs?utm_source=chatgpt.com "AzureDevops - microsoft - Terraform Registry"
[2]: https://registry.terraform.io/providers/microsoft/azuredevops/1.8.1/docs/resources/pipeline_authorization?utm_source=chatgpt.com "azuredevops_pipeline_authoriza..."


========================================================

======================================================


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


Verstanden. In diesem Teil geht es **nicht** um Theorie und **nicht** um eine reine Kurzfassung, sondern um eine **präzise, fachlich dichte Beschreibung der Implementierung**. Also: direkt auf den Punkt, aber mit genug Substanz für eine Masterarbeit.

Unten ist die **ausgewogene Fassung** von **7.4 bis zum Abschluss des Implementierungsteils**.

---

## **7.4 Governance, Sicherheit und Compliance**

Governance, Sicherheit und Compliance wurden als feste Randbedingungen der Implementierung behandelt. Backstage wurde deshalb nicht als Ausführungsplattform für privilegierte Operationen konzipiert, sondern als kontrollierte Interaktionsschicht. Die eigentliche Ausführung fachlicher Prozesse erfolgt über Azure DevOps Pipelines, Infrastructure-as-Code und definierte Skripte. Dadurch bleibt die technische Kontrolle über Änderungen in den bestehenden Automatisierungs- und Governance-Mechanismen verankert.

Für den Zugriff auf Plattformfunktionen wurde ein rollenbasiertes Modell vorgesehen. Nicht jede Benutzergruppe soll dieselben Templates oder Aktionen ausführen können. Besonders relevante Aspekte waren hierbei die Absicherung sensibler Funktionen, die Trennung von Zuständigkeiten sowie die Nachvollziehbarkeit von Änderungen. Zugangsdaten und API-Tokens wurden nicht im Anwendungscode hinterlegt, sondern außerhalb der Anwendung verwaltet. Auf diese Weise wurde eine Grundlage geschaffen, um Self-Service-Funktionen bereitzustellen, ohne Sicherheits- und Compliance-Anforderungen zu unterlaufen.

---

## **7.5 Umgang mit heterogenen Teamanforderungen**

Die Implementierung musste unterschiedliche technische und organisatorische Ausgangsbedingungen berücksichtigen. Teams arbeiten nicht vollständig einheitlich, nutzen verschiedene Werkzeuge und unterscheiden sich in ihrer Nähe zu Build-, Deployment- und Betriebsprozessen. Die IDP wurde daher nicht als starres System mit nur einem einzigen Standardpfad umgesetzt, sondern als standardisierte Grundstruktur mit kontrollierter Variabilität.

Dieses Prinzip wurde insbesondere über Templates realisiert. Templates definieren einen festen Rahmen für wiederkehrende Prozesse, erlauben jedoch parametrisierbare Eingaben für kontextspezifische Unterschiede. Dadurch wird Standardisierung erreicht, ohne die Plattform auf einen einzigen technologischen Sonderfall zu beschränken. Die Plattformarchitektur bleibt damit anschlussfähig für unterschiedliche Teams, reduziert aber gleichzeitig die im Unternehmen beobachtete Varianz bei Setup, Pipeline-Konfiguration und Plattformnutzung.

---

## **7.6 Zusammenfassung der Konzeption**

Die konzeptionelle Grundlage des Prototyps besteht in der klaren Trennung zwischen Portal, Ausführung und Governance. Backstage bildet den zentralen Einstiegspunkt. Die fachliche Ausführung verbleibt in bestehenden Automatisierungsmechanismen. Damit entsteht keine konkurrierende Parallelplattform, sondern eine ordnende und standardisierende Schicht über der vorhandenen Toollandschaft.

Die Konzeption adressiert insbesondere drei Zielrichtungen: Reduktion technischer und prozessualer Varianz, Verbesserung der Transparenz über Services und Workloads sowie Bereitstellung erster kontrollierter Self-Service-Funktionen. Der Prototyp ist damit als IDP-MVP ausgelegt, der einen realen Plattformnutzen demonstriert, ohne bereits den Umfang einer vollständigen Produktivplattform zu beanspruchen.

---

## **8. Testen und Veröffentlichen von Templates**

Die entwickelten Templates wurden nicht nur syntaktisch geprüft, sondern als vollständige Scaffolding-Abläufe getestet. Im Mittelpunkt stand dabei die Frage, ob aus einem Template unter realistischen Bedingungen tatsächlich ein konsistentes Ergebnis entsteht. Geprüft wurden die Parameterverarbeitung, die korrekte Erzeugung von Artefakten, die Verlinkung der Ergebnisse sowie die Nutzbarkeit der erzeugten Ressourcen in den Zielsystemen.

Nach erfolgreicher Validierung wurden die Templates so eingebunden, dass sie über den Backstage-Katalog verfügbar sind. Damit wurden aus technischen Template-Definitionen tatsächlich nutzbare Plattformfunktionen. Dieser Schritt war für die Implementierung wesentlich, da der Mehrwert eines IDP nicht in der Existenz von Templates liegt, sondern in deren verlässlicher Nutzbarkeit durch Entwicklungsteams.

**Screenshot hier**

---

## **9. TechDocs und Documentation-as-Code**

TechDocs wurde integriert, um Dokumentation als Bestandteil der Plattform und nicht als separates Artefakt zu behandeln. Dokumentationen sind dadurch direkt mit Katalogentitäten verknüpft und gemeinsam mit dem zugehörigen Code bzw. Service verwaltbar. Dieser Ansatz unterstützt eine konsistente, repository-nahe Pflege technischer Inhalte.

Für die Implementierung wurde ein Documentation-as-Code-Ansatz mit MkDocs berücksichtigt. Dadurch lassen sich technische Beschreibungen, Onboarding-Hinweise und Nutzungsinformationen versioniert und reproduzierbar verwalten. Im Kontext des Prototyps ist dies besonders relevant, da ein Internal Developer Portal nicht nur Funktionen bereitstellen, sondern auch deren Nutzung nachvollziehbar erklären muss.

**Screenshot hier**

---

## **10. Containerisierung mit Docker sowie Sicherheitsaspekte**

Zur Überführung der lokalen Backstage-Instanz in eine portable und clusterfähige Form wurde ein Docker-Image erstellt. Die Containerisierung stellte sicher, dass Anwendung und Laufzeitabhängigkeiten in reproduzierbarer Form gebündelt werden. Dadurch wurde eine belastbare Grundlage für die Bereitstellung in Kubernetes geschaffen.

Im Rahmen der Containerisierung wurden zentrale Sicherheitsaspekte berücksichtigt. Dazu gehörten die Trennung von Anwendung und Laufzeitkonfiguration, der Verzicht auf hartkodierte Zugangsdaten sowie die Vorbereitung eines sicheren Secret-Handlings. Ziel war kein vollständig gehärtetes Produktivsetup, sondern eine saubere, produktionsnahe Basis, die spätere Erweiterungen in Richtung AKS-Betrieb und GitOps unterstützt.

**Screenshot hier**

---

## **11. Integration von Keycloak zur Authentifizierung**

Für die Authentifizierung wurde Keycloak als OIDC-basierter Identity Provider integriert. Diese Entscheidung diente dazu, den Prototypen an ein realistisches Unternehmensszenario anzunähern und gleichzeitig eine saubere Grundlage für spätere Rollen- und Berechtigungskonzepte zu schaffen. Die Integration umfasste die Konfiguration der erforderlichen Clients, Redirect-URIs und Vertrauenseinstellungen zwischen Backstage und Keycloak.

Die Authentifizierung war nicht nur ein technischer Konfigurationsschritt, sondern ein wesentlicher Bestandteil der Plattformarchitektur. Erst durch eine zentrale Identitätsverwaltung wird das Portal in die Lage versetzt, Benutzerkontexte, Rollen und zugriffsbezogene Entscheidungen konsistent zu verarbeiten. Die Analyse und Behebung von Authentifizierungsfehlern war daher ein notwendiger Teil der Implementierung.

**Screenshot hier**

---

## **12. Role-Based Access Control (RBAC) und Permissions**

Aufbauend auf der Authentifizierung wurde ein rollenbasiertes Zugriffskonzept umgesetzt. Ziel war die kontrollierte Freigabe von Portal-Funktionen in Abhängigkeit von Benutzergruppen und Verantwortlichkeiten. Hierfür wurde das Berechtigungsframework von Backstage aktiviert und mit einem gruppenbasierten Rollenmodell verknüpft.

Das Rollenmodell bildet die Grundlage dafür, dass Templates, Katalogaktionen und potenziell sensible Funktionen nicht für alle Benutzer gleichermaßen freigegeben werden. Dies ist insbesondere für Self-Service-Funktionen relevant, die in bestehende Delivery- oder Berechtigungsprozesse eingreifen. Die RBAC-Umsetzung stellt damit sicher, dass die Plattform nicht nur standardisierte Interaktion ermöglicht, sondern diese zugleich kontrolliert und nachvollziehbar bleibt.

---

## **13. Deployment von Backstage auf Kubernetes (AKS)**

Nach der lokalen Validierung wurde der Prototyp auf dem Azure Kubernetes Service (AKS) des Unternehmens bereitgestellt. Damit wurde der Übergang von einer isolierten Entwicklungsumgebung in eine unternehmensnahe Laufzeitumgebung vollzogen. Die Anwendung wurde containerisiert, als Kubernetes-Workload deployt und mit den erforderlichen Laufzeitparametern konfiguriert.

Für das Backend wurde eine Datenbank angebunden, um die für Backstage erforderlichen Zustands- und Konfigurationsdaten persistent zu verwalten. Der Zugriff auf die laufende Instanz erfolgte zunächst kontrolliert über Portweiterleitung. Dieses Vorgehen ermöglichte eine schrittweise Validierung der Integration, bevor eine breitere interne Erreichbarkeit betrachtet wird.

**Screenshot hier**

---

## **14. Konfiguration des Kubernetes-Plugins**

Das Kubernetes-Plugin wurde integriert, um Ressourcen aus dem Cluster im Portal sichtbar zu machen. Ziel war es, Backstage nicht nur als Katalog- und Template-Oberfläche zu nutzen, sondern auch als Einstiegspunkt in den aktuellen Betriebszustand relevanter Workloads. Für diese Verknüpfung wurden Labels und Annotationen verwendet, die Katalogentitäten mit Kubernetes-Ressourcen verbinden.

Zusätzlich wurden Service Accounts und lesende RBAC-Berechtigungen im Cluster eingerichtet. Dadurch konnte Backstage die erforderlichen Ressourceninformationen abrufen, ohne über unnötige Privilegien zu verfügen. Im Zielzustand ist die Entität **„kuka-platform“** im Katalog sichtbar, und die zugehörigen Kubernetes-Ressourcen lassen sich über das Plugin einsehen.

**Screenshot hier**

---

## **15. Entwicklung eines eigenen Backstage-Plugins**

Zur Demonstration der Erweiterbarkeit von Backstage wurde neben den Standardplugins auch die Entwicklung eines eigenen Plugins berücksichtigt. Dieser Schritt war konzeptionell relevant, da ein Internal Developer Portal im Unternehmenskontext langfristig nicht allein auf vorkonfigurierten Standardfunktionen beruhen kann. Vielmehr muss die Plattform in der Lage sein, organisationsspezifische Anforderungen abzubilden.

Das eigene Plugin dient daher als Nachweis, dass Backstage nicht nur konfiguriert, sondern gezielt erweitert werden kann. Im Rahmen des Prototyps wurde damit die Grundlage geschaffen, interne Plattformfunktionen, spezielle Übersichten oder domänenspezifische Bedienoberflächen künftig direkt in das Portal zu integrieren.

---

## **16. Produktionsreife Bereitstellung mittels GitOps**

Für einen produktionsnahen Zielzustand wurde ein GitOps-basierter Betriebsansatz berücksichtigt. Konfigurationsänderungen an der Plattform sollen nicht manuell im Cluster erfolgen, sondern deklarativ, versionskontrolliert und reproduzierbar verwaltet werden. Ein Werkzeug wie ArgoCD eignet sich dafür, Deployments und Änderungen kontrolliert aus einem Git-Repository in die Laufzeitumgebung zu überführen.

Im Kontext dieser Arbeit dient GitOps nicht als vollständig implementierter Produktivbetrieb, sondern als architektonische Zielrichtung für die Verstetigung des Prototyps. Damit wird deutlich, dass die Plattform nicht nur funktional demonstriert, sondern auch in eine skalierbare und nachvollziehbare Betriebslogik eingebettet werden kann.

---

## **Abschluss des Implementierungsteils**

Mit der vorliegenden Umsetzung wurde ein funktionsfähiger Prototyp eines Internal Developer Portals auf Basis von Backstage realisiert und in eine unternehmensnahe Umgebung überführt. Die Plattform läuft auf AKS, ist an zentrale technische Komponenten angebunden und bildet mit Katalog, Authentifizierung, RBAC, Kubernetes-Integration und ersten Self-Service-Funktionalitäten die wesentlichen Bausteine eines IDP-MVP ab.

Im Ergebnis ist die Entität **„kuka-platform“** im Softwarekatalog sichtbar. Kubernetes-Ressourcen können im Portal eingesehen werden. Zentrale Plattformfunktionen lassen sich über Templates und Workflows anstoßen. Damit zeigt die Implementierung nicht nur die technische Umsetzbarkeit des Ansatzes, sondern auch dessen Eignung, Standardisierung, Transparenz und kontrollierten Self-Service in einem realen Unternehmenskontext zusammenzuführen.














