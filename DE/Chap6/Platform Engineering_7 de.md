**Teil 3 – Plattformen als Produkt – Best Practices**

Im letzten Teil stellen wir Ihnen die Tools zur Verfügung, mit denen Sie Ihre Plattform hinsichtlich Kosteneffizienz optimieren können, sodass Ihre Nutzer dasselbe tun können. Dazu skizzieren wir die einfachen Schritte, die erforderlich sind, um Transparenz in Ihrer Kostenlandschaft zu schaffen, und stellen Ihnen Best Practices zur Reduzierung Ihrer Infrastrukturkosten vor. Von den Infrastrukturkosten gehen wir zu technischen Schulden über, die sich negativ auf die Wartungskosten des ausgewählten Technologie-Stacks auswirken können, wenn sie nicht richtig behandelt werden. Sie lernen Tools und Frameworks zur Bewertung technischer Schulden kennen und erfahren, wie wichtig es ist, Ihre Entscheidungen zu dokumentieren. Abschließend werfen wir einen Blick in die Zukunft. Sie erfahren, warum Veränderungen unumgänglich sind und warum Sie sich aktiv für Veränderungen einsetzen müssen. Vielleicht entdecken Sie eine neue Perspektive auf Ihren goldenen Weg und einige Ideen zu zukünftigen relevanten Technologien.

Dieser Teil umfasst die folgenden Kapitel:

- [Kapitel 7](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap6/Platform%20Engineering_7%20de.md), Entwicklung sicherer und konformer Produkte
- [Kapitel 8](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap7/Platform%20Engineering_8%20de.md), Kostenmanagement und Best Practices
- [Kapitel 9](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap9/Platform%20Engineering_9%20de.md), Auswahl technischer Schulden, um Plattformen unzerstörbar zu machen
- [Kapitel 10](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap9/Platform%20Engineering_9%20de.md), Entwicklung von Plattformprodukten für die Zukunft

Entwicklung sicherer und konformer Produkte

Im digitalen Zeitalter nehmen Cyberverbrechen zu. Zwar gelten nicht für jedes Unternehmen die strengen Compliance-Anforderungen einer Bank oder einer Regierungsbehörde, doch können und sollten die Sicherheitsstandards und Best Practices für diese stark regulierten Umgebungen auf Ihre Plattform übertragen werden. Sicherheit auf jeder Ebene eines Unternehmens trägt dazu bei, Sicherheitsverletzungen zu verhindern.

Am Ende dieses Kapitels sollten Sie ein besseres Verständnis von Sicherheitsstandards, Frameworks und Trends gewonnen haben. Dazu gehören Tipps zum Verständnis und zur Nutzung einer **Software-Stückliste** (**SBOM**), zum Verständnis von Open-Source-Projekten für die Plattformsicherheit und zum Verständnis von Policy-Engine-Technologien (mit Beispielen und Anwendungsfällen). Sie sollten in der Lage sein, diese Erkenntnisse zu nutzen, um die richtigen Maßnahmen zur Sicherung Ihrer Plattform zu definieren, ohne Ihre Fähigkeiten einzuschränken, und um sicherzustellen, dass der App-Bereitstellungsprozess gehärtete und sichere Software-/Containerpakete liefert.

Daher werden wir in diesem Kapitel die folgenden Hauptthemen behandeln:

- Vereinbarkeit von Sicherheit auf der linken Seite und Zero Trust
- Plattform-Sicherheit verstehen – wie man ein sicheres und dennoch flexibles und offenes System aufbaut
- Betrachtung von SBOM-Praktiken
- Verständnis der Pipelinesicherheit – was Sie beachten müssen, um Ihre **Continuous Integration/Continuous Delivery** (**CI/CD**)-Pipelines zu sichern
- Verständnis der Anwendungssicherheit – Festlegen und Durchsetzen von Richtlinien
- **Freie und quelloffene Software** (**FOSS**) für die Plattformsicherheit und deren Verwendung

Vereinbarkeit von Security to the Left und Zero Trust

**Sicherheit links** und **Zero Trust** sind die aktuellen Schlagworte in der Cybersicherheit. Diese Schlagworte – oder Modewörter, wenn Sie so wollen – werden sicherlich wieder in Vergessenheit geraten, aber die Praktiken, für die sie stehen, werden auch in den kommenden Jahren weiterhin Best Practices sein.

Sicherheit links betrachtet den Prozess der Softwareentwicklung und -bereitstellung als lineares Flussdiagramm, das von links nach rechts gelesen wird. Dieses Diagramm würde in etwa so aussehen:

Abbildung 7.1: Einfacher App-Entwicklungs-Workflow

In diesem stark vereinfachten Beispiel schreibt ein Entwickler Code, der dann in die Quellcodeverwaltung gestellt wird und schließlich als Anwendung für die Nutzer herauskommt. Es ist wichtig, diesen Sicherheits-Workflow auf der rechten Seite, also auf der Anwendungsebene selbst, zu betrachten, aber das ist zu spät. Es gibt bereits drei andere offensichtliche Stellen, an denen mangelnde Sicherheit Schwachstellen schaffen kann, die ausgenutzt werden könnten.

Die Lösung von Sicherheitsproblemen auf Personalebene ist das Wesentliche der Sicherheit auf der linken Seite, aber damit ist die Sicherheit noch nicht abgeschlossen, sondern erst der Anfang. Sicherheit muss in jedem Schritt des Flussdiagramms im Mittelpunkt stehen, damit wir an realistischeren Beispielen sehen können, wie Sicherheit mit der Reichweite erweitert werden muss:

Abbildung 7.2: Erweiterter Entwicklungs- und Bereitstellungs-Workflow

In der vorstehenden Abbildung sehen Sie bereits einige gängige Sicherheits-Best-Practices, die an dem Punkt implementiert sind, an dem Benutzer versuchen, mit der Anwendung und ihrer unterstützenden Infrastruktur zu interagieren. Die Sicherheit auf der Ebene des Entwicklerteams und der Open-Source-Abhängigkeiten, innerhalb der Quellcodeverwaltung, mit CI/CD und auf der Anwendung selbst wird jedoch nicht behandelt. Selbst die Speicherung von Schlüsseln und Geheimnissen, die zwar eine bewährte Vorgehensweise darstellt, erfordert ebenfalls Sicherheitsmaßnahmen für den Zugriff auf diese Passwörter. Sicherheit von Anfang an hilft Ihnen dabei, Ihre Sicherheitsstrategie vom Beginn des Produktlebenszyklus bis zur Auslieferung der fertigen Anwendung an die Endbenutzer zu entwickeln. In der Plattformentwicklung kann dies zu einem Gefühl der Dissonanz zwischen der sichersten Plattform und der Plattform führen, die einen perfekten Self-Service bietet. Da die Plattform den Self-Service für Entwickler unterstützen muss, steht die Plattform, die die vollständige Sicherheitsstrategie besitzt, im Widerspruch zur Flexibilität, die mit dem Self-Service einhergeht. Sie kann daher so viele Einschränkungen auferlegen, dass sie wie eine hohe Eintrittsbarriere wirkt und somit die Akzeptanz der Plattform und die Zufriedenheit der Entwickler gefährdet.

In der Vergangenheit wäre „Trust but Verify“ das Sicherheitsmodell gewesen, um dieses Problem zu lösen. Die Bedeutung ist selbsterklärend. Man vertraut darauf, dass die Entwickler alles Notwendige getan haben, um die gewünschte Sicherheitslage für die Anwendung aufrechtzuerhalten, aber als Plattformteam ist man nicht für die gesamte Sicherheitslage verantwortlich. Diese Plattform würde nach besten Kräften überprüfen, ob alle richtigen Maßnahmen ergriffen wurden, ohne in den Self-Service einzugreifen.

Heutzutage haben sich die Best Practices für Sicherheit geändert, und „Zero Trust“ ist das Gebot der Stunde. Zero Trust geht im Wesentlichen davon aus, dass jeder ein böswilliger Akteur ist (ob dies absichtlich geschieht oder nicht, ist irrelevant). Um diese Sicherheitslage aufrechtzuerhalten, muss die Plattform den Best Practices entsprechen, kann jedoch nicht die Verantwortung für die Anwendung übernehmen. Mit anderen Worten: Die Plattform muss dem Entwicklerteam und den Stakeholdern alle Voraussetzungen bieten, um ein sicheres und konformes Produkt zu unterstützen. Wenn beispielsweise die Sprache Python benötigt wird, könnte eine gesicherte Python-Binärdatei, entweder intern gesichert oder von einem vertrauenswürdigen Anbieter ( ), in einer Image-Registry bereitgestellt werden, auf die alle Benutzer und Anwendungen der Plattform Zugriff haben. Die Verwendung von Python-Slim aus der Docker-Registry ist ebenfalls eine sicherere Wahl und leichter verfügbar. Das Slim-Image ist wahrscheinlich für die meisten Anwendungsfälle geeignet. Von dort aus wäre eine vernünftige und selbstbedienungsorientierte Einschränkung, Workloads abzulehnen, die keine Images aus einer bekannten sicheren Quelle verwenden. Eine Überprüfung in der CI-Pipeline kann dies übernehmen. Wenn die Überprüfung so weit wie möglich nach links verschoben wird, spart das allen Zeit und vermeidet außerdem, dass Rechenleistung für die Verarbeitung einer Änderung aufgewendet wird, die nicht mit der Sicherheitslage konform ist. Das Hinzufügen einer Überprüfung in diesem Teil kann jedoch etwas mühsam sein, da dafür ein Job geschrieben werden muss, der alle Dockerfiles im Repository scannt, analysiert und dann eine Entscheidung trifft. Diese können in Unterverzeichnissen verschachtelt sein, was zwar keine unmögliche Herausforderung ist, aber dennoch mühsam sein kann. Darüber hinaus sollte das Schreiben dieser Art von Funktionalität in CI-Pipelines als außerhalb des Aufgabenbereichs eines durchschnittlichen Plattformteams liegend betrachtet werden.

Aus Sicht der Plattform wäre ein alternativer Ansatz die Verwendung von Policy-Engines und Admission-Webhooks, um alle Pod-Definitionen abzulehnen, die keine vertrauenswürdige Image-Quelle nutzen. Dies ist nicht ganz so extrem wie das Ideal, und hoffentlich verhindern das Entwicklungsteam und die von ihm befolgten Prozesse Fälle, in denen dies notwendig wäre, aber in Zero-Trust-Umgebungen würde diese Richtlinie als letzte Ausfallsicherung dienen, um sicherzustellen, dass nur die richtige Software in Produktionsumgebungen übertragen wird. Es könnte als sinnvoll angesehen werden, dass Images aus öffentlicheren Quellen für die Prototypenentwicklung innerhalb des IDP akzeptabel sind und daher die Ausfallsicherung nur für Produktionsumgebungen erforderlich ist. Auf diese Weise kann die Plattform weiterhin im Dienste des Teams agieren und es nicht unnötig behindern.

Ein weiteres Beispiel wäre, nur Commits in ein GitHub-Repository zu akzeptieren, wenn der Commit signiert ist. Die Signatur bestätigt, dass der Autor und der Code seit dem Anbringen der Signatur nicht manipuliert wurden. Dies kann über Webhooks in einem GitHub-Repository durchgesetzt werden, obwohl der Einfluss des Plattformteams auf GitHub-Organisationen für jedes Unternehmen möglicherweise begrenzt ist; das Sicherheitsteam (falls vorhanden) wird dies wahrscheinlich verlangen. Und obwohl dies ein gutes Beispiel für die Zusammenarbeit von Zero Trust und Security to the Left ist, liegt es wiederum höchstwahrscheinlich außerhalb des Zuständigkeitsbereichs des Plattformteams.

Auch wenn diese Phrasen wie leere Sprüche klingen mögen, scheitern Teams, wenn sie die grundlegenden Prinzipien, für die sie stehen, ignorieren. Richtige Sicherheit ist eine der besten Investitionen, die ein Unternehmen tätigen kann. Sicherheit nach links zu verlagern bedeutet, sie frühzeitig und häufig zu testen.

Jede größere Sicherheitsverletzung und Schwachstelle hätte durch Tests aufgedeckt werden können. Es gibt verschiedene Arten von Tests, darunter einige, die speziell von Sicherheits sfachleuten durchgeführt werden. Unabhängig davon, ob es sich um Penetrationstests oder nur um grundlegende Negativtests in Ihrem Qualitätsmanagementprozess handelt, sollten Sicherheit und Compliance regelmäßig getestet werden, um sicherzustellen, dass es keine unerwarteten Schwachstellen gibt. Dies kann beispielsweise durch die Verwendung von Software auf unerwartete Weise oder einfach durch die Überprüfung der korrekten Berechtigungseinstellungen für Rollen innerhalb des Unternehmens erfolgen.

Nachdem wir nun die Konzepte der Sicherheit auf der linken Seite und „Vertrauen, aber überprüfen“ vorgestellt haben, wollen wir uns ansehen, wie man ein System aufbaut, das sowohl sicher als auch flexibel ist.

Plattform-Sicherheit verstehen – wie man ein sicheres und dennoch flexibles und offenes System aufbaut

Die Plattform ist nicht die Gesamtheit der Sicherheitslage eines Unternehmens, sondern nur ein Teil der Gleichung. Bei der Beurteilung, wie Cybersicherheit oder DevSecOps in die Plattform integriert werden können, muss ein Gleichgewicht gefunden werden. Das Vorziehen der Sicherheit hilft, den Aufwand für das Plattformteam zu reduzieren, aber ein klar definierter Umfang hilft allen, ihren Teil der Sicherheitsgeschichte zu verstehen.

Das Problem in überschaubare Teile zerlegen

Sicherheit und Flexibilität können auch wie zwei Begriffe wirken, die sich diametral gegenüberstehen. Gute Sicherheit ist von Natur aus unflexibel, aber für den Erfolg eines IDP ist es möglich und notwendig, beide Aspekte in Einklang zu bringen. Wie erreichen wir das? Der erste Schritt ist **die Festlegung des Sicherheitsumfangs**.

Der erste Teil der Festlegung des Umfangs besteht darin, zu verstehen, welches Mindestmaß an Sicherheit erforderlich ist. Natürlich sollten wir immer mehr als das absolute Minimum tun. Wenn Sie also verstehen möchten, wie ein Höchstmaß aussehen würde, ist das keine schlechte Idee, aber es kann den Umfang künstlich vergrößern und dazu führen, dass Sie den Wald vor lauter Bäumen nicht mehr sehen. Daher empfehlen wir, mit einem engen Fokus zu beginnen. Sobald Sie wissen, welches Mindestmaß an Sicherheit die Plattform gewährleisten muss, können Sie sich damit befassen, welches Mindestmaß an Sicherheit die Plattform unterstützen muss.

Wenn man sich mit dem Thema Sicherheit beschäftigt, wird man sehr schnell erkennen, wie gefährlich die Welt des Internets ist, und möglicherweise überkorrigieren. Diese Überkorrekturen können die kognitive Belastung erhöhen und eine Barriere für die Nutzung einer Plattform schaffen. Wenn ein guter Entwickler faul ist, muss die Plattform ihm helfen, faul zu sein, und darf keine zusätzlichen Komplexitätsebenen einführen. Aus diesem Grund kann die Plattform zwar nicht die gesamte Cybersicherheitsstrategie einer Organisation übernehmen, spielt aber dennoch eine zentrale Rolle in dieser Strategie. Sicherheit ist gut, Sicherheitstheater ist es nicht.

Zu wissen, wie viel zu viel und wie viel genau richtig ist, ist eine Fähigkeit, die man mit der Zeit verfeinert, und es gibt keine eindeutige Antwort darauf, wann eine Sicherheitsmaßnahme zu viel oder genau richtig ist. Die Antwort lautet immer: Es kommt darauf an. Beispielsweise kann die Absicherung einer Umgebung, sodass sie für das öffentliche Internet nicht zugänglich ist, die Möglichkeit der Projektmitarbeiter beeinträchtigen, von zu Hause aus zu arbeiten. Wenn es sich bei diesem Projekt jedoch um Raumfähren oder Kernreaktoren handelt, ist die luftisolierte Umgebung richtig und keine Überkorrektur.

Viele Sicherheitsexperten haben jahrelang Sicherheitsfragen erforscht und solide Definitionen dafür entwickelt, was es bedeutet, sicher und konform zu sein. Die Abteilung des **National Institute of Standards and Technology** (**NIST**) des US-Handelsministeriums besteht aus solchen Experten, die regelmäßig neue Standards veröffentlichen und bestehende Standards entsprechend der Entwicklung der Branche aktualisieren.

Es lohnt sich, die Arbeit dieser Organisationen zu verstehen, um ein besseres Verständnis dafür zu entwickeln, wie Sicherheit und eine flexible **interne Entwicklerplattform** (**IDP**) zusammenwirken. Da diese Behörden in der Regel Standards für Unternehmen veröffentlichen, die mit der Regierung zusammenarbeiten, ist zu beachten, dass ihre Veröffentlichungen für ein bestimmtes Publikum bestimmt sind und nicht den Austausch mit einem Cybersicherheitsexperten ersetzen, der über Erfahrung in Ihrer spezifischen Branche verfügt.

Umgang mit den OWASP 10

Wenn Sie sich immer noch nicht sicher sind, wo Sie anfangen sollen, hat eine andere Organisation Richtlinien veröffentlicht, die einen guten Ausgangspunkt für die Festlegung des Sicherheitsumfangs bieten. Das **Open Worldwide Application Security Project** (**OWASP**) ([owasp.org](http://owasp.org/)) ist eine gemeinnützige Stiftung, die sich auf Cybersicherheit konzentriert. Als angesehene Gruppe von Sicherheitsexperten ist ihre Top-Ten-Liste zu einem Leitfaden für die Vorhersage und Prävention von Sicherheitsproblemen in Software geworden. Diese Liste wird regelmäßig neu veröffentlicht. Die aktuelle Liste aus dem Jahr 2021 lautet wie folgt:

- A01:2021 – Defekte Zugriffskontrolle
- A02:2021 – Kryptografische Fehler
- A03:2021 – Injektion
- A04:2021 – Unsichere Konzeption
- A05:2021 – Fehlkonfiguration der Sicherheit
- A06:2021 – Anfällige und veraltete Komponenten
- A07:2021 – Identifizierungs- und Authentifizierungsfehler
- A08:2021 – Fehler bei der Software- und Datenintegrität
- A09:2021 – Fehler bei der Sicherheitsprotokollierung und -überwachung
- A10:2021 – Server-Side Request Forgery (SSRF)

OWASP ging noch einen Schritt weiter und führte 2022 zusätzlich eine Kubernetes-spezifische Top-Ten-Liste ein:

- K01: Unsichere Workload-Konfigurationen
- K02: Schwachstellen in der Lieferkette
- K03: Zu freizügige RBAC-Konfigurationen
- K04: Fehlende zentralisierte Durchsetzung von Richtlinien
- K05: Unzureichende Protokollierung und Überwachung
- K06: Defekte Authentifizierungsmechanismen
- K07: Fehlende Kontrollen zur Netzwerksegmentierung
- K08: Fehler bei der Verwaltung geheimer Daten
- K09: Falsch konfigurierte Cluster-Komponenten
- K10: Veraltete und anfällige Kubernetes-Komponenten

Die Listen stimmen weitgehend überein, gelten jedoch beide für einen Kubernetes-basierten IDP. Anstatt diese Listen als umfassende Leitfäden für die Erstellung einer Sicherheitsstrategie zu betrachten, sollten sie als Mindestanforderungen für die Sicherheitsstrategie des IDP angesehen werden, die jedoch einen umfassenden Ausgangspunkt für Ihr Scoping-Projekt darstellen.

Implementierung von Bedrohungsmodellen

Nachdem Sie den Sicherheitsumfang festgelegt haben, ist der zweite Schritt **die Bedrohungsmodellierung**. Ein Bedrohungsmodell ist eine Darstellung aller Faktoren, die die Sicherheit Ihrer Anwendung oder in diesem Fall Ihrer Plattform beeinträchtigen können. Die Durchführung einer Bedrohungsmodellierung ist ein hervorragendes Beispiel dafür, wie man zu den richtigen Schlussfolgerungen für die Sicherheitsstrategie eines Unternehmens gelangt. Sie können diese Top-Ten-Listen als Leitfaden für Ihre Gespräche zum Thema Bedrohungsmodellierung verwenden. Laut „ ” (Was ist Bedrohungsmodellierung?), den Autoren des Threat Modeling Manifesto ([threatmodelingmanifesto.org](http://threatmodelingmanifesto.org/)), sollte ein Bedrohungsmodell die folgenden vier Fragen beantworten:

- Woran arbeiten wir?
- Was kann schiefgehen?
- Was werden wir dagegen tun?
- Haben wir gute Arbeit geleistet?

Sie können beispielsweise mit folgender Frage beginnen: Wir arbeiten daran, wie sich Benutzer beim IDP authentifizieren. Fahren Sie dann mit der Frage fort: Was kann bei zu freizügigen RBAC-Konfigurationen schiefgehen? und arbeiten Sie sich durch jeden dieser Top-Ten-Punkte in der Kubernetes-Liste. Diese Fragen sind täuschend einfach, aber der Umfang erweitert sich schnell, da Frage zwei (Was kann schiefgehen?) und Frage eins (Woran arbeiten wir?) ein Verhältnis von vielen zu eins haben, ebenso wie Frage drei (Was werden wir dagegen tun?) im Vergleich zu Frage vier. In jedem Fall sollte der Fragenkreislauf wiederholt werden, wenn die Antwort auf „Haben wir gute Arbeit geleistet?“ nicht eindeutig „Ja“ lautet. Ein erfolgreiches Bedrohungsmodell und ein erfolgreicher Reaktionsplan werden in Zusammenarbeit mit allen Beteiligten der Plattform erstellt.

Diese Zusammenarbeit im Bereich Sicherheit ist eine der wichtigsten Strategien, um Sicherheit erfolgreich in den Mittelpunkt zu stellen, ohne dabei die Benutzerfreundlichkeit, die Möglichkeit, Beiträge anzunehmen, oder den Self-Service zu beeinträchtigen. Durch einen kollaborativen Prozess der Bedrohungsmodellierung können auch soziotechnische Sicherheitsrisiken angegangen werden. Sicherheit auf der linken Seite bedeutet nicht nur den Computer des Entwicklers, sondern auch den Entwickler selbst. Stellen Sie sicher, dass sie angemessene Vorsichtsmaßnahmen treffen, sich bewusst sind, wie böswillige Akteure versuchen, Situationen zu manipulieren, um Anmeldedaten zu stehlen, und dass sie generell bewährte Verfahren befolgen – beispielsweise, dass sie einen Firmenlaptop nicht im Auto liegen lassen, wo er gestohlen werden könnte.

Gängige Sicherheitsstandards und -frameworks

Um sich in der Welt der Sicherheitsstandards zurechtzufinden, muss man zunächst versuchen, die Sprache der Akronyme zu entschlüsseln. Das Ziel ist nicht, über Nacht zum Sicherheitsexperten zu werden, sondern zu wissen, welches Sicherheitsniveau Sie benötigen, und sicherzustellen, dass die Plattform alles Notwendige tut, um diese Sicherheit zu gewährleisten. Eine einfache Möglichkeit, dieses Problem anzugehen, besteht darin, sich anzuschauen, in welcher Branche Ihr Unternehmen tätig ist und welche Sicherheitsframeworks relevant sind. Ein Krankenhaus oder eine große medizinische Gruppe in den USA müsste beispielsweise die Vorschriften des **Health Insurance Portability and Accountability Act** (**HIPAA**) einhalten. Daher müsste jeder Anbieter einer ähnlichen Organisation, unabhängig vom Standort, in der Lage sein, die Vorschriften v , einzuhalten. Durch das Verständnis der Endkunden und der Bedürfnisse des Entwicklungsteams kann ein Plattformteam bestimmen, welches Maß an Sicherheit und Compliance über die üblichen Best Practices hinaus erforderlich ist.

Werfen wir einen kurzen Blick auf einige Sicherheitsstandards. Diese Liste ist keineswegs vollständig, behandelt jedoch einige der gängigsten Standards:

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
| **Standard** | **Standort** | **Stufen** | **Beschreibung** | **Anmerkungen** |
| **PCI DSS** | International | 1-4 | **Datensicherheitsstandard der Zahlungskartenindustrie**. Definiert Sicherheit und Compliance. Gilt für alle Unternehmen, die Kreditkartendaten verarbeiten, übertragen oder speichern. Die Stufen basieren auf dem Transaktionsvolumen. | Wurde von Kreditkartenunternehmen und nicht von der Regierung erstellt. |
| **DPDPA** | Indien | N/A | **Gesetz zum Schutz digitaler personenbezogener Daten**. Legt fest, wie personenbezogene Daten verarbeitet werden dürfen. | Die indische Regierung hat dieses Gesetz 2023 verabschiedet. Es ist zwar mit der **Datenschutz-Grundverordnung** ( **, DSGVO**) vergleichbar, weist jedoch auch einige bemerkenswerte Unterschiede auf. |
| **FedRAMP** | USA | Mäßig, Hoch | **Federal Risk and Authorization Management Program** (Bundesprogramm für Risikomanagement und Autorisierung). Legt die Sicherheits- und Compliance-Anforderungen fest, die für die Bereitstellung von Software und Dienstleistungen für die Bundesregierung gelten. | US-Bundesregierung; unterscheidet sich von der Landesregierung. |
| **HIPAA** | US  | N/A | **Gesetz über die Übertragbarkeit und Rechenschaftspflicht von Krankenversicherungen**. | Ein in den 90er Jahren festgelegter Standard, der mit der Technologie weiterentwickelt werden musste. |
| **DGA** | **Europäische Union** (**EU**) | Nicht zutreffend | **Datenschutzgesetz**. Legt die Politik der EU für die Nutzung und Weitergabe von Daten fest. | Gilt für Daten des öffentlichen Sektors und Datenaltruismus sowie dafür, was geteilt werden darf und was nicht. Schließt Lücken im DSGVO-Standard. |
| **DSGVO** | EU  | N/A | Wie personenbezogene Daten verwendet werden dürfen und wie nicht. | Dies war ein historischer Schritt, der den Umgang mit Daten weltweit radikal verändert hat. |

Tabelle 7.1: Erläuterung der Sicherheits- und Compliance-Rahmenwerke

Obwohl sich die Rahmenwerke geringfügig unterscheiden und unterschiedliche Ziele verfolgen, sind sie im Kern identisch. Die von einer Anwendung erfassten und gespeicherten Daten müssen während der Übertragung und im Ruhezustand gesichert sein und dürfen nur an den vorgesehenen Orten landen, auf die die vorgesehenen Benutzer Zugriff haben. Dies wird teilweise mit RBAC erreicht, aber RBAC allein reicht nicht aus. Sicherheitsstandards wie PCI DSS umfassen eine physische Überprüfung der Hardware, der Server und des Zugriffs auf diese physischen Geräte und deren Unterbringung, damit die Compliance zertifiziert werden kann. Compliance und Sicherheit gehen in der Regel Hand in Hand, sind aber eigentlich zwei unterschiedliche Dinge. Ein System kann sicher sein, aber nicht konform, und umgekehrt. Wir werden hier nicht auf diese Unterschiede eingehen, da sie außerhalb des Rahmens eines IDP liegen, aber es ist wichtig zu verstehen, dass Sicherheit mehr ist als nur das Ankreuzen von Kästchen auf einer Liste. Diese Kästchen sollten Aufschluss darüber geben, wie weit sich die Arbeit der Bedrohungsmodellierung durch das System erstrecken muss und wie Sie die Rolle der Plattform in einer regulierten Branche entwickeln.

Schutz von Vermögenswerten

Entsprechend dem Paradigma des digitalen Raums sind die Vermögenswerte, die wir hier diskutieren, die Daten Ihres Dienstes. Die meisten Sicherheits- und Compliance-Vorschriften konzentrieren sich auf den Umgang mit Daten. Sie sollten dies so verstehen, dass Daten das wertvollste Kapital eines durchschnittlichen Unternehmens sind und als solches geschätzt werden sollten.

Ihre Daten befinden sich in drei Zuständen: Sie sind entweder in Bewegung, in Gebrauch oder ruhen. Daher muss die Sicherheit für sie alle Zustände abdecken. Da die Daten auf der Plattform gespeichert sind, liegt es in der Verantwortung der Plattform, diesen Teil der Sicherheitsstrategie zu übernehmen. Es gibt nur wenige Produkte, bei denen die Daten nicht mit größter Sorgfalt gesichert werden müssen, daher ist es sehr schwierig, bei der Sicherung von Daten zu weit zu gehen.

Sicherung ruhender Daten

Ihre Daten befinden sich die meiste Zeit im Ruhezustand. Das Datendesign und die allgemeine Datenbanksicherheit erfordern besondere Aufmerksamkeit und regelmäßige Überprüfungen, aber die übergeordneten Konzepte für ruhende Daten lassen sich in folgende Kategorien einteilen:

- Klassifizierung
    - Um welche Art von Daten handelt es sich und welche Informationen enthalten sie?
    - Wie wichtig sind sie?
    - Physische Isolierung von Daten aufgrund regulatorischer Anforderungen oder geschäftlicher Bedeutung
    - Die Interaktion der Daten mit dem System kann Aufschluss über die Klassifizierung geben
- Verschlüsselung
    - Verschlüsselung auf jeder Ebene, sowohl physisch als auch digital
- Salts und Hashes
    - Nicht nur zur Verschlüsselung, sondern auch zur Komprimierung
        - Nicht ideal, wenn Sie möchten, dass die Daten für Menschen lesbar bleiben
        - Kann den Speicher enorm belasten und zu einem unbeabsichtigten **Distributed-Denial-of-Service** (**DDOS**) führen
- Eingeschränkter Zugriff
    - Kann je nach Klassifizierung angepasst werden
    - Sollte einen formellen Überprüfungsprozess, Rollen und Verantwortlichkeiten haben
- Redundante Backups
    - Drei ist die magische Zahl für Systeme mit hoher und niedriger Verfügbarkeit
    - Die Redundanz der Daten muss nicht einheitlich sein; die Richtliniengestaltung basiert auf den Kosten eines Datenverlusts
- Richtlinien zur Datenaufbewahrung
    - Wie lange werden die Daten wirklich benötigt? Gibt es diesbezüglich gesetzliche Vorschriften?
        - Wie sieht die **Kontrollkette** für diese Entscheidung aus?
        - Wie bei der Redundanz: Es ist nicht erforderlich, eine einheitliche Richtlinie für alle Daten festzulegen
    - Brauchen Sie sie überhaupt?
        - Hinterfragen Sie jedes einzelne Element:
            - Aufblähung entsteht, wenn Menschen Daten für notwendig halten
            - Unsicherheit führt dazu, dass Menschen mehr verlangen, als sie benötigen
            - Zeigen Sie, wie Daten einen Mehrwert und Verantwortlichkeit schaffen und es später einfacher machen, ihre Verwendung und Kosten zu rechtfertigen:
                - Reduzieren Sie den Umfang ungerechtfertigter Elemente aggressiv
                - Dokumentieren Sie die Entstehungsgeschichte des Systems

Die Einarbeitung neuer Mitarbeiter wird einfacher

Die Beantwortung von Fragen zum System wird einfacher, auch von unfairen Fragen

Die Busnummer verliert an Bedeutung

- - - - - Was spricht aus geschäftlicher Sicht für die Aufbewahrung der Daten?

Bringt es Geld ein?

Spart es Geld?

Können wir daraus lernen?

Ist es das Richtige?

Welchen Risiken setzen wir uns aus, wenn wir es behalten?

- - - - Was ist der operative Anwendungsfall? (z. B.: Fehlerbehebung, Zugriffsprotokolle, Prüfpfade)
- Hot- und Cold-Storage
    - Heißspeicher sind leichter verfügbar
        - Erfordert Zugriffsregeln
    - Kaltlagerung ist nicht ohne Weiteres verfügbar
        - Ältere Daten, die nicht häufig benötigt werden, aber dennoch wichtig sind, werden in den Kalt-Speicher verschoben
        - Schwierigerer Zugriff, in der Regel durch höhere Berechtigungsstufen geschützt

Datenhoheit

Viele Länder führen Gesetze zur Datenhoheit ein, die im Wesentlichen vorschreiben, dass Daten, die von Personen innerhalb der Landesgrenzen erstellt wurden, die physischen Grenzen des Landes, in dem sie erstellt wurden, nicht verlassen dürfen. Das bedeutet nicht immer, dass Daten außerhalb des Landes nicht eingesehen werden können (Daten in Verwendung), sondern dass die Datenspeicherung innerhalb der regionalen Grenzen bleiben muss. Dies betrifft die Compliance-Situation für ruhende Daten, nicht jedoch die Sicherheitssituation.

Sicherung von Daten während der Übertragung

Wenn Daten übertragen werden, werden sie zwischen Microservices übertragen, was bedeutet, dass sie dem Netzwerk der Plattform und/oder externen Endpunkten ausgesetzt sind. Die Daten müssen während der Übertragung verschlüsselt werden, aber letztendlich müssen die Daten verwendet werden, sodass sie irgendwann vom empfangenden Endpunkt entpackt werden:

- Begrenzen Sie, welche Daten wie lange im Speicher gespeichert werden – dies schützt die Integrität der Plattform und die Daten (gehen Sie beim Caching klug vor).
- Übertragen Sie keine Daten über Ports, die weit geöffnet oder privilegiert sind.
- Protokollieren Sie nur absolut notwendige Informationen über die Datentransaktion, nicht die transaktionalen Daten selbst (siehe Protokollbereinigung).
- Schützen Sie sich vor Injektionen, indem Sie Eingaben bereinigen.
- Verwenden Sie Netzwerksicherheit und Best Practices für Kryptografie, um Man-in-the-Middle-Angriffe (**MITM**) und andere Arten von Angriffen zu verhindern.

Daten in Verwendung

Daten in Verwendung sind genau das, wonach es klingt: Daten, die das System anzeigt oder ändert. Wenn sie bereits gespeichert und in Verwendung sind, werden sie entweder aus dem Speicher abgerufen oder zwischengespeichert. Sie können im Speicher gehalten oder unter Verwendung verschiedener Lese- und Caching-Technologien direkt gelesen werden. Daten sind auch dann in Gebrauch, wenn sie zum ersten Mal in ein System eingegeben werden. Dazu gehören die Registrierung neuer Benutzer oder die Speicherung einer neuen Protokollzeile. Oftmals werden Daten in diesem Zustand auch einer Datenumwandlung unterzogen, z. B. Aggregationen oder Bereinigungsvorgängen, die sicherstellen, dass die Daten nicht für einen Injektionsangriff oder sogar für eine Löschung verwendet werden können. Die Sicherung von Daten in Gebrauch ist nur eine weitere Anwendung derselben Prinzipien, die wir auch für Daten in Bewegung oder im Ruhezustand verwenden.

Sichern Ihres Netzwerks

Kubernetes hat eine steckbare Architektur und wird zwar ohne Netzwerkstack ausgeliefert, aber einige Kubernetes-Plattformoptionen haben ihre eigenen Standardeinstellungen. Beispielsweise hat die OpenShift Container Platform eine **Standard-Container-Netzwerkschnittstelle** (**CNI**) namens **Open Virtual Network** (**OVN**) übernommen. Neben OVN gibt es noch andere sichere und besser beobachtbare Lösungen für Kubernetes-Netzwerke.

**Cilium** ist ein Beispiel für dieses sicherere Netzwerk. Es verwendet **eBPF**, eine Technologie auf Linux-Kernel-Ebene, mit der Kernel-Funktionen von Programmen genutzt werden können, die in einem privilegierten Kontext ausgeführt werden, ohne dass Änderungen am Kernel oder ein Kernel-Modul geladen werden müssen. Durch die Verwendung von eBPF schafft Cilium ein hochsicheres, beobachtbares und leistungsfähiges Netzwerk für Kubernetes-Umgebungen. Cilium bringt diese Funktionen auf Kernel-Ebene in die Netzwerkschicht von Kubernetes ein. Die Website des Cilium-Projekts (https://cilium.io/) enthält zahlreiche praktische Tutorials und Übungen, um sich mit der Technologie vertraut zu machen, und ist Eigentum der **Cloud Native Computing Foundation** (**CNCF**).

Neben der Netzwerktechnologie spielt auch die Netzwerktopologie eine wichtige Rolle für die Netzwerksicherheit. Netzwerktools wie Firewalls, VPNs, VLANs, Router, Switches usw. befinden sich möglicherweise nicht auf dem Kubernetes-Cluster, spielen aber eine sehr wichtige Rolle für die Sicherheit des Clusters. Unabhängig davon, wie die endgültige Netzwerktopologie aussieht und wie der Cluster mit dem öffentlichen Internet interagiert (oder vielleicht auch nicht!), müssen Sie für eine ordnungsgemäße Bedrohungsmodellierung und Compliance in der Lage sein, Ihr Netzwerk zu beobachten und zu dokumentieren.

Isolation zwischen Vorproduktions- und Produktionsumgebungen

Eine allgemeine Best Practice besteht darin, dass Ihr System unabhängig von Sicherheits- und Compliance-Anforderungen Produktionsdaten und den Zugriff darauf von anderen Umgebungen isoliert, um den Schutz der Daten zu gewährleisten. Daten sind das wertvollste Kapital der meisten Unternehmen. Daher ist der Schutz und die Isolierung von Daten der beste Weg, um dieses Kapital zu sichern und eine angemessene Sicherheit und Compliance für alle Unternehmen zu gewährleisten. Der Schutz von Daten ist das Herzstück von Sicherheit und Compliance. Produktionsdaten sollten niemals die Produktionsumgebung verlassen, und der Zugriff auf diese Daten muss streng kontrolliert werden, um sicherzustellen, dass keine böswilligen Akteure – intern, extern, absichtlich oder versehentlich – Zugriff auf diese Produktionsdaten erhalten. Beziehen wir uns noch einmal auf unsere Plattformarchitektur aus [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2):

Abbildung 7.3: Referenzkomponenten der Plattform

Jede weiße Box, auch die sicherheitsrelevanten Boxen, muss über eigene Sicherheitskontrollen verfügen. Die Möglichkeit, RBAC für die Organisation zu verwalten, darf beispielsweise nicht für jedermann zugänglich sein. Es ist leicht zu erkennen, wie dies schnell zu einem Problem werden kann, das ein ganzes Fachgebiet von Experten hervorgebracht hat. Wir wollen in diesem Buch nicht versuchen, deren Wissen und Fachkenntnisse zu ersetzen, sondern Ihnen einige der unserer Meinung nach wichtigsten Aspekte der Sicherheit für ein IDP vorstellen, damit Sie den richtigen Weg einschlagen können.

Ein einfacher Gewinn für jede Organisation besteht darin, die Staging-, Entwicklungs- und Produktionsumgebungen vollständig voneinander zu isolieren. Dazu gehört, dass separate Datenbanken mit unterschiedlichen Zugriffsregeln verwendet werden, anstatt eine einzige Datenbank mit verschiedenen Tabellen und unterschiedlichen Zugriffsregeln.

Es ist möglich, einen einzigen Cluster zu verwenden und netzwerkrichtlinienbasierte Trennungen sowie RBAC für ganz bestimmte Namespaces einzurichten, um eine ähnliche Isolierung zu erreichen, wie Sie sie mit mehreren Clustern erzielen würden. Allerdings stellen der API-Server, die Audit-Protokolle, etcd, das Netzwerk und andere clusterbezogene Ressourcen des Clusters weiterhin einen einzigen potenziellen Schwachpunkt für diese Isolierung dar.

Aus Sicherheits- und Compliance-Gründen ist es daher am besten, die Umgebungen vollständig zu trennen. Durch zwei getrennte Cluster ist die Isolierung der Produktionsdaten gewährleistet und es gibt weniger Spielraum für menschliche Fehler, die diese Sicherheit beeinträchtigen könnten. Darüber hinaus können Sie auch unterschiedliche Netzwerkkonfigurationen verwenden, z. B. Firewall-Regeln mit unterschiedlichen Berechtigungen oder sogar Umgebungen, die vollständig vom öffentlichen Internet getrennt sind.

Verwaltung von Geheimnissen und Tokens

In Kubernetes ist ein Geheimnis ein Passwort, ein Authentifizierungstoken, eine Umgebungsvariable, ein API-Schlüssel oder ähnliche sensible Daten, auf die eine Anwendung möglicherweise zugreifen muss, um korrekt zu funktionieren oder eine Aufgabe auszuführen. Die Verwaltung von Geheimnissen wird zu einer der wichtigsten Herausforderungen, die es zu lösen gilt, wenn man an einem System arbeitet, das so stark auf Automatisierung angewiesen ist wie ein IDP. Glücklicherweise gibt es Muster und Technologien, die dabei helfen sollen.

Als Kubernetes-basierte Plattform sind die integrierten Kubernetes-Funktionen für die Geheimhaltungs-Sicherheit der wichtigste Ausgangspunkt. Es ist wichtig zu wissen, dass das Standardverhalten nicht sicher ist. Geheimnisse werden ähnlich wie ConfigMaps gespeichert und sind nicht verschlüsselt. Sie sind zwar codiert, aber die Codierung ist nur Base64. Das ist für Entwicklungsumgebungen in Ordnung, für Produktionsumgebungen jedoch nicht so gut geeignet. Sie können jedoch geheime Daten im Ruhezustand verschlüsseln, ohne Anwendungen von Drittanbietern installieren zu müssen.

Weitere Informationen zur Verschlüsselung im Ruhezustand und einige Beispiele, die für einen Testcluster verwendet werden könnten, finden Sie im Abschnitt „Datenverschlüsselung“ der Kubernetes-Dokumentation: https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/.

Die Verwaltung geheimer Daten ist oft sehr umfangreich, und sobald Sie über mehr als einen Cluster oder mehr als eine Umgebung verfügen, wird es schwierig, alle geheimen Daten zu verwalten, die der IDP zur Unterstützung von Anwendungen benötigt. Daher ist die Verwendung von Software zur Speicherung geheimer Daten wie HashiCorp's Vault oder Passwort-Managern wie Bitwarden oder 1Password zum Industriestandard geworden. Eine bewährte Standardmethode für die automatische Speicherung von Geheimnissen in einem Cluster besteht darin, einen Verweis auf das Geheimnis in einem Code zu speichern und dann eine Logik zu verwenden, die weiß, wie das Geheimnis anhand seines Verweises gesucht und für die Anwendung abgerufen werden kann. Ein gängiges Muster für Anwendungen, die geheime Informationen über Verweise abrufen, ist daher die Verwendung eines Sidecar-Modells.

In einem Sidecar-Modell hat einer der Container im Pod die spezifische Aufgabe, Geheimnisse abzurufen und für die Verwendung durch den Hauptanwendungscontainer beim Start des Pods verfügbar zu machen. Die Geheimnisse werden dann in einem Speichervolumen abgelegt und von der Anwendung gelesen, wenn sie benötigt werden.

Ein Sidecar-Modell würde wie folgt aussehen, wobei der Pod sowohl die Anwendung als auch den Sidecar enthält:

Abbildung 7.4: Container-Sidecar-Modell

Sofern jedoch der Sidecar (oder ein anderer Dienst), der die Suche durchführt, nicht in einer Schleife läuft, wird dieses Problem nur einmal gelöst und es werden keine Umgebungen berücksichtigt, in denen sich Geheimnisse regelmäßig ändern können. Hier sind FOSS-Lösungen eine hervorragende Option. Der **External Secrets Operator** (**ESO**) ist ein FOSS-Angebot, das dies ermöglicht. Das Projekt ist Eigentum der Linux Foundation. Eine vollständige Übersicht über die Funktionsweise finden Sie unter [external-secrets.io](http://external-secrets.io/).

Das Referenzarchitekturdiagramm sieht wie folgt aus und entspricht weitgehend unserer Sidecar-Referenz:

Abbildung 7.5: Referenzarchitektur für ESO

Im Wesentlichen werden Geheimnisse in einem Passwortspeicher außerhalb des Clusters gespeichert, auf den der Operator dann zugreifen kann. Die Geheimnisreferenzen existieren als **benutzerdefinierte Ressourcen** (**CRs**), die der Operator interpretieren und abrufen kann. Wenn sich das Geheimnis ändert, wird das neue Geheimnis automatisch vom Operator auf den Cluster angewendet, sodass es immer nur eine einzige **Quelle der Wahrheit** (**SOT**) für Geheimnisse im IDP gibt.

Natürlich muss das Authentifizierungsgeheimnis für den Speicher zunächst bereitgestellt werden, damit der Betreiber arbeiten kann. Dies kann zu einer Art Zwickmühle führen, da derjenige, der diesen Betreiber einrichtet, in der Lage sein muss, ihm die Anmeldedaten für den Zugriff auf den geheimen Speicher außerhalb des Clusters zur Verfügung zu stellen.

ESO ist besonders nützlich in stark regulierten Umgebungen, in denen die Inhalte von Geheimnissen, wie Zertifikate und Token, häufig rotiert werden. Dadurch kann die Rotation an der Quelle erfolgen, wird aber automatisch auf die erforderlichen Umgebungen übertragen.

ESO ist nicht das einzige Open-Source-Projekt für die Geheimnisverwaltung in einem Cluster; es gibt mehrere andere, die in der CNCF inkubiert werden, und alle sind eine Überprüfung wert. Die Auswahl des richtigen Tools für Ihr Unternehmen muss nach Abwägung einer Liste von Vor- und Nachteilen erfolgen, aber das von diesen Tools genutzte Muster stellt die beste Vorgehensweise dar, die Sie nachahmen sollten.

Bereinigung von Protokollen

Alle von der Plattform generierten Protokolle sollten bereinigt werden. Dies gilt auch für Anwendungen, überschreitet jedoch die Grenzen der Plattform. Protokolle sind Teil der Daten und daher Vermögenswerte, die die Sicherheit der Plattform schützen muss. Zusätzlich zu den zuvor behandelten Themen Speicherung und Übertragung ist die Datenbereinigung ein wichtiger Bestandteil, um sicherzustellen, dass selbst wenn ein Angreifer Zugriff auf Protokolldaten erhält, er diese nicht dazu verwenden kann, das System weiter zu kompromittieren. Tools zur Überprüfung der Codequalität wie SonarQube (https://docs.sonarsource.com/sonarqube/latest/) eignen sich hervorragend, um sensible Daten zu erkennen, die an den falschen Ort gelangen, sodass das Problem behoben werden kann, bevor es zu einem Sicherheitsvorfall kommt.

In bereinigten Protokollen werden Passwörter oder Tokens aus dem Textkörper entfernt. Wenn beispielsweise Anfragen an eine API protokolliert werden, könnte die Art und Weise, wie die Anfrage authentifiziert wurde (z. B. Bearer-Token), protokolliert werden, aber das eigentliche Token selbst muss entfernt werden. Wenn sensible Daten erfasst oder gespeichert werden, sollten sie gesalzen und gehasht werden.

Diese Plattformprotokolle sollten außerdem so weit wie möglich frei von **personenbezogenen Daten** (**PII**) sein. Diese Art von Daten wird in der Regel nicht benötigt, sodass ihre Speicherung ein unnötiges Risiko darstellt.

Die Bereinigung von Protokollen umfasst auch Aufbewahrungsrichtlinien. Genauso wie Anwendungsdaten nach Ablauf ihrer **Lebensdauer** (**TTL**) entsorgt werden sollten, gilt dies auch für Protokolldaten. Mit fortschreitender Laufzeit der Plattform verlieren Protokolle für das Plattformteam zunehmend an Nutzen, aber die darin enthaltenen Informationen können ihren Wert behalten, wenn personenbezogene Daten aufgrund geschäftlicher Erfordernisse nicht entfernt werden können. Daher stellt die Aufbewahrung von Daten, die für Kriminelle von Wert sind, ein unnötiges Risiko dar, das selbst durch die Verwendung von Cold Storage nicht gemindert werden kann. Wann Daten vernichtet werden, ist letztlich eine geschäftliche Entscheidung, und es könnte eine Datenumwandlung vorgenommen werden, um die Daten weiter zu anonymisieren, sodass nur die personenbezogenen Daten vernichtet werden, wenn es einen zwingenden Grund gibt, die Plattformmetriken für immer aufzubewahren.

Sicherer Zugriff

Wir haben RBAC bereits einige Male behandelt. Es wird ausdrücklich als eines der OWASP Top Ten genannt, daher ist es für die Sicherheitslage eines Unternehmens eindeutig wichtig, dass die Zugriffskontrollen korrekt sind. Eine Methode, um dies sicherzustellen, ist die Erstellung von Dienstkonten. Diese Konten sind nicht-menschliche Identitätskonten, die von Workloads auf dem System genutzt werden können. Genau wie bei einem Menschen erfordert die Authentifizierung eines Dienstkontos ein Token, das regelmäßig ausgetauscht werden sollte. Durch die Aufteilung der Zugriffstypen in menschliche und nicht-menschliche können Sie das **Prinzip der geringsten Privilegien** (**PoLP**) nutzen, um sicherzustellen, dass ein Mensch oder eine Workload über die erforderlichen Berechtigungen verfügt, aber keine Berechtigungen, die er nicht benötigt.

Das Prinzip der geringsten Privilegien sollte nicht nur für Workloads gelten, sondern auch für Menschen. Bei der Bewertung der Berechtigungen, über die Benutzer verfügen sollten, sind einige Dinge hinsichtlich ihres Zugriffs zu beachten. Als Nächstes definieren wir einige allgemeine Best Practices, die Sie untersuchen sollten:

- Einzelbenutzer, Multi-RBAC:
    - Der Benutzer hat unabhängige RBAC-Rollen für Staging und Produktion.
    - Die Staging-Umgebung sollte mit der Produktionsumgebung übereinstimmen, damit der Benutzer durch die in einer Umgebung durchgeführten Aktionen darauf vorbereitet ist, dasselbe in der anderen Umgebung zu tun.
    - Es können Notfallverfahren vorhanden sein, um höhere Zugriffsebenen zu erhalten. Dieser Zugriff muss, falls vorhanden, überprüfbar sein, d. h. alle Fakten dazu müssen protokolliert werden.
- GitOps für Sicherheit:
    - Kann RBAC verwalten.
    - Reduziert die Notwendigkeit, direkten Zugriff auf den Cluster zu gewähren.
    - Wird zu einem SPOF.
    - Konzentriert sich auf die Sicherheit.

Audit-Protokolle

Was ist ein Audit-Protokoll? Ein Audit-Protokoll ist eine Aufzeichnung der Aktionen, die der Kubernetes-API-Server sieht. Das bedeutet, dass jede Änderung im Kubernetes-Cluster, sowohl automatisierte als auch von Menschen initiierte, von Anmeldungen bis zur Pod-Planung, in Audit-Protokollen verfolgt wird. Wenn es identifizierende Informationen gibt, werden diese in Ihren Audit-Protokollen gespeichert. Der Grund dafür ist, dass es für die Behebung von Vorfällen und **die Reaktion auf Sicherheitsvorfälle** (**IR**) entscheidend ist, zu wissen, wer welche Aktion wann und wo durchgeführt hat. Audit-Protokolle sollten nicht nur die API-Anfrage enthalten, sondern auch die Nutzlast, falls vorhanden – wie es bei Methoden wie PUT oder PATCH zu erwarten ist. Anmeldedaten sollten nicht als personenbezogene Daten protokolliert werden und in den meisten Fällen weggelassen werden.

Die Nutzung von Audit-Protokollen zur Ermittlung anomaler Verhaltensweisen kann mit einigen grundlegenden Observability-Implementierungen und entsprechenden Warnmeldungen erfolgen. Bei der Definition der Plattform sollten Sie User Stories und kritische User Journeys erstellt haben. In diesen Übungen haben Sie sich angesehen, was Ihre Benutzer tun werden und womit sie Erfolg haben werden. Aber haben Sie sich angesehen, was Ihre Benutzer nicht tun würden oder nicht tun sollten und womit sie Erfolg haben würden?

Verhaltensweisen, die in Audit-Protokollen gefunden werden und den Normen der Plattformnutzer widersprechen, sind der einfachste Weg, um Warnmeldungen zu potenziellen Anomalien zu definieren. Ein Beispiel hierfür wäre eine sehr hohe Anzahl von 403-Fehlern oder eine erhebliche Anzahl von Anfragen von einer IP-Adresse außerhalb eines bestimmten CIDR-Bereichs (**Classless Inter-Domain Routing**).

Weitere Elemente, nach denen die automatische Erkennung suchen könnte, sind unter anderem die folgenden:

- Erkennung ungewöhnlicher oder ungültiger User Agents oder Bots
- Mehrere Benutzeranmeldungen oder Sitzungen von verschiedenen Standorten aus

Im Allgemeinen sollten Ereignisse, die gegen bekannte Normen verstoßen, automatisch von Menschen überprüft werden. Die meisten davon erfordern jedoch nach wie vor eine manuelle Überprüfung, da sie nicht immer auf einen Sicherheitsvorfall hindeuten. Sie können auf ein Softwareproblem oder ein Ereignis hinweisen, das zwar notwendig ist, bei der Konzeption der Warnmeldungen jedoch nicht berücksichtigt wurde. Warnmeldungen sollten nicht zu laut werden. Falsche Signale können Schaden anrichten, insbesondere wenn sie Ihr Team mitten in der Nacht alarmieren. Wenn falsche Signale zu häufig ausgelöst werden, werden sie möglicherweise bald von den Ingenieuren ignoriert, die ihre kognitive Belastung gering halten möchten.

Wir haben bisher die Grundlagen der Sicherheit behandelt und haben noch einen langen Weg vor uns. Nachdem wir nun einige allgemeine Themen kennengelernt haben, wollen wir uns nun mit spezifischeren Themen befassen.

Ein Blick auf SBOM-Praktiken

Open-Source-Tools, Bibliotheken innerhalb von Programmiersprachen, Paketmanager und Container-Images sind die Bausteine moderner Anwendungen und bringen eine Reihe einzigartiger Herausforderungen mit sich, wenn es um die Sicherheit Ihrer **Software-Lieferkette** geht. Dies bezeichnen wir liebevoll als das Dilemma der Lieferkettensicherheit. Wie können Sie eine gute Sicherheitslage aufrechterhalten, wenn Sie nicht den gesamten Code besitzen, der gesichert werden muss?

Wenn wir die Lieferkette visuell darstellen, gibt es einige unbekannte Personen (wir nennen sie Akteure), die zu einer Open-Source-Abhängigkeit beitragen, und einen weiteren, wahrscheinlich bekannten Akteur, der direkter zu Ihrer Codebasis beiträgt. Dies ist eine extrem vereinfachte Darstellung (hier fehlen wahrscheinlich 10 Kästchen), aber sie sollte Ihnen helfen, den Punkt zu verstehen:

Abbildung 7.6: Beispiel für eine Lieferkette

Ihre Software-Lieferkette umfasst alles und jeden, der an der Veröffentlichung Ihrer App beteiligt ist. Wenn wir uns mit der Aufrechterhaltung der Sicherheit befassen, müssen wir unsere Anwendung und Infrastruktur-Topologie aufschlüsseln. Eine SBOM ist ein wichtiges Werkzeug zur Verfolgung und Verwaltung der Risiken eines Projekts.

Nachdem die US-Regierung 2021 eine Durchführungsverordnung erlassen hatte, wurden diese Dokumente für viele Unternehmen verbindlich. Die wesentliche Voraussetzung ist, dass ein Unternehmen weiß, wovon die von ihm entwickelte Software abhängt und woher diese Abhängigkeiten stammen. Eine SBOM wird zu dem Zeitpunkt erstellt, zu dem eine Software und alle ihre Abhängigkeiten für die Veröffentlichung gebündelt werden. Obwohl sie nicht für jedes Unternehmen zwingend erforderlich sind, stellen sie eine bewährte Vorgehensweise dar, da sie in Verbindung mit einem Scan-Tool bei Audits helfen und dabei unterstützen können, das Ausmaß eines Risikos zu verstehen, wenn erneut eine Day-0-Sicherheitslücke wie Heartbleed oder Log4j gefunden wird.

Eine SBOM wird in der Regel zum Zeitpunkt der Erstellung in der CI-Pipeline generiert. **Syft** ist ein weit verbreitetes Tool zur SBOM-Generierung und wird häufig mit dem Scanner **Grype** kombiniert, da es sich bei beiden um kostenlose Open-Source-Tools von Anchore handelt. Das Open Source Program Office von Cisco hat kürzlich ebenfalls ein SBOM-Tool namens **KubeClarity** (https://github.com/openclarity/kubeclarity) veröffentlicht, das mehrere SBOM- und Scanner-Tools gemeinsam nutzen kann, um ein möglichst vollständiges Bild der Software und ihrer Risikofläche zu liefern.

SBOM-Generierungstools sind noch relativ neu und daher noch nicht perfekt. Es ist möglich, dass ein Tool ein Paket übersieht, das das andere Tool erkennt, und umgekehrt. Um Ihre Sicherheitslage zu verstehen, ist weniger nicht mehr, daher ist es für die Sicherheit am wichtigsten, sich ein möglichst vollständiges Bild zu verschaffen.

Verwendung einer SBOM

Eine SBOM ist mehr als nur ein Häkchen auf einer Liste von Anforderungen eines Kunden oder der US-Regierung. Sie ist auch ein wirksames Tool zur Erkennung und Behebung von Schwachstellen. In Abbildung 7.6 zeigen wir, wie Ihre Anwendung wahrscheinlich Code und damit Schwachstellen aus Abhängigkeiten und Bibliotheken übernimmt, die sie möglicherweise nutzt und die Open Source sind. Diese Abhängigkeiten sind schwer nachzuverfolgen, weshalb eine SBOM als Hauptbuch für Ihr System dienen kann. Das bedeutet, dass Sie, wenn später eine erhebliche Sicherheitslücke bekannt gegeben wird, diese Meldung schnell mit Ihrer SBOM abgleichen und zeitnah erkennen können, ob Ihre Software anfällig ist. Dies kann durch einen Blick auf einen bereits erstellten Bericht oder durch einfaches erneutes Ausführen des Berichts erfolgen. Wenn die Erstellung Ihres „ ”-Berichts mit einem Scan gekoppelt ist, sollte das Scan-Tool die neue Sicherheitslücke erkennen, sobald sie in das Register für kritische Sicherheitslücken aufgenommen wurde.

Erstellen einer SBOM für ein GitHub-Repo

Eine einfache Möglichkeit, eine SBOM für ein GitHub-Repo anzuzeigen, besteht darin, die GitHub-API für das Repo, das Sie untersuchen möchten, zu curlen. Um ein kurzes Beispiel zu geben, werden wir Ihnen zeigen, wie Sie dies tun und wie Sie die Ergebnisse interpretieren können.

GitHub-SBOMs liegen in einem Format namens SPDX vor. Weitere Informationen zu diesem Format finden Sie hier: https://spdx.github.io/spdx-spec/v2.3/introduction/.

Um eine SBOM abzurufen, verwenden Sie den folgenden Code-Block in Ihrem Terminal, um die GitHub-API abzurufen. Sie müssen sich dafür nicht authentifizieren, können dies aber tun. Ersetzen Sie die Variablen $REPOSITORY und $OWNER durch das gewünschte Repository. Als Beispiel betrachten wir das CNCF-Repository „tag-security“:

curl -L \\

\-H "Accept: application/vnd.github+json" \\

\-H "X-GitHub-Api-Version: 2022-11-28" \\

https://api.github.com/repos/$OWNER/$REPOSITORY/dependency-graph/sbom

KopierenErklären

Die JSON-Rückgabe ist etwas lang, daher sehen wir uns nur einen Ausschnitt aus der SBOM an, die wir von curling erhalten haben (https://api.github.com/repos/cncf/tag-security/dependency-graph/sbom):

{

&nbsp; „sbom”: {

&nbsp;   "SPDXID": "SPDXRef-DOCUMENT",

&nbsp;   "spdxVersion": "SPDX-2.3",

&nbsp;   "creationInfo": {

&nbsp;     „created”: „2024-08-16T05:37:53Z”,

&nbsp;     „creators”: \[

&nbsp;       „Tool: GitHub.com-Dependency-Graph“

&nbsp;     \]

&nbsp;   },

&nbsp;   „name“: „com.github.cncf/tag-security“,

&nbsp;   „dataLicense“: „CC0-1.0“,

&nbsp;   „documentDescribes”: \[

&nbsp;     „SPDXRef-com.[github.cncf-tag-security”](https://github.com/cncf/tag-security/dependency_graph/sbom-0a6b74785f7954ee)

&nbsp;   [\],](https://github.com/cncf/tag-security/dependency_graph/sbom-0a6b74785f7954ee)

&nbsp;   [„documentNamespace“:](https://github.com/cncf/tag-security/dependency_graph/sbom-0a6b74785f7954ee) https://github.com/cncf/tag-security/dependency_graph/sbom-0a6b74785f7954ee,

CopyExplain

Am Anfang der Ausgabe finden Sie einige grundlegende Informationen zur SBOM, darunter, wie sie erstellt wurde, wann und relevante Datenlizenzen. Hier erhalten Sie einen Überblick über das Repository, das Sie analysiert haben. Der nächste Abschnitt betrifft Pakete und enthält alle darin enthaltenen Softwareabhängigkeiten und deren Beziehungen:

&nbsp;   „packages”: \[

&nbsp;     {

&nbsp;       „SPDXID”: „SPDXRef-npm-babel-helper-validator-identifier-7.22.20”,

&nbsp;       „name”: „npm:@babel/helper-validator-identifier”,

&nbsp;       „versionInfo“: „7.22.20“,

&nbsp;       „downloadLocation“: „NOASSERTION“,

&nbsp;       „filesAnalyzed”: false,

&nbsp;       „licenseConcluded“: „MIT“,

&nbsp;       „supplier“: „NOASSERTION“,

&nbsp;       „externeReferenzen“: \[

&nbsp;         {

&nbsp;           „referenceCategory“: „PACKAGE-MANAGER“,

&nbsp;           „referenceLocator“: „pkg:npm/%40babel/helper-validator-identifier@7.22.20“,

&nbsp;           „referenceType“: „purl“

&nbsp;         }

&nbsp;       \],

&nbsp;       „copyrightText“: „Copyright (c) 2014-heute Sebastian McKenzie und andere Mitwirkende“

&nbsp;     },

CopyExplain

Wenn Sie sich nur eines der Pakete in der SBOM ansehen, erhalten Sie die Paketinformationen, die verwendete Version sowie Lizenz- und Copyright-Informationen. Die MIT-Lizenz bedeutet, dass das Paket Open Source ist, aber die Copyright-Informationen geben an, wer das Paket gepflegt hat, und verhindern im Wesentlichen, dass der Name dieses Pakets von einem anderen Softwareprojekt verwendet wird. IBM erklärt den Grund für das Copyright hier: https://www.ibm.com/topics/open-source. Ebenfalls in der Ausgabe enthalten sind der Label-Anbieter und der Download-Speicherort. Für diese beiden Felder in diesem Beispiel finden Sie in den Metadaten den Vermerk NOASSERTION. Wie in der SPDX-Dokumentation (https://spdx.github.io/spdx-spec/v2.3/package-information/) erläutert, sollte dies unter den folgenden Umständen verwendet werden:

- Der Ersteller des SPDX-Dokuments hat versucht, eine vernünftige objektive Entscheidung zu treffen, konnte jedoch keine treffen.
- Der Ersteller des SPDX-Dokuments hat keinen Versuch unternommen, dieses Feld zu bestimmen.
- Der Ersteller des SPDX-Dokuments hat absichtlich keine Informationen bereitgestellt (dies sollte keine Bedeutung haben).

Bei anderen Paketen können diese Felder zusätzliche Daten zum Paket enthalten oder auch keine Angaben enthalten. Nach der Liste der Pakete folgen in derselben Reihenfolge die Beziehungen der Pakete zum Repository:

&nbsp;   „Beziehungen”: \[

&nbsp;     {

&nbsp;       „relationshipType”: „DEPENDS_ON”,

&nbsp;       „spdxElementId”: „SPDXRef-com.github.cncf-tag-security”,

&nbsp;       „relatedSpdxElement”: „SPDXRef-npm-babel-helper-validator-identifier-7.22.20”

KopierenErklären

In diesem Beispiel ist dies ziemlich einfach, da es besagt, dass das primäre Element, das Tag-Sicherheits-Repo, vom Paket npm:@babel/helper-validator-identifier in der Version 7.22.20 abhängt. Zusätzliche Metadaten könnten vom SBOM-Ersteller bereitgestellt werden, wurden in diesem Fall jedoch nicht angegeben. Weitere Informationen zu diesen Beziehungen finden Sie hier: https://spdx.github.io/spdx-spec/v2.3/relationships-between-SPDX-elements/#111-relationship-field.

Auch hier gilt: Eine SBOM ist ein recht einfaches Tool; sie erstellt ein Verzeichnis, das auflistet, woraus eine Anwendung oder Codebasis besteht. Für sich genommen leistet sie nicht viel, aber als Teil einer Toolchain trägt sie wesentlich dazu bei, Ihre Systeme und die Risikofläche für Schwachstellen, die ihre Abhängigkeiten mit sich bringen, zu verstehen.

Sicherheitslücken im Blick behalten

Software-Schwachstellen werden in der Regel als **Common Vulnerabilities and Exposures** (**CVE**) bezeichnet. Das **US-Heimatschutzministerium** (**DHS**) unterhält ein öffentliches CVE-Register ([https://www.cve.org](https://www.cve.org/)), in dem Sie sich über bekannte Schwachstellen auf dem Laufenden halten können. Dieses Register kann mit Ihrer Software und Ihren Anwendungen abgeglichen werden, um zu überprüfen, ob bekannte CVEs und Schwachstellen in Ihrer Umgebung vorhanden sind ( ). Ein Plattformteam kann zwar einen maßgeschneiderten Dienst entwickeln, um festzustellen, ob es CVEs in den Systemen gibt, dies ist jedoch nicht erforderlich, da es zahlreiche FOSS-Tools gibt, die diese Aufgabe für Sie übernehmen.

Sie können CVEs in GitHub wie folgt überprüfen:

- **Dependabot**, ein GitHub-Bot, der Ihr Repository scannt und Pull-Anfragen generiert, um CVEs proaktiv zu beheben, indem er Pakete auf bekannte sichere Versionen aktualisiert.
- **Snyk**, das Pull-Anfragen validiert, um sicherzustellen, dass sie keine neuen Schwachstellen einführen
- **CodeQL**, ähnlich wie Snyk, bewertet den Inhalt von Pull-Anfragen, um sicherzustellen, dass sie keine Schwachstellen einführen.

Um Schwachstellen während der Laufzeit im Blick zu behalten, hilft Ihnen das regelmäßige Scannen einer Image-Registry wie Harbor oder eines Tools wie Trivy, das auf Ihre kritischsten Umgebungen abzielt (mindestens), dabei, den Überblick über Schwachstellen in Ihrer Umgebung zu behalten.

Da die SBOM-Generierung und die Erkennung von Schwachstellen in der Regel Teil einer CI-Pipeline sind, wollen wir uns nun mit dem Rest der Pipeline befassen und erläutern, wie Sie die Sicherheit in Ihrem CI/CD-Prozess gewährleisten können.

Pipeline-Sicherheit verstehen – was Sie beachten müssen, um Ihre CI/CD-Pipelines zu sichern

Angenommen, das Plattformteam hat Einfluss oder Zuständigkeit für GitHub oder andere vom Unternehmen genutzte Repositorys zur Quellcodeverwaltung, dann wird die Sicherheit der CI/CD-Pipelines von Anfang bis Ende zu einem wichtigen Bestandteil der IDP-Sicherheitsstrategie.

Sichern Sie Ihr Repository

Die Sicherheit des Code-Repositorys ist ein hervorragendes Beispiel für „Security to the Left“. Durch die frühzeitige Durchsetzung von Sicherheitsnormen und deren Integration in die Arbeitsweise eines Projekts kann ein Unternehmen Probleme im weiteren Verlauf verhindern. Ein gesichertes Repository nutzt mehrere Best Practices:

- **Hauptzweige schreibgeschützt machen**
    - Sie können private Git-Repositorys und selbst gehostetes Git verwenden, wenn Sie zusätzliche Sicherheit benötigen.
- **Signierte Commits erfordern**
    - Dadurch wird die Identität des Autors des Commits überprüft
- **Webhooks vor dem Commit**
    - Wird verwendet, um zu überprüfen, dass keine Geheimnisse versehentlich committet werden
- **Obligatorische Peer-Review**
    - Einschließlich Signoff durch Code-Eigentümer
- **Automatisierte Validierung von Pull-Anfragen**
    - Sicherheitsscans für Abhängigkeiten
    - Tests – sollten die Validierung der Sicherheit und des Zugriffs umfassen
- **Kontinuierliches Scannen**
    - Scans auf versehentliche Commits von Passwörtern, Tokens oder anderen geheimen Daten

Diese Liste ist keineswegs vollständig, sollte jedoch jedem Unternehmen einen guten Ausgangspunkt bieten, um seinen Quellcode vor böswilligen Akteuren und menschlichen Fehlern zu schützen.

Sicherheit von GitOps

GitOps wurde in [Kapitel 5](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/5) ausführlich behandelt, daher werden wir es aufgrund seiner Bedeutung für die Plattformsicherheit nur kurz wiederholen. GitOps wird grob definiert als ein automatisierter Prozess, der das SOT (Git oder eine andere Versionskontrolle) validiert, das den gewünschten Zustand und die Übereinstimmung mit dem tatsächlichen Zustand definiert. Dies geschieht durch einmalige Bereitstellungen oder Änderungen, aber auch durch eine automatisierte Abgleichschleife, die aktiv nach Änderungen im gewünschten Zustand sucht und auf den tatsächlichen Zustand reagiert, um ihn anzupassen, oder eine Änderung im tatsächlichen Zustand erkennt und Änderungen am System vornimmt, um es wieder in den gewünschten Zustand zu versetzen. Das derzeit größte Open-Source-GitOps-Projekt ist Argo CD, ein CD-Tool, das Eigentum der CNCF ist. Innerhalb von Argo CD und anderen GitOps-Paradigmen gibt es einige Best Practices, die zu beachten sind, um eine sicherere Umgebung zu gewährleisten.

Für GitOps gibt es zwei Modelle zur Weitergabe von Änderungen: das Push-Modell und das Pull-Modell. In einem Push-Modell empfängt das GitOps-System Änderungen als Pushes an seinen API-Endpunkt. Es versteht sich von selbst, dass diese Pushes ordnungsgemäß authentifiziert sein sollten, aber wir weisen dennoch darauf hin, um Verwirrung zu vermeiden. Nach dem Empfang des Pushs verarbeitet das GitOps-System die Änderungen und ergreift dann Maßnahmen. Diese Maßnahme besteht wahrscheinlich darin, neue Softwarepakete in die Produktion zu überführen, kann aber auch Konfigurationsänderungen umfassen. Die Quelle des Pushs wird bei diesem Modell jedoch in der Regel nicht validiert, und Argo CD verfügt über keine Konfiguration, um dies zu überprüfen. Dies schafft einen Angriffsvektor, denn wenn die Anmeldedaten kompromittiert werden, kann ein Angreifer Änderungen über das CD-System übertragen, wodurch zusätzliche Einstiegspunkte entstehen können.

Eine Pull-Methode ist genau das Gegenteil. Das GitOps-System kontaktiert das SOT unter Verwendung seiner Authentifizierung und liest dann die Änderungen vom Endpunkt ein. Da es sich um eine bekannte sichere Quelle handelt, gilt die Anwendung dieser Änderungen durch Automatisierung als sichere Maßnahme. Das bedeutet jedoch nicht, dass ein Pull-Modell risikofrei ist. Sowohl Push- als auch Pull-Modelle können MITM-Angriffen ausgesetzt sein, aber in einem ordnungsgemäß gesicherten Netzwerk mit den richtigen kryptografischen Implementierungen sollten diese Risiken erheblich begrenzt sein.

Wenn Ihr GitOps-System Maßnahmen ergreift, sollte es dies auf die sicherste Weise tun. Wir haben bereits die Verwendung und den Wert eines Dienstkontos erörtert, daher sollte es keine Überraschung sein, dass Ihre GitOps-Systeme Dienstkonten nutzen sollten. Diese Dienstkonten sollten auch über einen möglichst geringen Zugriff verfügen, während sie dennoch in der Lage sind, die Ziele der GitOps-Implementierung in der Plattform zu erreichen.

Sicherheit und GitOps können ein wichtiger Faktor bei der Auswahl des GitOps-Arbeitsmodells für Ihren IDP sein, und wir hoffen, dass diese Richtlinien beim Aufbau von GitOps für Ihr Unternehmen hilfreich sind.

Nachdem wir nun die Sicherheit der Anwendungsbereitstellung behandelt haben, wollen wir auf unserer sicheren Grundlage aufbauen und uns mit der Anwendungssicherheit befassen.

Anwendungssicherheit verstehen – Richtlinien festlegen und durchsetzen

Sicherheit ist ein bewegliches Ziel, und mit dem technologischen Fortschritt nehmen die Angriffsvektoren zu und die Angreifer werden immer raffinierter. Aus diesem Grund sind die Prozesse und Abläufe, die das Team im Bereich Sicherheit pflegt, sogar noch wichtiger als die Technologie selbst. Das liegt nicht daran, dass Technologie keine Rolle spielt, sondern daran, dass eine gute Disziplin und die Gewohnheit eines starken Prozesses es ermöglichen, Technologien entsprechend der Entwicklung der Branche ein- und auszublenden.

Ein Aspekt guter Sicherheitsdisziplin ist die Pflege genauer Dokumentationen und Architekturdiagramme. Wenn eine wesentliche Änderung an der Anwendungsarchitektur vorgenommen wird, kann dies die Risikooberflächen und Angriffsvektoren verändern. Beispielsweise könnte eine undokumentierte oder unzureichend dokumentierte Abhängigkeit von einer Bibliothek oder einem Netzwerkport zu einer Schwachstelle führen, die möglicherweise schwieriger zu erkennen ist.

Grundlegende Anwendungssicherheit

In [Kapitel 5](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/5) haben wir die Erstellung und Bereitstellung von Images und Artefakten behandelt. Die beschriebene Methode der semantischen Versionierung für eine Anwendung stellt eine Best Practice für die Erstellung von Software dar, jedoch nicht für deren Verwendung. Wenn eine Version unter Verwendung von Git für die Quellcodeverwaltung einer Anwendung erstellt wird, erhält die Version dank der modernen Funktionalität von Git zusätzlich zu einer vom Menschen definierten Version eine SHA-256-Signatur. Im Gegensatz zu den Versionsnummern, die wiederverwendet werden können, ist der **Secure Hash Algorithm** (**SHA**) eine Signatur für genau diesen Build der Software und immer eindeutig. Daher ist es für bewährte Sicherheitsverfahren wichtig, die vollständige SHA-Adresse für die von der Plattform verwendeten Images anstelle der Image-Version zu verwenden.

Hier ist ein Beispiel für den Docker-Pull-Befehl unter Verwendung der Image-Version und SHA:

docker pull quay.io/keycloak/keycloak@sha256:520021b1917c54f899540afcb0126a2c90f12b828f25c91969688610f1bdf949

KopierenErklären

Neben den Image-Versionen gibt es noch eine weitere Identifizierungsmethode, die als **Floating Tags** bekannt ist. Ein Floating Tag ist ein Zeiger und wendet einen beliebigen Wert an, der für die Wiederverwendung in einem Release-Image vorgesehen ist. Die gängigsten Tags sind „latest“, aber sie können so ziemlich alles be ieren, da es nur Branchennormen und keine technischen Einschränkungen gibt. Da ein Tag später auf jedes Release-Image umgeleitet werden kann, ist dies keine sichere Methode, um eine Abhängigkeit zu ziehen. Zu den Risiken der Verwendung von Floating Tags gehören die folgenden:

- Unbeabsichtigte und ungetestete/ungeprüfte Updates von Anwendungskomponenten.
- Eingeschränkte Möglichkeit, sofort zu erkennen, was wo und wann ausgeführt wird.
- Nicht geprüfte externe Softwarepakete können sich automatisch verbreiten und so ausnutzbare Hintertüren für böswillige Akteure schaffen. Dies ist häufig der Fall, wenn ein Pod neu gestartet wird und „latest“ im Dockerfile für den Pod verwendet wird.

Es gibt einige Gründe, ein Floating-Tag oder ein semantisches Versions-Release-Tag anstelle eines präzisen SHA zu verwenden. Es ist einfacher, die fortgesetzte Unterstützbarkeit einer Abhängigkeit zu testen, wenn Sie regelmäßig Tests mit dem neuesten Build durchführen. Die Flexibilität, die sich aus der Verwendung der jeweils neuesten Version eines bekanntermaßen guten Pakets ergibt, kann in einer Entwicklungsumgebung wünschenswert sein und dann bei der Umstellung auf die Produktion an ein präzises Versions-Tag oder SHA gebunden werden. Die Validierung anhand von Floating-Tags kann es einem Team auch ermöglichen, schneller auf Sicherheitslücken zu reagieren. Daher sollte eine Risikobewertung jeder Abhängigkeit und eine Richtlinie festgelegt werden, um die Normen der Anwendung zu bestimmen.

Eine typische Methode zur Festlegung einer Richtlinie wäre die Verwendung von Tools wie Open-Source-Policy-Agents, um Abweichungen von den definierten Normen zu erkennen und zu verhindern, dass diese Abweichungen in eingeschränkte Umgebungen gelangen. **Open Policy Agent** (**OPA**) und **Kyverno** sind beide Open-Source-Optionen, die kostenlos genutzt werden können. Bei beiden Tools nutzen Sie **Policy as Code** (**PaC**), das leicht überprüft und in der Quellcodeverwaltung aufbewahrt werden kann.

OPA und Kyverno sind zwei Beispiele für OSS, die für die Sicherheit genutzt werden können, aber sie sind nicht die einzigen Tools im Open-Source-Ökosystem.

FOSS für die Plattformsicherheit und wie man es einsetzt

Es gibt eine Vielzahl von FOSS-Projekten innerhalb und außerhalb der Linux Foundation oder CNCF, die Ihnen bei der Verwaltung der Sicherheitslage Ihrer Plattform helfen. Die zuvor erwähnten Projekte wie Harbor und Trivy sind nur zwei von vielen.

Wenn Sie Ihre Sicherheitsanforderungen vergleichen, z. B. die Einhaltung der OWASP Top Ten für verfügbare Open-Source-Projekte, finden Sie ein Tool, mit dem Sie jeden Punkt auf der Liste abarbeiten können.

Muster und Tools für das Sicherheitsmanagement

Die Plattform kann nur begrenzt zur Verwaltung der Sicherheitslage des Unternehmens beitragen. Daher muss sie eine solide Grundlage für die Sicherheit bieten, indem sie nützliche Integrationen bereitstellt, einen sicherheitsorientierten Ansatz verfolgt und, wie in den vorangegangenen Kapiteln erläutert, offen für Beiträge der Entwickler-Community ist, die sie unterstützt. Wenn Sie festgelegt haben, welche Compliance-Stufen erforderlich sind, können Sie damit beginnen, zu untersuchen, welche Fehler zu einem Versagen Ihrer Compliance und Sicherheitslage führen könnten, indem Sie prozessbasierte Sicherheitsüberprüfungen und technologiebasierte Sicherheitsüberprüfungen durchführen:

- Eine **prozessbasierte Überprüfung** bedeutet, dass eine Person die Compliance und Sicherheit überprüft und bewertet. Dabei kann es sich um ein Audit handeln, das zur Erlangung einer Zertifizierung durchgeführt wird, oder um eine interne Überprüfung, die regelmäßig durchgeführt wird, um sicherzustellen, dass Best Practices weiterhin gelten und die Richtlinien auf dem neuesten Stand sind.
- Bei **einer technologiebasierten Überprüfung** wird Software eingesetzt, um die Sicherheit und Compliance automatisch und wahrscheinlich kontinuierlich zu überprüfen und zu validieren. SBOMs und CVE-Scans sind Beispiele für technologiebasierte Überprüfungen von Software-Builds, und Policy-Engines wie OPA oder Kyverno können bei der automatisierten Governance des IDP helfen. Technologische Lösungen können auch einen zusätzlichen Schritt gehen und dabei helfen, Anomalien und Ereignisse zu erkennen, die einen Sicherheitsvorfall darstellen könnten. Das CNCF-Projekt **Falco** ([https://falco.org](https://falco.org/)) tut genau das. Es verfügt über mehrere wichtige Funktionen, aber vor allem erkennt es, wenn Zugriffsebenen eskaliert werden, was auf eine schlechte Sicherheits- und Compliance-Situation oder auf einen böswilligen Akteur hindeuten kann, der sich Zugang zum System verschafft hat.

Für jedes Unternehmen, das ein bestimmtes Maß an Sicherheit und Compliance gemäß einem geltenden Rahmenwerk nachweisen möchte, hilft dieses Compliance-Rahmenwerk dabei, die Häufigkeit der Prozessausführung zu definieren und diese Leitlinien mit regelmäßigen Audits zu kombinieren, um sicherzustellen, dass die Plattform nicht ins Hintertreffen gerät.

Was würde unser fiktives Unternehmen tun?

Unser fiktives Unternehmen Financial One ACME ist ein traditionsreiches Finanzinstitut, das an seiner Cloud-nativen Transformation arbeitet, um gegenüber jüngeren Fintech-Unternehmen wettbewerbsfähig zu bleiben. Als Finanzinstitut hat es das inhärente Ziel, Risiken zu minimieren. Außerdem unterliegt es regulatorischen Beschränkungen, darunter PCI DSS.

Da es sich um eine Bank handelt, die sowohl Geldvermögen als auch Kundendaten schützen muss, hat sie außerdem potenzielle Bedrohungen für ihre Systeme modelliert. Aus einer langen Liste physischer und nicht-physischer Risiken wurden dem Plattformteam viele Sicherheitsmaßnahmen vorgelegt, die während der Implementierung des IDP umgesetzt werden sollten. Diese Maßnahmen wurden wahrscheinlich bereits umgesetzt, aber da es sich bei diesem IDP um eine Greenfield-Anwendung (oder eine brandneue Anwendung) handelt, müssen die Compliance-Anforderungen neu berücksichtigt werden.

Eine Aufgabe, die dem Plattformteam zur Umsetzung vorgelegt wurde, war die Gewährleistung, dass alle neuen Versionen ihres Softwarepakets ordnungsgemäß gesichert sind.

Ordnungsgemäß gesichert bedeutet Folgendes:

- Signiert und validiert
- Sicher gespeichert
- Sicher abgerufen
- Strenge Änderungskontrolle
- Prüfpfad

Das Plattformteam hat die zuvor beschriebenen Maßnahmen ergriffen, um sein Repository und sein GitOps-System zu sichern, aber diese reichten nicht aus, um diese Anforderung zu erfüllen. Aus diesem Grund entschied sich das Plattformteam, eine interne Image-Registry zu nutzen, in der alle Software-Commits und -Pakete signiert werden. Die CI/CD-Pipelines erstellen Images auf der Grundlage dieser Artefakte und legen sie in der privaten Registry ab, wo sie von den Plattformanwendungen genutzt werden.

Die Auswahl der Image-Registry würde wie eine der folgenden Optionen aussehen:

- Bezahlung eines Image-Registry-Anbieters, der ihnen durch Scans bei der Aufrechterhaltung ihrer Sicherheitslage hilft und ihnen vertrauenswürdige **Universal Base Images** (**UBIs**) zur Verfügung stellt
- Hosting einer eigenen Image-Registry wie Harbor, einem CNCF-graduierten Projekt mit einer Image-Registry, die Container-Images signiert, speichert und scannt (https://goharbor.io/) und die mit genehmigten Images gefüllt wird
- Wenn sie OpenShift verwenden, gibt es bereits eine Image-Registry als Teil der Cluster-Topologie, die das Plattformteam durch Scan-Tools ergänzt.

Außerdem haben sie einen Admission-Webhook hinzugefügt, um sicherzustellen, dass kein Container auf einem nicht genehmigten Image basiert. Dieser Anwendungsfall ist sehr einfach: Ein validierender Webhook überprüft, ob das Container-Image den definierten Erwartungen entspricht. Ist dies nicht der Fall, wird die Workload abgelehnt und der Pod wird nicht gestartet. Das Team könnte zwar einen eigenen Zulassungs-Webhook-Dienst entwickeln, würde sich aber wahrscheinlich für OPA entscheiden. Es ist zwar nicht das einzige Open-Source-Projekt, das diese Funktionalität bietet, aber es ist das einzige abgeschlossene Projekt, was es zur sichersten Wahl für den Einsatz in der Produktion macht.

Sysdig hat eine Open-Source-Version eines solchen Webhooks entwickelt, der auch Pod-Konfigurationen mutiert oder modifiziert, damit ihre Images das vollständige Image-SHA anstelle eines Release-Tags verwenden. Dieser ist hier zu finden: https://github.com/sysdiglabs/opa-image-scanner. Beide Webhooks stellen absolute Best Practices für Sicherheit und Compliance dar und sind ein kluger Schachzug für jedes Plattform-Engineering-Team, das auf einfache Weise mehr Sicherheit erreichen möchte.

So wichtig diese Einschränkungen auch sind, können sie sich doch negativ auf die Innovation auswirken, da sie die Flexibilität der IDP-Funktionen einschränken. Aus diesem Grund hat das Plattformteam beschlossen, diese Einschränkungen auf die Produktionsumgebung zu beschränken. Auf diese Weise können die Entwicklungsteams in ihren Entwicklungsumgebungen experimentieren, ohne etwas zu riskieren, das nicht versehentlich in die Produktionsumgebung gelangen sollte.

Eine Strategie zur Verwaltung von Abhängigkeiten, bei denen Sie keinen Quellcode aus nicht vertrauenswürdigen Quellen beziehen möchten, ist die Verwendung von Vendoring. Vendoring ist der Prozess des Kopierens des Codes aus der Open-Source-Bibliothek, den Sie sonst in Ihre Codebasis importieren würden. Während des Vendoring können Änderungen an diesem Code vorgenommen werden, um ihn sicherer zu machen, z. B. durch Aktivieren des FIPS-Modus (**Federal Information Processing Standards**). Die FIPS-Konformität legt die Stärke der Verschlüsselung von Daten über **Secure Socket Layer** (**SSL**) fest und ist im Allgemeinen eine bewährte Vorgehensweise.

Eine weitere Aufgabe, die dem Plattformteam zukommen könnte, wäre es, im Falle eines vermuteten Sicherheitsverstoßes als erster Ansprechpartner zu fungieren. Das bedeutet, dass es eine Möglichkeit geben muss, sofort auf Meldungen über ein Problem zu reagieren. Da die Plattform für einen Großteil der Unternehmensinfrastruktur verantwortlich ist, von der Entwicklung bis zur Produktion, muss das Team in der Lage sein, schnell zu reagieren, um Schäden durch böswillige Akteure zu minimieren.

Solche **IR-Pläne** (**IRPs**) sollten ausgearbeitet und regelmäßig getestet werden. Ähnlich wie bei einem **Disaster-Recovery-Plan** (**DRP**) können regelmäßige Tests des Plans und die Fähigkeit, auf eine echte Sicherheitsverletzung zu reagieren, Schäden mindern.

Die frühzeitige Erkennung ist eine weitere wichtige Funktion, die von der Plattform benötigt wird. Die Analyse von Audit-Protokollen ist entscheidend, um zu verstehen, wer eingedrungen ist (oder wessen Anmeldedaten kompromittiert wurden) und was getan wurde, nachdem der böswillige Akteur Zugriff auf das System erhalten hat. Audit-Protokolle können auch für die proaktive Erkennung verwendet werden, da sie von Machine-Learning-Modellen (**ML**) zur Erkennung von Anomalien genutzt werden können, die eine Sicherheitsverletzung schneller aufdecken können, als ein Mensch sie finden könnte. Darüber hinaus kann die Verwendung einer gut beobachtbaren Cloud-nativen Netzwerklösung wie Cilium dabei helfen, Angreifer zu identifizieren und zu verfolgen. Einige fest programmierte Observability-Implementierungen können zwar die gleichen Ergebnisse erzielen, müssen jedoch manuell gepflegt und gewartet werden, während ML-Modelle aufgrund ihrer selbstlernenden Natur möglicherweise eine größere Flexibilität bieten.

Keine der beiden Methoden ist perfekt. Bei der Entscheidung, wie die Automatisierung der Bedrohungserkennung umgesetzt werden soll, muss ein Unternehmen daher eine Abwägung zwischen Vorteilen, Kompromissen und Teamfähigkeiten vornehmen. Die Entscheidung für den weiteren Weg unseres fiktiven Unternehmens wäre eine „Build-versus-Buy”-Diskussion, die aufgrund des Umfangs und der Komplexität der Aufgabe sowie der hochsicheren Umgebung, die es aufrechterhalten soll, sehr wohl zu einer Kaufentscheidung führen könnte.

Apropos hochsichere Umgebung: Um einem Prüfer die PCI-Konformität des Unternehmens mit dem neuen IDP nachzuweisen, muss unser Plattformteam in der Lage sein, eine Zeichnung der Netzwerkarchitektur zu erstellen und dem Prüfer den Inhalt dieser Zeichnung zu erklären.

Jeder Compliance-Prüfer wird überprüfen wollen, ob die Entwicklungs- und Produktionsumgebungen ausreichend voneinander isoliert sind, sei es physisch oder durch Netzwerkimplementierungen.

Schließlich wird das Plattformteam von Financial One ACME nicht nur sicherstellen, dass alle bekannten Best Practices für die Build-Zeit befolgt werden, sondern auch Tools implementieren, um sicherzustellen, dass die Laufzeit ebenso sicher ist. Es ist sehr wahrscheinlich, dass die einzigen Benutzer mit Berechtigungen zum Erstellen von Pods in der Produktionsumgebung diejenigen Service-Account-Benutzer sind, wodurch sichergestellt wird, dass Git das SOT bleibt und GitOps zur Kodifizierung der Sicherheitslage der Plattform genutzt werden kann.

Diese Beispielantworten decken nur einen Teil der Sicherheits- und Compliance-Anforderungen ab, die für ein Finanzinstitut wie eine Bank gelten würden. Darüber hinaus unterliegen sie wahrscheinlich zusätzlichen staatlichen Vorschriften, die noch weitergehende Maßnahmen zur Minderung von Sicherheits- und Compliance-Risiken erfordern würden. Genau wie Ihr Team müsste auch unser fiktives Unternehmen jeden einzelnen Punkt der für es geltenden Compliance-Rahmenbedingungen berücksichtigen und vor allem gemeinsame Verfahren einführen, um ein Höchstmaß an Sicherheit zu gewährleisten.

Zusammenfassung

Zusammenfassend lässt sich sagen, dass Sicherheit und Compliance ein weites Feld sind, zu dem viele Experten spezielle Werke veröffentlicht haben. Dieses Kapitel sollte nicht als allumfassend angesehen werden, sondern Ihnen den richtigen Weg weisen, um eine Cybersicherheitsstrategie für Ihr IDP zu definieren und umzusetzen. Es ist wichtig zu wissen, wie Sie Schwachstellen im Blick behalten können, und in Ihrem Unternehmen Verfahren und Tools einzurichten, um Schwachstellen im IDP und den darin gehosteten Anwendungen zu erkennen und aufzudecken.

Sicherheit und Flexibilität sind zwar keine natürlichen Partner, aber intelligente Implementierungen, die sich auf kritische Sicherheitsanforderungen konzentrieren, ohne die Innovation zu behindern, sind der Schlüssel, um den Entwicklern die Tools zur Verfügung zu stellen, die sie für ihren Erfolg benötigen, und ihnen den Schutz zu bieten, den sie für ihre Sicherheit benötigen.

Denken Sie daran: Die Kosten eines Sicherheitsvorfalls können astronomisch hoch sein und sogar zu Insolvenz oder Gerichtsverfahren führen. Die Speicherung von Protokollen und andere Sicherheitsanforderungen können zwar Kosten verursachen, diese Kosten sind jedoch überschaubar und niemals höher als die Kosten, die durch die Nicht-Sicherung Ihrer Systeme entstehen. Weitere Informationen zur Verwaltung der **Kosten** Ihrer Plattform finden Sie in [Kapitel 8](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap6/Platform%20Engineering_7%20de.md).
