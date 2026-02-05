# Kostenmanagement und Best Practices

Die Cloud-Migration hatte in den letzten Jahren für viele IT-Organisationen höchste Priorität und ist auch für die kommenden Jahre weiterhin eine strategisch relevante Ausrichtung. Der Betrieb und Besitz eines eigenen Rechenzentrums ist ebenfalls nach wie vor ein wertvoller Ansatz; das Design und die Kosten für die eigenen Rechenzentrumskapazitäten sind in der Regel besser durchdacht als bei der Cloud. In diesem Kapitel werden wir uns näher damit befassen und über die Notwendigkeit des Cloud-Kostenmanagements und der Optimierung nachdenken.

Sie erfahren mehr über Tagging-Strategien und warum sie eine sinnvolle Ressource sind, um Transparenz und Übersichtlichkeit bei Ihren Cloud-Ausgaben zu gewinnen. Wir werden auch untersuchen, wie man sie definiert, welche Best Practices es gibt und welche praktischen Ansätze es gibt, um sicherzustellen, dass sie gut eingerichtet sind. Auf dieser Grundlage werden wir uns den vier Säulen der Kostenoptimierung zuwenden: Prozesse, Preisgestaltung, Nutzung und Design.

Zum Abschluss dieses Kapitels geben wir Ihnen praktische Tipps, wie Sie Ihre Plattform optimieren und Ihre Kosten langfristig senken können, sodass Sie Ihren Nutzern kostensparende Vorteile bieten können.

Insgesamt konzentrieren wir uns auf ein effektives Kostenmanagement und darauf, wie Sie als Plattformingenieur dies umsetzen können. Folgendes können Sie lernen:

- Die Kostenlandschaft verstehen – ist die Cloud der richtige Weg?
- Implementierung einer Tagging-Strategie, um versteckte Kosten aufzudecken
- Betrachtung von Strategien zur Kostenoptimierung
- Autoscaling, Cold Storage und andere Tricks zur Kostenoptimierung

# Die Kostenlandschaft verstehen – ist die Cloud der richtige Weg?

Das Kostenmanagement im Bereich Platform Engineering beginnt mit einem guten Verständnis der Kostentreiber innerhalb Ihrer Infrastruktur und der Frage, wie bestimmte Plattformkomponenten diese beeinflussen können. Kostentreiber sind auch Elemente, die sich direkt auf die Gesamtkosten Ihres Plattformbetriebs auswirken. Wenn Sie diese verstehen und später identifizieren, können Sie fundierte Entscheidungen treffen, um kostenorientierte und optimierte Plattformen bereitzustellen.

## Cloud oder keine Cloud – das ist hier die Frage

In den letzten Jahren gab es fast keinen Weg an einer Cloud-Einführungsstrategie vorbei. In diesen Jahren stieß diese Entwicklung auf Widerstand von Unternehmen, die erfolgreich von der Cloud abgewandert sind und behaupten, dass ihre lokale Infrastruktur billiger, besser und alles ist, was sie brauchen. Dies wird als Repatriierung bezeichnet. Die Zahl derjenigen, die dies tun, ist nicht ganz klar und hängt stark davon ab, was darunter verstanden wird. Bekannt wurde dies durch HEY/Basecamp/37signals, deren CTO David Heinemeier Hansson erklärte, dass sie in den nächsten 5 Jahren über 7 Millionen Dollar einsparen würden, wenn sie nicht in der Cloud arbeiten würden. Ein völlig unsinniger Vergleich ihrer gekauften Server, die eine halbe Million Dollar gekostet haben, mit ihren wahnsinnigen jährlichen Cloud-Ausgaben von 1,9 Millionen Dollar macht die Rechnung komplett \[1\].

Sicher – Basecamp oder HEY sind nicht mit einem Unternehmen vergleichbar, oder? Aus eigener Erfahrung kann ich sagen, dass es sogar für größere Unternehmen günstiger ist, ihre Hardware in ihrem eigenen Rechenzentrum zu betreiben, als auf die Cloud umzusteigen. Ein entscheidender Faktor ist die Datenmenge und wie dynamisch und skalierbar die Infrastruktur dafür sein muss. Bei Datenmengen im Petabyte-Bereich wird die Cloud schnell zu einer Geldverschwendung ohne Ende. Eine relativ statische Arbeitslast reduziert auch die damit verbundenen Vorteile drastisch und hat viele andere Nachteile. Auf der anderen Seite wächst der Cloud-Markt jedes Jahr kontinuierlich, ohne dass ein Ende in Sicht ist. Um zu einer Entscheidung zu gelangen, welcher Weg der richtige ist, müssen Sie viele variable Faktoren berücksichtigen, von einem einfachen Kostenvergleich über die verfügbaren Kompetenzen bis hin zum tatsächlichen Bedarf Ihres Unternehmens. Eine umfassende Bewertung, ob die Cloud für Sie sinnvoll ist, kann ein Projekt für sich sein. Wir möchten Ihnen jedoch einige Ideen zu Kriterien geben, die Sie berücksichtigen sollten, wenn Sie sich an diesem Punkt befinden:

- **Kosten**: Bewerten Sie die anfänglichen Investitionskosten oder einmaligen Kosten für On-Premise-Lösungen im Vergleich zu den Betriebskosten oder laufenden, abonnementähnlichen Kosten für Cloud-Dienste. Berücksichtigen Sie dabei die langfristigen finanziellen Auswirkungen, aber auch, dass Sie mit Cloud Computing am meisten Geld sparen, wenn Sie für 1 oder 3 Jahre im Voraus bezahlen. Das ist fast so, als würden Sie die Hardware kaufen.
- **Skalierbarkeit**: Bewerten Sie Ihren Bedarf, Ressourcen dynamisch zu skalieren, um auf schnelle Veränderungen reagieren zu können. Ein Tipp: Wenn die Spitzen zu schnell auftreten, ist ein statischer Server für die Benutzererfahrung möglicherweise besser geeignet als minutenlanges Warten, bis neue Instanzen gestartet sind.
- **Zuverlässigkeit**: Bewerten Sie Verfügbarkeitsgarantien, Redundanz und Failover-Fähigkeiten, um einen kontinuierlichen Betrieb aufrechtzuerhalten. Werfen Sie einen Blick auf die Geschichte der Ausfälle. Einige Cloud-Anbieter haben häufig Probleme.
- **Compliance**: Stellen Sie die Einhaltung gesetzlicher und regulatorischer Anforderungen sicher, wobei Sie sich auf Datenresidenz und Datenhoheit konzentrieren sollten. Bevor Sie eine Entscheidung treffen können, müssen Sie Ihre Sichtweise zur Datenhoheit schärfen. Leider ist dieser Begriff eher ein Spektrum als eine klare Liste von Anforderungen.
- **Integration**: Stellen Sie die Kompatibilität mit bestehenden Systemen und Software sowie die Verfügbarkeit von APIs und Integrationstools sicher. Der Anbieter sollte **Infrastructure as Code** (**IaC**) unterstützen, insbesondere um Konten, Benutzer und Berechtigungen programmgesteuert zu erstellen.
- **Support**: Bewerten Sie die Verfügbarkeit und Qualität des technischen Supports sowie **die Service Level Agreements** (**SLAs**). Informieren Sie sich über die Zufriedenheit anderer Benutzer mit dem angebotenen Support. Nur weil Sie einen Vertrag haben, der besagt, dass jemand Ihr System wartet und Ihnen hilft, bedeutet das nicht, dass der Service auch gut ist.
- **Entwicklung neuer Dienste**: Bewerten Sie die Geschwindigkeit und Anzahl der neuen Funktionen, die Ihnen der Anbieter zur Verfügung stellt. Bedenken Sie, dass es auch zu viele Updates pro Monat geben kann, aber auch, dass es kaum neue Funktionen gibt.
- **Geografische Überlegungen**: Berücksichtigen Sie die Nähe der Rechenzentren zu den Endnutzern und die regionale Verfügbarkeit der Dienste. Wenn Ihr Unternehmen global verfügbare **Software as a Service** (**SaaS**) entwickelt, ist es möglicherweise einfacher, auf einer öffentlichen Cloud aufzubauen, als mehrere regionale Anbieter zu integrieren.
- **Fähigkeiten und Fachwissen**: Bewerten Sie die Verfügbarkeit von qualifiziertem Personal und die Schulungsanforderungen für die Verwaltung der Infrastruktur. Bedenken Sie, dass Sie dafür praktisch jeden aus dem IT-Bereich benötigen, der dies tun kann. Wie sieht ein kurzfristiger Plan aus? Was wird langfristig benötigt? Vergessen Sie, dass Cloud Computing einfach ist; die meisten Unternehmen haben Schwierigkeiten, weil sie ihre Teams nicht schulen.
- **Umweltverträglichkeit und Nachhaltigkeit**: Berücksichtigen Sie den Energieverbrauch, den CO2-Fußabdruck und die Nachhaltigkeitspraktiken des Anbieters. Wie wird mit Abwasser umgegangen? Wenn der Anbieter CO2-Ausgleichszertifikate kauft, denken Sie daran, dass Sie dafür bezahlen müssen, da diese theoretisch die Stromkosten erhöhen.

Die Cloud hat oft einen großen Vorteil: Es gibt fast nichts, was Sie daran hindert, sofort loszulegen. Sie finden unzählige Vorlagen, Blaupausen und Beispiele. Und innerhalb kurzer Zeit sind Sie startklar und haben Ihre erste Umgebung als Plattform zur Verfügung.

# Wenn wir uns für die Cloud entscheiden, müssen wir ihre versteckten Kosten berücksichtigen

Da wir uns in diesem Buch in erster Linie auf die Cloud konzentrieren, gehen wir vorerst davon aus, dass diejenigen, die sich für Bare-Metal-Lösungen entscheiden, von Natur aus ein höheres Kostenbewusstsein und eine höhere Sensibilität haben.

Cloud-Anbieter stellen uns Dienste mit vielen integrierten Funktionen zur Verfügung. Diese umfassen häufig Backup-Lösungen, Skalierbarkeit, **Hochverfügbarkeit** (**HA**) und einen zentral verwalteten Service. Bei der Planung der Cloud-Infrastruktur finden wir meist harte Fakten und fundierte Schätzungen. Harte Fakten sind Informationen wie die Anzahl der benötigten CPUs oder Server, die zu verwendende Datenbank, ob es sich um einen einzelnen Knoten oder HA handelt und so weiter. Sie sollten sich jedoch bewusst sein, dass fast jede Option, für die Sie sich bei einem öffentlichen Cloud-Anbieter entscheiden, gewisse Kostenauswirkungen hat.

Zu den häufigsten Kostenfaktoren gehören die folgenden:

- **Load Balancer**: Diese werden in fast jeder Architektur benötigt, und das gilt auch für Sie. Wie bereits erläutert, haben wir die Möglichkeit, die App-Dienste vom Kubernetes-Namespace auf die Cloud auszuweiten und sogar das Netzwerk zu steuern – eine große Kostenfalle.
- **API-Gateway**: Der noch schlimmere Zwilling des Load Balancers, der als Best Practice eingesetzt wird, ist sehr kostspielig, insbesondere für kommunikationsintensive Systeme und Routing-intensive Kommunikation.
- **Daten**: Ob im Ruhezustand oder während der Übertragung – Daten werden schnell zum größten Kostenfaktor in einer Cloud-Rechnung. Während alles nach oben und unten skaliert werden kann, müssen Ihre Daten irgendwo gespeichert werden.
- **Backups und Snapshots**: Sie sind für eine ausgereifte Plattform unverzichtbar. Sie benötigen eine sehr gute Backup-Strategie, die schlank, aber zuverlässig ist.
- **Skalierbare Managed Services**: Wenn Sie serverlose, Message-Streaming- oder vortrainierte KI-Modelle verwenden – also alles, was unbegrenzt skalierbar ist –, ist es entscheidend, Grenzen zu setzen, um unerwartete Kosten zu vermeiden.

Ideale Cloud-Projekte – und wir müssen hier betonen, dass es sich um Dinge mit einer Frist handelt – sind streng vorgegeben und folgen den Best Practices des Cloud-Anbieters. Fast jedes Cloud-Projekt ist nicht ideal, was zu Reibungsverlusten bei der Migration durch benutzerdefinierte Implementierungen führt, die erforderlich sind, um die alte Welt und den Cloud-Anbieter irgendwie miteinander kompatibel zu machen. Diese versteckten Kosten entstehen durch fehlende Fähigkeiten, denn woher sollen die erforderlichen Fähigkeiten plötzlich kommen? Hilfe von externen Anbietern von Fachwissen zu erhalten, würde bedeuten, dass diese Sie zuerst verstehen müssen, bevor sie Ihnen tatsächlich helfen können. Ohne externe Unterstützung würden die meisten Cloud-Projekte jedoch viel früher als gescheitert gelten.

Zusammenfassend lässt sich sagen, dass sich die meisten Dienste in Bezug auf die Kosten gegen Sie wenden können. Als Plattformingenieure müssen wir in der Lage sein, diese Elemente zu kontrollieren und Leitplanken und Beschränkungen zu schaffen. Um dies zu ermöglichen, brauchen wir Transparenz bei den Kosten.

# Wo findet man Transparenz?

Mittlerweile gibt es eine Vielzahl von Möglichkeiten, Informationen darüber abzurufen, wo wir Geld ausgeben und ob dies anhand von Kennzahlen wie der Auslastung als Verschwendung angesehen wird. Alle Cloud-Anbieter bieten die Möglichkeit, Kosten zu untersuchen (und aufzuschlüsseln), aber aufgrund der Fokussierung auf die Infrastruktur fehlen Details, insbesondere auf der Anwendungsebene. Der folgende Screenshot aus dem AWS Cost Explorer zeigt eine Verbrauchskurve für verschiedene Diensttypen. Wir müssten nun Filter anwenden, um mehr Einblicke zu gewinnen und die Ursachen der Kosten zu analysieren:


<img width="1041" height="443" alt="image" src="https://github.com/user-attachments/assets/42c7c3ef-d536-43c5-9f51-5c7761707872" />

Abbildung 8.1: AWS Cost Explorer

Kommerzielle Lösungen wie Apptio Cloudability können Kosten aus vielen verschiedenen Konten, Cloud-Anbietern und Umgebungen in einem einzigen Tool erfassen. Sie wenden die FinOps-Logik auf die gegebenen Daten an und verfügen über vordefinierte Dashboards wie das Dashboard für Stückkosten und Einsparungen aus dem folgenden Screenshot:


<img width="1012" height="576" alt="image" src="https://github.com/user-attachments/assets/5fa29606-14ff-4bc0-aa35-4a409ab157c6" />


Abbildung 8.2: Detailliertes Dashboard von Apptio Cloudability zu Stückkosten

Microsoft definiert Stückkosten wie folgt: „Die Messung von Stückkosten bezieht sich auf den Prozess der Berechnung der Kosten einer einzelnen Einheit eines Unternehmens, die den Geschäftswert der Cloud aufzeigen kann.“ Was genau eine Einheit ist, bleibt Ihnen überlassen. Es können Transaktionen in Finanzsystemen, Nutzer einer Medienplattform oder alles andere sein, was Sie verschiedenen Teilen der Infrastruktur zuordnen können.

In unserer Plattform- und Open-Source-Welt finden wir auch Lösungen für mehr Transparenz, wie Kubecost (mit kommerziellen Tarifen) und OpenCost. Beide können Kosten innerhalb eines Clusters und in Kombination mit Cloud-Anbieter-Ressourcen zuweisen. Leider mangelt es beiden an guten Analysefunktionen. Aus diesem Grund sehen wir oft selbst implementierte Lösungen in Kombination mit Business-Intelligence-Tools (**BI**) oder Prometheus- und Grafana-Implementierungen, die mit einigen Kostendaten angereichert sind. Wie gut diese Lösungen sind, hängt von der investierten Zeit und dem investierten Geld ab.

# FinOps und Kostenmanagement

In den letzten Jahren hat FinOps an Popularität gewonnen und versucht, sich vom klassischen Kostenmanagement abzuheben. Kostenmanagement wird oft als kurzfristige, isolierte, zweckgebundene Aktivität beschrieben, die schnelle Kosteneinsparungen erzielen soll. Wenn Sie als Plattformteam kostenbewusst handeln und Ihre Kosten aktiv verwalten, ist dies auch eine nachhaltige und langfristige Lösung. Der Erfolg von FinOps liegt jedoch in seinem ganzheitlichen Ansatz, der Beschaffungsabteilungen, **Geschäftsbereiche** (**BUs**) und Finanzabteilungen einbezieht und klar darauf abzielt, ein organisatorisches Verständnis für Cloud-Kosten und deren Dynamik zu schaffen.

Die folgende Übersicht über das FinOps-Framework zeigt, dass es einen ähnlichen Ansatz verfolgt wie das, was ein Plattform-Engineering-Team tut. Wir sehen Prinzipien, die mit Ihren Prinzipien in Einklang gebracht werden müssen, Fähigkeiten, die integriert und aktiviert werden müssen und die Ihren Input erfordern, sowie Personas – Rollen wie die des Plattform-Ingenieurs, mit dem sie zusammenarbeiten \[2\]:


<img width="1024" height="539" alt="image" src="https://github.com/user-attachments/assets/a8dfc17e-bb5d-4ade-8861-d3656dda5451" />

Abbildung 8.3: FinOps-Framework der FinOps Foundation

Als Plattformteam sollten Sie mit FinOps-Teams zusammenarbeiten und deren Einfluss auf Ihre Plattform aktiv steuern. Potenzielle Kosteneinsparungen müssen gegen Ihre Grundsätze, die Zufriedenheit der Nutzer und die Entwicklererfahrung abgewogen werden. Datenbasierte Empfehlungen erfordern eine architektonische Qualifikation und die Berücksichtigung alternativer Optionen und Vorschläge zur Realisierung von Kosteneinsparungen.

Im folgenden Abschnitt werden wir diskutieren, wie eine Tagging-Strategie implementiert werden kann. Tags sind eine einfache Lösung, um zusätzliche Informationen zu Cloud- und Kubernetes-Ressourcen bereitzustellen und eine gewisse Transparenz zu schaffen. Außerdem benötigen viele Kostenmanagement- und FinOps-Tools Tags, um bessere Einblicke zu liefern.

# Implementierung einer Tagging-Strategie zur Aufdeckung versteckter Kosten

Tags und Labels sind für Sie wahrscheinlich nichts Neues, da sie in einer Vielzahl von Tools, Public Clouds und Kubernetes verwendet werden. Wir verwenden das Wort „Tag” auch für Labels, aber wenn wir das Wort „Labels” verwenden, schreiben wir eigentlich ausschließlich über Kubernetes-Labels.

Das Anwenden und Verwenden von Tags kann zu einer Kunst für sich werden. Wenn es zu viele Tags gibt, kann unklar werden, welche Informationen sie mit dem Dienst verknüpfen sollen. Auch das Fehlen von Tags ist natürlich nicht hilfreich. In Unternehmen mit vielen verschiedenen Geschäftsbereichen und Abteilungen sowie komplexen Release-Mechanismen können Tags überladen oder zu einer bloßen Ansammlung von Abkürzungen werden. Der Punkt ist, dass wir Tags benötigen, um Transparenz darüber zu gewinnen, zu welchen Diensten sie gehören, möglicherweise um verschiedene Service-Levels oder Sicherheitsklassen anzuzeigen, und um letztendlich eine Verknüpfung zwischen diesen Diensten und Kostenstrukturen sowie der Ressourcennutzung herzustellen. Tags ermöglichen also eine genauere Analyse der kostenrelevanten Ressourcen und der Kostenursachen.

# Tags für einen bestimmten Zweck verwenden

Tags können auf verschiedene Zielgruppen und Benutzer ausgerichtet sein. Je nachdem, um welche Subdomain es sich handelt, sollten sie organisatorische, betriebliche, sicherheitsrelevante oder sogar architektonische Informationen enthalten. Wir können auch über Tags nachdenken, die für uns als Plattformingenieure potenziell hilfreich sind.

Tags für organisatorische Informationen können definieren, welche Abteilung, Rolle oder welches Team für den Dienst verantwortlich ist, ob es sich um eine interne oder externe Lösung handelt und ob es Einschränkungen hinsichtlich des Landes, der Compliance oder der Governance gibt.

Im operativen Bereich sind häufige Attribute der Servicelevel, Zeitpläne und Wartungsfenster, aber auch sehr technische Informationen, die durch Tools von Drittanbietern eingeführt werden können, beispielsweise über Cloud Custodian, das bestimmte Cloud-Richtlinien implementiert \[3\].

Für domänenspezifische Bereiche wie Sicherheit oder ein Plattformteam können wir uns Tags und Labels als Definition einer erforderlichen Isolierung oder eines erforderlichen Datenschutzes vorstellen, oder aber als typisches Skalierungsmuster, Spitzenwerte oben und unten oder als Identifizierung für eine Microservice-Architektur und deren Zugehörigkeit zu bestimmten Komponenten und einer Struktur.

Unser Fokus liegt auf relevanten Kosten-Tags. Diese ähneln oft organisatorischen Tags oder stehen in Zusammenhang mit den zuvor erwähnten operativen oder domänenspezifischen Tags. Die Klärung der organisatorischen Zugehörigkeit oder die Bereitstellung von Einblicken, warum etwas so drastisch skaliert, sind wichtige Faktoren für das Kostenmanagement. Diese Tags tragen dazu bei, Projekten und Teams, die das Kostenbewusstsein schärfen müssen, eine klare Übersicht zu verschaffen.

Einige Quellen weisen auch auf die Verwendung von Tags für die Zugriffsverwaltung hin. Dies sollte aus mehreren Gründen mit Vorsicht behandelt werden. Wenn Sie über **eine attributbasierte Zugriffskontrolle** (**ABAC**) und Rechteverwaltung verfügen, können Tags ein praktikabler und einfacher Ansatz sein, um dies zu erreichen. Dies hat jedoch den Nachteil, dass Sie eine reine Informationsquelle in ein sicherheitskritisches Element verwandeln, das geschützt und bei der Verwendung doppelt überprüft werden muss. Die Vermischung mit dem Informationscharakter kann die Verwendung von Tags erschweren und höchstwahrscheinlich ein Hindernis für die ordnungsgemäße Verwendung darstellen. Wir haben bereits erwähnt, dass Tags zur Übertragung von Sicherheitsinformationen verwendet werden können. Es besteht jedoch ein Unterschied zwischen der Bereitstellung von Informationen wie Risikoklassifizierungen oder Sicherheitsstufen und der Möglichkeit, Zugriff zu gewähren.

Daher ist es wichtig, wie bei unserer Plattform, den Zweck zu definieren, warum wir Tags verwenden wollen. Tags nach Belieben zu verwenden und so viele wie möglich zu setzen, ist zwar besser als gar nichts, kann aber in Zukunft zu Problemen führen, wenn unklar ist, ob ein Tag nun kritisch ist oder nicht.

# Einschränkungen bei Tags und Labels

Leider gibt es zwei häufig auftretende Probleme:

- Tags haben keinen Standard, was bedeutet, dass es viele Variationen hinsichtlich ihrer Länge, Anzahl, zulässigen Zeichen oder Groß-/Kleinschreibung gibt.
- Unternehmen verfügen in der Regel über mehrere Umgebungen bei vielen verschiedenen Anbietern und Plattformen.

Um also in den nächsten Schritten eine Tagging-Strategie zu definieren, müssen Sie die kleinste Zahl kennen, auf die Sie sich zuverlässig stützen können. Eine Tagging-Strategie führt einen Standard ein, der auf jeder Plattform anwendbar sein muss. Die Definition mehrerer unterschiedlicher Ansätze pro Plattform führt zu Verwirrung und Fehlern.

Als Beispiel vergleichen wir verschiedene Anbieter und Plattformen:

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
|     | **AWS** | **GCP** | **Kubernetes** | **Azure** |     |
| **Maximale Anzahl von Tags pro Dienst** | 50  | 64  | Keine Begrenzung angegeben | 50  |     |
| **Max. Länge des Tag-Namens in Zeichen** | 128 | 63  | 63  | 512 |     |
| **Max. Zeichenanzahl für Tag-Wertlänge** | 256 | 63  | 63  | 256 |     |
| **Sonderzeichen** | Alphanumerische Zeichen, Leerzeichen und + - = . _ : / @ | Alphanumerische Zeichen, - und _ | Alphanumerische Zeichen, - . _ | Alphanumerische Zeichen, &lt;, &gt;, %, &, \\, ?, / nicht zulässig |     |
| **Groß-/Kleinschreibung** | Ja  | Ja  | Ja  | Ja  |     |

Tabelle 8.1: Tag-Beschränkungen von Cloud-Anbietern und Kubernetes

Obwohl 63 Zeichen als allgemeine Richtlinie gut erscheinen, haben wir in der Praxis festgestellt, dass für viele Unternehmen selbst 256 Zeichen nicht ausreichten. Dies ist nur ein weiteres Beispiel dafür, warum eine Tagging-Strategie gut durchdacht sein muss.

Außerdem funktionieren einige Strukturen nicht bei allen Anbietern. Angenommen, unser Unternehmen Financial One ACME nutzt AWS und GCP, einschließlich des verwalteten Kubernetes-Dienstes für die Plattform. Warum stößt Financial One ACME an die Grenze der maximal zulässigen Anzahl von Tags? Das AWS-Team hat dieses Problem als erstes entdeckt und herausgefunden, dass es längere Tags und einige Sonderzeichen verwenden kann, die eine Art verschachtelte Struktur ermöglichen. Also begann es, verschiedene Tags zu einem einzigen zu kombinieren, mit folgendem Ergebnis:

department-responsible=financial-one-ACME/domain-sales+marketing/stream-customer-management/squad-frontend/operations-squad-lazy-turtle

Der Wert hat 112 Zeichen und enthält /, um die hierarchischen Schritte darzustellen, und +, um „und“ darzustellen. Das Team ist mit dem Ergebnis zufrieden und überträgt dieses neue Tag in das gemeinsame Repository. Einige Zeit später erhält das Plattformteam Beschwerden, dass es in der IT-Abteilung für Vertrieb und Marketing ein Problem mit den Bereitstellungen gibt und die neuesten Releases aufgrund einiger Labels nicht ausgerollt werden.

Darüber hinaus gibt es weitere Einschränkungen, wie beispielsweise die maximale Anzahl von Tags pro Konto oder Abonnement.

# Festlegen einer Tagging-Strategie

Wie bereits erläutert, können Tags viele verschiedene Zwecke haben; in erster Linie müssen wir ein Gleichgewicht zwischen technischen Tags und geschäftlichen Tags finden. Geschäftliche Tags lassen sich in organisatorische und kostenbezogene Tags unterteilen. Letztendlich überschneiden sich die Informationen vieler Tags. Um den richtigen Ansatz zu finden, ist es daher oft sinnvoll, einige grundlegende Regeln und Grenzen für die Definition festzulegen. Im zweiten Schritt müssen Sie sich zwischen Betrieb, Plattform und Entwicklung abstimmen, um die richtigen Tags aus technischer Sicht zu finden, bevor Sie mit der Festlegung der organisatorischen Tags fortfahren. Diese Vorgehensweise ist sinnvoll, da die für den Betrieb erforderlichen Tags oft auch Informationen über die Organisation enthalten.

Beginnen wir mit einigen allgemeinen Grundregeln:

- Tag-Namen und -Werte dürfen maximal 63 Zeichen lang sein.
- Tags dürfen nur aus alphanumerischen Zeichen bestehen.
- Tags dürfen nur die Zeichen - und _ enthalten.
- Konzentrieren Sie sich auf den Tag-Wert und dessen Inhalt, da Sie in der Regel danach filtern und suchen.
- Tag-Namen sind eher für das Sortieren und Gruppieren relevant.
- Geben Sie keine **personenbezogenen Daten** (**PII**) in ein Tag ein.
- Legen Sie einen einheitlichen Stil fest. Unternehmen bevorzugen möglicherweise den Pascal-Stil, während in der Technik der Kebab-Stil häufiger verwendet wird.
- Es ist besser, mehr Tags zu verwenden als zu wenige, aber versuchen Sie, 10 % bis 20 % der verfügbaren Tags frei zu halten.

Auf der Grundlage dieser Regeln können wir die nächsten relevanten Elemente erstellen. Zunächst müssen wir über Tagging-Kategorien nachdenken, damit diese feiner gegliedert sind als die bisher besprochenen. Eine bewährte Vorgehensweise ist es, die folgenden Kategorien zu berücksichtigen:

- Eigentumsverhältnisse – Abteilungen, Teams, Organisationen, Ströme.
- Umgebung – unabhängig davon, wie Ihre Staging-Umgebungen aussehen.
- Projekt oder Produkt – Projekt- oder Produktcluster, um zu identifizieren, welche Komponenten zusammengehören.
- Kostenstelle – wer ist dafür verantwortlich? Gibt es zusätzliche gemeinsame Kosten?
- Compliance – gesetzliche Beschränkungen und Anforderungen, Richtlinien und Compliance-Regeln.
- Betrieblich – Lebenszyklen, Backups, Wartungsfenster.

An dieser Stelle müssen wir uns mit einer Namenskonvention befassen. Wie bereits erwähnt, ist es wichtig, einen einzelnen Tag nicht zu überladen. Unter Berücksichtigung der vorgegebenen Regeln und Einschränkungen sowie der Beschaffenheit vieler Software- und Systemkomponenten könnte eine Tag-Konvention wie folgt aussehen:

- department=public-relations-content-management
- Eigentümer=Abteilung-Öffentlichkeitsarbeit
- Datenklassifizierung=personenbezogene-Daten

In einigen Sprachen wird es bevorzugt, einem Pascal-Stil (Hello-My-Name-Is-Pascal) oder einem Camel-Stil (i-Am-A-Camel) zu folgen. Der Stil, alles in Kleinbuchstaben zu schreiben, wird als Kebab-Stil bezeichnet. Sie müssen diese Muster sehr klar definieren. Wie viele Zeichen und wie viele Wörter sollte der Name haben? Ist er eher beschreibend oder entspricht er nur dem, was identifiziert wurde? Das Gleiche gilt für den Wert. Stellen Sie sicher, dass diese Konventionen dokumentiert, kommuniziert und in die Einarbeitung oder Schulung Ihrer Ingenieure aufgenommen werden.

Der letzte Schritt besteht nun darin, mit diesen Grundregeln einen Tag-Katalog aufzubauen. Es wird empfohlen, diese Kataloge so zu erstellen, dass Sie Platz haben, um die Bedeutung, den Zweck und die Zielgruppe des Tags zu beschreiben. Dies hilft Ihnen auch dabei, die Tags kurz zu halten, da Sie den Wert der Tags nicht weiter beschreiben müssen. Die folgende Tabelle ist ein einfaches Beispiel für einen Tag-Katalog. Er kann je nach den individuellen Anforderungen der Organisation erweitert werden. Es ist wichtig, alle Informationen, die Sie möglicherweise auch in das Tag aufnehmen müssten, aber die es künstlich lang und unlesbar machen, in den Katalog auszulagern:

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| #   | Tag-Name | Erwarteter Wert | Bedeutung | Zweck | Tag Stakeholder |
| 1   | Abteilung | Abteilungsbezeichnung oder -code, z. B. DE-22-P | BU oder der Bereich, zu dem die Anwendung gehört | Klärung des Eigentümers der Anwendung | Anwendungsinhaber; Betrieb |
| 2   | Anwendung | Anwendungsname; zum Beispiel internal-cms | Name der Anwendung | Identifizieren Sie die Anwendung | Anwendungsinhaber; Betrieb; Architekt |
| 3   | Wartung zulässig | Tag und Uhrzeit, an denen die Wartung durchgeführt werden kann; zum Beispiel Sonntag-0800-1230 | Das Tag identifiziert den Tag oder die Tage sowie einen Zeitrahmen, der als 0800 geschrieben wird, was 08:00 Uhr morgens bedeutet. | Legt fest, wann die Anwendung heruntergefahren werden kann, um ein Update/Patch durchzuführen oder eine neue Version zu veröffentlichen | Operationen; First-Level-Support |

Tabelle 8.2: Beispiel für einen Tag-Katalog

# Automatisierung der Tag-Vergabe

Es wäre unmöglich, alle Ressourcen manuell zu taggen, insbesondere auf einem IDP mit vielen beweglichen Komponenten. Bestimmte Tools können uns dabei helfen, Ressourcen bei ihrer Erstellung automatisch zu taggen oder sie sogar nachträglich zu „patchen”. Wie wir bereits gesehen haben, müssen wir auf der Plattform zwischen der Infrastruktur, auf der die Plattform läuft, und der Benutzerperspektive der Workloads unterscheiden, die sie ausführen oder vom Cluster aus verwalten.

Wenn Sie Ihre Infrastruktur mit Tools wie Terraform/OpenTofu verwalten, können Sie Komponenten in Ihrem Code wie folgt kennzeichnen:

resource "aws_ec2_tag" "example" {

resource_id = aws_vpn_connection.example.transit_gateway_attachment_id

key = "Owner"

value = "Operations" }

KopierenErklären

Bei bestimmten Anbietern können Sie sogar allen Ressourcen dieselben Tags zuweisen. Dies sollte mit Vorsicht geschehen, da Sie andere Ressourcen nicht fälschlicherweise taggen möchten, insbesondere wenn diese Integrationen von Drittanbietern auslösen oder zu falschen Abrechnungen führen:

provider "aws" { # ... weitere Konfiguration ...

default_tags {

tags = {

Environment = „Production”

Owner = „Ops“ } } }

### KopierenErklären

Praktisch alle IaC-Lösungen bieten diesen Ansatz und können an jede Art von Infrastruktur angepasst werden, egal ob Cloud oder On-Prem.

Dies ist auch für Kubernetes-Ressourcen möglich. Wir werden hier auf reguläre Bereitstellungsdateien verzichten, da diese höchstwahrscheinlich anders behandelt werden, wie beispielsweise bei Helm. Das folgende Beispiel zeigt, wie Helm den Wert für die Labels aus der Helm-Chart-Wertedatei übernimmt. Vorlagenwerte werden dynamisch durch eine \_helper.tpl-Vorlagendatei erstellt, während .Release-Werte integrierte Informationen sind. Eine weitere Option besteht darin, die Werte aus einer vom Benutzer bereitgestellten values.yaml-Datei zu lesen:

apiVersion: apps/v1

kind: Deployment

metadata:

name: {{template "grafana.fullname".}}

Labels:

&nbsp;  app: {{template "grafana.fullname".}}

&nbsp;  Diagramm: {{template "grafana.chart".}}

&nbsp;  release: {{.Release.Name}}

&nbsp;  Herkunft: {{.Release.Service}}

### KopierenErklären

Eine Stärke von Helm ist, dass wir dies mit einer einfachen if-Anweisung kombinieren können. Dadurch können wir einen vordefinierten Satz von Informationen übergeben, je nachdem, wo die Bereitstellung erfolgen soll, oder basierend auf einem anderen Auslöser.

### Hinweis

Verwenden Sie vordefinierte Labels in Ihren Backstage-Vorlagen, um Ihre Benutzer zu zwingen, ein Mindestmaß an Labels zu definieren.

Beide Ansätze sind stark deklarativ und können bei ihrer Einführung oder Überwachung fehlschlagen. Natürlich können Sie die korrekte Verwendung von Labels in den CI/CD-Pipelines überprüfen, aber dies kann dazu führen, dass viele Bereitstellungen fehlschlagen. Dies führt uns zu Policy-Engines. Einerseits können diese verwendet werden, um die Bereitstellungen auf Labels zu testen, aber ein Tool wie Kyverno kann diese Informationen bei Bedarf auch hinzufügen. Das folgende Beispiel einer Kyverno-Richtlinie fügt allen Pods oder Diensten die Labels „foo=bar“ hinzu:

apiVersion: kyverno.io/v1

kind: ClusterPolicy

metadata:

name: add-labels

annotations:

&nbsp;  policies.kyverno.io/title: Labels hinzufügen

&nbsp;  …

&nbsp;  policies.kyverno.io/subject: Label

Spezifikation:

Regeln:

\- name: add-labels

&nbsp;  Übereinstimmung:

&nbsp;    beliebig:

&nbsp;    - Ressourcen:

&nbsp;        Arten:

&nbsp;        - Pod

&nbsp;        - Dienst

&nbsp;  mutate:

&nbsp;    patchStrategicMerge:

&nbsp;      Metadaten:

&nbsp;        Labels:

&nbsp;          foo: bar

### CopyExplain

Wir können diese Informationen sehr detailliert auswählen und patchen, und sie können bei Bedarf jederzeit später aktualisiert werden.

# Konsolidierte versus getrennte Kosten- und Abrechnungsberichte

In vielen Unternehmen besteht Bedarf an konsolidierten Kosten- und Abrechnungsberichten. Für das Unternehmen ist dies zwar auf einer höheren Ebene der schnellste Weg, um die Ausgaben für die Infrastruktur zu verstehen, aber es erfordert auch viele Tags, um eine korrekte Aufteilung und Detailgenauigkeit zu gewährleisten. Wenn Unternehmen zu groß werden und die Anzahl der geschäftlichen Tags die der technischen Tags übersteigt, ist dies ein klares Zeichen dafür, dass etwas schiefgelaufen ist. An diesem Punkt radikal zu sein, wird es dann zu einem Anti-Muster, konsolidierte Kosten- und Abrechnungsberichte zu erstellen. Aber was können wir dann tun? Unternehmen arbeiten beispielsweise häufig mit alphanumerischen Codes, um Abteilungen zu identifizieren. Anstelle einer Abteilung namens „Finanzen und Buchhaltung” gibt es dann beispielsweise „B-2-FA-4”. Ein solcher Code ist die perfekte Grundlage, um viele andere organisatorische oder geschäftliche Tags zu eliminieren und sie in eine Zuordnungstabelle oder Datenbank einzutragen, falls Sie diese Zuordnung programmgesteuert an anderer Stelle vornehmen möchten. Weitere zu berücksichtigende Aspekte sind beispielsweise die Staging-Umgebungen und der Cluster. In den meisten Fällen sind Entwicklungs-, Integrations- und Produktionssysteme eigenständig. Das bedeutet, wenn Ihre Anwendung auf dem Manhattan-Cluster läuft, was mit prod-1234-eu übersetzt werden könnte, dann brauche ich kein weiteres Tag, das stage=production oder region=eu angibt. Um es klar zu sagen: Sie sollten sich darauf beschränken, nicht zu viele Informationen in einen einzigen Wert einzufügen.

Allerdings gibt es in dieser Geschichte ein großes Aber, das uns zum Anfang des Themas zurückführt. Aus Sicht des Kostenmanagements benötigen Sie viele gute Tags, damit Sie Ihre Analysen und Recherchen durchführen können.

Tags allein reichen nicht aus; sie sind zwar ein wichtiger Bestandteil der Kostenoptimierung, aber welche Optimierungen nehmen Sie vor? Im nächsten Abschnitt werden wir uns mit allgemeinen Ansätzen für Optimierungsstrategien befassen, die nicht nur die richtige Dimensionierung und Reduzierung der Infrastruktur umfassen.

# Betrachtung von Strategien zur Kostenoptimierung

Der schnellste Ansatz zur Senkung der Cloud- und Plattformkosten besteht darin, nicht benötigte Ressourcen abzuschalten. Das größte Problem dabei ist, dass alle an diesem Prozess Beteiligten möglicherweise Gründe haben, warum sie die Infrastruktur in ihrer jetzigen Form benötigen. Ich möchte jedoch Ihre Sichtweise auf dieses Thema von nun an ändern: Kostenoptimierung ist nichts, was wir nachträglich einführen sollten. Hier ist ein weiterer Grundsatz, den Sie berücksichtigen sollten: Seien Sie kostenbewusst und effektiv und berücksichtigen Sie dies bei der Gestaltung der Plattform.

### Hinweis

Je mehr Potenzial zur Kostenoptimierung in einer Plattform steckt, desto schlechter haben wir unsere Arbeit als Plattformingenieure und -architekten gemacht.

Wir können das Potenzial in jedem Teil unserer Plattform nutzen. Allerdings könnte man darüber ein ganzes Buch schreiben, um alle Aspekte abzudecken. Daher werden wir Prinzipien behandeln, die auf alle Komponenten innerhalb der Plattform anwendbar sind.

# Prozesse rationalisieren

Prozesse, sowohl geschäftliche als auch technische, können höhere Kosten verursachen. Ich werde Ihnen ein Beispiel für ein Muster/Anti-Muster geben, das zu unnötigen Kosten führt. Die Kubernetes-Version ist in drei Hauptversionen unterteilt, und alle paar Wochen dazwischen erhalten Sie Patches, Bugfixes und Sicherheitspatches. Das Kubernetes-Release-Team hat einen großen Teil des Release-Prozesses automatisiert, indem es nächtliche Builds durchführt und ständig mehrere tausend Tests auf der Kubernetes-Infrastruktur ausführt. Als dieser Ansatz eingeführt wurde, betrachtete die Community ihn als den Heiligen Gral der Top-Tech-Unternehmen. Plötzlich wollte jeder nächtliche Builds seiner Container haben, wobei oft der Testteil übersprungen wurde, da dieser zu aufwendig war.

Der Nachteil dieses Ansatzes ist, dass die meisten nächtlichen Builds nie bereitgestellt werden. Außerdem verhindert er, dass Build-Server nachts heruntergefahren werden können. Die Container-Registry ist ständig ausgelastet, einschließlich CVE-Scans, und die Unternehmenscontainer sind in der Regel eher schwer, was die Übertragungs- und Speicherkosten erhöht. Was die meisten Unternehmen nicht verstanden haben, ist, dass Kubernetes ein globales Projekt ist. Außerdem gibt es, wenn es für jemanden Nacht ist, irgendwo anders Menschen, die wach sind und an neuen Funktionen arbeiten und diese in das Kubernetes-Repository „ “ übertragen. Letztendlich ist Kubernetes eines der größten Open-Source-Projekte, initiiert von Google, dem größten digital-nativen Unternehmen.

# Denken Sie darüber nach!

Nur weil alle anderen es tun, sollten Sie zweimal darüber nachdenken, ob es wirklich sinnvoll ist!

Zurück zu den Prozessen. Fast jeder Prozess kann verbessert werden, da er in der Regel historisch gewachsen ist. Im Plattformbereich werden regelmäßig Tools eingeführt, die Skripte und selbst entwickelte Tools ersetzen. Bessere Prozesse senken nicht nur die Kosten, sondern können auch die Effizienz steigern, Risiken reduzieren, Fehler minimieren und für Konsistenz sorgen.

Bewährte Ansätze zur Prozessoptimierung finden sich in den Methoden Lean und Six Sigma. Um einen Prozess zu verbessern, lehren sie Ihnen Folgendes:

1.  Definieren/identifizieren Sie das Problem des Prozesses.
2.  Messen Sie die Leistung und die Dauer der Transaktion.
3.  Analysieren Sie die Leistung auf Ineffizienzen und Abhängigkeiten.
4.  Verbessern Sie den Prozess, um Ineffizienzen zu beseitigen.
5.  Kontrollieren und überprüfen Sie den neuen Prozess durch die Einführung von Canary-Deployments.

Das Schöne an Plattformen ist, dass die meisten Prozesse in CI/CD-Pipelines und GitOps-Implementierungen zu finden sind. Diese übersetzen unser Ziel in technische Schritte, um den gewünschten Zustand sicherzustellen. Kompliziert wird es, wenn wir Prozessabhängigkeiten innerhalb von Kubernetes und den darauf aufbauenden Komponenten haben. Als letztendlich konsistentes, ereignisgesteuertes System ist es eine Herausforderung, zu identifizieren, welche Abhängigkeiten welches Verhalten verursachen. Manchmal können wir diese Komponentenreaktion nicht ändern, ohne weitere Auswirkungen zu verursachen.

Prozesse in einer technischen Welt klingen oft wie eine Reihe von Skripten, die zusammenlaufen. Ein idealer Zustand ist ein Cloud-nativer Ansatz, der die standardisierte API von Kubernetes, Controller-Funktionen und Ressourcendefinitionen nutzt. Er entkoppelt verschiedene Funktionen und erleichtert mit diesen Prozessen deren Optimierung. Außerdem erschwert er die Einführung neuer, historisch gewachsener Prozessabfälle.

# Die besten Angebote zu den besten Preisen finden

Eine einfache Möglichkeit zur Kostenoptimierung besteht darin, die Listenpreise zu vergleichen und die günstigste Option zu wählen. Günstig ist dabei relativ, da Sie möglicherweise die Leistung, den Durchsatz der Web , die verfügbaren IP-Adressen usw. einschränken. Kosten und Auslastung sind gute Indikatoren, müssen jedoch hinsichtlich ihrer Auswirkungen auf der zweiten Ebene bewertet werden. Wenn Sie beispielsweise die Instanzgröße reduzieren, kann dies zu einer Verringerung des Durchsatzes und der Leistung führen, sodass Sie eine weitere Instanz einführen müssen. Auf diese Weise nutzen Sie möglicherweise zwei Instanzen zu 80 % bis 90 %, zahlen aber dennoch genauso viel oder sogar mehr, als wenn Sie eine größere Instanz mit geringerer Auslastung betreiben würden.

Wenn Sie nicht an eine bestimmte Region gebunden sind, sind einige Regionen günstiger als andere; dennoch hat dies keine großen Auswirkungen. Eine derzeit sehr gute Option ist die Nutzung von ARM-Servern. Wenn Sie Ihre eigene oder die Workload Ihrer Benutzer nicht darauf ausführen können, führen Sie sie zumindest für verwaltete Dienste wie Datenbanken ein. Dadurch können Sie 20 bis 30 % oder mehr der Kosten einsparen.

Das sind sehr offensichtliche Schritte. Finden und identifizieren Sie die richtigen Ressourcen, die in der richtigen Region nicht überdimensioniert sind. Und wie bereits erläutert, können Sie oft eine bessere Kostenleistung erzielen, wenn Sie die Dinge schlank und übersichtlich halten.

Es gibt viele Tools wie Cloudability oder Flexera, die Ihnen helfen können, eine günstigere Option zu finden, und einige empfehlen sogar eine Änderung der Architektur, um Kosten zu senken. Diese Tools sind für den Einstieg äußerst hilfreich, aber sie sind oft auch mit hohen Kosten verbunden, und das darin enthaltene Wissen können Sie sich auch durch eigene Recherchen oder die Teilnahme an kostenlosen Kursen zur Kostenoptimierung aneignen.

# Entwerfen für höchste Auslastung und geringste Anforderungen

Wenn Plattformingenieure die Infrastruktur reduzieren, hat dies höchstwahrscheinlich Auswirkungen auf die Benutzererfahrung. Je flexibler Ihre Plattform wird, desto besser kann sie sich an die jeweilige Situation anpassen. Sie können aktive Komponenten einführen, die das System entrümpeln und verkleinern, wo dies möglich ist, und Ihre Benutzer über die Möglichkeiten informieren, die Arbeitslast nach Bedarf zu erhöhen oder zu verringern. Die Abstimmung der Auslastung mit der Rechnung kann die Benutzer zu einem verantwortungsvollen Umgang motivieren.

Zuvor haben Sie etwas über die Schwierigkeiten zwischen vielen kleinen Knoten und wenigen größeren Knoten gelernt. Wir haben auch festgestellt, dass wir verschiedene CPU-Architekturen problemlos unterstützen und Ressourcen dynamisch zuweisen können. All diese Elemente spielen eine Rolle bei der Definition des Kerns der Plattform. Ich habe immer das Bild einer Ameisenkolonie im Kopf. In ihrer Mitte herrscht reges Treiben, aber der Kern ist eine stabile Konstruktion, in der sich die Mehrheit der Ameisen befindet. Wenn die Kolonie, also unsere Plattform, wächst, werden wir diesen Teil erweitern. Manchmal wissen wir jedoch nicht, ob dies nur vorübergehend ist. Im Buch „ “ haben Sie verschiedene Möglichkeiten zum Umgang mit dynamischen Workloads kennengelernt. Im folgenden Abschnitt zeigen wir Ihnen einige Best Practices für die Skalierung.

Wie würde also ein ideales Szenario aussehen? Abgesehen davon, dass dies von Ihren Anforderungen abhängt, sollte die Plattform ihre Ressourcen so gut wie möglich nutzen und gleichzeitig keine Overhead-Infrastruktur haben. Einfach gesagt: Das ist für eine Plattform nicht einfach zu bewerkstelligen. Die Arbeitslast liegt nicht in Ihrer Hand und kann von statischer, ressourcenintensiver Software mit langer Laufzeit bis hin zu Tausenden von serverlosen Containern reichen, die ständig in Bewegung sind. Daraus können wir schließen, dass Sie die Plattform so gestalten können, wie Sie möchten; letztendlich kommt es jedoch auf eine kontinuierliche Analyse, Reaktion und Anpassung an. Mit der Zeit können Sie eine Basisebene für automatische Reaktionen in die Plattform einbauen, die die meisten Fälle abdeckt, aber Sie müssen dennoch an der Optimierung arbeiten.

Im letzten Teil dieses Kapitels sehen wir uns einige konkrete Beispiele für Skalierung und Optimierung an. Sie lernen reaktive und prädiktive Skalierung sowie kostenbewusstes Engineering kennen.

Autoscaling, Cold Storage und andere Tricks zur Kostenoptimierung

In [Kapitel 4](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap4/Platform%20Engineering_4%20de.md), im Abschnitt „Automatische Skalierung von Clustern und Workloads”, haben wir bereits einen wichtigen Vorteil und eine Kernfunktion von Kubernetes besprochen. K8s verfügt über verschiedene integrierte Tools und Mechanismen zur Skalierung, z. B. die Konfiguration von ReplicaSets (die Anzahl der gewünschten Instanzen pro Workload) oder die Verwendung von Observability-Daten zur automatisierten Skalierungsentscheidung mit **Horizontal Pod Autoscaler** (**HPA**), **Vertical Pod Autoscaler** (**VPA**) oder **Kubernetes Event Driven Autoscaling** (**KEDA**). Es gibt ein großartiges kostenloses Tutorial, das alle verschiedenen Optionen zur automatischen Skalierung auf Kubernetes durchgeht und von Is It Observable bereitgestellt wird. Hier ist der Link zum YouTube-Tutorial, das auch Links zum GitHub-Tutorial enthält: https://www.youtube.com/watch?v=qMP6tbKioLI.

Der Hauptanwendungsfall der automatischen Skalierung besteht darin, sicherzustellen, dass Workloads über genügend Rechenleistung, Arbeitsspeicher und Speicherplatz verfügen, um bestimmte Verfügbarkeitsziele zu erreichen. Für unser Unternehmen Financial One ACME könnte dies bedeuten, dass es die automatische Skalierung nutzt, um sicherzustellen, dass sein Backend für Finanztransaktionen 1.000 gleichzeitige Transaktionen innerhalb einer Antwortzeit von 100 ms verarbeiten kann. Autoscaling kann uns zwar dabei helfen, unsere Verfügbarkeitsziele zu erreichen, ist jedoch auch mit Kosten verbunden, da für die Skalierung von Ressourcen jemand für die zusätzlichen Rechen- (CPU) oder Speicherressourcen aufkommen muss. Unsachgemäßes Autoscaling – zu starkes Hoch , kein Herunterskalieren oder Skalieren zum falschen Zeitpunkt – kann ebenfalls zu ungeplanten Kostenexplosionen führen, ohne dass das eigentliche Ziel des Autoscalings erreicht wird!

Wir wollen eine richtige automatische Skalierung. Wenn wir es richtig machen, können wir nicht nur unsere geschäftlichen und technischen Ziele erreichen, sondern auch die automatische Skalierung nutzen, um die Kosten unter Kontrolle zu halten. Werfen wir einen Blick auf einige Themen zur automatischen Skalierung, die Plattformingenieure kennen sollten, und darauf, was wir noch tun können, um die Kosten zu optimieren. Beachten Sie, dass einige der Praktiken, die wir in den folgenden Abschnitten besprechen werden, auch für jede Art von Workload gelten: ob Cloud oder nicht.

# Viele Facetten der automatischen Skalierung

Die Skalierbarkeit der Cloud und von Kubernetes als Kernplattform ist eine großartige Fähigkeit, über die Plattformingenieure verfügen sollten. Es gibt jedoch viele verschiedene Möglichkeiten der Skalierung. Es gibt verschiedene Auslösepunkte, die eine Skalierung des Systems bewirken können, und die Skalierung darf nicht nur in eine Richtung (in der Regel nach oben) erfolgen, sondern wir müssen auch eine Verkleinerung der Systeme in Betracht ziehen – sogar bis auf Null, um keine Ressourcen zu verschwenden!

# Skalierung nach oben – nicht nur bei CPU und Arbeitsspeicher

Die meisten Ingenieure sind mit der Skalierung auf Basis von CPU und Speicher vertraut. Die meisten Beispiele, die Sie für HPA finden, skalieren die Replikate von Pods in der Regel auf Basis einer bestimmten durchschnittlichen CPU-Auslastung dieses Pods. Das ist die gängigste Methode, die wir auch als reaktive Skalierung bezeichnen, da wir auf Basis einer erreichten Schwelle skalieren.

Eine Skalierung auf Basis von CPU oder Speicher ist jedoch nicht immer die beste Option. Es ist auch nicht die einzige, die wir haben, obwohl die meisten Skalierungsframeworks ursprünglich nur mit einer Skalierung auf Basis von CPU und Speicher begonnen haben, da dies die beiden wichtigsten Grenzen sind, die man für Pods oder Namespaces festlegen kann.

Für Dienste, die für einen bestimmten Durchsatz optimiert sind, wäre es beispielsweise sinnvoller, die Skalierung auf der Grundlage gleichzeitig eingehender Anfragen vorzunehmen. Auch für die CPU könnte es besser sein, Ihr System zu skalieren, wenn K8s beginnt, die CPU für einen Pod zu drosseln, anstatt die Skalierung auf der Grundlage der durchschnittlichen CPU-Auslastung vorzunehmen. Im vorigen Kapitel haben wir Tools wie KEDA sowie das Keptn-Projekt **der Cloud Native Computing Foundation** (**CNCF**) erwähnt, die beliebige Metriken aus verschiedenen Observability-Quellen (Prometheus, Dynatrace, Datadog, New Relic) für die ereignisgesteuerte automatische Skalierung bereitstellen können. Um zu sehen, wie dies funktioniert, sehen Sie sich ein vollständiges Beispiel in der Keptn-Dokumentation an: https://keptn.sh/stable/docs/use-cases/keda.

Die wichtigste Erkenntnis ist, dass nicht jede Workload CPU- oder speichergebunden ist und Kubernetes Sie nicht darauf beschränkt, Ihre Skalierungsregeln nur auf der Grundlage dieser beiden Schlüsselattribute zu definieren. Die Definition von Skalierungsregeln auf der Grundlage dessen, was Ihre Workload tatsächlich effizienter ausführen lässt, führt auch zu einer effizienteren Ressourcennutzung, was wiederum zu einem System führt, das auch hinsichtlich der Kosten optimiert ist!

# Prädiktive versus reaktive Skalierung

Oft wird angenommen, dass die automatische Skalierung sofort funktioniert. Das ist jedoch nicht der Fall! Denken Sie an das Finanzunternehmen ACME. Wenn am Zahltag alle ihren neuen Kontostand überprüfen möchten, kann dies innerhalb der ersten paar Stunden dieses Tages zu einem zehnfachen Anstieg des regulären Datenverkehrs führen. Der Cloud-Anbieter kann jedoch nicht garantieren, dass all diese Ressourcen sofort verfügbar sind, da Sie mit vielen anderen Unternehmen konkurrieren, die ebenfalls versuchen, gleichzeitig Cloud-Ressourcen anzufordern. Hinzu kommt, dass die Arbeitslast selbst nicht in der Lage ist, eingehende Anfragen sofort zu verarbeiten, da viele dieser Pods eine bestimmte Startzeit benötigen, bis sie einsatzbereit sind.

Dieses Problem kann durch vorausschauende Skalierung gelöst werden. Im Vergleich zur reaktiven Skalierung – also der Skalierung, wenn wir einen bestimmten Schwellenwert erreichen, wie im vorherigen Abschnitt erläutert – untersucht die vorausschauende Skalierung eine potenzielle zukünftige Situation und reagiert darauf, bevor ein Schwellenwert erreicht wird. Prädiktiv bedeutet nicht, dass wir eine magische Kristallkugel brauchen, um die Zukunft vorherzusagen. Es kann so einfach sein, wie die Skalierung ein paar Stunden vor dem erwarteten Anstieg des Datenverkehrs zu starten, beispielsweise kurz vor dem Zahltag oder vor einer Marketingkampagne, die zu einem bestimmten Zeitpunkt beginnt.

# Andere Vorhersagen können dynamischer sein:

- **Saisonalität**: Eine Prognose könnte auf der Saisonalität basieren, indem historische Daten herangezogen werden. E-Commerce ist ein gutes Beispiel dafür, wo es im Laufe des Jahres bestimmte Termine gibt, an denen es zu einem Anstieg der Auslastung kommt, wie beispielsweise Black Friday oder Cyber Monday. Diese Spitzen sind leicht vorherzusagen!
- **Verwandte Datenquellen**: Eine weitere Möglichkeit besteht darin, andere Datenquellen zu untersuchen. Versicherungsunternehmen werten häufig Daten zu Unwettern aus. Wenn Stürme vorhergesagt werden und eine gewisse Wahrscheinlichkeit besteht, dass diese Stürme Schäden verursachen, ist es sinnvoll, die Dienste, die diese Kunden zur Einreichung von Versicherungsansprüchen nutzen, vorausschauend zu skalieren. In diesem speziellen Szenario können Sie sogar bestimmte Regionen skalieren, die dem Sturm am nächsten liegen.
- **Systemabhängigkeiten**: In komplexen Systemen besteht auch die Möglichkeit, abhängige Komponenten auf der Grundlage des Auslastungsverhaltens anderer Teile des Systems zu skalieren. Nehmen wir das Gastgewerbe als Beispiel. Wenn wir feststellen, dass mehr Menschen nach Flügen suchen, weil sie ein langes Wochenende verreisen möchten, können wir auch Backend-Dienste vorausschauend skalieren, die Empfehlungen für Hotels, Autos oder zusätzliche Veranstaltungen am Reiseziel geben.

# Anwendungsfall – Vorausschauende Speicherskalierung zur Optimierung von Kosten und Verfügbarkeit

Nachdem wir nun verschiedene Ansätze zur prädiktiven Skalierung kennengelernt haben, wenden wir diese auf ein sehr kostspieliges Beispiel an: Speicher!

Unsere digitalen Systeme generieren mehr Daten als je zuvor, und es wird davon ausgegangen, dass sich dieser Trend fortsetzen wird. Speicherplatz – obwohl scheinbar in Hülle und Fülle verfügbar – ist für viele Unternehmen ein großer Kostenfaktor. Das Gleiche gilt für unser Unternehmen Financial One ACME, vorausgesetzt, wir müssen alle Details zu jeder Finanztransaktion speichern, die unsere Systeme verarbeiten. Als Unternehmen müssen wir sicherstellen, dass wir alle Datensätze jederzeit aufbewahren können, aber wir möchten auch sicherstellen, dass wir nicht für Speicherplatz bezahlen, den wir derzeit nicht benötigen. Daher möchten wir unseren freien Speicherplatz so gering wie möglich halten, um keine Kosten für nicht benötigte Festplatten zu verursachen. Andererseits müssen wir auch sicherstellen, dass wir über genügend freien Speicherplatz verfügen, falls es zu einem Anstieg der Transaktionen kommt, da wir es uns nicht leisten können, Transaktionen zu verlieren. Da eine Skalierung von Festplatten in großem Umfang nicht sofort erfolgen kann, sondern mehrere Stunden dauern kann, können wir eine vorausschauende Speicherskalierung anwenden, um alle unsere Anforderungen zu erfüllen!

Der folgende Screenshot veranschaulicht, wie dies funktioniert. Er zeigt die Metrik „Prozentualer freier Speicherplatz auf der Festplatte“ im Zeitverlauf. Je mehr Daten wir schreiben, desto weniger freier Speicherplatz steht zur Verfügung. Anstatt unseren Cloud-Speicher bei Erreichen eines bestimmten festen Schwellenwerts zu skalieren, können wir ein prädiktives Modell verwenden und skalieren, wenn wir vorhersagen, dass wir innerhalb des für die Skalierung erforderlichen Zeitraums einen bestimmten niedrigen Schwellenwert erreichen werden. So stellen wir sicher, dass wir immer über genügend freien Speicherplatz verfügen, ohne zu viel zu bezahlen:


<img width="1024" height="473" alt="image" src="https://github.com/user-attachments/assets/c0c2d8cc-700e-449e-aef7-5538f3aac12f" />


Abbildung 8.4: Vorausschauende Skalierung des Cloud-Speichers zur Optimierung von Kosten und Verfügbarkeit

Das vorstehende Beispiel stammt aus einem realen Anwendungsfall, bei dem durch die kontinuierliche Anpassung der Speichergröße mithilfe eines prädiktiven Skalierungsansatzes erhebliche Kosteneinsparungen erzielt wurden!


# Skalierung auf Null – Abschalten, wenn nicht benötigt

Während viele der von uns betriebenen Systeme rund um die Uhr verfügbar sein müssen, gilt diese Anforderung für einige Systeme nicht. Dabei kann es sich um Systeme handeln, die nur von Mitarbeitern während der regulären Geschäftszeiten genutzt werden, oder um Systeme, die nur zu bestimmten Tages-, Monats- oder Jahreszeiten für bestimmte Aufgaben benötigt werden. Wir alle kennen sicherlich Systeme, die oft ungenutzt sind, aber dennoch wertvolle Ressourcen verbrauchen und somit Kosten verursachen, obwohl sie derzeit nicht benötigt werden.

**Virtuelle Maschinen** (**VMs**) sind ein gutes Beispiel für die Skalierung auf Null. Wir machen das schon seit vielen Jahren, um Snapshots zu erstellen, VMs herunterzufahren, wenn sie nicht gebraucht werden, und sie wieder hochzufahren, wenn die Arbeit fortgesetzt werden muss. Viele Unternehmen haben dies vollständig automatisiert, indem sie VMs, die für tägliche Geschäftsaufgaben verwendet wurden, am Ende des Arbeitstages automatisch herunterfahren und am nächsten Morgen wieder hochfahren. Allein dies ist eine großartige Möglichkeit zur Kosteneinsparung, da viele VMs nachts und am Wochenende heruntergefahren werden können!

In Kubernetes haben wir ebenfalls die Möglichkeit, Workloads auf Null zu skalieren. Wir könnten das bereits erwähnte KEDA verwenden, aber auch Tools wie Knative (das serverlose Workloads ausführen kann) oder kube-green in Betracht ziehen. Letzteres wurde entwickelt, um den CO2-Fußabdruck von K8s-Workloads und -Clustern zu reduzieren, und ist in der Lage, Workloads, Knoten oder Cluster in den Ruhezustand zu versetzen , wenn sie nicht benötigt werden. Weitere Informationen zu kube-green finden Sie auf der folgenden Website: https://kube-green.dev/.

Eine Frage, die wir noch beantworten müssen, lautet: Welche Workloads können auf Null skaliert werden und für wie lange? Diese Daten erhalten wir von den Eigentümern dieser Workloads, indem wir angeben, wann und wie lange sie diese benötigen. Ein anderer Ansatz besteht darin, einfach Observability-Daten zu verwenden, um zu sehen, welche Workloads zu welchen Tageszeiten genutzt werden, und auf dieser Grundlage eine kube-green-Sleep-Konfiguration zu erstellen, um Workloads auf Null zu skalieren. Ein Beispiel für diese Implementierung finden Sie im Workshop „The Sustainability” von Henrik Rexed: https://github.com/henrikrexed/Sustainability-workshop.

# Von der Skalierung von Workloads zu Clustern

Bisher haben wir viel über die richtige Dimensionierung oder Skalierung von Workloads gesprochen, um sicherzustellen, dass wir über genügend Ressourcen verfügen, um unsere Geschäftsziele zu erreichen, aber auch, um keine Überkapazitäten zu schaffen, damit wir die Kosten optimieren können.

Wenn wir unsere Workloads nach oben oder unten skalieren, muss auch der zugrunde liegende Kubernetes-Cluster entsprechend dimensioniert werden. Hier kommt die automatische Skalierung von Clustern ins Spiel, die die Knoten eines Clusters nach oben skaliert, um sicherzustellen, dass genügend Ressourcen für die Ausführung aller Workloads zur Verfügung stehen, aber auch die Knoten nach unten skaliert, wenn sie nicht ausgelastet sind und die Workloads auf die verbleibenden Knoten verteilt werden können. Dadurch wird sichergestellt, dass die zugrunde liegenden Cluster-Knotenmaschinen optimiert sind, was letztendlich Kosten spart.

Auf der Kubernetes-Dokumentationswebsite finden Sie zahlreiche Informationen zu diesem Thema: https://kubernetes.io/docs/concepts/cluster-administration/cluster-autoscaling/.

Es gibt spezielle Autoscaler wie Karpenter – ursprünglich von AWS entwickelt –, die dabei helfen, einen Kubernetes-Cluster richtig zu skalieren und gleichzeitig die Kosten im Griff zu behalten. Karpenter lässt sich in die APIs Ihres Cloud-Anbieters integrieren und ist in der Lage, die richtige Größe der Knoten bereitzustellen, die für die Bewältigung einer bestimmten Workload erforderlich sind. Es skaliert auch Knoten herunter, wenn sie nicht mehr benötigt werden.

Neben Tools wie kube-green (bereits erwähnt) ist Karpenter eine hervorragende Option, um Ihre Cluster unter Berücksichtigung der Kosten zu skalieren. Weitere Informationen zu Karpenter finden Sie unter https://karpenter.sh/.

Als Plattformingenieure ist es wichtig, alle verschiedenen Skalierungsoptionen zu kennen. Viele davon können so eingerichtet werden, dass Workloads und Cluster richtig dimensioniert werden. Für einige ist es wichtig, eng mit den Engineering-Teams und den Workload-Eigentümern zusammenzuarbeiten, um Skalierungsstrategien zu definieren, die für diese spezifischen Workloads sinnvoll sind. Insgesamt ist die automatische Skalierung – egal ob es sich um Rechenleistung, Speicher oder Speicherplatz handelt – einer der wichtigsten Faktoren für eine kosteneffiziente Plattformentwicklung!

# Kostenbewusstes Engineering

Nachdem wir nun gelernt haben, was wir in unsere Plattformen integrieren können, um die richtige Größe zu finden und Kosten durch automatische Skalierung zu sparen, müssen wir auch darüber sprechen, was wir tun können, damit Engineering-Teams von Anfang an kostenbewusster arbeiten. Die beste Kostenoptimierung beginnt damit, dass sich jeder in einem Unternehmen der Kostenauswirkungen seiner Handlungen bewusst ist und daher von vornherein kosteneffizientere Systeme entwickelt und entwirft. Die Berichterstattung über Kosten auf der Grundlage von Tags ist eine Möglichkeit, Teams für ihre Kosten zu sensibilisieren. Diese Strategie wurde bereits weiter oben in diesem Kapitel erläutert.

Schauen wir uns einige zusätzliche Optionen an, die unserer Meinung nach jeder in Betracht ziehen sollte, da sie zu einem kostenbewussten Engineering führen können!

# Der Ansatz „Nur das, was Sie benötigen”

In den Anfängen der Cloud gewährten viele Unternehmen ihren Engineering-Teams uneingeschränkten Zugriff auf Cloud-Portale. Dieser einfache „Self-Service” steigerte die Produktivität, da jeder problemlos neue VMs einrichten, neue Speicherdienste erstellen oder sogar Kubernetes-Cluster erstellen konnte. Dieser „Wildwest”-Ansatz führte jedoch bei vielen Unternehmen zu Kostenexplosionen, da die Benutzer einfach neue Dienste einrichteten, ohne über grundlegende Fragen nachzudenken, wie z. B.: Wie groß muss meine virtuelle Umgebung wirklich sein und wie lange brauche ich sie?

Eine der Organisationen, mit denen die Autoren zusammengearbeitet haben, ist ein Finanzunternehmen. Anstatt allen Mitarbeitern uneingeschränkten Zugriff auf ihre Cloud-Portale zu gewähren, haben sie ein eigenes Self-Service-Portal eingerichtet, über das die Entwicklerteams neue VMs, Datenbanken, Cluster usw. erstellen können. Als Teil dieses Self-Service-Portals musste das Team definieren, für welche Anwendung und für welche Umgebung die Ressource benötigt wurde und wie lange diese Maschine benötigt wurde, beispielsweise nur während der Geschäftszeiten. Das Ergebnis war eine Kostenreduzierung von 60 %, da die bereitgestellten Dienste automatisch abgeschaltet wurden, wenn sie nicht mehr benötigt wurden. Der folgende Screenshot zeigt, wie Ingenieure Ressourcen für den Zeitraum anfordern, in dem sie diese benötigen. Auf der rechten Seite sehen Sie außerdem die detaillierten Berichte und das Gesamtoptimierungsziel, das diese Organisation erreicht:


<img width="1001" height="464" alt="image" src="https://github.com/user-attachments/assets/f631dce2-c8b9-44f1-af14-c23188e7507c" />

Abbildung 8.5: Eine Self-Service-Plattform, die Kosten meldet und reduziert

Die Berichterstattung in diesem Anwendungsfall bezog sich nicht nur auf die Kosten, sondern auch auf die CO2-Bilanz, die heutzutage für die meisten Unternehmen ein wichtiges Thema ist. Durch die Bereitstellung dieses Self-Service über eine zentrale Plattform war es für dieses Unternehmen einfach, seinen Ingenieuren von Anfang an ein stärkeres Kostenbewusstsein zu vermitteln und ihnen auch die positiven Auswirkungen ihres Handelns aufzuzeigen.

# Leasing versus Pauschalpreis für Ressourcen

Das vorherige Beispiel ist großartig, erfordert jedoch, dass die Teams im Voraus genau überlegen, wie lange und wann sie bestimmte Ressourcen benötigen. Ein anderer Ansatz wäre die Verwendung eines **Leasingmodells**. Was bedeutet das?

Wenn das Entwicklerteam A eine Ressource anfordert – beispielsweise einen Kubernetes-Cluster, den es für bestimmte Entwicklungsarbeiten benötigt –, kann es diese einfach für einen Standardzeitraum anfordern, beispielsweise für eine Woche. Dieser Zeitraum von einer Woche wird dann zum „ursprünglichen Leasingzeitraum” für diese Ressource. Sowohl der Zeitraum als auch die Teamzugehörigkeit werden über Tags für die erstellte Ressource verwaltet. Durch Automatisierung können 1 Tag vor Ablauf des Leasingvertrags E-Mails oder Chat-Nachrichten an die Teams gesendet werden, um sie daran zu erinnern, dass ihr Leasingvertrag bald ausläuft. Die Nachricht kann ihnen auch die Möglichkeit bieten, den Leasingvertrag um einen weiteren Tag oder eine weitere Woche zu verlängern, sie aber auch an die Kosten erinnern, die durch diese zusätzliche Zeit entstehen würden.

Dieser Ansatz wurde in mehreren Organisationen umgesetzt und stellt sicher, dass jedes Team weiterhin die benötigten Ressourcen über Self-Service erhalten kann. Außerdem wird so sichergestellt, dass „ “-Ressourcen, die vergessen wurden oder nicht mehr benötigt werden, abgeschaltet werden, ohne dass im Voraus genau angegeben werden muss, wie lange eine Ressource benötigt wird.

Nachdem wir nun darüber gesprochen haben, wie Ressourcen nur dann ausgeführt werden können, wenn sie wirklich benötigt werden, um Kosten zu sparen, wollen wir uns damit befassen, wie Ingenieure auch ihren Code optimieren können, um Kosten zu senken!

# Green Engineering – Optimierung Ihres Codes

Effizienter Code wird in der Regel nicht nur schneller ausgeführt, sondern benötigt auch weniger CPU, Speicher und möglicherweise weniger Festplattenspeicher oder Netzwerkbandbreite. Weniger von allem bedeutet auch weniger Kosten. Warum erstellt dann nicht jeder von Anfang an effizienten Code?

Allzu oft stehen Ingenieure unter Zeitdruck, neue Funktionen zu liefern, oder Unternehmen haben nicht in Tools investiert, die im Rahmen des Software-Lieferzyklus Tests durchführen und Optimierungsempfehlungen geben. Die Autoren haben in der Vergangenheit mit vielen Softwareunternehmen zusammengearbeitet und eine Reihe sehr häufiger Muster identifiziert, die zu ineffizientem und damit kostspieligem Code führen. Hier sind einige Beispiele:

- **Anforderung zu vieler Daten**: Anstatt Abfragesprachen zu nutzen, um nur die für einen bestimmten Vorgang benötigten Daten anzufordern, werden mehr Daten abgerufen und dann im Speicher gefiltert und verarbeitet. Dies führt zu mehr Netzwerkverkehr für die Übertragung der Daten, mehr Speicherverbrauch für die Speicherung der Daten und mehr CPU-Leistung für die Iteration und Filterung im Client-Code.
- **Ineffiziente Nutzung von Bibliotheken oder Algorithmen**: Es gibt viele Softwarebibliotheken, um bestimmte Aufgaben zu erledigen, z. B. **Object Relational Mappers** (**ORMs**), um Daten in Datenbanken Objekten in einer Entwicklungssprache zuzuordnen. Leider haben Entwicklungsteams nicht immer die Zeit, diese Bibliotheken ordnungsgemäß zu testen oder zu konfigurieren, um sie für ihren spezifischen Anwendungsfall zu optimieren. Dies führt daher zu einer ineffizienten Nutzung, was wiederum zu einem höheren CPU-, Speicher-, Netzwerk- und Festplattenzugriff führt.
- **Übermäßige Protokollierung**: Softwareentwickler verwenden Protokollierungsframeworks, um Informationen während der Ausführung ihres Codes zu protokollieren. Protokolle werden in der Regel für Analysen, Diagnosen und die Fehlerbehebung bei fehlgeschlagenen oder problematischen Codeausführungen benötigt. Allzu oft werden Protokolle jedoch übermäßig erstellt oder dupliziert, ohne dass sie ordnungsgemäß formatiert sind oder ausreichende Kontextinformationen enthalten, z. B. wenn keine Protokollebenen festgelegt sind. Dies führt zu einem Mehraufwand bei der Erstellung der Protokolle, aber auch bei der Erfassung, Transformation und Analyse dieser Protokolle durch Observability-Plattformen.

Es gibt viele weitere Muster in der Softwareentwicklung, die zu Leistungs- oder Skalierbarkeitsproblemen führen. Neben der Erkennung von Mustern können Architekturüberprüfungen für Anwendungen auch zu Kostensenkungen durch effizientere Architekturen oder umgeschriebenen Code führen. Ein prominentes Beispiel ist Amazon Prime Video, das seine verteilte serverlose AWS-Architektur aufgegeben und für seine Videoqualitätsanalyse auf eine sogenannte Monolith-Architektur umgestellt hat, wodurch die Infrastrukturkosten um 90 % gesenkt werden konnten \[4\]. Letztendlich bedeuten diese Muster auch eine ineffiziente Codeausführung, was zu höheren Kosten führt. Als Plattform-Engineering-Teams haben wir die Möglichkeit, diese Muster mit modernen Observability-Tools zu analysieren und diese Informationen an die Ingenieure zurückzugeben, um sie nicht nur auf die Kosten hinzuweisen, die ihnen durch ihren Code entstehen, sondern auch darauf, wo sie mit der Optimierung beginnen können, wie im nächsten Screenshot gezeigt. Diese beiden Diagramme zeigen, wie viele Protokolle pro Dienst erstellt werden, und heben auch hervor, welche Protokolle nicht richtig konfiguriert sind, z. B. wenn keine Protokollebenen festgelegt sind:


<img width="1030" height="423" alt="image" src="https://github.com/user-attachments/assets/a7682926-0dcd-47de-8b77-cc85bb682192" />

Abbildung 8.6: Teams einfache Einblicke in Muster wie übermäßige Protokollierung geben

Dies bringt mich zum letzten Teil dieses Abschnitts, nämlich der Möglichkeit, Ingenieure zu schulen und ihnen von der ersten Zeile Code an ein Kostenbewusstsein zu vermitteln!

# Die Möglichkeit zur Schulung

Auch wenn dies vielleicht nicht als eine der wichtigsten Aufgaben eines Plattform-Engineering-Teams angesehen wird, da Engineering-Teams unsere Plattformen nutzen, um ihre Anwendungen als Self-Service bereitzustellen, können wir v diese Plattform auch nutzen, um alle über die Kostenauswirkungen aufzuklären, die sie haben, wenn sie die Plattform nutzen, um ihre Software-Services bereitzustellen.

In den vorangegangenen Abschnitten haben wir bereits Anwendungsfälle wie das Senden von Kosten- und Nutzungsberichten an Engineering-Teams oder das Identifizieren und Hervorheben ineffizienter Codemuster hervorgehoben. Der Schlüssel dazu ist eine ordnungsgemäße Kennzeichnung (z. B. wer ist für welchen Teil der Infrastruktur und Anwendungen verantwortlich) sowie eine gute Beobachtbarkeit (z. B. welche Systeme wie viel CPU, Speicher, Netzwerk usw. nutzen). Mit diesen Informationen können die Plattform-Entwicklungsteams diese Daten proaktiv an die Teams weitergeben und ihnen so kontinuierlich zeigen, welche Kostenauswirkungen ihre Anwendungen haben. Dies führt auch zu einem Lerneffekt, der dazu beiträgt, dass die Entwickler von vornherein ein besseres Verständnis für die Kostenauswirkungen ihrer Handlungen haben.

# Zusammenfassung

In diesem Kapitel sollten Sie ein Gefühl für die Kosten entwickelt und Ideen dazu gewonnen haben, wie Sie dieses Thema auf Ihrer Plattform angehen können. Gute Plattformen bieten ihren Nutzern Transparenz und ermöglichen die Verwendung flexibler Optionen, um ihre Arbeitslast für verschiedene Auslöser anzupassen. An dieser Stelle sollten Sie in der Lage sein, die in den vorherigen Kapiteln erlernten Ansätze, wie z. B. die dynamische Ressourcenzuweisung mit GPUs, zu kombinieren, um eine hohe Auslastung und eine optimale Kostenverteilung zu erreichen.

Denken Sie daran, dass die Kostenperspektive allein nicht ausreicht, um die Gesamtkosten der Plattform zu senken, da eine Verringerung der Servergröße aufgrund anderer Einschränkungen der Cloud-Anbieter zu einer erhöhten Nachfrage nach mehreren kleinen Servern führen kann. Eine Tagging-Strategie bildet den Kern für Kontrolle und Transparenz. Was einfach klingt, kann zu vielen organisatorischen Diskussionen führen. Um Ihre Kosten zu optimieren, können Sie auch andere Elemente wie Prozesse nutzen und langfristige Verpflichtungen vereinbaren, um bessere Preisangebote zu erhalten.

Abschließend haben wir Ihnen einige praktische Beispiele und Best Practices für Ihre Plattform vorgestellt. Wir haben uns mit den verschiedenen Ansätzen der Skalierung und dem Unterschied zwischen prädiktiver und reaktiver Skalierung befasst und neben der CPU auch andere Skalierungsfaktoren wie Arbeitsspeicher und Speicher beleuchtet.

Zusammenfassend lässt sich sagen: Wenn Sie rational denken und das Geld, das Sie für die Plattform ausgeben, wie Ihr eigenes behandeln, können Sie sehr kosteneffizient werden. Als Plattform-Engineering-Team könnten Sie auch eine Metrik entwickeln, um die Effizienz der Plattform zu definieren, damit Sie sich mit Ihrem Management darauf einigen können, dieses freie Budget für weitere Investitionen und Optimierungen zu verwenden. Denken Sie daran, dass uns die Cloud zwar unbegrenzte Ressourcen zur Verfügung stellt, wir diese aber nicht alle in Anspruch nehmen müssen, nur weil sie vorhanden sind.

Kommen wir nun direkt zum letzten Kapitel. Wie bereits erwähnt, ist die einzige Konstante die Unbeständigkeit. In unserem letzten Kapitel werden wir daher über den kontinuierlichen Wandel und wie man ihn übersteht sprechen, wobei wir uns mit leichtgewichtigen Architekturen befassen, die von nachhaltigen Ideen motiviert sind, sowie mit dem goldenen Weg für Veränderungen. Zum Abschluss des Kapitels wagen wir einen Blick in die Kristallkugel und behandeln einige technologische Trends, die in den nächsten Jahren relevant werden könnten oder auch nicht.Weiter[Chap 9](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap9/Platform%20Engineering_9%20de.md)

# Weiterführende Literatur

- \[1\] Warum wir die Cloud verlassen haben – David Heinemeier Hansson:
    - https://world.hey.com/dhh/we-have-left-the-cloud-251760fb
    - https://world.hey.com/dhh/the-hardware-we-need-for-our-cloud-exit-has-arrived-99d66966
- \[2\] FinOps Framework-Poster in hoher Auflösung: https://www.finops.org/wp-content/uploads/2024/03/FinOps-Framework-Poster-v4.pdf
- \[3\] Cloud Custodian: https://cloudcustodian.io/
- \[4\] Prime Video-Kostenoptimierung: https://www.thestack.technology/amazon-prime-video-microservices-monolith/
