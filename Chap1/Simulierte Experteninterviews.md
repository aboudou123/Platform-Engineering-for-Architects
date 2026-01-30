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

Wenn du möchtest, mache ich als nächsten Schritt **eine saubere Codiertabelle nach Mayring** *pro Persona* (P1–P6) und zeige dir in 1–2 Seiten, **welche Aussagen welche Codes** tragen (Audit Trail).

