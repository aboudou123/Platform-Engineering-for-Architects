### Die Grundlage für die Unterstützung von Plattformfunktionen schaffen ###

Die Lösung von Problemen, die Nutzer haben, die Gestaltung einer guten Nutzer- und Entwicklererfahrung und die Vermeidung technischer Komplexität sind die grundlegenden Schritte zu erfolgreichen Produkten und erfolgreicher Plattformentwicklung.

In der Realität scheitern viele Projekte, weil diese grundlegenden Prinzipien vernachlässigt werden: Wir sehen, wie Architekten sich in technischen Details verlieren und das zu lösende Problem aus den Augen verlieren. Allzu oft scheitern Projekte, weil der Endnutzer nicht kontinuierlich in den Entstehungsprozess eines neuen Produkts einbezogen wurde. Häufig werden architektonische Entscheidungen getroffen, ohne zu berücksichtigen, wie sich dieses neue Produkt in das bestehende Ökosystem, die Prozesse und die Kompetenzen der Organisation einfügt. All dies führt zu einer wackeligen Grundlage mit begrenztem Erfolgspotenzial.

In diesem Kapitel gehen wir die obligatorischen Schritte und Prozesse durch, um eine solide Grundlage für eine Plattform zu definieren, die von einem ersten Satz von Funktionen zu wichtigen unternehmensunterstützenden Plattformfunktionen ausgebaut werden kann.

**Daher behandeln wir in diesem Kapitel die folgenden Hauptthemen**:

- Finanzielles ACME – unser fiktives Unternehmen
- Überwindung der Komplexität der Plattform durch die richtige Perspektive
- Berücksichtigung bestehender Prozesse und Integration einer neuen Implementierung
- Entwurf der Infrastrukturarchitektur
- Erkundung von Multi-Cloud, Multi-SaaS und der Fragmentierung von Funktionen
- Erforschung einer Referenzarchitektur für unsere Plattform

Financial One ACME – unser fiktives Unternehmen

In diesem Abschnitt lernen wir, wie man die Anforderungen der Nutzer in einem Ingenieursunternehmen versteht, wie man die Anforderungen verschiedener Teams in Einklang bringt und wie man entscheidet, welche Funktionen in eine Plattform aufgenommen werden sollen und welche nicht.

Um dies anschaulicher und realistischer zu gestalten, stellen wir Ihnen Financial One ACME vor. Es handelt sich zwar um ein fiktives Unternehmen, aber die Geschichte, die technologischen Herausforderungen und die Teams, die wir im weiteren Verlauf dieses Buches vorstellen und verwenden werden, entsprechen denen vieler Unternehmen, mit denen wir in den letzten Jahren zusammengearbeitet haben. Anhand eines solchen Unternehmens können wir besser erklären, wie die in diesem Buch vorgestellte Theorie in die Praxis umgesetzt werden kann.

Werfen wir einen Blick auf einige wichtige Details zu Financial One ACME:

- **Eine kurze Geschichte von Financial One ACME**: Financial One ACME ist ein führender Anbieter von Softwarelösungen für den Finanzdienstleistungsmarkt. Das Unternehmen startete Anfang der 2000er Jahre mit einer klassischen 3-Tier-Anwendungsarchitektur (Windows Rich Client, Anwendungsserver und Datenbank), die Kunden in ihren Rechenzentren installierten, wobei zweimal jährlich neue Versionen der Software ausgeliefert wurden.

Im Laufe der Jahre wurde der Windows-Rich-Client nach und nach durch einen Web-Client ersetzt.

- **Bereitstellung eines selbst gehosteten SaaS- und On-Premises-Angebots**: Im Jahr 2015 stieg die Nachfrage nach einer SaaS-gehosteten Version. Anstatt das Produkt neu zu konzipieren, um Multi-Tenancy für eine SaaS-basierte Lösung zu unterstützen, wurde beschlossen, den Anwendungsserver und die Datenbank für jeden SaaS-Kunden einfach separat im bestehenden Rechenzentrum von Financial One ACME zu hosten. Damit waren die Bedenken hinsichtlich Datenresidenz und Datenzugriff ausgeräumt. Allerdings bedeutete dies, dass mit der wachsenden Zahl von SaaS-basierten Kunden auch der Betriebsaufwand stieg, da jeder Kunde (=Tenant) eine Produktionsumgebung auf seinen separaten VMs hatte.

Darüber hinaus stand der IT-Betrieb vor der Herausforderung, die Kapazität des Rechenzentrums für Produktionsumgebungen kontinuierlich zu erweitern, um mit dem Geschäftswachstum Schritt zu halten. Aufgrund der unterschiedlichen Größe der Kunden mussten sie auch eine individuelle Kapazitätsplanung für jeden Mandanten durchführen, um die Umgebungen richtig zu dimensionieren und nicht zu überdimensionieren.

Die Entwicklungsteams hingegen waren für die Vorproduktionsumgebungen verantwortlich. Dazu gehörte alles von den Entwicklungs-Workstations über die Build-Server bis hin zu den Vorproduktions-Test- und Staging-Umgebungen.

- **Umstellung auf monatliche Releases**: Von 2015 bis 2020 wurde die Release-Kadenz kontinuierlich verbessert, was zu einem monatlichen Release-Zyklus führte. Diese Releases wurden von den Entwicklungsteams auf Basis v s erstellt und getestet und dann dem IT-Betrieb zur Bereitstellung in SaaS sowie den Kunden zur Verfügung gestellt, die die Software noch vor Ort betrieben. Diese Geschwindigkeitsänderung führte dazu, dass nicht alle Kunden ihre Software so häufig aktualisieren wollten, da dies mit ihren internen Änderungsanforderungsprozessen abgestimmt werden musste. Einige Kunden waren bis zu sechs Releases hinter dem aktuellen Build zurück, was das Entwicklungsteam zusätzlich belastete, da es all diese älteren Versionen unterstützen musste.
- **Der Umzug in die Cloud**: Im Jahr 2020 expandierte das Unternehmen in neue Regionen, wodurch auch der Bedarf an SaaS-Angeboten in diesen Regionen stieg. Anstatt weitere Rechenzentren zu bauen, beschloss das Unternehmen, seine bestehende Produktionsarchitektur in die Compute-Angebote der Public-Cloud-Anbieter zu verlagern.

Dieser Schritt umfasste auch neue Prozesse und Richtlinien für die Aktualisierung von Software oder den Zugriff auf Daten auf diesen Cloud-Servern – zum Beispiel, wie man auf Protokolle von Server X zugreift, die zu Mandant Y gehören!

- **Von neuen FinTech-Unternehmen übertroffen**: Während der Pandemie entstanden neue FinTech-Softwareunternehmen, die für die Cloud konzipiert und entwickelt wurden! Dies setzte Financial One ACME unter Druck, da diese neuen reinen SaaS-Unternehmen keine Legacy-Architektur zur Unterstützung von SaaS und On-Premises-Lösungen unterhalten mussten. Ihre Architekturen waren zudem mandantenfähig und Multi-Cloud-fähig, wodurch sie kosteneffizienter arbeiten konnten als das entsprechende Angebot von Financial One ACME.

Die Unternehmensleitung traf die strategische Entscheidung, ihr Angebot neu zu gestalten und gleichzeitig die Effizienz der Entwicklung, des Supports und des Betriebs der bestehenden Plattform zu verbessern, bis alle Kunden auf das zukünftige reine SaaS-Angebot umgestellt werden konnten.

Und nun sind wir im Jahr 2024 angelangt und es ist an der Zeit, darüber nachzudenken, wie wir diesem Unternehmen helfen können, sich zu modernisieren und neu zu erfinden. Kubernetes und Cloud Native sind die Technologieplattformen der Zukunft! Die Hoffnung liegt in der Plattformentwicklung, um die Arbeit der Ingenieure zu verbessern, die sowohl an der zukünftigen Plattform arbeiten als auch die alte Plattform warten. Hier kommen wir ins Spiel – das neu gegründete Plattformentwicklungsteam!

Lassen Sie uns nun verstehen, wer die potenziellen Nutzer unserer zukünftigen **internen Entwicklerplattform** (**IDP**) sein könnten:

- **Entwicklungsteams**: Verwaltung aller Vorproduktions-Tools und -Umgebungen
- **IT-Betrieb**: Verwaltung der lokalen Rechenzentrums- und Cloud-Computing-Ressourcen
- **DevOps**: Das Team, das für die Bereitstellung und den Betrieb der bestehenden SaaS-basierten Produktionsumgebungen aus Anwendungssicht verantwortlich ist
- **Qualitätsingenieure**: Die Teams, die sich auf das Testen neuer Software konzentrieren, bevor diese in die Produktion übernommen wird
- **Site Reliability Engineers (SREs)**: Teams, die sich auf Ausfallsicherheit, Verfügbarkeit und die Unterstützung bei der Berichterstattung und Durchsetzung von SLAs und SLOs konzentrieren
- **Technische Dokumentation**: Das Team, das für jede Veröffentlichung die Dokumentation für Endbenutzer vorbereitet, zusammen mit Versionshinweisen, neuen Funktionen und Anleitungen
- **Sonstige**: Dazu gehören **Datenbankadministratoren**, **Projektmanager**, **Product Owner**, **ProdSec** und andere

Nachdem wir nun wissen, wer wir als Team sind und wer unsere potenziellen Nutzer sind, wollen wir uns damit befassen, wie wir eine Plattform aufbauen müssen, die ihre Probleme löst!

Überwindung der Komplexität der Plattform durch die richtige Perspektive

„Wir haben Monate damit verbracht, unsere neue Plattform aufzubauen. Die Entwickler hassen sie! Helfen Sie mir zu verstehen, warum!“

Wir möchten nicht in eine Situation geraten, in der wir das Gefühl haben, eine solche Frage in einem öffentlichen Diskussionsforum stellen zu müssen. Diese Überschrift stammt – ob Sie es glauben oder nicht – aus einem echten Beitrag. Wenn Sie mehr über diese Geschichte erfahren möchten, lesen Sie den Reddit-Beitrag \[1\] im Abschnitt „Weiterführende Literatur“.

Wie kann so etwas passieren? Der Grund, warum viele Plattform-Engineering-Initiativen scheitern, ist derselbe, warum auch andere Produktentwicklungsinitiativen gescheitert sind: Jemand hatte eine großartige Idee – entwickelte ein Produkt oder ließ es entwickeln –, fand aber letztendlich niemanden, der den Nutzen dieses neuen Produkts erkannte, da es kein echtes Problem der Menschen löste.

Der Fehler, den viele machen, besteht darin, die ursprüngliche Idee nicht mit den potenziellen Endnutzern zu validieren, von denen sie glauben, dass sie von dieser Lösung profitieren würden. Wenn Sie keine kritische Masse an Nutzern finden, deren Problem durch ein neues Produkt gelöst wird, ist es besser, gar kein Produkt zu entwickeln, da es von vornherein zum Scheitern verurteilt ist.

Wenn Sie in der Vergangenheit bereits im Produktmanagement tätig waren, denken Sie wahrscheinlich: „Aber das ist doch Produktmanagement für Anfänger!“ Da stimme ich voll und ganz zu! Allerdings verfügt nicht jedes Team, das mit der Entwicklung einer neuen Plattform beauftragt ist, über Erfahrung im Produktmanagement. Viele Teams, die wir gesehen haben, befinden sich in einer Situation, in der sie mit der Entwicklung einer Plattform beginnen können, ohne die Parallelen zur Entwicklung eines normalen Produkts zu erkennen. Viele Aufgaben fallen bereits vor Beginn der Produktentwicklung an.

Anwendung grundlegender Produktmanagement-Prinzipien – „Geben Sie Ihren Nutzern kein schnelleres Pferd“

Der richtige Ansatz für erfolgreiche Plattform-Engineering-Initiativen entspricht dem, was erfolgreiche Produktteams in der Vergangenheit getan haben:

- Identifizieren Sie ein Problem, das eine ausreichend große Nutzerbasis hat.
- Verstehen Sie, warum dies eine Herausforderung ist und welche negativen Auswirkungen dies derzeit hat
- Recherchieren Sie, warum dieses Problem noch nicht gelöst wurde
- Wie würden Sie den Nutzen quantifizieren, wenn Sie dieses Problem lösen könnten?

Um diese Fragen zu beantworten und über die Grundlagen hinauszugehen, empfehlen wir Ihnen, mit Ihren potenziellen Endnutzern zu sprechen. Lassen Sie sich von ihnen das tatsächliche Problem schildern und geben Sie ihnen die Freiheit, eine Lösung zu erklären, mit der sie ihre Arbeit ideal erledigen können.

Achten Sie beim Zuhören darauf, dass Sie sich nicht durch technische Einschränkungen oder Herausforderungen, die Ihnen derzeit bekannt sind, einschränken lassen. Es gibt ein berühmtes Zitat von Henry Ford, der angeblich gesagt haben soll: „Hätte ich die Menschen gefragt, was sie wollen, hätten sie gesagt: schnellere Pferde.“ Sie werden feststellen, dass Ihre Nutzer in der Regel leicht beschreiben können, welches Problem sie haben. Die Lösung, die sie oft vorschlagen, ist jedoch durch das, was sie für möglich halten, oder durch die technischen Einschränkungen, die ihnen derzeit bekannt sind, begrenzt.

Wir werden jetzt nicht damit beginnen, eine revolutionäre neue Methode für die Softwareentwicklung zu entwickeln, die Monate oder Jahre in Anspruch nimmt. Diese Denkweise ist jedoch wichtig, da sie ein „ “-Schritt zur Lösung von Problemen ist, die andere nicht lösen konnten, und zwar auf eine Weise, dass die Lösung breite Anwendung findet!

Lassen Sie uns zunächst darüber nachdenken, wie wir dieses Problem mit der einfachsten und schnellsten technischen Lösung lösen können. Versuchen Sie nicht, von Anfang an eine übertrieben komplexe Lösung zu entwickeln, um die beste oder revolutionärste technische Umsetzung zu finden. Das sollte zwar ein inspirierendes Ziel sein, aber unser ursprüngliches Ziel ist es, schnelles Feedback und eine Bestätigung dafür zu erhalten, ob unsere vorgeschlagene Umsetzung die Probleme unserer potenziellen Endnutzer löst.

Um dieses schnelle Feedback zu erhalten, müssen Sie Folgendes tun:

- Liefern Sie schnell eine Lösung
- Zeigen Sie sie Ihren potenziellen Endnutzern
- Holen Sie sich kontinuierliches Feedback
- Verfeinern Sie die Lösung auf der Grundlage des Feedbacks
- Wiederholen Sie diese Schritte immer wieder

Dieser Prozess wird so lange fortgesetzt, bis Sie nachweisen können, dass Ihre Nutzer bereit sind, Ihre Lösung zu verwenden, da sie ihre Arbeitsweise verbessert.

Vermeiden Sie den „Sunk-Cost-Fehler”

Nicht jedes Projekt wird zum Erfolg führen, egal wie hart und oft Sie es versuchen und wiederholen. Der **Sunk-Cost-Fallacy** ist ein bekanntes Problem, das wir sowohl in alltäglichen Entscheidungen als auch in der Softwareentwicklung beobachten können. Es verdeutlicht das Problem, dass Unternehmen aufgrund bereits getätigter Investitionen weiterhin in eine Strategie investieren, obwohl es offensichtlich ist, dass es besser wäre, diese Investition zu stoppen, da sie keine Aussicht auf Erfolg hat. Zu diesem Thema gibt es zahlreiche Informationen, die Sie nachlesen können, beispielsweise den Artikel **„Sunk Cost“** \[2\].

Daher ist es wichtig, zu definieren, wann Sie Ihre Iterationen beenden sollten. Wenn der Moment, in dem „die Nutzer die Lösung lieben”, nicht innerhalb einer bestimmten Zeitspanne eintritt, müssen Sie bereit sein, den Stecker zu ziehen und die Initiative zu beenden. Dazu müssen Sie sich Meilensteine setzen, um diesen **Validierungspunkt** Ihrer Lösung zu erreichen. Denken Sie daran, wie bereits erwähnt, dass Sie nicht mit einem Beitrag enden wollen, der lautet: „Wir haben Monate damit verbracht, diese Plattform zu entwickeln. Die Entwickler hassen sie! Helfen Sie mir zu verstehen, warum!“

Schritte zum Aufbau dessen, was die Nutzer brauchen – ein Beispiel aus der Praxis

Kehren wir noch einmal zum Anfang zurück. Was müssen wir entwickeln? Im Produktmanagement gibt es viele verschiedene Memes (ein Beispiel finden Sie in Abbildung 3.1) darüber, wie sich die entwickelten Produkte von den Bedürfnissen der Nutzer unterscheiden. Das Gleiche gilt, wenn Sie nach Memes zum Thema Overengineering suchen. Sie alle kommen zu dem gleichen Schluss: Etwas entwickeln, ohne zuvor die Bedürfnisse der Nutzer zu verstehen!

Abbildung 3.1: Das Paradoxon des Overengineering

Es ist möglich, eine Situation zu vermeiden, in der wir am Ende etwas entwickeln, das das eigentliche Problem nicht löst oder es auf eine viel zu komplexe Weise löst, sodass sich die Investition nicht auszahlt.

Der schwierigste Schritt auf jedem Weg ist der erste Schritt. In unserem Fall geht es darum, zu verstehen, wer die potenziellen Nutzer unserer Plattform sind und welche tatsächlichen Probleme eine Plattform lösen kann!

Um dies in der Praxis zu veranschaulichen, gehen wir mehrere Schritte durch, wie wir dies für Financial One ACME angehen würden!

Schritt 1 – Verstehen Sie die tatsächlichen Probleme Ihrer Nutzer

In Flurgesprächen beklagen sich die Entwicklungsteams oft darüber, dass die Analyse von Problemen in ihrer Software in der Vorproduktionsphase viel einfacher war als in Produktionsumgebungen. Sie haben vollen Zugriff auf alle Protokolle ihres Build-Servers (Jenkins) und ihrer Testtools (Selenium und JMeter) sowie auf die Umgebung, in der sie ihre Software bereitgestellt haben. Sie konnten problemlos die Protokollebenen erhöhen oder schnell eine neue Version mit mehr Protokollausgaben bereitstellen, um Probleme schneller zu triagieren.

Wenn Probleme in der Produktion entdeckt werden, ist die Analyse des Problems eine ganz andere Geschichte! Die Entwicklungsteams müssen die IT-Abteilung um Erlaubnis bitten, um Zugriff auf die Protokolle zu erhalten, indem sie ein Jira-Ticket eröffnen. Das dauert manchmal Stunden, da das IT-Team in der Regel mit vielen anderen Aufgaben überlastet ist. Das IT-Team verfügt auch nicht über das Insiderwissen darüber, wo die Software alle Protokolle schreibt, und die Entwicklungsteams geben diese Informationen auch nicht immer im ersten Ticket an. Aus diesem Grund sind oft mehrere Iterationen erforderlich, um die gewünschten Protokolle zu erfassen und sie in das Tool der IT-Abteilung hochzuladen, um produktionsrelevante Daten mit anderen Teams zu teilen. Auch die Änderung der Protokollebenen ist nicht so einfach. Produktionsänderungen wie diese müssen einem speziellen Änderungsgenehmigungsprozess folgen. Da es sich um eine Softwareänderung handelt, wird sie vom DevOps-Team bearbeitet, was den Prozess noch weiter verlangsamt!

Für die Entwicklungsteams bedeutet dies, dass sie nicht mehr einfach per Fernzugriff auf einen Server zugreifen können, um die Protokolle vor Ort zu analysieren, sondern dass diese Protokolle über das zentrale Produktionsdatenspeichertool der IT-Abteilung analysiert werden müssen. Das Entwicklungsteam ist jedoch nicht besonders vertraut mit diesem Tool, da es nicht regelmäßig damit arbeitet. Dieses zentralisierte Tool verfügt außerdem über ein eigenes Berechtigungssystem, das ursprünglich eingerichtet wurde, um unbefugten Zugriff auf geschützte Daten zu verhindern. Da dieses System nicht in das Authentifizierungs- und Zugriffskontrollsystem integriert ist, das die Entwickler verwenden, ist es oft nicht mit den aktuellen Teamzuweisungen synchronisiert. Dies führt zu Situationen, in denen einzelne Ingenieure eines Teams nicht auf die benötigten Protokolle zugreifen können, was zusätzliche Zyklen mit IT-Ops und DevOps zur Folge hat oder dazu führt, dass sie eine nicht genehmigte Abkürzung verwenden, indem sie einfach einen Entwicklerkollegen fragen, der zufällig Zugriff auf die Protokolle hat!

Wie Sie sehen, gibt es viel Frust und Ärger im Entwicklungsteam. Aber wie Sie sich auch vorstellen können, gibt es auch viel Frust bei den IT-Ops- und DevOps-Teams. Ihre Arbeit im Produktionsbetrieb wird ständig durch Aufgaben unterbrochen, bei denen sie Daten aus der Produktion nachschlagen und Zugriff darauf gewähren oder eine Änderung der Protokollebene genehmigen müssen. Es gibt ständig viel Hin und Her, um zu verstehen, welche Daten angefordert werden, wo diese Daten zu finden sind und wer Zugriff auf diese Daten haben sollte.

In der Regel sind viele Gespräche erforderlich, um sich ein vollständiges Bild zu machen, die Probleme auf beiden Seiten zu verstehen und genügend Details zu sammeln, um über eine bessere, durchdachte Vorgehensweise nachzudenken. Wenn Sie dies in Ihrem Unternehmen anwenden, planen Sie genügend Zeit ein und informieren Sie die Personen, mit denen Sie sprechen möchten, im Voraus, damit sie sich auf diese Gespräche vorbereiten können!

Um mit dem Vorschlag einer Lösung zu beginnen, ist es am besten, sich einen Überblick über die Probleme aller Seiten zu verschaffen, wie in der folgenden Tabelle dargestellt:

|     |     |     |
| --- | --- | --- |
| **Problem**: Entwickler haben keinen direkten Zugriff auf Protokolle in der Produktion |     |     |
| **Schwachstellen**: Entwicklungsteam | **Schwachstellen**: IT-Betrieb | **Schwachstellen**: DevOps |
| Es müssen Jira-Tickets erstellt werden, um Zugriff auf Protokolle in der Produktion zu beantragen. | Es müssen Jira-Tickets bearbeitet werden, um Zugriff auf Protokolle zu beantragen. |     |
| Es wird viel Zeit für Tickets aufgewendet, bis das IT-Betriebsteam das richtige Protokoll zum Erfassen identifiziert hat. | Entwickler geben in Tickets nicht immer genügend Informationen an. Es sind zusätzliche Iterationen erforderlich, um alle notwendigen Details zu erhalten. |     |
| Es ist schwierig, die Protokollebenen in der Produktion während der Triage zu ändern. Es müssen noch mehr Änderungsanforderungstickets erstellt werden. |     | Bearbeitung ungeplanter Änderungsanforderungstickets zur Erhöhung der Protokollebenen. |
| Ineffiziente Protokollanalyse. Entwickler sind eher an das in der Vorproduktion verwendete Tool gewöhnt. Das Produktionstool ist für sie nicht so intuitiv und verlangsamt ihre Arbeit. |     |     |
| Umgang mit Berechtigungsproblemen im Produktionsprotokollanalyse-Tool. | Zusätzlicher Aufwand, um zu erklären, dass die Informationen zu Eigentums- und Berechtigungs en nicht mit den Entwicklersystemen synchronisiert sind. |     |

Tabelle 3.1: Organisation des Problems und seiner Schwachstellen in einer übersichtlichen Tabelle

Nachdem wir nun eine Liste der Schwachstellen beider Seiten haben, ist es an der Zeit, über eine Lösung für diese Schwachstellen nachzudenken, wie groß die Auswirkungen dieser Lösung wären, wie viel sie kosten würde und wie hoch die **Kapitalrendite** (**ROI**) wäre!

Schritt 2 – Quantifizieren Sie den Nutzen der Lösung dieser Schwachstellen

Wir beginnen damit, die Auswirkungen einer Lösung zu quantifizieren. Dies ist notwendig, um zu rechtfertigen, wie viel Zeit und Aufwand in den Aufbau einer Plattform fließt, die diese Schwachstellen behebt. Die zuvor erläuterten Schwachstellen sind zwar real, aber wir müssen verstehen, ob es sich um Einzelfälle oder regelmäßige Vorkommnisse handelt. Die Frage, die wir beantworten müssen, lautet: Ist es gerechtfertigt, Wochen in den Aufbau einer Plattform zu investieren, die dieses Problem löst?

Zurück zu denselben Teams: Es ist an der Zeit, die Kosten der aufgeführten Probleme in Bezug auf den Zeitaufwand oder die tatsächlichen Kosten in Dollar zu quantifizieren. Wir können diese Zahlen entweder durch fundierte Schätzungen oder anhand der aktuellen Zeiterfassung (die beste Option) ermitteln. Da das Team derzeit Tickets verwendet, sollten wir in der Lage sein, die Gesamtzeit zu ermitteln, die auf beiden Seiten für diese Tickets aufgewendet wurde.

Hier ist eine überarbeitete Tabelle mit den zusätzlichen Kostenauswirkungen!

|     |     |     |     |
| --- | --- | --- | --- |
| **Probleme/Zeitaufwand pro Monat** | **Entwicklungsteams** | **IT-Betrieb** | **DevOps** |
| Langsamer Prozess zur Beantragung des Protokollzugriffs | 2 Tage | 4 Tage |     |
| Zusätzlicher Prozess zur Änderung der Protokollstufe | 0,5 Tage |     | 0,5 Tage |
| Ineffiziente Protokollanalyse | 2 Tage |     |     |
| Workaround für Berechtigungsprobleme | 0,5 Tage |     |     |
| **Gesamtsumme** | 5 Tage pro Monat oder 60 Tage pro Jahr | 4 Tage pro Monat oder 48 Tage pro Jahr | 0,5 Tage pro Monat oder 6 Tage pro Jahr |

Tabelle 3.2: Quantifizierung des Nutzens jedes einzelnen Problemfelds und einfache Übersicht

Dies ist eine großartige Übersicht mit interessanten Statistiken, die uns die Entscheidung erleichtern. Wenn wir alle diese Schwachstellen für das Problem lösen können, das Entwickler haben, nämlich dass sie derzeit keinen einfachen Zugriff auf die erforderlichen Protokolldateien in der Produktion haben, können wir bis zu 114 Engineering-Tage pro Jahr einsparen. Das ist ein guter Ausgangspunkt und ein gutes Argument, um in die Verbesserung der Effizienz unserer Teams zu investieren, indem wir in die Plattformentwicklung investieren!

Schritt 3 – Vorschlag einer Lösung, die die Entwicklererfahrung verbessert

Da wir nun wissen, dass wir potenziell bis zu 114 **Vollzeitäquivalente** (**FTE**) an Engineering-Tagen pro Jahr einsparen können, sollten wir einen Lösungsvorschlag ausarbeiten, den wir den betroffenen Anwendern präsentieren können. Wir dürfen dabei nicht die technischen Details der Lösung präsentieren, sondern müssen zeigen, wie die Entwickler die User Journey erleben werden. **Entwicklererfahrung** ist hier das Schlüsselwort, das im Bereich Plattform-Engineering häufig diskutiert wird. Lassen Sie uns also eine Lösung entwickeln, die unseren Entwicklern eine neue Erfahrung bietet, die sie dazu bringt, unsere Lösung nutzen zu wollen!

Wie in der Produktentwicklung müssen wir unsere Endnutzer einbeziehen, indem wir sie um Input dazu bitten, wie sie mit einer zukünftigen Lösung interagieren möchten. Entwickler bevorzugen oft einen Ansatz, bei dem sie alles über Code oder eine einfach zu bedienende **Befehlszeilenschnittstelle** (**CLI**) erledigen können. Wichtig ist dabei, dass wir eine Lösung finden, die sich in die aktuellen Arbeitsprozesse und Tools einfügt, damit unsere Nutzer nicht noch ein weiteres Tool erlernen oder ihre Arbeitsweise ändern müssen.

Der Vorschlag in unserem Szenario nutzt den Ansatz „Configuration as Code“. Entwickler können Log-Levels, Log-Ausgabe, Eigentumsrechte und Benachrichtigungskanäle im Code festlegen. Dies kann eine eigenständige YAML- oder JSON-Datei sein oder Teil einer Kubernetes-Bereitstellungsdefinition. Die Entwickler müssen diese Datei lediglich in ihrem Git-Repository einchecken. DevOps und IT-Ops können den **Pull Request** (**PR**) validieren und genehmigen, um sicherzustellen, dass alle Daten korrekt sind. Wenn eine neue Warnmeldung eingeht oder jemand Protokolle auf Abruf anfordert, ruft die neue Plattform-Engineering-Funktion die richtigen Protokolldateien für die Komponente ab, bei der ein Problem vorliegt. Anschließend kontaktiert sie anhand der Informationen zu Eigentumsverhältnissen und Benachrichtigungen das Entwicklungsteam mit einem Link oder einer Zusammenfassung der für diese Situation relevanten Protokolle. Das folgende Diagramm veranschaulicht den vorgeschlagenen End-to-End-Workflow und zeigt, wie er die Erfahrung für Entwickler, IT-Ops und DevOps verbessert:

Abbildung 3.2: Verbesserung der Erfahrung durch Configuration as Code für Entwickler, DevOps und IT-Mitarbeiter

Die vorgeschlagene Lösung behebt alle aktuellen Schwachstellen und stellt gleichzeitig sicher, dass nur die Teams, denen eine Komponente gehört, ihre Daten sehen können. Diese Lösung ist auch erweiterbar, sodass sie in Produktions- und Vorproduktionsumgebungen gleichermaßen funktioniert. Dies wäre eine zukünftige Weiterentwicklung dieser Funktion!

Schritt 4 – Ihr erster Prototyp

Wenn die vorgeschlagene Lösung akzeptiert wird, ist es an der Zeit, an einer Prototyp-Implementierung zu arbeiten. Prototypen sind eine großartige Möglichkeit, schnelles Feedback zu einer Implementierung zu erhalten, die technisch noch nicht perfekt sein muss. Für unsere Zwecke ist ein Prototyp der beste Weg, da wir überprüfen möchten, ob das Problem, das die Benutzer gelöst haben möchten, so gelöst werden kann, dass sie unsere Lösung nutzen würden.

Der erste Teil des Prototyps sollte sich auf die Schnittstelle zu dieser neuen Funktion konzentrieren, die wir entwickeln. In unserem Fall ist dies die zuvor besprochene Konfigurationsdatei. Eine wichtige Überlegung für den Prototyp ist die Entscheidung, ob die Lösung das Problem auf dem bestehenden Technologie-Stack (3-Tier-Anwendung auf Cloud-VMs) lösen soll oder ob es sich um ein Problem handelt, das wir nur lösen wollen, wenn Financial One ACME seine neue Cloud-native Implementierung einführt. Das Ziel sollte immer sein, unabhängig vom zugrunde liegenden Technologie-Stack die gleiche Entwicklererfahrung zu bieten. Bei der Implementierung können jedoch der Gewinn und der Aufwand sehr unterschiedlich sein.

Um den Prototyp für beide Technologie-Stacks zu testen, sehen Sie sich die folgenden Configuration-as-Code-Dateien an:

Tabelle 3.3: Zwei deklarative Möglichkeiten zur Implementierung der vorgeschlagenen Lösung

Beide Optionen ermöglichen es den Entwicklungsteams, alle relevanten Informationen bereitzustellen, und DevOps und IT-Ops können diese validieren:

- **Dienstdetails**: Name, Version, zu welcher Komponente er gehört
- **Eigentumsverhältnisse**: Team-Kennung, bevorzugtes Benachrichtigungstool und bevorzugter Kanal
- **Protokolle**: Protokollebene und Speicherort der Protokolle

In diesem Kubernetes-Beispiel sehen Sie auch, wie wir einige dieser Informationen in bereits standardisierten Anmerkungen wie app.kubernetes.io/name, part-of und version übergeben können. Wir sehen auch, dass Informationen wie die Protokollstufe an den Container übergeben werden können, da eine Änderung der Protokollstufe in dieser Konfigurationsdatei auch die Protokolle ändern kann, die vom bereitgestellten Container erzeugt werden!

Frühzeitiges Feedback zu diesem vorgeschlagenen Konfigurationsdateiformat kann bereits vor der eigentlichen Implementierung eingeholt werden. Dies gibt den Bereichen Entwicklung, DevOps und IT-Betrieb die Möglichkeit, zusätzliche Metadaten zu erstellen, die sie benötigen, wie z. B. die Priorität des Dienstes. Diese könnten verwendet werden, um den Eskalationsprozess zu definieren, wenn in der Produktion Problemwarnungen auftreten, oder um eine Fallback-E-Mail-Adresse anzugeben, an die E-Mail-Updates an das Team gesendet werden sollen.

Der Kern unserer vorgeschlagenen Lösung ist nicht die Konfigurationsdatei, sondern der Automatisierungsprozess, der auf Anfragen von Entwicklern reagieren kann, aber auch durch eine Warnmeldung ausgelöst werden kann. Die einfachste Lösung wäre ein einfacher Dienst, der einen REST-Endpunkt bereitstellt, der für beide Anwendungsfälle ausgelöst werden kann. Dieser Dienst muss in einer Umgebung ausgeführt werden, in der er Zugriff auf Folgendes hat:

- Das Git-Repository oder der K8s-Cluster, der „die Konfiguration” enthält
- API-Zugriff auf die vorhandene Protokollierungslösung in der Zielumgebung
- API-Zugriff auf die Benachrichtigungstools

Um mit einem minimal funktionsfähigen Prototyp zu beginnen, können wir festlegen, dass wir nur K8s, nur die Produktionsprotokollierungslösung und nur ein einziges Benachrichtigungstool, wie z. B. Slack, unterstützen. Auf diese Weise können wir den Wert anhand des Prototyps nachweisen und haben die Möglichkeit, ihn auf andere Konfigurationsdatenquellen, zusätzliche Protokollierungsumgebungen und eine längere Liste von Benachrichtigungstools auszuweiten.

Was noch fehlt, ist die Definition der REST-API. Hier sollten wir uns mit den Entwicklungs- und IT-Ops-Teams beraten, da sie die Hauptnutzer dieser API sind. Entwickler verwenden sie, um bei Bedarf Zugriff auf Protokolle anzufordern, während IT-Ops sie verwenden, um die API aufzurufen, wenn ein Problem identifiziert wird. Die folgende Tabelle zeigt eine Beispiel-REST-API-Definition für beide Anwendungsfälle:

|     |     |
| --- | --- |
| **Daten auf Abruf anfordern** | **Benachrichtigung über ein Problem** |
| GET https://logservice/request?service=fund-transfer-service&environment=prod-useast-01 | GET https://logservice/request?service=fund-transfer-service&environment=prod-useast-01&incident=PROD-1234 |

Tabelle 3.4: Beispiele für eine REST-API für den neu vorgeschlagenen Dienst

Während beide Implementierungen versuchen, die richtigen Protokolldateien für diese Dienste zu finden und sie an das richtige Team zu senden, erhält die Notify-API auch eine Vorfallreferenz, wodurch unsere Implementierung diese Informationen in die Nachricht aufnehmen kann, die an das Entwicklungsteam gesendet wird.

Im Rahmen des Prototyps dieser Lösung könnten wir noch viel mehr tun:

- Die aktuelle SDLC-Effizienz messen und lernen, wie wir die positiven Auswirkungen, die wir erzielen möchten, messen können
- Bereitstellung einer CLI, eines Chatbots oder einer Web-Benutzeroberfläche
- Erstellen einer Vorlage für ein Git-Repository für neue Dienste, um die neue Konfiguration einzubeziehen
- Erstellen von Audit-Protokollen, um zu verfolgen, wer Daten anfordert
- Bereitstellung von Metriken zur Verfolgung der Nutzung und Leistung der API
- Implementieren Sie eine ordnungsgemäße Authentifizierung, um die REST-API aufzurufen
- Implementieren Sie Ratenbegrenzungen, um Probleme beim Aufruf des Backend-Git, der K8s-API oder der Logging-Plattform-API zu vermeiden

Die Liste ließe sich fortsetzen.

Es ist nicht notwendig, all diese Punkte zu Beginn zu implementieren, um den Prototyp zu validieren und den Wert solcher Funktionen zu beweisen.

Wenden Sie grundlegende Produktmanagement-Kenntnisse auf Ihr Plattformprojekt an

Was wir bisher gelernt haben, ist, wie wir die tatsächlichen Probleme unserer Nutzer verstehen, wie wir den Nutzen einer Lösung für diese Probleme quantifizieren, wie wir eine Lösung vorschlagen und wie wir die Nutzer durch die Erstellung eines Prototyps in einen engen Feedback-Kreislauf einbinden können!

Nachdem wir nun verstanden haben, dass wir beim Aufbau einer neuen Plattform eine produktorientierte Denkweise benötigen, ist es an der Zeit, unsere Anforderungserfassung zu erweitern. Wenn wir über die Bedürfnisse der Entwickler hinausblicken und verstehen, wie sich die Plattform in die bestehenden End-to-End-Prozesse und -Tools einfügt, sind wir für die zukünftige Einführung und das Wachstum in Bezug auf die Funktionen bestens gerüstet!

Berücksichtigung bestehender Prozesse und Integration einer neuen Implementierung

Wir haben gerade darüber gesprochen, wie Sie die tatsächlichen Schwachstellen Ihrer Benutzer identifizieren und gute Kandidaten für Ihre ersten Prototypen auswählen können, um frühzeitig Feedback zu erhalten. Die Anforderungen dürfen jedoch nicht nur von Ihren Endbenutzern kommen. Wir müssen über die einfache Bereitstellung von Self-Service-Funktionen über einen Chatbot, eine Vorlagen-Datenbank oder eine neue CLI hinausdenken.

Wir müssen den gesamten Wertschöpfungsprozess betrachten und analysieren und herausfinden, wo die neuen Plattformfunktionen hineinpassen. Wir müssen sicherstellen, dass wir den aktuellen **Softwareentwicklungslebenszyklus** (**SDLC**) verstehen – den Prozess, den das Unternehmen bei der Entwicklung, Veröffentlichung, dem Betrieb und der Stilllegung neuer Software durchläuft. Es gibt einige Fragen, die wir beantworten können müssen:

- Was sind die Kriterien und Prozesse für die Einführung von Änderungen im bestehenden SDLC?
- Wie wird die Effizienz des aktuellen SDLC gemessen und wie können wir die positiven Auswirkungen messen, die wir erzielen wollen?
- Gibt es regulatorische Anforderungen für neue Tools, die wir einhalten müssen?
- Wer innerhalb des Unternehmens muss über neue Tools informiert werden oder diese genehmigen?
- Lassen sich neue Tools in bestehende Systeme für Authentifizierung, Zugriffskontrolle, Auditing, Beobachtbarkeit, Sicherheit und Ausfallsicherheit integrieren?

Der erste Schritt besteht darin, den bestehenden Prozess zu verstehen, wie wir die positiven Auswirkungen, die wir erzielen möchten, nachweisen können, welche Anforderungen für eine Erweiterung bestehen und wer die wichtigsten Entscheidungsträger sind.

Verständnis des bestehenden SDLC – „der Lebenszyklus eines Artefakts”

Da das Ziel des Platform Engineering darin besteht, Plattformfunktionen bereitzustellen, die die Art und Weise verbessern und verändern, wie Entwickler bestimmte Aufgaben neben dem SDLC ausführen, ist es wichtig, den aktuellen SDLC in der Organisation zu verstehen. Insbesondere in großen Unternehmen ist es sehr wahrscheinlich, dass es nicht nur einen Prozess gibt, sondern viele, die sich im Laufe der Jahre entwickelt haben. Es ist auch sehr wahrscheinlich, dass nur wenige – wenn überhaupt – den aktuellen SDLC von der ersten Anforderung und Erstellung des Artefakts bis zum Betrieb der neuen Software in der Produktion kennen, bis sie ersetzt oder außer Betrieb genommen wird. Es ist sehr wichtig, nicht den Fehler zu machen, anzunehmen, dass wir – oder eine einzelne Person – den bestehenden End-to-End-Prozess kennen. Selbst Ingenieure, die seit vielen Jahren für Unternehmen arbeiten, leben oft in ihrer eigenen Blase und haben nur ein begrenztes Verständnis dafür, was typischerweise von der Entstehung einer neuen Idee bis zur Auslieferung, zum Betrieb und schließlich zur Stilllegung des Codes geschieht.

Das Artefakt-Lebenszyklus-Experiment – von der Idee über den Git-Commit bis zur Produktion!

Eine einfache Methode, um den End-to-End-Prozess zu lernen, ist ein kleines Experiment.

Als Kind waren Sie wahrscheinlich genauso fasziniert von Flüssen (kleinen oder großen) wie ich. Sicherlich haben Sie schon einmal ein Stück Holz oder einen kleinen Ast ins Wasser geworfen und dann beobachtet, wie das Wasser ihn davontrug. Wahrscheinlich sind Sie am Fluss entlanggelaufen, um zu sehen, wie dieser Ast seinen letzten Lebenszyklus-Schritt erreichte: das Meer! Denn dort landet letztendlich alles Wasser. Als Kinder hatten wir keine Möglichkeit, diesem Ast bis zum Ozean zu folgen. Als Ingenieure haben wir jedoch die Möglichkeit, den gesamten Lebenszyklus eines Artefakts zu verfolgen: von der Entstehung der Idee (ein Ticket in einem Requirements-Engineering-Tool) über den ersten Git-Commit durch einen Entwickler bis hin zur Bereitstellung, Aktualisierung oder Ersetzung des Artefakts in der Produktion.

Wir haben zwei Möglichkeiten, diesen Artefakt-Lebenszyklus zu verstehen. Erstens können wir einen bestehenden Dienst oder eine bestehende Funktion auswählen und eine Forensik durchführen, indem wir alle Tickets, Git-Commits, Pipeline-Läufe, Testberichte, E-Mails, Änderungsanforderungen und Vorfallberichte analysieren und so die Prozesse, Tools und beteiligten Personen kennenlernen!

Ein anderer Ansatz besteht darin, eines der Entwicklungsteams zu bitten, eine „Demo“- oder „nicht beeinträchtigende“ Funktion zu erstellen. Angesichts der Beliebtheit von Feature-Flagging könnte dies eine einfache Funktion hinter einem Flag sein, die einen kleinen Aspekt der Laufzeit des Artefakts verändert. Der Vorteil dabei ist, dass dies kein Risiko für die Produktion darstellt, uns aber ermöglicht, alles über den aktuellen SDLC zu erfahren und daraus den aktuellen Lebenszyklus von Artefakten in dieser Organisation abzuleiten!

Einblicke in den Lebenszyklus von Artefakten

Ich habe mehrere dieser Workshops zum Thema „Den Lebenszyklus eines Artefakts verstehen” mit verschiedenen Organisationen auf der ganzen Welt durchgeführt. Das Ergebnis waren viele Einblicke und Erkenntnisse über die Menschen, Prozesse und Tools. Dazu gehörten unter anderem die folgenden Punkte:

- Welche Aufgaben waren von der Anforderung bis zum ersten Git-Commit bis zur Produktionsbereitstellung beteiligt?
- Wer war beteiligt – die verschiedenen Teams, die an der Entwicklung, dem Testen, der Validierung und der Förderung von Änderungen von der Entwicklung bis zur Produktion beteiligt waren
- Welche Tools wurden dabei verwendet und gab es möglicherweise unterschiedliche Tools für dieselbe Aufgabe in verschiedenen Umgebungen?
- Welche Aufgaben entlang des Prozesses manuell und welche bereits automatisiert waren
- Abhängigkeiten von anderen Aufgaben oder Teams, um die Änderung in Richtung Produktion voranzutreiben
- Die Zeit, die für jede Aufgabe benötigt wurde, die Gesamtzeit, die Wartezeit zwischen den Aufgaben und mehr

Mit diesen Erkenntnissen können Sie auch eine Visualisierung des gesamten SDLC oder des gesamten Artefakt-Lebenszyklus erstellen. Eine solche Visualisierung wird sehr nützlich sein, sobald wir Diskussionen darüber führen, wie sich die Fähigkeiten unserer Plattform auf die derzeit bestehenden Prozesse auswirken werden:

Abbildung 3.3: Verständnis des Lebenszyklus eines Software-Artefakts

Der Lebenszyklus eines Artefakts beschränkt sich nicht auf die anfängliche Bereitstellung

Während Initiativen im Bereich Platform Engineering oft darauf abzielen, die anfängliche Einbindung oder Lieferung von Softwarekomponenten zu verbessern, dürfen wir uns nicht darauf beschränken. Aus diesem Grund ist der Begriff „Lebenszyklus eines Artefakts” eine gute Alternative, da der Lebenszyklus nicht mit dem anfänglichen Entwicklungsprozess endet. Der Lebenszyklus eines Artefakts umfasst auch den Betrieb, die Veröffentlichung von Updates, die Wartung oder sogar den Austausch oder die Außerbetriebnahme dieses Artefakts.

In unserem ersten Beispiel von Financial One ACME haben wir über eine operative Lebenszyklusphase gesprochen. Diese umfasste den mühsamen Prozess für Entwicklungsteams, Zugriff auf Log-Dateien in der Produktion zu erhalten, um aktuelle Probleme zu triagieren. Die folgende Abbildung visualisiert diese Lebenszyklusphase und diesen Prozess!

Abbildung 3.4: Lebenszyklus der Incident Response beim Zugriff auf Protokolle

Anforderungen der beteiligten Teams und bestehender Prozesse

Bei unserer Übung zum Verständnis des Flusses eines Artefakts während des gesamten Lebenszyklus haben wir viel über die beteiligten Teams, vorhandenen Tools und Prozesse gelernt. Wir haben auch erfahren, welche Tools unsere zukünftigen Plattformfunktionen möglicherweise integrieren müssen, mit welchen Teams wir zusammenarbeiten müssen und – falls wir bestehende Tools ersetzen oder integrieren – was wir tun müssen, um die Funktionen der aktuellen Tool-Implementierung nicht zu beeinträchtigen.

Hier sind einige Beispiele für diese Erkenntnisse:

- **Single Sign-On (SSO)**: Jedes Tool muss in das zentrale SSO integriert werden.
- **Sicherheit**: Jedes Tool muss die Sicherheitsrichtlinien für die Software-Lieferkette erfüllen
- **Auditing**: Jedes Tool muss spezifische Zugriffsprotokolle erstellen.
- **Service Level Agreements (SLAs)**: Jedes kritische Tool muss die unternehmensweit definierten SLAs zur Verfügbarkeit kritischer Dienste einhalten.

Bisher haben wir gelernt, wie wichtig es ist, den gesamten Prozess und Lebenszyklus von Software-Artefakten zu verstehen. Es ist wichtig zu wissen, welche Teams beteiligt sind und welche bestehenden Prozesse wir durchlaufen müssen, wenn wir ein neues Tool einführen. Wir haben auch zusätzliche zukünftige Bereiche kennengelernt, in denen eine Plattform-Engineering-Fähigkeit erhebliche Verbesserungen für die Softwarebereitstellung und den Lebenszyklus von Artefakten bieten kann!

Einführung von Lebenszyklusereignissen – Messung und Verbesserung der Effizienz des SDLC

Wir haben bereits über das Konzept des Artefakt-Lebenszyklus gesprochen. Ein Artefakt durchläuft in der Regel eine Reihe von Phasen: Anforderung akzeptiert, Implementierung gestartet, Pull-Anforderung, Artefakt erstellt, Sicherheitsscan abgeschlossen, Test abgeschlossen, Build validiert, Artefakt befördert, Bereitstellung abgeschlossen, Funktion freigegeben, Problem erkannt, Konfiguration geändert, Problem behoben und Artefakt außer Betrieb genommen. Auch wenn jede Organisation leicht unterschiedliche Lebenszyklusphasen hat, lässt sich dies gut anhand der DevOps-Unendlichkeitsschleife veranschaulichen. Um den Lebenszyklus eines Artefakts nachzuverfolgen, empfehlen wir Ihnen, jeden Schritt als Lebenszyklusereignis zu protokollieren. Die folgende Abbildung zeigt ein Beispiel für solche Ereignisse und einige der Metadaten, die die beteiligten Tools und Teams hinzufügen sollten, um den gesamten Ablauf eines Artefakts von den anfänglichen Anforderungen bis zum Betrieb besser zu verstehen:

Abbildung 3.5: Der SDLC und seine Artefakt-Lebenszyklusereignisse

Die Idee der Lebenszyklusereignisse ist nicht neu. Viele Unternehmen setzen dieses Konzept auf unterschiedliche Weise um, beispielsweise indem sie am Anfang und am Ende ihrer CI/CD-Pipelines Log-Ausgaben hinzufügen, darunter Metadaten wie Zeitstempel, Git-Repository, Pipeline, erstelltes Artefakt und Erfolgsstatus. Die Continuous Delivery Foundation hat an der **CDEvents** \[3\]-Spezifikation gearbeitet, die ein Vokabular von Ereignissen definiert, das Tools eine interoperable Kommunikation ermöglicht. CDEvents ist ein guter Ausgangspunkt, der erweitert werden kann, um den gesamten Lebenszyklus von Artefakten abzudecken, wie zuvor vorgeschlagen.

Die Standardisierung von Ereignissen wie diesen hat viele Vorteile:

- **Jedes Artefakt kann über seinen gesamten Lebenszyklus hinweg verfolgt werden**: So lassen sich beispielsweise Fragen beantworten, wer an der Erstellung eines Artefakts beteiligt war!
- **Verwaltung von Releases**: Welche Version eines Release-Artefakts wurde wann von wem in welcher Umgebung bereitgestellt?
- **Die Lebenszyklusphasen können gemessen werden, wodurch wir DORA-Metriken erhalten**: Wie lange dauert es von der ersten Anforderung bis zur ersten Bereitstellung (Vorlaufzeit), wie viele Bereitstellungen haben wir (Bereitstellungshäufigkeit), wie viele Bereitstellungen führen zu einem Problem in der Produktion (Bereitstellungsausfallrate) und wie lange dauert es, ein Problem in der Produktion zu beheben (Zeit bis zur Wiederherstellung des Dienstes)?
- **Compliance**: Damit können wir feststellen, ob bei einigen Artefakten wichtige Schritte wie Sicherheitsscans, Ausfallsicherheitstests und mehr übersprungen wurden.
- **Interoperabilität**: Hier wird festgelegt, ob wir Jenkins oder GitHub Actions zum Erstellen von Artefakten verwenden. Wenn alle Tools die gleiche Art von Ereignissen generieren, behalten wir die Kontrolle über den Lebenszyklus.

Bevor Sie sich daran machen, Ihre Lebenszyklusereignisse zu definieren, sollten Sie sich die bestehenden Initiativen in den Open-Source-Communities sowie die Aktivitäten der Anbieter in den Bereichen Bereitstellung, Observability und **Application Lifecycle Management** (**ALM**) ansehen. Es besteht kein Grund, das Rad neu zu erfinden, da derzeit Standards entwickelt werden!

Präsentation des Wertversprechens zur Verbesserung des bestehenden SDLC/DORA

Das Verständnis des bestehenden SDLC und die Visualisierung des Lebenszyklus eines Artefakts liefern wertvolle Erkenntnisse für unsere laufenden Plattform-Engineering-Initiativen. Dies wird auch für alle Mitglieder der Engineering-Organisation aufschlussreich sein, da viele von ihnen wahrscheinlich noch nie einen Überblick darüber hatten, wo der aktuelle Prozess Verbesserungspotenzial bietet.

Die gewonnenen Erkenntnisse ermöglichen es uns, an einem Wertversprechen zu arbeiten, das nicht nur den Alltag der Entwicklungsteams, sondern idealerweise auch vieler anderer Teams entlang des SDLC verbessern wird. Deshalb ist es so wichtig, den aktuellen Prozess zu verstehen und zu messen – so können wir nicht nur eine neue Lösung vorschlagen, sondern auch die Verbesserungen anhand von harten Fakten präsentieren, wie z. B. die Verbesserung der Vorlaufzeit, der Bereitstellungshäufigkeit, der Bereitstellungsausfallrate oder der Zeit bis zur Wiederherstellung des Dienstes (unsere geliebten DORA-Kennzahlen).

Wie würde dies in Bezug auf alles, was wir bisher gelernt haben, in unserem Anwendungsfall für den Log-Zugriff für Financial One ACME aussehen? Unser ursprünglicher Anwendungsfall konzentrierte sich nur auf die Verbesserung des Zugriffs auf Logs im Falle eines Fehlers in der Produktion. Nachdem wir den gesamten End-to-End-Prozess, alle beteiligten Teams sowie die bestehenden Prozesse, Tools und organisatorischen Anforderungen verstanden hatten, konnten wir die folgende Lösung und das folgende Wertversprechen vorschlagen:

|     |
| --- |
| **Vorschlag**: Automatisierung der Beobachtbarkeit als nicht-funktionale Softwareanforderung |
| **Wertversprechen**: Verbesserung der DORA-Metriken, Reduzierung der kognitiven Belastung und Skalierung von Best Practices |
| **KPIs und betroffene Teams**:<br><br>Verbesserung der Zeit bis zur Wiederherstellung des Dienstes um 50 % durch automatische Weiterleitung relevanter Observability-Daten aus der Produktion an das Entwicklungsteam. Dadurch entfällt die manuelle Erfassung und Weiterleitung von Protokollen für DevOps und IT-Ops.<br><br>Verbesserung der Vorlaufzeit um 50 % durch Automatisierung des Prozesses der Erfassung und Analyse von Observability-Daten (Protokolle, Metriken, Traces und Ereignisse) in früheren Phasen des Lebenszyklus (Entwicklung, Test). Die Analyse verbessert und automatisiert die Validierung neuer Build-Artefakte und reduziert somit den manuellen Aufwand für Qualitätsingenieure.<br><br>Reduzieren Sie die Fehlerquote bei der Produktionsbereitstellung um 50 %, indem Sie Probleme in früheren Umgebungen automatisch erfassen, indem Sie die Erkennung häufiger Probleme (neue kritische Protokolle, Ausnahmen, Verlangsamung der Anwendung usw.) auf der Grundlage von Observability-Daten automatisieren. |
| **Übergeordnete Benutzerabläufe und Zusammenarbeit**:<br><br>Als Entwicklungsteam übernehme ich eine Observability-as-Code-Konfigurationsdatei, die Informationen über die Protokollquelle (für die automatische Erfassung), die Eigentumsverhältnisse (für die automatische Weiterleitung) und wichtige Protokollmuster (für die automatische Validierung und automatische Warnmeldungen) enthält.<br><br>Als Quality-Engineering-Team arbeite ich mit anderen zusammen und erweitere die Protokollmuster, um im Rahmen der Testergebnisanalyse Regressionen automatisch zu erkennen.<br><br>Als DevOps-Team arbeite ich mit anderen zusammen und erweitere die Regeln zur Erkennung von Protokollmustern auf der Grundlage von Erfahrungen und Mustern, die in anderen Entwicklungsteams beobachtet wurden.<br><br>Als IT-Ops-Team arbeite ich mit anderen zusammen, validiere korrekte Protokollquellen und erweitere die Erkennung von Produktionsproblemen auf der Grundlage relevanter Protokollmuster, die von der Entwicklung und DevOps definiert wurden. |

Tabelle 3.5: Formulierung eines Vorschlags für unsere Lösung in einem präsentablen Layout

Ein klarer Vorschlag und ein klares Wertversprechen

Die Erfolgschancen sind höher, wenn wir die Vorteile unserer Plattform klar artikulieren können.

Nachdem wir nun gelernt haben, wie wir unsere Vorschläge so gestalten können, dass sie alle Beteiligten des Software-Lieferungs- und Artefakt-Lebenszyklus einbeziehen, ist es an der Zeit, darüber nachzudenken, wie wir die vorgeschlagene Lösung gestalten sollten.

Entwurf der Infrastrukturarchitektur

An dieser Stelle haben wir unseren Vorschlag vorgestellt. Sobald wir die erste Zustimmung aller beteiligten Teams und Sponsoren aus der Geschäftsleitung erhalten haben, ist es an der Zeit, zur nächsten Phase überzugehen: Wir müssen über die Gestaltung der Lösung nachdenken und darüber, wie sie sich in die zugrunde liegende Infrastruktur einfügt, um alle nicht-funktionalen Anforderungen unserer Organisation zu erfüllen: Ausfallsicherheit, Verfügbarkeit, Überprüfbarkeit, Sicherheit, obligatorische Integrationen und so weiter.

Wir dürfen zwar von Anfang an nicht übertreiben, aber es ist wichtig, sich aller Anforderungen bewusst zu sein, die sich auf unsere Infrastrukturentscheidungen auswirken. Hier sind einige Fragen, die wir beantworten müssen:

- Wie, wer und wo werden wir die Plattform bereitstellen, aktualisieren und betreiben?
- Gibt es organisatorische Anforderungen, die den Betrieb auf einer bestimmten Infrastruktur erfordern?
- Gibt es die Anforderung, unsere Lösung in mehreren geografischen Regionen oder sogar über mehrere Infrastrukturanbieter hinweg zu betreiben?
- Gibt es Infrastrukturanforderungen für den Zugriff auf und die Verbindung mit anderen Systemen?
- Wie viele Benutzer muss unsere Lösung unterstützen können?
- Wie lauten unsere SLAs für die Infrastruktur und für Endnutzer?
- Wie würden wir skalieren?

In [Kapitel 4](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/4) werden wir uns eingehender mit der Architektur des Plattformkerns befassen und dabei Kubernetes als einheitliche Orchestrierungsschicht verwenden. Unabhängig davon, ob Sie sich letztendlich für Kubernetes als zugrunde liegende Abstraktionsschicht entscheiden oder etwas anderes verwenden, müssen Sie diese Fragen beantworten, da sie sich auf einige Ihrer Entscheidungen auswirken werden. Lassen Sie uns also einige Antworten darauf finden, wie sich dies auf unsere Architekturentscheidungen auswirken würde!

Vermeiden Sie den Elfenbeinturm-Ansatz – wir sind Eigentümer der Plattform!

Bevor wir die Fragen zu den Auswirkungen auf die Infrastruktur beantworten, wollen wir uns mit der grundlegenden Frage der Eigentumsverhältnisse befassen:

Wir sind Eigentümer der Plattform!

Das Plattform-Engineering-Team ist Eigentümer der Plattform als End-to-End-Produkt!

Da unsere Plattform Funktionen bereitstellt, die die Bereitstellung und den Betrieb von Softwarekomponenten vereinfachen, muss es unser oberstes Ziel sein, unsere eigenen Best Practices zu befolgen und die Plattform idealerweise mit denselben Golden Paths und Self-Service-Funktionen bereitzustellen, die wir unseren Endbenutzern zur Verfügung stellen möchten. Einige Unternehmen bezeichnen dies als „Customer Zero“ oder „Drink your own champagne“. Wenn wir diesem Mantra nicht folgen und einfach nur etwas entwickeln, es über den Zaun werfen und hoffen, dass jemand anderes es betreibt, verfehlen wir den Sinn einer modernen Produktphilosophie für die Plattformentwicklung.

Wir müssen die gleichen Probleme bei der Softwarebereitstellung und dem Betrieb spüren, die unsere Benutzer derzeit spüren. Dies wird für uns eine noch größere Motivation sein, Plattformfunktionen zu entwickeln, die unser Leben als Softwareteams erleichtern.

Wir müssen einen Elfenbeinturm-Ansatz vermeiden, bei dem wir Best Practices von oben nach unten durchsetzen, ohne diese Best Practices selbst zu befolgen. Wenn wir dies tun, könnten wir am Ende einen berühmten Reddit-Beitrag erhalten, ähnlich dem, der am Anfang dieses Kapitels erwähnt wurde: „Wir haben Monate damit verbracht, diese Plattform zu entwickeln. Die Entwickler hassen sie! Helft mir zu verstehen, warum!“

Kehren wir nun zurück und beantworten wir einige der zuvor aufgeworfenen Fragen zur Infrastruktur, die unsere Architekturentscheidungen beeinflussen könnten.

Organisatorische Einschränkungen – bestehende Infrastrukturanforderungen?

Wir müssen herausfinden, ob es Einschränkungen bei der Nutzung bestehender Infrastrukturdienste gibt. In Unternehmen bestehen wahrscheinlich Verträge mit Infrastruktur- oder Cloud-Anbietern. Wenn solche Einschränkungen bestehen, spielen sie eine Rolle bei unseren Entscheidungen – müssen wir beispielsweise unseren eigenen K8s-Cluster vor Ort betreiben oder können wir einen Managed Service eines Anbieters nutzen? Wenn wir an einen bestimmten Cloud-Anbieter gebunden sind, bedeutet dies auch, dass wir möglicherweise auf dessen Serviceangebote (Speicher, Datenbank, Caches und mehr) beschränkt sind.

In diesem Zusammenhang möchten wir auch die Zugriffskontrolle, den Datenverkehr und die Kostenbeschränkungen untersuchen!

Es ist wichtig, alle diese organisatorischen Einschränkungen zu kennen, bevor wir die Entscheidungen über Infrastruktur und Architektur endgültig treffen!

Konnektivitätsbeschränkungen – Interoperabilitätsanforderungen?

Die Funktionen unserer Plattform erfordern die Verbindung und Interaktion mit anderen bestehenden Systemen. Dies reicht vom Zugriff auf SSO, Ihr Git-Repository, CI/CD-Pipelines, Observability, Orchestrierungsebenen, Cloud-APIs und mehr.

Je nachdem, wo die Plattform betrieben wird – also vor Ort oder in der Cloud – hat dies Auswirkungen darauf, wie die Plattform mit all diesen Tools verbunden werden kann oder wie diese Tools wieder mit der Plattform verbunden werden können.

Wir müssen uns Gedanken über Firewalls, Pull- versus Push-Konnektivität sowie API-Ratenbeschränkungen und -Kosten machen, da wir eine robuste Interoperabilität zwischen all diesen Systemen sicherstellen müssen.

Es ist wichtig, alle diese Konnektivitätsbeschränkungen zu kennen, bevor wir endgültige Entscheidungen über die Infrastruktur und den Standort unserer Plattform in Bezug auf alle anderen Systeme treffen, mit denen wir uns verbinden müssen.

Ausfallsicherheitsbeschränkungen – SLAs und andere nicht-funktionale Anforderungen?

Das Ziel unserer Plattform ist es, die tägliche Arbeit für eine Vielzahl interner Benutzer (Entwickler, DevOps, IT-Ops, Qualitätsingenieure, App-Support und mehr) zu verbessern. Das bedeutet, dass unsere Plattform jederzeit verfügbar sein und funktionieren muss, wenn unsere Benutzer sie benötigen. In globalen Unternehmen kann dies operative Ausfallsicherheit und hohe Verfügbarkeit rund um die Uhr bedeuten. Wenn die Plattform nicht verfügbar ist, können unsere Ingenieure ihre wichtigen Aufgaben nicht ausführen, wie z. B. die Veröffentlichung einer neuen Version einer Software, das Beheben eines Sicherheitsproblems oder die Skalierung ihrer Workloads, um der gestiegenen Nachfrage der Endnutzer gerecht zu werden!

Daher müssen wir die nicht-funktionalen Anforderungen an unsere Plattform verstehen, wie zum Beispiel die folgenden:

- Verfügbarkeit – zum Beispiel von 9 bis 17 Uhr in einer einzigen Zeitzone oder von Montag bis Freitag in allen Zeitzonen
- Benutzererfahrung – beispielsweise muss die akzeptable Leistung eines Systems für Endbenutzer gewährleistet sein, wobei bis zu 100 Ingenieure gleichzeitig die Funktionen der Plattform nutzen können

Diese nicht-funktionalen Anforderungen bedeuten auch, dass wir darüber nachdenken müssen, wie wir nach oben und unten sowie nach außen und innen skalieren. Wir müssen definieren, ob wir unsere Plattform zentral bereitstellen, damit sie alle Regionen rund um den Globus bedient, oder ob wir die Plattformkomponenten in den verschiedenen Regionen bereitstellen müssen, um die Anforderungen an die Benutzererfahrung hinsichtlich einer akzeptablen Leistung besser zu erfüllen.

Dynamische, horizontale oder vertikale Skalierung ist ein Thema, auf das wir später in diesem Buch näher eingehen werden, wenn wir uns mit der Architektur des Kerns der Plattform mit Kubernetes als einheitlicher Schicht befassen.

Nachdem wir nun Antworten auf all diese Fragen haben, können wir fundiertere Entscheidungen über die Infrastruktur und die Architektur unserer Plattform und ihre Funktionen treffen!

Erforschung von Multi-Cloud, Multi-SaaS und der Fragmentierung von Funktionen

Wenn wir uns mit der Fragmentierung von Funktionen und deren Interaktion mit der Platform as a Service und ihrer Skalierbarkeit befassen, fällt uns eine Sache als wichtige Funktion ein, die auf den ersten Blick vielleicht nicht ganz offensichtlich ist: Der IDP sollte nicht nur Multi-User, sondern auch Multi-Tenant sein.

Multi-Tenancy und Eigentumsrechte als Funktion unserer Plattform

Multi-Tenancy wird normalerweise im Zusammenhang mit einer Produktionsanwendung betrachtet. Unser Plattformkunde Financial One ACME möchte beispielsweise sein Single-Tenant-Produkt in ein Multi-Tenant-Produkt umwandeln. Dies wird ihm helfen, höhere Gewinnmargen zu erzielen, den Betriebsaufwand zu senken und eine Reihe weiterer geschäftlicher Vorteile zu erzielen. Die gleiche Datentrennung, die innerhalb einer Produktionsanwendung in einer stark regulierten Branche besteht, sollte auf jeder Ebene des Anwendungslebenszyklus, einschließlich der IDP, vorhanden sein. Dies ist nicht nur eine bewährte Vorgehensweise, sondern möglicherweise auch notwendig, um bestimmte Sicherheits- und Compliance-Zertifizierungen zu erhalten.

Da Produktionsdaten in Tests gelangen können, trägt die Gewährleistung, dass die Standardzugriffsebene jedes Benutzers auf der Plattform standardmäßig so restriktiv wie möglich ist, dazu bei, dass die Oberfläche, über die diese Daten zugänglich sind, so klein wie möglich ist, falls sie an einem unerwünschten Ort landen sollten. Darüber hinaus stellt die vollständige Isolierung der Mandantenfähigkeit sicher, dass die Geheimnisse, die jedes Team möglicherweise benötigt, voneinander isoliert sind, wodurch weitere Risiken gemindert werden.

Die Vorteile der Sicherheit und Mandantenfähigkeit der Plattform werden wir in [Kapitel 7](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/7) näher beleuchten. Es ist jedoch wichtig zu beachten, dass die Mandantenfähigkeit auch dazu beitragen kann, die kognitive Belastung der Benutzer der Plattform zu verringern. Wir werden dies in [Kapitel 6](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/6), „Entwickeln für Entwickler und deren Self-Service“, ausführlicher behandeln.

Mandantenfähigkeit bedeutet auch, dass jede architektonische Entscheidung, die wir treffen – jedes Tool, das wir in unsere Plattform integrieren – ebenfalls die Mandantenfähigkeit unterstützt. Nehmen wir als Beispiel die Beobachtbarkeit: Wenn wir Protokolle, Metriken, Traces und Ereignisse für die Kernplattform sowie für die von unseren Benutzern bereitgestellten Anwendungen erfassen, müssen wir sicherstellen, dass diese Beobachtbarkeitsdaten in einzelne Mandanten „aufgeteilt” werden können. Wir haben bereits besprochen, dass unsere Plattform Eigentumsrechte als Metadaten enthalten muss, wenn wir unsere Kernplattform bereitstellen und wenn wir Vorlagen für die Self-Service-Einbindung neuer Anwendungen bereitstellen. Betrachten wir ein Beispiel für eine Bereitstellungsdefinition, die mit Metadaten zu Eigentumsrechten angereichert ist, wie im Abschnitt „Überwindung der Plattformkomplexität“ beschrieben. Diese Metadaten zu Eigentumsrechten können verwendet werden, um die Zugriffskontrolle auf alle für diese Bereitstellung erfassten Daten durchzusetzen, einschließlich der Verwendung für Filter bei der Abfrage Ihrer Metriken oder Traces:

|     |     |
| --- | --- |
| **service-abc.yaml (Kubernetes-Bereitstellung)** | **Verwendung von Eigentumsmetadaten mit Observability!** |
| apiVersion: apps/v1<br><br>kind: Deployment<br><br>Metadaten:<br><br>&nbsp; name: fund-transfer-service<br><br>&nbsp; namespace: prod-useast-01<br><br>Spezifikation:<br><br>&nbsp; …<br><br>&nbsp; Vorlage:<br><br>&nbsp;   Metadaten:<br><br>&nbsp;     Anmerkungen:<br><br>&nbsp;       owner.team: dev-team-backend<br><br>&nbsp;       app.kubernetes.io/name: fund-transfer-service<br><br>&nbsp;       app.kubernetes.io/part-of: Backend-Services<br><br>&nbsp;      app.kubernetes.io/version: 2.34<br><br>&nbsp;   …<br><br>&nbsp;   Spezifikation:<br><br>&nbsp;     Container:<br><br>&nbsp;     - name: fund-transfer<br><br>&nbsp;       image: "financeoneacme/fund-transfer:2.34"<br><br>&nbsp;   … | Die Anmerkungen können als Filter in PromQL-Abfragen verwendet werden, zum Beispiel:<br><br>sum(rate(container_cpu_usage_seconds_total{annotation_name="owner.team", annotation_value="dev-team-backend"}\[5m\])) |

Tabelle 3.6: Wie Metadaten zur Eigentümerschaft definiert und verwendet werden können

Diese Eigentumsinformationen können verwendet werden, um den Teams, denen diese Komponente gehört, Zugriff auf Observability-Daten zu gewähren. So können wir die Daten nach Mandanten trennen und gleichzeitig den Administratoren unserer Plattform oder den Eigentümern gemeinsamer Dienste die Analyse von Daten ermöglichen, die über einen einzelnen Mandanten hinausgehen. Dies ist auch eine wichtige Funktion, da es sehr wahrscheinlich ist, dass wir auf mandantenübergreifende Probleme stoßen werden. Daher ist es für die Identifizierung und Behebung von Problemen von entscheidender Bedeutung, dass alle Observability-Daten im richtigen Kontext verfügbar sind.

Datenpipelines – egal ob mit OpenTelemetry Collectors oder kommerziellen Produkten – können diese Metadaten auch nutzen, um die Observability-Daten an verschiedene Backend-Speicher zu senden und sogar die Speicherung dieser Daten basierend auf der Mandantschaft zu trennen!

Das Thema Eigentumsrechte und Beobachtbarkeit wird in den folgenden Kapiteln ausführlicher behandelt, da es ein wichtiger Faktor für viele Funktionen und Eigenschaften unserer Plattform ist!

Überlegungen zum Betrieb auf Multi-X

Im Abschnitt „Organisatorische Einschränkungen” haben wir darüber gesprochen, dass es wichtig ist, alle bestehenden Einschränkungen zu verstehen, z. B. ob wir geschäftliche oder regulatorische Verpflichtungen haben, Multi-Cloud, Multi-SaaS oder – wie manche es nennen – **Hybrid Cloud** zu betreiben.

Wenn Financial One ACME auf verschiedenen globalen Märkten verkaufen möchte, wird es wahrscheinlich erforderlich sein, unsere Software aus der lokalsten Region eines Cloud-Anbieters heraus zu betreiben – zum Beispiel EU-WEST oder APAC-SOUTHEAST. Es könnte sogar erforderlich sein, sie über mehrere Regionen oder mehrere verschiedene Anbieter hinweg zu betreiben, um vertragliche Verpflichtungen hinsichtlich hoher Verfügbarkeit und Ausfallsicherheit zu erfüllen und gleichzeitig die Standards einzuhalten, denen diese Unternehmen unterliegen.

Aus Wettbewerbs- oder regulatorischen Gründen ist es auch möglich, dass einige Cloud- oder SaaS-Anbieter überhaupt nicht genutzt werden können. Warum ist das so? Nun, wenn ein potenzieller Kunde von Financial One ACME einen dieser Cloud-Anbieter als Konkurrenten betrachtet oder wenn ein Anbieter bestimmte regulatorische Anforderungen nicht erfüllt, könnte er unsere Software-Services nicht erwerben.

Das klingt nach vielen Einschränkungen, die uns nicht viel Auswahl lassen, nicht wahr? Glücklicherweise gibt es Lösungen für dieses Problem: In den kommenden Kapiteln werden wir viel über Kubernetes als zugrunde liegende Abstraktionsschicht sprechen. Auf dieser Abstraktionsschicht aufzubauen, wird es für uns einfacher – aber nicht völlig problemlos – machen, Workloads in verschiedene Regionen und zu verschiedenen Cloud-Anbietern zu verlagern.

Da unsere Plattform und alle ihre Komponenten nicht ausschließlich auf Kubernetes laufen, sondern auch andere Dienste umfassen, ist es wichtig, eine gründliche Checkliste zu erstellen, um Architekturentscheidungen zu vermeiden, die in Zukunft nur schwer zu ändern sind. Wenn unsere Plattform beispielsweise Anforderungen an einen Dokumentenspeicherdienst hat, können wir entweder entscheiden, eine Dokumentendatenbank wie MongoDB auf Kubernetes zu betreiben, oder ein bestehendes SaaS-Angebot eines der Cloud-Anbieter auswählen. Die Wahl eines Managed Service reduziert den Aufwand auf unserer Seite, aber wir müssen sicherstellen, dass jeder potenzielle SaaS- -Anbieter, der einen Dokumentenspeicherdienst unterstützt, die gleiche Schnittstelle, ähnliche Leistungsmerkmale und eine ähnliche Kostenstruktur bietet. Wenn wir die falsche Architekturentscheidung treffen, könnte es schwierig sein, Folgendes zu tun:

- Änderung unserer Implementierung, damit sie eine andere API unterstützt
- Auswirkungen auf die Leistung und Skalierbarkeit verschiedener Anbieter zu haben
- Erhöhung der Gesamtbetriebskosten unserer Software

Zentralisierte und dezentralisierte Plattformfunktionen

In den folgenden Kapiteln werden wir weitere Beispiele für den Betrieb unseres IDP und seiner Komponenten entweder als zentraler Dienst, pro Umgebung, pro Region oder sogar pro Mandant (falls dies erforderlich ist) vorstellen. Ihre Erkenntnisse über die organisatorischen Anforderungen werden diese Entscheidungen beeinflussen, z. B. ob unsere Kunden verlangen, dass sie in bestimmten Regionen betrieben werden, oder ob sie einen bestimmten Cloud-Anbieter nicht nutzen dürfen.

Die Zentralisierung von Komponenten hat den großen Vorteil, dass sie einfacher zu verwalten sind. Denken Sie an ein zentrales Continuous-Integration-System (**CI**) wie Jenkins oder GitLab, das Pipelines ausführt, die durch Pull-Anfragen zum Erstellen neuer Artefakte ausgelöst werden. Eine zentrale Instanz eines solchen CI-Systems ist einfacher zu bedienen, zu überwachen, zu sichern und zu verwalten. Auf der anderen Seite bedeutet dies, dass alle unsere Benutzer dasselbe System nutzen, was leicht zu Engpässen führen kann. Das zentrale System muss außerdem Zugriff auf alle Zielumgebungen haben, die sich in verschiedenen geografischen Regionen oder sogar bei anderen Cloud-Anbietern befinden können. Die Anzahl der Abhängigkeiten von diesen Cloud-Umgebungen steigt mit jedem neuen Team, das seine Anwendung einführt, oder mit jedem neuen Kunden von Financial One ACME, der eine spezielle Bereitstellung unserer Software verlangt!

Dezentrale Komponenten haben den Vorteil, dass sie die Prozesse der Datenerfassung, -speicherung und des Datenzugriffs automatisch kapseln können. Diese Komponenten werden nur von den Teams in den jeweiligen Regionen oder Umgebungen verwendet, was das Potenzial für Muster wie „Noisy Neighbors“ begrenzt, auf die wir in [Kapitel 6](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/6) näher eingehen werden. Der Nachteil eines dezentralen Ansatzes besteht darin, dass es schwieriger ist, diese Komponenten zu betreiben, zu beobachten, zu sichern und zu verwalten, da die Anzahl der Komponenten mit jeder neuen Umgebung zunimmt. Automatisierung kann hier helfen, aber wir dürfen die zusätzliche Komplexität nicht unterschätzen. Denken Sie nur daran, was passiert, wenn eine Schwachstelle in unserem CI-System gefunden wird. Anstatt sie einmal in einem zentralen System zu beheben, müssen wir jede einzelne Instanz in allen unseren dezentralen Diensten patchen!

Nachdem wir nun gelernt haben, dass Multi-X – darunter Multi-Tenancy, Cloud und SaaS – Auswirkungen auf unsere Architekturentscheidungen haben wird, ist es wichtig, ein gutes Gleichgewicht zwischen Aufwand, Nutzen und externen Anforderungen an unsere Plattform zu finden. Mit all dem Wissen, das wir bisher gewonnen haben, können wir eine gute Referenzarchitektur für unsere Plattform entwickeln, die wir im letzten Teil dieses Kapitels besprechen werden!

Erkundung einer Referenzarchitektur für unsere Plattform

Architekturdiagramme sind eine gute Möglichkeit, einen Überblick darüber zu geben, was ein System dem Endbenutzer bietet und wie es im Inneren funktioniert. In diesem Kapitel haben wir mehrere wichtige Schritte zur Schaffung der Grundlage für eine zukünftige Plattform und ihre Funktionen erörtert:

- **Der Zweck unserer Plattform (Lösung der Probleme der Endnutzer)**: Wer sind unsere Endnutzer und welche Probleme müssen wir lösen?
- **Benutzeroberfläche/Entwicklererfahrung**: Was ist die ideale Entwicklererfahrung für unsere Endnutzer, damit sie sich optimal in ihre täglichen Arbeitsabläufe einfügen kann?
- **Kernkomponenten der Plattform**: Auswahl der richtigen Komponenten, um bestehende Prozesse, Tools, Infrastruktur und Einschränkungen zu berücksichtigen.
- **Unsere Plattform als Produkt**: Wie jedes Softwareprodukt muss unsere Plattform verfügbar, widerstandsfähig (auch bei hoher Auslastung) und standardmäßig sicher sein.
- **Erfolgs-KPIs**: Nutzung der Beobachtbarkeit zur Messung und Förderung der Akzeptanz, Effizienz und Produktivität.

Eine andere Möglichkeit, dies darzustellen, ist ein hochrangiges Diagramm unserer Plattform. Das folgende Diagramm ist zwar nicht vollständig, kann jedoch als gute Referenz für die Plattformen dienen, die Sie aufbauen werden:

Abbildung 3.6: Referenzarchitektur für unsere Plattformgrundlage (Das Bild dient als visuelle Referenz; die Textinformationen sind nicht wesentlich.)

Unsere Plattform als Produkt muss einen klaren Zweck haben!

Beginnen Sie damit, den Zweck zu visualisieren und zu formulieren, bevor Sie sich mit den technischen Details befassen!

Gehen wir dieses Diagramm gemeinsam durch, so wie Sie es Ihren Kollegen oder Endnutzern präsentieren würden. Wir beginnen oben und arbeiten uns nach unten vor, bevor wir uns mit den Aspekten Beobachtbarkeit, Verfügbarkeit, Ausfallsicherheit und Sicherheit befassen.

Der Zweck – Self-Service für Ihre Endnutzer

In [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) haben wir ein Beispiel für ein Plattformprinzip gegeben, das wir „Self-Service first“ genannt haben. Wir haben eine detaillierte Beschreibung gegeben: „Wir werden unseren Kunden alle Plattformfunktionen als Self-Service zur Verfügung stellen, wobei wir uns auf ihre Benutzererfahrung konzentrieren und eine selbstbestimmte Softwareentwicklung ermöglichen.“

Genau das spiegelt sich oben im vorangegangenen Diagramm wider. Hier haben wir alle potenziellen Endnutzer aufgelistet, von denen wir erfahren haben. Bei Financial One ACME unterstützen unsere Entwicklungsteams sie mit Anwendungsfällen rund um die einfachere Einbindung neuer Anwendungen oder den leichteren Zugriff auf Protokolldateien aus den Altsystemen in der Produktion. Außerdem bieten wir Self-Service für die DevOps-, Sicherheits-, **Site Reliability Engineering** (**SRE**)- und Anwendungssupport-Teams, indem wir den manuellen Aufwand und die kognitive Belastung durch Self-Service-Funktionen reduzieren.

Ein hochrangiges Diagramm wie dieses bietet nur begrenzt Platz. Wir könnten Beispiele für die verschiedenen Self-Service-Funktionen für Endbenutzer als Text hinzufügen oder – falls erforderlich – eine detailliertere Version dieses Diagramms für jeden Endbenutzer und seine Self-Service-Funktionen bereitstellen!

Benutzeroberfläche/Entwicklererfahrung

Jede Endbenutzergruppe ist anders. Selbst innerhalb von Endbenutzergruppen gibt es möglicherweise unterschiedliche Fähigkeiten, die bei der Gestaltung und Implementierung der Benutzeroberfläche für die Self-Service-Funktionen unserer Plattform berücksichtigt werden müssen.

Entwicklungsteams bevorzugen höchstwahrscheinlich ihre bevorzugte IDE, wie Visual Studio Code oder IntelliJ. Sie sind wahrscheinlich damit einverstanden, YAML-Dateien zu bearbeiten, um neue Self-Service-Funktionen zu aktivieren. Einige erwarten möglicherweise eine IDE-Erweiterung, die die Erstellung dieser YAML-Dateien unterstützt, oder eine Erweiterung, die Code-Vervollständigung und Schema-Validierung bietet, um die Wahrscheinlichkeit von Fehlern wie Tippfehlern zu verringern.

Andere Teams innerhalb derselben Organisation wünschen sich hingegen möglicherweise eine ansprechende Benutzeroberfläche für das Entwicklerportal – beispielsweise Backstage, das praktische Vorlagenfunktionen für die Erstellung neuer Komponenten bietet.

Dann gibt es noch Ihre Automatisierungsingenieure, die weder in einer IDE arbeiten noch sich durch einen Assistenten klicken möchten, um ein neues Projekt zu erstellen. Sie möchten eine API oder eine CLI, mit der sie Aufgaben automatisieren können, da sie es gewohnt sind, auf diese Weise zu arbeiten. Sie erwarten wahrscheinlich einige Python-Bibliotheken, um unsere Self-Service-Funktionen aufzurufen.

Wie bereits in diesem Kapitel erwähnt, hat jeder Benutzer unterschiedliche Fähigkeiten und daher auch unterschiedliche Erwartungen an eine gute Benutzererfahrung. Die Fokussierung auf eine gute Benutzererfahrung ist entscheidend, da dies ein entscheidender Faktor dafür ist, ob die Plattform angenommen wird oder nicht. Aus diesem Grund ist es wichtig, die Benutzeroberfläche und ihr mögliches Aussehen in unserer Referenzarchitektur hervorzuheben, da dies die Art und Weise ist, wie unsere Benutzer mit unserer Plattform interagieren werden!

Kernkomponenten der Plattform

Auch wenn wir alle unsere Vorlieben bei der Auswahl von Tools und Technologien haben, sollte der richtige Ansatz für die Auswahl Ihrer Kernplattformkomponenten nicht auf persönlichen Vorlieben basieren. Er muss sich danach richten, welche Self-Service-Anwendungsfälle (d. h. Funktionen unserer Plattform) wir über eine Benutzeroberfläche bereitstellen möchten, die eine gute Benutzer- und Entwicklererfahrung bietet.

Im vorstehenden Diagramm haben wir die Plattformkomponenten in die folgenden Bereiche unterteilt:

- **Bereitstellungsdienste**: Dabei handelt es sich um Tools und Dienste, die sich auf die Softwarebereitstellung konzentrieren, da dies ein primärer Anwendungsfall unserer Plattform sein wird. CNCF-Open-Source-Tools wie Backstage, ArgoCD, Flux und OpenFeature, Open-Source-Tools wie GitLab, Jenkins und K6 oder sogar kommerzielle Tools wie die Tools von Atlassian würden in diese Kategorie fallen.
- **Plattformdienste**: Da ein wichtiger Anwendungsfall die Bereitstellung und der Betrieb von Softwarekomponenten sein wird, sollte unsere Plattform auch die zentralen Plattformdienste bereitstellen, die diese Softwarekomponenten benötigen. Dazu könnten Dienste wie Caching oder Datenbanken (Redis, MongoDB oder Postgres), Messaging und Eventing (Apache Kafka oder RabbitMB), Service Mesh (Istio, Linkerd oder Nginx) sowie Kerndienste wie Geheimnisverwaltung, Container-Registries, Policy Agents, Auto-Scaler und mehr gehören.
- **Plattform**: Die Plattform muss zwar nicht auf Kubernetes laufen, aber im weiteren Verlauf dieses Buches werden wir uns auf K8s als zugrunde liegende Plattform-Orchestrierungsschicht konzentrieren. Kubernetes darf jedoch nicht die Antwort auf alle Fragen der Plattformentwicklung sein. Das Ziel besteht darin, die richtigen Plattformkomponenten auszuwählen, um den Endbenutzern den erforderlichen Self-Service zu bieten. Dies kann dazu führen, dass Sie Ihre Plattform auf VMs ausführen oder sich sogar für eine vollständig verwaltete, sofort einsatzbereite SaaS-Lösung entscheiden!
- **X-as-Code**: Neben Self-Service First müssen wir auch das Mantra „Everything as Code” beherzigen. Ob es nun um die Definition von Bereitstellungen, Observability oder Eigentumsverhältnissen geht, wie zuvor in diesem Kapitel erläutert, oder um andere Aspekte des Software-Lebenszyklus – alles sollte in irgendeiner Form von Code ausgedrückt werden. Hier sollten Sie Tools wie Crossplane, Terraform oder Ansible wählen. Insbesondere Crossplane etabliert sich im Cloud-Native-Bereich als Werkzeug der Wahl, wenn es darum geht, Anwendungen und Infrastruktur auf deklarative Weise zu orchestrieren. Achten Sie auch darauf, Ihre Werkzeugauswahl für Bereitstellungs- und Plattformdienste danach zu validieren, wie X-as-Code-freundlich sie sind, z. B. wie sie **Service-Level-Ziele** (**SLOs**) definieren oder Warnmeldungen mit dem ausgewählten Observability-Tool überwachen!
- **Observability**: Sie würden kein Auto fahren oder kein Flugzeug fliegen, ohne Telemetrie und Ihre wichtigsten Indikatoren wie Geschwindigkeit, Höhe oder Tankanzeige. Ebenso wenig dürfen wir eine Plattform ohne integrierte Observability betreiben. Dank Standards wie OpenTelemetry und Projekten wie Prometheus und Fluent verfügen wir über viele integrierte Observability-Signale in den Komponenten, die wir in unserer Plattform verwenden werden. Ob es sich nun um Kubernetes selbst oder um Tools wie Nginx, Reddis, Harbour, ArgoCD oder Backstage handelt, alle diese Tools geben Metriken, Protokolle, Ereignisse und/oder Traces aus, die wir sammeln und an unser Observability-Backend senden können, um sie automatisch zu analysieren oder Warnmeldungen auszugeben! Obwohl viele bereits integriert sind, wird wahrscheinlich nicht jedes Tool, für das wir uns entscheiden, alle Daten liefern, die wir benötigen. Daher ist es wichtig, Ihre Tool-Auswahl anhand ihrer Observability zu überprüfen. Bei einigen Tools müssen Sie möglicherweise Metriken aus Protokollen extrahieren. Bei anderen benötigen Sie möglicherweise eine Erweiterung – Jenkins bietet beispielsweise ein OpenTelemetry-Plugin, um Traces für jede Jenkins-Job-Ausführung auszugeben. In anderen Fällen müssen Sie sich möglicherweise auf kommerzielle Observability-Angebote durch agentenbasierte Instrumentierung verlassen.

Die Beobachtbarkeit wird später in diesem Buch noch näher behandelt, da sie für viele Disziplinen wie SRE, automatische Skalierung, Incident Response und Fehlerbehebung eine wichtige Rolle spielt.

Eine Plattform, die verfügbar, widerstandsfähig und sicher ist

Eine Plattform ist ein Produkt! Ein Produkt, das von unseren internen Benutzern verwendet werden soll, muss daher verfügbar sein, wenn sie es benötigen, ausfallsicher sein, wenn viele Benutzer es gleichzeitig benötigen, und sicher sein, damit unsere Benutzer dem Produkt vertrauen.

Um sicherzustellen, dass unsere Plattform immer verfügbar ist, wenn unsere Nutzer sie benötigen, müssen wir dieselben architektonischen Prinzipien anwenden, die wir auch bei jeder anderen Software anwenden würden, die erfolgreich sein soll. Für unsere Plattform bedeutet dies, dass alle kritischen Komponenten der Plattform standardmäßig verfügbar, widerstandsfähig und sicher sein müssen. Sehen wir uns einige Beispiele und Best Practices für diese drei Säulen an.

Verfügbarkeit

Unsere Nutzer betrachten unsere Plattform als verfügbar, wenn sie sie für die von uns versprochenen Self-Service-Anwendungsfälle nutzen können. Erinnern Sie sich an unseren vorgeschlagenen Self-Service-Anwendungsfall „Anfordern eines Protokolls aus der Produktion” aus Abbildung 3.2? Wenn ein Entwicklungsteam diesen Self-Service-Anwendungsfall befolgt, erwartet es, dass unsere Plattform die angeforderten Protokolle jederzeit innerhalb einer angemessenen Zeit liefert, egal ob es Dienstagmittag oder Freitagabend um 23 Uhr ist.

Dieser Anwendungsfall umfasst viele verschiedene Tools, wie z. B. Git (wo die Konfigurationsdateien gespeichert sind) und unsere selbst entwickelte Lösung, die eine REST-API zum Anfordern von produktionsspezifischen Protokollen bietet. Beide Systeme müssen verfügbar sein. Beide Systeme müssen außerdem innerhalb einer bestimmten Zeit mit einer gültigen Antwort auf Anfragen reagieren.

Die beste Möglichkeit, die Verfügbarkeit sicherzustellen, besteht darin, zwei Schritte zu befolgen:

1.  **End-to-End-Überwachung des Anwendungsfalls**: Wie bei geschäftskritischen Anwendungen können wir synthetische Tests einrichten, um die End-to-End-Benutzerreise für diesen Anwendungsfall zu simulieren. In diesem Fall würden wir überprüfen, ob die Aufrufe der Git-API wie erwartet funktionieren, indem wir Dummy-Commits und PRs ausführen und die Antwortzeit und den Antwortcode überprüfen. Das Gleiche würden wir auch für unseren REST-API-Aufruf tun, um die Protokolle anzufordern. In diesem Szenario muss jedoch auch gewartet werden, bis die angeforderten Protokolle an den Kommunikationskanal des Entwicklungsteams zurückgesendet werden, damit wir die gesamte End-to-End-Zeit messen können.

Beide Szenarien können durch benutzerdefinierte Skripte durchgeführt werden, die wir als Cron-Job ausführen, oder wir können vorhandene synthetische Testlösungen nutzen. Sie sollten überprüfen, ob Ihre Observability-Plattform bereits synthetische Tests anbietet, da viele dieser Anbieter diese Funktion in ihrem Portfolio haben. Dies erleichtert auch unseren zweiten Schritt, nämlich die Überwachung und Alarmierung bei wichtigen Qualitätsindikatoren!

1.  **Überwachung und Warnmeldungen zu wichtigen Verfügbarkeitsindikatoren**: Als Plattformteam möchten wir benachrichtigt werden, wenn unsere Self-Service-Anwendungsfälle auf der Plattform nicht mehr wie erwartet funktionieren, bevor sich unsere Endbenutzer beschweren. Hier kommen die Überwachung und Warnmeldungen zu wichtigen Indikatoren ins Spiel. Unsere synthetischen Tests liefern bereits einen guten Indikator, aber wir sollten automatische Warnmeldungen einrichten, falls die Git-API oder unsere REST-API langsamer werden oder auf Fehler reagieren. Darüber hinaus können wir auch Warnmeldungen zu anderen Frühindikatoren einrichten. Viele Tools auf unserer Plattform – darunter auch Git aus unserem Beispiel – erstellen Protokolle sowie Metriken zu Gesundheitsindikatoren. Wir möchten benachrichtigt werden, wenn wir IRGENDWELCHE FEHLER-Protokolle auf diesen Systemen sehen. Diese können Frühwarnindikatoren sein. Die meisten Systeme verfügen auch über interne Warteschlangen, wie z. B. Anforderungswarteschlangen. Wir möchten benachrichtigt werden, wenn diese Warteschlangen immer länger werden, da dies ein Indikator dafür ist, dass sich zu viele eingehende Anforderungen stapeln, was letztendlich zu Leistungs- und Verfügbarkeitsproblemen führen wird.

Es gibt noch viele andere Dinge, die wir tun müssen, um die Verfügbarkeit der Systeme sicherzustellen. Diese werden wir im nächsten Abschnitt behandeln, in dem wir über Ausfallsicherheit sprechen werden.

Ausfallsicherheit

Wir haben gerade über die Verfügbarkeit unseres Produkts gesprochen. Für unsere Endbenutzer muss die Plattform immer verfügbar sein, unabhängig davon, ob sie der einzige Benutzer im System sind oder ob 1.000 andere versuchen, Self-Service-Aufgaben auszuführen. Sie erwarten auch Verfügbarkeit, unabhängig davon, ob es Probleme in unserer internen Infrastruktur oder unseren Cloud-Diensten gibt. An dieser Stelle sprechen wir über die Ausfallsicherheit eines Systems. Das bedeutet, dass das System trotz unerwarteter Ereignisse (hohe Auslastung, Komponentenausfälle, Verbindungsprobleme usw.) verfügbar bleibt.

Aus architektonischer Sicht gibt es viele Möglichkeiten, ein System widerstandsfähiger zu machen und so eine hohe Verfügbarkeit zu erreichen. Betrachten wir noch einmal unser REST-API-Beispiel. Aus Sicht der Bereitstellung können wir Folgendes tun:

- **Lastenausgleich bei replizierten Bereitstellungen**: Wir können unsere Implementierung mit ReplicaSets bereitstellen, wodurch mehrere tatsächliche Pod-Instanzen eingehende Anfragen bearbeiten müssen. Anfragen können mit Round-Robin- oder anderen komplexeren Algorithmen lastenausgeglichen werden.
- **Geografische Diversität implementieren**: Um einer globalen Nutzerbasis gerecht zu werden, können wir unsere Implementierung in Regionen bereitstellen, in denen unsere Nutzer ansässig sind. Dies reduziert die Auswirkungen von Netzwerklatenz und verteilt die Last je nach Standort unserer Nutzer.
- **Automatische Skalierung bereitstellen**: Mit **Horizontal Pod Autoscaler** (**HPA**) und **Kubernetes Event Driven Autoscaling** (**KEDA**) können wir unsere Implementierung auf der Grundlage von Indikatoren wie CPU, Speicher, eingehenden Anfragen oder sogar der Benutzererfahrung skalieren. Auf diese Weise können wir die meisten Probleme mit der Ausfallsicherheit bei Ressourcenengpässen vermeiden.
- **Automatische Sicherung und Wiederherstellung durchführen**: Nicht jedes Problem lässt sich vermeiden. Im Katastrophenfall ist es wichtig, über automatisierte Sicherungs- und Wiederherstellungsoptionen zu verfügen, damit wir so schnell wie möglich zum normalen Betrieb zurückkehren können.

Aus Sicht der Softwarearchitektur bietet unsere REST-API mehrere Optionen:

- **API-Ratenbegrenzung**: Wir können die Anzahl der eingehenden Anfragen insgesamt oder von einem bestimmten Benutzer oder Team begrenzen. Dadurch werden Probleme vermieden, die entstehen können, wenn jemand versehentlich (oder absichtlich) unser System mit zu vielen Anfragen überflutet.
- **Warteschlange für eingehende Anfragen**: Ereignisgesteuerte Architekturen ermöglichen es uns, Anfragen in eine Warteschlange zu stellen und sie zu bearbeiten, sobald Mitarbeiter verfügbar sind. Die Mitarbeiter können dann auch je nach Länge der Warteschlange skaliert werden. Während zusätzliche Ebenen, wie z. B. Anfragenwarteschlangen, möglicherweise die Latenz der Anfragen beeinflussen, erhöht dieses Architekturmuster die Stabilität, Ausfallsicherheit und Verfügbarkeit.
- **Wiederholungsversuche und Backoff für nachgelagerte Systeme**: Da wir auch Aufrufe an Backend-Systeme wie Git oder das Logging-Observability-Backend senden, möchten wir sicherstellen, dass wir nicht von Problemen auf deren Seite beeinträchtigt werden. Zu diesem Zweck können wir API-Wiederholungsversuche (für den Fall, dass ein API-Aufruf zu lange dauert oder fehlschlägt) in Kombination mit Backoff (Verlängerung der Zeit zwischen API-Aufrufen) implementieren. Diese Strategien erhöhen unsere Ausfallsicherheit und helfen auch unseren nachgelagerten Systemen.

Sicherheit

Wenn unsere Plattform jederzeit verfügbar ist, ist das ein guter Anfang. Aber wie jedes Softwareprodukt muss sie auch sicher sein. Dies ist für Plattformen sogar noch wichtiger, da sie es unseren Endbenutzern ermöglichen, neue Softwareanwendungen zu erstellen, bereitzustellen und zu betreiben, die ebenfalls sicher sein müssen. Wenn unsere Plattform auf einem Stack und Tools läuft, die bekannte Schwachstellen aufweisen oder gehackt werden können, sind wir Angreifern ausgesetzt, die dies für Angriffe auf die Software-Lieferkette oder für den Zugriff auf vertrauliche Informationen ausnutzen. Schauen wir uns noch einmal unsere REST-API an. Wenn wir jedem erlauben, diese API zu verwenden, um Protokolle aus der Produktion anzufordern, könnten wir am Ende wichtige Protokollinformationen an einen Hacker senden.

Deshalb ist es wichtig, strengste Sicherheitsrichtlinien auf unsere Plattform, jede Komponente und jedes Tool, das wir verwenden, sowie jede Zeile Code, die wir entwickeln, anzuwenden. In [Kapitel 7](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/7) werden wir das Thema der Entwicklung konformer und sicherer Produkte ausführlicher behandeln, weshalb wir es hier nur allgemein ansprechen. Wir müssen unsere Plattform als die kritischste Software in unserem Unternehmen betrachten. Daher dürfen wir keine Komponenten bereitstellen, die bekannte Schwachstellen aufweisen. Wir müssen in allen unseren selbst entwickelten APIs eine angemessene Zugriffskontrolle implementieren. Wir müssen alle Sicherheitsscan- und Warntools für unsere Plattform einsetzen, die wir auch für jede andere geschäftskritische Software verwenden würden, die wir in der Produktion einsetzen.

Wir sind das Plattform-Engineering-Team, was bedeutet, dass wir für die Sicherheit unserer Plattform ebenso verantwortlich sind wie für ihre Verfügbarkeit und Ausfallsicherheit!

Erfolgskennzahlen und Optimierung

„Wir haben Monate damit verbracht, unsere neue Plattform aufzubauen. Die Entwickler hassen sie! Helfen Sie mir zu verstehen, warum!“

Mit allem, was wir bisher gelernt haben, sollten wir in einer guten Position sein, um nicht auf das Problem zu stoßen, das wir zu Beginn dieses Kapitels vermeiden wollten. Wir wollen etwas entwickeln, das unsere Nutzer gerne verwenden, weil es ihnen das Leben erleichtert. Aber wir können unseren Erfolg nicht einfach aufgrund eines Bauchgefühls oder anekdotischer Beweise behaupten. Wir müssen unsere Wirkung messen und unseren Erfolg anhand von KPIs dokumentieren. Außerdem müssen wir alle Daten, die wir innerhalb unserer Plattform beobachten können, nutzen, um diese Erfolgskennzahlen sowie den operativen Aspekt der Plattform weiter zu optimieren.

Wir haben bereits viel über Observability gesprochen, sowohl als Self-Service-Funktion unserer Plattform und für unsere Endnutzer als auch über die Nutzung von Observability zum Verständnis der internen Abläufe unserer Plattform, um Verfügbarkeit und Ausfallsicherheit zu gewährleisten. Die Beobachtung unserer Plattformkomponenten wie Backstage, ArgoCD, Jenkins, OpenFeature, Git, Harbor, Redis, Istio und Kubernetes selbst gibt uns viele Einblicke in den Erfolg unserer Plattform und ihrer Funktionen. Lassen Sie uns einen Blick auf einige wichtige Indikatoren werfen, wie wir sie erfassen können und was wir mit ihnen tun können, um die Akzeptanz und Effizienz unserer Plattform zu optimieren.

Aktive Nutzer

Wenn Tools wie Backstage das Entwicklerportal der Wahl für unsere Plattform sind, möchten wir messen, wie viele unserer Benutzer sich täglich oder wöchentlich bei Backstage anmelden. Wir möchten messen, wie viele neue Projekte über die Backstage-Template-Engine erstellt werden und wie viele neue oder aktualisierte Git-Repositorys daraus resultieren.

Für unseren Financial One ACME-Anwendungsfall zur Protokollanalyse können wir messen, wie oft unsere REST-API aufgerufen wird. Da sich Teams mit einer Team-Kennung oder einem Token identifizieren sollten, können wir messen, wie viele Teams unsere Funktion nutzen und wie oft.

All dies sind gute Indikatoren für die aktuelle Akzeptanz. Wenn wir eine langsame Akzeptanz feststellen, können wir mehr Aufklärungsarbeit leisten oder mehr Einzelgespräche führen, um mehr Teams zu gewinnen. Wir können auch die bestehende Akzeptanz einzelner Teams nutzen und interne Erfolgsgeschichten erstellen, um die Fähigkeiten der Plattform bei anderen Teams bekannt zu machen.

Es ist jedoch wichtig, zunächst zu messen, wie viele aktive Nutzer wir auf der Plattform haben, und dies als Ausgangsbasis zu verwenden, damit wir zusätzliche Maßnahmen festlegen und die Akzeptanz steigern können!

SLOs/DORA

Eine Plattform bietet die Möglichkeit, Best Practices durch Self-Service-Vorlagen zu fördern. Hier kommen SLOs ins Spiel. Wir können nicht nur SLOs für unsere Plattformkomponenten definieren, wie z. B. die Verfügbarkeit, sondern dies auch als Gelegenheit nutzen, SLO-Definitionen in jede neue Vorlage für neue Softwareprojekte aufzunehmen, die unsere Endbenutzer über unsere Plattform erstellen – wir möchten, dass auch ihre Software hochverfügbar, widerstandsfähig und sicher ist.

Darüber hinaus können wir messen, wie viele neue Softwareprojekte und Releases mit Hilfe unserer Plattform erstellt und veröffentlicht werden. Wir können die Anzahl der Jenkins-Jobausführungen, deren Dauer, die Häufigkeit der ArgoCD-Synchronisationen und die Anzahl der Deployments, die in der Produktion landen und ihre SLOs erfüllen, untersuchen. All dies sind Indikatoren, die uns helfen, Teile der DORA-Metriken an die Engineering-Teams zurückzumelden. Diese Metriken benötigen sie, um ihre Effizienz nachzuweisen. Dies hilft uns als Plattformteam auch dabei, hervorzuheben, wie viel effizienter Teams mit Hilfe unserer Plattform werden, da wir davon ausgehen, dass sich Kennzahlen wie die Bereitstellungshäufigkeit oder die Vorlaufzeit für Änderungen verbessern werden. Wir werden DORA in [Kapitel 5](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/5), in dem wir uns mit CI/CD-Automatisierung befassen, genauer behandeln!

Nutzung/FinOps

Es ist ein großartiges Ziel, dass viele Nutzer unsere Plattform nutzen, und wir haben bereits gelernt, wie wir dies messen können. Indem wir mehr Teams auf eine zentralisierte Plattform bringen, können wir Best Practices für die richtige Dimensionierung und Skalierung von Bereitstellungen sowie die Optimierung der Auslastung der zugrunde liegenden Infrastruktur zentral durchsetzen, was zu einer Kostenoptimierung für die Plattform und alle darüber bereitgestellten Anwendungen führt.

In [Kapitel 1](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/1) haben wir eine neue europäische Verordnung zur Meldung von CO2-Emissionen erwähnt. Dies kann auch zentral als Plattformfunktion erfolgen, indem die tatsächliche Ressourcennutzung, die Kosten und die berechneten CO2-Auswirkungen der Plattform, jedes Plattformdienstes und jeder Anwendung, die über die Plattform bereitgestellt und betrieben wird, gemeldet werden.

Es gibt viele weitere Anwendungsfälle, die uns helfen, die Auslastung der zugrunde liegenden Infrastruktur zu optimieren, um unsere Kosten unter Kontrolle zu halten. Insgesamt bedeutet dies, dass unsere Plattform ein idealer Ort für unsere FinOps-Initiativen ist!

Wir hoffen, dass Sie einen ähnlichen Ansatz für die Erstellung einer Referenzarchitektur für Ihre Plattform-Engineering-Projekte anwenden können. Beginnen Sie mit einer allgemeinen Übersicht, die den Zweck der Plattform aufzeigt, einen Überblick über die Funktionen und die Benutzeroberfläche gibt, Einblicke in die Kernkomponenten der Plattform vermittelt und angibt, wie Sie den Erfolg Ihrer Plattform-Engineering-Initiative messen.

Zusammenfassung

In diesem Kapitel haben wir gelernt, wie man Plattform-Engineering mit einer produktorientierten Denkweise angeht: Finden Sie das eigentliche Problem, das wir lösen müssen, bieten Sie eine einfache, schnelle Lösung, um unsere Implementierung zu validieren, identifizieren Sie, wie unsere Plattform in bestehende Prozesse und organisatorische Anforderungen passt, präsentieren Sie eine Lösung mit einem Wertversprechen, das sich nicht nur auf die Entwicklungsteams konzentriert, und entwerfen Sie dann ein flexibles Design, ohne in Überengineering zu verfallen!

Am Ende haben wir eine hochrangige Referenzarchitektur erstellt, mit der Sie den Zweck der Plattform Ihren Endnutzern und allen anderen Stakeholdern, die dieses Projekt unterstützen müssen, näherbringen können.

In [Kapitel 4](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/4) werden wir uns mit den architektonischen Details einer Plattform, der Rolle von Kubernetes, der Integration in Ihre bestehenden Dienste und der Bereitstellung der Funktionen der Plattform für Ihre Anwendungs- und Serviceentwicklungsteams befassen!

Weiterführende Literatur

- \[1\]Reddit-Beitrag: [https://www.reddit.com/r/devops/comments/stuep4/weve_spent_months_building_this_platform_devs/](https://www.reddit.com/r/devops/comments/stuep4/weve_spent_months_building_this_platform_devs/%0A)
- \[2\] Sunk Cost: [https://developerexperience.io/articles/sunk-cost](https://developerexperience.io/articles/sunk-cost%0A)
- \[3\] CDEvents: https://github.com/cdevents/spec
