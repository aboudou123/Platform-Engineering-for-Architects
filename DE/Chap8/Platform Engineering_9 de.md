**Technische Schulden wählen, um Plattformen funktionsfähig zu halten**

Was sind **technische Schulden** und wie können sie eine Plattform reparieren? Technische Schulden sind die laufenden Kosten für die Wartung einer Software. Dabei handelt es sich um die tatsächlichen Ausgaben für die Laufzeitumgebung, die Zeit für den Betrieb und die Aktualisierung sowie die Kundenzufriedenheit. Genau wie finanzielle Schulden können sich auch technische Schulden anhäufen. Wenn sich der Betrag immer weiter erhöht, kann das Team keine neuen Schulden machen oder neue Funktionen bereitstellen, da die gesamte Arbeitszeit für die Behebung der aktuellen Probleme aufgewendet wird.

Anzeichen dafür, dass ein Team mit technischen Schulden überlastet ist, sind leicht zu erkennen: Versuchen Ihre Teams, extrem veraltete Software zu warten? Haben Sie Systeme, die betrieblich anfällig und/oder absturzgefährdet sind? Verwenden Sie unnötig komplexe Software?

Wenn Sie eine dieser Fragen mit Ja beantworten, entstehen entsprechende Kosten. Beispielsweise ist die Aktualisierung, Sicherung und der Betrieb veralteter Software sehr kostspielig bis unpraktisch. Betriebsunzuverlässige Software erfordert häufige manuelle Eingriffe, was die Zeit Ihres Betriebsteams in Anspruch nimmt und die Gefahr von Burnout erhöht. Und nicht zuletzt ist überkomplizierte Software in der Regel einfach schwer zu verstehen. Sie ist schwer zu lesen und zu warten, was laufende Entwicklungs- und Wartungskosten bedeutet.

Es gibt keine Software, die ohne Schulden entwickelt oder eingeführt werden kann, aber wenn dies neben den Funktionen bewertet wird, kann dies zu einem erfolgreicheren Betrieb der Plattform beitragen. In diesem Kapitel behandeln wir die folgenden Themen:

- Bewusste Übernahme technischer Schulden
- Nutzung von Daten zur Steuerung von Designentscheidungen
- Technische Schulden pflegen und überarbeiten
- Neuschreiben versus Refactoring – ein praktischer Leitfaden
- Aufzeichnungen zu architektonischen Entscheidungen – Dokumente für die Nachwelt

Technische Schulden bewusst eingehen

„Wählen Sie Ihre technischen Schulden mit Bedacht aus“, sagt die Autorin Hilliary immer wieder. Aber was bedeutet es, technische Schulden auszuwählen? Sollten wir nicht Probleme lösen und Lösungen finden?

Ja. Aber diese beiden Dinge schließen sich nicht gegenseitig aus. Es gibt wahrscheinlich keine perfekte Lösung von der Stange. In der Regel werden Produkte für bestimmte Anwendungsfälle entwickelt, aber diese Anwendungsfälle sind nicht allumfassend. Kein Produkt kann alle möglichen Bedürfnisse und Arbeitsabläufe jedes einzelnen Benutzers abdecken. Das Gleiche gilt auch für Ihre Plattform im Laufe ihres Lebenszyklus. Wenn wir uns dazu verpflichten, die Mängel einer Lösung oder Technologie zu akzeptieren, bedeutet das, dass wir uns dazu verpflichten, dies auf andere Weise auszugleichen. Dieser Ausgleich sollte so gestaltet werden, dass keine zusätzlichen Kosten oder manuellen Arbeitsabläufe entstehen, die zu einer untragbaren Belastung für das Plattformteam oder die Entwickler führen. Zu hohe technische Schulden schmälern die Rendite der Investition in die Plattform.

Technische Entscheidungen sollten gemeinsam getroffen werden. Es ist wichtig, als Team einen Konsens zu finden, um sicherzustellen, dass der eingeschlagene Weg zumindest für die Mehrheit akzeptabel ist. Um technische Schulden bewusst aufzunehmen, müssen Sie in der Lage sein, diese zu bewerten und die Antworten auf wichtige Fragen zu verstehen.

Im Folgenden finden Sie eine Bewertung der technischen Schulden, die Sie ausprobieren können:

1.  Welche Probleme lösen Sie heute?
2.  Welche Probleme haben Sie (noch) nicht?
3.  Was kostet uns die Entwicklung oder Einführung?
4.  Was kostet uns der Betrieb?
5.  Was ist für die Wartung erforderlich?
6.  Was ist unsere erwartete Rendite?
7.  Kann das Team es in seiner jetzigen Form aufrechterhalten?
    - Wenn nicht, ist das Team bereit, sich weiterzubilden, und hat es dafür Zeit?
    - Wenn es sich um Open-Source-Software handelt, wie stark ist die Community? Wie kann das Team dieser Community beitreten?
8.  Was ist erforderlich, damit neue Teammitglieder sich einarbeiten können?
9.  Wann wissen wir, dass es Zeit für eine Skalierung ist?
10. Wie werden wir skalieren?
11. Was sind unsere Kriterien für die Abwertung dieser Lösung?

Visualisieren Sie die Antworten auf diese Fragen als Buchhaltungsbuch. Wenn Sie alles zusammenrechnen, liegen Sie dann vorne oder hinten? Wie in Ihren Büchern müssen diese Werte ausgeglichen sein. Das Gleichgewicht der technischen Schulden eines Teams oder einer Organisation ist eher soziotechnischer als technischer Natur. Die Kunstfertigkeit der Technik kann zu einer emotionalen Bindung führen, die blinde Flecken und Mängel hervorrufen kann, die sich auf die langfristige Nachhaltigkeit einer Lösung auswirken. Beispielsweise geraten Tools, die von leidenschaftlichen Ingenieuren auf dem neuesten Stand der Technik geschrieben wurden, häufiger in Vergessenheit und verfallen, wenn sie nicht so geschrieben wurden, dass sie die Zusammenarbeit im Team fördern, und wenn die technischen Komponenten eine Reihe von Teammitgliedern ausschließen, die nicht über die erforderlichen Fähigkeiten zur Wartung dieser Tools verfügen.

Eine Lösung kann noch so clever, elegant und einfach sein, sie kann dennoch nicht nachhaltig sein, wenn sie nicht für das Team oder die Umgebung geeignet ist, in der das zu lösende Problem besteht. Wenn die Lösung beispielsweise in Rust geschrieben ist und das Team bisher Ruby verwendet hat, ist es unwahrscheinlich, dass das Team die Lösung aufrechterhalten kann, wenn die Person, die sie entworfen und implementiert hat, das Unternehmen verlässt.

Deshalb ist von allen Fragen die letzte die wichtigste. Verfallskriterien geben uns Aufschluss darüber, wann es an der Zeit ist, ein Tool, ein System oder einen Codeabschnitt aus dem Verkehr zu ziehen oder zu ersetzen. Alle Dinge werden irgendwann zu Legacy-Software, daher ist ein Verfallplan oder Kriterien, anhand derer Sie die Idee des Verfalls bewerten, ein wichtiger Aspekt der Aufrechterhaltung der technischen Schulden.

Nachhaltig über die dünnste tragfähige Plattform (TVP) hinausgehen

Wenn wir eine TVP aufbauen, verpflichten wir uns dem Grundsatz „gut genug”, aber im Laufe der Weiterentwicklung kann das, was einmal gut genug war, irgendwann nicht mehr richtig sein. Dies ist die erste Iteration der technischen Schulden der Plattform. Technische Schulden sind ein Zeichen für Wachstum und Weiterentwicklung. Manchmal sind sie das Ergebnis einer Entscheidung, die sich im Nachhinein als falsch herausgestellt hat, aber genauso oft sind sie das Ergebnis einer Weiterentwicklung über den Punkt hinaus, an dem die Entscheidung sinnvoll war. In gewisser Weise sind technische Schulden die Kosten der Geschäftstätigkeit, während sie in anderer Hinsicht als Wachstumsschmerzen betrachtet werden können. Wie auch immer man es betrachtet, es handelt sich um ein Symptom, das gemanagt oder gemildert werden muss.

Wenn es an der Zeit ist, dass die Plattform ihre Schwachstellen überwindet und sich zu einer robusten Lösung entwickelt, die ein Unternehmen in großem Maßstab unterstützen kann, beginnen wir mit der Neubewertung unserer bisherigen Entscheidungen. Erweitern wir unsere bestehenden Funktionen? Ersetzen wir Komponenten? Schalten wir alles aus, was nicht wie erwartet funktioniert hat? Dieser Übergang zur nächsten Generation des IDP wird von denselben Daten geleitet, die auch zur Definition des TVP verwendet wurden.

Kritische User Journeys

Die **kritische Benutzerreise**, die ursprünglich in der Entdeckungs- oder Planungsphase für Ihr IDP definiert wurde, beschreibt den erwarteten Arbeitsablauf der Interaktionen zwischen einem Benutzer und dem IDP und wo und wie diese erfolgreich sein sollen.

Mit der Weiterentwicklung von Organisationen ändern sich jedoch auch diese kritischen User Journeys. Es ist möglich, dass Dinge, die für eine Organisation früher sehr wichtig waren, mit der Zeit an Bedeutung verlieren oder gegenüber anderen Aspekten, die im Laufe der Zeit hinzugekommen sind, an Bedeutung verlieren.

Wenn Sie dem TVP-Muster gefolgt sind, ist es außerdem wahrscheinlich, dass in der Anfangsphase des Aufbaus der Plattform einige Anwendungsfälle und potenziell wichtige User Journeys nicht berücksichtigt wurden. Eine regelmäßige Überprüfung dieser Journeys und die bewusste Entscheidung, eine weitere hinzuzufügen oder eine bestehende zu erweitern, wird die Entwicklung Ihrer Plattform und die Innovationskraft Ihres Teams prägen.

Eine kritische User Journey basiert auf einer User Story. Für Financial One ACME besteht die Notwendigkeit, eine bestimmte geografische Region zu bedienen, sodass eine User Journey wie folgt formuliert werden könnte: „Als Nutzer der Plattform möchte ich eine Anwendung bereitstellen, auf die nur von Nordamerika aus zugegriffen werden kann.“ Sobald eine User Story vom Plattformteam akzeptiert wurde, sollte die User Journey erstellt werden. Nicht jede vorgeschlagene User Story sollte sofort akzeptiert werden. In der vorangegangenen Story erfordert beispielsweise die regionale Zugangsbeschränkung eine unterstützende Infrastruktur. Wenn dieser Anwendungsfall nicht geschäftskritisch ist, ohne zusätzlichen Aufwand erfüllt werden kann, auch wenn dies nicht optimal ist, oder außerhalb der Plattform unterstützt werden kann, dann ist es möglicherweise wichtiger, sich zuerst mit einer anderen User Story zu befassen.

Angenommen, die User Journey „Bereitstellung einer Anwendung, auf die nur von Nordamerika aus zugegriffen werden kann“ wird akzeptiert, könnten wir sie mit Tools wie Crossplane und der Composite-Funktion implementieren, mit der das Plattform-Engineering-Team eine Vorlage für die Bereitstellung einer Anwendung in einer bestimmten Region definieren kann. Der Benutzer muss dann in seiner Journey lediglich eine Instanz dieser Vorlage erstellen, alle Werte angeben und sie in Git committen. Der Rest wird von den zentralen Bereitstellungstools der Plattform übernommen. Das Ergebnis ist die bereitgestellte Anwendung, auf die nur aus der angegebenen Region zugegriffen werden kann. Technisch gesehen kann dies durch spezifische Ingress-Routing-Regeln für regionalspezifische Domainnamen erfolgen, wie in der folgenden Beispieldefinition gezeigt:

apiVersion: composites.financialone.acme/v1alpha1

kind: FinancialBackend

metadata:

&nbsp; name: tenantABC-us

spec:

&nbsp; service-versions:

&nbsp;   Geldtransfer: 2.34.3

&nbsp;   Kontoinformationen: 1.17.0

&nbsp; Redis-Cache:

&nbsp;   version: 7.4.2

&nbsp;   name: transfer-cache

&nbsp;   Größe: mittel

&nbsp; Datenbank:

&nbsp;   Größe: groß

&nbsp;   Name: accounts-db

&nbsp; Region: „us-east“

&nbsp; Eingang:

&nbsp;   URL: „https://tenantABC.financialone-us.acme“

KopierenErklären

Weitere Informationen zu Crossplane finden Sie im Abschnitt „Workload- und Anwendungslebenszyklus-Orchestrierung“ in [Kapitel 4](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/4).

Die Bewertung der Bedeutung und des Werts jeder User Story trägt zum nachhaltigen Wachstum der Plattform bei. Das Team kann nicht alles auf einmal erledigen, daher ist es wichtig, den Umfang nicht so stark anwachsen zu lassen, dass das Team ihn nicht mehr bewältigen kann.

Dies ist das gleiche Prinzip, das für die gesamte Softwareentwicklung gelten sollte, und in dieser Hinsicht unterscheiden sich die Plattform und eine Endbenutzeranwendung nicht voneinander.

Übermäßige Technik vermeiden

Was ist Überengineering? **Überengineering** ist in der Regel dadurch gekennzeichnet, dass ein sehr robustes und voll ausgestattetes System entwickelt wird, das versucht, jedes denkbare Problem zu lösen, noch bevor das Problem überhaupt existiert. Überengineering ist eine leicht zu fallende, aber gefährliche Falle. Die ersten beiden Fragen in unserer Bewertung helfen uns, übertriebene technische Lösungen zu vermeiden. Im Wesentlichen verwenden wir diese Fragen, um unsere Ziele und Nicht-Ziele für jede Entscheidung zu definieren. Wenn wir verstehen, welche Probleme und Anwendungsfälle wir lösen wollen, und definieren, was wir nicht lösen wollen – oder zumindest noch nicht –, können wir unsere Entscheidungen besser steuern und den Umfang unseres Projekts realistisch halten.

Bei einer Observability-Lösung ist es beispielsweise vernünftig, im Laufe der Zeit mit einer großen Datenmenge zu rechnen. Man kann leicht in die Falle tappen, unendlich viele Daten einzuplanen und die Infrastruktur entsprechend aufzubauen. Stellen Sie stattdessen gezielte Fragen:

- Wie viele Daten sind wirklich nützlich?
- Wie lange lohnt es sich für uns, diese Daten aufzubewahren?
- Wie lange müssen wir die Daten aufbewahren?
- Wer benötigt Zugriff auf die Daten?

Indem Sie anhand Ihrer Antworten Parameter definieren, sorgen Sie dafür, dass die Daten überschaubar bleiben. Wenn es keinen Anwendungsfall für die Aufbewahrung von Daten über einen Monat oder ein Jahr hinaus gibt, sollte die Lösung nicht darin bestehen, ein System zu entwickeln, das riesige Datenmengen verarbeiten kann. Eine bessere Lösung ist ein System, das kleine Datenmengen verarbeitet und regelmäßig nicht benötigte Daten löscht. Wenn vollständige Löschungen Ihren Anwendungsfällen nicht entsprechen oder Ihnen zu extrem erscheinen, ist möglicherweise die Datenaggregation der richtige Ansatz. Beispielsweise können Telemetriedaten, die über mehrere Sekunden hinweg erfasst werden, zu Tagen, Wochen, Monaten oder sogar Jahren zusammengefasst werden. Durch die Datenaggregation können Daten, die einen langen Zeitraum abdecken, weiterhin vorhanden sein, ohne dass Speicher- und Abrufmechanismen für riesige Datenmengen entwickelt werden müssen. Wenn Sie das Gefühl haben, dass Sie Flashbacks zu [Kapitel 7](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/7) haben, dann liegen Sie richtig. Die gleichen Fragen, die dazu beitragen, Over-Engineering zu vermeiden, helfen uns in vielen Fällen auch, unsere Sicherheitslage zu verstehen.

Überdimensionierung zu vermeiden bedeutet nicht, dass man niemals für Probleme planen sollte, die noch nicht aufgetreten sind. Wenn man nicht für die Zukunft plant, kann dies auch dazu führen, dass Lösungen entwickelt werden, die später möglicherweise komplett ersetzt werden müssen. Dies kann jedoch von Vorteil sein, wenn man sich zusammensetzbare Systemarchitekturen und die Leistungsfähigkeit von Microservices ansieht. Manchmal ist ein vollständiger Austausch einer Komponente der beste Weg, um optimale Ergebnisse zu erzielen. In der Regel ist dies jedoch keine einfache oder schnelle Angelegenheit. Wenn dies also gewünscht ist, muss es sorgfältig geplant und gemäß diesem Plan ausgeführt werden. Eine allgemeine Empfehlung zur Vermeidung von Overengineering lautet, die Probleme von heute zu lösen und einen Fahrplan für morgen zu erstellen. Durch einfachere Systeme lassen sich diese leichter warten und können im Zuge der Produktentwicklung mehr Flexibilität gewährleisten.

Entwickeln oder kaufen – Erstellung eines Entscheidungsbaums

Bei der Hinzufügung einer neuen Komponente und der Bewertung der technischen Schulden ist eine der wichtigsten Fragen, ob wir sie selbst entwickeln oder kaufen sollten. Dies ist eher eine soziotechnische als eine technische Frage , da es darum geht, den natürlichen Wunsch nach Eigenentwicklung mit der Notwendigkeit des Kaufs abzuwägen, wenn dies für das Team das Richtige ist.

Es ist ganz natürlich, dass Ingenieure Dinge entwickeln wollen. Unsere Identität, unsere Stärken, Erfahrungen und Interessen beeinflussen uns dabei, Entscheidungen zu treffen, die damit im Einklang stehen. Es ist jedoch wichtig, sich von der emotionalen und intellektuellen Bindung an die Lösung des Problems zu lösen und die Optionen so unvoreingenommen wie möglich zu betrachten.

Die folgende Abbildung zeigt einen Entscheidungsbaum zur Frage, ob eine Lösung entwickelt oder gekauft werden soll. Bitte beachten Sie, dass „Kaufen” nicht immer bedeutet, Geld auszugeben; es kann sich auch auf die Einführung eines kostenlosen oder Open-Source-Tools beziehen:

Abbildung 9.1: Entscheidungsbaum „Entwickeln oder kaufen”

Dieser Entscheidungsbaum sollte als Gruppe ausgearbeitet werden. Einige der Fragen können Antworten haben, die eher subjektiv sind oder zu denen verschiedene Teammitglieder unterschiedliche Meinungen haben. Zusammenarbeit ist der Schlüssel, um diese Entscheidungen nachhaltig voranzubringen.

Lassen Sie uns gemeinsam einen Beispiel-Entscheidungsbaum ausarbeiten. In diesem Fall möchte unser fiktives Unternehmen Financial One ACME einen älteren Technologie-Stack modernisieren. Dabei müssen sie sich wahrscheinlich mit technischen Herausforderungen auseinandersetzen, die zuvor nicht existierten, oder neue Funktionen integrieren, die in einem System ohne modernere Architekturen nicht möglich gewesen wären.

Ein Beispiel für eine neue oder andere Funktion könnte die Bewertung des Einsatzes von Datenumwandlungstools sein. Da eine Cloud-native Architektur mehr Datenfunktionen bietet, könnte entweder das Produktteam, das Plattformteam oder beide Teams den Einsatz eines solchen Tools in Betracht ziehen, um Rohdaten nutzbarer zu machen.

Wenn das Plattformteam beispielsweise Nutzungsmetriken für die Plattform mit Prometheus erfassen und diese in DORA-Metriken umwandeln möchte, wäre eine Datenumwandlung in diesem Workflow sinnvoll. In ähnlicher Weise könnten auch andere Anwendungsfälle für die Datenumwandlung im gesamten Unternehmen nützlich sein, sodass bei der Implementierung mehrere Benutzeranforderungen berücksichtigt werden müssten.

Wenn wir dieses Beispiel stark vereinfachen, würden wir dem folgenden Entscheidungsbaum folgen:

F: Welches Problem versuchen wir zu lösen?

A: Wir müssen automatisierte Datenumwandlungen ermöglichen.

F: Gibt es bereits eine Lösung?

A: Ja – Apache Airflow und Argo Workflows.

Beachten Sie, dass das Team in diesem Fall zwei mögliche Lösungen identifiziert hat. Von dort aus sollten die nächsten Fragen für beide Lösungen gestellt werden. Erfüllt es die Anforderungen? Kann das Team es warten? Und können wir es uns leisten? Da beide Lösungen Open Source sind, würde sich die Frage der Erschwinglichkeit eher auf die vergleichbaren Betriebskosten beziehen, die möglicherweise nicht auf den ersten Blick erkennbar sind. Bei der Bewertung von Open Source ist die wichtigste Frage, wenn ein Tool die Anforderungen erfüllt, die Fähigkeit des Teams, die Lösung zu warten. Die Fähigkeiten des Teams können nicht isoliert betrachtet werden, sondern erfordern, dass das Team seine Fähigkeiten und seine Bereitschaft für eine neue Integration abwägt. Wenn eine Weiterqualifizierung erforderlich ist, bedeutet das nicht, dass die technischen Kosten nicht tragbar sind, aber diese Zeit muss in den Zeitplan aufgenommen werden, damit alle auf den neuesten Stand kommen und die Antwort „Dies ist potenziell nachhaltig” nicht zu „Dies ist nicht nachhaltig” wird.

Die Bedeutung der Zustimmung des Teams

Zwar werden viele Plattformarchitekten in den täglichen Betrieb eines IDP eingebunden sein, aber es ist ebenso wahrscheinlich, dass dies nicht der Fall sein wird. Daher müssen die Mitarbeiter, die sich täglich mit der Verwaltung und Wartung befassen, voll und ganz hinter der Ausrichtung des IDP und seinen Angeboten stehen. Dies ist oft das Plattformteam, aber wenn Sie eine Plattform aufgebaut haben, die Selbstbedienung und Zusammenarbeit mit der gesamten Engineering-Organisation fördert, wird das Team viel größer sein.

Es kann Fälle geben, in denen es unmöglich ist, einen 100-prozentigen Konsens zu erzielen. In diesem Fall muss man sich auf eine Meinungsverschiedenheit einigen und sich darauf festlegen. Ein Konsens im Team kann Burnout reduzieren, aber das muss gegen die Notwendigkeit abgewogen werden, sicherzustellen, dass sich das IDP gemäß seiner Roadmap weiterentwickelt.

Die Zustimmung des Teams ist unglaublich wichtig bei Entscheidungen, die eine Weiterqualifizierung des Teams erfordern, wie z. B. das Erlernen des Tools selbst oder einer neuen Programmiersprache. Wenn das Team nicht bereit oder in der Lage ist, sich an die technologische Lösung anzupassen, wird die Lösung letztendlich keinen Mehrwert bieten, unabhängig von ihren anderen positiven Eigenschaften.

Nachdem wir uns nun mit dem Konzept der technischen Schulden vertraut gemacht haben, können wir Strategien zur Minderung dieser Schulden durch die Nutzung von Daten untersuchen.

Nutzung von Daten zur Steuerung von Designentscheidungen

Bisher haben wir die Bedeutung von Observability-Daten für Self-Service und Entwicklerzufriedenheit diskutiert, aber nicht alle anderen Anwendungsfälle für die Telemetriedaten, die ein IDP sammeln kann. Daten sind ein mächtiges Gut, das zur Entscheidungsfindung und zur Kosten- und Zeitersparnis beitragen kann. Wenn man beispielsweise zwei Lösungen betrachtet, die hinsichtlich Lösungsgrad und technischer Schulden gleichauf liegen, kann es schwierig sein, sich für eine Richtung zu entscheiden. Hier können Sie Daten nutzen, um Ihre Entscheidungen zu treffen und Ihre technischen Schulden im Blick zu behalten.

Nahezu alle Daten, die Ihr Team für Entscheidungen benötigt, sind entweder bereits in Ihrer Observability-Lösung enthalten oder können leicht hinzugefügt werden.

Observability ist der Schlüssel

Nachdem Sie viel Zeit und Mühe in die Einrichtung eines Observability-Stacks und die Erfassung und Speicherung von Daten investiert haben, wäre es fast unverantwortlich, diese Daten nur für das Incident Management und die Reaktion auf Vorfälle zu verwenden. Glücklicherweise werden Plattformteams selten als unverantwortlich bezeichnet, sodass Sie wahrscheinlich bereits wissen, dass diese Daten auf sinnvollere Weise genutzt werden können. Die Anwendung von Observability-Daten auf die Entscheidungsfindung und deren Nutzung zur Identifizierung und Verwaltung technischer Schulden sind wichtige Anwendungsfälle für Ihren Observability-Stack, die manchmal übersehen oder zu wenig betont werden. In [Kapitel 6](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/6) haben wir darüber gesprochen, wo und wie diese Observability angewendet wird, aber lassen Sie uns nun dieselben Aspekte für technische Schulden betrachten.

Betriebsdaten und Arbeitsaufwand

In [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3) haben wir kurz das Konzept der **Service-Level-Ziele** (**SLO**) vorgestellt. In [Kapitel 6](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/6) haben wir uns erneut damit befasst, da es ein wichtiger Faktor für die Kundenzufriedenheit ist. SLO-Daten können jedoch auch zur Untersuchung und Identifizierung technischer Schulden verwendet werden.

Ein SLO ist ein Ziel. Selten wird dieses Ziel in der ersten Runde als idealer Zustand definiert, da es unmöglich sein kann, dies bei einem neuen Projekt von Anfang an zu erreichen. Eine gute SLO-Definition für ein neues Projekt ist weitaus konservativer, enthält jedoch einen Fahrplan zum endgültigen gewünschten Ziel. Gute SLOs sind SLOs, die sich mit dem System, das sie messen, weiterentwickeln.

Wenn beispielsweise das ideale SLO darin besteht, dass 99 % der Anwendungsbereitstellungen über einen Zeitraum von 28 Tagen erfolgreich sind, kann das ursprüngliche Ziel bei nur 60 % liegen. In einer Situation, in der alles neu ist, ist es sinnvoll, mit einem viel höheren Ziel zu beginnen. Wenn wir uns jedoch Financial One ACME ansehen, ein Unternehmen, das ein bedeutendes Legacy-Angebot migriert, wissen wir, dass das Team dort in einer benachteiligten Position startet. Daher ist es nachhaltiger, realistisch erreichbare Ziele zu setzen und die nächsten Ziele zu definieren, nachdem diese erreicht wurden. Auf diese Weise kann das Team die Probleme, die den Erfolg behindern, in eine Rangfolge bringen und Erfolge vorweisen. Sie fragen sich vielleicht: „Ist das Gamification?“ Ja, das ist es. Positive Rückkopplungsschleifen haben sich jedoch als wirksam erwiesen, um Burnout zu reduzieren und die Zufriedenheit der Entwickler zu steigern. Teams sollten so aufgestellt sein, dass sie gewinnen und nicht scheitern.

SLOs sind jedoch nicht die einzigen operativen Daten, die von Bedeutung sind. Es ist durchaus möglich, ein SLO durch manuelle Eingriffe und nicht durch Automatisierung aufrechtzuerhalten. An dieser Stelle beginnen Zuverlässigkeitsingenieure in der Regel, über das Konzept der „Toil“ zu diskutieren. Toil ist eine langweilige, sich wiederholende Aufgabe, die regelmäßig oder manuell erledigt werden muss. Selbst ein teilweise automatisierter Prozess ist immer noch Toil, wenn ein Mensch den Knopf drücken muss, um ihn zu starten.

Ein gewisses Maß an mühsamer Arbeit ist akzeptabel, beispielsweise das manuelle Starten einer Release-Pipeline für ein Unternehmen, das noch nicht für eine vollständige CI/CD-Implementierung bereit ist. Andere mühsame Arbeiten sind es jedoch nicht, wie z. B. die Ausführung der Freigabe für jede Komponente der Software durch einen Ingenieur, wenn ein Upgrade erforderlich ist. Da mühsame Arbeiten von Menschen ausgeführt werden, kann es schwieriger sein, sie zu verfolgen, da die Verfolgung mühsamer Arbeiten selbst mühsam ist. Um technische Schulden zu verwalten, ist es jedoch entscheidend, sich der mühsamen Arbeiten bewusst zu sein und einen Aktionsplan zu ihrer Reduzierung zu erstellen, um sicherzustellen, dass das Team eine akzeptable kognitive Belastung hat und weiterhin innovativ sein kann.

Die Arbeit für das Team und die Entwickler muss sowohl von Fall zu Fall als auch ganzheitlich betrachtet werden, um zu vermeiden, dass sie sich zu einer unerträglichen Belastung entwickelt. Genauso wie wir jede einzelne gespeicherte Datenmenge oder jede neue Komponente, die wir hinzufügen, hinterfragen, muss auch jede manuelle Aufgabe derselben Prüfung unterzogen werden:

- Warum müssen wir das tun?
- Wie lange dauert es?
- Wie lange müssen wir das tun?
- Können wir es automatisieren?

Wenn die Antwort auf „Können wir das automatisieren?“ „Ja“ lautet, muss dies sofort priorisiert und im Backlog der Teamaufgaben eingestuft werden, vorzugsweise mit hoher Priorität, da die Zeit der Entwickler neben den Daten eines der wertvollsten Güter des Unternehmens ist. Die Toleranz jedes Teams gegenüber mühsamer Arbeit variiert, da sie von der Zusammensetzung des Teams und seinen Fähigkeiten abhängt. Das Buch „Google SRE“ (https://sre.google/sre-book/table-of-contents/) definiert ein Zielmaximum für mühsame Arbeit von 50 %, aber Teams haben ihre eigenen Toleranzen, die auf der Persönlichkeit des Teams und anderen organisatorischen Faktoren basieren.

Betrachten wir eine extrem zeitaufwändige Aufgabe, die nur einmal erledigt werden muss. Stellen Sie sich eine Aufgabe vor, die Sie schon einmal erledigt haben; es muss nichts Besonderes sein. Einige Ingenieure sehen die manuelle Aufgabe und erledigen sie einfach. Andere bewerten die Aufgabe und automatisieren sie, auch wenn es sich um eine einmalige Aufgabe handelt und der Prozess dadurch länger dauert.

Das könnte daran liegen, dass eine von Kollegen geprüfte Automatisierung sicherer erscheint als Schritte, bei denen menschliche Fehler auftreten können, oder daran, dass sie diese Aufgabe nie wieder ausführen möchten und lieber nicht riskieren wollen, sich zu irren, wenn es sich um eine einmalige Aufgabe handelt. Es könnte auch einfach daran liegen, dass durch die Kodifizierung der durchgeführten Schritte sichergestellt wird, dass diese nicht mit der Zeit verloren gehen und nur noch als implizites Wissen weitergegeben werden. Sowohl die Ausführung der Aufgabe als auch die Erstellung der Automatisierung dafür waren Beispiele für mühsame Arbeit, aber trotz des höheren Zeitaufwands geht der Automatisierungsprozess besser mit technischen Schulden um.

Die tatsächliche Toleranz für mühsame Arbeit muss durch Ausprobieren ermittelt werden, aber eine Taktik, um die mühsame Arbeit im Griff zu behalten, besteht darin, ein SLO dafür festzulegen. Wenn Sie die für mühsame Arbeit aufgewendete Zeit als SLO behandeln und dieses SLO verletzt wird, weil beispielsweise nicht mehr als 50 % unserer Zeit für mühsame Arbeit aufgewendet wird, sollte eine Ursachenanalyse durchgeführt werden, um festzustellen, warum mehr Zeit aufgewendet wird/wurde, und um Korrekturmaßnahmen zu identifizieren, mit denen die mühsame Arbeit wieder innerhalb der erwarteten Grenzen gehalten werden kann. Die Teams sollten sich jedoch sicher fühlen, Dinge richtig zu machen, auch wenn dies bedeutet, dass das Fehlerbudget für mühsame Arbeit für einen Berichtszeitraum aufgebraucht ist.

DORA-Kennzahlen

Wenn wir auf die DORA-Metriken und -Bewertungen zurückblicken, die wir in [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) definiert haben, wird schnell klar, wie diese Metriken Ihnen helfen können, sich Ihrer technischen Schulden bewusst zu bleiben:

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
|     | **Elite** | **Hoch** | **Mittel** | **Niedrig** |
| **Bereitstellungshäufigkeit** | Auf Anfrage | Zwischen einmal täglich und einmal wöchentlich | Zwischen einmal pro Woche und einmal pro Monat | Zwischen einmal pro Woche und einmal pro Monat |
| **Änderungsvorlaufzeit** | Weniger als 1 Tag | Zwischen 1 Tag und 1 Woche | Zwischen 1 Woche und 1 Monat | Zwischen 1 Woche und 1 Monat |
| **Änderungsfehlerquote** | 5   | 10  | 15  | 64  |
| **Wiederherstellungszeit nach fehlgeschlagener Bereitstellung** | Weniger als 1 Stunde | Weniger als 1 Tag | Zwischen 1 Tag und 1 Woche | Zwischen 1 Monat und 6 Monaten |

Tabelle 9.1: DORA-Metriken-Kompetenzen

Wenn Sie etwas wie **Keptn** oder eine andere Lösung zur Erfassung von DORA-Metriken in Ihrem IDP implementiert haben, dann haben Sie wahrscheinlich damit begonnen, diese Metriken für jede Komponente innerhalb Ihres IDP zu verfolgen. Wenn Sie diese Metriken über einen längeren Zeitraum verfolgen, werden Sie möglicherweise bestimmte Trends feststellen.

Wenn beispielsweise die Vorlaufzeit für Änderungen oder die Ausfallraten bei der Bereitstellung nach 6 Monaten immer noch im niedrigen bis mittleren Bereich liegen, lohnt es sich, die Gründe dafür zu untersuchen, um festzustellen, ob es ungelöste technische Schulden gibt.

Anwendungsleistungsdaten

Relevant für DORA-Metriken, aber in anderer Hinsicht damit verbunden, sind die Leistungsdaten für die Anwendungen und Komponenten innerhalb eines IDP. Das Plattformteam ist zwar nicht für Endbenutzeranwendungen verantwortlich, aber die Plattform kennt den Status der Pods und Container, die die Anwendung verwendet. Sie kann auch den Erfolg von API-Aufrufen und Antwortzeiten erkennen. Das Plattformteam muss den Entwicklern, die es betreut, ermöglichen, diesen Status ebenfalls zu verstehen, damit sie diese Metriken bewerten und feststellen können, ob etwas nicht in Ordnung ist. Auf diese Weise können Entwickler ihre technischen Schulden verwalten. Dies ist ein wichtiger Aspekt der Wartungsfreundlichkeit und Selbstbedienung der Plattform für den anhaltenden Erfolg des Unternehmens. Denken Sie daran, dass die Plattform, sobald sie in Betrieb ist, die kritischste Anwendung innerhalb des Unternehmens ist. Sie muss sowohl ihren eigenen Erfolg als auch den Erfolg der Endbenutzeranwendung gleichermaßen unterstützen.

Eine Anwendung kann hochverfügbar gestaltet sein und die Leistungsfähigkeit der K8s-Plattform voll ausschöpfen, aber dadurch können auch unbeabsichtigt Probleme oder Muster verschleiert werden, die Anlass zur Sorge geben könnten. Daher sollte die Anwendungsleistung regelmäßig gemessen und offengelegt werden. In einem für Hochverfügbarkeit ausgelegten System kann beispielsweise ein Pod mit drei ReplicaSets dafür sorgen, dass die Anwendung ohne Unterbrechungen oder scheinbar ohne Unterbrechungen läuft, selbst wenn es gelegentlich zu einem OOM oder anderen Abstürzen kommt. Die Plattform würde jedoch von diesen Abstürzen wissen, und mithilfe der Beobachtbarkeit kann sichergestellt werden, dass auch die Entwickler, die für die Anwendung verantwortlich sind, davon Kenntnis erhalten.

In [Kapitel 6](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/6) haben wir Möglichkeiten diskutiert, wie die Plattform die Beobachtbarkeit unterstützen, bei Bedarf ein wenig vorschreibend sein und Entwicklern Selbstbedienung ermöglichen kann. Schauen wir uns ein Beispiel an, bei dem die IDP vorschreibend sein kann, was gemessen wird, da der Zustand der Anwendung für die Plattform am einfachsten sichtbar ist.

Identifizieren anderer kritischer Daten

In [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) haben wir KPIs definiert, um die Einführung des IDP voranzutreiben. Dieselben Datenpunkte und Metriken, die die Einführung vorantreiben, können auch genutzt werden, um Innovationen voranzutreiben und technische Schulden zu verwalten. Wenn Sie die Einführung messen, haben Sie natürlich auch alle Fehler im Zusammenhang mit der Einführung gemessen. Diese Fehler sind wichtige Datenpunkte, die Ihrem Team helfen können, zu verstehen, wie Entwickler mit der Plattform umgehen.

In [Kapitel 6](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/6) wurde hervorgehoben, wie die Plattform in die Arbeitsweise des Unternehmens integriert werden kann, und wir haben das Beispiel einer fehlgeschlagenen Einführung von Tekton zugunsten von GitHub- -Workflows angeführt. Dies ist ein Beispiel für das Management technischer Schulden sowie für eine nicht ausreichend genutzte Komponente, die möglicherweise keinen ausreichenden **Return on Investment** (**ROI**) bietet, um die laufenden Wartungskosten zu rechtfertigen. Nutzungsmetriken wie die Anzahl der Anmeldungen oder – im Fall von Tekton – die pro Tag, Woche und Monat geplanten Jobs sind wichtige Kennzahlen. Wenn die Plattform oder eine Komponente der Plattform im Laufe der Zeit keine Steigerung der Nutzung verzeichnet, insbesondere im Vergleich zur Plattform als Ganzes, ist es an der Zeit, diese Komponente zu evaluieren.

Bietet die Komponente einen ROI, reduziert sie die kognitive Belastung, erfüllt sie die SLO-Ziele und sind die Entwickler damit zufrieden? Wenn die Plattform oder eine Komponente in dieser Hinsicht versagt, dann hat sie im Vergleich zu den Erträgen mehr Punkte auf der Seite der technischen Schulden in der Bilanz.

Datenaufbewahrung ist technische Schuld

Obwohl Observability-Daten für Entscheidungen über die Zukunft der Plattform unglaublich nützlich sind, ist es wichtig, nur so viele Daten zu speichern, wie Sie benötigen. Mit zunehmender Menge an gespeicherten Daten werden Sie wahrscheinlich feststellen, dass deren Aufbewahrung immer weniger Nutzen bringt und deren Pflege einen hohen Aufwand bedeutet. Je mehr Datenspeicher ein System benötigt, desto kritischer wird die Gestaltung dieses Datenspeichers, da er sich mit zunehmender Datenmenge negativ auf die Systemleistung auswirken kann. Da Daten zudem das wichtigste Kapital und im Falle eines Sicherheitsvorfalls am stärksten gefährdet sind, hilft die Aufbewahrung nur der unbedingt notwendigen Daten dabei, das Risiko und den Aufwand für die Messung der Auswirkungen eines Datenlecks zu begrenzen. Wir Autoren können zwar nicht garantieren, wie viele oder wie wenige Daten Sie benötigen, um die Anwendungsleistungsmetriken zu erhalten, während Sie sorgfältig entscheiden, welche Daten Sie aufbewahren, und die Best Practices befolgen, aber was wir hier und in [Kapitel 7](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/7) dargelegt haben, sollte dazu beitragen, dass die aufbewahrten Daten überschaubar bleiben. Zu beachten ist, dass sich die Plattform, die Nutzer und die Technologie von Jahr zu Jahr stark verändern werden, sodass Daten, die über längere Zeiträume aufbewahrt werden, mit der Modernisierung der Plattform im Einklang mit der Branche immer weniger relevant werden. Es ist am besten, sicherzustellen, dass alle aufbewahrten Daten einen zwingenden Grund für ihre Aufbewahrung haben, da sie sonst nur eine weitere Belastung für die Bilanz darstellen.

Nachdem wir nun mehr darüber wissen, wie wir Daten zur Identifizierung und Verwaltung technischer Schulden nutzen können, wollen wir dies nun praktischer auf unsere Plattform anwenden.

Pflege und Überarbeitung technischer Schulden

Jeder Aspekt der bisherigen Erstellung eines IDP stellt eine technische Schuld dar. Idealisten würden Ihnen sagen, dass es keine technischen Schulden gibt, wenn Sie kluge Entscheidungen getroffen haben, aber ehrlich gesagt ist das nicht ganz richtig. Ein einst florierendes Open-Source-Projekt kann ohne Vorwarnung eingestellt werden oder es kann unerwartet eine CVE auftreten. Es wird immer Schulden geben, unabhängig von den besten Bemühungen. Entscheidend für die Gesundheit einer Organisation ist die Fähigkeit, die Folgen solcher Ereignisse zu bewältigen und ein angemessenes Innovationstempo aufrechtzuerhalten.

Übernehmen Sie Verantwortung für Ihre technischen Schulden

Verantwortung für Ihre Architektur zu übernehmen bedeutet, Verantwortung für die damit verbundenen technischen Schulden zu übernehmen. Das klingt zwar nach einem abstrakten Konzept, aber wenn wir beginnen, die Komponenten unserer Architektur zu bewerten, wird schnell klar, wie groß die Auswirkungen sind. Erinnern Sie sich an diesen wichtigen Hinweis aus [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2)?

Wichtiger Hinweis

Die Umgebung, die Sie für Ihre Plattform wählen, schreibt automatisch bestimmte Teile Ihrer Plattform vor, ob Sie das wollen oder nicht! Eine exponentielle Zunahme der Anzahl von Cloud- und Infrastruktur-Anbietern erhöht die Herausforderungen für Ihr Plattformdesign.

Die zur Unterstützung des IDP erforderliche Infrastruktur kann einer der umfangreichsten Posten in der technischen Bilanz sein. Verantwortung bedeutet, dass die Schulden und die damit verbundenen Risiken klar definiert und verstanden sind. Manchmal kann dieses Risiko sicherheits- oder compliancebezogene Risiken bedeuten, aber im Zusammenhang mit technischen Schulden meinen wir in der Regel das Risiko für die Fähigkeit des Teams, ein Produkt zu warten und zu liefern, ohne auszubrennen. Es ist Aufgabe des Plattformarchitekten, diese Verantwortung zu übernehmen, aber er kann hier kein Superheld sein. Die Verantwortung für technische Schulden, einschließlich der Reaktion auf unerwartete Situationen, ist eine Teamleistung.

Technische Schulden und Teamzeremonien

Der einfachste Weg, das gesamte Team in die Verantwortung für technische Schulden einzubeziehen, besteht darin, diese in die Zeremonien zu integrieren, an denen das Team teilnimmt. Das endgültige Aussehen sollte vom Team selbst gestaltet werden. In einer agilen Arbeitsumgebung kann dies eine spezielle Überprüfung der technischen Schulden während der Planungsphase jedes Sprints oder Projekts umfassen, aber auch eine bestimmte Zeit pro Sprint, die für den Abbau technischer Schulden aufgewendet wird, z. B. durch die Reduzierung von Arbeitsaufwand oder die Umsetzung identifizierter Verbesserungsmöglichkeiten.

Wenn Ihr Plattformteam nach der Kanban-Methode arbeitet, kann es auch eine gute Strategie sein, sicherzustellen, dass das Backlog so gestaffelt ist, dass technische Schulden unter den übrigen Aufgaben aufgegriffen werden.

Wichtiger Hinweis

Es besteht ein sehr reales und sehr ernstes Risiko, dass diese Punkte zugunsten anderer Aufgaben ständig zurückgestellt werden. Dies hat jedoch einen Schneeballeffekt: Je länger die Arbeit aufgeschoben wird, desto größer wird der Aufwand, der zur Bewältigung der technischen Schulden erforderlich ist.

Es ist wichtig, unveränderliche Methoden zu entwickeln, um technische Schulden unter Kontrolle zu halten. Viele Unternehmen haben unterschiedliche Strategien zur Lösung unerwarteter Probleme. Wichtig ist es, die soziotechnischen Aspekte Ihres Unternehmens zu beherrschen, um sicherzustellen, dass das Gleichgewicht nicht aus den Fugen gerät.

Kombinierbarkeit der Plattform

Die Kombinierbarkeit der Plattform eignet sich gut für Überarbeitungen. Die Komponenten des IDP sollten weitgehend eigenständig sein und nur wenige – wenn überhaupt – gegenseitige Abhängigkeiten aufweisen. Daher sollte das Team sich befähigt fühlen, diesen Aspekt der Plattform zu nutzen und Komponenten gegebenenfalls auslaufen zu lassen und zu ersetzen.

Das Team muss diese Entscheidung sorgfältig treffen, da das Ersetzen einer bestehenden Komponente etwas komplizierter ist als das Hinzufügen einer neuen. Zusätzlich zur Beantwortung der Fragen zur Bewertung neuer technischer Schulden muss eine weitere Reihe von Fragen beantwortet werden, um die alten Schulden auslaufen zu lassen.

Hier sind einige Kriterien für die Abkündigung, die zu berücksichtigen sind:

- Verlieren wir dauerhaft die Funktionalität, die wir benötigen oder die uns wichtig ist?
- Wie wirkt sich dies auf die Nutzer aus?
- Wie würde der Übergangsplan aussehen?
- Wie sieht der Zeitplan aus?
- Ersetzen wir die Funktion oder entfernen wir sie nur?
- Wie lange würden sich das Original und der Ersatz überschneiden?
- Gibt es einen Kostenunterschied? Wenn ja, welchen?
- Was sind die neuen Wartungsanforderungen?

Abhängigkeiten

Das Management von Abhängigkeiten ist einer der Schlüsselbereiche beim Umgang mit technischen Schulden. Auch wenn die Übernahme mehrerer Lösungen, die das Team nicht kontrolliert, für manche zunächst wie ein Anti-Muster erscheinen mag, ist es in der Realität in der Regel einfacher, den Status Ihrer Abhängigkeiten zu verwalten, als zu versuchen, innerhalb einer angemessenen Zeitspanne ein voll funktionsfähiges, maßgeschneidertes IDP zu schreiben.

Wenn wir uns unsere Abhängigkeitsmatrix aus [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) ansehen, können wir sie auf Diskussionen über die Wartung der Plattform und ihre Schulden anwenden:

Abbildung 9.2: Abhängigkeitsmatrix

Ihre Plattform kann verschiedene Arten von Abhängigkeiten aufweisen. Hier sind einige offensichtliche Beispiele:

- Open-Source-Komponenten
- Netzwerke und Netzwerkgeräte
- Datenbanken
- Kostenpflichtige Komponenten
- Interne oder maßgeschneiderte Dienste

In einer perfekten Welt wäre ein IDP immer vollkommen einheitlich, unabhängig davon, wo er eingesetzt wird. Bei Multi-Cloud- oder Multi-Architektur-Implementierungen sind die Infrastrukturabhängigkeiten jedoch wahrscheinlich ähnlich, aber dennoch unterschiedlich. Daher müssen Sie möglicherweise mehrere verschiedene Versionen dieser Matrix erstellen und pflegen, um der Umgebung gerecht zu werden. Unabhängig davon, wie Sie sich entscheiden, müssen Sie sicherstellen, dass diese Dokumente „ ” auf dem neuesten Stand gehalten werden, um Fehler oder sicherheitsrelevante Probleme in der Zukunft zu vermeiden.

Sicherheit

Sicherheitsbest Practices werden oft als „bewegliches Ziel” bezeichnet und entwickeln sich mit der Branche weiter und verändern sich. Wenn diese Veränderungen eintreten, ist Ihre Software nicht mehr auf dem neuesten Stand, und die Notwendigkeit, aufzuholen, wird zu einem Posten in Ihrer technischen Schuldenbilanz. Wenn wir uns beispielsweise die Workload-Identitäten der großen Cloud-Anbieter ansehen, sehen wir ein etwas zeitnahes Beispiel für den Wandel in der Branche und eine neue Welle von technischen Schulden, die identifiziert werden.

Früher war die Verwendung von Geheimnissen durch Anwendungen die Norm, und die mit diesen Geheimnissen verbundenen Risiken wurden akzeptiert. Die Minderung dieser Risiken stellte zwar eine technische Schuld dar, aber zu dieser Zeit gab es keine bessere Alternative. Mit der Erfindung von Workload-Identitäten entfiel jedoch die Notwendigkeit für Anwendungen, Geheimnisse für die Interaktion mit den Cloud-Anbietern zu verwenden. Stattdessen verfügen sie über eine rollenbasierte Identität, mit der sie kurzlebige Token erhalten können, ähnlich wie es bei menschlichen Benutzern der Fall ist.

Nachdem diese Technologie nun bei allen drei großen Cloud-Anbietern Einzug gehalten hat, gibt es branchenweit Bestrebungen, Anwendungen zu modernisieren und anstelle von Geheimnissen Workload-Identitäten zu nutzen. Bei einigen Anwendungen ist dies durch eine Umgestaltung möglich, bei anderen kann dies jedoch bedeuten, dass eine neue Komponente hinzugefügt werden muss oder eine vollständige Neuprogrammierung erforderlich ist.

Nicht alle technischen Schulden haben das gleiche Gewicht

Die vorherige Unterüberschrift zum Thema Sicherheit ist wahrscheinlich der offensichtlichste Fall dafür, aber nicht alle technischen Schulden haben das gleiche Gewicht. Alles, was die Integrität des Systems beeinträchtigt, wie z. B. Sicherheit und Compliance, wird sehr stark gewichtet, obwohl auch andere Punkte, die mit einem hohen Zeitaufwand verbunden sind, ganz oben auf der Liste stehen können.

Beispielsweise kann die Veröffentlichung einer neuen Anwendung zwar beim ersten oder zweiten Mal manuell erfolgen, wird aber schnell automatisiert. Von da an übernimmt die Automatisierung, die weniger zeitaufwändig zu starten und weniger schwierig zu warten ist. Dies ist eine schnelle und offensichtliche Reduzierung des Aufwands für die Verwaltung der Software, aber die Automatisierung muss dennoch gewartet werden, was als technische Schuld angesehen wird. Da es jedoch unwahrscheinlich ist, dass sich daran häufig etwas ändert, ist diese Schuld weniger schwerwiegend als der Release-Prozess, wenn er als manueller Prozess belassen worden wäre.

Aus diesem Grund ist es wichtig, regelmäßig zu überprüfen und zu verstehen, wofür Ihr Team seine Zeit aufwendet, wenn es nicht innovativ tätig ist, oder welche Lücken im Angebot der Plattform identifiziert wurden.

Nachdem wir nun besprochen haben, wie Sie Ihre technischen Schulden in den Griff bekommen können, wollen wir uns näher damit befassen, wann diese Schulden umgestaltet oder neu geschrieben werden sollten.

Neuschreiben versus Refactoring von Daten – ein praktischer Leitfaden

Wenn sich technische Schulden häufen, verbringt das Team immer mehr Zeit damit, diese Schulden oder deren Folgen zu bewältigen, und weniger Zeit mit Innovationen. In der Praxis äußert sich dies in einem höheren Arbeitsaufwand, längeren Einarbeitungs- und Onboarding-Phasen für neue Teammitglieder und Nutzer sowie in einem Burnout des Teams. Es ist wichtig, den Überblick über die technischen Schulden zu behalten, um sicherzustellen, dass die Zufriedenheit der Entwickler und die Innovation für das Plattformteam im Vordergrund stehen.

Manchmal kann dieser Schneeball darin bestehen, dass Dinge nicht mehr wie erwartet funktionieren oder mehr Zeit als erwartet in Anspruch nehmen. Alternativ könnte es sein, dass der einst als akzeptabel angesehene Arbeitsaufwand für den Betrieb der Plattform nun verhindert, dass die Plattform und das Team mit dem Wachstum der Nutzerbasis Schritt halten können. Unabhängig davon, um welchen Fall es sich genau handelt, muss das Team, sobald diese technischen Schulden die vordefinierten Erwartungen für einen normalen Betrieb übersteigen, prüfen, was erforderlich ist, um zum Normalzustand zurückzukehren oder einen neuen guten Zustand zu finden.

Eine Möglichkeit hierfür könnte die Umgestaltung einiger Plattformen sein. Eine Umgestaltung könnte eine relativ schnelle Änderung für langfristigen Gewinn ermöglichen. Als beispielsweise Golang die Art und Weise änderte, wie es die Versionsadressierung für Abhängigkeiten durchführte, mussten viele Teams ihre Importe anpassen, um sie an die neue, bessere Methode anzupassen. Hier sind einige weitere Gründe für eine Umgestaltung:

- Verbesserung der Effizienz
- Verbesserung der Sicherheit
- Hinzufügen oder Ändern einer Schnittstelle

Wenn es jedoch keine Möglichkeit gibt, mit der aktuellen Codebasis oder Komponentenliste den gewünschten Zustand zu erreichen, kann eine Neuprogrammierung in Betracht gezogen werden. Wir haben bereits festgestellt, dass das System in seiner Grundform komponierbar sein sollte, d. h. es sollte nur wenige – wenn überhaupt – serverlose Funktionen oder Skripte als Hilfsmittel geben. Ein Grund für die Neuprogrammierung eines Dienstes w , wäre, wenn die weitere Nutzung des Dienstes die Hinzufügung dieser Art von Hilfs-Workload erforderlich machen würde. **Envoy Proxy** ist ein Beispiel für eine solche Hilfs-Workload. In der Dokumentation wird es als „ein leistungsstarker verteilter C++-Proxy für einzelne Dienste und Anwendungen sowie als Kommunikationsbus und „universelle Datenebene” für große Microservice-„Service-Mesh”-Architekturen” beschrieben, der „parallel zu jeder Anwendung läuft und das Netzwerk abstrahiert, indem er gemeinsame Funktionen plattformunabhängig bereitstellt”. (Quelle: https://www.envoyproxy.io/). In diesem Beispiel ist Envoy Proxy zwar sehr leistungsfähig, aber wenn der einzige Grund für seine Implementierung darin besteht, einen einzelnen Dienst zu unterstützen, der in einer anderen Sprache als die übrigen Dienste geschrieben ist, dann ist es möglicherweise sinnvoller, den Ausreißer neu zu schreiben, als die Envoy Proxy-Schicht hinzuzufügen.

Das Hinzufügen von Envoy Proxy wäre zwar eine elegante und sofort einsatzbereite Lösung, aber es handelt sich um eine ziemlich komplexe Schicht, die der Kubernetes-Plattform hinzugefügt werden muss, und dies für nur einen Dienst zu tun, müsste im Vergleich zur Neuprogrammierung dieses Dienstes gerechtfertigt sein.

Entscheiden, ob eine Neuprogrammierung notwendig ist

Stellen Sie sich vor, Sie sind Mitglied eines Plattformteams und betrachten eine Komponente, um über deren Zukunft zu entscheiden. Was würde Sie dazu veranlassen, zu entscheiden, dass es an der Zeit ist, sich von der Komponente in ihrem aktuellen Zustand zu verabschieden? Ein Grund könnten Änderungen der Lizenzbedingungen sein. Wenn das von Ihnen verwendete Tool früher Open Source war, nun aber andere Lizenzbedingungen hat, ist es möglicherweise an der Zeit, es zu ersetzen. Schließlich werden für die Open-Source-Version möglicherweise keine sicherheitsrelevanten Updates mehr bereitgestellt, und Ihr Team verfügt möglicherweise nicht über die erforderlichen Kenntnisse, um das Tool in seiner aktuellen Form zu warten.

Der Entscheidungsbaum für die Neuprogrammierung einer Komponente sollte fast identisch mit dem Entscheidungsbaum für „Build versus Buy“ sein. Wenn Sie an einem Punkt angelangt sind, an dem eine Neuprogrammierung erforderlich erscheint, muss die „Build versus Buy“-Diskussion erneut geführt werden. Wenn es eine Open-Source-Lösung oder eine erschwingliche Lösung im Handel gibt, könnte sich Ihre Neuprogrammierung auf die Implementierung einer neuen Integration beschränken. Ist dies jedoch nicht der Fall, muss möglicherweise ein maßgeschneiderter Service erstellt werden.

Wenn Sie jedoch die Funktionalität erweitern oder Leistungssteigerungen erzielen möchten, ist dies sehr unwahrscheinlich und eine vollständige Neuprogrammierung erforderlich. Sofern die Komponente nicht sehr alt ist oder seit ihrer Erstellung überhaupt nicht gewartet wurde, ist es wahrscheinlich besser, Ihre Codebasis zu überarbeiten.

Untersuchung der externen Einflüsse auf die Refaktorierung anhand eines Beispiels

Manchmal entsteht die Notwendigkeit einer Refaktorierung nicht intern, sondern ist das Ergebnis einer Änderung eines Tools oder einer Technologie innerhalb Ihres Ökosystems. Leider haben die Entscheidungen, die von den Betreuern dieser Abhängigkeiten getroffen werden, direkten Einfluss auf die technischen Schulden Ihres Teams und können dazu führen, dass die Implementierung dieses Tools refaktoriert werden muss.

Ein gutes Beispiel für einen Zeitpunkt für eine Refaktorisierung wäre der Übergang von Helm (https://helm.sh/) Version 2 zu Helm Version 3 für die Kubernetes-Paketverwaltung. Helm ist ein Paketmanager für Kubernetes-Bereitstellungen. Es handelt sich um ein Open-Source-Tool, das ein als **Charts** bekanntes Paketformat verwendet, um den Prozess der Installation und Aktualisierung von Anwendungen auf einem Cluster zu koordinieren. Ein Chart ist keine einzelne Datei, sondern eine Sammlung von Dateien, die die für die Ausführung einer Anwendung erforderlichen Kubernetes-Ressourcen definieren. Beispielsweise kann Argo CD mit Helm-Charts auf einem Kubernetes-Cluster installiert werden.

Helm 2 war bis zur Veröffentlichung von Helm 3 im November 2019 eine beliebte Version von Helm, hatte jedoch einige Nachteile bei der Verarbeitung von **Customer Resource Definitions** (**CRDs**). Auch wenn Helm heute noch keine Aktualisierung oder Löschung von CRDs unterstützt, hilft die neue Methode Helm dabei, für Benutzer, die CRDs nutzen, besser zu funktionieren.

Was war also das Problem, das Helm 3 gelöst hat? Schauen wir uns zunächst einmal an, was eine CRD ist. Dies wurde in [Kapitel 4](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/4) ausführlich erklärt, aber falls Sie es vergessen haben: Eine CRD erweitert die Kubernetes-API. Funktional bedeutet dies, dass Ihr Kubernetes-Cluster nun über ein Konzept Ihrer benutzerdefinierten Ressource verfügt. In Helm 2 erfolgte die Verarbeitung von CRDs über die Hook-Methode „crd-install“. Der Hook-Mechanismus in Helm ermöglicht es einem Chart, auf eine andere Abhängigkeit zuzugreifen und diese zu nutzen, bevor das Chart ausgeführt wird. Obwohl dies theoretisch hätte funktionieren müssen, kam es dennoch zu Situationen, in denen Helm eine CRD nicht kannte, sodass die API-Erweiterung von Helm nicht verstanden wurde, um ein Chart zu validieren. Wenn nach einer Installation ein neues CRD hinzugefügt wurde, schlugen Upgrades fehl, da die crd-install-Hook-Methode nicht ausgeführt wurde. Das bedeutete, dass frühere Versionen der Charts vollständig gelöscht und ersetzt werden mussten, wenn sich ein CRD änderte. Dies war für Helm-Benutzer ziemlich störend, und viele Teams mussten dafür Workarounds in ihren CI/CD-Pipelines implementieren.

Helm 3 hat diese Benutzererfahrung geändert, indem es die bisherige crd-install-Hook-Methode als veraltet deklariert und die zugrunde liegende Funktionalität, die sie unterstützte, entfernt hat. Jetzt wird ein CRD-Verzeichnis benötigt. Der Verzeichnispfad ist innerhalb des Charts verschachtelt, und die Verwendung dieses Verzeichnisses namens crds/ ermöglicht es Helm, anzuhalten, während die CRDs zu einem Cluster- us hinzugefügt werden, bevor die Ausführung des Charts fortgesetzt wird. Helm-Upgrades ermöglichen nun die Installation von CRDs, was zuvor nicht der Fall war. Im Wesentlichen kennt Helm nun bei der Chart-Validierung die neuen API-Funktionen, was eine reibungslosere Bedienung für die Benutzer gewährleistet.

Die zugrunde liegenden Änderungen an Helm waren zwar ziemlich umfangreich, für die Benutzer von Helm bedeutete dies jedoch lediglich eine Überarbeitung bestehender Charts und ein Upgrade der verwendeten Helm-Version. Dadurch konnten viele Benutzer jedoch auch ihre bisher implementierten Workarounds entfernen und stattdessen die integrierte Upgrade-Funktionalität von Helm nutzen. Je nach Größe und Komplexität der verwendeten Charts konnten diese Refactorings einen gewissen Aufwand bedeuten, aber bei weitem nicht so viel wie die Umstellung auf eine völlig andere Art der Handhabung von Softwareinstallationen und -upgrades.

Um den ungefähren Umfang der Refactoring-Änderungen zu verstehen, schauen wir uns die aktuellen Argo CD Helm Charts mit Helm 3 an (https://github.com/argoproj/argo-helm/tree/main/charts). Innerhalb des Repositorys gibt es eine Sammlung von Charts, die jeweils als Teil des gesamten Argo CD-Projekts installiert sind. Bei Helm ist die Verzeichnisstruktur sehr wichtig; ohne die richtige Struktur kann ein Chart nicht funktionieren.

Wenn wir uns eines der Charts ansehen, sehen wir, dass das neue CRD-Verzeichnis vorhanden ist:

Abbildung 9.3: Verzeichnisstruktur von Argo CD Helm Chart

Wenn wir uns die Datei values.yaml in einem dieser Charts ansehen, stellen wir fest, dass die Verwendung von CRD sehr einfach ist:

Abbildung 9.4: CRD-Konfiguration in einer Helm-Chart-Datei „values.yaml“

Der eigentliche Großteil der Arbeit zur Nutzung von CRDs aus Entwicklungssicht liegt in den CRD-Definitionen selbst. Hier werden die CRD-Annotationen definiert und alle anderen erforderlichen Logiken, wie z. B. die Ressourcenrichtlinie, angegeben:

Abbildung 9.5: Ein CRD aus dem Argo CD-Projekt

Nachdem wir gesehen haben, wie CRDs heute mit Helm-Charts verwendet werden, liegt die Frage nahe: „Wie sah es vorher aus?“ Die Antwort lautet: „Es kommt darauf an.“ Bevor der crd-intall-Hook zu Helm hinzugefügt wurde, bestand eine gängige Methode zur Umgehung dieses Problems darin, CRDs in separate Charts aufzuteilen und dann mit einem Bash-Skript sicherzustellen, dass die Charts in einer bestimmten Reihenfolge installiert wurden. Das Istio-Projekt ist ein Beispiel dafür, wo dies umgesetzt wurde. Das funktionierte zwar, verursachte aber einen höheren Wartungsaufwand, da die Skripte zur Sicherstellung der ordnungsgemäßen Installation eine weitere Aufgabe für die Helm-Chart-Betreuer darstellten, die sie auf dem neuesten Stand halten mussten.

Nachdem Helm den Installations-Hook hinzugefügt hatte, wurde es möglich, solche Skripte zu veralten. Unter Beibehaltung der gleichen CRD-Dateien konnte ein Benutzer die crd-install-Hook-Anmerkung hinzufügen. Dann stellte die zugrunde liegende Komponente von Helm, Tiller, sicher, dass die CRD-Erstellung ausgelöst wurde, bevor der Rest des Charts ausgeführt wurde.

Die Helm 2-Dokumentation erklärt dies näher (https://v2.helm.sh/docs/charts_hooks/#hooks). Wichtig zu wissen ist, dass eine YAML-Datei, die den crd-Hook enthält, zunächst wie folgt aussehen würde:

apiVersion: apiextensions.k8s.io/v1beta1

kind: CustomResourceDefinition

metadata:

&nbsp; name: crontabs.stable.example.com

spec:

&nbsp; Gruppe: stable.example.com

&nbsp; version: v1

&nbsp; Gültigkeitsbereich: Namespaced

&nbsp; Namen:

&nbsp;   Plural: crontabs

&nbsp;   Singular: crontab

&nbsp;   Art: CronTab

&nbsp;   Kurznamen:

&nbsp;   - ct

KopierenErklären

Danach würde es so aussehen:

apiVersion: apiextensions.k8s.io/v1beta1

Art: CustomResourceDefinition

Metadaten:

&nbsp; name: crontabs.stable.example.com

&nbsp; Anmerkungen:

&nbsp;   „helm.sh/hook”: crd-install

Spezifikation:

&nbsp; Gruppe: stable.example.com

&nbsp; Version: v1

&nbsp; Gültigkeitsbereich: Namespaced

&nbsp; names:

&nbsp;   Plural: crontabs

&nbsp;   Singular: crontab

&nbsp;   Art: CronTab

&nbsp;   Kurznamen:

&nbsp;   - ct

KopierenErklären

An sich handelt es sich hierbei um eine sehr kleine Änderung. Die verwendete Helm-Version musste ebenfalls aktualisiert werden, aber insgesamt war dies nur ein sehr geringer Arbeitsaufwand, der es den Personen, die Helm Charts für ihre Anwendungen verwalten, ermöglichte, viele benutzerdefinierte Bash-Skripte zu entfernen.

Manchmal ist der Prozess der Refaktorisierung recht geringfügig. Er kann so einfach sein wie das Identifizieren einiger weniger ineffizienter Bereiche oder einer Stelle, an der der Code auf Race Conditions stoßen könnte, und das Vornehmen von Änderungen am Code, um diese Situationen zu verbessern. In anderen Fällen kann die Refaktorisierung umfassender sein, z. B. das Ersetzen einer Bibliothek oder das Aktualisieren der Sprachversion auf eine Version mit einigen grundlegenden Änderungen. Unabhängig vom Grund für die Refaktorisierung ist der Aufwand in der Regel geringer und die Rendite höher als bei einer Neuprogrammierung.

Betrachtung einer berühmten Neuprogrammierung

Wenn immer noch unklar ist, wann eine Neuprogrammierung die richtige Wahl ist, können wir uns einige berühmte Neuprogrammierungsszenarien aus Open-Source-Softwareprojekten ansehen. Innerhalb des Linux-Kernels sowie der Containertechnologie selbst und damit auch von Kubernetes finden wir ein perfektes Beispiel in cgroups. Cgroups, auch bekannt als Kontrollgruppen, sind eine Technologie, die innerhalb des Linux-Kernels zur Verwaltung von Rechenprozessen existiert. Cgroups verwalten die Ressourcenzuweisung und steuern im Allgemeinen Prozesse. Vor kurzem gab es jedoch als Reaktion auf Forderungen der Community nach Leistungsverbesserungen eine Neuprogrammierung, und cgroupsv2 wurde geboren.

Dieses Beispiel ist aufgrund des Pile-on-Effekts besonders interessant. Während cgroupsv2 allgemein als v1 überlegen angesehen wird und die meisten Anwendungen Leistungssteigerungen erzielen, können ältere Anwendungen darunter leiden. In Kubernetes, wo eine cgroups-Version oder - s andere angegeben werden muss, ist das Problem mit Legacy-Anwendungen offensichtlich. Insbesondere ältere Java- und Node.js-Anwendungen werden Kompatibilitätsprobleme mit den Speicherabfragefunktionen von cgroupsv2 haben und wahrscheinlich Out-of-Memory-Fehler (**OOM**) erleben, die zum Absturz der Workload führen. Für Unternehmen, die ältere Anwendungen verwenden, ist ein Upgrade des Stacks angezeigt. Dies kann entweder eine Neuprogrammierung oder eine Umgestaltung bedeuten, je nachdem, wie weit der Legacy-Code hinterherhinkt und was erforderlich ist, um ihn auf eine mit dem neuen cgroupsv2 kompatible Version zu bringen.

Diejenigen, die sich besser mit Kubernetes auskennen, werden vielleicht bemerken, dass Kubernetes in der aktuellen Version 1.30 von K8s immer noch die Möglichkeit bietet, cgroups v1 zu verwenden. Das ist richtig, und jedes Unternehmen, das keine Modernisierung wünscht, kann diese Möglichkeit nutzen. Es wäre jedoch fahrlässig, sich auf die Fortführung von cgroupsv1 gegenüber der neu geschriebenen Version zu verlassen, da es wahrscheinlicher ist, dass v1 veraltet sein wird, anstatt dass zwei Versionen gepflegt werden. Wenn eine Modernisierung nicht gewünscht ist, würden statt einer neuen technischen Schuld die Cluster-Konfigurationen, die cgroupsv1 spezifizieren, zum Team-Ledger hinzugefügt werden. Alle neuen Cluster müssen unter Verwendung der cgroupsv1-Spezifikationen erstellt werden, solange diese unterstützt werden oder solange die Legacy-Anwendungen nicht modernisiert werden. Wenn die Erstellung der Cluster automatisiert ist, müsste dies überarbeitet und zur zusätzlichen Konfiguration hinzugefügt werden. Zwar können modernere Anwendungen mit cgroupsv1 ausgeführt werden, jedoch sind sie möglicherweise nicht so leistungsfähig wie mit cgroupsv2. Unabhängig davon, ob die Entscheidung für eine Überarbeitung der Clustererstellung oder für eine Modernisierung der Workloads, die auf älteren Sprachversionen liefen, getroffen wurde, hatten die Auswirkungen dieser Neuprogrammierung Auswirkungen auf die gesamte Branche.

Eine letzte Folge der Neuprogrammierung und der anschließenden Einführung von cgroupsv2 als Standard ist, dass einige neue, in Kubernetes integrierte Funktionen nur mit der neueren Version kompatibel sind. Mit anderen Worten: Wenn Sie bei cgroupsv1 bleiben, schränken Sie Ihre Möglichkeiten ein und können einige der Verbesserungen von Kubernetes für das Workload-Management nicht nutzen.

Übergang nach der Neuprogrammierung

Sie haben die Neuprogrammierung (oder vielleicht den Austausch) durchgeführt und es ist Zeit für die Umstellung. Leider verlaufen solche Übergänge selten – wenn überhaupt – reibungslos und erfordern in der Regel eine präzise Planung und Ausführung. Je chaotischer der Prozess ist, desto länger muss die ursprüngliche Komponente bestehen bleiben und desto länger muss das Team die mit beiden verbundenen Betriebskosten ausgleichen. Um einen reibungsloseren Übergang zu ermöglichen, sollten Sie frühzeitig einen Übergangsplan erstellen und diesen nach Möglichkeit testen, um sicherzustellen, dass nichts übersehen wurde. Darüber hinaus hat das Erstellen und Testen eines Übergangsplans noch einen weiteren Vorteil. Der fertige Plan und die Tests werden zu einer Aufzeichnung der Ereignisse und zu einer Blaupause für zukünftige Migrationen, die möglicherweise erforderlich werden. Wir hoffen zwar immer, dass eine Neuprogrammierung nur einmal erforderlich ist, aber in Wirklichkeit kommt es in jedem Unternehmen, das über einen längeren Zeitraum besteht, zu mehreren Neuprogrammierungen. Indem Sie diesen Prozess dokumentieren, tragen Sie dazu bei, die technischen Schulden der Neuprogrammierung zu verringern. Dies hilft zukünftigen Ingenieuren, die Geschichte des Systems zu entwirren, und spart ihnen Zeit bei der Erstellung von Übergangsplänen in der Zukunft.

Dokumentation architektonischer Entscheidungen – für die Nachwelt

**Ein Protokoll der Architekturentscheidungen** hilft zukünftigen Eigentümern der Plattform, nicht nur zu verstehen, was getan wurde, sondern auch warum es getan wurde. Die Pflege genauer Architekturdiagramme und Dokumentationen ist für das Verständnis jedes Softwaresystems von entscheidender Bedeutung, aber die Gründe für diese Entscheidungen und die endgültigen Zustände helfen zukünftigen Führungskräften zu wissen, was sie in Zukunft mit der Plattform tun müssen.

Warum sollte die Softwarearchitektur dokumentiert werden?

Die Softwarearchitektur sollte aus mehreren Gründen dokumentiert werden. Erstens kann sie neuen Teammitgliedern und Benutzern helfen, sich in das Projekt einzuarbeiten. Ein gutes Architekturdokument hilft diesen Personen zu verstehen, wie das System verwendet wird und wie Daten durch das System fließen.

Zweitens kann es zur Sicherheit und Compliance beitragen, da alle Sicherheits- und Compliance-Audits gründliche Softwarearchitektur-Dokumente und -Diagramme erfordern.

Schließlich bietet sie Ihnen einen Ausgangspunkt, von dem aus Sie weiter wachsen können. Indem Sie den aktuellen Stand dokumentieren, schaffen Sie ein Referenzdokument, auf das Sie sich bei der Planung stützen können. Wie könnte ein zukünftiger Architekt herausfinden, in welche Richtung sich die Plattform entwickeln sollte, ohne genau zu wissen, wo sie derzeit steht?

Wie sieht eine gute technische Dokumentation aus?

Ein gutes Architekturdokument enthält eine Mischung aus Bildern und Beschreibungen. Je nach Detaillierungsgrad des Dokuments sollte es zeigen, wie die Benutzer mit dem System interagieren, welche Abhängigkeiten das System hat, wie Daten bewegt und gespeichert werden, wo Daten geändert werden (falls überhaupt) und welche Ergebnisse von Interaktionen zu erwarten sind. Mit anderen Worten: Die Dokumentation sollte erfassen, was das System tut und wie es dies tut.

Eine zusätzliche Funktion der Dokumentation besteht darin, nicht nur das Was und Wie, sondern auch das Warum festzuhalten. Das Warum hinter jeder Entscheidung ist möglicherweise wichtiger als das Was und Wie und hilft dabei, zukünftige Entscheidungsprozesse zu steuern. Der Architekt von morgen muss beispielsweise wichtige Informationen über die getroffenen Entscheidungen kennen:

- Gab es einen begrenzenden Faktor, der zu einer nicht optimalen Lösung geführt hat?
- Welche Anforderungen müsste eine Ersatzlösung erfüllen, um in Betracht gezogen zu werden?
- Welche Risiken und Abhilfemaßnahmen waren zu diesem Zeitpunkt bekannt?
- Was waren die Ziele und Nicht-Ziele und warum?
- Welchen Einfluss hat jede Komponente auf die anderen?

Indem Sie sicherstellen, dass Sie diese Aspekte einer Entscheidung dokumentieren, schaffen Sie ein Vermächtnis und keine veraltete Software.

So wichtig Aufzeichnungen über architektonische Entscheidungen auch sind, sie sind nicht die einzigen wichtigen Dokumente für Ihre Plattform. Andere Arten von Dokumentationen, die in diesem Kapitel und in diesem Buch erwähnt werden, sollten zusammengestellt und gepflegt werden, damit Sie den Überblick über die technischen Schulden behalten, die das System verursacht. Die Organisation der Dokumentation und deren Aktualisierung kann zwar mühsam sein und ist in der Tat mit Aufwand verbunden, aber die dadurch gewonnene Zeitersparnis zahlt sich im Laufe der Zeit aus. Eine durchsuchbare, gut organisierte Dokumentation ist der Schlüssel zu einem System, das sich langfristig bewährt.

Unser fiktives Unternehmen – ein letzter Blick

ACME Financial One ist ein Unternehmen, das für unsere Zwecke konzipiert wurde – um sich wie viele echte Unternehmen anzufühlen, die ihre technischen Stacks modernisieren. In unserem Beispiel haben sie es sowohl mit Altsystemen als auch mit neuen oder Greenfield-Systemen zu tun. Wie bei jedem echten Unternehmen würde dies zu einer anfänglichen Verdopplung der technischen Schulden führen. Um die Ingenieure während dieser Übergangsphase, in der zwei Systeme nebeneinander existieren, zu unterstützen, bietet eine gut konzipierte Plattform die erforderliche Flexibilität für einen reibungslosen Übergang zwischen den beiden Umgebungen.

ACME Financial One müsste dies mit einer möglichst schlanken Plattform unterstützen, die skalierbar ist und mit den Anforderungen der Nutzer mitwächst. Eine klare Dokumentation der Plattform und der Prozesse zu ihrer Nutzung wird die Entwickler bei der Umstellung und der Einführung der neuen Umgebung unterstützen.

Zusammenfassung

Wenn es eine Lehre gibt, die Sie aus diesem Kapitel über technische Schulden mitnehmen sollten, dann ist es die, dass das Stellen der richtigen Fragen zum richtigen Zeitpunkt Ihrem Team helfen kann, eine Plattform zu entwickeln, die auf Langlebigkeit ausgelegt ist. Die Plattform wird vielleicht nie fertig sein. Es wird immer Verbesserungen geben und Gewinne zu erzielen sein. Ein ausgefeilter Prozess für die Verwaltung der Plattform und die dazugehörige Dokumentation wird es dem Team jedoch ermöglichen, sie aufrechtzuerhalten und gleichzeitig die Gesundheit des Teams zu erhalten.

Wenn Sie sich mit technischen Schulden befassen, denken Sie an die Beispielindikatoren und Fragen, die wir in der Einleitung zu diesem Kapitel besprochen haben. Wenn Sie technische Schulden erkennen und die entsprechenden Kosten kennen, können Sie besser kommunizieren und Prioritäten setzen, um diese Punkte mit den Teams zu klären, die sich damit befassen müssen. Die Bewältigung technischer Schulden ist zwar an sich zeitaufwändig und kostspielig, aber sie hilft Ihnen, die Grundlage für eine Plattform zu schaffen, die langfristig Bestand hat und für zukünftige Veränderungen gerüstet ist.

Im nächsten und letzten Kapitel werden wir uns mit Veränderungen befassen und damit, wie Ihre Plattform diese Veränderungen als stabile Grundlage für Ihre IT-Organisation bereitstellen kann. Sie lernen das Konzept nachhaltiger und schlanker Architekturen kennen und erfahren, wie Sie Ihren Benutzern die Umsetzung dieser Ansätze ermöglichen können. Wir werden die Perspektive des „goldenen Pfades” als benutzerorientierten Begriff hinterfragen und uns die Frage stellen, ob wir als Plattformingenieure und -architekten nicht auch einen goldenen Pfad benötigen. Abschließend schließen wir das Buch mit einigen abschließenden Gedanken zu den nächsten Trendthemen.

Plattformprodukte für die Zukunft entwickeln

Der Unterschied zwischen einem Projekt und einem Produkt ist dessen Lebensdauer. Projekte haben ein Ende. Wenn sie ihre Frist überschreiten, verteilen Unternehmen Ressourcen, Geld und Zeit neu, was zu einer Verschlechterung des Systems führt. Eine Plattform als Produkt muss so aufgebaut sein, dass sie sich anpassen, weiterentwickeln und mit den sich im Laufe der Zeit ändernden Anforderungen wachsen kann. Plattformen sind auch mehr als nur eine technische Lösung. Sie erfordern ein Team, eine Denkweise und einen ganzen Organismus, um einem Unternehmen einen echten Mehrwert zu bieten.

Im letzten Kapitel möchten wir einige ermutigende Worte finden, die die Erkenntnisse und Einsichten des Buches zusammenfassen. Wir werden die Kontinuität von Veränderungen diskutieren und wie Ihre Plattform diese Kontinuität als stabile Grundlage für Ihre IT-Organisation bieten kann. Anschließend werden wir uns mit den Prinzipien nachhaltiger und schlanker Architekturen befassen und untersuchen, wie Sie Ihre Nutzer dazu ermutigen können, diese Ansätze zu verfolgen. Als Plattform-Ingenieur liegt es an Ihnen, diese Fähigkeiten zu erschließen und einen Mehrwert zu schaffen.

Wir schließen das Thema dieses Buches ab, indem wir die Perspektive des goldenen Pfades als benutzerorientierten Begriff hinterfragen und uns fragen, ob wir als Plattformingenieure und -architekten nicht auch einen goldenen Pfad benötigen.

Nach einigen abschließenden Gedanken in diesem Kapitel zu den nächsten Trendthemen lassen wir Sie gehen, damit Sie weiter an Ihrer Plattform arbeiten oder damit beginnen können. Vielleicht ist Ihnen aufgefallen, dass wir oft „Ihre Plattform” geschrieben haben – eine Plattform als Produkt beginnt mit Ihrer Denkweise. Sie sind für ihre Qualität und die Begeisterung verantwortlich, die sie bei einem Benutzer hervorruft. Sie definieren ihren Erfolg, und sie ist nichts, was man hinterher einfach wegwerfen kann. Deshalb ist es Ihre Plattform.

In unserem letzten Kapitel erfahren Sie mehr über:

- Kontinuierliche Veränderungen – lernen, zu altern und sich anzupassen
- Berücksichtigung nachhaltiger und schlanker Architekturen und Support
- Der goldene Weg für Veränderungen
- Ein Blick in die Zukunft

Kontinuierliche Veränderungen – lernen, zu altern und sich anzupassen

Die größte Herausforderung bei kontinuierlichen Veränderungen besteht darin, dass Sie als Plattformteam selbst eine vorausschauende Denkweise annehmen und verkörpern müssen, während Sie gleichzeitig Ihre Nutzer dazu anleiten und inspirieren, denselben Ansatz zu verfolgen. Wenn Sie dies nicht leisten können, werden Ihre Nutzer im besten Fall Ihre Lösung und Ihr Team dazu auffordern und zwingen, sich anzupassen. Im schlimmsten Fall werden sie Ihre Plattform verlassen und nach anderen Lösungen suchen. Es liegt also an Ihnen, eine solide, aber flexible Grundlage für Veränderungen und Wachstum zu schaffen.

Die Notwendigkeit von Veränderungen

Wir haben bereits darüber gesprochen, wie schnell sich die Technologie weiterentwickelt und dass alle 10 bis 15 Jahre wichtige technologische Meilensteine erreicht werden. Da Kubernetes gerade 10 Jahre alt geworden ist, können wir in den nächsten Jahren mit einer Revolution rechnen. Aber auch kleinere Veränderungen machen es notwendig, dass sich Plattformen an neue Anforderungen und Innovationen anpassen. Plattformarchitekten müssen einen Weg finden, um die Stabilität einer Plattform und die vom Markt vorgegebenen Innovationen in Einklang zu bringen. Diese Spannung zwischen diesen beiden Elementen kann überwältigend sein. Sie stellt die Konzepte Ihrer Plattform, die Entscheidungen Ihrer IT-Organisation und die Designentscheidungen Ihrer Benutzer in Frage.

Die MIT Sloan School of Management hat diese zugrunde liegende Struktur des kontinuierlichen Wandels definiert. Sie fand heraus, dass das, was oft wie chaotische Veränderungen aussieht, nur eine Fortsetzung der vier in der folgenden Abbildung dargestellten Zyklen ist. Es dauerte 15 Jahre Forschung, um zu verstehen, dass diese Veränderungen nicht linear verlaufen, sondern immer wieder von vorne beginnen. Wo beginnen wir in diesem Zyklus? Das hängt davon ab, denn wir befinden uns bereits darin, und tatsächlich hat jede Technologie, Methodik oder jedes Framework seinen eigenen Zyklus, der andere Zyklen leicht beeinflusst. Nehmen wir das Konzept des Platform Engineering als Beispiel. Wo es wirklich begann, ist schwer zu sagen: Hat es sich aus DevOps entwickelt? Ist der Begriff mit Tools wie Backstage entstanden? Hat jemand philosophisch über die IT-Welt nachgedacht und fand, dass es eine gute Idee wäre? Höchstwahrscheinlich war es ein bisschen von allem, was die selbsttreibende Kraft des Platform Engineering in Gang gesetzt hat. Es führte zu neuen Tools und architektonischen Perspektiven. DevRel-Experten (kurz für **Developer Relations**) diskutierten es mit anderen, demonstrierten, wie es funktioniert, was schließlich dazu führte, dass wir ein Buch darüber schrieben.

Abbildung 10.1: Die zugrunde liegende Struktur des kontinuierlichen Wandels nach MIT

Wenn Sie ein solches selbsttragendes Verhalten beobachten, das in allen vier Bereichen ausgewogen ist, wird es wahrscheinlich von allen übernommen werden, und Sie können als Vorreiter einen Schritt nach vorne machen.

Förderung einer Kultur des Wandels

Was lernen wir aus der Notwendigkeit des Wandels? Wir können Veränderungen nicht vermeiden; wenn Sie dies tun, vermeiden Sie Ihre eigene Zukunft und die Ihrer Plattform. Als Plattformteam sind Sie in einer idealen Position, um eine Kultur des Wandels zu fördern. Ja, noch ein weiteres Thema, das Sie sich vornehmen müssen und das nichts mit Technik zu tun hat, aber genau das macht die Rolle der Plattformingenieure so besonders. Sie befinden sich in einer idealen Position, da die Plattform und Ihre Arbeit die Verbindungen zwischen Ihrer IT-Landschaft, den Entwicklungsteams und dem Unternehmen darstellen.

Diese Verantwortung zu übernehmen und eine Vordenkerrolle einzunehmen, ist keine leichte Aufgabe. Um die Rolle von Plattformingenieuren zu übernehmen, die eine Vision für die Zukunft entwickeln und Teams durch Veränderungen führen, sind Strategien erforderlich, um eine Teamkultur aufzubauen, die Veränderungen begrüßt, einschließlich Kommunikation, Anreizen und Unterstützung durch die Führungskräfte. Der richtige kulturelle Ansatz hängt von Ihrem Team und den einzelnen Personen in Ihrem Unternehmen ab, was in einem Buch kaum behandelt werden kann. Wir empfehlen Ihnen, Umgebungen zu schaffen, die Nutzer zum Experimentieren einladen, wie z. B. Sandbox-Umgebungen oder Pilotprojekte. Aber Sie müssen noch mehr tun: Sie müssen solche Umgebungen auch für Ihr eigenes Team schaffen und Ihre Plattformingenieure dazu ermutigen, neue Technologien zu testen. Ihre Ergebnisse müssen dokumentiert und für das gesamte Team verfügbar sein, damit Sie Doppelarbeit vermeiden und die Reife der getesteten Technologien im Laufe der Zeit vergleichen können.

Daher müssen Sie eine Routine einführen, um Erfolge und Misserfolge gleichermaßen zu feiern. In der praktischen Wissenschaft sind Misserfolge ein wichtiger Teil der Forschung. Unternehmen wie SpaceX sprengen eine Rakete nach der anderen, betrachten dies aber dennoch als Erfolg, da sie ihrem Ziel jedes Mal ein Stück näher kommen. Sprengen Sie vielleicht nicht Ihr Rechenzentrum in die Luft, aber schaffen Sie zumindest eine sichere Umgebung, in der Sie Geld für Misserfolge investieren können. Unternehmen verschwenden den ganzen Tag Geld für scheinbar unsinnige Aktivitäten. Wenn Sie etwas tun können, das Ihr Team und Ihre technologische Bereitschaft wachsen lässt, ist es viel besser, dies zu tun.

Iterative Evolution und eine sich weiterentwickelnde Strategie

Mit einer sicheren Umgebung zum Testen neuer Technologien können Sie herausfinden, welche Sie in Ihre Plattform integrieren und vielleicht sogar eine alte ersetzen sollten. Das Gleichgewicht zwischen Stabilität und Innovation kann von Fall zu Fall unterschiedlich sein. Wir haben Plattformen gesehen, die immer mit einem großen Knall eine völlig neue Umgebung veröffentlichen und sehr professionell darin sind, die Arbeitslast automatisch auf die neue Plattform zu migrieren. Viele entscheiden sich jedoch dafür, neue Technologien und Funktionen Schritt für Schritt einzuführen. Durch die Verwendung von Feature-Toggles und die Gewährung des Zugriffs im Canary-Deployment-Stil für einen Benutzer können Sie Änderungen langsam, aber sicher einführen. Mit guter Beobachtbarkeit und Feedback-Schleifen haben Sie außerdem die Möglichkeit, die Qualität der neuen Funktionen zu verbessern und den Benutzer an der Entwicklung teilhaben zu lassen.

Entwicklung muss nicht mit großen Meilensteinen einhergehen; es ist auch wichtig, kontinuierlich Folgendes zu tun:

- Code umgestalten und dessen Qualität verbessern
- Berücksichtigen Sie Feature-Anfragen
- Über technische Schulden nachdenken und prüfen, ob sie inzwischen lösbar geworden sind
- Aktualisieren Sie Integrationen von Drittanbietern regelmäßig

In diesem Zusammenhang ist es auch wichtig, darüber nachzudenken, wie Implementierungen außer Kraft gesetzt werden können. Einige Tools haben vielleicht viel Aufmerksamkeit erfahren, sind aber aufgrund fehlender nachhaltiger Beiträge und Entwicklungen kurz nach ihrer Implementierung wieder verschwunden. Andere werden möglicherweise im Laufe der Zeit durch neue Hauptversionen ersetzt. Die Festlegung einer Auslaufstrategie ist daher ebenfalls Teil der Weiterentwicklung Ihrer Plattform. Dies erfordert eine klare Kommunikation der Auswirkungen und Zeitpläne gegenüber den Benutzern. Mit der Auslaufstrategie können Sie auch feststellen, wie modular und lose gekoppelt die Komponenten Ihrer Plattform tatsächlich sind und ob die Benutzer bestimmte Abhängigkeiten aufgebaut haben.

Die Einführung neuer Technologien ist ein Prozess und eine Frage der Einstellung. Als Plattformingenieure sind Sie dafür genau richtig aufgestellt. Schaffen Sie eine Umgebung für kontinuierliches Lernen, regelmäßige Feedback-Schleifen und Nachbesprechungen, um schnell zu lernen und eine erfolgreiche Weiterentwicklung zu beschleunigen.

Im nächsten Abschnitt werden wir kurz einen aktuellen Trend in der nachhaltigen Entwicklung hervorheben. Wir konzentrieren uns dabei auf die ökologische Nachhaltigkeit, die in den letzten Jahren zu einem starken Treiber geworden ist und durch das plötzliche Wachstum **der generativen künstlichen Intelligenz** (**GenAI**) noch mehr in den Fokus gerückt ist. Hier sind also einige Dinge, die wir als Plattformingenieure tun können, um unseren Beitrag zu einer nachhaltigen Zukunft zu leisten.

Berücksichtigung nachhaltiger und schlanker Architekturen und Ansätze

Die IT-Branche ist neben der Bau- und Luftfahrtindustrie zu einem der weltweit größten Verursacher von **Kohlendioxid** (**CO2**) geworden. Die besten Studien zu diesem Thema sind leider schon mehrere Jahre alt, aber wir können die Ergebnisse aus dem Jahr 2018 zusammenfassen:

- Die globale IT verbrauchte rund 2 % der Elektrizität
- Dies verursachte zwischen 1,5 % und 2,4 % der weltweiten CO2e (**e** steht für **Äquivalent** – nicht jedes entstehende Gas ist CO2).
- Dieser Bereich ist vergleichbar mit dem CO2e-Anteil Indonesiens (1,48 %), Kanadas (1,89 %) oder Deutschlands (2,17 %)
- Prognosen aus dem Jahr 2018 gingen davon aus, dass sich diese Zahlen bis 2025 verdoppeln würden; einige weniger vertrauenswürdige Quellen sagen sogar einen Anstieg der CO2e um 12 % bis 2025 voraus

Wir müssen nicht alles abschalten und wieder wie Höhlenmenschen leben, aber wir sollten uns zumindest der Auswirkungen unserer unbegrenzten Rechenressourcen auf die Umwelt bewusst werden. Rechenressourcen jeglicher Art verursachen CO2e-Emissionen während ihrer Herstellung, ihrer Nutzung durch den dafür benötigten Strom und wenn sie ausgemustert und vernichtet werden.

Das Beste, was wir tun können, ist daher Folgendes:

- **Reduzieren**: Bei der Reduzierung geht es darum, nachhaltig mit dem umzugehen, was wir konsumieren. In unserem täglichen Leben müssen wir keine Plastiktüten nehmen, aber was machen wir mit digitalen Ressourcen? Nun, es ist ganz einfach: Brauchen wir wirklich einen hochverfügbaren Webserver, der über fünf Kontinente verteilt ist und stündliche standortübergreifende Backups durchführt?
- **Wiederverwenden**: In der IT hat Wiederverwendung zwei Aspekte. Wenn ein Server ausgemustert wird, kann es sinnvoll sein, ihn nicht zu vernichten, sondern an einen Anbieter zu verkaufen, der sich auf den Betrieb von Legacy-Servern spezialisiert hat. Zweitens sollten wir den Server so lange wie möglich weiter nutzen. Auch das ist eine Form der Wiederverwendung. Kubernetes als Orchestrator macht dies extrem einfach und ermöglicht uns eine bewährte Lastverteilung im Falle eines Ausfalls.
- **Reparatur**: Die meisten von uns sind nicht in der Lage, Server zu reparieren. Oft fallen einzelne Komponenten wie Speichermodule oder Netzwerkgeräte aus.
- **Rightsizing**: Passen Sie die angeforderten Rechenkapazitäten vor Ort und in der Cloud an Ihre Arbeitslast an. Die Zeiten, in denen Server zu 80 % ausgelastet waren, sind vorbei. Wer seine Rechenressourcen nicht zu mindestens 90 % nutzt, schadet praktisch dem Planeten.
- **Ablehnen**: Arbeiten Sie nicht mit Anbietern zusammen, die sich nicht zur Erreichung von Nachhaltigkeitszielen verpflichten. Es liegt an Ihnen, dies als Kriterium in Ihre Lieferantenauswahlprozesse aufzunehmen.
- **Replatform**: Achten Sie darauf, ob ein Anbieter oder eine Plattform sich nicht für Nachhaltigkeitsziele engagiert oder diese nicht unterstützt.

Nun könnten Sie sagen, dass das Geschäftsmodell „Nachhaltigkeit” wirtschaftlich nicht besonders interessant ist. Vielleicht haben Sie sogar den Eindruck gewonnen, dass wir bereits zuvor Maßnahmen diskutiert haben, die wir ergreifen sollten. Die Reduzierung von Kosten geht oft mit der Optimierung Ihres CO2-Fußabdrucks einher. Daher wirkt sich die Optimierung Ihres Fußabdrucks auch positiv auf Ihre Kosten aus. Darüber hinaus werden immer mehr Vorschriften erlassen, um das Wachstum der globalen Erwärmung zu verlangsamen. Die Einhaltung dieser Vorschriften ist besser als die Zahlung von Geldstrafen.

Leichte Architekturen ermöglichen

Die Ermöglichung einer schlanken Architektur sollte ein vorrangiges Ziel für eine Plattform sein. Dies hat nicht nur Vorteile in Bezug auf die Nachhaltigkeit, sondern auch in Bezug auf die Robustheit und die Fähigkeit, Fehler zu tolerieren. Die Architektur einer Anwendung wird schlank, wenn sie keine harten Abhängigkeiten aufweist, weniger Komponenten verwendet, flexibel in der Bereitstellung ist (einschließlich Skalierbarkeit) und genau die richtigen Technologien verwendet. Ein gutes Beispiel hierfür ist Apache Kafka, das im Zusammenhang mit der Stream-Verarbeitung zu einer Art De-facto-Standard geworden ist. Ich habe jedoch gesehen, dass immer mehr Systeme es nur zum Transportieren von Protokollen und Ereignissen und zum Konsolidieren von Datenflüssen verwenden. Es gibt Dutzende leichterer und effizienterer Tools, die die gleichen Funktionen bieten, nur ohne die Skalierbarkeit, den Ressourcenbedarf und den Aufwand aufgrund der Komplexität. Dieses Muster ist sehr verbreitet. Wir bevorzugen eine Lösung, die unseren Anforderungen entspricht und noch viel mehr kann, auch wenn wir sie nicht benötigen, andere jedoch schon, sodass es die richtige Wahl sein muss.

Unabhängig davon, wofür wir uns entscheiden, müssen wir als Plattformteam, um leichtgewichtige Architekturen zu ermöglichen, technologische Optionen bereitstellen, um zwei bis drei bessere Antworten auf eine Anforderung zu geben, anstatt die falsche.

Unterstützung für die Benutzer bei der Anpassung

Wie unterstützen wir die Benutzer jetzt und ermöglichen ihnen, ihre Systeme in Zukunft zu optimieren?

Wir bieten ihnen Transparenz hinsichtlich ihrer Auswirkungen, zeigen ihnen die möglichen Plattformfunktionen zur Skalierung, zum Ausgleich und zum serverlosen Betrieb und stellen alternative leichtgewichtige Technologien bereit. Dies kann ein integrierter Bestandteil unserer **internen Entwicklungsplattform** (**IDP**) und Observability sein.

Um Transparenz hinsichtlich des CO2-Fußabdrucks zu schaffen, bieten Open-Source-Tools wie Kepler, Scaphandre sowie kommerzielle Lösungen Einblicke darin, welche Systemkomponente welchen CO2e-Ausstoß verursacht. Der folgende Screenshot aus Kepler zeigt ein einfaches Grafana-Dashboard mit dem Energieverbrauch pro Komponente.

Abbildung 10.2: Ein Kepler-Dashboard mit dem Energieverbrauch pro Komponente (Das Bild dient als visuelle Referenz; die Textinformationen sind nicht wesentlich.)

Derzeit befinden sich diese Tools noch in der Entwicklung und sind oft fehleranfällig und schwer zu handhaben, aber sie sind ein Anfang. Ob sie erfolgreich sein werden, hängt von der Fähigkeit ab, die Nutzer zu schulen. Wir müssen die Perspektive der Nutzer ändern, weg vom Erstellen von Software in einer Umgebung hin zu einer Plattform, die dies für sie übernimmt. Software muss auf einer Plattform entwickelt werden, um alle ihre Funktionen nativ nutzen zu können. Das klingt vielleicht so, als wollten wir Abhängigkeiten schaffen und damit unser Konzept der Modularität aufgeben. Aber genau darin liegt die Schwierigkeit eines Produkts: Man muss den richtigen Ansatz finden, um sich weiterzuentwickeln und neue Ansätze zu ermöglichen, während man gleichzeitig die Abwärtskompatibilität beibehält. Wenn Ihre neuen Funktionen oder der Ersatz einer alten Funktion einen Mehrwert bieten, werden sich die Benutzer darauf einstellen.

Wichtiger Hinweis

Der beste Weg, neue Ansätze anzupassen, ist Offenheit, die Transparenz und Aufklärung fördert.

Im nächsten Teil werden wir unsere Plattformreise mit dem Golden Path abschließen. Wir werden erneut aus einer anderen Perspektive einen Blick auf eines der gängigen Themen im Bereich Platform Engineering werfen und dabei den Golden Path als Feature für eine Plattform betrachten. Letztendlich schaffen wir als Platform Engineers einen Golden Path, um weitere Golden Paths zu schaffen.

Der Golden Path für Veränderungen

Der Begriff „Goldener Pfad” wurde in unserem Buch bereits mehrfach verwendet. Eine der ersten Verwendungen fand sich in einem Spotify-Blogbeitrag aus dem Jahr 2020 \[1\]. Golden Paths wurden geschaffen, um Ingenieure durch unterstützte Vorgehensweisen zu führen, mit denen sie ihre Aufgaben erledigen können (z. B. durch die Verwendung eines bestimmten Dienstes oder die Erstellung eines neuen Codes, der einen bestimmten Zweck erfüllt). Bei der Plattformentwicklung geht es darum, benutzerfreundliche Golden Paths bereitzustellen, um den Aufwand für einzelne Teams bei der Erstellung, Kompilierung, dem Testen, der Bereitstellung und dem Betrieb von Software zu reduzieren.

Werfen wir noch einmal einen Blick auf unser fiktives Unternehmen Financial One ACME! Zu Beginn des Buches haben wir mehrere Anwendungsfälle identifiziert, die wir als Self-Service-Golden Paths für Ingenieure bereitstellen können, die wir als Plattform-Engineering-Team unterstützen. Ein wichtiger Aspekt für die Bereitstellung eines guten Supports für jedes Produkt sind geeignete Feedback-Kanäle, die wir als Nächstes besprechen werden.

Bereitstellung von Feedback-Kanälen

Die Unterstützung unserer Plattform bedeutet, dass wir sicherstellen, dass alle über sie bereitgestellten Golden Paths jederzeit wie erwartet funktionieren. Sollte etwas nicht wie erwartet funktionieren, muss das Plattform-Engineering-Team sicherstellen, dass wir alles, was nicht funktioniert, so schnell wie möglich beheben, um negative Auswirkungen auf unsere Endbenutzer zu minimieren.

Im Idealfall erkennen wir automatisch, wenn etwas nicht wie erwartet funktioniert, und müssen nicht warten, bis sich unsere Nutzer beschweren. In [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3), im Abschnitt „Eine verfügbare, ausfallsichere und sichere Plattform“, haben wir erläutert, wie wichtig es ist, unsere Plattform und alle ihre Komponenten zu beobachten, um automatisch zu erkennen, wenn etwas nicht wie erwartet funktioniert. Wie bei jedem anderen Softwareprodukt können und müssen wir Observability nutzen, um sicherzustellen, dass unsere Plattform und alle ihre Komponenten ihre **Service-Level-Ziele** (**SLOs**) erfüllen. Wenn unsere Observability also anzeigt, dass etwas nicht verfügbar ist, langsamer geworden ist oder plötzlich Fehlermeldungen ausgibt, müssen wir Maßnahmen ergreifen, um den funktionsfähigen Zustand wiederherzustellen.

Eine weitere Möglichkeit, automatisiertes Feedback durch Observability zu erhalten, besteht darin, zu beobachten, wie viele Benutzer die Plattform aktiv nutzen und welchen Golden Paths sie folgen. Eine Auffrischung zu diesem Thema finden Sie unter „Erfolgs-KPIs und Optimierung“ in [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3). Wenn wir feststellen, dass unsere Benutzer plötzlich ihr Nutzungsverhalten ändern, ist dies ein Hinweis darauf, dass sich etwas geändert hat, das wir angehen müssen. Möglicherweise sind einige der goldenen Pfade unterbrochen (z. B. können Entwickler nicht auf Tools wie Backstage, Git oder ArgoCD zugreifen) oder einige Pfade sind veraltet (z. B. funktioniert eine Backstage-Vorlage nicht mehr, weil sie eine veraltete Konfiguration verwendet). Es könnte auch sein, dass sich die Anforderungen, Vorschriften oder bevorzugten Technologie-Stacks in einer Organisation geändert haben und dass unsere Plattform derzeit keine Golden Paths bereitstellt, die neue Anwendungsfälle widerspiegeln, die mit einer Änderung der Anforderungen einhergehen.

Um über einen aktuellen Satz von Golden Paths zu verfügen, müssen wir einen Feedback-Kanal bereitstellen, über den unsere Benutzer uns aktiv Feedback zu ihren neuen Anforderungen geben können. Das ist vergleichbar mit der Anforderung neuer Funktionen für ein beliebiges Softwareprodukt. Der beste Weg, um mehr über diese neuen Funktionsanforderungen zu erfahren, ist die Einrichtung eines direkten Kanals zu unseren Endbenutzern, bei denen es sich um unsere internen Ingenieure handelt. Dies kann über einen internen Chat erfolgen (z. B. über einen speziellen Slack-Kanal wie #goldenpath-suggestions), Sie könnten eine E-Mail-Verteilerliste einrichten (z. B. goldenpaths@yourcompany.com) oder Sie könnten einen Self-Service-Feedback-Golden Path in die Plattform selbst integrieren, über den die Nutzer Details dazu angeben können, was sie sich als Nächstes von der Plattform wünschen.

Feedback ist der ultimative Treiber für die kontinuierliche Verbesserung unserer Plattform mit neuen oder verbesserten Golden Paths. Für unsere Endnutzer bedeutet dies, dass sie kontinuierlich neue Funktionen von der Plattform erhalten, die ihnen den Alltag erleichtern, auch wenn sich ihre Anforderungen und Prozesse zur Bereitstellung von Software ändern.

Golden Paths sind die Funktionen unserer Plattformen

Wie in der Einleitung dieses letzten Kapitels erwähnt, ist eine Plattform ein Produkt und als solches niemals fertiggestellt, im Gegensatz zu einem Projekt, das eine endgültige Frist hat. Eine Plattform entwickelt sich weiter, da neue Anwendungsfälle hinzukommen, wenn neue Golden Paths oder bestehende Golden Paths aufgrund von Änderungen der Anforderungen aktualisiert werden müssen, um weiterhin zu funktionieren.

Da wir unsere Plattform wie ein Produkt aufbauen, können wir unsere Golden Paths auch als die Funktionen unseres Produkts betrachten. Diese Funktionen können unterschiedliche Formen annehmen, je nachdem, wie wir unsere Plattform aufbauen und welche Arten von Benutzeroberflächen wir unseren Endbenutzern zur Verfügung stellen. In [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3) im Abschnitt „Eine Referenzarchitektur für unsere Plattform“ haben wir die verschiedenen Formen der Benutzeroberfläche für eine Plattform diskutiert – **die Befehlszeilenschnittstelle** (**CLI**), eine REST-API, eine spezielle Konfigurationsdatei in einem Git-Repo oder eine ansprechende Entwicklerportal-Benutzeroberfläche, die alle verfügbaren Anwendungsfälle auflistet. Ein Beispiel für eine solche Benutzeroberfläche, die einen Self-Service-Zugriff auf eine Liste der verfügbaren Golden Paths (d. h. Funktionen) bietet, ist in der folgenden Abbildung dargestellt:

Abbildung 10.3: Ein Self-Service-Portal mit allen verfügbaren Golden Paths (d. h. Funktionen) (Das Bild dient als visuelle Referenz; die Textinformationen sind nicht wesentlich.)

Der vorstehende Screenshot stammt von einem Finanzinstitut (ähnlich unserem Financial One ACME), das eine Liste von Self-Service-Golden Paths für eine Vielzahl von Anwendungsfällen bereitstellt, die entweder vom Plattform-Engineering-Team identifiziert oder von den Endbenutzern im Laufe der Jahre angefordert wurden. Die meisten der im Screenshot sichtbaren Golden Paths konzentrieren sich auf die Anforderung von Cloud-Ressourcen (z. B. EC2 oder Azure Virtual Machines), die Anforderung von Cloud-Diensten (z. B. AWS **Relational Database Service** (**RDS**) oder Azure Load Balancer) oder die Erstellung neuer Elemente auf der Grundlage einer Vorlage (z. B. die Erstellung einer Chef-Richtlinie oder einer Azure DevOps-Pipeline).

Wenn der Benutzer auf einen dieser Golden Paths klickt, wird er in der Regel zur Eingabe von Informationen aufgefordert, wodurch dann eine Automatisierung ausgelöst wird, um die Anfrage zu erfüllen. Einige Golden Paths, die nicht automatisiert werden können oder noch nicht automatisiert sind, bieten möglicherweise nur eine Anleitung, in der erklärt wird, wie diese bestimmte Anfrage erfüllt werden kann.

Um sich noch einmal über die Auswirkungen dieser Golden Paths im realen Leben zu informieren, lesen Sie bitte noch einmal [Kapitel 8](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/8), in dem es um Kostenoptimierung geht. Im Abschnitt „Nur das anfordern, was Sie benötigen” haben wir erklärt, was hinter der Anforderung eines Azure Virtual Machine Golden Path geschieht.

Das vorangegangene Beispiel gibt bereits einen guten Überblick darüber, wie sich eine Plattform entwickeln kann. Aber wir beginnen nicht mit so vielen Golden Paths (d. h. Funktionen). Wir fangen klein an und müssen dann bereit sein, zu skalieren. Aber wie machen wir das?

Fangen Sie klein an, rechnen Sie mit Wachstum und vermeiden Sie Engpässe

In [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2), im Abschnitt über **Thinnest Viable Platforms** (**TVPs**), haben wir erläutert, wie wir mit einer kleinen Auswahl von Anwendungsfällen beginnen müssen, von denen wir glauben, dass sie eine Wirkung erzielen werden. Von dort aus nutzen wir Feedback, um mehr über zusätzliche Anwendungsfälle zu erfahren, die wir zum Ausbau einer Plattform verwenden.

Betrachten wir einmal Financial One ACME. In den ersten Kapiteln dieses Buches haben wir mehrere Self-Service-Anwendungsfälle diskutiert, die das Leben von Entwicklern, DevOps, ITOps oder Testern bei Financial One ACME verbessern würden. Dazu gehörten Anwendungsfälle wie der Self-Service-Zugriff auf Produktionsprotokolle zur Fehlerbehebung, die Bereitstellung einer konformen Umgebung, die Durchführung von Leistungs- und Ausfallsicherheitstests sowie die Einführung einer neuen Anwendung. Sobald diese Anwendungsfälle implementiert sind und sich als Erleichterung für die Arbeit dieser Ingenieure bewährt haben, ist garantiert, dass weitere Golden Path Requests hinzukommen werden. Wir müssen also mit einem Wachstum rechnen, das sich aus der Entwicklung eines erfolgreichen Produkts ergibt.

Das Problem bei einer wachsenden Anzahl von Anwendungsfällen, die unterstützt werden müssen, ist, dass dies einen höheren Aufwand für Tests und Wartung erfordert, wodurch weniger Zeit für die Hinzufügung neuer Anwendungsfälle oder Kernfunktionen zu einer Plattform bleibt. Wir laufen Gefahr, zu einem Engpass zu werden, da wir uns bemühen, die Plattform und ihre Funktionen mit allen Anforderungen unserer Benutzer auf dem neuesten Stand zu halten. Eine Lösung für dieses Problem besteht darin, einen Golden Path zum Erstellen von Golden Paths bereitzustellen, wodurch die Erweiterung der Plattform vereinfacht wird – nicht nur durch Experten, sondern durch alle!

Goldene Pfade zum Erstellen goldener Pfade

Im gesamten Buch haben wir darüber gesprochen, Golden Paths bereitzustellen, um die kognitive Belastung der Ingenieure bei der Erledigung ihrer Arbeit zu reduzieren. Die Frage ist nun, ob wir bei der Gestaltung unserer Plattform auch Golden Paths bereitstellen können, die es dem Plattform-Engineering-Team ermöglichen, die Plattform effizienter um neue Funktionen, Fähigkeiten und Anwendungsfälle zu erweitern. Können wir einen Goldenen Pfad erstellen, der es dem Plattform-Engineering-Team ermöglicht, weitere Goldene Pfade zu erstellen? Und könnte dieser Goldene Pfad dann auch von unseren Endnutzern (den Engineering-Teams unserer Organisation) verwendet werden, um ihre neuen Anforderungen zu implementieren, ohne dass das Plattform-Engineering-Team als neuer Goldener Pfad benötigt wird? Das erinnert fast an den Science-Fiction-Film „Inception“ aus dem Jahr 2010 mit Leonardo DiCaprio in der Hauptrolle.

Die gute Nachricht ist, dass wir Hollywood nicht brauchen, um so etwas zu erreichen. In [Kapitel 5](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/5), im Abschnitt „Bereitstellen von Vorlagen als Golden Paths für einen leichteren Einstieg“, haben wir die Vorlagenfunktion in Backstage besprochen. Vorlagen in Backstage sind eine Möglichkeit, Golden Paths zu definieren. Die Vorlagen werden in der Regel vom Plattform-Engineering-Team erstellt und gepflegt, da ihre Erstellung einiges an Fachwissen erfordert. Der folgende Ausschnitt zeigt einen Auszug aus einer solchen Vorlagendefinition:

apiVersion: scaffolder.backstage.io/v1beta3

kind: Template

metadata:

&nbsp; name: self-service-app-onboarding

&nbsp; title: Onboarding einer neuen App bei Financial One ACME

&nbsp; description: Golden Path zum Onboarding einer neuen App

Spezifikation:

&nbsp; Eigentümer: financialoneacme/platform-engineering

&nbsp; Typ: Dienst

&nbsp; # Bei Verwendung dieses goldenen Pfades erforderliche Eingabeparameter

&nbsp; Parameter:

&nbsp;   - title: Welche Programmiersprache

&nbsp;     Eigenschaften:

&nbsp;       Sprache:

&nbsp;         title: Programmiersprache

&nbsp;         Typ: Zeichenfolge

&nbsp;         Beschreibung: Welche Sprache möchten Sie verwenden?

&nbsp;       Eigentümer:

&nbsp;         title: Eigentümer

&nbsp;         Typ: Zeichenfolge

&nbsp;         Beschreibung: Welches Team ist Eigentümer dieser neuen App?

&nbsp;   - Titel: Wählen Sie einen Zielort für Git

&nbsp;     ...

&nbsp; # Schritte bei Ausführung von Golden Path

&nbsp; Schritte:

&nbsp;   - id: fetch-base

&nbsp;     name: Basis abrufen

&nbsp;     Aktion: fetch:template

&nbsp;     Eingabe:

&nbsp;       URL: ./template

&nbsp;       Werte:

&nbsp;         Sprache: ${{ parameters.language }}

&nbsp;         Eigentümer: ${{ parameters.owner }}

&nbsp;   - id: veröffentlichen

&nbsp;     name: Veröffentlichen

&nbsp;     Aktion: veröffentlichen:github

&nbsp;   - id: registrieren

&nbsp;     name: Registrieren

&nbsp;     Aktion: Katalog:Registrieren

&nbsp; # Ausgabe, die dem Endbenutzer angezeigt wird

&nbsp; Ausgabe:

&nbsp;   links:

&nbsp;     - Titel: Repository

&nbsp;       URL: ${{ steps\['publish'\].output.remoteUrl }}

KopierenErklären

Ein vollständiges Beispiel finden Sie in der Dokumentation **zur Backstage-Vorlage** \[2\]. Das vorstehende Beispiel definiert einen Golden Path, über den ein Benutzer eine Programmiersprache auswählen, das Team definieren kann, das diese neue Komponente erstellt, sowie ein Ziel-Git-Repository, in dem das neue Projekt für eine neue App erstellt werden soll. Nehmen wir an, ein Benutzer wählt **Java** als bevorzugte Programmiersprache aus. Der Schritt „fetch-base“ ruft dann eine Reihe von Dateien ab, die in einem Git-Repository für die Verwendung festgelegt wurden, wenn jemand Java auswählt. Der Schritt „publishing“ veröffentlicht dann das neue Git-Repository basierend auf der ausgewählten Sprache. Hinter den Kulissen geschieht noch ein bisschen mehr, aber im Wesentlichen geht es bei der Erstellung einer Golden-Path-Vorlage genau darum.

Was bei diesem Beispiel deutlich wird, ist, dass die Erstellung von Golden Paths eigentlich gar nicht so schwer ist. Sicher, es gibt einige Besonderheiten, die wir in diesem kurzen Abschnitt des Buches nicht behandeln können, aber es zeigt, dass es bereits Tools wie Backstage gibt, mit denen die Erstellung oder Aktualisierung von Golden-Path-Vorlagen sehr einfach macht. Dies ermöglicht es den Plattform-Engineering-Teams auch, andere Teams bei der Erstellung und Aktualisierung ihrer eigenen Golden Paths zu unterstützen, wodurch die Wahrscheinlichkeit verringert wird, dass das Kern-Plattform-Engineering-Team zu einem Engpass wird.

Wir verwenden Backstage als Beispiel, aber es gibt auch andere Tools, die eine ähnliche Flexibilität bieten. Sie sollten sich mit den im Open-Source-Bereich verfügbaren Tools vertraut machen und sich auch kommerzielle Angebote ansehen. Ein weiteres Open-Source-Projekt, das Sie sich ansehen sollten, ist **Kratix** – das Open-Source-Framework für die Plattformentwicklung \[3\]. Kratix bietet ein Framework für den Aufbau komponierbarer **interner Entwicklungsplattformen** (**IDPs**). Es verfolgt einen interessanten Ansatz, bei dem sogenannte Promises verwendet werden, die im Wesentlichen mit Golden Paths vergleichbar sind. Kratix ermutigt alle Benutzer, ihre eigenen Promises zu erstellen und zur Plattform beizutragen, sodass jeder Benutzer der Plattform die von anderen Mitgliedern der Organisation erstellten Golden Paths nutzen kann.

Nachdem wir nun erläutert haben, dass Golden Paths nicht nur den Anfang Ihrer Plattform darstellen, sondern sich auch weiterentwickeln, und wie Sie Golden Paths bereitstellen können, um neue Golden Paths zu erstellen und so das zukünftige Wachstum Ihrer Plattform sicherzustellen, ist es an der Zeit, einen Blick auf einige andere Zukunftstrends zu werfen, die wir bei der Entwicklung zukunftsfähiger Plattformprodukte berücksichtigen müssen!

Ein Blick in die Zukunft

Die nächsten Zeilen sind vielleicht die gefährlichsten in diesem Buch. Sie könnten völliger Unsinn sein, nur ein Traum oder vielleicht die Zukunft unserer täglichen Arbeit. Eine Plattform aufzubauen bedeutet, sie auf dem neuesten Stand zu halten, wenn sich die Dinge um uns herum ändern. Dazu gehört, den Markt genau zu beobachten, zu verfolgen, was passiert, und zu bewerten, ob einer der Trends wahrscheinlich von Dauer sein wird. Am wichtigsten ist natürlich die Beantwortung der Frage, ob diese neuen Trends für die Nutzer und das Unternehmen Ihrer Plattform von Vorteil sind.

Der Ersatz von Hypervisoren

Das erste Thema, über das es sich nachzudenken lohnt, ist der mögliche Ersatz von Hypervisoren durch Kubernetes. Wir haben dieses Thema bereits zuvor angeschnitten und dabei insbesondere die Geschichte und die Gründe für die weiterhin verwendeten Hypervisoren beleuchtet. Was muss geschehen, damit dies zu einem ernstzunehmenden Ansatz wird, der die **Chief Information Security Officers** (**CISO**) beruhigt? Folgende Fragen müssen geklärt werden:

- Containerisolierung und Verschlüsselung
- Netzwerkisolierung und -verschlüsselung
- Speicherisolierung und -verschlüsselung

Kurz gesagt müssen wir alles voneinander isolieren und verschlüsseln, während wir den Container-Orchestrator vollständig flexibel halten, um alle erforderlichen Funktionen für die Plattform bereitzustellen. Aber vielleicht denken wir dabei zu klassisch und altmodisch. Natürlich können wir Container so weit absichern, dass sie zu einer vollständig versiegelten Black Box werden. Für einige Anwendungen können wir WebAssembly als sehr sicheres Kompilierungsziel in Betracht ziehen. Und wenn das nicht ausreicht, können wir noch vertrauliches Computing hinzufügen oder einfach darauf warten, dass die Open-Source-Community bessere Lösungen findet. Es ist, als würde niemand jemals aus dem Kontext einer VM ausbrechen \[4\]. Auch die Isolierung von Netzwerken ist kein Allheilmittel. Technologien wie **Extended Berkeley Packet Filter** (**eBPF**) werden verwendet, um „den Kernel dynamisch für effizientes Networking, Beobachtbarkeit, Tracing und Sicherheit zu programmieren“. eBPF verbessert die sichere Netzwerkkommunikation, indem es die Ausführung benutzerdefinierter, sandboxed Programme im Kernel-Bereich ermöglicht, ohne den Kernel-Code zu verändern. Diese Fähigkeit ermöglicht eine fein abgestimmte Kontrolle über die Verarbeitung, Filterung und Überwachung von Netzwerkpaketen, was dazu beiträgt, Sicherheitsrichtlinien durchzusetzen und böswillige Aktivitäten in Echtzeit zu erkennen. Das letzte Problem wäre die Speicherung, aber in diesem Bereich bauen wir auf softwaredefiniertem Speicher auf. Insgesamt ist es machbar, VMs durch Kubernetes zu ersetzen. Sicherlich haben wir einige Details ausgelassen, aber in einem Cloud-nativen Bereich gibt es für jedes Problem eine Lösung.

KI für Plattformen

Kein anderes Thema ist zum Zeitpunkt des Verfassens dieses Artikels so allgegenwärtig wie KI, genauer gesagt GenAI. Jede Konferenz, jede Medienquelle und jedes Fachmagazin berichtet über GenAI. Auch die Open-Source-Community blieb nicht untätig und entwickelte als Reaktion darauf K8sGPT. K8sGPT ist ein Tool zum Scannen Ihrer Kubernetes-Cluster, das Probleme in einfachem Englisch diagnostiziert und triagiert. Das ist die Gegenwart, aber was wir in Zukunft sehen werden, ist interessant. Die tatsächlichen Probleme der richtigen Dimensionierung, der Skalierungsanpassung, der Konfiguration der Lastverteilung und aller anderen operativen Aufgaben sind perfekte Themen für KI. Wir haben standardisierte Schemata und Kommunikationsmuster. Methoden zur Ermittlung des am besten geeigneten Knotens oder der richtigen Konfiguration eines Pods in Bezug auf seinen Ressourcenverbrauch sollten daher einfach sein. Es ist überraschend, dass es derzeit keine marktfähige Lösung gibt. Aber vielleicht liegt das Problem darin, dass es zu einfach ist, KI einzusetzen. Umgekehrt sehen wir viele verschiedene Einflüsse auf die IT aufgrund demografischer Veränderungen, und es gibt viele Qualifikations slücken und Kostendruck bei Unternehmen und auf dem Markt, was den Einsatz von KI im operativen Bereich beschleunigen könnte.

OCI-Registry als Speicher und RegistryOps

Wir ändern ständig die Art und Weise, wie wir unsere Abläufe gestalten. Seit dem Aufkommen von DevOps „opsifizieren“ wir alles – ML, Sicherheit, Kostenmanagement und so weiter. Hinzu kommt RegistryOps. Die Idee dabei ist, alle für die Bereitstellung erforderlichen Artefakte an einem Ort zu speichern, anstatt sie in verschiedenen anderen Speicherlösungen zu verteilen. Zu diesem Zweck hat die Open Container Initiative mehrere Standards für Registries definiert, die eingehalten werden müssen, darunter die Distributionsspezifikation, die Laufzeitspezifikation und die Bildspezifikation. In [Kapitel 5](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/5), „Die Bedeutung von Container- und Artefakt-Registern als Einstiegspunkte“, haben wir dies ausführlich besprochen. Dadurch wird das Register zu einer einzigen Quelle der Wahrheit und zu einem einzigen Fehlerpunkt. Das Projekt „**OCI Registry as Storage**“ (**ORAS**) baut auf diesen Standards auf. Es ermöglicht die Verwendung von Container-Images, den Aufbau von Beziehungen zwischen Artefakten und das Anhängen beispielsweise einer **Software-Stückliste** (**SBOM**) an einen Container. Natürlich wird die SBOM in derselben Registry gespeichert. GitOps-Tools verwenden die Registry dann als Speicher für den gewünschten Zustand und übernehmen die Bereitstellung für den Cluster. Da die meisten Registries mit diesem Ansatz kompatibel sind, lässt sich ORAS einfach skalieren, bietet eine sehr detaillierte Berechtigungsspezifikation und verbessert die Sicherheit der Lieferkette.

Es gibt immer mehr Angriffe auf die Lieferkette, die zu einer relevanten Angriffsfläche wird. Mit einer Registry, die zwischen CI und CD liegt, richten Sie einen gewünschten Haltepunkt für diese Ketten ein. Das verlangsamt den Prozess des Scannens von Artefakten auf Schwachstellen und stellt sicher, dass sie von den richtigen Personen signiert werden. Letztendlich ist RegistryOps immer noch GitOps, aber es verwendet eine Registry und nicht Git.

Containerisierte Pipelines als Code

Ein relativ neues Konzept oder eine neue Idee ist es, eine CI/CD-Pipeline in einem Container zu definieren, sodass Sie diese lokal sowie in einem Tool wie GitHub Actions oder Jenkins ausführen können. Auf diese Weise können Sie die automatisierten Schritte harmonisieren und sicherstellen, dass sie überall ausgeführt werden können. Die Idee wurde durch das Open-Source-Tool Dagger eingeführt, das vom ehemaligen CTO und Gründer von Docker, Solomon Hykes, initiiert wurde. Darüber hinaus codieren Sie die Pipeline praktisch, wodurch sie unabhängig von der eigenen Logik der CI/CD-Systeme ist. Der folgende Code ist nur eine Funktion aus einer Dagger-Datei und führt den Build einer Anwendung aus.

func (m \*HelloDagger) Build(source \*dagger.Directory) \*dagger.Container {

&nbsp;   build := m.BuildEnv(source).

&nbsp;       WithExec(\[\]string{"npm", "run", "build"}).

&nbsp;       Directory("./dist")

&nbsp;   return dag.Container().From("nginx:1.25-alpine").

&nbsp;       MitVerzeichnis("/usr/share/nginx/html", build).

&nbsp;       MitExposedPort(80)

}

KopierenErklären

Dieser Ansatz kann für Unternehmen, die über eine fragmentierte Landschaft von Tools und Prozessen verfügen und dazu neigen, ihre Landschaft alle zwei Jahre auf etwas anderes umzustellen, eine entscheidende Veränderung bedeuten.

Einige Kritiker meinen jedoch, dass es möglicherweise nicht notwendig ist, CI/CD-Komponenten lokal auszuführen, da ein wichtiger Trend darin besteht, alles remote zu übertragen, um die Ressourcennutzung zu optimieren. Plattformen wie GitHub Actions bieten wiederverwendbare Schritte, die nur mit Werten gefüllt werden müssen. Mal sehen, ob wir in zukünftigen Pipelines darauf zurückgreifen werden.

Plattformen – eine bessere Zukunft mit ihnen?

Mit Plattformen, einer produktorientierten Denkweise und einem starken Plattform-Engineering-Team können wir eine Grundlage und eine Integrationsschicht bereitstellen, um die Softwareentwicklung und -ausführung zu harmonisieren und zu optimieren. Unsere Herausforderung besteht darin, das Gleichgewicht zwischen der Stabilität und Sicherheit der von uns bereitgestellten Umgebungen und einem innovativen Antrieb zu finden, der unsere Plattformen ständig weiterentwickelt und sicherstellt, dass sie zwar altern, aber nicht ausgemustert werden.

Aber es liegt an uns. Wie bei vielen Dingen im Leben gilt: Wenn wir nicht daran glauben und es nicht verwirklichen, wird es niemand anderes tun. Der Plattformansatz ist nicht der einzige Weg, aber er hat eine stark wachsende Gruppe von Experten, motivierten Mitwirkenden und eine lebendige Community. Bei jeder größeren Veranstaltung können wir beobachten, wie Endnutzer ihre Erfolgsgeschichten über die Einführung von Plattformen und Plattformteams erzählen und wie dies für ihre Organisationen zu einem Game Changer geworden ist.

Mit Blick auf die Zukunft stehen Plattformen an der Spitze unserer technologischen Zukunft und versprechen, Komplexitäten zu vereinfachen und Innovationen zu fördern. Durch die Konzentration auf die Plattformentwicklung können Architekten Systeme entwickeln, die nicht nur robust sind, sondern sich auch an die sich schnell verändernde Technologielandschaft anpassen lassen. Die Integration von Plattformen geht mit kontinuierlichem Lernen und Verbessern einher, wobei kleine, durchdachte Iterationen zu erheblichen Verbesserungen führen können. Wir müssen eine Kultur der Zusammenarbeit und des gemeinsamen Wachstums fördern. Die Herausforderungen sind zwar zahlreich, aber die potenziellen Vorteile gut entwickelter Plattform- s sind unbestreitbar und bieten, wie bereits mehrfach gezeigt wurde, eine solide Grundlage für den Aufbau widerstandsfähiger und skalierbarer Systeme. Durch sorgfältige Planung und Ausführung kann das Plattform-Engineering neue Möglichkeiten für effizientere und effektivere Systeme eröffnen. Mit Engagement und Fokus auf unsere Prinzipien und Ziele können wir rein wünschenswerte Umgebungen schaffen, die zukunftssicher und bereit für Veränderungen sind.

Zusammenfassung

In diesem Kapitel diskutieren wir die Notwendigkeit von Veränderungen und wie wir als Plattformingenieure diese aktiv annehmen müssen. Durch iterative evolutionäre Schritte begleiten wir eine Plattform durch ihren gesamten Lebenszyklus, nicht indem wir sie demontieren, sondern indem wir sie weiterentwickeln. Wir halten sie zukunftssicher und bieten innovative Lösungen. Wir haben auch die Bedeutung nachhaltiger Ansätze und Architekturen hervorgehoben und betont, dass es für Plattformen einfach ist, Optimierungen zentral für das gesamte Unternehmen bereitzustellen.

Wir haben den Golden Path, seine Feedbackschleifen und eine andere Perspektive darauf als Feature und nicht als rein meinungsgebundene Einrichtung diskutiert. Wir haben das Wachstum Ihrer Plattform und die Notwendigkeit betont, Golden Paths zu definieren, um ihr Wachstum mit neuen Fähigkeiten zu unterstützen. Wir haben die Diskussion mit der Untersuchung der Verwendung eines bestehenden Golden Paths zur Schaffung neuer Golden Paths abgeschlossen.

Abschließend haben wir aktuelle Trends und Themen hervorgehoben, die die nächsten Jahre unseres Cloud-nativen Universums prägen könnten – oder auch nicht. Wer weiß schon, wann der nächste Big Bang stattfinden wird und wohin er uns in Zukunft führen wird?

Dieses Buch hat Ihnen viele verschiedene Perspektiven, Werkzeuge und Ansätze für die Gestaltung Ihrer eigenen Plattformarchitektur vermittelt. Als Ingenieur oder Entscheidungsträger haben Sie die tatsächliche Komplexität des Aufbaus von Plattformen kennengelernt, die weit über die reine Technologie hinausgeht, und Sie haben den Wert und die Vorteile für Benutzer und Organisationen kennengelernt. Als Plattformarchitekt unterstützen Sie diese Schritte und Überlegungen auf Ihrem Weg und helfen Ihnen dabei, ein sich weiterentwickelndes Produkt zu schaffen und einen positiven Einfluss auf diejenigen auszuüben, die es implementieren und nutzen.

Wie Sie das Gelernte künftig nutzen, liegt ganz bei Ihnen. Wenn Sie gerade dabei sind, Ihre Referenz- und Zielarchitektur zu definieren, greifen Sie auf die Vorlagen von **Miro** oder **draw.io** zurück \[5\]. Wir empfehlen Ihnen außerdem, sich verschiedenen Plattform-Engineering-Communities anzuschließen, beispielsweise der CNCF Platforms Working Group \[6\], die regelmäßig Wissensaustausch-Sessions veranstaltet, und anderen Nutzern, die Einblicke in ihre Ansätze geben.

Wir wünschen Ihnen alles Gute für Ihre Reise und viel Erfolg mit Ihrer Plattform.

Weiterführende Literatur

- \[1\] Spotify-Blog zu Golden Paths: https://engineering.atspotify.com/2020/08/how-we-use-golden-paths-to-solve-fragmentation-in-our-software-ecosystem/
- \[2\] Backstage-Vorlagendokumentation: [https://backstage.io/docs/features/software-templates/writing-templates](https://backstage.io/docs/features/software-templates/writing-templates%0A)
- \[3\] Kratix: https://www.kratix.io/
- \[4\] Sicherheitsvorfälle mit virtuellen Maschinen, bei denen Forscher und zwielichtige Personen aus dem VM-Kontext ausgebrochen sind:
    - VENOM-Sicherheitslücke (2015): Die VENOM-Sicherheitslücke (**Virtualized Environment Neglected Operations Manipulation**) wurde im Floppy-Disk-Controller der QEMU-VM entdeckt. Sie ermöglichte es einem Angreifer, aus der Gast-VM auszubrechen und beliebigen Code auf dem Host-Rechner auszuführen: [https://en.wikipedia.org/wiki/VENOM](https://en.wikipedia.org/wiki/VENOM%0A)
    - CVE-2017-5715 (Spectre) und CVE-2017-5754 (Meltdown): Diese Sicherheitslücken nutzten Schwachstellen im CPU-Design aus und betrafen fast alle modernen Prozessoren. Sie ermöglichten es Angreifern, sensible Daten über VM-Grenzen hinweg zu lesen, indem sie spekulative Ausführung ausnutzten: [https://meltdownattack.com/](https://meltdownattack.com/%0A)
    - CVE-2019-11135: Diese als ZombieLoad bekannte Sicherheitslücke in Intel-CPUs kann es einem Angreifer ermöglichen, Daten aus anderen Prozessen oder VMs zu stehlen, die auf derselben physischen CPU laufen: [https://nvd.nist.gov/vuln/detail/CVE-2019-11135](https://nvd.nist.gov/vuln/detail/CVE-2019-11135%0A)
    - Blue Pill (2006): Joanna Rutkowska demonstrierte den Blue Pill-Angriff, der zeigte, wie ein Hypervisor-basiertes Rootkit im laufenden Betrieb installiert werden kann, wodurch im Wesentlichen ein nicht nachweisbarer VM-Escape entsteht: [https://en.wikipedia.org/wiki/Blue_Pill_(software)](https://en.wikipedia.org/wiki/Blue_Pill_%28software%29%0A)
    - Cloudburst (2009): Hierbei handelte es sich um eine VMware-Sicherheitslücke, die die Ausführung von Code auf dem Host-Rechner aus einer Gast-VM heraus ermöglichte: [https://nvd.nist.gov/vuln/detail/CVE-2009-1244](https://nvd.nist.gov/vuln/detail/CVE-2009-1244%0A)
    - Und einige weitere Sicherheitsvorfälle mit VMs: [https://en.wikipedia.org/wiki/Virtual_machine_escape](https://en.wikipedia.org/wiki/Virtual_machine_escape%0A)
- \[5\] Erstellen Sie Ihren eigenen Architektur-Workshop:
    - Miro-Vorlage: [https://miro.com/miroverse/platform-architecture-workshop](https://miro.com/miroverse/platform-architecture-workshop%0A)
    - Draw.io-Vorlage: [https://github.com/PacktPublishing/Platform-Engineering-for-Architects/tree/main/Chapter%2002](https://github.com/PacktPublishing/Platform-Engineering-for-Architects/tree/main/Chapter%2002%0A)
- \[6\] CNCF-Arbeitsgruppe „Plattformen”: [https://tag-app-delivery.cncf.io/wgs/platforms/](https://tag-app-delivery.cncf.io/wgs/platforms/%0A)

**DevOps-Release-Management**

Joel Kruger

ISBN: 978-1-83546-185-3

- Entdecken Sie die Bedeutung und den Aufbau des SDLC
- Verstehen Sie die Geschichte des Release-Managements und die Funktionsweise verschiedener Modelle
- Erfassen Sie das DevOps-Release-Management und grundlegende Strategien zu dessen Umsetzung
- Erstellen Sie optimierte CI/CD-Pipelines, die eine frühzeitige Fehlererkennung ermöglichen
- Implementieren Sie den Shift-Left-Ansatz, um die Wertlieferung an Kunden in Rekordgeschwindigkeit zu verbessern
- Fördern Sie eine Kultur der funktionsübergreifenden Zusammenarbeit in Ihrem Team
- Machen Sie das DevOps-Release-Management pragmatisch und zugänglich
- Überwinden Sie häufige Fallstricke im DevOps-Release-Management