Plattformarchitektur verstehen, um eine Plattform als Produkt aufzubauen

In diesem Kapitel werden Sie durch alle relevanten Grundlagen und Ansätze zur Erstellung Ihrer Plattformarchitektur geführt. Zunächst lernen Sie die Prinzipien kennen und erfahren, wie diese zu einem Leitfaden für Ihre Plattformstrategie werden. Dies hilft Ihnen, auf Kurs zu bleiben und sich auf das Wesentliche zu konzentrieren. Abschließend definieren wir den Zweck Ihrer Plattform.

Von hier aus beginnen wir mit der Definition Ihrer Architektur. Sie lernen die Komponenten einer Plattform, die Kombinierbarkeit von Plattformen und den Umgang mit Abhängigkeiten kennen. Als Nächstes beschäftigen Sie sich mit Referenzarchitekturen und deren Erstellung für Ihre Anforderungen. Um Ihnen neue Perspektiven zu eröffnen, haben wir einige Anwendungsfälle für „Platform as a Product“ zusammengestellt.

Zuletzt lernen Sie, wie Sie Ihre Plattformreise mit der **Thinnest Viable Platform** (**TVP**) beginnen und wie Sie die Einführung der Plattform durch relevante **Leistungskennzahlen** (**KPIs**) sichtbar machen können.

In [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) lernen Sie Folgendes:

- Verständnis der Plattformprinzipien und Definition des Zwecks Ihrer Plattform und Ihres Teams
- Erkunden der Plattformarchitektur – Schichten, Komponenten und Meta-Abhängigkeiten
- Erkundung der Plattform als Produkt – Anwendungsfälle und Implementierungen
- Verstehen von TVPs
- Betrachten der relevanten KPIs, um die Akzeptanz transparent zu machen

Verständnis der Plattformprinzipien und Definition des Zwecks Ihrer Plattform und Ihres Teams

Sie benötigen zwei wesentliche Dinge, um die richtige Architektur für Ihre Plattform zu entwickeln und diese zu befolgen. Zunächst müssen Sie die Leitplanken definieren, die Ihnen die Richtung vorgeben, und die Schritte zur Entwicklung und zum Betrieb Ihrer **internen Entwicklungsplattform** (**IDP**) als Produkt v ieren. Zweitens müssen Sie verstehen, was Sie erreichen möchten. Damit ist nicht die Architektur gemeint, sondern die identifizierten und definierten Zwecke, die hinter Ihrer Plattform stehen.

Einführung von Prinzipien als Leitplanken für die Entscheidungsfindung

Prinzipien klingen vielleicht wie ein altmodischer Ansatz aus den vergessenen Zeiten der Unternehmensarchitekten und sehr starren Organisationen. In Zeiten, in denen alles agil wird, sind Prinzipien die Eckpfeiler für eine aktive Entscheidungsfindung. Sie helfen, Diskussionen zu verkürzen und sich auf die Bereitstellung der Plattform zu konzentrieren. Wie unterscheiden sich Prinzipien von Fähigkeiten oder Attributen? Die Fähigkeiten einer Plattform sind die Funktionen, die ein IDP bereitstellen oder anbieten kann. Stellen Sie sich vor, Sie benötigen Dateispeicherplatz, und mit der Spezifikation einer Ressourcendefinition, die Sie innerhalb Ihrer Plattform anwenden, stellt Ihnen das System einen S3-konformen Bucket zur Verfügung. Attribute sind eine Obermenge der bereitgestellten Fähigkeiten und werden aktiv oder passiv genutzt. Wenn Sie eine sichere Plattform definieren, ist dies das Attribut, das dann die Absicherung der Knoten, CVE-Scans (**Common Vulnerabilities and Exposures**) und Dinge wie Netzwerkverschlüsselung und strenge **rollenbasierte** Zugriffskontrollregeln (**RBAC**) kombinieren kann. Ein Prinzip hilft Ihnen bei der Entscheidung, WIE Sie diese Fähigkeiten und Attribute erreichen wollen. Daher werden Sie in der Regel auf zwei Arten von Prinzipien stoßen:

- **Allgemeine Grundsätze**: Dies sind organisationsweite Orientierungspunkte. Ein gängiger Grundsatz aus den letzten Jahren lautet: Daten sind ein Vermögenswert. Dies bedeutet Folgendes:

Alle Daten sind für eine Organisation wertvoll. Sie sind eine messbare Ressource, für deren Schutz und Nutzung wir bestimmte Verfahren anwenden:

- - Für jede Datenquelle ist jemand verantwortlich
    - Daten werden allen zur Verfügung gestellt
    - Wir schützen Daten vor Verlust und Sicherheitsbedrohungen
- **Spezifische Grundsätze**: Hierbei handelt es sich um anwendungsorientierte Grundsätze, die für andere relevant sein können, sich jedoch nur an eine kleine Gruppe von Personen/Spezialisten richten. Ein Beispiel aus dem Bereich Sicherheit lautet: Jede Aktivität wird durch eine Identität definiert. Dies kann wie folgt interpretiert werden:
    - Für jeden Prozess in einem System wird eine Identität protokolliert
    - Unbekannte Identitäten sind unverzüglich zu melden
    - Jedes System erfordert eine Benutzerauthentifizierung

Wenn Sie diese beiden Grundsätze berücksichtigen, werden Ihre Entscheidungen bei der Gestaltung der Architektur für Ihr Szenario in verschiedene Richtungen gehen. Sie werden feststellen, dass bestimmte Grundsätze so aussehen, als würden sie die offensichtlichen Erwartungen einer Abteilung beschreiben. Aber gehen Sie niemals von etwas aus oder erwarten Sie etwas implizit, wenn Sie sicher sein wollen, dass es so gemacht wird, wie Sie es wollen.

Wichtiger Hinweis

Definieren Sie explizite Regeln, Richtlinien und Rahmenbedingungen, wenn Sie bestimmte Erwartungen an das Ergebnis der Aktivitäten einer Person haben. Implizit wird vorausgesetzt, dass man Ihre Gedanken lesen kann und die gleiche Weltanschauung hat wie Sie.

Beispiele für Plattform- und Plattform-Engineering-Prinzipien

Bevor wir Ihnen dabei helfen, Ihre eigenen Grundsätze zu definieren, möchten wir Ihnen einige Anregungen zu möglichen Grundsätzen geben:

- **Konzentrieren Sie sich auf allgemeine Probleme**: Identifizieren und priorisieren Sie Probleme, deren Lösung vielen Abteilungen oder Mitarbeitern in Ihrem Unternehmen hilft. Verhindern Sie, dass andere das Rad neu erfinden, indem Sie gemeinsame Probleme beseitigen und Probleme, die sich wie ein Schneeball immer weiter ausbreiten und immer größer werden, verhindern.
- **Erfinden Sie das Rad nicht neu**: Recherchieren Sie den Markt nach potenziellen Lösungen, die Ihren Anforderungen entsprechen. Überprüfen Sie regelmäßig selbst entwickelte Lösungen auf Standardersatz. Der Markt entwickelt sich schneller als wir. Konzentrieren Sie sich auf die Schaffung von Mehrwert, nicht auf interne Abhängigkeiten.
- **Jeder Kunde ist wichtig**: Jeder Nutzer Ihrer Plattform ist relevant, von großen Systemen bis hin zu kleinen Produkten. Sammeln und bewerten Sie jedes Feedback gleichermaßen. Gehen Sie auf die Bedürfnisse und Anforderungen aller gleichermaßen ein und bieten Sie die gleiche Servicequalität. Betrachten Sie diese Rückmeldungen als wichtigste Grundlage für die Festlegung Ihres Entwicklungspfads.
- **Beseitigen Sie Verschwendung**: Wir werden unsere Plattform so ressourceneffizient wie möglich gestalten und unseren Kunden helfen, so optimiert wie möglich zu arbeiten. Wir fördern Transparenz beim Ressourcenverbrauch und bieten Optionen zur Skalierung, Reduzierung und Anpassung der Arbeitslast. Gemeinsam entwickeln wir Best Practices für Entwickler, damit diese verstehen, wie sie fortschrittliche Technologien für mehr Flexibilität konfigurieren und nutzen können.
- **Eine Plattform ist ein Produkt**: Denken Sie bei jeder Entscheidung an Ihre Produktphilosophie. Konzentrieren Sie sich auf das, was Ihren internen Kunden, wie Entwicklern, dem Betrieb, der Sicherheit und anderen, einen echten Mehrwert bietet. Stellen Sie sicher, dass Funktionen schnell bereitgestellt werden und eine kurze Feedback-Schleife haben. Erkennen Sie Ablenkungen durch nicht wertorientierte Technologien. Ihr oberstes Ziel ist es, dass Ihre Kunden Ihre Plattform nutzen wollen, nicht dass Sie sie dazu zwingen.
- **Inner Source**: Jede Zeile Code Ihrer Plattform ist für Ihre interne Organisation zugänglich. Probleme und Fehler werden öffentlich verfolgt und ihre Lösung dokumentiert. Führen Sie gegebenenfalls eine FAQ. Jeder kann eine Funktion, eine Fehlerbehebung, Codezeilen und Dokumentation vorschlagen, um Ihre Plattform zu verbessern. Fördern Sie Community-Events und den Austausch zwischen Ihnen und allen Nutzern.

Diese Prinzipien versuchen, verschiedene Sichtweisen und Detailebenen abzudecken. Welches für Sie das richtige ist, lässt sich schwer sagen. Scheuen Sie sich nicht, Formulierungen oder Prinzipien im Laufe der Zeit anzupassen, wenn Sie feststellen, dass sie nicht funktionieren.

Produktdenken als Kernprinzip

Ihre internen Kunden sollten Ihre Plattform nutzen wollen. Sie sollten nicht dazu gezwungen werden.

Definieren Sie Ihre eigenen Grundsätze

Nachdem Sie sich mit der Idee der Grundsätze angefreundet haben, sehen sie alle gut aus, oder? Nun besteht die Herausforderung darin, sie so zu definieren und zu formulieren, dass sie von Ihrem Team angenommen werden. Sie müssen zu Ihrer Ausdrucksweise und dem internen Ansatz Ihres Unternehmens zur Definition ähnlicher Elemente passen.

Grundsätze können aus Ihren Unternehmenswerten, Kundenfeedback oder einem internen Workshop Ihres Teams abgeleitet werden. Was auch immer Sie tun, es ist wichtig, Transparenz über die Herkunft der Grundsätze zu schaffen, da sich das Team sonst ausgeschlossen fühlen könnte. Sie müssen sie auch einige Male überarbeiten, um die Formulierung zu schärfen und sie auf das Wesentliche zu reduzieren. Wie alle Grundsätze sollten sie nicht zu lang, aber auch nicht zu kurz sein. Die Sätze sollten kurz und prägnant formuliert sein, ohne Verschachtelungen oder Bedingungen. Bedingungen sind entweder ein Zeichen dafür, dass Sie sich über den Grundsatz „ ” unsicher sind oder dass es sich um zwei Grundsätze handeln könnte. Die richtige Länge ist erreicht, wenn Sie ein Thema ansprechen, es mit zwei oder drei erklärenden Sätzen und vielleicht einer Motivation oder Begründung versehen.

Ich habe zwei Schreibweisen gesehen, die sehr effizient sind, um ein Prinzip zu definieren und häufige Zitate und Anpassungen zu finden, und manchmal findet man sie in Slack-/Teams-Kanalbeschreibungen oder E-Mail-Fußzeilen.

Befehl und Begründung

Der Ansatz **„Befehl und Begründung“** funktioniert in der Regel gut für Organisationen mit stärkeren Hierarchien, in denen das Plattformteam möglicherweise gerade erst gebildet wurde oder in denen die gesamte Initiative mit Skepsis betrachtet wird. Dies erfordert eine strengere Ausrichtung für die Initialisierung. Ich bin jedoch der Meinung, dass diese Prinzipien im Laufe der Zeit überarbeitet werden sollten und die Beiträge des Plattform-Engineering-Teams und der Endnutzer gesammelt werden sollten.

Hier ist eine Übersicht, wie man das schreiben kann:

- **Titel**: Jeder Grundsatz hat so etwas wie einen Titel, der im Gedächtnis bleiben sollte.

Auf den Titel folgt eine Liste von Befehlen:

- 1.  Der erste Befehl gibt die Richtung vor
    2.  Dann sollte eine Erklärung folgen, warum dies relevant ist
    3.  Danach sollten einige detailliertere Maßnahmen zu berücksichtigen sein
    4.  Dann sollte eine weitere Maßnahme oder Begründung folgen
    5.  Hier sollte die Verantwortung an den Leser übertragen werden

Hier ist ein Beispiel basierend auf der vorangegangenen Gliederung:

- **Titel**: Self-Service First:
    1.  Jede Plattformfunktion muss für den Endbenutzer nutzbar sein, ohne dass er mit dem Plattform-Engineering-Team interagieren muss
    2.  Dies ermöglicht die Selbstbestimmung des Benutzers und entlastet die Plattform- und DevOps-Teams
    3.  Schreiben Sie keine bestimmten Vorgehensweisen vor, sondern geben Sie Best Practices als Orientierung
    4.  Eröffnen Sie die Möglichkeit einer vollständigen Transparenz der Bereitstellungen Ihrer Endnutzer und ermöglichen Sie einen detaillierten Zugriff auf Betriebsdaten.
    5.  Sie stellen eine Reihe äußerst wertvoller Tools und Automatisierungsfunktionen bereit, die die Entwicklung und den Betrieb der Software vereinfachen.

Wie Sie sehen, sagt dieser Stil dem Leser, was er tun soll. Der Titel ist aussagekräftig und lautet: Was auch immer Sie tun, denken Sie zuerst darüber nach, wie Sie es als Self-Service verfügbar machen können. Seien Sie vorsichtig mit solchen Nummerierungen. Es funktioniert nicht, wenn Sie jedes Prinzip mit „zuerst“, „vorrangig“ oder „übergeordnet“ benennen. Hier sehen Sie jedoch, dass dieses Prinzip von allen möglichen Prinzipien, die Sie aufschreiben, immer an erster Stelle steht und höchstwahrscheinlich andere Prinzipien außer Kraft setzt.

Die Sätze II-IV erläutern und begründen den ersten Satz. Sie liefern unterstützende Argumente und Richtlinien, die es zu berücksichtigen gilt. Die Schlussfolgerung ist genauso wichtig wie der Titel oder der erste Satz. Es muss sich um eine Übergabeerklärung handeln. Sie ist wie ein Aufruf zum Handeln, aber nicht in der Weise, dass jemand aufgefordert wird, etwas zu tun – das ist in den vorangegangenen Sätzen geschehen. Sie muss auf persönlicher Ebene angesprochen werden, mit einer direkten Ansprache an den Leser. Weitere Ideen zum Abschluss eines Grundsatzes finden Sie in der Liste mit Beispielen.

Plattform-Teams werden mit der Zeit ihr internes Vertrauen und ihre Motivation stärken, was einen anderen Stil von Grundsätzen erfordert.

Wir werden …

Erfahrene Plattform-Engineering-Teams und junge Organisationen benötigen Grundsätze, die ihr Wir-Gefühl fördern. Das ist fast wie ein Schwur der Brüderlichkeit und Schwesternschaft. Allerdings müssen Sie Ihr Team auch gut kennen und vorsichtig damit umgehen. Nicht jeder mag diese Art der Definition von Grundsätzen, da sie starke Bindungen und Kommunikation erfordern. Das ist nur eine persönliche Frage und nichts Negatives, aber Sie könnten wertvolle Teammitglieder verlieren, wenn Sie dies ignorieren. So würde ich einen „Wir werden”-Grundsatz definieren:

- **Gliederung**:

**Titel**: Keine Änderungen am Titel; fett, kurz und prägnant, das ist alles:

- 1.  Der erste Satz kombiniert in der Regel den Willen des Prinzips und enthält eine Erläuterung, um es zu rationalisieren.
    2.  Die nächsten Sätze definieren weitere Ziele oder Ansätze.
    3.  Jeder Satz beginnt mit „wir“, „gemeinsam“, „als Team“, „für unseren Kunden“ usw.
- **Beispiel**:

**Titel**: Selbstbedienung an erster Stelle:

- 1.  Wir stellen unseren Kunden alle Plattformfunktionen als Self-Service zur Verfügung, wobei wir uns auf ihre **Benutzererfahrung** (**UX**) konzentrieren und eine selbstbestimmte Softwareentwicklung ermöglichen.
    2.  Wir bieten Best Practices und arbeiten bei der Definition der besten Ansätze mit.
    3.  Gemeinsam schaffen wir eine transparente, wertschöpfende Umgebung, die Automatisierung und endbenutzerorientierte Funktionen fördert, um die Softwareentwicklung und den Betrieb zu vereinfachen.

Was halten Sie von diesem Ansatz? Ich habe das Prinzip beibehalten, damit Sie einen direkten Vergleich anstellen können. Welcher Ansatz gefällt Ihnen besser?

Sie sehen, dass der „Wir werden”-Ansatz kürzer und etwas komplizierter ist. Das liegt daran, dass Sie sich an das Team wenden, ihm sagen wollen, worauf es sich konzentrieren soll, und in einem Satz die Gründe dafür darlegen möchten. Würde man diese in kurze Sätze zerlegen, würde das nicht dasselbe Gefühl vermitteln und könnte eine falsche Botschaft senden.

Eine Kombination beider Ansätze kann gut funktionieren und Ihnen helfen, herauszufinden, welcher Typ besser zu Ihrem Team passt. Es ist jedoch nicht ungewöhnlich, dass Plattformteams mit einer Mischung zufrieden sind. Es kann sich schwerfällig anfühlen, wenn Sie vier bis sechs Prinzipien haben, die alle Ihr „Wir”-Gefühl ansprechen, aber es kann auch sehr bedrückend sein, eine Liste von Befehlen zu haben.

Hier ist eine Zusammenfassung davon in der folgenden Liste:

- Prinzipien sind hilfreiche Leitplanken für Ihre architektonischen und technischen Entscheidungen.
- Vier bis sechs Prinzipien funktionieren am besten
- Wenn Sie sich unsicher sind, beginnen Sie mit weniger und beziehen Sie die Endnutzer und die Plattformingenieure ein, um die nächsten Grundsätze zu identifizieren
- Überprüfen Sie Ihre Prinzipien regelmäßig, um festzustellen, ob sie noch zu Ihrem Team passen, aber ändern Sie sie nicht alle paar Monate

Entwickeln Sie den Zweck Ihrer Plattform als Produkt

Für einen erfolgreichen Start bei der Erstellung einer Plattform müssen wir deren Zweck und Ziel definieren und festlegen, wie wir das Plattform-Engineering-Team strukturieren oder umstrukturieren können. Dieser Schritt hilft Ihnen auch dabei, eine erste Iteration Ihrer zuvor definierten Grundsätze durchzuführen ( ). Reflektieren Sie Ihre eigene Wahrnehmung und hinterfragen Sie Ihre ursprüngliche Definition. Auf diese Weise lernen Sie, wie Sie zwei unterschiedliche Kräfte und widersprüchliche Ziele miteinander verbinden können.

Es mag einfach erscheinen, mit einer Plattform als Produkt zu beginnen. Eine Änderung der Denkweise, Gespräche mit Kunden und die Bereitstellung einiger guter Funktionen sind alles, was Sie brauchen. Dies ist jedoch nur ein Teil der Geschichte. Wir möchten Ihnen bewusst machen, dass eine Cloud-native Plattform das Potenzial hat, zum Motor Ihrer Organisation für Softwareentwicklung, -bereitstellung und -betrieb zu werden. Daher stellen wir Ihnen verschiedene Konzepte vor, die Sie auch in anderen Organisationstheorien und -praktiken finden, wie Kanban, Lean Inception oder Team Topologies.

Ihren eigenen Wert verstehen

Wenn Menschen in einer Sache wirklich schlecht sind, dann ist es das Schätzen. Ohne Maßstab oder Bezugspunkte fällt es uns schwer, richtig zu schätzen. Angenommen, ich frage Sie, welchen Wert eine Plattform für Ihr Unternehmen hat. Sie könnten Argumente wie einen schnelleren Softwareentwicklungszyklus, weniger Betriebsaufwand und zufriedene Ingenieure, die die Rekrutierungskosten senken, anführen. Nichts davon ist falsch, aber nichts davon ist präzise. In geschäftlicher Hinsicht liegt der Wert einer Plattform als Produkt darin, dass sie die Markteinführungszeit verkürzt oder die Flexibilität bei den Verzögerungskosten optimiert. Mit anderen Worten: Je länger Sie brauchen, um einen Dienst auf den Markt zu bringen, desto weniger Wert schaffen Sie. Eine gute Plattform ermöglicht es Ihnen, diesen Wert zu optimieren, indem sie den Implementierungsteams ein hohes Maß an Flexibilität und Geschwindigkeit bietet.

In der Theorie der **Verzögerungskosten** \[1\] wird davon ausgegangen, dass die Kapazitäten feststehen. Wenn Sie drei Projekte umsetzen möchten, müssen Sie entscheiden, mit welchem Sie beginnen. Jedes Projekt bringt einen anderen Wert mit sich. Wenn Sie mit allen drei gleichzeitig beginnen, geht die Annahme so weit, dass Sie alles zur gleichen Zeit fertigstellen, aber Sie sind nicht schneller oder langsamer, als wenn Sie sie nacheinander durchführen würden. Mit einem IDP, das Self-Service, ein hohes Maß an Automatisierung und Autonomie, Zuverlässigkeit usw. fördert, reduzieren Sie die Abhängigkeit von den verfügbaren Kapazitäten und ermöglichen die gleichzeitige Umsetzung mehrerer Projekte. Wenn man weiter darüber nachdenkt, ist das einer der Gründe, warum öffentliche Cloud-Anbieter so erfolgreich sind. Diese Vorteile werden jedoch mit steigender Komplexität und falschen Rollendefinitionen zu einem Hindernis.

Abbildung 2.1: Kosten der Verzögerung ohne und mit einer Plattform

Die vorstehende Abbildung zeigt den Unterschied zwischen der Umsetzung von Projekten ohne und mit einer Plattform. Auf der linken Seite sehen wir mindestens zwei Verzögerungen, was bedeutet, dass das zweite Projekt erst spät im Jahr oder Zeitraum einen Mehrwert liefert. Diese Verzögerung kann durch manuelle Prozesse, Abhängigkeiten von anderen Teams und Teammitgliedern oder verschiedene technische Schritte verursacht werden, die nicht miteinander integriert sind. Auf der rechten Seite führt ein gleichzeitiger Start der Projekte aufgrund einer sehr guten Plattform zu einer erheblichen Wertsteigerung. Beachten Sie, dass der Bereich unterhalb der Linien den Wert darstellt.

Wichtiger Hinweis

Cloud-native Plattformen wie IDPs brechen mit der Theorie der Verzögerungskosten und ermöglichen eine schnelle und frühzeitige Wertschöpfung. Je besser die Plattform, desto geringer die Abhängigkeiten von Kapazitäten und desto effizienter können Teams ihre Produkte implementieren und betreiben, desto mehr Wert kann Ihr Unternehmen generieren.

Vom System zur Plattform als Produkt

Letztendlich ist ein Produkt nichts anderes als ein Objekt mit Dienstleistungen, die sich aus den Anforderungen Ihrer Kunden, Ihren Geschäftsinteressen, einer bestimmten Technologie und einer ganzheitlichen Benutzererfahrung zusammensetzen. Fehlt eines dieser Elemente, wird Ihr Produkt scheitern. In der Projektwelt gibt es drei Eckpfeiler, die ständig aufeinander einwirken: Zeit, Geld und Umfang. Dies wird als das **eiserne Dreieck** bezeichnet. Um ein Gleichgewicht zwischen diesen drei Faktoren zu finden, sind sorgfältige Anpassungen erforderlich. Da wir jedoch die Projektperspektive hinter uns lassen wollen, stellen wir Ihnen hier das eiserne Dreieck des Produkts vor. Es besteht aus Machbarkeit, Attraktivität und Rentabilität.

Abbildung 2.2: Das eiserne Dreieck der Produkte

Innerhalb dieses Gleichgewichts finden wir verschiedene Kräfte, die auf das Produkt einwirken. Daher müssen wir uns folgende Fragen stellen:

- Welchen Bedarf oder welche Aufgabe lösen wir für den Kunden und Nutzer?
- Was möchte unser Kunde? (In der Regel wissen sie es selbst nicht.)
- Wie können wir das umsetzen?
- Welche Technologie sollten wir verwenden?
- Wie können wir daraus ein nachhaltiges Geschäft machen?

Wir können nun diese Produktperspektive mit einer Plattformperspektive kombinieren.

„Eine digitale Plattform ist eine Grundlage aus Self-Service-APIs, Tools, Services, Wissen und Support, die als überzeugendes internes Produkt zusammengestellt sind.“ So beschrieb sogar Bottcher einmal eine solche Plattform \[2\]. Darüber hinaus sagte er: „Autonome Delivery-Teams können die Plattform nutzen, um Produktfunktionen schneller und mit weniger Koordinationsaufwand bereitzustellen.“

Plattformen und Produkte überschneiden sich stark. Beide erfüllen folgende Aufgaben:

- Sie müssen für ihre Nützlichkeit werben und sie an interne Teams vermarkten.
- Sie sollten sorgfältig konzipiert und präzise sein.
- Sie sind auf den Nutzer zugeschnitten oder, noch besser, gemeinsam mit Nutzern/Entwicklern entworfen (mit Schwerpunkt auf UX/DevEx).
- Sie entwickeln die angebotenen Funktionen mit der Zeit weiter und benötigen einen klaren Fahrplan.

Bei der Entwicklung einer klaren Vision und eines klaren Zwecks für Ihre Plattform als Produkt sollten diese Aspekte berücksichtigt und überprüft werden. Sie werden feststellen, dass für das Produkt-Eisendreieck sofort zwei Rollen zugewiesen werden.

Der Product Owner der Plattform kümmert sich um die Rentabilität, während der Plattform-Ingenieur für die Machbarkeit zuständig ist. Aber fast jedem Unternehmen fehlt die Rolle der Person, die sich um die Attraktivität kümmert. Diese Rolle ist allgemein als **Developer Experience** (**DevX**) bekannt.

Ohne DevX ist ein Plattform-Engineering-Team unvollständig.

Wichtiger Hinweis

Der Produktverantwortliche der Plattform kümmert sich um die Rentabilität. Die Plattformingenieure kümmern sich um die Machbarkeit. Der DevX kümmert sich um die Attraktivität. Diese Rollen bestimmen den Erfolg einer Plattform als Produkt.

Stakeholder und ihr Einfluss auf Ihr Backlog

Wenn man über Stakeholder und Kunden in einer internen Unternehmenswelt spricht, ergibt sich ein Bild von Personen mit vielen Interessen. Um sich auf das Wesentliche zu konzentrieren, empfehle ich Ihnen, sie in drei Gruppen einzuteilen:

- **Benutzer**: Die Gruppe von Personen, die Ihre Plattform/Ihr Produkt tatsächlich nutzen werden. In unserem Fall sind dies Entwickler oder DevOps.
- **Kunden**: Personen, die über Budgethoheit verfügen und/oder Entscheidungen für ein ganzes Team, eine Abteilung oder ähnliches treffen.
- **Influencer**: Andere Personen, die ein Interesse an Ihrer Plattform haben, z. B. Sicherheits- oder Betriebsteams.

Sie bauen Ihre Plattform für diese Stakeholder-Gruppen, nicht für sich selbst! Bei der Definition des Zwecks Ihrer Plattform sollten Sie die verschiedenen Stakeholder-Gruppen aus unterschiedlichen Perspektiven betrachten. Ihre Bedürfnisse können sich im Laufe der Zeit ändern, was Sie durch häufige Iterationen und Sondierungen herausfinden können. Wenn Sie Funktionen für das Backlog definieren, machen Sie deutlich, von welchen Stakeholdern diese Anforderungen stammen. Nach einiger Zeit, in der Regel sind sechs Monate ein guter Zeitrahmen, sollten Sie die Feature-Anforderungen mit Ihren Stakeholdern neu priorisieren. Dies hat wiederum Auswirkungen auf den Zweck Ihrer Plattform. Schauen wir uns ein Beispiel an.

Vor einiger Zeit wurden wir gebeten, die Plattform des Kunden zu stabilisieren. Wir wussten ein wenig über die Arbeitslast, aber das Gesamtsystem war unzuverlässig und kaum als nützliches System zu gebrauchen. Nach einigen Wochen Arbeit tauchten neue Stakeholder auf. Sie interessierten sich für die Plattform, da sie ihre Größe automatisch an die Arbeitslast anpasste und die Leute im Allgemeinen mit der schnellen und unkomplizierten Einarbeitung zufrieden waren. Außerdem wurde bei der früheren Implementierung eine Single-Tenant-Bereitstellung für eine strikte Isolierung vorgesehen. Die neuen Stakeholder kamen aus einer Data-Science-Abteilung und suchten nach einem einfachen Ansatz, um ihre Modelle auszuführen, ohne Experten zu werden. Der von ihnen genutzte Cloud-Anbieter war bereits zu komplex, da er sich nur auf maschinelles Lernen konzentrierte. Der Plattformbetreiber erklärte sich bereit, für einige Wochen Kapazitäten zur Verfügung zu stellen, um die von den Datenwissenschaftlern benötigten Tools auf der Plattform zu implementieren. Obwohl sie noch weit von der Perfektion entfernt waren, waren die Implementierung und die Plattform gut genug, um benutzerfreundlich und kostengünstig zu sein und alle Datenschutzbestimmungen zu erfüllen. Wenn wir wieder in die Gegenwart springen, besteht das Hauptziel des Plattformteams darin, isolierte Umgebungen für Data-Science-Teams bereitzustellen, die mit einer ganzen Reihe von Tools ausgestattet sind und nach Abschluss ihrer Arbeit wieder abgebaut werden. Die Plattform kann auch weiterhin andere Workloads ausführen, derzeit besteht jedoch keine Nachfrage dafür.

Dieses Beispiel aus der Praxis zeigt, dass externe Einflüsse manchmal stärker sind als die eigene Motivation, aber zu einer höheren Akzeptanz und Akzeptanz im gesamten Unternehmen führen können.

Wichtiger Hinweis

Letztendlich haben Sie eine Plattform als Produkt für Ihre Stakeholder, in erster Linie für die Nutzer, und nicht für sich selbst entwickelt.

Conways Gesetz in Frage stellen

Organisationen, die Systeme entwerfen, sind darauf beschränkt, Designs zu produzieren, die Kopien der Kommunikationsstrukturen dieser Organisationen sind. (Melvin Conway, 1967.)

KopieErklären

Ich glaube, dass einer der Hauptzwecke einer Plattform darin besteht, Dinge besser zu machen, als sie derzeit sind. Dazu müssen wir den Status quo einer Organisation in Frage stellen. Unternehmen reorganisieren sich kontinuierlich, tauschen Verantwortlichkeiten aus und passen ihre Strukturen an. Aber letztendlich bleibt die Organisation dieselbe. Das ist Conways Schuld – zumindest hat er seine Beobachtungen von Organisationen beschrieben. Plattformen sind dazu da, zu disruptieren und zu harmonisieren; einerseits nutzen sie die DevOps-Methoden, um Engpässe zu identifizieren und diese Strukturen zu disruptieren, und andererseits harmonisieren sie die Bemühungen der Spezialistenteams in einer einheitlichen Umgebung.

Als Plattformteam sollten Sie zunächst Ihr Ziel und eine Ideologie definieren, der Sie folgen möchten, um Ihren Zweck zu erfüllen, bevor Sie gezwungen sind, der Struktur Ihrer Organisation zu folgen. Leider führt dies zu politischen Spielchen – wie man mehr Macht erlangt, wie man die meisten Nutzer gewinnt und wer die besten Verbindungen hat, um Entscheidungen voranzutreiben. Aber seien Sie nicht so naiv zu glauben, dass eine schöne Plattform mit einigen fantastischen Funktionen ausreicht, um erfolgreich zu sein.

Daher benötigen Sie eine gute Definition des Zwecks Ihres Teams, um in stürmischen Zeiten die Richtung zu halten, weiterzumachen, wenn alles Sie zurückhalten will, oder Sie auf Kurs zu halten, wenn Sie zu viel Geschwindigkeit und Traktion haben. Das hilft Ihnen, das Gleichgewicht zu halten.

Um all dies zusammenzufassen und für Ihr Team und die Nachwelt zu speichern, können Sie die Platform Engineering Purpose Canvas als Ausgangspunkt verwenden. Sie können die folgende Vorlage (https://miro.com/miroverse/platform-engineering-purpose-canvas-template/) verwenden oder selbst eine erstellen.

Abbildung 2.3: Platform Engineering Purpose Canvas \[3\] (Das Bild dient als visuelle Referenz; die Textinformationen sind nicht wesentlich.)

Da wir uns auf die Konzeption und Erstellung einer Plattform als Produkt konzentrieren, werden wir nicht weiter auf die Details von Plattform-Engineering-Teams, deren Aufbau und die richtigen Change-Management-Ansätze eingehen. Es gibt andere Bücher und Methoden, die sich darauf konzentrieren. Wenn Sie sich auch für Teamentwicklung interessieren, empfehlen wir Ihnen daher, sich mit Team Topologies zu befassen \[4\].

Mit Ihrem Plattformzweck ausgestattet, können wir uns der nächsten Herausforderung stellen, nämlich der schrittweisen Erstellung Ihrer Plattformarchitektur. Im nächsten Abschnitt erstellen wir eine Referenzarchitektur und andere Diagramme für Ihre Plattform als Produkt.

Erkundung der Plattformarchitektur – Schichten, Komponenten und Meta-Abhängigkeiten

Die Navigation für Ihre Plattformreise wird durch die Referenzarchitektur definiert, an der Sie Ihre gesamte Implementierung ausrichten können. Architektur und insbesondere Architekturdiagramme sind nicht für die Ewigkeit gemacht. Sie sind ein Rahmen, ein Entwurf, an dem Sie sich orientieren müssen, aber sie können und sollten im Laufe der Zeit aufgrund der Entwicklung der jeweiligen Marktlösungen, egal ob Open Source oder Closed Source, geändert werden.

Um bestimmte Teile besser verständlich zu machen, müssen wir Ihnen einige Tools und Produkte zur Verfügung stellen. Daher bevorzugen wir Open-Source-Lösungen gegenüber kommerziellen Lösungen. Wir möchten Ihnen keine Voreingenommenheit vermitteln, daher sollten Sie sich immer bewusst sein, dass es für alles, was wir erwähnen, mindestens eine Handvoll Optionen gibt. Einige Tools, die wir als Referenz verwenden, werden ausgewählt, weil wir sie besser kennen oder weil sie in der Community häufiger verwendet werden als andere.

Die Erstellung einer Architektur sollte niemals nur eine Perspektive berücksichtigen. Wie bei jedem vorherigen Thema müssen wir die verschiedenen Blickwinkel berücksichtigen, aus denen die Beteiligten eine Plattform betrachten. Ich möchte Ihnen nicht die gesamte Palette der traditionellen Tools für das Enterprise-Architektur-Management zur Verfügung stellen, sondern Ihnen bestimmte relevante Visualisierungen und Tools vorstellen.

Plattformkomponentenmodell

Stephan Schneider und Mike Gatto stellten 2023 die erste Version eines IDP-Referenzarchitekturmodells vor \[5\], das von der Community mehrfach überarbeitet wurde. Leider fehlen diesem Modell einige wichtige Perspektiven, entweder aufgrund der Benennung oder einfach weil eine sogenannte Ebene fehlt. Daher haben wir einen ganzheitlicheren Ansatz für das Modell entwickelt, der die folgenden Ebenen umfasst:

- **Die Entwicklererfahrungsebene**: Diese umfasst alle Komponenten der ersten Reihe, die für die Softwareentwicklung und das Infrastruktur-Engineering benötigt werden.
- **Die Automatisierungs- und Orchestrierungsebene**: Diese bündelt die Tools zum Erstellen, Testen, Bereitstellen, Speichern und Orchestrieren von Anwendungen und Infrastruktur.
- **Die Beobachtbarkeitsebene**: Diese umfasst alle Tools, die erforderlich sind, um Transparenz und Sichtbarkeit hinsichtlich der Vorgänge auf der Plattform und in ihren Anwendungen zu gewährleisten.
- **Die Sicherheits- und Identitätsebene**: Diese Ebene umfasst Systeme zur Durchsetzung und Überwachung der Sicherheit, Lösungen für die Benutzer- und Kontenverwaltung sowie Tools für die Verwaltung von Geheimnissen und Zertifikaten.
- **Die Ressourcenebene**: Dies ist ein Container für alle Rechenressourcen, die für eine Plattform genutzt werden können.
- **Die Fähigkeitsebene**: Die Ebene innerhalb oder oberhalb der Plattform, wie z. B. Kubernetes, die Dienste für die Benutzer bereitstellt.

Abbildung 2.4: Referenzkomponenten einer Plattform

Diese Sichtweise auf die Komponenten zeigt, dass eine Plattform definitiv mehr ist als ein einzelner Server, auf dem ich einfach eine Container-Orchestrierung oder ein Entwicklerportal installiere. Oftmals haben diese Komponenten mehrere Speicherorte. Dies ist eine Art Verbindung, die die relevanten Elemente miteinander verknüpft. Um beispielsweise die Sicherheit zu gewährleisten, finden wir relevante Elemente in der Ressourcenebene, um die Compliance einzuhalten und gehärtete Konfigurationen bereitzustellen, wie z. B. externe Systeme zum Sammeln und Analysieren von Daten, zusätzlich zur Funktionsebene innerhalb von Kubernetes, um Container zu scannen und Netzwerke zu schützen, aber auch in der CI/CD, um nur gehärtete Container bereitzustellen. Sie sehen, dass ein einzelnes Thema überall innerhalb einer Plattform angesiedelt sein kann.

Kombinierbarkeit der Plattform

Eine Plattform besteht aus vielen Teilen, die sich ständig weiterentwickeln. Parallel zu dieser Entwicklung können sich auch Ihre Benutzer und Ihr Unternehmen weiterentwickeln. Ein großes Problem, das wir häufig feststellen, ist die Zurückhaltung, bestimmte Teile einer Plattform zu ersetzen. Oft gibt es zwar Diskussionen über Prioritäten oder Budgets, aber das häufigste Problem ist, dass ein Austausch nicht einfach möglich ist. Manchmal liegt das daran, dass die Plattform und die Komponente alt sind und buchstäblich miteinander verschraubt sind, und manchmal liegt es daran, dass die Wahl der Technologie nicht gut war und eine Kette von Abhängigkeiten mit sich bringt, die schwer zu ersetzen sind. Aber es gibt noch einen dritten Grund: Sie zwingen Ihre eigene Vorgehensweise in das falsche Werkzeug.

Komponierbarkeit ist ein Prinzip, vielleicht sogar eine Ideologie, und auf jeden Fall ein Ansatz und eine Entscheidungsgrundlage, auf denen Plattformen aufgebaut sein sollten. Komponenten sind komponierbar, wenn sie miteinander interagieren, ohne dass dazwischen etwas für die Übersetzung entwickelt werden muss, wie Skripte oder serverlose Funktionen. Komponierbare Komponenten können mit möglichst geringem Aufwand und mit minimalen bis keinen Auswirkungen auf die Plattformfunktionalität ersetzt werden. Kubernetes ist eine Umgebung, die diesen Ansatz drastisch unterstützt und daher zum De-facto-Standard für die Erstellung Ihrer Plattform wird. Die Komponenten einer Plattform sind jedoch verteilt und laufen nicht alle auf Kubernetes. Dies macht es zu einer Herausforderung, die richtigen Tools zu finden.

Die Kombinierbarkeit hilft auch bei der richtigen Anpassung einer Plattform. Eine generische, einheitliche Plattform klingt auf dem Papier immer gut, ist aber unrealistisch und erhöht die Komplexität. Je mehr Komponenten Sie in eine Plattform einbringen müssen, desto wahrscheinlicher ist es, dass sie nicht gut zusammenarbeiten. Daher erhöht die Möglichkeit, Anpassungen für bestimmte Anwendungsfälle vorzunehmen, ohne die gesamte Architektur zu ändern, die Nutzbarkeit. Ein weiterer großer Vorteil der Kombinierbarkeit ist die Trennung der Aufgabenbereiche.

In [Kapitel 1](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/1) haben wir den Zweck einer Plattform als Abstraktionsschicht für Plug-and-Play-Speziallösungen hervorgehoben. Die strikte Durchsetzung der Kombinierbarkeit verursacht zwar viel Arbeit auf organisatorischer Ebene, ermöglicht es aber spezialisierten Teams, ihre Kernkompetenzen direkt in Ihre Plattform einzubringen.

Um zu beurteilen, ob eine Komponente für Ihre Plattform komponierbar ist, müssen Sie auf vier Fähigkeiten achten:

- **Orchestrierbar**: Sie kann in einer modernen dynamischen Umgebung wie Kubernetes ausgeführt werden, ohne beeinträchtigt zu werden.
- **Modular**: Sie erfordert keine weiteren Tools oder technischen Voraussetzungen, kann diese jedoch zur Erweiterung ihrer Fähigkeiten nutzen.
- **Auffindbar**: Sie muss mit anderen Komponenten nach standardisierten APIs oder nach Konzepten wie der benutzerdefinierten Ressourcendefinition von Kubernetes interagieren.
- **Autonom**: Sie muss unabhängig von anderen externen Eingaben sein und selbstständig funktionieren.

Jetzt wissen wir, worauf wir bei der Entwicklung der Plattform und der Auswahl der Plattformkomponenten achten müssen. Im nächsten Abschnitt erfahren Sie mehr über die Dinge zwischen diesen Komponenten, die die Plattform zusammenhalten.

Abhängigkeiten und der versteckte Klebstoff

Unabhängig davon, wie komponierbar die Plattformkomponenten sind, gibt es immer Abhängigkeiten und versteckte Verbindungen. Diese versteckten Verbindungen sind die Informationen, die zwischen den Komponenten fließen und dafür sorgen, dass sie aufeinander reagieren. Als Architekten ist es unsere Aufgabe, sicherzustellen, dass diese Informationen nicht widersprüchlich sind. Diese Informationen sind wichtig, werden aber oft nicht richtig verstanden.

Verwalten und Handhaben von Abhängigkeiten

Lassen Sie uns zunächst auf der Kombinierbarkeit aufbauen, indem wir die Abhängigkeiten zwischen den Komponenten visualisieren. Dazu können wir eine einfache Abhängigkeitsmatrix verwenden. Dieses Tool kann Ihnen helfen, Entscheidungen zu treffen und zukünftige Komponenten zu planen. Außerdem erfordert es einen gewissen Wartungsaufwand; viele Plattformen sind vom Wissen einzelner Ingenieure abhängig, und mit zunehmender Komplexität der Plattform wird auch die Dokumentation immer umfangreicher. Das Abbilden von Abhängigkeiten ist daher der kürzeste Weg zur Transparenz.

Im folgenden Beispiel haben wir **die Tools A-C**, wie z. B. **Container-Netzwerkschnittstellen** (**CNI**) **1-3**. Diese Tools können nun beliebige Tools aus der zuvor erwähnten Liste der Referenzkomponenten sein.

Bei den Abhängigkeiten ziehe ich es vor, ausdrücklich anzugeben, um welche Art von Abhängigkeiten es sich handelt. Daher können Sie beispielsweise Folgendes verwenden:

- **Unidirektionale und bidirektionale Abhängigkeiten**: Damit können Sie beschreiben, ob Tool B von Tool A abhängt oder Tool C von Tool B abhängt, da Tool B von Tool C abhängt.
- **Erweiternde Abhängigkeiten**: Erweiternde Abhängigkeiten erschließen mehr Funktionen und Features, wenn sie eingerichtet sind, müssen aber nicht unbedingt vorhanden sein. Wenn Sie beispielsweise ein Tool mit manueller Benutzerverwaltung haben, können Sie nun **Single Sign-On** (**SSO**) dafür nutzen, was Ihren manuellen Aufwand reduziert.
- **Konfliktbehaftete Abhängigkeiten**: Wie der Name schon sagt, vertragen sich diese beiden Dinge nicht gut miteinander.

Abbildung 2.5: Abhängigkeitsmatrix

Haben Sie es bemerkt? Im Beispiel der bidirektionalen Abhängigkeiten wird die Beziehung zwischen den Tools B und C nicht korrekt dargestellt. In der Spalte für Tool C fehlt der bidirektionale Markt für Tool B. Wenn Sie Ihre Abhängigkeitsmatrix implementieren, müssen Sie klare Anweisungen geben, wie diese Beziehungen verfolgt werden sollen. Ich halte es für am sinnvollsten, Markierungen für beide Tools festzulegen. Allerdings müssen Sie dann die Leserichtung klar angeben oder weitere Markierungen einführen. Sie könnten beispielsweise (u) verwenden, um eine eingehende Abhängigkeit zu definieren.

Das Abhängigkeitsmanagement ist eine kontinuierliche Aufgabe. Mit der Zeit besteht die Gefahr, dass Sie vergessen, neue Tools hinzuzufügen. Unabhängig davon, welche Methode Sie zur Implementierung neuer Funktionen verwenden, ist es daher möglicherweise eine gute Idee, eine automatische Unteraufgabe zu erstellen, um auch die Abhängigkeitsmatrix zu aktualisieren. Ein großer Vorteil ist auch, diese Matrix von Zeit zu Zeit zu bewerten, um potenzielle Engpässe oder Probleme zu identifizieren, an denen Sie arbeiten können.

Anwendungen x Plattform – eine wechselseitige Beeinflussung

Der **wechselseitige Einfluss** ist so definiert, dass beide Elemente in einer Beziehung zueinander stehen, in der das eine das andere ergänzt oder ihm gleichwertig ist. In der Beziehung zwischen der Plattform und den Anwendungen Ihrer Benutzer besteht eine gewisse gegenseitige Beeinflussung. Beispielsweise muss eine Anwendung drastisch skaliert werden. Als Plattform unterstützen Sie dieses Verhalten, garantieren aber auch, dass es keine Auswirkungen auf andere Anwendungen hat. Auf der anderen Seite hat sich die Anwendung für Ihre Plattform entschieden, weil Sie ihre Anforderungen unterstützen. Eine Plattform ohne Benutzer ist nutzlos. Um als Anwendung die beste Leistung zu erzielen, sollten Sie auf dieser Plattform laufen.

Dieses Beispiel ist jedoch sehr allgemein gehalten. Gegenseitige Beeinflussung wirkt sich auch auf Elemente außerhalb der in YAML-Dateien definierten Schichten aus. Es geht auch um die Anforderungen und Bedürfnisse, die dadurch entstehen, ohne dass sie ausdrücklich gestellt werden, um die Teamdynamik zwischen beiden implementierenden Parteien und um die Auswirkungen, die eine Lösung auf die Arbeitsweise anderer hat.

Daher wäre „Abhängigkeit” das falsche Wort, um diese Beziehung zu beschreiben. Es handelt sich um eine Koexistenz, eine Zusammenarbeit, ein gemeinsames Ziehen in die gleiche Richtung. Als Plattform-Engineering-Team und insbesondere als Architekt müssen Sie diese gegenseitige Beeinflussung bei der Entwicklung Ihrer Lösung berücksichtigen. Um dies zu Ihrer eigenen Superkraft zu machen, müssen Sie die Plattform-Ingenieure und Nutzer über diese Auswirkungen aufklären und sich darauf konzentrieren, wie sie das Beste aus der Plattform herausholen können, ohne Einschränkungen zu spüren.

Gegenseitige Beeinflussung

Der gegenseitige Einfluss ist das unsichtbare Zusammenspiel zwischen der Anwendung und der Plattform. Verstehen Sie ihn als eine gemeinsame Kraft, die die Plattform und die Anwendung der Nutzer zusammen besser macht, als sie es ohne einander wären.

Ein weiterer Bereich, in dem solche wechselseitigen Einflüsse sichtbar werden, sind Prozesse.

Möglichkeiten der Prozessdefinition für eine Plattform

Die Plattformentwicklung übernimmt viele Ansätze aus der DevOps-Methodik. In einer DevOps-Rolle konzentrieren sich einige Teile auf die Automatisierung. Diese automatisierten Schritte führen zur Definition von Prozessen. Man könnte also auch sagen, dass Plattformingenieure technische Prozesse erstellen, die als Plattform als Produkt implementiert werden, damit sie benutzerorientiert funktionieren. Diese Verfahren sind jedoch bei expliziten Designentscheidungen nicht sehr verbreitet. Die Form des Prozesses (oder wie der Prozess aussieht) hängt davon ab, wie bestimmte Komponenten funktionieren. Im Hinblick auf die Kombinierbarkeit der Plattform mag dies ein selbstverständlicher Ansatz sein, aber könnten wir die Plattform durch explizites Design der Prozesse verbessern?

Dies sollte nicht zu einer Geschäftsprozessmodellierung werden. Zu viele erweiterte Funktionen, die in Tools wie GitOps oder Operatoren auf Kubernetes integriert sind, können mehrere Variablen basierend auf Entscheidungspfaden haben. Es wäre lächerlich, all diese zu zeichnen. Es ist jedoch hilfreich, den Prozess zu dokumentieren und zu entwerfen, um die Plattform zu verstehen . Die Schwierigkeit liegt in den Prozessen mit mehreren Einstiegspunkten, die an folgenden Stellen beginnen können:

- Bereitstellung der Infrastruktur
- Benutzer-Onboarding
- Anwendungsbereitstellung
- Bearbeitung von Vorfällen

Jeder dieser Punkte erfordert eine eigene Prozessdefinition.

Sie haben die Möglichkeit, Optimierungspotenziale mit Fokus auf Benutzerfreundlichkeit und Handhabung zu finden. Durch die Nutzung der Prozessperspektive unterscheidet sich die Benutzerorientierung in Ihrer Plattformentwicklung von der gängigeren, rein technisch ausgerichteten Definition von Funktionen. Leider können wir Ihnen zum jetzigen Zeitpunkt keine weiteren Einblicke geben, da diese Disziplin noch neu ist und es kaum einen Wissensaustausch dazu gibt. In [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3) werden wir uns näher mit diesem Thema befassen.

Die Diskussion um Vendor Lock-in

Zum Abschluss des Themas Abhängigkeiten müssen wir noch auf die Diskussion über Vendor Lock-in eingehen. Sie ist Teil strategischer und architektonischer Entscheidungen und führt oft zu seltsamen Ergebnissen. An dieser Stelle sollten Sie sich bewusst sein, dass Sie immer Abhängigkeiten haben werden und ein Vendor Lock-in nichts anderes ist. Da Open Source eine fantastische Grundlage bietet, um proprietäre Software zu vermeiden, wird es auch als Argument dafür verwendet, Dinge selbst zu entwickeln. Die wichtige Frage lautet: Mit welcher Geschwindigkeit und Servicequalität möchten Sie Ihren Nutzern die Plattform zur Verfügung stellen? Mit welchen Betriebskosten rechnen Sie? Darüber hinaus müssen Sie Aspekte wie das verfügbare Team, die erforderlichen Fähigkeiten und die von Ihrem Unternehmen bevorzugten Kosten (**Betriebskosten** (**OPEX**) oder **kapitalisierte Ausgaben** (**CAPEX**)) berücksichtigen.

Hier sind einige unterschiedliche Perspektiven zum Thema Vendor Lock-in:

- **Besser selbst entwickeln**: Bestimmte Funktionen komplett selbst zu entwickeln, mag sich wie die ultimative Freiheit anfühlen und vermeidet jegliche Art von Anbietern. In Wahrheit werden Sie jedoch nur zu Ihrem eigenen Anbieter. Irgendwann möchten oder können Sie nicht mehr in Ihre Entwicklung investieren (übliches Projektverhalten). Damit ziehen Sie sich als Ihr eigener Anbieter aus Ihrem eigenen Markt zurück und alles, was Sie befürchtet haben, wird wahr.
- **Auswahl der besten Lösung pro Problem, nicht pro Kontext**: Im Bereich der Beobachtbarkeit gibt es eine Vielzahl von Optionen für Überwachung, Protokollierung und Nachverfolgung. Ein gängiger Ansatz hierfür ist die Auswahl des Open-Source-Tools, das am besten zum jeweiligen Anwendungsfall passt. Dazu müssen Sie dann einen Log-Collector und Agenten implementieren, um Metriken weiterzuleiten. Das Ergebnis ist eine vollständig komponierbare Observability-Lösung. Andererseits büßen Sie im Vergleich zu einer Lösung eines einzelnen Anbieters Funktionen wie Kontextbewusstsein, Skalierbarkeit oder Bedienbarkeit ein. Ich möchte nicht sagen, dass proprietäre Software besser ist, aber ich habe viel zu oft Organisationen gesehen, die 10 bis 14 verschiedene Tools in unterschiedlichen Versionen einsetzen, die in großem Umfang laufen und hohe Betriebskosten verursachen. Tatsächlich wird diese Vorgehensweise bei einem Toolset als nicht hilfreich angesehen, wenn es um Vorfälle geht. In diesem Fall neigen wir leider dazu, die Wahrheit zu ignorieren und Ausreden dafür zu finden, warum es so besser ist.
- **Fokus auf die falschen Dinge**: Die Leute konzentrieren sich immer noch auf die Aufgaben der Bereitstellung von Kubernetes. Das wird als Herausforderung angesehen und wird zu einer nie endenden Geschichte. Erwägen Sie den Einsatz von Tools, eigenwilligen Plattformen oder kommerziellen Lösungen, um Ihre Container-Orchestrierung zu realisieren, und konzentrieren Sie sich auf den wertschöpfenden Teil Ihrer Plattform.

Vendor Lock-in ist ein emotionaler Diskussionspunkt auf der Agenda eines Architekten, der ein Ziel definiert. Sie müssen Ihre Augen und Ihren Geist offen halten und wirklich überlegen, was wichtig ist und was nur dazu dient, das Ego zu füttern. Komplexe und unüberschaubare Lösungen sind nichts, wofür man Preise gewinnen kann.

Bis jetzt haben Sie etwas über Abhängigkeiten und den Umgang mit ihnen gelernt. Im nächsten Abschnitt werden wir lernen, wie man sie sichtbar macht.

Referenzarchitekturen

Referenzarchitekturen sind wertvolle Ressourcen für ein Plattform-Engineering-Team, Ihre Plattform und interessierte Nutzer. Sie bilden die Grundlage für Diskussionen und Entscheidungsprozesse und helfen dabei, zukünftige Arbeiten mit etwas Weitsicht zu definieren. Leider können viele Plattform-Teams kein klares Bild ihres Systems vermitteln.

Anbieterspezifische Referenzarchitekturen

Nun können sich diese Referenzarchitekturen ändern und für verschiedene Anbieter, die Sie möglicherweise nutzen, unterschiedlich aussehen. Die Plattform-Engineering-Community \[6\] hat einige Optionen und Vorlagen zusammengestellt, auf denen Sie aufbauen können. Ein guter Ausgangspunkt ist die Vorlage für einen einzelnen Cloud-Anbieter, hier mit einem Bezug zu AWS. Allerdings fehlt noch die Funktionsebene. Der Fokus liegt hier auf dem Cloud-Anbieter, da dieser oft eine große Anzahl von Komponenten für Ihre Plattform definiert. Wie Sie in der nächsten Abbildung sehen können, finden sich die Dienste **des Cloud-Service-Providers** (**CSP**) in jedem Teil der Architektur wieder. Sie könnten ein noch aussagekräftigeres Ziel entwerfen, indem Sie CSP CI/CD, Secrets Management und Cloud-IDPs nutzen.

Abbildung 2.6: AWS-Referenzarchitektur von platformengineering.org

Im Vergleich zur Single-Provider-Plattform bringt eine Multi-Provider-Plattform ihre eigene Komplexität mit sich. Neben den von jedem Anbieter genutzten Ressourcen müssen wir auch berücksichtigen, wo Container-Images gespeichert und verteilt werden sollen, wie die Beobachtbarkeit gewährleistet werden kann und wie Geheimnisse und Zertifikate über die Anbieter hinweg verwaltet werden sollen. Die folgende Referenzarchitektur zeigt, dass es nicht einfach ist, die Erwartungen zu erfüllen. Mit einer Multi-Cloud-Plattformstrategie entsteht eine Vielzahl von Problemen, um die Sie sich kümmern müssen. Die Kosten steigen drastisch, die Implementierungen und das Plattformverhalten ändern sich mit jedem CSP geringfügig, und es wird schwierig, einen Ansatz zu definieren, der sich überhaupt richtig anfühlt. Aspekte wie Verfügbarkeit, Sicherheit, Skalierbarkeit und Effizienz stehen im Widerspruch zueinander, da sie auf mehreren Umgebungen aufbauen.

Abbildung 2.7: Multi-Provider-Referenzarchitektur von platformengineering.org

Allerdings muss nicht jede Plattform in der Cloud ausgeführt werden. Die Anzahl der Optionen ist unbegrenzt. In etablierten Unternehmen sehen wir häufig hybride, lokale oder Cloud-erweiterte Umgebungen, die auf bewährten Lösungen wie VMware Tanzu oder Red Hat OpenShift basieren. In der folgenden Abbildung sehen wir, wie eine Plattform mit OpenShift als Kern aussehen würde.

Abbildung 2.8: OpenShift-Referenzarchitektur von platformengineering.org

Es ist wichtig, Ihre Referenzarchitektur an die Umgebungen anzupassen, in denen sie ausgeführt wird.

Wichtiger Hinweis

Die Umgebung, die Sie für Ihre Plattform wählen, schreibt automatisch einige Teile Ihrer Plattform vor, ob es Ihnen gefällt oder nicht! Eine exponentielle Zunahme der Anzahl von Cloud- und Infrastrukturanbietern erhöht die Herausforderungen für Ihr Plattformdesign.

Erweiterung der Referenzarchitekturen um eine Funktionsebene

Die Schwachstelle der meisten Referenzarchitekturen ist, dass sie keinen Überblick über die Fähigkeiten bieten, die von den Komponenten bereitgestellt werden, die auf der tatsächlichen Plattform-Laufzeitumgebung ausgeführt werden. Diese Perspektive ist erforderlich, da Benutzer ohne sie die Features und Funktionen der Plattform nicht nutzen können.

In der nächsten Abbildung finden Sie einige Referenzen für die Fähigkeitsebene:

- **Benutzerbereich**: Die tatsächliche Umgebung, die der Benutzer sieht und zum Hosten seiner Anwendungen nutzen kann
- **Skalierung und Zeitplanung**: Funktionen, die die Benutzeranwendung dabei unterstützen, auf Ereignisse zu reagieren, herunterzuskalieren oder benutzerdefinierte Zeitplanungsoptionen bereitzustellen
- **Netzwerk**: Zur Verarbeitung des Eingangs- und Ausgangsverkehrs, zur automatischen Verwaltung von DNS-Einträgen oder zum Lastenausgleich im Cluster
- **Heavy Babies**: Dinge, die Sie in der Regel lieber verwalten lassen, als selbst zu betreiben, wie z. B. ein Framework für die Stapelverarbeitung oder das Streaming von Nachrichten
- **Ressourcenintegration**: Eine wichtige Komponente, die die tatsächlichen Infrastrukturressourcen mit der Plattform-Laufzeit verbindet; Speicher- oder GPU-Integration, aber auch Ressourcensteuerung, beispielsweise mit dem Tool Crossplane
- **Sicherheit und Compliance**: Bereitstellung von Funktionen zur Verwaltung und Speicherung von Geheimnissen, zum aktiven Scannen von Clustern und Anwendungen auf CVEs und Schwachstellen
- **Beobachtbarkeit**: Dies bietet einen einfachen und schnellen Einstieg in die Beobachtbarkeit, vereinheitlicht die Datenerfassung oder hilft bei der Kostenkontrolle

Abbildung 2.9: Die Funktionsebene mit Beispiel-Tools

Die Funktionsebene ist für die eigentliche Anwendungsbereitstellung und den Betrieb von entscheidender Bedeutung. Hier findet die größte technische Interaktion statt, und wenn die Anwendung des Benutzers hier versagt, sind alle anderen investierten Anstrengungen umsonst.

Eine Plattformarchitektur geht über Referenzen hinaus

Zusammenfassend lässt sich sagen, dass Referenzarchitekturen ein leicht verständliches Konzept der Plattform vermitteln. Was sie nicht bieten, ist die tatsächliche Architektur der Plattform. Wo läuft die Versionsverwaltung des Quellcodes? Wo befinden sich die CI/CD-Pipeline-Komponenten? Wo ist die Container-Registry? Wie wird der IDP gehostet?

Daher müssen wir als Plattformarchitekten eine tatsächliche Plattformarchitektur bereitstellen, die visualisiert, wo sich diese Komponenten befinden. Dies gibt einen tiefen Einblick in weitere Abhängigkeiten, Netzwerkkommunikation und Anforderungen, Verfügbarkeit und Skalierbarkeit der Plattform mit all ihren Komponenten oder einfach darin, ob zu viele Teile eingebaut sind, die der Stabilität der Plattform nicht wirklich zuträglich sind.

Das folgende Diagramm zeigt, wie eine solche Architektur aussehen könnte. Sie werden auch sehen, dass verschiedene Komponenten und Netzwerkverbindungen verteilt sind. Wenn man jedoch von einer Plattformarchitektur spricht, sollte sie technisch gesehen so dargestellt werden.

Abbildung 2.10: Plattformarchitektur

Es ist schwierig, den richtigen Ansatz zu finden, um die Infrastruktur- und Plattformkomponenten in einem Diagramm darzustellen. Es ist nicht der sauberste Ansatz, aber es ist notwendig, alle Abhängigkeiten und gegenseitigen Einflüsse hervorzuheben. Halten Sie es so einfach wie möglich, aber so detailliert wie erforderlich. Sie können es sogar in verschiedene Diagramme aufteilen, um bestimmte Informationen hervorzuheben.

Verantwortung für Ihre Architekturen übernehmen

Es scheint viel Papierkram zu sein, verschiedene Versionen und Varianten einer Architektur zu verwalten und zu handhaben. Möglicherweise haben Sie jedoch bereits die Erfahrung gemacht, dass sich eine Plattform schneller verändert als die Diagramme. Wichtig ist, dass weder das Diagramm als Ergebnis Ihrer Arbeit als Architekt die Entwicklung der Plattform verlangsamt, noch dass die Plattformentwicklung die Diagramme verlangsamt. Ich habe Projekte gesehen, in denen Architekten zu einer herausragenden hierarchischen Institution wurden. Alle diese Projekte scheiterten und hatten Schwierigkeiten, das Richtige zu tun. Als Architekt sind Sie nicht allwissend, aber Sie sind auch nicht das Plattform-Entwicklungsteam. Zusammenarbeit, Abstimmung und Synchronisation sind der Schlüssel, fast wie bei der Plattform, die Sie aufbauen möchten.

Das Gleiche gilt für Ihre Architekturen. Sie müssen sie besitzen, aber nicht beherrschen. Eine Architektur muss ein Spielplatz für Ideen, ein Kommunikator für zukünftige Entwicklungen und eine Quelle der Wahrheit in Bezug auf die Fähigkeiten der Plattform sein. Das ist nur möglich, wenn Sie dafür verantwortlich sind, sie mit den Beiträgen anderer voranzutreiben.

Später in diesem Buch werden wir ein relevantes Thema behandeln, wenn wir über die Verantwortung für Ihre Architektur sprechen: den Umgang mit technischen Schulden.

Meinungsstarke Plattformen und die Kosten für Qualität

Bei der Architektur einer Plattform treten zwei Probleme auf: meinungsstarke Tools und die Kosten für Qualität. Für beide gibt es sehr gute Argumente, aber auch sehr starke Gegenargumente.

Meinungsstarke Tools und Produkte

Meinungsstarke Tools, Produkte und Dienstleistungen betonen ein striktes Konzept und bieten keine Alternativen. Praktisch alles kommt mit einer Meinung daher, aber die Frage ist, wie flexibel und kombinierbar sie sind. Eine starke Meinung darüber, wie etwas gemacht werden sollte, erleichtert die folgenden Entscheidungen, da der Lösungsraum kleiner wird. Mit einer wachsenden Nutzerbasis für einen solchen Ansatz könnte er dominant werden und schließlich zu einem De-facto-Standard werden. Wir müssen sie in unserer Architektur sorgfältig berücksichtigen und uns über ihre potenziellen zukünftigen Auswirkungen im Klaren sein.

Nun kann die strikte Umsetzung eines Konzepts viele Vorteile mit sich bringen. Beispielsweise ist jede Lösung im Bereich der Bereitstellung von Kubernetes-Clustern meinungsstark. Sie bieten jedoch eine ganzheitliche Lösung, die konsistent und in der Regel produktionsreif ist. Solche Tools lassen sich auch schneller integrieren, wenn sie einen großen Themenbereich abdecken und andere Tools vorintegrieren. Dies kann andererseits auch ein Nachteil sein, da die Implementierung anderer Optionen mehr Aufwand erfordert. In einigen Fällen ist dies sogar fast unmöglich oder viel zu teuer.

Sie sollten auch zwischen den sichtbaren und großen Konzepten und den eher unsichtbaren, versteckten unterscheiden. Die ersten sind leicht zu identifizieren und zu bewerten. Sie verfügen über eine große Anzahl vordefinierter Integrationen und basieren in der Regel auf der Technologie eines einzigen Anbieters. Die kleinen und versteckten, eigenwilligen Tools sind schwieriger, da sie ihre Nachteile umso mehr offenbaren, je intensiver Sie sie nutzen.

Die Kosten für Qualität

Es gibt ein Sprichwort: Lieber einmal teuer kaufen als oft billig. Bei gut gemachten Plattformen ist dieses Sprichwort falsch. Eine produktorientierte Denkweise bedeutet kontinuierliche Investitionen. Es ist eher wie ein Garten, den man Tag für Tag pflegen muss, als wie eine Uhr, in die man einmalig investiert.

Die Kosten für Qualität sind ein multidimensionales Problem. Eine hochwertige Plattform, die höchstwahrscheinlich sehr eigenwillig ist, kann für bestimmte Anwendungsfälle die perfekte Lösung sein. Aber Qualität ist nicht umsonst und basiert auf hohen Investitionen oder Betriebsgebühren. In größeren Unternehmen gibt es so etwas wie eine interne Kostenteilung. Das bedeutet auch, dass man sich die Kosten für Qualität teilen muss. In der Endnutzer-Community sehen wir häufig, dass solche Plattformen zu Frustrationen führen. Die Einstiegshürde aufgrund der Kosten ist dann zu hoch für das Hosting einfacher Anwendungen oder zu eigenwillig, um ein sehr komplexes Anwendungssystem darauf auszuführen. Dies veranlasst andere dazu, ihre eigene Plattform und Lösungen für ihre Anwendung von Grund auf neu zu entwickeln. Wie Sie sehen, ist dies ein seltsames Problem. Aufgrund der hohen Kosten der Plattform werden auch die Betriebskosten für einen Nutzer hoch, während die eigenwillige Lösung nicht wirklich das bietet, was man braucht. Das nennt man die **Kosten der Qualität**.

Sie können dieses Problem jedoch auch nicht umgehen, indem Sie schnell einige zufällige Tools zusammenstecken und so eine billige und möglichst offene Plattform anbieten. Dies könnte zwar zu einem anfänglichen schnellen Anstieg von Projekten führen, die die Plattform übernehmen, aber ich kann Ihnen versprechen, dass diese Lösungen umso schneller wieder verschwinden werden, je schneller sie zu Ihnen kommen. Denken Sie daran, dass Sie mit einer produktorientierten Denkweise Ihren Benutzern ermöglichen möchten, Dinge selbst zu tun, während Ihre Plattform ihnen alle schweren Aufgaben abnimmt. Im Idealfall muss Ihr Benutzer auch kein Experte für alle verwendeten Technologien sein.

Auf strategischer Ebene beeinflusst das Problem der Qualitätskosten viele Entscheidungen. Wir haben Plattformen gesehen, die jahrelang entwickelt wurden, nur um am Ende aufgrund ihres Preis-Leistungs-Verhältnisses in Frage gestellt zu werden.

Sie müssen den goldenen Mittelweg für Ihre Plattform finden. Gehen Sie jedoch nicht davon aus, dass eine perfekte Plattform den Anforderungen anderer entspricht. Wenn Sie dieses Problem in Phasen angehen, ist das ein klares Zeichen dafür, dass Sie die Produktmentalität mit Nutzerorientierung aus den Augen verloren haben.

Erstellen Sie Ihre eigene Architektur

Es ist Zeit zu handeln. Bisher haben wir alle relevanten Input-Quellen, Themen und Perspektiven behandelt, die zu berücksichtigen sind, damit wir mit der Erstellung einer Architektur beginnen können. Daher haben wir eine Vorlage vorbereitet, die Sie im GitHub-Repository für dieses Buch oder als Miro-Vorlage für die Zusammenarbeit finden.

In diesen Vorlagen werden Sie durch verschiedene Schritte und Architekturdiagramme geführt, um Ihre Plattformarchitektur aufzubauen:

1.  Erstellen Sie Ihre Referenzarchitektur.
2.  Konzentrieren Sie sich auf die Fähigkeitsebene und die Komponenten.
3.  Definieren Sie die Infrastrukturarchitektur für die Plattform.
4.  Visualisieren Sie den Kontrollfluss der Plattform.

Da Architektur ein lebendiges Konstrukt ist, müssen Sie sie wiederholt überarbeiten und dabei den Zyklus PLANEN, AUSFÜHREN, ÜBERPRÜFEN, HANDELN befolgen.

Nehmen Sie sich Zeit, um die Vorlagen durchzugehen:

- **GitHub**: https://github.com/PacktPublishing/Platform-Engineering-for-Architects/tree/main/Chapter02
- **Miro**: [https://miro.com/miroverse/platform-architecture-workshop](https://miro.com/miroverse/platform-architecture-workshop%0A)

Erstellen Ihrer Referenzarchitektur

Die Referenzarchitektur umreißt Ihre geplanten Komponenten, kategorisiert sie und verankert sie an vorderster Front Ihrer Plattformimplementierung. Dies ist auch Ihre Hilfe bei der Definition der Abhängigkeitskarte zu einem bestimmten Zeitpunkt.

Um Ihr Referenzarchitekturdiagramm mit Leben zu füllen, empfiehlt es sich, entweder mit den bereits festgelegten Komponenten oder der gegebenen Infrastruktur zu beginnen. Feste Komponenten können beispielsweise CI/CD-Tools oder Sicherheitslösungen sein. Zu Beginn ist die Infrastruktur relevant, da sie die bereitgestellten Ressourcen beeinflusst. Wenn Sie sich für einen Public-Cloud-Anbieter entscheiden, können viele Dienste als Managed Solution genutzt werden. In einigen Fällen definiert dies auch, welche **Infrastructure as Code** (**IaC**) Sie verwenden werden, oder umgekehrt: Wenn Sie sich nur für einen Infrastructure-as-a-Service-Anbieter entscheiden, müssen Sie über potenzielle Dienste nachdenken, die an anderer Stelle in der Plattform ausgeführt werden. Höchstwahrscheinlich landen sie in der Capability-Ebene, was dann folgende Frage aufwirft: Benötigen wir einen dedizierten Cluster für gemeinsam genutzte Dienste oder implementieren wir einen Ansatz, bei dem der Dienst vor Ort im Namespace der Benutzer bereitgestellt wird?

Als Nächstes befassen Sie sich mit der Automatisierungs- und Orchestrierungsebene. Aus irgendeinem Grund ist diese Ebene relativ vorbestimmt und bietet eine solide Grundlage für Entscheidungen für die Entwicklererfahrungsebene. Sie sollten sicherstellen, dass die gegebenen Lösungen auf einer neueren Version basieren und ohne Skripting in andere Cloud-native Dienste integriert werden können.

Zu guter Letzt müssen Sie sich mit der Observability- und der Sicherheitsebene befassen. Wie bereits erwähnt, kann es sein, dass Sie bereits Lösungen definiert haben. Aber insbesondere für Unternehmen, für die diese Plattform-Engineering- und Cloud-Native-Reise neu ist, könnten Sie die vorgegebenen Lösungen in Frage stellen. Sicherheitstools müssen in der Lage sein, die Cloud und Kubernetes zu verstehen. Sie müssen in diese Plattformen integriert werden und mit deren sehr dynamischer Natur umgehen können. Das Gleiche gilt für Observability- und Betriebslösungen. Sie möchten nicht jedes Mal eine Warnmeldung erhalten, wenn Pods im Cluster beendet oder verschoben werden.

Am wichtigsten ist, dass Sie am Ende alle Perspektiven zusammenführen: die Prinzipien und den Zweck der Plattform, ihre Hauptnutzer, ihre Kombinierbarkeit und die gegenseitige Beeinflussung all dieser beweglichen Komponenten. Aber Ihr Entwurf muss nicht perfekt sein. Bevor Sie sich zu tief in den Entwurfsprozess vertiefen, lesen Sie weiter, denn wir behandeln das Thema TVP später in diesem Kapitel.

Fokus auf die Fähigkeitsebene und Komponenten

Wenn die Referenzarchitektur steht, müssen wir sie im nächsten Schritt um die Fähigkeitsebene erweitern. Dies ist sicherlich ein großer Schritt, da es buchstäblich Hunderte von Open-Source-Lösungen für jede Anforderung innerhalb der Fähigkeitsebene gibt. Falls Sie die CNCF-Landschaft noch nie gesehen haben, zeigt die folgende Momentaufnahme etwa ein Drittel aller verfügbaren, von der CNCF gelisteten Open-Source-Projekte \[7\].

Abbildung 2.11: CNCF-Landschaft (Das Bild dient als visuelle Referenz; die Textinformationen sind nicht wesentlich.)

Beachten Sie, dass es mindestens eine Handvoll anderer Open-Source-Organisationen gibt, die ebenfalls Dutzende von Projekten verwalten, die Sie zum Cloud-Native-Bereich zählen können.

Das Gute und das Schlechte am Cloud-Native-Universum ist, dass Sie für jedes Mikroproblem mindestens drei ± 1 Optionen zur Lösung haben.

Für die Fähigkeitsebene wird ebenfalls empfohlen, von unten nach oben zu arbeiten:

- Welche Integrationen in die Ressourcen benötigen wir?
- Wie stellen wir die Betriebsdaten für die Observability-Lösung bereit? Müssen wir zwischen Infrastruktur- und Anwendungsbereich unterscheiden, und wenn ja, wie?
- Stellen Sie sicher, dass Sicherheits- und Compliance-Maßnahmen korrekt in die Umgebung des Benutzers übertragen werden.
- Wie gehen wir mit dem Netzwerkverkehr um? Benötigen wir eine Verschlüsselung innerhalb des Clusters?
- Stellen wir eine API zur Verfügung oder integrieren wir sie in eine Cloud-API?
- Was könnte für die Skalierung und Planung erforderlich sein? Gibt es zusätzliche Funktionen, die bereitgestellt werden müssen?

Rechnen Sie damit, dass Sie die meiste Zeit auf der Funktionsebene arbeiten werden. Mit jedem neuen Benutzer und Produkt werden neue Anforderungen hinzukommen. Das Beste daran ist, wenn Sie beobachten können, wie sich die Produkte weiterentwickeln und anspruchsvollere Funktionen erfordern.

Konzentrieren Sie sich auch hier zunächst auf das Wesentliche. Die richtige Netzwerkverwaltung und Speicherintegration ist wichtiger als die Bereitstellung einer Machine-Learning-Workbench-Lösung oder neuer Container-Laufzeiten wie **WebAssembly** (**Wasm**) \[8\].

Definition der Infrastrukturarchitektur für die Plattform

Nach dem unterhaltsamen Teil der Definition der Referenzarchitektur müssen wir uns direkt der ernsthaften Architekturdefinition zuwenden. Was wie ein Witz klingt, wird ziemlich oft übersprungen, doch viele Plattformen können diese Ansicht nicht bieten. Tatsächlich ist dieses Diagramm für die Implementierung, die Architekturdiskussion sowie die Sicherheits- und Compliance-Prüfungen relevanter als die Referenzarchitektur. Es ist jedoch auch schwieriger zu verstehen.

Wie bereits erläutert, müssen wir auf der einen Seite eine Infrastrukturarchitektur mit den jeweiligen Komponenten der Plattform kombinieren. Dies hilft uns zu verstehen, wo sich alles in unserer Systemlandschaft befindet und welche Verbindungen erforderlich sind.

Das Diagramm muss die verschiedenen Umgebungen hervorheben, in denen die Computing-Infrastruktur genutzt wird, welche Managed Services in Anspruch genommen werden, wie diese miteinander verbunden sind und welche externen Verbindungen bestehen. Jede Organisation hat ihre eigene Art, solche Diagramme zu zeichnen, wobei sie entweder vorgegebene Standards befolgt oder vereinfacht vorgeht. Unsere Vorlage versucht, einen Mittelweg zu finden.

Sie können auch die Hervorhebungen im Architekturdiagramm variieren. Wir sehen oft eine große Relevanz in der Visualisierung der genauen Netzwerkverbindung, der Netzwerkisolierung oder der Protokolle. Die Kombination einer isolierten Umgebung mit einem entsprechenden Kontrollfluss und der Art und Weise, wie Updates darin umgesetzt werden, nutzt beide Arten von Diagrammen, um das Verständnis zu maximieren.

Denken Sie daran, Dinge wie Verwaltungsumgebungen/Cluster, Staging-Umgebungen für Integrationstests oder sogar einen Schritt vor der Entwicklungsumgebung in das Diagramm aufzunehmen. Aus Gründen der Kontinuität können auch Backup und Wiederherstellung hilfreich sein. Je mehr Sie daran arbeiten, desto mehr Details werden Sie entdecken. Wenn ein Diagramm zu komplex wird, sollten Sie verschiedene Versionen bereitstellen.

Visualisierung des Kontrollflusses der Plattform

Neu für Sie könnte der **Kontrollfluss** sein. Er ist der erste gute Schritt eines prozessähnlichen Ansatzes, um bestimmte relevante Pfade für die Verwaltung der Plattform und der Benutzerergebnisse freizugeben. Innerhalb einer Plattform gibt es mehrere Flüsse; diese drei sind die wichtigsten:

- **Bereitstellung der Infrastruktur**: Dieser Fluss visualisiert die Bedeutung der Infrastruktur-Testumgebungen und wie sich Änderungen auf dieser Ebene auf sie auswirken können, vom Commit des IaC-Manifests in einem Versionsverwaltungssystem über die Bereitstellung und das Testen bis hin zur endgültigen Einführung.
- **Vom Code zur Bereitstellung**: Dies ist für die Plattformnutzer am relevantesten. Wie wird der festgeschriebene Code aufgegriffen, um gebaut, integriert, gescannt und getestet zu werden? Wie sieht der Entwicklungs- und Lebenszyklusprozess aus?
- **Verwaltung der Plattformfunktionen**: Dies ist besonders relevant für die Plattformingenieure, die sich um die vom Cluster bereitgestellten Komponenten kümmern.

Es gibt viele weitere kleinere Kontrollflüsse, die uns helfen können, die Plattform zu verstehen, wie z. B. die Verwaltung von Geheimnissen und Zertifikaten oder die Benutzerverwaltung.

Wir verlassen nun die Theorie und wenden uns konkreten Anwendungsfällen zu. Wir werden uns einige Beispiele für verschiedene Plattformtypen und -implementierungen ansehen. Im nächsten Teil werden Sie Ihren Blickwinkel von allgemeinen Plattformen auf spezialisierte Lösungen erweitern.

Plattformen als Produkt erkunden – Anwendungsfälle und Implementierungen

Wir haben viel über den Zweck der Plattform gesprochen, beispielsweise über Self-Service First. Aber wie erreichen wir dies und welche Anwendungsfälle möchten wir als Self-Service anbieten?

Jedes Unternehmen hat leicht unterschiedliche Anwendungsfälle und Implementierungen für eine Plattform. Das liegt daran, dass jedes Unternehmen über einen anderen Technologie-Stack und andere ältere/bestehende Tools und Prozesse verfügt, die für eine Optimierung in Frage kommen.

In diesem Abschnitt diskutieren wir Anwendungsfälle, die wir in Unternehmen gesehen haben, mit denen wir im Laufe der Jahre zusammengearbeitet haben. Wir können davon ausgehen, dass einige davon gute Kandidaten für Ihre eigene zukünftige Plattform-Engineering-Initiative sind.

Experten finden und die von ihnen verursachten Engpässe

Es gibt einen großartigen Blogbeitrag von Thoughtworks mit einem Zitat, das uns dabei hilft, mit der Suche nach guten Anwendungsfällen zu beginnen \[9\].

Was macht etwas zu einer Plattform?

Plattformen sind ein Mittel, um Fachwissen zu zentralisieren und gleichzeitig Innovationen an den Kunden oder Nutzer zu dezentralisieren.

Mit anderen Worten: In jeder IT-Organisation, die Software zur Unterstützung ihres Geschäfts produziert, ausliefert und betreibt, finden wir Experten für Themen wie Bereitstellung von Infrastruktur, Zugriffskontrolle, Erstellung und Bereitstellung von Artefakten, Beobachtbarkeit, Qualitätssicherung, Release-Management, Kapazitätsplanung, **Site Reliability Engineering** (**SRE**), Incident Response, Datenanalyse, Automatisierung, Business Insights und so weiter.

Das Ziel unserer Plattform ist es, Anwendungsfälle und das dafür erforderliche Fachwissen zu identifizieren und diese Anwendungsfälle dann auf einfache Weise als Self-Service für alle bereitzustellen, ohne dass jedes Mal ein Experte hinzugezogen werden muss.

Zentralisieren Sie Fachwissen durch einen Self-Service

Ermöglichen Sie es jedem, seine Arbeit zu erledigen, ohne ein Experte sein zu müssen oder einen Experten in allen Bereichen zu befragen, die für die Erledigung seiner Arbeit erforderlich sind!

Wenn wir uns nun den gesamten **Softwareentwicklungslebenszyklus** (**SDLC**) innerhalb dieser Organisationen ansehen und alle Aufgaben, Experten und die benötigte Zeit von der ersten Idee einer neuen App oder Funktion bis zur Veröffentlichung für Endbenutzer auflisten, können wir viele Engpässe identifizieren, die den SDLC verlangsamen. Dies liegt entweder daran, dass bestimmte Aufgaben manuell ausgeführt werden müssen oder dass jemand mit Expertenwissen erforderlich ist, um eine Aufgabe zu erledigen. Da Experten in der Regel rar sind, werden sie zu gemeinsamen Ressourcen, auf die Teams warten müssen, wenn sie ihre neue Funktion auf den Markt bringen wollen.

In [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3), im Abschnitt „Den bestehenden SDLC verstehen“, werden wir uns genauer ansehen, wie man den aktuellen SDLC oder den Wertschöpfungsprozess innerhalb eines Unternehmens am besten versteht. Sie lernen verschiedene Ansätze zum Verständnis des Lebenszyklus eines Artefakts, der damit verbundenen Aufgaben und Abhängigkeiten kennen und erfahren, wie Sie die Zeit verfolgen können, um geeignete Kandidaten für die Automatisierung dieser Aufgaben als Teil eines Plattformangebots zu identifizieren.

Lassen Sie uns nun einige dieser Anwendungsfälle und Implementierungsoptionen von Organisationen untersuchen, mit denen wir in der Vergangenheit zusammengearbeitet haben!

Zentralisierung von Fachwissen als Self-Service-Anwendungsfall

Es gibt zwar noch viele weitere Anwendungsfälle, aber hier sind einige Beispiele, die Sie wahrscheinlich als Self-Service-Funktion als Teil Ihrer Plattform implementieren werden.

Bereitstellung konformer Umgebungen

Je nach Branche gibt es bestimmte Vorschriften darüber, wie Daten gespeichert werden müssen, wie Umgebungen gesichert werden müssen und welche Art von Berichterstattung erforderlich ist. Um sicherzustellen, dass jede Umgebung, die von einem Team in einem Unternehmen angefordert wird, all diesen Regeln entspricht, können wir dies als Self-Service-Funktion unserer Plattform implementieren.

Hier ist eine User Story für diesen Anwendungsfall: „Als Datenwissenschaftler möchte ich meine neuen Datenmodelle anhand eines produktionsähnlichen Datensatzes validieren!“

Es gibt mehrere Details, die geklärt werden müssen, um diese Geschichte in einzelne Aufgaben zu unterteilen, wie zum Beispiel die folgenden: Woher kommen diese Datensätze? Möchte der Datenwissenschaftler einen aus mehreren verfügbaren auswählen? Was ist das Ergebnis der Validierung, wo wird es gespeichert und wer hat Zugriff darauf? Wie wählt man das Datenmodell aus? Wie lange dauert diese Validierung und benötigen wir eine maximale Zeit, um die Umgebung herunterzufahren, um unnötige Kosten zu vermeiden? Welche Art von Audit-Daten müssen wir erstellen, da es sich um den Zugriff auf Produktionsdaten handelt?

Eine weitere ähnliche User Story könnte lauten: „Als QA-Ingenieur möchte ich meine manuellen Tests mit der neuesten Version unserer Software durchführen, die mit einer Produktionsdatenbank verbunden ist, und dabei eine Browser-/Betriebssystemkombination verwenden, die der von 80 % unserer Endbenutzer entspricht!“

Ähnlich wie bei der vorherigen User Story müssen wir einige zusätzliche Fragen stellen, wie zum Beispiel: Um welches Softwareprodukt handelt es sich, das Sie testen möchten, und wie kann es automatisch bereitgestellt werden? Wo finden wir die Daten über die Browser-/Betriebssystemnutzung unserer Produktionsnutzer? Wie lange muss diese Umgebung verfügbar sein? Können wir eine Ablaufzeit für diese bereitgestellte Umgebung festlegen? Welche Daten darf der Ingenieur sehen und welche Daten darf er nicht sehen, da es sich um den Zugriff auf Produktionsdaten handelt?

Die Umsetzung eines solchen Anwendungsfalls kann sehr unterschiedlich sein, aber wir sollten immer mit der Endbenutzererfahrung beginnen und diese berücksichtigen. Wahrscheinlich möchten wir, dass sich unsere Datenwissenschaftler oder Qualitätsingenieure bei unserem internen Entwicklungsplattform-Portal anmelden. Dort können sie den Anwendungsfall der Bereitstellung einer konformen Umgebung auswählen. Anschließend können sie die relevanten Daten eingeben, um alle aufgeworfenen Fragen zu beantworten. Diese Eingaben können dann verwendet werden, um diese Umgebung zu erstellen und sie dem Team, das sie angefordert hat, zur Verfügung zu stellen.

Durchführung von Leistungs- und Ausfallsicherheitstests

Leistungs- und Ausfalltests sollten Teil jeder Softwareversion sein, um sicherzustellen, dass neue Funktionen die Benutzererfahrung nicht beeinträchtigen, indem sie extrem langsam werden. Wir möchten auch sicherstellen, dass unsere neue Software gegen unvorhergesehene Szenarien wie Netzwerkverbindungsprobleme, langsame oder nicht verfügbare Backend-Dienste oder Daten oder eine unerwartet hohe Auslastung resistent ist.

Es gibt zwar viele Tools, die Datenverkehr generieren (Lasttest-Tools) oder Probleme simulieren (Chaos Engineering) können, aber diese Tools und die dafür erforderlichen Umgebungen erfordern oft viel Fachwissen, um sie einzurichten, zu konfigurieren, auszuführen und später die Ergebnisse zu analysieren.

Anstatt unsere Performance-, Site-Reliability- oder Chaos-Engineers zum Engpass werden zu lassen, können wir uns bemühen, dieses Fachwissen zu zentralisieren und es unseren Engineering-Teams als Self-Service zur Verfügung zu stellen. Hier wäre die richtige User Story: „Als Entwicklungsteam möchten wir wissen, ob die neueste Version unserer Software Leistungseinbußen oder eine geringere Ausfallsicherheit aufweist!“

Es könnte mehrere Iterationen dieser Self-Service-Funktion geben, die wir implementieren könnten. Ausgehend von der Bereitstellung der Umgebung, die die relevanten Tools enthält, müssen die Entwickler lediglich die Tests ausführen und auf die Ergebnisse warten. Im Idealfall möchten wir jedoch eine Situation erreichen, in der dies vollständig automatisiert und sogar in unseren Entwicklungsprozess integriert werden kann. Wir sollten etwa Folgendes anstreben: „Als Entwicklungsteam möchten wir einen Leistungs- und Ausfallsicherheitsindikator für wichtige Pull-Anfragen erhalten, damit wir wissen, ob die neueste Codeänderung gut genug ist, um in die Produktion übernommen zu werden!“

Wie im vorherigen Beispiel könnten wir mit einem Portal beginnen, über das Teams die Leistungstestumgebung anfordern können. Um die zweite, vollständig automatisierte User Story zu erfüllen, müssen wir über die Bereitstellung einer API nachdenken, die vom CI/CD-Pipeline-System aufgerufen werden kann, alle relevanten Eingabeparameter abruft und dann das tatsächliche Ergebnis des ausgeführten Tests zurückgibt.

Onboarding einer neuen Anwendung

Die Erstellung neuer Anwendungen oder Dienste ist die Aufgabe von Entwicklungsteams. Dazu müssen sie in der Regel viele verschiedene Schritte durchlaufen, wie z. B. die Erstellung eines neuen Git-Repositorys, das Hinzufügen von Boilerplate-Code und Metadaten-Einstellungen, die Konfiguration der Build-Pipelines (CI) und viele weitere Schritte.

Wenn jedes Entwicklungsteam immer bei Null anfangen würde, hätten wir nicht nur mehrere verschiedene Möglichkeiten, im Wesentlichen dasselbe zu tun, sondern auch eine Menge doppelter Arbeit in allen Entwicklungsteams, die Zeit für die eigentliche Programmierung kostet.

Eine gute User Story für eine Self-Service-Funktion der Plattform wäre folgende: „Als Entwicklungsteam möchten wir eine neue Anwendung auf der Grundlage einer vollständig konfigurierten Vorlage erstellen, damit wir uns auf das Schreiben von Code konzentrieren können und uns nicht mit dem Erstellen, Bereitstellen und Betreiben befassen müssen!“

Betrachtet man den gesamten SDLC, kann unser Self-Service sogar einen Schritt früher beginnen, nämlich mit den Funktionsanforderungen, die vom Produktteam mit Tools wie **Jira** erstellt wurden. Die folgende Abbildung 2.12 zeigt den End-to-End-Onboarding-Workflow einer neuen Anwendung in einer der Organisationen, mit denen die Autoren zusammengearbeitet haben:

Abbildung 2.12: End-to-End-Anwendungs-Onboarding als Self-Service (Das Bild dient als visuelle Referenz; die Textinformationen sind nicht wesentlich.)

Für Entwicklungsteams beginnt die Reise mit dem Jira-Ticket. Anschließend gehen sie zu Backstage, dem von dieser Organisation ausgewählten IDP, wo sie den Self-Service-Assistenten für das Onboarding von Anwendungen durchlaufen. Dieser Assistent erstellt ein neues Git-Repository, das mit einsatzbereiten Codevorlagen, Pipelines, Bereitstellungsanweisungen, Konfigurationen für die Beobachtbarkeit, Eigentumsrechten und vielem mehr vorinstalliert ist. Sobald der Code committet ist, stellen die Pipelines das Artefakt automatisch in einem Entwicklungscode-Bereich bereit, der automatisch mit Visual Studio Code verbunden wird!

Zugriff auf Observability-Daten für die Reaktion auf Vorfälle

Sobald neue Software in der Produktion bereitgestellt wird, verlagert sich der Fokus der Entwickler in der Regel auf die nächste Anwendung oder Funktion. Wenn jedoch eine Katastrophe eintritt, ist es an der Zeit, dass sie das Operations- oder SRE-Team bei der Fehlerbehebung unterstützen, um alle aufgetretenen Probleme zu beheben.

In vielen Unternehmen ist der Zugriff auf Telemetrie- oder Beobachtungsdaten in der Produktion auf ausgewählte Teams beschränkt, die sich um diese Produktionsumgebungen kümmern. Es gibt auch Compliance-Gründe, da nicht jeder Zugriff auf potenziell sensible Daten haben sollte. Wenn man jedoch im sogenannten War Room sitzt, ist es wichtig, schnell auf die relevanten Observability-Daten zugreifen zu können, ohne zu viele Antragsformulare ausfüllen, Daten von einer Umgebung in eine andere kopieren oder Daten aus dem Produktions-Observability-Tool in ein Format konvertieren zu müssen, das die Entwickler gewohnt sind.

In [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3) gehen wir näher auf diesen Anwendungsfall ein, daher beschränken wir uns hier auf die User Story: „Als Entwicklungsteam möchten wir einfachen Zugriff auf die relevanten Observability-Daten für einen Produktionsvorfall erhalten, um das Problem schnell zu lösen!“

Nachdem wir nun einige Anwendungsfälle haben, wollen wir uns ansehen, wie wir diese Ideen in etwas umsetzen können, das unsere Benutzer tatsächlich nutzen und von dem sie profitieren können.

TVPs verstehen

Im Produktmanagement sprechen wir in der Regel von einem **Minimum Viable Product** (**MVP**). Das MVP definiert die einfachste Version eines Produkts, die Sie entwickeln müssen, um es auf dem Markt zu verkaufen. Das Konzept des MVP wurde ursprünglich durch die Lean-Startup-Bewegung von Eric Ries \[10\] eingeführt. Ich empfehle jedem, entweder das Buch oder die ausgezeichneten Blog-Beiträge auf der Website [theleanstartup.com](https://theleanstartup.com/) zu lesen.

Das Minimum im MVP bezieht sich auf eine Version eines Produkts, die dem Start-up-Team hilft, die Hypothese zu validieren, dass ihre Idee wirklich ein Problem oder einen Schmerzpunkt löst. All diese Lean-Startup-Ideen lassen sich direkt auf die Plattformentwicklung wie folgt anwenden:

- Unser Team ist das Start-up
- Unsere Plattform ist das Produkt
- Unser Zielmarkt sind unsere internen Nutzer
- Unsere Hypothese lautet, dass sie den Zweck erfüllt

In Lean Startup wird das MVP auch als die erste Version eines Produkts definiert, die gut genug ist, um ausgeliefert zu werden. Es ist gut genug, weil es bereits Probleme löst, auch wenn es vielleicht noch nicht alle Funktionen enthält. Es ist gut genug, um es den Nutzern zur Verfügung zu stellen, unsere Hypothese zu validieren und frühzeitig Feedback zu erhalten, auf dessen Grundlage wir iterieren und die nächste Version verbessern können.

Lassen Sie uns nun genauer betrachten, wie wir all diese Lean-Startup-Ideen anwenden und unser eigenes MVP definieren können – oder, wie wir es gerne nennen, unser TVP!

Finden Sie Ihren TVP-Anwendungsfall

In einem früheren Abschnitt haben wir bereits untersucht, welche Anwendungsfälle wir als Self-Service über unsere Plattform anbieten könnten. Wir haben sie identifiziert, indem wir untersucht haben, wo derzeit Experten benötigt werden, um eine Aufgabe zu erledigen, oder wo viel manuelle Arbeit erforderlich ist.

Wie bei jedem neuen Softwareprodukt gibt es wahrscheinlich viele großartige Funktionen, die wir implementieren möchten. Die Frage ist: Mit welcher sollten wir beginnen? Um dies zu beantworten, ist es am besten, anhand verschiedener Dimensionen Prioritäten zu setzen. Ein solcher Ansatz ist das ICE-Bewertungsmodell, aber Sie können auch jedes andere Bewertungsmodell verwenden, mit dem Sie vertraut sind oder das Sie bereits in Ihrem Unternehmen einsetzen \[11\]. **ICE** steht für **Impact** (die Auswirkungen, die wir mit dieser Funktion erzielen werden), **Confidence** (wie zuversichtlich wir sind, dass wir wirklich die gewünschten Auswirkungen erzielen) und **Ease** (der Aufwand, der mit der Umsetzung verbunden ist). Wir geben jedem Indikator einen Wert zwischen 1 und 10 und multiplizieren dann die Zahlen. Wenn wir dies für jede Feature-Idee tun, können wir leicht vergleichen und eine erste Prioritätenliste erstellen. So könnte dies für die vier zuvor besprochenen Anwendungsfälle aussehen, wobei wir einige fiktive Zahlen für die ICE-Bewertung verwenden:

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
| **Anwendungsfall** | **Auswirkung** | **Zuversicht** | **Einfachheit** | **Punktzahl** |
| Bereitstellung Konforme Umgebungen | 6 (gute Wirkung) | 5 (mittleres Vertrauen) | 2 (nicht einfach) | 60  |
| Durchführung von Leistungs- und Ausfallsicherheitstests | 6   | 5   | 5   | 150 |
| Einführung einer neuen Anwendung | 8   | 7   | 3   | 168 |
| Zugriff auf Observability-Daten | 8   | 8   | 3   | 172 |

Tabelle 2.1: Beispiel für eine ICE-Bewertung

Wie bereits erwähnt, sind die ICE-Bewertungen in der vorstehenden Tabelle nur fiktiv. Die Beispiele sollen Ihnen jedoch einen Eindruck davon vermitteln, wie diese Bewertung funktioniert. Eine andere Form davon umfasst auch die Reichweite, sodass sie als RICE bezeichnet wird. **Bei RICE** werden einfach Reichweite, Auswirkung und Zuverlässigkeit multipliziert und das Ergebnis durch den Aufwand geteilt, wodurch wir eine einfach zu verwendende Bewertung erhalten.

Basierend auf dem vorangegangenen Beispiel könnten wir argumentieren, dass wir entweder mit dem Onboarding einer neuen Anwendung oder dem Zugriff auf Observability-Daten beginnen sollten, da diese die höchsten Werte erzielt haben. Ander s könnten wir auch argumentieren, dass die Durchführung von Leistungs- und Ausfallsicherheitstests ein besserer Kandidat wäre, da dies am einfachsten zu implementieren scheint.

Unabhängig davon, ob Sie ICE, RICE oder ein anderes Modell verwenden, sollte es Ihnen helfen, eine Entscheidung darüber zu treffen, welcher Anwendungsfall zuerst angegangen werden soll, um schnell eine Wirkung zu erzielen. Bevor wir mit der Umsetzung beginnen, lassen Sie uns darüber sprechen, wie gut diese erste Umsetzung sein muss!

Gut genug oder perfekt gemacht?

Wir sind uns wahrscheinlich alle einig, dass ein Produkt so gut wie nie perfekt oder fertig ist! Es gibt immer das eine oder andere Feature, das wir gerne hätten, oder diesen lästigen Bug, von dem wir hoffen, dass ihn endlich jemand behebt. Wenn wir mit einem neuen Produkt wie unserer Plattform beginnen, müssen wir diese Denkweise ändern und uns mit einer ersten Version zufrieden geben, die gut genug ist. Das bedeutet nicht, dass wir Abkürzungen nehmen, sondern nur, dass wir unsere perfektionistische Mentalität beiseite lassen und den Mut haben müssen zu sagen: „Es ist gut genug – lasst es uns veröffentlichen!“

In „Lean Startup“ wird auf die Einführung von Google Maps verwiesen \[12\]. Anscheinend hat das Team dem Führungsteam von Google seine neue dynamische Webkartenlösung (unter Verwendung von AJAX) vorgeführt. Ihr Ansatz war der erste seiner Art. Das Managementteam war sehr beeindruckt, obwohl das Entwicklungsteam es noch als frühen Prototyp betrachtete. Larry und Sergey sagten Gerüchten zufolge einfach: „Es ist schon gut genug. Bringt es auf den Markt.“ Obwohl das Entwicklungsteam Vorbehalte und Befürchtungen hatte, tat es wie verlangt. Der Rest ist – wie wir alle wissen – Geschichte: Google Maps war und ist nach wie vor ein großer Erfolg. Dieser Erfolg beruhte darauf, dass die Lösung nur eine einzige Aufgabe erfüllte – diese Aufgabe jedoch extrem gut und als entscheidendes Unterscheidungsmerkmal zu allen anderen Lösungen auf dem Markt. Die Markteinführung mit nur einem begrenzten Funktionsumfang überraschte die Konkurrenz und verschaffte ihnen einen Vorsprung.

Wie lässt sich das auf unser TVP übertragen? Im Gegensatz zum Beispiel von Google müssen wir keine Konkurrenz fürchten – oder doch? Tatsächlich müssen wir das: Unsere Konkurrenz sind die Entwicklungsteams, die entweder ihre Zeit damit verschwenden, Dinge auf die gleiche Weise zu tun, oder ihre eigene Initiative starten, um Tools und Automatisierungen zu entwickeln, die das Problem nur für sie lösen, anstatt darüber nachzudenken, wie dies in großem Maßstab für das gesamte Unternehmen umgesetzt werden kann.

Das bedeutet, dass wir bei der ersten Implementierung unseres TVP nicht perfekt sein müssen, aber es muss gut genug sein, um zu zeigen, dass wir einen Mehrwert bieten. Was dieser Mehrwert ist, müssen wir in unserer Hypothese für die von uns implementierten Anwendungsfälle spezifizieren.

TVP – Validierung unserer Hypothese

Wir haben also unseren Anwendungsfall ausgewählt und wissen, dass unsere erste Lieferung gut genug sein muss, damit unsere Endnutzer sie verwenden und einen Mehrwert daraus ziehen können. Aber worin besteht dieser Mehrwert? Wie können wir messen und nachweisen, dass die Leistungsfähigkeit unserer Plattform tatsächlich Wirkung zeigt?

Hier kommt unsere Produkthypothese ins Spiel. Wenn wir uns die gleichen Anwendungsfälle wie zuvor ansehen, könnten wir die folgenden Annahmen über die gewünschten Auswirkungen treffen:

|     |     |     |
| --- | --- | --- |
| **Anwendungsfall** | **Hypothese** |     |
| Bereitstellung konformer Umgebungen | 80 % weniger Compliance-Verstöße bei der Validierung neuer Datenmodelle |     |
| Durchführung von Leistungs- und Ausfallsicherheitstests | 50 % weniger Skalierbarkeitsprobleme in der Produktion, da wir diese Probleme früher erkennen und beheben |     |
| Einführung einer neuen Anwendung | 20 % Verkürzung der Vorlaufzeit einer neuen Anwendung |     |
| Zugriff auf Observability-Daten | 50 % weniger Zeitaufwand für die Fehlerbehebung bei Produktionsproblemen |     |

Tabelle 2.2: Produkthypothese zur Validierung von Anwendungsfällen

Die Hypothese ist auch eine gute Möglichkeit, die Idee denjenigen Personen innerhalb des Unternehmens vorzustellen, die die Finanzierung für unsere Bemühungen bereitstellen müssen. Letztendlich verkaufen wir intern – und wir müssen überzeugende Argumente dafür liefern, warum wir Zeit und Geld in den Aufbau einer neuen internen Entwicklungsplattform investieren sollten. Diese Wertvorstellungen, die wir als Hypothesen bezeichnen, werden bei Ihrer Unternehmensleitung höchstwahrscheinlich großen Anklang finden.

Die letzte Frage, die noch offen ist, lautet: Wie können wir unsere Hypothese messen und validieren? Für manche dürfte es einfach sein, davon auszugehen, dass wir über Daten wie die Anzahl der Tickets für Compliance-Verstöße, Tickets für skalierbarkeitsbezogene Produktprobleme oder die für Incident-Response-Tickets gebuchte Entwicklungszeit verfügen. Schwieriger wird es bei der Vorlaufzeit, da zunächst erklärt werden muss, wie ein Unternehmen die Vorlaufzeit definiert. Beginnt sie mit der Erstellung der ersten Feature-Anforderung oder wenn der Entwickler mit der Arbeit daran beginnt? Wie messen wir außerdem den gesamten End-to-End-Stream? All dies ist zwar möglich, aber wir müssen sicherstellen, dass wir wissen, wie wir den Status quo messen können, um ihn dann mit den Zahlen vergleichen zu können, sobald wir unser TVP eingerichtet haben, um unsere Hypothese zu validieren.

Entwickeln, messen und lernen

Wir wissen, was wir entwickeln wollen, wie unsere Hypothese lautet und wie wir sie messen. Jetzt ist es an der Zeit, dies in die Tat umzusetzen. Wie bei jeder agilen Produktentwicklung wollen wir entwickeln, messen und lernen. Wir möchten unsere Endnutzer so früh wie möglich einbeziehen. Der beste Weg, dies zu tun, ist, sie bereits in der Prototyping-Phase einzubeziehen und von ihnen zu lernen. Kontinuierliches Feedback hilft uns, wichtige Entscheidungen frühzeitig zu treffen, anstatt zu warten, bis wir eine endgültige Version haben, die unsere Nutzer ablehnen, weil wir etwas sehr Offensichtliches übersehen haben.

Der Prozess lässt sich am besten mit dem folgenden Diagramm veranschaulichen, das Sie auch in vielen Publikationen finden, die vom Lean-Startup-Ansatz inspiriert sind:

Abbildung 2.13: Entwickeln, messen und lernen, um zu Ihrem TVP zu gelangen

Es handelt sich um einen kontinuierlichen Kreislauf, der versucht, die Zeit zwischen den Phasen „Entwickeln, Messen und Lernen” zu minimieren, damit wir Kurskorrekturen vornehmen oder umschwenken können, falls das Feedback aus unseren Messungen darauf hindeutet, dass wir auf dem falschen Weg sind.

Einige Meilensteine, die in diesem Kreislauf zu berücksichtigen sind, sind die folgenden:

- **Erster Prototyp**: Zeigen Sie diesen interessierten und potenziellen Power-Usern. Sie werden Ihnen frühzeitig wertvolles Feedback geben.
- **Gut genug**: Sobald Sie eine Phase erreicht haben, in der die User Story ihre Versprechen erfüllt, erweitern Sie sie auf eine Gruppe von Early Adopters, um ein breiteres Feedback zu erhalten.
- **Hypothese bestätigt**: Sobald Sie die Hypothese mit Ihren ersten Early Adopters bestätigt haben, ist es an der Zeit, dies dem Rest der Organisation vorzustellen und zu bewerben. Nutzen Sie Ihre Early Adopters, um die neuen Funktionen für Sie zu bewerben!

Das war's. Wir haben unser TVP!

Die TVP

Die TVP ist die Version unserer Plattform, die unseren Endnutzern einen Mehrwert bietet. Sie ermöglicht es dem Plattform-Entwicklungsteam, unsere Hypothese zu validieren, dass sie den Zweck unserer Anwendungsfälle erfüllt (z. B. Verringerung der kognitiven Belastung). Sie ermöglicht es uns, mit minimalem Aufwand ein Maximum an validierten Erkenntnissen für unsere nächste Produktiteration zu sammeln.

Wenn Sie mit der Einführung einer Plattform beginnen, ist es wichtig, deren Akzeptanz zu verfolgen und festzustellen, ob Sie auf dem richtigen Weg sind. Als Nächstes helfen wir Ihnen dabei, KPIs dafür zu definieren.

Betrachten Sie die relevanten KPIs, um die Akzeptanz transparent zu machen

Tue Gutes und rede darüber. (Georg Volkmar Graf von Zedtwitz-Arnim, 1978.)

Ein häufiges Problem, das wir bei vielen Plattformimplementierungen beobachten, ist der Mangel an Belegen für deren Vorteile. Theoretisch macht das alles Sinn, aber lassen Sie uns einige Zahlen dazu anführen. Darüber hinaus helfen sie Ihnen zu verstehen, ob Sie sich in die richtige Richtung bewegen.

Daher ist es hilfreich, verschiedene **KPIs** zu definieren, anhand derer man den Fortschritt der Plattformakzeptanz nachvollziehen kann. Im ersten Schritt sollten Sie darüber nachdenken, was Sie bereits messen. Sehr oft müssen wir nur die verfügbaren Zahlen richtig kombinieren, um neue Leistungsindikatoren definieren zu können.

Zunächst müssen wir die Metriken, Protokolle und Traces verstehen, definieren, wie wir die Werte erhalten, die sie darstellen, und was sie bedeuten. Obwohl alle diese Daten relevante Quellen sein können, sind die meisten für die Akzeptanz Ihrer Plattform nicht relevant. Dies repräsentiert nur die Systemseite. Dabei sollte klar sein, dass wir mehr an den Nutzern und ihrer Erfahrung interessiert sind. Supportkanäle, Ticket-Systeme, offene Pull-Anfragen, die Anzahl der Onboarding-Anfragen und andere interaktive Tools für Benutzer sind hilfreich, um die Anpassung zu verstehen. Die Bedeutung dieser Zahlen wird sich im Laufe der Zeit ändern. Beispielsweise sieht die Anzahl der Personen, die Zugang zur Plattform beantragen, in der Regel wie ein Hügel mit zwei flachen Seiten aus. Auf der einen Seite beginnt die Akzeptanz langsam, weil die Menschen zu schüchtern sind, um neue Dinge auszuprobieren. Auf der anderen Seite des Hügels werden weniger neue Projekte auf die Plattform gebracht. Ein weiteres Beispiel könnte die Anzahl der Supportanfragen sein. Diese steigt in der Regel mit der Anzahl der Nutzer. Da eine Plattform jedoch auf Selbstbedienung ausgerichtet ist, ist zu erwarten, dass diese Zahlen im Laufe der Zeit auf ein Minimum sinken, während Ihre Plattform besser wird und die Nutzer verstehen, wie sie zu bedienen ist.

Aus diesem Grund müssen Sie zweitens den aktuellen Kontext der KPIs Ihrer Plattform definieren. Es mag offensichtlich erscheinen, dass eine ausgereifte Plattform andere KPIs haben könnte oder dass Ihre Stakeholder diese KPIs anders lesen müssen, aber glauben Sie mir, das ist es nicht. Es liegt an Ihnen, dies für alle transparent, klar und verständlich zu machen.

Wichtiger Hinweis

KPIs und ihr aktueller Reifegrad müssen ausdrücklich angegeben werden.

Das folgende Diagramm zeigt beispielsweise, wie die KPIs im Vergleich zu einer Umgebung aussehen könnten, in der eine Plattform schlecht integriert ist. Die Zahlen basieren auf einigen Messungen aus verschiedenen Projekten und wurden hier verallgemeinert. Auf der linken Seite ist keine Verbesserung erkennbar, oder sie entwickeln sich weiter auf und ab. Am offensichtlichsten ist ein Anstieg der Supportanfragen. Im Zusammenhang mit einer geringeren Anzahl von Anwendungen, die diese nutzen, ist dies ein schlechtes Zeichen. Auf der rechten Seite sehen wir nun eine Verbesserung für alle KPIs. Die meisten Zahlen werden nicht auf Null sinken, aber sie werden unabhängig vom Wachstum der Plattform, der Endnutzerzahlen oder anderen langfristigen Auswirkungen stabil bleiben.

Abbildung 2.14: Vergleich der Auswirkungen der Plattform (links: ohne Plattform, rechts: mit Plattform)

Diesen Zahlen fehlt der Kontext. Wenn Sie einen bestimmten Zustand der Plattform während ihres Lebenszyklus angeben, werden die Zahlen aussagekräftiger. In der nächsten Abbildung haben wir ein Beispiel für eine Segmentierung hinzugefügt.

Mit den ersten Supportanfragen zur Einführung steigen die Kosten pro Änderung, während nur wenige Anwendungen migriert werden. Während der Anlaufphase ist zu sehen, dass die Anzahl neuer Anwendungen schnell zunimmt und gleichzeitig die Supportanfragen steigen. Die Kosten pro Änderung stagnieren. Im nächsten Segment der Optimierung sind nun erhebliche Veränderungen zu erkennen. Die Kosten pro Änderung und die Supportanfragen sinken in der Steig t stark. Die Anzahl neuer Anwendungen hat ihren Höhepunkt erreicht und geht langsam zurück, da die meisten Anwendungen, die eine Plattform nutzen könnten, migriert wurden.

Über die drei Phasen hinweg sinkt die Zeit pro Release. Dies ist ein Effekt der Automatisierung und des Self-Service und flacht im letzten Segment ab. Dies ähnelt fast allen anderen KPIs, die eine stetige Entwicklung aufweisen. Im Vergleich zu den anderen Diagrammen haben wir auch die Darstellung der Anzahl der hinzugefügten Anwendungen geändert. Jetzt können Sie die Anzahl der migrierten Apps pro Quartal sowie die Gesamtzahl der Anwendungen sehen.

Abbildung 2.15: Beispiel-KPIs mit der Segmentierung des Plattform-Lebenszyklus

Wenn Unternehmen solche Zahlen sehen, würden sie normalerweise ihre Investitionen einstellen. Mit einer produktorientierten Denkweise bedeuten diese Zahlen jedoch, dass Sie in der Lage sind, kontinuierliche Verbesserungen und Innovationen zu statischen Kosten anzubieten, während die Kunden zufrieden sind und eine schnelle Entwicklung ermöglicht wird.

Definition von KPIs für die Plattformakzeptanz

Wir können viele technische Zahlen als Grundlage für unsere KPIs verwenden. Diese sind leicht zugänglich und lassen sich gut miteinander in Beziehung setzen. Die Interpretation der Zahlen liegt jedoch bei Ihnen. Der Rückgang der Serviceanfragen kann daran liegen, dass Sie über eine hervorragende Dokumentation verfügen, aber auch daran, dass niemand die Plattform nutzt. Wie bereits gezeigt, muss daher ein vollständiges Bild vermittelt werden. Dies kann kompliziert werden, da jeder neue KPI weitere Details zu den Daten hinzufügen kann. Irgendwann müssen Sie hier eine Grenze ziehen.

Für Entwickler und DevOps-Teams gibt es bereits einige Frameworks, die wir als Grundlage verwenden können.

DORA-Metriken

**DevOps Research and Assessment** (**DORA**) ist ein Start-up, das von Gene Kim und Jez Humble gegründet wurde, die Sie vielleicht aus dem DevOps-Handbuch kennen. Die DORA-Metriken sind ein Satz von vier KPIs, mit denen die Leistung eines DevOps-Teams und die Auswirkungen einer Plattform auf ihre Nutzer gemessen werden können. Obwohl sie nicht immer gut passen, werden sie weit verbreitet eingesetzt und beispielsweise von Systemen wie GitLab \[13\] verwendet.

Die DORA-Metriken lauten wie folgt:

- **Bereitstellungshäufigkeit**: Wie oft eine Organisation erfolgreich in die Produktion geht
- **Durchlaufzeit für Änderungen**: Die Zeit, die benötigt wird, bis eine Änderung in die Produktion gelangt
- **Zeit bis zur Wiederherstellung der Dienste**: Der Prozentsatz der Bereitstellungen, die zu einem Ausfall in der Produktion führen
- **Änderungsausfallrate**: Wie lange ein Unternehmen benötigt, um sich von einem Ausfall in der Produktion zu erholen

Ich habe oft beobachtet, dass Unternehmen den Begriff „Produktion” durch „Release” oder „produktive Veröffentlichung” ersetzen. Das liegt daran, dass die meisten Unternehmen mehrere Phasen durchlaufen, bevor ein Release für den Endnutzer live geht. Aufgrund der Besonderheiten jedes Unternehmens gibt es mehrere Lösungen, um diese Zahlen zu messen, aber letztendlich ist es üblich, einen eigenen Ansatz dafür zu implementieren.

Um die Anzahl der Releases zu messen, können Sie einen einfachen API-Aufruf an Ihr bevorzugtes Versionskontrollsystem für Quellcode senden, das Sie bei Ihren Releases unterstützt. Diese Zahlen können in eine Datenbank übertragen und mit einem Grafana-Dashboard visualisiert werden.

Die Ermittlung der Vorlaufzeit ist komplizierter. Dazu müssen Sie Commits verfolgen und feststellen, wann sie in einer Release landen. Beide Kennzahlen sind jedoch einfach zu ermitteln und zu berechnen. Die Änderungsfehlerquote ist hingegen problematischer. Dazu müssen Sie Informationen zu Ihren Releases über die gesamte Bereitstellungs- und Produktionskette hinweg einbeziehen, damit Sie bei einem Fehler in den Protokollen erkennen können, zu welchem Release dieses Problem gehört. Darüber hinaus müssen Sie dann auch beurteilen, ob es sich wirklich um ein durch das Release verursachtes Problem handelt oder nicht.

Die Zeit bis zur Wiederherstellung des Dienstes folgt dem gleichen Verfahren. Sie müssen feststellen, wann ein Vorfall auftritt, wann er erfolgreich geschlossen wurde und wann er durch eine Wiederherstellung behoben wurde. Ihr Vorfallmanagementsystem kann beide Kennzahlen liefern.

Das Besondere an den DORA-Kennzahlen ist, dass sie auf der Grundlage von Untersuchungen bei Tausenden von Unternehmen einen Überblick darüber geben, wie gut oder schlecht Sie im Vergleich zu anderen sind. Aus ihrem letzten Bericht aus dem Jahr 2023 gehen die folgenden Kategorien und der Anteil der Unternehmen hervor, die in diese Kategorien fallen \[14\].

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
|     | **Elite** | **Hoch** | **Mittel** | **Niedrig** |
| **Bereitstellungshäufigkeit** | Auf Anfrage | Zwischen einmal täglich und einmal wöchentlich | Zwischen einmal pro Woche und einmal pro Monat | Zwischen einmal pro Woche und einmal pro Monat |
| **Änderungsvorlaufzeit** | Weniger als ein Tag | Zwischen einem Tag und einer Woche | Zwischen einer Woche und einem Monat | Zwischen einer Woche und einem Monat |
| **Änderungsfehlerquote** | 5   | 10  | 15  | 64  |
| **Wiederherstellungszeit nach fehlgeschlagener Bereitstellung** | Weniger als eine Stunde | Weniger als ein Tag | Zwischen einem Tag und einer Woche | Zwischen einem Monat und sechs Monaten |
| **Prozentualer Anteil der Befragten** | 18  | 31  | 33  | 17  |

Tabelle 2.3: DORA-Kennzahlen für verschiedene Reifegrade

Das Gute an den DORA-Kennzahlen ist, dass die meisten Unternehmen in der Lage sein werden, solche Zahlen zu erheben. Andererseits fehlen uns als Plattformingenieuren einige Aspekte rund um direktes und persönliches Feedback.

Die folgende Abbildung zeigt ein Grafana-Dashboard für Endbenutzer, das Echtzeitdaten anzeigt. In der oberen linken Ecke sehen Sie, dass die Anzahl der in der Produktion bereitgestellten Apps 105 beträgt und die Gesamtzahl der Bereitstellungen 1.847. In der oberen rechten Ecke werden die Vorlaufzeit für eine Änderung in Stunden (612,5), die Änderungsfehlerquote (0,522 %), die Bereitstellungshäufigkeit (5,02) und die MTTR (199) angezeigt. Die Grafiken unten zeigen die Bereitstellungen pro Anwendung.

Abbildung 2.16: Reales Beispiel für ein DORA-Dashboard (Das Bild dient als visuelle Referenz; die Textinformationen sind nicht wesentlich.

Wie können Sie mit DORA beginnen? Eine Möglichkeit ist die Nutzung **von Keptn**, einem CNCF-Inkubationsprojekt, das automatisierte Beobachtbarkeit für anwendungsorientierte Bereitstellungen auf Kubernetes bietet. Keptn kann auf Namespace-Ebene über die Anmerkung „ “ aktiviert werden und erstellt Prometheus-Metriken sowie OpenTelemetry-Traces, um Bereitstellungen beobachtbar zu machen. Diese Metriken umfassen die Dauer der Bereitstellungen sowie deren Erfolg oder Misserfolg und liefern Dimensionen für Bereitstellung, Anwendung, Umgebung und Version. Damit stehen Ihnen sofort einige der wichtigsten DORA-Metriken zur Verfügung, die Sie in Ihr Dashboard aufnehmen können, wie in der folgenden Abbildung gezeigt:

Abbildung 2.17: Keptn bietet automatisierte Beobachtbarkeit von Bereitstellungen, um einige der DORA-Metriken zu melden

Keptn bietet zusätzliche Funktionen, wie z. B. die SLO-basierte Validierung des Deployment-Erfolgs, und verfolgt Deployments über mehrere Phasen hinweg, um zusätzliche Metriken zu identifizieren, z. B. „Wo stecken Deployments im Promotionsprozess fest?“

Weitere Informationen finden Sie auf der Keptn-Website und in den DORA-Tutorials \[15\].

SPACE-Framework

Das **SPACE-Framework** kombiniert fünf Dimensionen, die die Produktivität eines Entwicklerteams bewerten. Dieser Ansatz wurde von GitHub, Microsoft und der University of Victoria entwickelt. Er konzentriert sich auf die Art und Weise, wie Teams zusammenarbeiten, und auf ihre Ergebnisse. Die fünf Dimensionen verdeutlichen dies:

- **Zufriedenheit und Wohlbefinden**: Sammeln Sie Informationen über die allgemeine Zufriedenheit, das Glück und die arbeitsbezogene psychische Gesundheit.
- **Leistung**: Output-orientierte Kennzahlen, wie z. B. abgeschlossene Aufgaben oder veröffentlichte Releases
- **Aktivität**: Konzentration auf Aktivitäten wie die Anzahl der Commits, Merge-Anfragen oder Code-Reviews
- **Kommunikation und Zusammenarbeit**: Wir untersuchen das Kommunikationsverhalten und die Abstimmung der Teams sowie Mechanismen zur Überprüfung der Nutzung und Kommentierung
- **Effizienz und Ablauf**: Wie reibungslos verlaufen der Entwicklungs- und Bereitstellungsprozess?

Vielleicht haben Sie das Gefühl, dass Sie einige oder alle DORA-Kennzahlen verwenden könnten, um Fragen zu Leistung, Effizienz und vielleicht auch Aktivität zu beantworten, und damit haben Sie Recht. Es gibt jedoch noch weitere Ansätze, die Sie verfolgen können.

Für Zufriedenheit und Wohlbefinden können wir Methoden wie den **Employee Satisfaction Score** (**ESS**), den **Employee Net Promoter Score** (**eNPS**) oder den **Employee Engagement Index** (**EEI**) verwenden. Für den Anfang können Sie mit einer einfachen Umfrage beginnen.

Ideen für Leistungskennzahlen sind Vorlaufzeit, Zeit vom Vorfall bis zur Wiederherstellung, Anzahl der Releases und Testcodeabdeckung. Um pragmatisch zu sein, verwenden Sie für den Anfang die DORA-Kennzahlen.

Um die Aktivität zu messen, können Sie Folgendes heranziehen:

- Bereitstellungshäufigkeit
- Anzahl der Codezeilen
- Commits
- Anzahl der Pull-Anfragen
- Anzahl der Überprüfungen
- Abgeschlossene Probleme/Aufgaben
- Gelöste Story Points

Diese Zahlen sind nicht immer einfach zu erheben. In einigen Ländern ist es ausdrücklich verboten, die Leistung einer Person zu bewerten, und dies ist nur für eine bestimmte Anzahl von Personen zulässig. Dies bringt SPACE auch häufig in die Kritik. Wenn Sie SPACE nutzen möchten und wir zugeben müssen, dass die Metriken hilfreich sind, um Einblicke in den Entwicklungszyklus zu gewinnen, sollten Sie mit Ihrem Datenschutzteam sprechen, das für die richtige Einrichtung verantwortlich ist.

Ähnliche Probleme treten bei der Dimension Kommunikation und Zusammenarbeit auf. Wenn Sie sich nicht mit den Nutzerstatistiken Ihres Kommunikationstools befassen möchten, sind Merge-Anfragen, Merge-Zeiten oder die Anzahl der Kommentare bei Commits, Merge-Anfragen oder Issue-Tickets ein guter Anfang. Sie können auch die Qualität von Besprechungen bewerten, indem Sie um Feedback bitten.

Die letzte Dimension, Effizienz und Fluss, kann wiederum auf DORA-Metriken basieren. Darüber hinaus ist es hilfreich zu bewerten, wie viele Übergaben Sie in einem Entwicklungszyklus haben, wie viele Fokusstunden ein Entwickler tatsächlich hat und wie hoch seine Geschwindigkeit ist.

Das SPACE-Framework kann auf individueller, Team- und Organisationsebene angewendet werden. Das folgende Diagramm aus Michael Kaufmanns Buch „Accelerate DevOps with GitHub” enthält weitere Beispiele für diese Ebenen.

Abbildung 2.18: Beispiele für SPACE-Metriken von Michael Kaufmann \[16\]

Mit dem SPACE-Framework erhalten wir nun tiefe Einblicke in die Entwicklung, was für uns als Plattformingenieure hilfreich ist und die DORA-Metriken erweitert. Wir können diese Metriken aufeinander aufbauen. So können Produktverantwortliche, Architekten und Plattformingenieure beurteilen, ob sie das Richtige auf die richtige Weise tun. Allerdings fehlen uns noch Inputs von den Experten **für Entwicklererfahrung** (**DevEx**).

DevEx-Framework

SPACE und DORA fehlt die DevEx-Perspektive. Auch wenn wir uns mit Zufriedenheit und Fluss befassen, erhalten wir kein vollständiges Bild unseres Plattform-Engineering-Teams. Hier kommt das **DevEx-Framework** ins Spiel \[17\]. Es beschränkt die Perspektive auf nur drei Dimensionen. Zusammen bilden sie die Grundlage für DevEx und können dessen Wirkungsbereich erweitern.

Abbildung 2.19: Die drei Kerndimensionen von DevEx

Aus der Perspektive eines Entwicklers ist der Flow-Zustand erreicht, wenn er sich zu 100 % auf das Schreiben von Code konzentriert und dabei Zeit, Hunger und andere Bedürfnisse buchstäblich vergisst. Je einfacher es ist, einen Flow-Zustand zu erreichen und aufrechtzuerhalten, desto besser ist das DevEx.

Wir haben viel über kognitive Belastung gesprochen. Kurz gesagt, ein gutes DevEx beinhaltet eine sehr geringe kognitive Belastung.

Schließlich misst die Feedbackschleife, wie schnell und in welcher Qualität ein Entwickler Feedback zu seinen Handlungen erhält. Je besser dieses Feedback ist, desto kontinuierlicher und umsetzbarer kann ein Entwickler mit minimalen Reibungsverlusten und Transaktionsverlusten reagieren.

Diese zu messen ist schwierig, da die Antwort zwischen tatsächlichen Kennzahlen und subjektivem Feedback liegt:

- **Flow-Zustand**:
    - **Metriken**: Wiedereröffnete Commits, Anzahl der Änderungsanfragen, Anzahl der Commits pro Pull-Anfrage.
    - **Subjektives Feedback**: Wie oft fühlen sie sich unterbrochen? Fühlen sie sich ständig gestresst oder unter Druck? Wie hoch ist ihre Entscheidungsautonomie?
- **Kognitive Belastung**:
    - **Kennzahlen**: Anzahl der wiedereröffneten Bugs, Debugging-Zeit, Anzahl der Abhängigkeiten für eine Komponente und Zeit zur Lösung technischer Probleme
    - **Subjektives Feedback**: Die für das Codieren aufgewendete Zeit im Vergleich zur Zeit, die für andere Aufgaben aufgewendet wird; der technische Umfang ihrer Komponente und wie oft sie den Kontext wechseln müssen
- **Feedbackschleife**:
    - **Kennzahlen**: Zykluszeit, Bereitstellungshäufigkeit, **mittlere Zeit bis zur Lösung** (**MTTR**), Anzahl der Fehler und Grad der Testautomatisierung
    - **Subjektives Feedback**: Effektivität von Code-Reviews, interne Teamkommunikation und Qualität des Feedbacks

Wie Sie an diesen Beispielen sehen können, gibt es viel Interpretationsspielraum. Wenn Sie die KPIs Ihrer Plattform definieren, müssen Sie sicherstellen, dass diese Kennzahlen klar beschrieben sind. Sie müssen besonders präzise sein, indem Sie erklären, wie Sie welches Feedback und welche Kennzahlen auf welche Weise interpretieren.

Wichtiger Hinweis

Architekten müssen diese KPIs und ihre Bedeutung verstehen, damit sie die Plattform effektiv verbessern können.

Verwendung von Leistungskennzahlen

Im vorherigen Rahmen wurden einige Leistungskennzahlen hervorgehoben, wie z. B. die Anzahl der geschlossenen Probleme oder Story Points. Diese Kennzahlen funktionieren gut auf Teamebene, können aber auch zu vielen Missverständnissen führen.

Es gibt jedoch einen Weg, der nicht abstrakt und unklar ist wie ein Story Point, und der eine narrensichere Methode darstellt, um mit Benutzern und Stakeholdern über die Plattform und ihre Effizienz zu sprechen: Kosten. Ich weiß, dass dies kein innovativer KPI ist, aber er wird von vielen Teams oft falsch angewendet und von Produktverantwortlichen gefürchtet. Damit meine ich auch nicht, die Kosten, die Infrastruktur oder die Lizenzen des Teams zu melden. Sie können die Kostenkennzahlen als Nachweis für die Leistung Ihrer Plattform und des Plattformteams verwenden.

Kosten pro Änderung

**Die Kosten pro Änderung** sind eine effiziente Möglichkeit, die Verbesserung und Leistungsfähigkeit einer Plattform hervorzuheben. Innerhalb der Endnutzer-Community des Cloud-nativen Ökosystems finden wir Beispiele für diesen KPI, der verwendet wird, um zu diskutieren, wie gut eine Plattform läuft.

Vergleichen wir zwei verschiedene Werte für die Kosten pro Änderung:

- **500 $ pro Änderung**: 15.000 $ pro Monat oder 180.000 $ pro Jahr bei 30 Änderungen pro Monat
- **80 $ pro Änderung**: 2.400 $ pro Monat oder 28.800 $ pro Jahr bei 30 Änderungen pro Monat

Nun gibt es natürlich einen drastischen Unterschied zwischen beiden Zahlen. Sie sollten jedoch bedenken, dass Sie immer mit höheren Kosten und sehr wenigen Änderungen beginnen werden. Im Idealfall verbessern sich das Plattformteam und die Plattform im Laufe der Zeit, sodass sich die Gesamtkosten stabilisieren, aber die Anzahl der Änderungen steigt. Dies führt zu niedrigeren Kosten pro Änderung. Die folgende Grafik veranschaulicht dies, um es besser zu visualisieren. Die gepunktete Linie zeigt ein Beispiel für die Gesamtkosten. Sie steigen im Laufe der Zeit leicht an, da die Plattform effektiver wird. Die dunkle Linie zeigt die Änderungen pro Jahr und die gestrichelte Linie die Kosten pro Änderung. Wie Sie sehen können, sinken die Kosten pro Änderung drastisch, je mehr Änderungen Sie vornehmen können. Es handelt sich um eine sehr einfache Zahl, aber ein starkes Kommunikationsmittel für Ihre Plattform und ihr Plattform-Engineering-Team.

Abbildung 2.20: Beispiel für die Gesamtkosten pro Jahr

Kosten pro Projekt/Produkt

Im Zusammenhang mit den Kosten pro Änderung stehen die Kosten pro Projekt, Produkt oder Anwendung. Wir können diese Kosten aus zwei verschiedenen Blickwinkeln betrachten:

- **Gesamtkosten**: Betrachtung nur von Aspekten wie Teamkosten, zusätzlichem Aufwand oder Kosten, die nicht ursachenbasiert sind
- **Ausgewogene verursachungsbasierte Kosten**: Die verursachungsbasierten Kosten umfassen neben den gemeinsamen Kosten auch die tatsächlichen Kosten für Infrastruktur und Dienstleistungen, die von einem Projekt in Anspruch genommen werden

Um die Leistung der Plattform und des Teams hervorzuheben, würde ich empfehlen, die gesamten gemeinsamen Kosten zu verwenden. Solche Zahlen sind einfach zu ermitteln und können auf die Projekte aufgeteilt werden, sodass Sie sie ohne großen Aufwand monatlich verfolgen können. Eine Alternative dazu sind die Einführungskosten pro Projekt. Für diese Kennzahl müssen Sie den Aufwand berechnen, der für die Einarbeitung in jedes Projekt unter Verwendung der Plattform erforderlich ist. Ich persönlich würde jedoch keinen Aufwand für diese Kennzahlen betreiben. Es handelt sich dabei eher um rhetorische Zahlen v er Natur, die keinen Einblick in die Leistung Ihrer Plattform geben, sondern eher Aufschluss darüber liefern, wie effizient Sie bei der Einarbeitung sind.

Benutzer-/Produkt-Gemeinkosten

Die Perspektive der Gemeinkosten ist der Kosten pro Änderung sehr ähnlich. Hier summieren Sie alle direkten und gemeinsamen Kosten und reduzieren sie nur um die verbrauchten Ressourcen. Daher ist es wichtig, zwischen Tools wie Agenten, Netzwerkverkehr und möglicherweise persönlichen benutzerbezogenen Kosten und den tatsächlich vom Produkt verbrauchten Ressourcen zu unterscheiden. Die Berechnung ist kompliziert, aber das Ergebnis ist eine Leistungskennzahl für die Gemeinkosten Ihrer Plattform und Ihres Plattformteams.

Diese Kennzahl spaltet die Gemüter. Einerseits sollte sie so gering wie möglich sein, um die Plattform intern verkaufen zu können. Andererseits repräsentiert diese Zahl die Kosten für den tatsächlichen Wert der Plattform. Daher glaube ich, dass wir einen Mittelweg finden müssen, der nicht zu kostspielig, aber auch nicht zu teuer ist.

Zusammenfassung

In diesem Kapitel haben Sie die grundlegenden Prinzipien von Plattformen kennengelernt und erfahren, wie Sie die Ziele Ihres Plattformteams entwickeln können. Sie verfügen nun über die Werkzeuge, um eine Plattformarchitektur zu dokumentieren und zu entwerfen, gefolgt von Endbenutzerbeispielen für verschiedene Plattformen. Dieses Kapitel hat Ihnen zusätzliche Perspektiven auf die Fähigkeiten von Plattformen vermittelt. Mit dem Ansatz des TVP haben Sie gelernt, sich auf einzelne Meilensteine zu konzentrieren, ohne zu übergreifend zu sein, und sich schneller an die Anforderungen anzupassen. Abschließend haben wir Ihnen einige Ansätze zur Messung Ihrer Plattformakzeptanz und Leistungsmetriken vorgestellt.

In [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3) werden wir die Details zum Aufbau der Grundlage für Plattformen besprechen. Zunächst stellen wir Ihnen unser Referenz- und Beispielunternehmen vor und erläutern bestimmte Details. Sie lernen die Grundlagen der Infrastruktur, die Herausforderungen von Multi-Cloud und **Software as a Service** (**SaaS**) sowie die Erstellung einer Referenzarchitektur für die Grundlage kennen.

Weiterführende Literatur

- \[1\] Kosten der Verzögerung: Die wirtschaftlichen Auswirkungen einer Verzögerung bei der Projektabwicklung: [https://businessmap.io/lean-management/value-waste/cost-of-delay](https://businessmap.io/lean-management/value-waste/cost-of-delay%0A)
- \[2\] Evan Bottcher, Worüber ich spreche, wenn ich über Plattformen spreche: [https://martinfowler.com/articles/talk-about-platforms.html](https://martinfowler.com/articles/talk-about-platforms.html%0A)
- \[3\] Miro-Vorlage, The Platform Engineering Purpose Canvas: [https://miro.com/miroverse/platform-engineering-purpose-canvas-template](https://miro.com/miroverse/platform-engineering-purpose-canvas-template%0A)
- \[4\] **Team-Topologien**: [https://teamtopologies.com/](https://teamtopologies.com/%0A)
- \[5\] PlatformCon2023, Plattform als Code: Vereinfachung des Designs von Entwicklerplattformen mit Referenzarchitekturen: [https://youtu.be/AimSwK8Mw-U?si=1CDAJb1gLtlCgeyH](https://youtu.be/AimSwK8Mw-U?si=1CDAJb1gLtlCgeyH%0A)
- \[6\] **PlatformEngineering.ORG-Tools**: [https://platformengineering.org/platform-tooling](https://platformengineering.org/platform-tooling%0A)
- \[7\] **CNCF-Landschaft**: [https://landscape.cncf.io/](https://landscape.cncf.io/%0A)
- \[8\] **Wasm-Beispielquellen**:
    - **Allgemeine Seite**: [https://webassembly.org/](https://webassembly.org/%0A)
    - **Ein einfacher Kubernetes-Operator zum Ausführen von Wasm – kwasm**: [https://kwasm.sh/](https://kwasm.sh/%0A)
    - **Ein Operator und Entwicklungstoolkit für Wasm auf Unternehmensniveau**: https://www.spinkube.dev/
- \[9\] **ThoughtWorks-Plattform-Technologiestrategieebenen**: [https://www.thoughtworks.com/insights/blog/platform-tech-strategy-three-layers](https://www.thoughtworks.com/insights/blog/platform-tech-strategy-three-layers%0A)
- \[10\] **The Lean Startup**: https://theleanstartup.com
- \[11\] ICE-Bewertungsmodell: [https://www.productplan.com/glossary/ice-scoring-model/](https://www.productplan.com/glossary/ice-scoring-model/%0A)
- \[12\] **Startup-Lehren aus Google Maps**: [https://www.startuplessonslearned.com/2010/09/good-enough-never-is-or-is-it.html](https://www.startuplessonslearned.com/2010/09/good-enough-never-is-or-is-it.html%0A)
- \[13\] **GitLab DORA-Metriken**: [https://docs.gitlab.com/ee/user/analytics/dora_metrics.html](https://docs.gitlab.com/ee/user/analytics/dora_metrics.html%0A)
- \[14\] **DORA-Bericht 2023**: [https://cloud.google.com/devops/state-of-devops](https://cloud.google.com/devops/state-of-devops%0A)
- \[15\] **DORA-Tutorial**: [https://keptn.sh/stable/docs/guides/dora/](https://keptn.sh/stable/docs/guides/dora/%0A)
- \[16\] Michael Kaufmann, Accelerate DevOps with GitHub: [https://www.packtpub.com/product/accelerate-devops-with-github](https://www.packtpub.com/product/accelerate-devops-with-github%0A)
- \[17\] **DevEx-Framework**: https://queue.acm.org/detail.cfm?id=3595878