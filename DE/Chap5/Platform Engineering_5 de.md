Integration, Bereitstellung und Implementierung – Automatisierung ist allgegenwärtig

[Kapitel 2](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap2/Platform%20Engineering_2%20de.md) enthielt eine Referenzarchitektur einer Plattform, in der Schichten wie Entwicklererfahrung, Automatisierung und Orchestrierung sowie Beobachtbarkeit hervorgehoben wurden. [Kapitel 3](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap3/Platform%20Engineering_3%20de.md) endete mit einer anderen Perspektive auf diese Referenzarchitektur unter Verwendung eines Top-Down-Ansatzes aus Zweck, Benutzeroberfläche, Kernplattformkomponenten, Plattform als Produkt und Erfolgskennzahlen.

Die meisten Plattformen werden mit dem Ziel entwickelt, es Entwicklungsteams zu erleichtern, Software auszuliefern, ohne sich mit der Komplexität der Erstellung, Bereitstellung, Prüfung, Validierung, Sicherung, des Betriebs, der Veröffentlichung oder der Skalierung von Software auseinandersetzen zu müssen. In diesem Kapitel werden wir uns eingehend mit diesen Ebenen und Komponenten unserer Plattform befassen, um zu verstehen, wie wir das für die Auslieferung von Software erforderliche Fachwissen zentralisieren und automatisieren und als Self-Service bereitstellen können.

Am Ende dieses Kapitels werden wir gelernt haben, wie man einen End-to-End-Release-Prozess für Software-Artefakte definiert, den **Continuous Integration/Continuous Deployment** (**CI/CD**)-Prozess an die Phasen des Artefakt-Lebenszyklus anpasst, die Phasen mit Tools für CI, CD und Continuous Release automatisiert, diese Tools in Ihren bestehenden Prozess integriert, die Automatisierung beobachtet und über ein IDP skaliert.

Daher werden wir in diesem Kapitel die folgenden Hauptthemen behandeln:

- Eine Einführung in Continuous X
- GitOps: Vom Pushen zum Pulling des gewünschten Zustands
- Die Bedeutung von Container- und Artefakt-Registrys als Einstiegspunkte verstehen
- Definition des Release-Prozesses und -Managements
- Erreichen einer nachhaltigen CI/CD für DevOps – Orchestrierung des Anwendungslebenszyklus
- **Interne Entwicklerplattformen** (**IDPs**) – die Automatisierung Kraken in der Plattform

Eine Einführung in Continuous X

Wenn Sie zum ersten Mal von **Continuous Integration** (**CI**) oder **Continuous Delivery** (**CD**) hören, empfehlen wir Ihnen, sich mit der hervorragenden Literatur zu diesen Grundkonzepten vertraut zu machen. Jez Humble ist der Betreuer von https://continuousdelivery.com/ und hat zusammen mit Dave Farley das Originalbuch zu Continuous Delivery verfasst. Wenn Sie einen Crashkurs zu diesem Thema benötigen, schauen Sie sich bitte deren Material an. Es gibt auch mehrere aufgezeichnete Vorträge, die einen guten Überblick bieten, wie beispielsweise der Vortrag mit dem Titel „Continuous Delivery Sounds Great But It Won't Work Here” (Kontinuierliche Bereitstellung klingt großartig, aber hier wird es nicht funktionieren): https://vimeo.com/193849732.

Damit wir alle dasselbe Verständnis haben, lassen Sie uns kurz zusammenfassen, was die Bausteine sind und warum dies für die Softwarebereitstellung wichtig ist.

Allgemeine Definition von Continuous X

Die Grundlage für die Automatisierung der Softwarebereitstellung ist ein ordnungsgemäßes Konfigurationsmanagement aller Ressourcen, die für die Erstellung, Bereitstellung, Validierung, den Betrieb und die Skalierung unserer Systeme erforderlich sind: Code, Tests, Bereitstellungs- und Infrastrukturdefinitionen, Abhängigkeiten, Beobachtbarkeit, Eigentumsverhältnisse und mehr. Durch die Versionierung all dieser Ressourcen können wir wiederholbare und zuverlässige Ergebnisse erzielen, haben die Möglichkeit zur Überprüfung, können schwerwiegende Änderungen rückgängig machen und verfügen über Disaster-Recovery-Funktionen.

Git oder eine beliebige Variante von Git ist wahrscheinlich das, was heute in Softwareunternehmen für die Versionskontrolle verwendet wird. Je nach der von Ihnen verwendeten Git-Lösung stehen Ihnen zusätzliche integrierte Funktionen zur Verfügung, wie z. B. teamübergreifende Zusammenarbeit (Problemverfolgung, Lösung von Merge-Konflikten usw.), Automatisierung (Commit-Prüfungen, Bereitstellungspipelines usw.) oder Berichterstellung (Effizienz- oder DORA-Metriken).

Nachdem wir nun die Grundlagen geschaffen haben, wollen wir uns mit Continuous X befassen.

CI

**CI** ist eine Methode, bei der der Schwerpunkt auf der häufigen und automatisierten Integration von Codeänderungen in ein gemeinsames Repository liegt. Wenn mehrere Entwickler an derselben Codebasis arbeiten, ist es wichtig, diese Änderungen regelmäßig zusammenzuführen, um sicherzustellen, dass der Code gut integriert ist und ein Artefakt (ein Container-Image, eine Binärdatei) erzeugt, das in einer Umgebung bereitgestellt werden kann. Zu den wichtigsten Aspekten von CI gehören die folgenden:

- **Automatisierte Builds**: Code-Commits in der Versionskontrolle lösen einen automatisierten Build-Prozess aus, der kompiliert, Tests ausführt und Artefakte generiert.
- **Testautomatisierung**: Während des Build-Prozesses werden Unit-Tests, Integrationstests und andere Prüfungen durchgeführt, wobei der Build als fehlerhaft markiert wird, wenn einer der Tests fehlschlägt.
- **Feedback-Schleife**: Diese bietet Entwicklern schnelles Feedback, um Probleme rasch zu beheben, was zu einer insgesamt höheren Codequalität und -stabilität führt.

Kontinuierliche Tests und Validierung der Beobachtbarkeit

Während CI bereits die Bedeutung automatisierter Unit- und Integrationstests hervorhebt, möchten wir betonen, dass mehr automatisierte Tests und Validierungen in einer frühen Phase des Lebenszyklus zu einer besseren Qualität und Stabilität führen. Angenommen, die gebaute Software bietet REST-APIs oder eine Benutzeroberfläche, sollte eine grundlegende Validierung dieser Schnittstellen durchgeführt werden, um die korrekte Funktionalität zu überprüfen (z. B. geben APIs die richtigen Antworten zurück, werden beim Testen mit ungültigen Parametern die richtigen HTTP-Statuscodes verwendet, gibt es Zeitüberschreitungen bei API-Aufrufen oder werden HTTP-Fehler zurückgegeben?

**Die Beobachtbarkeit** ist unerlässlich, um zu überprüfen, ob die Systeme fehlerfrei sind, und liefert die Daten, um Probleme schneller zu beheben. Als Teil des kontinuierlichen Validierungsprozesses müssen wir überprüfen, ob der getestete Build gültige und erwartete Beobachtbarkeitsdaten liefert. Wir sollten überprüfen, ob alle erwarteten Metriken, Protokolle oder Traces erzeugt werden und ob nach der Ausführung dieser grundlegenden Unit-, Integrations- oder API-Tests keine offensichtlichen Anomalien oder Ausreißer vorhanden sind.

Wir haben immer wieder betont, dass Beobachtbarkeit eine nicht-funktionale Anforderung an moderne Software sein muss. Aus diesem Grund sollte die CI bereits überprüfen, ob die erwarteten Daten erzeugt werden. Ist dies nicht der Fall, entspricht dies einem fehlgeschlagenen Unit- oder Integrationstest, und Sie sollten den Build als fehlerhaft markieren!

Für Financial One ACME und seine kritischen Finanzdienstleistungen sollten wir Folgendes überprüfen:

- Wird die API die Zugriffskontrolle des Aufrufenden ordnungsgemäß validieren (z. B. keine Abfrage von Finanzdaten anderer Benutzer)?
- Protokolliert die API keine vertraulichen Daten wie Kreditkartennummern, Benutzernamen oder Tokens?
- Generiert die API ordnungsgemäß Metriken für fehlgeschlagene Versuche, sodass diese in der Produktion verwendet werden können, um vor potenziellen Hackerangriffen zu warnen?

Kontinuierliche Bereitstellung

Wie auf der Website zu Continuous Delivery (https://continuousdelivery.com/) definiert, ist „Continuous Delivery die Fähigkeit, Änderungen aller Art – einschließlich neuer Funktionen, Konfigurationsänderungen, Fehlerbehebungen und Experimente – sicher, schnell und nachhaltig in die Produktion oder in die Hände der Benutzer zu bringen“. Das Ziel besteht darin, die Angst vor Fehlschlägen bei Bereitstellungen zu beseitigen. Anstelle von seltenen Big-Bang-Releases sollten Bereitstellungen zur Routine werden, da sie kontinuierlich erfolgen. Darüber hinaus können wir das Risiko durch die Anwendung neuer Bereitstellungsmuster wie Blue/Green, Canary oder Feature Flagging noch weiter reduzieren. Diese werden im Abschnitt über Bereitstellungen im Vergleich zu Releases näher erläutert!

Einige Aspekte der kontinuierlichen Bereitstellung sind wie folgt:

- **Automatisierte Bereitstellungen**: Neue Artefakte, die aus CI hervorgehen, werden mit anderen Änderungen gebündelt und automatisch bereitgestellt. Bereitstellungsdefinitionen sind deklarativ und versionskontrolliert und ermöglichen daher eine besser vorhersehbare, wiederholbare und risikoarme Art der Aktualisierung in jeder Umgebung.
- **Bereitstellungspipelines**: Pipelines ermöglichen im Vergleich zu CI Tests und Validierungen der Bereitstellung auf höherer Ebene. Hier werden Tests hinsichtlich Leistung, Sicherheit, Skalierbarkeit, Ausfallsicherheit und Benutzererfahrung durchgeführt. Dabei wird nicht nur ein einzelnes Artefakt validiert, sondern der gesamte Satz an Bereitstellungsänderungen!
- **Qualitätskontrollen und Freigabe**: Am Ende einer Bereitstellungspipeline dienen alle Testergebnisse als Qualitätskontrolle, bevor die Änderung in die nächste Umgebung übernommen wird: von der Entwicklung zur **Qualitätssicherung** (**QA**), von der QA zur Staging-Umgebung, von der Staging-Umgebung zur Produktion.
- **Rollback versus Rollforward**: Wenn das Qualitätsgate in der Produktion fehlschlägt, kann ein Rollback ausgelöst werden, indem auf die vorherige versionskontrollierte Bereitstellungskonfiguration zurückgegriffen wird. Eine andere Strategie ist das Rollforward, bei dem Probleme behoben werden und dank automatisierter Bereitstellungen die Korrektur schnell bereitgestellt werden kann, um ein Rollback zu vermeiden.

Kontinuierliche Bereitstellungen – Entkopplung von Bereitstellungen und Releases

CD stellt Änderungen automatisiert und schnell bereit. Es besteht jedoch weiterhin das Risiko, dass eine Änderung zu einem Fehler führt, der entweder ein Rollback oder ein Rollforward erforderlich macht, wie zuvor erläutert.

Kontinuierliche Bereitstellungen gehen noch einen Schritt weiter und nutzen neue Bereitstellungsmuster, die die Trennung der Bereitstellung einer Änderung und der Freigabe der neuen Funktionen für die Endbenutzer begünstigen. Die derzeit etablierten Muster sind wie folgt:

- **Blue/Green-Bereitstellungen**: Die neue Bereitstellung (üblicherweise als „blau” bezeichnet) erfolgt parallel zur bestehenden Bereitstellung (üblicherweise als „grün” bezeichnet). Über einen Load Balancer kann der Datenverkehr auf „blau” umgeschaltet werden. Wenn es ein Problem mit „blau” gibt, kann der Datenverkehr zurück auf die noch laufende Instanz umgeschaltet werden, wodurch ein Rollback überflüssig wird und die Auswirkungen auf den Endbenutzer minimiert werden. Wenn alles gut läuft, wird „grün” zu „blau”, bis die nächste Bereitstellung erfolgt.
- **Canary-Bereitstellungen**: Ähnlich wie Blau/Grün-Bereitstellungen, jedoch auf einer granulareren Ebene. Dabei handelt es sich um die schrittweise Bereitstellung der neuen Version neben der alten Version. Zunächst wird sie für eine kleine Untergruppe von Benutzern oder einen Prozentsatz des Datenverkehrs bereitgestellt. Wenn alles gut läuft, wird die schrittweise Einführung fortgesetzt, bis der gesamte Benutzerdatenverkehr die neue Version hat. Wenn während der einzelnen Phasen ein Problem auftritt, wird der Datenverkehr an die alte Version weitergeleitet.
- **Feature Flagging**: Anstelle einer lastverteilten parallelen Bereitstellung der alten und neuen Version ermöglicht Feature Flagging den Entwicklern, neuen Code hinter einem Schalter/Umschalter zu „verstecken”. Während einer Bereitstellung wird die neue Version über die alte Version gestellt, ohne den neuen versteckten Code auszuführen. Durch eine detaillierte Konfiguration können Funktionen für einzelne Benutzer, Benutzertypen, geografische Regionen oder andere Attribute eines Dienstnutzers aktiviert werden. Wenn eine Funktion ein Problem aufweist, ist lediglich eine Änderung der Laufzeitkonfiguration erforderlich, und der Code wird wieder inaktiv.

Durch die Entkopplung von Bereitstellungen und Releases können Teams die Einführung neuer Funktionen ihrer Software besser steuern und damit Risiken minimieren. Es gibt noch mehr über die Implementierungsdetails und Herausforderungen zu erklären, aber das würde den Rahmen dieses Buches sprengen. Wenn Sie mehr erfahren möchten, schauen Sie sich OpenFeature \[1\] an, ein Inkubationsprojekt der **Cloud Native Computing Foundation** (**CNCF**). OpenFeature bietet Entwicklern eine standardisierte, herstellerunabhängige Methode zur Verwaltung von Feature-Flags. Die Community rund um OpenFeature verfügt auch über viele Best Practices für die progressive Bereitstellung, darunter alle zuvor besprochenen Muster.

Continuous X für die Infrastruktur

Continuous X ist nicht nur für Anwendungscode oder Konfigurationen relevant. Die gleichen Konzepte sollten auf jede Infrastrukturdefinition angewendet werden. Als Plattform benötigen wir bestimmte Infrastrukturkomponenten. Dabei kann es sich um virtuelle Maschinen, Kubernetes-Knoten, Load Balancer, **Domain Name System** (**DNS**), Dateispeicher, Datenbanken, virtuelle Netzwerke, Serverless oder andere Komponenten handeln, die es uns ermöglichen, unsere Kernplattform sowie die Anwendungen zu betreiben, die über unsere Plattform-Self-Services bereitgestellt, betrieben und verwaltet werden.

Genau wie beim Anwendungscode möchten wir unsere Infrastrukturanforderungen als Code konfigurieren, sie versionskontrollieren und die gleichen CI- und kontinuierlichen Tests, Validierungen und Bereitstellungen anwenden.

**GitOps** ist ebenfalls ein Begriff, der in den letzten Jahren aufgekommen ist und sich auf die Automatisierung des Prozesses der Bereitstellung von Infrastruktur aus einem gewünschten Zustand konzentriert, der deklarativ definiert und in Git versionskontrolliert ist. Wir werden GitOps in einem späteren Abschnitt dieses Kapitels näher behandeln. Lassen Sie uns zunächst die Grundlagen besprechen, beginnend mit **Infrastructure as Code** (**IaC**).

**IaC**

Es gibt viele verschiedene Tools, die **IaC** ermöglichen, und höchstwahrscheinlich verfügen Sie in Ihrem Unternehmen bereits über eines oder mehrere davon: Terraform, Ansible, Puppet, Chef, CloudFormation und **AWS Cloud Development Kit** (**CDK**), um nur einige zu nennen.

Hier ist ein sehr einfacher Terraform-Ausschnitt, der eine EC2-Instanz vom Typ c5.large erstellen würde:

resource "aws_instance" "finoneacme_demoserver" {

&nbsp; ami = "ami-01e815680a0bbe597"

&nbsp; instance_type = "c5.large"

&nbsp; Tags = {

&nbsp;   Name = "IaCTFExample"

&nbsp; }

}

KopierenErklären

Hier ist ein weiteres Beispiel für die Erstellung eines AWS S3-Buckets mit Ansible:

\- name: Bereitstellung eines S3-Buckets mit Ansible-Playbook

&nbsp;  hosts: localhost

&nbsp;  Verbindung: lokal

&nbsp;  gather_facts: false

&nbsp;  tags: Bereitstellung

&nbsp;  Aufgaben:

&nbsp;    - Name: S3-Bucket erstellen

&nbsp;      S3_bucket:

&nbsp;        name: finoneacme_bucket_dev

&nbsp;        Region: us-east-1

&nbsp;        Versionierung: ja

&nbsp;        Tags:

&nbsp;          name: bucketenv

&nbsp;          Typ: dev

KopierenErklären

Mit IaC können wir den gewünschten Zustand unserer IaC definieren. Dabei handelt es sich um Code, der versionskontrolliert werden kann, wie beispielsweise Anwendungscode, und der nach der Bereitstellung zur Bereitstellung der gewünschten Infrastruktur führt. Wie bei Anwendungscode können wir Folgendes verwenden:

- **CI**: Verwenden Sie dies, um zu überprüfen, ob unser gesamtes IaC gültig ist. IaC-Tools verfügen in der Regel über Funktionen zum „Trockenlauf“ und zur Überprüfung, ob keine Fehler vorliegen und alle Konfigurationsdateien keine Konflikte oder Abhängigkeitsprobleme aufweisen.
- **Testen und Validieren der Bereitstellung**: Nach der Bereitstellung von IaC können wir überprüfen, ob wir wirklich den gewünschten Zustand erreicht haben (z. B. sicherstellen, dass die EC2-Instanz wirklich läuft, dass die S3-Buckets zugänglich sind usw.).
- **Rollback oder Rückgängigmachen**: IaC bietet uns die Möglichkeit, Änderungen rückgängig zu machen oder zu einer früheren Version zurückzukehren, da alles versionskontrolliert ist!

Für weitere Details zu IaC, einschließlich Versionskontrollstrategien (wo IaC angesiedelt ist), empfehlen die Autoren, sich bestehende Bücher und Blogs zu diesem Thema anzusehen.

Crossplane – IaC für Plattformen und Anwendungen

IaC ist nicht auf die Kernplattformdienste beschränkt, sondern auch für die Anwendungen relevant, die unsere Entwicklungsteams über unsere Plattform-Self-Services bereitstellen dürfen. Eine neue Anwendung benötigt möglicherweise Dateispeicher, eine Datenbank und ein öffentliches DNS oder muss eine Drittanbieterlösung bereitstellen; dies hängt von ihrer eigenen virtuellen Maschine ab, auf die von der bereitgestellten Anwendung aus zugegriffen werden kann, die sich möglicherweise auf K8s befindet.

Sie können Vorlagen für Terraform, Ansible und CDK bereitstellen, die Ihre Entwickler zu ihren eigenen Code-Repositorys hinzufügen können und die dann als Teil des Continuous X ihrer Anwendung angewendet werden.

Ein Tool, das im Cloud-Native-Bereich entstanden ist, um sowohl die Anwendungs- als auch die Infrastruktur-Orchestrierung abzudecken, ist das **CNCF-Projekt Crossplane** \[2\]. Es umfasst nicht nur viele verschiedene Anbieter für alle großen Cloud-Anbieter oder sogar Terraform, sondern auch Compositions. **Compositions** sind Vorlagen zum Erstellen mehrerer verwalteter Ressourcen als ein einziges Objekt. Auf diese Weise kann das Plattformteam solche Vorlagen für gängige Anwendungsarchitekturen definieren, und das Anwendungsteam kann diese Vorlage dann einfach verwenden, um die richtige Infrastruktur zu instanziieren und die Anwendung bereitzustellen.

Einer unserer in [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) diskutierten Self-Service-Anwendungsfälle war die automatisierte Bereitstellung einer Leistungstestumgebung. Wir könnten eine Composition definieren, die für die Entwicklungsteams genauso einfach zu verwenden wäre wie die in diesem Beispiel gezeigte:

apiVersion: composites.financialone.acme/v1alpha1

kind: PerformanceTestCluster

metadata:

&nbsp; name: ptest-devteam1

spec:

&nbsp; clusterSize: „medium“

&nbsp; Zielanwendung:

&nbsp;   repoUrl: „https://financialone.acme/our-app-repo”

&nbsp;   Zielrevision: „2.5.1”

&nbsp;   Diagramm: „ourapp”

&nbsp; Lastprofil: „Spike-Last“

&nbsp; Beobachtbarkeit: true

&nbsp; notifySlackOnReady: "#devteam1"

&nbsp; Mietdauer: „12 Stunden”

CopyExplain

Die Kompositionsdefinition von PerformanceTestCluster wurde vom Plattform-Engineering-Team in Zusammenarbeit mit Experten erstellt, die sich mit der Installation von Lasttest- und Beobachtungstools auskennen. Im vorangegangenen Beispiel würde ein neuer mittelgroßer K8s-Cluster bereitgestellt, die angeforderte App würde mithilfe des referenzierten Helm-Charts installiert, Observability-Daten würden erfasst (z. B. Prometheus und Log-Scraping konfiguriert) und das Lasttest-Tool würde bereitgestellt, um Spike-Last-Szenarien ausführen zu können. Sobald alles bereit ist, wird eine Slack-Benachrichtigung mit den Umgebungsdetails an das Team gesendet. Zu guter Letzt würde die Umgebung nach 12 Stunden, wie im obligatorischen Feld „leaseTime“ angegeben, heruntergefahren werden.

Das vorstehende Beispiel zeigt bereits die Leistungsfähigkeit von IaC, wenn wir dies in unsere Continuous X-Bemühungen integrieren!

Continuous X als systemkritische Komponente unserer Plattform

Es gibt viele verschiedene Tools, aus denen wir wählen können, um Continuous X zu implementieren: Jenkins, GitLab, Tekton, Argo CD, Flux, Keptn, Crossplane, Selenium und k6, um nur einige zu nennen. Unabhängig davon, für welche Tools wir uns entscheiden, müssen diese Tools jederzeit verfügbar, widerstandsfähig und sicher sein, da sie das Rückgrat unserer Plattform bilden. Diese Tools sind genauso geschäftskritisch wie jede andere Software, die unser Geschäft antreibt. Denken Sie an Financial One ACME. Wenn die Entwickler eine Korrektur für ein kritisches Produktionsproblem in ihrer Finanzsoftware veröffentlichen müssen, müssen sie sich darauf verlassen können, dass Continuous X einwandfrei funktioniert.

Um sicherzustellen, dass diese Komponenten bei Bedarf verfügbar sind, müssen wir dieselben Best Practices anwenden wie bei unseren geschäftskritischen Anwendungen:

- **Standardmäßig sicher**: Wenn Angreifer einen Weg in unser Continuous X-Toolkit finden, haben sie freie Bahn, um in jedes System einzudringen, das von unserer Plattform verwaltet wird. Aufgrund dieser Kritikalität widmet sich [Kapitel 7](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/7) vollständig der Entwicklung sicherer und konformer Produkte.
- **Jede Änderung testen**: Nehmen wir an**,** wir verwenden GitLab als eines unserer Tools für Git und CI. Wir müssen die Bereitstellungskonfiguration von GitLab versionskontrollieren und denselben Continuous X-Prozess durchlaufen, um jede neue Version oder Konfigurationsänderung zu validieren. Falls erforderlich, führen wir ein Rollback oder Rollforward durch, falls ein Update Probleme verursacht!
- **Hochverfügbare Bereitstellung**: Befolgen Sie die Bereitstellungsrichtlinien für diese Tools, um eine hohe Verfügbarkeit zu gewährleisten. Wenn wir global verteilte Teams haben, möchten wir sicherstellen, dass bestimmte Komponenten so nah wie möglich an unseren Endbenutzern bereitgestellt werden. Informieren Sie sich auch über Upgrade-Optionen ohne Ausfallzeiten und befolgen Sie diese.
- **Beobachten Sie jede Komponente**: Jedes Tool liefert Telemetriedaten, die Aufschluss über den Zustand geben. Argo CD beispielsweise stellt Prometheus-Metriken für die Länge der Arbeitswarteschlange, Git-Anfragen und Synchronisierungsaktivitäten bereit. Diese geben Aufschluss darüber, ob Argo CD noch in der Lage ist, seine Aufgabe zu erfüllen. Eine ständig zunehmende Tiefe der Arbeitswarteschlange ist ein Zeichen dafür, dass Argo CD nicht mit allen Anfragen Schritt halten kann, was untersucht werden muss.
- **Service Level Agreements (SLAs) und Warnmeldungen bei Problemen**: Wir – das Plattformteam – müssen wissen, dass etwas nicht in Ordnung ist, bevor unsere Endbenutzer uns dies melden. Aus diesem Grund müssen wir für jede Komponente SLAs einrichten und geeignete Warnmeldungen konfigurieren, falls die Systeme nicht wie erwartet funktionieren. Der einfachste Weg, dies zu erreichen, ist die Einrichtung synthetischer Überprüfungen der wichtigsten API-Endpunkte jedes Tools (z. B. die Überprüfung der Reaktionsfähigkeit der Jenkins-Benutzeroberfläche mit einer synthetischen Überprüfung, die alle fünf Minuten durchgeführt wird; dies gibt uns ein Frühwarnsignal, falls Jenkins Probleme bekommt, bevor es jemand anderes bemerkt).

Das folgende Beispiel-Dashboard zeigt wichtige Gesundheitsindikatoren von Tools wie Argo CD. Das Gleiche muss für alle anderen Tools gelten, die unsere Kernplattformfunktionen ausmachen!

Abbildung 5.1: Überwachen und beobachten Sie jedes Tool, das Teil der Plattform ist

Plattformkomponenten sind genauso geschäftskritisch wie Ihre kritischen Anwendungen

Der Kern der Plattform dreht sich um die Bereitstellung von Änderungen in verschiedenen Umgebungen. Alle Tools, die diese Anwendungsfälle unterstützen – insbesondere diejenigen für Continuous X – müssen hochverfügbar, widerstandsfähig und sicher sein. Achten Sie darauf, dass Sie für alle Komponenten der Plattform die gleichen bewährten Verfahren anwenden!

Nachdem wir nun die Kernkonzepte von Continuous X (Integration, Testen, Validierung, Bereitstellung, Deployment und Release) zusammengefasst und erläutert haben, dass alle Konfigurationen (Code, Deployment-Konfiguration, Infrastruktur, Beobachtbarkeit usw.) denselben Prinzipien folgen müssen, ist es an der Zeit, einen Blick darauf zu werfen, wie diese Konzepte genutzt werden können, um Teams, die dies über eine Plattform nutzen, Selbstbedienungsautonomie zu bieten.

GitOps – Vom Pushen zum Pulling des gewünschten Zustands

**CI/CD** gibt es schon seit vielen Jahren. Das Buch „Continuous Delivery“ wurde ursprünglich im Jahr 2010 veröffentlicht – Jahre vor dem Aufkommen von Containern (die durch Docker ab 2013 populär wurden) und Container-Orchestrierungsplattformen (wie Kubernetes ab 2014).

Schnellvorlauf ins Jahr 2024, als dieses Buch ursprünglich veröffentlicht wurde: Wir leben in einer Welt, in der Folgendes gilt:

- **Git** ist die Quelle der Wahrheit. Es enthält alles als Code: Quellcode, Tests, Infrastruktur- und Bereitstellungsdefinitionen, Beobachtbarkeit, Eigentumsverhältnisse und so weiter.
- **CI/CD** erstellt, testet und packt **Container-/Open Container Initiative** (**OCI**)-Images aus einem Quellcode-Git-Repository und veröffentlicht sie in einer Artefakt-Registry (z. B. Harbor).
- **GitOps** versucht kontinuierlich, den neuesten gewünschten Zustand, wie er in einem Deployment-Git-Repository (z. B. Helm Charts) deklariert ist, auf die Ziel-Kubernetes-Umgebung anzuwenden und zusätzliche Konfigurationen (z. B. Observability für die jeweiligen Tools) zu übertragen.

Die vorstehende Beschreibung ist kein einheitliches Modell. GitOps wird in jeder Organisation etwas anders implementiert. Wenn Sie nach „Was ist GitOps?“ suchen, finden Sie viele verschiedene Varianten, wie zum Beispiel die folgenden:

- **Getrennte CI und CD**: CI veröffentlicht Container und CD veröffentlicht gepackte Artefakte, wie z. B. Helm Charts
- **Single Git**: Alles als Code (Quelle, Test, Bereitstellung, Beobachtbarkeit usw.) in einem einzigen Git-Repository
- **Push GitOps**: Pushen des gewünschten Zustands über Pipelines oder Workflows im Gegensatz zum Pulling von Änderungen in die Zielumgebung durch GitOps-Operatoren

Im folgenden Abschnitt beleuchten wir eine Variante von GitOps, die das Pull-Modell (Einlesen einer Konfiguration in die Zielumgebung) gegenüber dem **Push**\-Modell (Einfügen einer Konfiguration aus einem externen Tool in die Zielumgebung) bevorzugt . Diese Variante kann mit CNCF-Tools wie Flux oder Argo CD implementiert werden, wie in der folgenden Abbildung aus dem Learning Center von Codefresh zu GitOps dargestellt: https://codefresh.io/learn/gitops/.

Abbildung 5.2: Grundlegender GitOps-Ablauf, wie er von GitOps-Tools wie Argo CD oder Flux gefördert wird

Es liegt an Ihnen, ob Sie das Push-Modell mit automatisierten Pipelines oder Workflows bevorzugen, um Änderungen in Ihre Ziel-Kubernetes-Umgebungen zu übertragen! Um Ihnen die Entscheidung zu erleichtern, wollen wir uns die einzelnen Phasen genauer ansehen und einige Best Practices kennenlernen, die in jeder Phase zum Einsatz kommen sollten!

Phase 1 – vom Quellcode zum Container-Image

Die Umstellung auf GitOps ändert nichts daran, wie wir unsere Anwendungen aus Quellcode erstellen, der in Git versionskontrolliert ist. Vor dem Erstellen neuer Artefakte empfiehlt es sich, Abhängigkeitsprüfungen und -aktualisierungen zu automatisieren. Tools wie **Renovate Bot** \[3\] lassen sich in Git integrieren und erstellen Pull-Anfragen, wenn veraltete Abhängigkeiten, Bibliotheken von Drittanbietern oder andere Abhängigkeiten gefunden werden.

Sobald wir unseren aktuellen Code in Git haben, hat **CI** die gleiche Aufgabe wie immer: Es erstellt ein Artefakt, höchstwahrscheinlich ein Container-Image, das in eine Container-Registry gepusht wird! Dieses CI kann bei Bedarf, bei Commits zu bestimmten Branches, bei Pull-Anfragen oder bei jedem anderen für das Unternehmen sinnvollen Auslöser ausgelöst werden!

Es gibt viele verschiedene Tools, die diese Aufgabe übernehmen können: Jenkins, GitLab, Azure DevOps, GitHub Actions, Bitbucket Pipelines und viele mehr. Außerdem gibt es verschiedene Optionen für Container-Registries ( ). Wir werden später in diesem Buch noch auf Container-Registries und ihre Bedeutung eingehen, da sie – wie alle Komponenten unserer Plattform – für den Erfolg unserer zukünftigen Plattform von entscheidender Bedeutung sind!

Sobald die CI den Quellcode erfolgreich kompiliert, Unit-Tests durchgeführt und zusätzliche Qualitätsprüfungen des Codes durchgeführt hat, ist es an der Zeit, die Binärdatei in ein Container-Image zu packen. Es gibt viele Best Practices für die Erstellung von Container-Images: vom einfachen Verpacken eines einzelnen Dienstes in einen Container über die sorgfältige Verwendung öffentlicher Basis-Images bis hin zur Erstellung eines möglichst kleinen Images. Die Befolgung all dieser Regeln führt zu einer höheren Erfolgsquote, wenn das Container-Image von der CI bis zur Produktion gelangt. Hier sind zwei offensichtliche, aber sehr wichtige Praktiken, die wir in diesem Kapitel erwähnen möchten (weitere Informationen finden Sie in den zuvor genannten Büchern):

- **Kennzeichnen Sie Ihre Images ordnungsgemäß und konsistent**: Images werden im Allgemeinen durch zwei Komponenten identifiziert: ihren Namen und ihr Tag (z. B. finoneacme/fund-transfer:2.34.3, wobei finoneacme/fund-transfer der Name und 2.34.3 das Tag ist). Wenn Sie ein Image erstellen, liegt es an Ihnen, es ordnungsgemäß zu kennzeichnen, aber Sie sollten dabei eine konsistente Richtlinie befolgen. In der Branche gibt es zwei gängige Methoden, um dies zu tun:
    - **Semantische Versionierung**: Eine gängige Methode ist die Verwendung einer Versionsnummer. Die **Semantic Versioning Specification** \[4\] bietet eine leicht verständliche Richtlinie mit einer dreiteiligen Versionsnummer: MAJOR.MINOR.PATCH. Jede Minor- oder Patch-Versionsnummer muss für eine abwärtskompatible Änderung stehen. In Kombination mit dem Versionsnamen „latest“, der standardmäßig auf die neueste verfügbare Version verweist, können Sie einen einfachen Zugriff auf ein bestimmtes Image (z. B. X.Y.Z) ermöglichen. Außerdem können Sie die neueste Patch-Version für eine bestimmte Minor-Version (z. B. X.Y) oder die neueste Minor- und Patch-Version für eine Major-Version (z. B. X) auswählen.
    - **Tagging mit Git-Commit-Hash**: Wenn Git-Commits einen CI-Build auslösen, ist es am besten, den Git-Commit-Hash direkt als Version zu verwenden, anstatt die semantische Versionierung zu verfolgen. Der Commit-Hash auf dem Image sagt uns auch sofort, welcher Quellcode-Commit für die Erstellung dieses Container-Images verantwortlich war. Für unser Image könnte dies bedeuten, dass es wie folgt getaggt ist: financeoneacme/fund-transfer:d85aaef.
- **Scannen Sie Ihre Images auf bekannte Schwachstellen**: Images, die von Ihrer CI erstellt werden, müssen auf bekannte Schwachstellen gescannt werden. Dies kann als zusätzlicher Schritt in der CI erfolgen (z. B. Aufruf eines Scan-Tools vor dem Hochladen des Images in die Registry). Es kann auch von der Container-Registry selbst übernommen werden. Je nach verwendeter Registry kann das Image während des Uploads gescannt und bei gefundenen Schwachstellen blockiert oder unter Quarantäne gestellt werden. Dadurch werden bekannte Schwachstellen zum Zeitpunkt der Erstellung des Container-Images gestoppt. Beachten Sie, dass dies keine Schwachstellen stoppt, die zu einem späteren Zeitpunkt identifiziert werden, wie beispielsweise die bekannte log4j-Schwachstelle. Aus diesem Grund muss die Sicherheit über die statischen Prüfungen im CI-Prozess hinausgehen und während des gesamten Lebenszyklus eines Artefakts fortgesetzt werden. Dies wird in [Kapitel 7](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/7) näher erläutert, in dem wir uns eingehender mit der Entwicklung und dem Betrieb sicherer Produkte befassen.

Nachdem wir nun ein Container-Image in unsere Container-Registry hochgeladen haben, können wir es in einer Bereitstellungsdefinition verwenden.

Phase 2 – vom Container-Image zum mit Metadaten angereicherten Bereitstellungsartefakt

Das Container-Image muss nun seinen Weg in eine Bereitstellungsdefinition finden. Bei Kubernetes benötigen wir eine Manifestdatei, die unsere Bereitstellungsdefinition definiert und die wir später auf unseren K8s-Cluster anwenden können.

In [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3) haben wir hervorgehoben, dass das Hinzufügen von Metadaten (Eigentumsverhältnisse, Beobachtbarkeitsstufe, Benachrichtigungen) zu unserer Bereitstellungsdatei für viele Self-Service-Anwendungsfälle von Vorteil ist, beispielsweise für den Anwendungsfall „Anfordern von Protokollen als Self-Service“. Neben unserem Quellcode müssen wir daher auch unsere Bereitstellungsdefinition versionskontrollieren und einen Mindestsatz an Metadaten durchsetzen. Dies ermöglicht unsere Plattform-Self-Service-Anwendungsfälle (z. B. wer welche Dienste zu welcher Anwendung bereitgestellt hat) sowie die Einhaltung allgemeiner Best Practices für die Infrastruktur (z. B. die Definition von Anforderungs- und Ressourcenlimits), wie Sie im folgenden Manifest sehen können:

mainfest.yaml (Kubernetes-Bereitstellung)

apiVersion: apps/v1

kind: Deployment

metadata:

&nbsp; Name: Geldtransferdienst

Spezifikation:

&nbsp; …

&nbsp; Vorlage:

&nbsp;   Metadaten:

&nbsp;     Anmerkungen:

&nbsp;       # Teamverantwortung

&nbsp;       Eigentümerteam: dev-team-backend

&nbsp;       app.kubernetes.io/name: fund-transfer-service

&nbsp;       # App-Kontext

&nbsp;       app.kubernetes.io/part-of: backend-services

&nbsp;       app.kubernetes.io/version: d85aaef

&nbsp;       # Protokollstufe

&nbsp;       observability.logs.level: info

&nbsp;       # Protokollquelle

&nbsp;       observability.logs.location: stdout

&nbsp;   …

&nbsp;   Spezifikation:

&nbsp;     Container:

&nbsp;     - Name: fund-transfer

&nbsp;       image: „financeoneacme/fund-transfer:d85aaef”

&nbsp;       imagePullPolicy: IfNotPresent

&nbsp;       Ressourcen:

&nbsp;         # Limits festlegen

&nbsp;         Grenzen:

&nbsp;           Speicher: „200 Mi”

&nbsp;           CPU: „2”

&nbsp;         Anfragen:

&nbsp;           Speicher: „100 Mi”

&nbsp;           CPU: „2”

&nbsp;   …

KopierenErklären

Die Bereitstellungsdefinition kann ein Manifest oder eine Reihe von Manifestdateien sein, da wir wahrscheinlich auch zusätzliche K8s-Ressourcen benötigen, wie z. B. eine Service- oder Ingress-Definition. Anstelle von einfachen Manifestdateien, die wir in einem Unterordner neben dem Quellcode unseres Dienstes organisieren, gibt es Optionen zur Nutzung von Template- oder Packaging-Frameworks und -Tools wie **Kustomize** \[5\] oder **Helm** \[6\].

Es ist wichtig, zu überlegen, wie wir all unsere Dateien als Code-Dateien organisieren und versionskontrollieren können. Es gibt mehrere Strategien mit Vor- und Nachteilen, die gut dokumentiert sind. Um mehr zu erfahren, empfehlen die Autoren, sich über die verschiedenen Muster für Repositorys und Verzeichnisstrukturen zu informieren. Der folgende Abschnitt gibt nur einen kurzen Überblick über das, was Sie wissen müssen, um Ihre eingehende Recherche zu diesem Thema fortzusetzen!

Monorepo versus Polyrepo

Bei der Gestaltung Ihrer Git-Repository-Struktur haben Sie zwei allgemeine Optionen, die in der Branche als Monorepo oder Polyrepo bezeichnet werden: ein einzelnes Git-Repository oder mehrere Repositorys, die nach Teams oder Funktionen aufgeteilt sind:

Abbildung 5.3: Mono versus Polyrepo – Vor- und Nachteile beider Muster

- **Monorepo**: Beim Monorepo-Muster werden alle Konfigurationsdateien (Code, Infrastruktur, Beobachtbarkeit usw.) in einem einzigen Git-Repository gespeichert. Dieses Muster gilt für jede potenzielle Umgebung (Entwicklung, Test, Staging, Produktion) – das bedeutet, dass sich jede Konfiguration in einem einzigen Git-Repo befindet, getrennt durch Ordner.

Der Vorteil eines Monorepos ist, dass sich alles an einem Ort befindet. Der Nachteil ist, dass dieses Repo irgendwann sehr groß wird, was zu potenziellen Leistungsproblemen führen kann, wenn Tools wie ArgoCD oder Flux ständig das gesamte Repo nach Änderungen durchsuchen müssen. Außerdem wird es dadurch schwieriger, die Aufgabenbereiche zwischen Anwendungs- und Infrastrukturverantwortlichen zu trennen.

- **Polyrepo**: Beim Polyrepo-Muster gibt es mehrere Repositorys, was die Trennung der Zuständigkeiten erleichtert. Dies können Repositorys pro Team (App-Team A, B, C), pro Umgebung (Entwicklung, Staging, Produktion usw.), pro Mandant (in mandantenfähigen Systemen) oder pro Organisationsgrenze (App-Teams, Plattform-Teams usw.) sein.

Der Vorteil ist eine bessere Trennung der Zuständigkeiten. Der Nachteil ist, dass wir letztendlich eine große Anzahl von Git-Repositorys verwalten müssen, was es schwieriger macht, die Konsistenz und allgemeine Gültigkeit über alle Konfigurationen hinweg sicherzustellen, die sich über mehrere Repositories erstrecken, aus denen die gesamte Konfiguration besteht.

Verzeichnisstruktur – befolgen Sie das DRY-Prinzip

Unabhängig davon, ob es sich um ein Mono- oder Polyrepo handelt, muss das einzelne Git-Repository über eine gute Verzeichnisstruktur verfügen. In der Regel spiegelt diese die Organisationsstruktur wider, die die Entwicklungsteams von den Teams trennt, die die zugrunde liegende Infrastruktur oder Plattform verwalten. Eine bewährte Vorgehensweise ist es, dem DRY-Prinzip (**Don't Repeat Yourself**) \[7\] zu folgen. Die Idee dahinter ist, die beste Struktur zu finden, um das Kopieren/Einfügen gemeinsamer YAML-Einstellungen an verschiedenen Stellen zu vermeiden. Hier helfen Tools wie Helm und Kustomize.

Das folgende Strukturbeispiel wurde von einem GitOps-Blog von **Red Hat** \[8\] inspiriert und zeigt die Konfiguration für den Plattformadministrator und die Konfiguration für ein Anwendungsteam unter Verwendung eines Vorlagen-Tools wie Kustomize. Diese Struktur könnte entweder in einem einzigen Monorepo verwendet werden, das durch einen Ordner getrennt ist, oder sie könnte nach dem Polyrepo-Muster in einzelne Repositories eingefügt werden.

| **Plattformteam** | **Entwicklungsteam** |
| --- | --- |
| ├── bootstrap<br><br>│ ├── base<br><br>│ └── overlays<br><br>│ └── default<br><br>├── cluster-config<br><br>│ ├── GitOps-Controller<br><br>│ ├── identity-provider<br><br>│ └── Bildscanner<br><br>└── Komponenten<br><br>&nbsp;   ├── Anwendungssätze<br><br>&nbsp;   ├── Anwendungen<br><br>&nbsp;   └── argocdproj | └── Bereitstellung<br><br>&nbsp;   ├── Basis<br><br>&nbsp;   └── overlays<br><br>&nbsp;       ├── dev<br><br>&nbsp;       ├── prod<br><br>&nbsp;       └── stage |

Tabelle 5.1: Eine mögliche Verzeichnisstruktur, die von Tools wie Kustomize verwendet wird

Nachdem wir nun die verschiedenen Möglichkeiten zur Organisation unserer Repositorys und Verzeichnisstrukturen kennengelernt haben, müssen wir lernen, wie das neue Container-Image aus Phase 1 in unsere Bereitstellungsdefinition in unseren Repositorys gelangt!

Aktualisieren des Manifests mit der neuen Container-Image-Version

Der letzte Schritt in Phase 2 besteht darin, eine neue Image-Version, die aus der CI hervorgegangen ist, in unsere Bereitstellungsdateien zu übernehmen. Dies kann durch Aktualisieren des Bereitstellungsmanifests, wie im vorangegangenen Beispiel gezeigt, oder durch Aktualisieren einer values.yaml-Datei bei Verwendung von Helm-Charts erfolgen.

Da diese Konfigurationsdateien in einem Git-Repository (mono oder poly, das spielt keine Rolle) versionskontrolliert sind, sollten wir den regulären Git-Workflow befolgen und einen Pull Request erstellen, um die Aktualisierung dieses Images zu fördern. Wir können die Erstellung dieses Pull Requests auf zwei Arten automatisieren:

- **Schritt in der CI-Pipeline**: Als letzter Schritt in CI kann ein Pull Request geöffnet werden, der das neue Image-Tag in das entsprechende Bereitstellungsdefinitions-Repo und die richtige Verzeichnisstruktur überträgt (z. B. Aktualisierung der Werte im Entwicklungs-Overlay-Verzeichnis, wenn es sich um ein neu erstelltes Image handelt).
- **Webhook in einer Container-Registry**: Wenn die Registry ein neues Image von CI erhält, kann sie einen Webhook auslösen, mit dem wir denselben Pull Request in unserem Deployment-Git-Repository erstellen können.

Im Folgenden finden Sie die aktualisierten Versionsinformationen der Kubernetes-Bereitstellung, die wir im vorherigen Beispiel gesehen haben. Sie können diese mit den Werten aus dem vorherigen Beispiel vergleichen:

apiVersion: apps/v1

kind: Deployment

metadata:

&nbsp; name: fund-transfer-service

spec:

&nbsp; …

&nbsp; Vorlage:

&nbsp;   Metadaten:

&nbsp;     Anmerkungen:

&nbsp;       Eigentümerteam: dev-team-backend

&nbsp;       app.kubernetes.io/name: fund-transfer-service

&nbsp;       app.kubernetes.io/part-of: Backend-Services

&nbsp;       app.kubernetes.io/version: a3456bc

&nbsp;       observability.logs.level: info

&nbsp;       observability.logs.location: stdout

&nbsp;   …

&nbsp;   Spezifikation:

&nbsp;     Container:

&nbsp;     - Name: fund-transfer

&nbsp;       image: "financeoneacme/fund-transfer:a3456bc"

&nbsp;   …

KopierenErklären

Jetzt wissen wir, wie ein neues Image, das von CI erstellt wurde, in die Bereitstellungsdefinition in unseren jeweiligen Repositorys gelangt. Wir haben den GitOps-Operator bereits weiter oben in diesem Kapitel in einem Image gesehen. Jetzt ist es an der Zeit, uns damit zu befassen, was der GitOps-Operator tatsächlich tut, um unseren gewünschten Zustand aus Git auf unsere Zielcluster anzuwenden!

Phase 3 – GitOps – Beibehaltung Ihres gewünschten Bereitstellungszustands

Nachdem wir nun alles als Code in Git haben, ist es an der Zeit, darüber zu sprechen, wie wir diese Konfiguration auf unsere Zielumgebungen anwenden können. Eine Möglichkeit besteht darin, dasselbe Push-Modell zu verwenden, das wir auch für CI verwenden. Wir könnten Delivery-Pipelines bei Änderungen in unserem Git-Repository auslösen und dann die neueste Version der Manifeste oder Helm-Charts auf die Zielumgebung anwenden. In diesem Kapitel konzentrieren wir uns jedoch auf das Pull-Modell, das von GitOps-Operatoren oder GitOps-Agenten wie Argo CD, Flux und einigen kommerziellen Angeboten implementiert wird.

GitOps-Operatoren in Kürze – Git mit K8s synchronisieren

GitOps-Operatoren gleichen kontinuierlich ab und stellen sicher, dass der in unseren Repositorys deklarierte gewünschte Zustand mit dem tatsächlichen Zustand in unseren Zielumgebungen übereinstimmt. Der Operator erkennt eine Nichtübereinstimmung, wenn der Zustand in Git nicht mit dem in der Zielumgebung übereinstimmt. Dies kann passieren, wenn die Git-Konfiguration geändert wurde (z. B. wenn ein neues Image verfügbar ist und eine Manifestaktualisierung verursacht). Es kann auch passieren, wenn jemand die Konfiguration in K8s ändert (z. B. durch eine manuelle Aktualisierung oder ein anderes Automatisierungstool). Das Folgende ist eine allgemeine Übersicht über die Rolle des GitOps-Operators:

Abbildung 5.4: Der GitOps-Operator synchronisiert den gewünschten Zustand in Git mit dem tatsächlichen Zustand in K8s

Je nach GitOps-Operator-Tool gibt es unterschiedliche Konfigurationsoptionen für den Abgleichprozess. Es lohnt sich, die Dokumentation der beiden bekanntesten Tools im Cloud-Native-Ökosystem zu lesen: **Argo CD** \[9\] und **Flux** \[10\]. Machen Sie sich auch mit den Konfigurationselementen vertraut, da einige Tools das Konzept von Projekten und Anwendungen verwenden, während andere nur das Konzept einer Quelle kennen.

Abstimmung verstehen – K8s mit Git synchronisieren

Im Wesentlichen ruft der GitOps-Operator den gewünschten Zustand für ein Projekt oder eine Anwendung aus einer Quelle (Git-Repository, einem Ordner im Git-Repository, dem OCI-Repository, S3-Buckets usw.) ab und vergleicht ihn mit dem aktuellen Zustand, der auf dem Ziel-K8s-Cluster ausgeführt wird. Die beiden Zustände können entweder synchron oder nicht synchron sein. Wenn der Zustand nicht synchron ist, gibt es für den GitOps-Operator verschiedene Optionen, um die Zustände zu synchronisieren, d. h. den aktuellen Zustand an den gewünschten Zustand anzupassen:

- **Manuelle Synchronisierung**: Entweder über eine **Befehlszeilenschnittstelle** (**CLI**) oder eine Benutzeroberfläche kann man den GitOps-Operator dazu veranlassen, die beiden Zustände zu synchronisieren.
- **Automatische Synchronisierung**: Sobald ein System nicht synchron ist, versucht der GitOps-Operator, automatisch zu synchronisieren.
- **Synchronisierungszeitpläne/-fenster**: Es kann vorkommen, dass Sie eine Synchronisierung wünschen oder nicht wünschen. Hier kommen Synchronisierungszeitpläne oder Synchronisierungsfenster ins Spiel, die Synchronisierungen entweder blockieren oder zulassen.
- **Synchronisierung fehlgeschlagen**: Es kann vorkommen, dass der GitOps-Operator den gewünschten Zustand nicht anwenden kann. Dies kann an Fehlern in der Konfigurationsdatei liegen (z. B. Verweis auf ein ungültiges Image). Es könnte an einem Infrastrukturproblem liegen (z. B. wenn K8s nicht über genügend Ressourcen verfügt). Es könnte auch an konkurrierenden Tools liegen (z. B. Auto-Scaling-Tools wie HPA/KEDA, die Replikate oder Ressourcenlimits ändern). Es ist wichtig, sich dieses Zustands bewusst zu sein und richtig damit umzugehen. Weitere Informationen finden Sie im Abschnitt über Best Practices!

Nachdem wir nun die Grundlagen der Synchronisierung kennen, wollen wir uns verschiedene GitOps-Operator-Bereitstellungsmuster ansehen!

GitOps-Operator-Muster – Single, Hub and Spoke und Many-to-Many

Die einfachste Version – und wahrscheinlich das Modell, mit dem viele beginnen – ist der Monorepo-Ansatz mit GitOps-Operatoren, die in eine einzige Zielumgebung ziehen, wie wir in Abbildung 5.3 für beide Muster „ “ gesehen haben. Während das einzelne Ziel ein gängiges Muster ist, insbesondere wenn Sie mit GitOps beginnen, gibt es noch andere Muster, die wir kurz hervorheben möchten.

GitOps kann auch so eingerichtet werden, dass wir einen zentralen GitOps-Operator haben, der den gewünschten Zustand, wie er in Git deklariert ist, beibehält und mit mehreren Zielumgebungen synchronisiert, indem er diese Änderungen herausgibt. Dies wird als **Hub-and-Spoke-Modell** bezeichnet. Eine weitere Option ist das **Many-to-Many-Modell**, bei dem jede Zielumgebung über einen eigenen GitOps-Operator verfügt, der den gewünschten Zustand kontinuierlich mit dem Zustand auf seinem eigenen Cluster synchronisiert, wie in der folgenden Abbildung dargestellt:

Abbildung 5.5: Hub-and-Spoke- und Many-to-Many-GitOps-Operator-Muster

Nachdem wir nun die wichtigsten Phasen in GitOps besprochen haben, lassen Sie uns noch einmal zusammenfassen und einen kurzen Blick auf einige Best Practices werfen.

GitOps-Best Practices

Diese Liste ist nicht vollständig, sollte Ihnen jedoch einen guten Ausgangspunkt für die Definition Ihres GitOps-Prozesses bieten:

- **Trennen Sie die Konfiguration von den Quellcode-Repositorys/Ordnern**: Es wird empfohlen, den eigentlichen Quellcode von den Bereitstellungsdefinitionen zu trennen. Entweder in separaten Repositorys oder innerhalb des Repos in separaten Ordnern. Warum ist das so? Dadurch werden Aufgaben und Zugriffsrechte klar voneinander getrennt. Dies erleichtert Git-ausgelöste Aktionen, da eine Änderung in einer Bereitstellungskonfigurationsdatei andere Aktionen auslösen sollte als in den Quellcode-Dateien. So wird eine potenziell unendliche Schleife von Änderungen vermieden, wenn CI dasselbe Repository ändert! Je kleiner das Repository, desto weniger Arbeit haben GitOps-Tools, um alle Dateien zu scannen und den gewünschten Zustand zu ermitteln.
- **Richtige Synchronisierungseinstellungen – Polling versus Webhook**: GitOps-Tools bieten verschiedene Synchronisierungseinstellungen sowohl für das Scannen der Quellsysteme (z. B. Git) als auch für die Planung der Auslösung von Synchronisierungen. Machen Sie sich für das Scannen mit der Standard-Polling-Häufigkeit vertraut (z. B. ruft Argo CD standardmäßig alle drei Minuten alle Git-Repositories ab). Sowohl Argo CD als auch Flux können so geändert werden, dass sie Webhooks vom Git-System empfangen, wodurch der Pull-Mechanismus durch einen Push-Mechanismus ersetzt wird! Dies ist sehr wichtig zu verstehen, da mit der Zunahme der Anzahl der Quellsysteme (Git, Artefakt-Repositorys, S3-Buckets usw.) auch die Anzahl der API-Aufrufe von Ihrem GitOps-Tool an diese Systeme zunimmt. Es empfiehlt sich, die Anzahl der Aufrufe vom GitOps-Tool an diese externen Systeme zu überwachen, um bei drastischen Verhaltensänderungen benachrichtigt zu werden. Eine Verhaltensänderung kann durch eine versehentliche Änderung der Standardeinstellungen verursacht werden. Die meisten Tools bieten Prometheus- oder OpenTelemetry-Metriken, die von Ihrem Observability-Tool beobachtet werden können!

Die Autoren haben Konfigurationen gesehen, die zu API-Ratenbegrenzungen und sogar zum Absturz von Git-Systemen führten, weil die GitOps-Tools während einer Synchronisierung eine zu hohe Last erzeugt haben!

- **Nicht jede Konfiguration muss in einem Manifest enthalten sein**: Da GitOps den gewünschten Zustand mit dem tatsächlichen Zustand vergleicht, ist es wichtig, einige Konfigurationen, die möglicherweise von anderen Tools verwaltet werden, aus Ihrem Manifest herauszulassen. Nehmen Sie beispielsweise Replikate. Wenn Sie Tools wie HPA oder KEDA zur automatischen Skalierung Ihrer Pods verwenden, sollten Sie keine statische Replikanzahl in Ihrem Manifest angeben. Dies würde dazu führen, dass das GitOps-Tool bei jeder Änderung durch HPA/KEDA eine Asynchronität feststellt. Dies würde dazu führen, dass zwei Automatisierungstools miteinander konkurrieren.
- **GitOps-Benachrichtigungen zur Behandlung von Synchronisierungszuständen**: GitOps-Tools geben Benachrichtigungen aus, wenn sich der Synchronisierungsstatus ändert. Dies ist der Fall, wenn GitOps eine Nichtübereinstimmung erkennt, wenn es eine Synchronisierung abgeschlossen hat oder wenn ein Problem auftritt und eine Synchronisierung fehlschlägt. In all diesen Fällen ist es wichtig, benachrichtigt zu werden, da Sie sicherstellen möchten, dass Sie Synchronisierungsfehler beheben oder Informationen an das Entwicklungsteam zurücksenden, wenn die letzte Aktualisierung erfolgreich synchronisiert wurde.

Um Benachrichtigungen zu erhalten, erstellen GitOps-Tools Kubernetes-Ereignisse, die Sie in Ihre Observability-Lösung einspeisen und dann darauf reagieren/alarmieren können. GitOps-Tools bieten in der Regel auch eine Art native Benachrichtigungsfunktion, mit der bei einem besonderen Ereignis ein externes Tool ausgelöst werden kann. Flux bietet beispielsweise Alerts, während Argo CD mit „ ” ein Benachrichtigungskonzept bereitstellt. Beide ermöglichen es Ihnen beispielsweise, Slack-Nachrichten zu senden oder andere externe Tools auszulösen, wenn bestimmte Ereignisse auftreten, die Ihre Aufmerksamkeit erfordern!

GitOps – vom Push zum Pull

GitOps erweitert die Leistungsfähigkeit von Git vom Anwendungscode auf alles, was als Code vorliegt. Während CI/CD sich weiterhin auf die Erstellung von Artefakten konzentriert, bietet GitOps eine elegante Möglichkeit, den gewünschten Bereitstellungsstatus während des gesamten Softwareentwicklungslebenszyklus in jede Zielumgebung zu übertragen. Änderungen an einem System können nur über Git vorgenommen werden, was den Vorteil der Rückverfolgbarkeit von Änderungen, der Rückgängigmachung zu einer früheren Version und der Durchsetzung von Überprüfungsprozessen durch Pull-Anfragen bietet.

Nachdem wir nun die Grundlagen von GitOps behandelt haben, sollten wir uns ansehen, wie wir davon beim Aufbau moderner Plattformen profitieren können. Als Plattformteams können wir Best Practices (Versionskontrolle, Richtlinien usw.) zentral durchsetzen, indem wir Automatisierung in CI/CD und die Container-Registry nutzen, um das Risiko einer fehlerhaften Änderungsanforderung zu verringern. Mit Git lässt sich jede Änderung und Bereitstellung bis zu einem Git-Commit zurückverfolgen, was die Fehlerbehebung erheblich vereinfacht. Außerdem bietet es ein zusätzliches Maß an Self-Service (z. B. Benachrichtigung der Entwicklungsteams, wenn ihre Änderung mit der Zielumgebung synchronisiert wurde, oder Benachrichtigung, wenn ihre neueste Version (über den Git-Commit-Hash) Probleme aufweist).

Wenden wir uns nun den Container-Registries zu, denn ohne sie könnten wir keine der Images veröffentlichen oder verteilen, die von den Entwicklungsteams erstellt werden, die die Plattform als Self-Service nutzen.

Die Bedeutung von Container- und Artefakt-Registern als Einstiegspunkte verstehen

Container- und Artefakt-Registries verdienen ein eigenes Kapitel, da sie einer der Grundbausteine moderner Cloud-nativer Plattformen sind. Wir werden jedoch versuchen, Ihnen das relevante Wissen zu vermitteln, das Ihnen helfen soll, den späteren Kapiteln dieses Buches folgen zu können.

Wir unterscheiden zwischen öffentlichen und privaten Registries:

- **Öffentliche Registries** werden in der Regel von Einzelpersonen oder kleinen Teams verwendet, die ihre Registries so schnell wie möglich einrichten und nutzen möchten. Ab einem bestimmten Punkt lohnt es sich jedoch, private Registries in Betracht zu ziehen.
- **Private Registries** bieten mehrere wichtige Funktionen, wie z. B. die effiziente Speicherung von Images, das Scannen nach Schwachstellen, das Replizieren von Images in andere Registries, die Durchsetzung von Zugriffskontrollen beim Abrufen von Images und die Benachrichtigung anderer Tools über Aktualisierungen, mit dem Ziel, Images für die Umgebungen, in denen sie bereitgestellt werden müssen, schnell und einfach zugänglich zu machen.

Während private Container-Registries in der Regel nur intern aufgerufen werden, um neue Builds zu pushen und sie von unseren GitOps-Tools abrufen zu lassen, können wir die Registry auch für die Öffentlichkeit zugänglich machen. Mit „öffentlich” meinen wir, dass wir Drittanbietern die Möglichkeit geben, ihre neuesten Images oder Bereitstellungsartefakte zu übertragen. Da Unternehmen auf Software von Drittanbietern angewiesen sind – denken Sie an jedes handelsübliche Softwareprodukt, das Sie selbst bereitstellen –, können wir denselben Prozess der Schwachstellensuche, Replikation und Zugriffskontrolle nutzen, bevor diese Software auf den internen Systemen bereitgestellt wird. Financial One ACME könnte beispielsweise seinen Drittanbietern für ein Development Ticketing System erlauben, neue Versionen an diesen öffentlichen Endpunkt zu übertragen. Nach dem Scannen und Validieren kann es auf den internen K8s-Clustern bereitgestellt werden, auf denen alle Entwicklungstools laufen.

Die folgende Abbildung gibt einen sehr allgemeinen Überblick darüber, wie Container-Registries in den End-to-End-Bereitstellungsprozess integriert sind, der mit dem Pushen eines neuen Artefakts (von Drittanbietern oder CI/CD) beginnt und endet, wenn dieses neue Artefakt in den Zielumgebungen bereitgestellt wird:

Abbildung 5.6: Container-Registries – das Herzstück unserer Plattform

Obwohl es viele detaillierte Informationen von verschiedenen Open-Source- und kommerziellen Registry-Anbietern gibt, möchten wir einen kurzen Überblick darüber geben, wie Registries in unsere Plattform-Engineering-Architektur passen, warum bestimmte Konzepte wichtig sind und wie wir Container-Registries unseren Endbenutzern am besten als benutzerfreundlichen Self-Service zur Verfügung stellen können!

Vom Container zum Artefakt-Register

Bevor wir uns mit dem Prozess befassen, möchten wir kurz darauf hinweisen, dass Container-Registries – obwohl der Name dies vermuten lässt – nicht auf Container-Images beschränkt sind. Die meisten Container-Registries unterstützen in der Regel den OCI \[11\]-Image-Standard. In den letzten Jahren wurden Container-Registries erweitert, um auch Nicht-Container-Artefakte wie Helm Charts, gezippte Versionen von Manifesten oder Kustomize-basierte Vorlagen zu unterstützen. Mit dieser Erweiterung ging auch eine Namensänderung für Artefakt-Registries einher, da diese Tools Artefakte im Allgemeinen und nicht nur Container-Images verwalten.

Aber das ist noch nicht alles. Artefakt-Registries, Open-Source- oder SaaS-Dienste (kurz für **Software as a Service**) bieten oft zusätzliche Funktionen wie Zugriffskontrolle, regionale Replikation, Audit-Protokollierung, Durchsetzung von Richtlinien, Sicherheitsscans, Benachrichtigungen und vieles mehr.

Erstellen und Übertragen von Artefakten in die Registry

Das Hochladen (Pushing) und Herunterladen (Pulling) von Images kann mit Docker-Befehlen (oder anderen Tools wie Podman) erfolgen. Zuvor müssen Sie sich bei der Registry (Ihrer privaten oder öffentlichen Registry, z. B. Docker Hub) authentifizieren. Nach der Authentifizierung ist das Pushen und Pulling ganz einfach, wie der folgende Code zeigt:

Interaktion mit der Container-Registry über Docker-Befehle

export REGISTRY=registry.finone.acme

\# Authentifizieren

docker login -u YOURUSER -p YOURPASSWORD $REGISTRY

\# Image erstellen

docker build -t $REGISTRY/financeoneacme/fund-transfer:1.2.3 .

\# Image übertragen

docker push $REGISTRY/financeoneacme/fund-transfer:1.2.3

\# Image abrufen

docker pull $REGISTRY/financeoneacme/fund-transfer:1.2.3

KopierenErklären

Beim Erstellen neuer Images im Rahmen des CI-Prozesses ist es wichtig, die Best Practices für Image-Labels und Metadaten zu befolgen. Die OCI hat daher auch eine Liste mit empfohlenen Anmerkungen \[12\] als Teil ihrer Image-Spezifikation, die verwendet werden sollten, wie z. B. erstellt, Autoren, URL und Dokumentation (alle mit dem Präfix org.opencontainers.image.).

Neben einer API-Schnittstelle bieten Registries in der Regel auch eine **Benutzeroberfläche** (**UI**), die es einfacher macht, zu sehen, welche Images hochgeladen wurden, wie viel Speicherplatz sie belegen, und – je nach den Verwaltungsfunktionen der Registry – auch die Konfigurationsaspekte all dieser Funktionen bereitstellt (z. B. Erstellen von Projekten, Verwalten von Benutzern, Festlegen von Richtlinien, Konfigurieren von Webhooks usw.).

Verwalten hochgeladener Artefakte

Registries verwalten Artefakte in der Regel in Projekten. Projekte können innerhalb der Registry privat oder öffentlich sein, was bedeutet, dass Artefakte in einem öffentlichen Projekt für jeden zugänglich sind, der auf die Registry zugreifen kann, während private Projekte nur für autorisierte Benutzer zugänglich sind. Damit kommen wir zur Benutzerverwaltung und Zugriffskontrolle, die auf Projektebene definiert werden kann und auch in Zugriffsprotokolle einfließen kann. Registries erstellen Protokolle für jeden Push und Pull, um einen guten Prüfpfad zu haben. CNCF Harbor ist eine sehr beliebte Container-Registry, die auch eine gute Dokumentation zu all diesen Funktionen bietet. Anstatt hier ins Detail zu gehen, empfehlen wir Ihnen, die öffentlich zugängliche Dokumentation \[13\] zu all diesen Funktionen zu lesen. Wichtig ist, dass Sie sich merken, wie Sie Ihre Images in Projekten organisieren und wem Sie Zugriff gewähren. Wenn Sie auch externen Dritten erlauben möchten, ihre Images in Ihre Registries zu übertragen, können Sie für sie spezielle Benutzer erstellen, die ihnen das Hochladen in die jeweiligen Containerprojekte ermöglichen!

Sicherheitslücken-Scan

[Kapitel 7](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/7) befasst sich ausführlicher mit dem Thema Sicherheit, aber es ist wichtig, an dieser Stelle zu erwähnen, dass eine zentrale Komponente wie ein Artefakt-Register, durch das jedes Artefakt laufen muss, ein idealer Ort für die statische Überprüfung auf Schwachstellen ist. Register bieten oft sofort einsatzbereite Scan-Funktionen oder ermöglichen die Integration zusätzlicher Tools, je nach Art des Artefakts. Diese Tools werden dann entweder beim Hochladen eines neuen Bildes aufgerufen, um die Bilder bei ihrer Ankunft zu scannen, oder nach einem Zeitplan, um sicherzustellen, dass die Bilder kontinuierlich gescannt und erneut gescannt werden.

Abonnieren der Lebenszyklusereignisse eines Artefakts in der Registrierung

Ein Artefakt durchläuft in der Regel verschiedene Lebenszyklusphasen, vom ersten Hochladen (Push) über den Sicherheitsscan und die Replikation in andere Repositorys bis hin zum Herunterladen (Pull), bis es schließlich gelöscht wird, weil es nicht mehr benötigt wird. Am Beispiel der Registry Harbor können wir auch alle diese Lebenszyklusphasen mithilfe von Webhooks abonnieren. Dies ermöglicht viele interessante Anwendungsfälle, wie zum Beispiel die folgenden:

- **Sicherheit**: Benachrichtigung des Sicherheitsteams über neue Schwachstellen
- **Speicher**: Bereinigung alter Images, wenn die Speicherquoten erreicht sind
- **Bereitstellung**: Neue Images, die von CI/CD oder Drittanbietern hochgeladen wurden
- **Audit**: Verfolgen Sie, wer welche Artefakte abruft

Zur Information finden Sie hier die vollständige Liste der verfügbaren Lebenszyklusereignisse, die mit Webhooks verwendet werden können: Artefakt gelöscht, Artefakt abgerufen, Artefakt gepusht, Diagramm gelöscht, Diagramm heruntergeladen, Diagramm hochgeladen, Kontingent überschritten, Kontingent fast erschöpft, Replikation abgeschlossen, Scan fehlgeschlagen und Scan abgeschlossen.

Aufbewahrung und Unveränderlichkeit

Repositorys können sehr schnell wachsen – was zu hohen Speicherkosten führen kann, wenn Sie keine gute Bereinigungsstrategie haben. Aus diesem Grund ist es ratsam, alte Bilder, die nicht mehr benötigt werden, zu bereinigen. Einige Registries bieten daher vorgefertigte Aufbewahrungsrichtlinien, in denen Sie festlegen können, welche Bilder bestimmten Regeln entsprechen, die aufbewahrt werden sollen, und wie lange. Sobald Bilder aus der Aufbewahrungsfrist herausfallen, werden sie gelöscht.

Ein weiterer Anwendungsfall ist, dass standardmäßig jeder ein neues Image mit demselben Image-Tag hochladen kann, wodurch die vorherige Image-Version ohne Tag bleibt. Um dies zu verhindern, bieten einige Registries Unveränderbarkeitsregeln, die verhindern, dass Tags aus bestehenden Images entfernt werden!

Überwachung unserer Registries

Da Registries das Herzstück unserer Plattform sind, müssen wir sicherstellen, dass sie einwandfrei funktionieren. Wenn Registries keine Push- oder Pull-Anfragen mehr verarbeiten, keine Schwachstellenprüfungen mehr durchführen und keine Replikationen an andere Registries oder Benachrichtigungen mehr versenden können, haben wir ein Problem! Das bedeutet, dass wichtige Updates nicht schnell genug in die Zielumgebungen gelangen. Dies könnte bedeuten, dass eine Sicherheitslücke – obwohl sie durch ein neues Image behoben wurde – nicht geschlossen werden kann, da das neue Image nicht an die infizierte Umgebung geliefert werden kann. Es kann auch bedeuten, dass wir neue Funktionen nicht zum versprochenen Zeitpunkt ausliefern können.

Um den Zustand unserer Registries zu überwachen, können wir verschiedene Zustandsmetriken beobachten. Bei selbst gehosteten Registries werden diese Metriken häufig über Prometheus oder eine benutzerdefinierte REST-API bereitgestellt. Bei SaaS-gehosteten Registries werden diese Metriken in der Regel über die Monitoring-Service-API des Anbieters bereitgestellt, beispielsweise AWS CloudWatch.

Eine gute Referenz ist Harbor, das zuvor erwähnte CNCF-Projekt. Es stellt über **Prometheus** \[14\] viele wichtige Kennzahlen bereit, darunter die Anzahl der Projekte und Repositorys innerhalb eines Projekts, den belegten Speicherplatz, die Anzahl der ausgeführten und in der Warteschlange stehenden Aufgaben sowie Leistungskennzahlen zu den Harbor-APIs (z. B. wie lange es dauert, Artefakte zu pushen oder zu pullen).

Abbildung 5.7: Überwachung unserer Registry zur frühzeitigen Erkennung potenzieller Probleme

Harbor ist auch ein Early Adopter von OpenTelemetry, dem CNCF-Projekt, das ursprünglich einen Standard für verteiltes Tracing in der Cloud-Native-Community eingeführt hat. Harbor bietet einen **OpenTelemetry-Exporter** \[15\], der Traces mit noch detaillierteren Informationen generiert, die sowohl für die Zustandsüberwachung als auch für die Fehlerbehebung verwendet werden können!

Registries – die zentrale Drehscheibe für alle unsere Artefakte

**Container- oder Artefakt-Registries** sind die zentrale Drehscheibe für alle Software, die erstellt und bereitgestellt wird. Sie bieten eine zentrale Möglichkeit, den Zugriff auf alle Software zu verwalten, zu scannen, zu verteilen und durchzusetzen, bevor sie bereitgestellt wird. Sie müssen daher als äußerst kritische Komponente behandelt werden, die beobachtet werden muss, um Verfügbarkeit und Ausfallsicherheit zu gewährleisten, und die selbst sicher sein muss!

Nachdem wir nun über die Bedeutung unserer Artefakt-Registrierung gesprochen haben, wollen wir uns nun ansehen, wie all diese Komponenten in unseren End-to-Release-Prozess integriert sind.

Definition des Release-Prozesses und -Managements

Wir haben alle Bausteine behandelt, die für die Erstellung und Bereitstellung von Software erforderlich sind. CI erstellt neue Container-Images oder Artefakte und überträgt sie in ein Register. Wir wissen, dass Register in der Lage sind, nach Schwachstellen zu suchen, sich auf andere Register zu replizieren, andere Tools über Aktivitäten zu benachrichtigen und Zugriffskontrollen durchzusetzen.

Wir haben auch etwas über GitOps und seinen Pull-Ansatz gelernt, mit dem der gewünschte Bereitstellungsstatus (Manifestdateien, Helm-Charts, Kustomize usw.) sichergestellt wird, wie er in einem Git-Repository in der Zielumgebung definiert ist.

Wir diskutieren nun, wie ein vollständiger End-to-End-Release-Prozess definiert und durchgesetzt werden kann und wie der Lebenszyklus von Artefakten von der ersten Erstellung über die erste Bereitstellung, die Weitergabe an andere Stufen und Updates auf neue Versionen bis hin zur möglichen Stilllegung, wenn die Software nicht mehr benötigt wird, verwaltet werden kann!

Die folgende Abbildung verdeutlicht, dass das Pushen eines neuen Images und dessen Replikation in andere Registries nur ein Teil des Puzzles ist. Die neue Version des Images muss auch in der Bereitstellungsdefinition referenziert werden, die in Mono- oder Poly-Git-Repositorys verwaltet wird. Bei mehreren Phasen (Entwicklung, QA, Produktion) und mehreren Regionen oder Clustern in einer Phase müssen wir diese neue Version auch zwischen den einzelnen Phasen und Regionen/Clustern befördern!

Abbildung 5.8: Release-Prozess – vom ersten Push bis zur Bereitstellung und Weitergabe, von Stufe zu Stufe

In der vorstehenden Abbildung stellt values.yaml die Werte für ein Helm-Chart dar. Es ist natürlich vereinfacht, da es noch viele weitere Werte gibt, die wir zuvor besprochen haben (z. B. Eigentumsverhältnisse, Anwendungskontext, Protokollstufe, Git-Commit-Hash, Container-Registry usw.).

Schauen wir uns nun an, wie diese Bereitstellungsaktualisierungen durchgeführt werden können, was zwischen den Phasen geschehen sollte, welche Rollout-Optionen wir haben und wie wir am besten den Überblick über einen Live-Bestand behalten können, um zu wissen, was wo, wann und von wem bereitgestellt wird!

Aktualisierung der Bereitstellung auf eine neue Version

Es gibt verschiedene Möglichkeiten, wie values.yaml für die erste Entwicklungsphase aktualisiert und dann in die nächsten Phasen überführt werden kann. Je nach den verwendeten Tools und dem Reifegrad oder den Prozessen, die in Unternehmen vorhanden sind, kann dies auf verschiedene Weise umgesetzt werden. Die Optionen wären wie folgt:

- **Aktualisierung als Teil der CI**: Sobald die CI ein neues Image in der Registry veröffentlicht, könnte sie einen Pull Request öffnen, um die Version im Repository für die erste Phase zu aktualisieren.
- **Aktualisierung über einen Registry-Webhook**: Wenn ein neues Image in die Registry hochgeladen wird, kann ein Webhook verwendet werden, um einen Pull Request zu öffnen. Dieser Ansatz ähnelt dem Vorgehen der CI. Allerdings wird der Prozess dadurch entkoppelt. Dies funktioniert auch unabhängig davon, welches Tool (z. B. CI) oder welcher Ersteller (z. B. Drittanbieter) eine neue Image-Version pusht.
- **Geplante Aktualisierungen**: Jede Stunde, jeden Tag um 8 Uhr morgens oder nach einem anderen Zeitplan kann ein Pull-Request mit den neuesten Versionsinformationen aus der Registry erstellt werden. Dies ermöglicht sowohl kontinuierliche Aktualisierungen als auch planmäßige Batch-Änderungen.
- **Manuelle Pull-Anfragen**: Als Vorstufe zur Automatisierung der Pull-Anfragen oder zur Durchsetzung einer obligatorischen manuellen Genehmigung kann die Versionsaktualisierung auch manuell durchgeführt werden.

Änderungen stapeln, um Abhängigkeiten zu bekämpfen

Bei einfachen Anwendungen oder Microservices, die unabhängig voneinander bereitgestellt werden können, reicht möglicherweise eine einzige Dateiaktualisierung aus. Oft müssen wir jedoch mehrere Änderungen in einer einzigen Änderungsanforderung zusammenfassen. Dies ist der Fall, wenn Änderungen von Änderungen in anderen Komponenten abhängig sind. Ein Beispiel für unser Finance One ACME könnte sein, dass die neue Version des Überweisungsdienstes auch eine neue Version des Kontoinformationsdienstes erfordert, was eine Änderung der Infrastruktur notwendig macht. Sie sehen, dass dies schnell komplex werden kann und eine vollständige Automatisierung erschwert.

Diese Änderungen sind schwer zu automatisieren und werden oft an ein Release-Management-Team zurückgegeben, das diese Abhängigkeiten manuell löst.

Es gibt andere Möglichkeiten, dieses Problem zu lösen. Ein Ansatz ist die Verwendung von Paketmanagern wie Helm, wobei ein Helm-Chart alle Konfigurationen enthalten kann, die für die Bereitstellung einer vollständigen Anwendung erforderlich sind. Helm-Charts können dann auch zu Artefakten werden, die in eine Registrierungsstelle hochgeladen werden.

Ein weiterer Ansatz, den wir in einem früheren Abschnitt gesehen haben, ist die Verwendung von Tools wie Crossplane, das IaC und Anwendung als Code bereitstellt. Das folgende Beispiel zeigt die Verwendung einer Komposition für eine Anwendung, die mehrere Komponenten enthält, wie z. B. die Geschäftslogik, einen Cache, einen Ingress und eine Datenbank:

apiVersion: composites.financialone.acme/v1alpha1

kind: FinancialBackend

metadata:

&nbsp; Name: tenantABC-eu-west

Spezifikation:

&nbsp; Service-Versionen:

&nbsp;   Geldtransfer: 2.34.3

&nbsp;   Kontoinformationen: 1.17.0

&nbsp; Redis-Cache:

&nbsp;   version: 7.4.2

&nbsp;   name: transfer-cache

&nbsp;   Größe: mittel

&nbsp; Datenbank:

&nbsp;   Größe: groß

&nbsp;   Name: accounts-db

Region: „eu-west“

&nbsp; Eingang:

&nbsp;   URL: „https://tenantABC-eu-west.financialone.acme”

KopierenErklären

Wie wir sehen können, gibt es verschiedene Möglichkeiten, dieses Problem der Anwendungsabhängigkeiten zu lösen.

Komplizierter wird es, wenn wir es mit anwendungsübergreifenden Abhängigkeiten oder Abhängigkeiten von gemeinsam genutzten Diensten zu tun haben, die unabhängig voneinander bereitgestellt und aktualisiert werden. Die Befolgung von Best Practices zur Definition guter und klarer APIs zwischen diesen Diensten und die Gewährleistung der Abwärtskompatibilität zwischen den Hauptversionen erleichtern dies. Weitere Informationen finden Sie in der vorhandenen Literatur oder in den Arbeiten der CNCF **TAG App Delivery** \[16\] zum Management von Anwendungs- und Bereitstellungsabhängigkeiten.

Prüfungen vor und nach der Bereitstellung

Sobald wir alle Änderungen an unserer Bereitstellungskonfiguration fertiggestellt und in Git committet haben, können wir die Bereitstellung im Zielcluster durchführen. Wie bereits in diesem Kapitel erläutert, können wir entweder ein Push-Modell (z. B. eine Delivery-Pipeline, die unsere Änderungen bereitstellt) oder ein Pull-Modell (z. B. einen GitOps-Operator, der die neueste Version in Git mit dem Zielcluster synchronisiert) verwenden.

Bei beiden Ansätzen möchten wir einige Überprüfungen vor und nach der Bereitstellung durchführen, um Fragen wie die folgenden zu beantworten:

- **Vor der Bereitstellung: Sind wir bereit, diese Änderung bereitzustellen?**
    - Sind alle externen Abhängigkeiten bereit?
    - Wurden alle neuen Images erfolgreich gescannt und weisen sie keine Schwachstellen auf?
    - Gibt es keine laufenden Wartungsarbeiten oder Bereitstellungsquarantänen in der Zielumgebung?
    - Haben alle, die eine Bereitstellung genehmigen müssen, diese genehmigt?
- **Nach der Bereitstellung: War die Bereitstellung erfolgreich?**
    - Sind die aktualisierten Dienste verfügbar und bearbeiten sie Anfragen erfolgreich?
    - Erfüllt das System alle funktionalen und nicht-funktionalen Anforderungen?
    - Erfüllen alle Dienste ihre SLAs und **Service-Level-Ziele** (**SLOs**)?
    - Wurden alle über die Bereitstellung informiert?
    - Kann die Bereitstellung zur nächsten Stufe weitergeleitet werden?

Die Überprüfungen vor der Bereitstellung können auf verschiedene Weise durchgeführt werden. Einige können als Teil des Pull-Request-Ablaufs implementiert werden (z. B. können Pull-Requests nicht zusammengeführt werden, wenn nicht alle Überprüfungen vor der Bereitstellung erfüllt sind). Sie können auch innerhalb einer Bereitstellungspipeline validiert oder als Pre-Sync-Hook in GitOps-Tools implementiert werden.

Die Überprüfungen nach der Bereitstellung können nach Abschluss der Bereitstellung aus der Bereitstellungspipeline sowie über Post-Sync-Hooks in GitOps-Tools implementiert werden.

Ein Tool, das Vor- und Nachbereitungsprüfungen auf Kubernetes unabhängig von der Art der Bereitstellung ermöglicht, ist das CNCF-Projekt Keptn. **Keptn** kann Kubernetes-Bereitstellungen stoppen, wenn die Vorbereitungsprüfungen nicht erfolgreich sind. Keptn kann auch Nachbereitungsprüfungen durchführen, z. B. Tests ausführen, SLOs bewerten oder Teams benachrichtigen.

Weitere Informationen zu Keptn finden Sie in der Dokumentation \[17\].

Benachrichtigungen zur Bereitstellung

Sobald wir wissen, dass eine neue Bereitstellung die Überprüfung nach der Bereitstellung bestanden oder nicht bestanden hat, können wir diese Informationen nutzen und die Personen oder Tools benachrichtigen, die von diesen Informationen profitieren können. Unabhängig davon, ob Sie Tools wie Keptn, die Benachrichtigungen der GitOps-Tools oder die Pipeline verwenden, finden Sie hier einige Beispiele, wohin diese Informationen gesendet werden können:

- **Ein Chat**: Benachrichtigen Sie die Entwicklungsteams in ihrem Slack-Kanal, dass ihre neueste Bereitstellung entweder bereit ist oder die Prüfungen nicht bestanden hat.
- **Ein Ticket**: Aktualisieren Sie den Pull Request oder ein Jira-Ticket mit den Informationen zum Bereitstellungsstatus.
- **Eine Statusseite**: Halten Sie eine Deployment-Statusseite mit Informationen zu Version, Umgebung und Zustand auf dem neuesten Stand.
- **Ein Observability-Backend**: Senden Sie ein Bereitstellungsereignis an Ihr Observability-Backend.

Bereitstellungsereignisse an das Observability-Backend

Observability-Tools verfolgen nicht nur Metriken, Protokolle und Traces, sondern können auch Ereignisse wie Bereitstellungs- oder Konfigurationsänderungen verfolgen. Viele Observability-Tools (**Dynatrace**, **Datadog**, **New Relic** usw.) können diese Ereignisse nutzen und sie mit einer Änderung im Verhalten der Anwendung in Verbindung bringen. Dies kann die Reaktion auf Vorfälle erheblich verbessern, da sie mit einer bestimmten Bereitstellungsänderung in Verbindung gebracht werden kann.

Beförderungen zwischen Stufen

Angenommen, wir haben eine neue Version in der Entwicklung, die alle Prüfungen nach der Bereitstellung erfolgreich bestanden hat. Wie werden diese Änderungen von der Entwicklung zur Qualitätssicherung und dann in die Produktion übertragen? Muss jede Änderung bis in die Produktion übertragen werden oder nicht? Werden neue Versionen auf einmal in allen Produktionsumgebungen ausgerollt oder gibt es dafür bessere Strategien?

Hier sind einige Strategien, die wir in Organisationen gesehen haben, mit denen wir in der Vergangenheit zusammengearbeitet haben. Bei allen diesen Strategien wird ein Pull Request erstellt, um die neue Bereitstellungsdefinition vom Git-Speicherort der unteren Stufe zum Git-Speicherort der höheren Stufe zu übertragen:

- **Automatisiert**: Oft zwischen Entwicklungs- und QA-Umgebungen zu beobachten. Jedes Mal, wenn die Überprüfungen nach der Bereitstellung erfolgreich sind, kann dies einen automatisierten Pull Request auslösen. Dadurch wird sichergestellt, dass alle Entwicklungsänderungen, die die grundlegenden Überprüfungen durchlaufen haben, schnell in eine Umgebung übertragen werden, die für gründlichere Tests verwendet wird.
- **Geplant**: Beispielsweise wird einmal täglich die neueste Version aus der Entwicklung oder QA in eine spezielle Testumgebung (z. B. eine Leistungstestumgebung) befördert. Dadurch wird sichergestellt, dass das Team täglich Feedback zu Änderungen des Leistungsverhaltens seiner Updates aus den letzten 24 Stunden erhält.
- **Kontrolliert/manuell**: Dies geschieht in der Regel, je näher Sie der Produktion kommen. Änderungen, die die Qualitätssicherung und die Leistungstests erfolgreich durchlaufen haben, werden als sicher markiert, um in höhere Umgebungen übertragen zu werden. Die tatsächliche Übertragung erfolgt in der Regel manuell, während der Pull Request selbst möglicherweise bereits automatisch erstellt wird (aber nicht automatisch genehmigt wird), beispielsweise aus den Versionen, die die Leistungstestphase erfolgreich durchlaufen haben!
- **Mehrstufig in der Produktion**: Bei mehreren Produktionsclustern ist es üblich, die Änderungen zunächst in einem Cluster einzuführen. Anschließend wird überprüft, ob alles funktioniert, und dann werden die übrigen Cluster ausgerollt. Dieser erste Cluster kann nur für den internen Gebrauch oder für Benutzer vorgesehen sein, die wissen, dass sie Updates zuerst erhalten (z. B. Freunde und Familie oder Mitglieder einer Early-Access-Gruppe). Bei der Bereitstellung in mehreren Regionen oder bei mehreren SaaS-Anbietern ist es ebenfalls ratsam, eine klare Reihenfolge festzulegen (z. B. zuerst in Europa beginnen und dann in den USA ausrollen).

Die Verwendung mehrerer Qualitätskontrollstufen und einer gestaffelten Rollout-Strategie in unseren verschiedenen Produktionsumgebungen hat ein Ziel: das Risiko fehlgeschlagener Bereitstellungen zu reduzieren!

Blue/Green, Canary und Feature Flagging

Die Verwendung mehrerer Phasen mit Checks vor und nach der Bereitstellung reduziert zwar bereits das Risiko, aber wir können für jede einzelne Bereitstellung noch mehr tun: **progressive** Bereitstellungsstrategien wie Blue/Green, Canary oder Feature Flags. Was das genau ist, haben wir bereits im Abschnitt „Kontinuierliche Bereitstellung – Entkopplung von Bereitstellungen und Releases“ ausführlich erläutert.

Im Zusammenhang mit dem Release-Prozess ist dies ein wichtiges Thema, da es mehrere offene Fragen gibt:

- Wer erhält die neue Version? Ist es ein bestimmter Prozentsatz der Benutzer oder eine bestimmte Gruppe?
- Wie messen und validieren Sie, ob die Einführung erfolgreich war?
- Wer ist für die Entscheidung über ein Rollforward oder Rollback verantwortlich?

Genau wie bei der Validierung einer Bereitstellung durch Post-Deployment-Checks können wir dasselbe auch bei der progressiven Bereitstellung tun. Open-Source-Tools wie **Argo Rollouts** \[18\] und **Flagger** \[19\] oder kommerzielle Tools bieten automatisierte Analysen zwischen den Phasen des progressiven Rollouts. Dies funktioniert in der Regel durch Abfragen von Daten aus der Observability-Plattform, z. B. Prometheus, um zu überprüfen, ob sich die neue Version in Bezug auf wichtige Service-Level-Indikatoren wie Fehlerrate bei Anfragen, Antwortzeit, Speicher- und CPU-Auslastung nicht von der bestehenden Version unterscheidet. Für weitere Details empfiehlt es sich, die Dokumentation der jeweiligen Tools zu lesen, die für progressive Rollouts verwendet werden.

Release-Bestand

Der Mehrwert der Automatisierung des Bereitstellungs- und Release-Prozesses besteht darin, dass Engineering-Teams Updates häufiger in den verschiedenen Zielumgebungen veröffentlichen können. Je einfacher wir diese Automatisierung über unsere Plattform verfügbar machen, desto mehr Teams werden letztendlich mehr Releases bereitstellen.

Mit Release-Inventaren können wir nachverfolgen, welche Versionen derzeit in welchen Umgebungen von welchen Teams veröffentlicht werden. Aus Sicht der Plattformentwicklung können wir eine einheitliche Definition genau dieser Informationen durchsetzen: Version, Umgebung und Eigentumsverhältnisse. Wenn alles als Code konfiguriert ist, bedeutet dies, dass diese Informationen in Git verfügbar sind. Bei Verwendung von Kubernetes als Zielplattform können wir diese Informationen auch als Anmerkungen zu unseren Kubernetes-Objekten (Deployments, Pods, Ingress) hinzufügen.

In den vorherigen Beispielen haben wir bereits einige der Standard-K8s-Anmerkungen hervorgehoben. Hier ist ein Ausschnitt aus einer Deployment-Definition:

apiVersion: apps/v1

kind: Deployment

metadata:

&nbsp; name: fund-transfer-service

spec:

&nbsp; …

&nbsp; Vorlage:

&nbsp;   Metadaten:

&nbsp;     Anmerkungen:

&nbsp;       Eigentümerteam: team-us

&nbsp;       app.kubernetes.io/name: fund-transfer

&nbsp;       app.kubernetes.io/part-of: backend-tenant-2

&nbsp;       app.kubernetes.io/version: 1.5.1

KopierenErklären

Mit diesen Informationen in K8s können wir einfach die K8s-API jedes K8s-Clusters abfragen, um einen Überblick über alle Bereitstellungen nach diesen Labels zu erhalten. Wir könnten dann einen Überblick wie diesen erhalten:

| **Cluster** | **Release** | **Teil von** | **Eigentümer** |
| --- | --- | --- | --- |
| dev | Geldtransfer:1.5.1 | Backend | team-at |
| dev | Kontoinformationen:1.17.2 | Backend | team-ae |
| qa  | Überweisung:1.4.9 | Backend | team-at |
| qa  | Kontoinformationen:1.17.1 | Backend | team-ae |
| prod-eu | Überweisung:1.4.7 | Backend-Mandant-1 | team-de |
| prod-eu | Kontoinformationen:1.17.1 | Backend-Mandant-1 | team-de |
| prod-us | Überweisung:1.4.6 | Backend-Mandant-2 | team-us |
| prod-us | Kontoinformationen:1.17.0 | Backend-Mandant-2 | team-us |

Tabelle 5.2: Release-Bestand basierend auf Metadaten zu bereitgestellten Artefakten

Observability-Tools bieten diese Funktion häufig, da sie bereits die K8s-APIs abrufen, um den Zustand des Clusters, Ereignisse und Objekte einschließlich dieser Metadaten zu beobachten.

Ein anderer Ansatz besteht darin, diese Informationen direkt aus Git zu parsen. Tools wie Backstage tun genau das und bieten mit diesen Informationen einen leicht durchsuchbaren Softwarekatalog.

Release-Management – vom Start bis zur Missionskontrolle

Für viele Unternehmen endet der Release-Prozess mit der tatsächlichen Bereitstellung einer neuen Version in der Produktion, wenn die Betriebsteams alle Aspekte der Aufrechterhaltung des Betriebs der Software „ “ übernehmen. Diese beiden Phasen werden oft auch als **Start** und **Missionskontrolle** bezeichnet, in Anlehnung an die Art und Weise, wie die NASA ihre Weltraummissionen verwaltet.

Vor vielen Jahren wurde die DevOps-Bewegung durch prominente Beispiele wie die AWS-Plattform beflügelt, die den Ansatz „You built it, you run it!“ (Du hast es gebaut, du betreibst es!) propagierte. Das bedeutete, dass die Verantwortung der Entwickler nicht mit der Erstellung eines Artefakts und dessen Übergabe an die sogenannte „Ops Wall“ endete. Die Entwickler mussten die volle Verantwortung und Eigentumsrechte für ihren Code von der Entwicklung bis hin zur Produktion übernehmen. Sie mussten sich um Vorfälle und Updates kümmern, bis ihr Code schließlich ausgemustert wurde.

Angesichts der komplexen Umgebungen von heute ist es sehr schwierig, jeden Aspekt (Code und Infrastruktur) zu kontrollieren. Mit Platform Engineering versuchen wir, das Versprechen von DevOps wieder einzulösen, indem wir Self-Services anbieten, um die Komplexität zu reduzieren und Teams die Möglichkeit zu geben, mehr Verantwortung für den gesamten Lebenszyklus ihrer Software zu übernehmen.

Beim Aufbau zukünftiger Plattformen muss unser Fokus darauf liegen, Self-Services bereitzustellen, um den gesamten Lebenszyklus eines Artefakts zu orchestrieren. Tatsächlich ist die Orchestrierung des gesamten Lebenszyklus einer Anwendung als einzelnes Artefakt in der Regel nur ein Bruchteil einer Anwendung. **Die Lebenszyklus-Orchestrierung** umfasst die Erstellung, Bereitstellung und Veröffentlichung, aber auch alle Anwendungsfälle, die für den Produktionssupport erforderlich sind. Dazu gehören Ausfallsicherheit durch Skalierung, Incident Management, Zugriff auf die richtigen Beobachtungsdaten für die Fehlerbehebung und automatisierte Bereitstellung, um Korrekturen und Updates zu pushen.

Im nächsten Abschnitt befassen wir uns eingehend mit der Lebenszyklusorchestrierung, der Erhöhung der Transparenz durch die Beobachtbarkeit unserer Lebenszyklen und der Frage, wie ein ereignisgesteuertes Modell dazu beitragen kann, die Komplexität von Pipeline- und Orchestrierungscode zu reduzieren.

Erreichen einer nachhaltigen CI/CD für DevOps – Orchestrierung des Anwendungslebenszyklus

Vom Erstellen über das Veröffentlichen, Bewerben und Bereitstellen bis hin zum Freigeben und Beheben. Das sind eine Menge Aufgaben, die automatisiert werden müssen, um den gesamten Lebenszyklus unserer Artefakte und Anwendungen zu orchestrieren. Die Herausforderung, die wir bei Teams gesehen haben, die die End-to-End-Verantwortung übernehmen, besteht darin, dass die meisten dieser Skripte sich mit Folgendem befassen:

- Auslösen eines bestimmten (fest programmierten) Tools
- Dies in einer bestimmten (fest programmierten) Umgebung
- Anschließend Warten, bis das Tool seine Aufgabe abgeschlossen hat
- Parsen des spezifischen Ergebnisformats
- Auf der Grundlage des Parsing-Ergebnisses entscheiden, was als Nächstes zu tun ist (fest codiert)

Dieser Skriptcode wird dann oft zwischen verschiedenen Projekten kopiert und eingefügt, leicht modifiziert und angepasst. Korrekturen oder Anpassungen an einem einzelnen Skript lassen sich nur schwer auf alle anderen Varianten übertragen, da es keine einfache Möglichkeit gibt, alle diese Skripte zu verfolgen. Dies führt zu einem hohen Wartungsaufwand, macht es schwierig, die in diesen Skripten verwendeten Prozesse oder Tools zu ändern, und nimmt den Ingenieuren Zeit für ihre regulären Aufgaben.

Es ist nichts falsch daran, die Leistungsfähigkeit von Pipeline-Skripten zu nutzen. Viele der Pipeline-Automatisierungstools bieten auch Abstraktionen, Code-Wiederverwendung durch Bibliotheken und andere Funktionen, um Code-Duplikate zu reduzieren und die Wiederverwendbarkeit zu erhöhen. Achten Sie also je nach den von Ihnen verwendeten Tools darauf, diese Best Practices zu befolgen!

Es gibt einen anderen Ansatz, der zur ereignisgesteuerten Natur moderner Cloud-nativer Anwendungen und Cloud-nativer Umgebungen passt: **die ereignisgesteuerte Orchestrierung des Lebenszyklus**!

Im nächsten Abschnitt werden wir uns näher mit diesem Ansatz befassen, da er viel Flexibilität und zentralisierte Beobachtbarkeit bietet und zu einer nachhaltigeren Art der Automatisierung von CI/CD und Operationen führt!

Beobachtbarkeit von Artefakt-Lebenszyklusereignissen

Die Grundlage für die ereignisgesteuerte Orchestrierung sind Lebenszyklusereignisse, wie sie in [Kapitel 3](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/3) beschrieben wurden. Dabei geht es darum, den gesamten Lebenszyklus eines Artefakts zu beobachten: vom ersten Git-Commit des Codes über das Erstellen und Pushen von Container-Images in eine Registry bis hin zur Freigabe in jeder Phase, bis das Artefakt aktualisiert oder außer Betrieb genommen wird, einschließlich aller Schritte dazwischen.

Bisher haben wir in diesem Kapitel viele dieser Lebenszyklus-Schritte besprochen und auch hervorgehoben, wie einige dieser Lebenszyklusereignisse extrahiert werden können:

- **CI/CD-Pipelines** können Ereignisse ausgeben, wenn sie erstellt oder bereitgestellt werden
- **Artefakt-Registries** stellen Webhooks bereit, wenn Container gepusht, gezogen oder gescannt werden
- **GitOps**\-Tools können Benachrichtigungen für PreSync, Sync, PostSync und SyncFailed senden.
- Git-Workflows können verwendet werden, um Ereignisse zu senden, wenn sich Code ändert oder befördert wird
- Tools wie **Keptn** bieten Ereignisse vor und nach der Bereitstellung für einzelne Bereitstellungen sowie für komplexe Anwendungen
- Containerplattformen wie Kubernetes machen Ereignisse zum Status der Bereitstellung sichtbar

**CDEvents** \[20\], ein Projekt der Continuous Delivery Foundation, erweitert die CloudEvents-Spezifikation, die bereits ein abgeschlossenes CNCF-Projekt mit breiter Akzeptanz im Ökosystem ist. CDEvents wurde ursprünglich ins Leben gerufen, um Ereignisse für alle Lebenszyklusphasen beim Erstellen, Testen und Bereitstellen zu standardisieren. Vor kurzem wurde es erweitert, um auch die Lebenszyklusphasen von Bereitstellungen im Betrieb, wie z. B. Produktionsvorfälle, abzudecken.

Die Idee dahinter ist, dass Tools, die diesen Ereignisstandards entsprechen, leichter mit allen anderen Tools im Ökosystem zu integrieren sind. Anstatt Hardcode-Integrationen zwischen Tools verwalten und pflegen zu müssen, kommunizieren diese Tools über offene Standard-APIs und Ereignisse. Tools können diese Ereignisse ausgeben; beispielsweise hat Jenkins ein neues Artefakt erstellt, und andere Tools können diese abonnieren (z. B. kann GitLab sie abonnieren und einen Workflow zum Scannen und Veröffentlichen des Containers auslösen). Diese Lebenszyklusphase würde ebenfalls ein standardisiertes Ereignis generieren.

Alle Ereignisse verfügen über einen Mindestsatz an Eigenschaften zur Identifizierung der Phase, des Artefakts und des beteiligten Tools sowie über zusätzliche Eigenschaften, die obligatorisch sind (z. B. initialer Git-Commit, Version, Umgebung und zuständiges Team).

Wenn alle diese Ereignisse an einen zentralen Ereignishub gesendet werden, ermöglicht dies eine vollständig ereignisgesteuerte Orchestrierung des Lebenszyklus von Artefakten.

Wenn Sie beispielsweise beschließen, Entwicklungsteams über neue Bereitstellungen in ihrem Slack zu benachrichtigen, können Sie die Bereitstellungsereignisse einfach abonnieren und dieses Ereignis an Slack weiterleiten. Wenn Sie das Chat-Tool zu einem anderen wechseln, ändern Sie einfach dieses Ereignisabonnement. Es ist nicht notwendig, den gesamten Code in allen Pipelines zu suchen, die derzeit Benachrichtigungen senden, da dies durch eine einfache Änderung des Ereignisabonnements erfolgt.

Zusammenfassend lässt sich sagen, dass die Verwendung eines klar definierten Satzes von Lebenszyklusereignissen über alle Tools und Phasen hinweg viele Möglichkeiten in unserem Plattform-Engineering-Ansatz eröffnet:

- **Rückverfolgbarkeit**: Wir können jedes Artefakt von seiner ersten Erstellung bis zum Ende seines Lebenszyklus verfolgen. So können wir sehen, wo sich Artefakte befinden (Release-Bestand), wo sie stecken geblieben sind und wer dafür verantwortlich ist, ein Artefakt in eine bestimmte Umgebung zu lassen.
- **Messung**: Wir können messen, wie viele Artefakte den Lebenszyklus durchlaufen und wie lange dies dauert. Dies ist die Grundlage für die Berichterstattung der DORA-Effizienzmetriken!
- **Interoperabilität**: Wir können neue Tools problemlos integrieren oder ersetzen, wenn sie alle denselben Standards entsprechen (z. B. ist der Wechsel von einem Benachrichtigungstool zu einem anderen nur eine Frage der Änderung eines Ereignisabonnements).
- **Flexibilität**: Wie beim Ersetzen von Tools können wir unsere Bereitstellungsprozesse leicht anpassen, indem wir zusätzliche Tools für bestimmte Ereignisse hinzufügen (z. B. kann ein zusätzlicher obligatorischer Sicherheitsscan für Bereitstellungen in bestimmten Umgebungen durch ein Ereignisabonnement eines Sicherheitsscan-Tools durchgeführt werden).

Verschaffen wir uns einen kurzen Überblick über die Bausteine eines solchen ereignisgesteuerten Systems im Vergleich zur Erstellung und Pflege langwieriger, komplexer Automatisierungsskripte, die eine Vielzahl von Prozesslogiken enthalten müssen.

Arbeiten mit Ereignissen

Der erste Schritt besteht darin, dass die Tools, die wir entlang des Artefakt-Lebenszyklus verwenden, diese Ereignisse ausgeben. Wenn man sich CDEvents (eine Erweiterung von CloudEvents) ansieht, gibt es mehrere Tools im Ökosystem, die bereits sofortige Unterstützung dafür bieten, wie z. B. Jenkins, Tekton, Keptn, Tracetest, Spinnaker und andere.

Die Tools, die noch nicht integriert sind, können diese Ereignisse mithilfe der verfügbaren SDKs problemlos ausgeben. Das folgende Code-Beispiel in Python erstellt ein Pipeline Run Finished Event (cdevents.new_pipelinerun_finished_event) mit Metadaten, die die Pipeline, das Artefakt oder den Eigentümer identifizieren:

import cdevents

event = cdevents.new_pipelinerun_finished_event(

&nbsp; context_id="git-abcdef1231",

&nbsp; context_source="jenkins",

&nbsp; context_timestamp=datetime.datetime.now(),

&nbsp; subject_id="pipeline_job123",

&nbsp; custom_data={

&nbsp;   "owner": "dev-team-backend",

&nbsp;   „part-of”: „backend-services”,

&nbsp;   "name" : "fund-transfer-service"

&nbsp; },

&nbsp; subject_source="build",

&nbsp; custom_data_content_type="application/json",

&nbsp; pipeline_name="backendBuildPipeline",

&nbsp; url="https://finone.acme/ci/job123",

)

\# Erstellen Sie ein CloudEvent aus dem CDEvent

cloudevent = cdevents.to_cloudevent(event)

\# Erstellt die HTTP-Anfrage-Darstellung des CloudEvents im strukturierten Inhaltsmodus

headers, body = to_structured(event)

\# An den Event-Bus senden, Datenspeicher

requests.post("&lt;some-url&gt;", data=body, headers=headers)

KopierenErklären

Das vorstehende Python-Codebeispiel erstellt ein neues pipelinerun_finished_event, das die abgeschlossene Ausführung einer Pipeline anzeigt. Die zusätzlichen Kontextdaten geben an, um welche Pipeline es sich handelt und wann sie erstellt wurde, und ermöglichen es uns, zusätzliche Metadaten bereitzustellen, z. B. Eigentumsverhältnisse, Artefakte oder die Anwendung, zu der diese Pipeline gehört.

Unabhängig davon, ob Sie den CDEvents-Standardvorschlag verwenden oder Ihre eigenen Lebenszyklusereignisse senden, ist es ratsam, sich an CloudEvents zu orientieren, da dieses Projekt bereits über zahlreiche Branchenintegrationen verfügt, die CloudEvents entweder ausgeben oder konsumieren können, darunter beispielsweise Knative!

Abonnieren von Ereignissen zur Orchestrierung

Sobald alle unsere Tools standardisierte Ereignisse ausgeben, können wir unseren Artefakt-Lebenszyklusprozess einfacher orchestrieren, indem wir die Tools, die wir in den Prozess einbinden möchten, die Ereignisse abonnieren lassen, auf die sie reagieren sollen.

Wir haben dasselbe Konzept bereits weiter oben in diesem Kapitel besprochen, als wir über die Verwendung der Webhook-Funktionen von Tools wie Argo CD oder Harbor gesprochen haben, um zu reagieren, wenn ein neues Artefakt verfügbar ist oder wenn eine neue Bereitstellung erfolgreich synchronisiert wurde.

Der Vorteil eines Standard-Ereignismodells besteht darin, dass Tools nicht mehr einen bestimmten Webhook eines bestimmten Tools (z. B. Argo CD-Webhooks) abonnieren müssen. Stattdessen können wir einen zentralen Ereignishub abonnieren, der alle standardisierten Lebenszyklusereignisse von allen beteiligten Tools empfängt, wie hier dargestellt:

Abbildung 5.9: Alle Tools senden und abonnieren standardisierte Lebenszyklusereignisse

Da alles auf einem Ereignisstandard basiert, sind keine Punkt-zu-Punkt-Tool-Integrationen oder fest codierte Tool-Integrationen in Pipeline-Skripten mehr erforderlich. Anstatt beispielsweise von jeder Pipeline, die einen neuen Build bereitstellt, eine Benachrichtigung an Slack oder Mattermost zu senden, können wir einfach das Ereignis dev.cdevents.service.published abonnieren und die Details zu diesem Dienst an unser Chat-Tool weiterleiten lassen.

Wenn dieses Tool heute Slack ist und wir uns zu einem späteren Zeitpunkt entscheiden, zu einem anderen Tool zu wechseln, ändern wir einfach dieses Abonnement.

Ein weiterer Anwendungsfall ist die Verwendung verschiedener Tools als Teil des Prozesses, die in unterschiedlichen Umgebungen aktiv sind. Da diese standardisierten Ereignisse viele Metadaten enthalten (z. B. in welcher Umgebung ein Dienst bereitgestellt wird), können wir Ereignisse für eine bestimmte Umgebung abonnieren. Die folgende Tabelle zeigt einige Beispiele:

| **Quell-Tool** | **Eigenschaften des Ereignisses** | **Abonniert von** | **Aktion** |
| --- | --- | --- | --- |
| Argo | **Typ**: service.deployed<br><br>**Umgebung**: Staging<br><br>**Artefakt**: fund-transfer:2.3<br><br>**Eigentümer**: team-backend | K6, wenn Umgebung == „Staging“ | Einfache Last ausführen |
| .   |     | Slack wenn Eigentümer == team-backend | Benachrichtigung an den Backend-Slack-Kanal des Teams senden |
|     |     | OTel Collector | Sammeln aller Ereignisse zur Weiterleitung an das Observability-Backend |

Tabelle 5.3: Dasselbe Ereignis aus Argo kann von verschiedenen Tools für verschiedene Aktionen abonniert werden

Einige Tools bieten bereits standardmäßige Unterstützung für CloudEvents, wobei sie entweder eine CloudEvent-Quelle abonnieren oder einen API-Endpunkt bereitstellen können, der CloudEvents verarbeiten kann. Für andere ist es erforderlich, eine schlanke Integrationsschicht zu erstellen, über die diese Ereignisse abonniert und dann an das Zieltool weitergeleitet werden. Dies kann auch mithilfe von Event-Bus-Systemen implementiert werden, die CloudEvents unterstützen.

Ereignisse analysieren

Nachdem wir nun wissen, wie Ereignisse gesendet werden und wie sie von anderen Tools abonniert werden können, können wir diskutieren, wie wir sie nutzen können, um zu analysieren, wie gut unsere Lebenszyklusprozesse tatsächlich funktionieren.

Gut definierte Ereignisse, die einen Zeitstempel, eine Lebenszyklusphasen-Definition (= Ereignistyp) und einen gewissen Kontext (Artefakt, Umgebung, Eigentümer) haben, können analysiert werden, um Fragen wie die folgenden zu beantworten:

- Wie viele Bereitstellungen finden in einer bestimmten Umgebung statt?
- Wie viele Bereitstellungen werden für eine bestimmte Anwendung oder einen bestimmten Mandanten durchgeführt?
- Wie aktiv ist ein Team basierend auf den Informationen zur Eigentümerschaft?
- Wie viele Artefakte schaffen es von der Entwicklung bis zur Produktion?
- Welche Artefakte benötigen viel Zeit und wo werden sie auf dem Weg zur Produktion blockiert?
- Gibt es bestimmte Artefakte, die mehr Sicherheitslücken oder Produktionsprobleme verursachen als andere?
- Welche Tools, die an dem Prozess beteiligt sind, nehmen die meiste Zeit in Anspruch?
- Gibt es Tools, die am häufigsten für einen langsamen End-to-End-Prozess verantwortlich sind?

Es gibt wahrscheinlich noch viele weitere Fragen, die wir alle durch die Analyse dieser Ereignisse beantworten können.

Wie können wir sie analysieren? Sie können alle diese Ereignisse in eine Datenbank oder Ihre Observability-Plattform streamen. In Abbildung 5.9 haben wir OpenTelemetry aufgenommen, da Ereignisse einfach erfasst, an Ihr Observability-Backend weitergeleitet und dort analysiert werden können.

Transparenz in CI/CD durch Ereignisbeobachtbarkeit

Wenn alle Ereignisse mit all ihren Metadaten und klar definierten Typen, die die Lebenszyklusphasen repräsentieren, an einem einzigen Ort gespeichert sind, erhalten wir viel Transparenz in den Integrations-, Bereitstellungs- und Betriebsprozessen. Mit diesen Daten können wir unsere Prozesse optimieren, was zu mehr Nachhaltigkeit führt.

Die Automatisierung von CI/CD und Betrieb führt in der Regel zu einer Vielzahl von angepassten Codes, die in allen Projekten, in die sie kopiert wurden, gepflegt werden müssen. In diesem Abschnitt haben wir gelernt, dass die Umstellung auf einen ereignisgesteuerten Ansatz für das Lebenszyklusmanagement von Artefakten viele der Komplexitätsprobleme lösen kann, die sonst in benutzerdefinierten Skripten oder fest codierten Tool-to-Tool-Integrationen verborgen sind.

In [Kapitel 9](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/9) werden wir weitere Aspekte behandeln, wie wir durch die richtigen architektonischen Entscheidungen die technischen Schulden in allen unseren Plattformkomponenten reduzieren können.

IDPs – der Automatisierungs-Kraken in der Plattform

In diesem Kapitel haben wir bisher viel über die grundlegenden Bausteine zur Automatisierung des End-to-End-Prozesses von Build, Delivery, Deployment und Release gelernt. Wir haben über neue Ansätze zur Bereitstellung des gewünschten Zustands mit GitOps gesprochen, bei denen der gewünschte Zustand aus der Zielumgebung abgerufen und nicht von einem externen Tool, wie z. B. einer Pipeline, übertragen wird.

Wir haben die End-to-End-Release-Prozesse besprochen, die vom ersten Commit bis zur Veröffentlichung der Software für die Endbenutzer ablaufen. Schließlich haben wir über die Anwendung eines ereignisgesteuerten Ansatzes zur Orchestrierung unseres Artefakt-Lebenszyklus gesprochen, der einen zentralisierten Ereignishub bereitstellt, um alles, was geschieht, transparenter und beobachtbarer zu machen. Dies gibt uns auch mehr Flexibilität, da wir die Komplexität von Tool-Integrationen und Prozessdefinitionen aus Pipeline- oder Bash-Skripten in Ereignisabonnements und ereignisgesteuerte Workflows verlagern können.

In diesem letzten Abschnitt möchten wir einen kurzen Blick darauf werfen, welche dieser Konzepte mit bereits vorhandenen Tools umgesetzt werden können, welche neuen Ansätze es zur Lösung einiger der von uns diskutierten Herausforderungen gibt und wo Sie sich umsehen sollten, da in den letzten Jahren einige neue Tools – sowohl Open Source als auch kommerzielle – auf den Markt gekommen sind, die uns einen Teil dieser Arbeit abnehmen.

Dabei versetzen wir uns in die Lage unserer Benutzer, unserer Entwickler oder unserer Entwicklungsteams, da sie es sind, die sich auf eine neue Arbeitsweise einstellen müssen.

Bereitstellung von Vorlagen als „Golden Paths” für einen leichteren Einstieg!

Wir versuchen, viele neue Praktiken durchzusetzen, wie z. B. die Sicherstellung der richtigen Metadaten bei den Bereitstellungen (Version, Anwendungskontext, Eigentumsverhältnisse usw.) oder die Durchführung von Sicherheitslückenprüfungen als Teil jeder Build-Pipeline. In der Plattform-Engineering-Community werden diese auch als „Golden Paths” bezeichnet. Um sicherzustellen, dass diese Praktiken von Teams, die neue Projekte starten, leicht befolgt werden können, müssen wir sie leicht zugänglich und anwendbar machen!

Der einfachste und wirkungsvollste Ansatz ist die Bereitstellung von Software- oder Repository-Vorlagen. Dabei handelt es sich um Vorlagen in Form von Manifestdateien, Pipelines, Automatisierungsskripten usw., die Entwickler in einem Vorlagen-Repository finden und dann für ihre Projekte verwenden können.

Dieser Ansatz funktioniert zwar, zwingt die Ingenieure jedoch nicht dazu, diese Vorlagen auch wirklich zu verwenden. Außerdem handelt es sich um einen zusätzlichen manuellen Schritt, der auch zu Fehlern führen kann.

Eine Möglichkeit, dies zu vereinfachen und zu automatisieren, besteht darin, entweder eine CLI oder eine UI bereitzustellen, um neue Git-Repositorys zu initialisieren oder bestehende mit Best-Practice-Vorlagen zu aktualisieren. Dies kann entweder individuell entwickelt werden, oder wir können uns bestehende Lösungen ansehen, wie beispielsweise **Backstage**, ein CNCF-Projekt, das von Spotify gespendet wurde.

Die **Software**\-Vorlagenfunktion von Backstage wurde entwickelt, um Golden-Path-Vorlagen zum Einstiegspunkt für jeden Entwickler zu machen, der neue Softwarekomponenten erstellt. Vorlagen können von Fachexperten definiert werden, die wissen, wie man Pipelines richtig konfiguriert, automatisierte Tests und Bereitstellungen ermöglicht und Sicherheitsprüfungen durchführt.

Sobald die Vorlagen definiert sind, stehen sie über einen benutzerfreundlichen Assistenten zur Verfügung, der den Entwickler zur Eingabe einiger wichtiger Daten auffordert, z. B. welche Art von Dienst sie implementieren, Informationen zum Eigentumsrecht, Anforderungen an die Beobachtbarkeit oder Sicherheit usw. All diese Eingaben wirken sich dann auf die Erstellung eines neuen Repositorys oder die Aktualisierung eines bestehenden Repositorys mit den Dateien und Konfigurationen aus der Vorlage aus.

Weitere Informationen zu Vorlagen finden Sie in der ausführlichen Dokumentation und den Beispielen auf der **Backstage-Website** \[21\].

Abstraktionen durch Crossplane

Eine weitere Vereinfachung und Möglichkeit zur Durchsetzung von Best Practices besteht darin, bei der Definition Ihrer Anwendung oder Dienste eine zusätzliche Abstraktionsebene bereitzustellen. In K8s müssen wir unsere Bereitstellungen, Dienste, Ingress, **Persistent Volume Claims** (**PVCs**) und noch mehr definieren, wenn wir abhängige Dienste wie eine Datenbank, einen Cache oder andere erforderliche Softwarekomponenten bereitstellen müssen.

Im vorherigen Abschnitt über IaC haben wir das CNCF-Projekt Crossplane vorgestellt. **Crossplane** orchestriert sowohl die Infrastruktur als auch die Anwendungsbereitstellung durch Code und bietet ein Konzept der sogenannten **Composites**. Wir werden hier nicht weiter darauf eingehen, da wir bereits zuvor mehrere Beispiele dafür gegeben haben, wie man mit Composites eine Leistungstestumgebung bereitstellen und eine Finanz-Backend-Anwendung definieren kann, bei der der Entwickler nur die Versionen der Dienste angeben muss, die dann zusammen bereitgestellt werden sollen. Im Folgenden sind nur die ersten beiden Zeilen dieser Composite-Definition aufgeführt. Den Rest finden Sie im Abschnitt „Crossplane – IaC für Plattformen und Anwendungen“:

apiVersion: composites.financialone.acme/v1alpha1

kind: FinancialBackend

KopierenErklären

Bei der Bereitstellung von Abstraktionen ist es wichtig, diese den Entwicklern bekannt zu machen. Dies kann durch die Bereitstellung von Schulungsmaterialien oder einfach durch denselben Template-Ansatz erfolgen, wie zuvor beschrieben, unter Verwendung eines Tools wie Backstage.

Alles Git-Flow-gesteuert

Nun, es sollte keine Überraschung sein, dass Git unsere Quelle der Wahrheit ist – das haben wir bereits zu Beginn des Kapitels festgestellt. Die meisten Git-Lösungen bieten jedoch zusätzliche Funktionen, mit denen wir auch Standards und Prozesse durchsetzen können (z. B. GitHub-Workflows). Workflows können nach einem Zeitplan oder als Teil vieler verschiedener Ereignisse ausgelöst werden, die im End-to-End-Ablauf eines Git-gesteuerten Prozesses auftreten können (z. B. Push, Pull-Anfragen, Release).

Auf diese Weise können wir unsere Standards auch vor dem Erstellen und Pushen von Artefakten durchsetzen, beispielsweise durch die Validierung obligatorischer Metadatendateien, die wir für jede Bereitstellung erwarten (z. B. Informationen zum Eigentumsrecht). Wir können dies auch nutzen, um automatisch Code-Scans durchzuführen und Scorecards zu erstellen, oder um zu überprüfen, ob alle Abhängigkeiten sicher sind und keine bekannten Sicherheitslücken aufweisen.

Je nach ausgewähltem Git-Tool finden Sie in der Regel einen Marktplatz oder einen Best-Practice-Katalog mit Workflows und Aktionen, die für bestimmte Arten von Projekten ausgeführt werden können und sollten. Machen Sie sich mit allen Möglichkeiten vertraut, die Ihnen Ihr ausgewähltes Tool bietet.

Softwarekatalog

Sobald wir Entwicklern die Möglichkeit geben, mehr Software zu entwickeln, die allen unseren Prozessen entspricht, werden wir hoffentlich das Ergebnis in Form vieler neuer Dienste sehen. Das sind Dienste, über die auch andere Entwickler Bescheid wissen müssen, damit wir das Problem der „ ” vermeiden, bei dem Entwicklungsteams doppelte Dienste erstellen, und damit Entwickler dazu ermutigt werden, auf der Grundlage bestehender Dienste und APIs weitere Funktionen zu entwickeln.

Unser Ziel ist ein **Softwarekatalog,** der einen Überblick über alle verfügbaren Dienste und APIs bietet und im Idealfall auch einige Dokumentationen enthält.

Da Git die Quelle der Wahrheit ist, können wir die meisten dieser Informationen direkt aus Git extrahieren. Je nachdem, für welche Git-Lösung wir uns entscheiden, ist ein Softwarekatalog möglicherweise bereits Teil des Angebots. Es gibt jedoch noch weitere Dienste und APIs, die Teil des Softwarekatalogs sind, den eine Organisation besitzt und auf dessen Grundlage sie entwickeln kann (z. B. externe APIs oder vor Ort bereitgestellte Software von Drittanbietern).

Backstage, das Tool, das auch die zuvor erwähnte Vorlagenfunktion bietet, verfügt ebenfalls über einen Softwarekatalog. Es bezieht seine Daten aus der Analyse spezifischer Metadatendateien in Git-Repositorys, ermöglicht aber auch die Bereitstellung von Entitätsinformationen aus externen Datenquellen. Die folgende Abbildung stammt aus dem Backstage-Blog und zeigt, wie der Softwarekatalog von Spotify in Backstage aussieht:

Abbildung 5.10: Aus Entitätsmetadaten in Git extrahierter Softwarekatalog

Wie wir dem vorstehenden Screenshot entnehmen können, sind Softwarekataloge eine leistungsstarke Möglichkeit, um zu verstehen, welche Softwarekomponenten innerhalb einer Organisation verfügbar sind, um welche Art von Software es sich handelt ( ), wem sie gehört, wo der Quellcode zu finden ist und welche weiteren Informationen verfügbar sind.

Tools wie Backstage sind nicht das vollständige IDP, sondern stellen ein Portal – eine grafische Benutzeroberfläche – zu allen Daten dar, die für die Mehrheit der Benutzer eines IDP relevant sind.

Backstage ist zwar eine Option, aber es gibt noch viele andere Möglichkeiten. Von selbst entwickelten bis hin zu anderen Open-Source- oder kommerziellen Tools wie Cortex, Humanitec, Port oder Kratix.

Zusammenfassung

In diesem Kapitel haben wir viel über die zugrunde liegende Automatisierung und die Prozesse gelernt, mit denen ein Artefakt von der ersten Erstellung bis zur Produktion gelangt. Für moderne Plattformen sollte ein GitOps-Ansatz, bei dem wir Änderungen ziehen statt zu pushen, eine wichtige Überlegung sein. Wir haben gelernt, dass Git die Quelle der Wahrheit und Artefakte (Container- oder OCI-konforme Images) unsere Geschäftslogik in unseren Zielumgebungen sind.

Wenn ein Unternehmen wächst, ist es wichtig, gute Prozesse und Best Practices durchzusetzen. Damit die Durchsetzung funktioniert, muss sie leicht zugänglich sein und sollte durchgängig als Self-Service verfügbar sein, um den Kreativitätsfluss der Ingenieure nicht zu beeinträchtigen.

Dies bringt uns auch zum Thema des nächsten Kapitels. In [Kapitel 6](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/6) beschäftigen wir uns mit der Bedeutung von Self-Service-Funktionen, die wirklich auf die Bedürfnisse unserer Zielgruppe, nämlich unserer Entwickler, zugeschnitten sind. Wir werden diskutieren, wie wir die Best Practices dieser Golden Paths in unsere Plattform integrieren können, um die Arbeitsweise von Entwicklern erheblich zu verbessern.

Weiterführende Literatur

- \[1\] OpenFeature – https://openfeature.dev/
- \[2\] Crossplane – https://www.crossplane.io/
- \[3\] Renovate Bot – https://github.com/renovatebot/renovate
- \[4\] Semantic Versioning – https://semver.org/
- \[5\] Kustomize – https://kustomize.io/
- \[6\] Helm – https://helm.sh/
- \[7\] The Pragmatic Programmer – das DRY-Prinzip – https://media.pragprog.com/titles/tpp20/dry.pdf
- \[8\] Einrichten der GitOps-Verzeichnisstruktur – https://developers.redhat.com/articles/2022/09/07/how-set-your-gitops-directory-structure#directory_structures
- \[9\] Argo CD – https://argo-cd.readthedocs.io/en/stable/
- \[10\] Flux – https://fluxcd.io/flux/
- \[11\] Open Container Initiative – https://opencontainers.org/
- \[12\] Vorgeschlagene Container-Annotationen – https://github.com/opencontainers/image-spec/blob/main/annotations.md
- \[13\] Harbor – https://goharbor.io/
- \[14\] Harbor Prometheus-Metriken – https://goharbor.io/docs/2.10.0/administration/metrics/
- \[15\] Harbor Distributed Tracing – https://goharbor.io/docs/2.10.0/administration/distributed-tracing/
- \[16\] CNCF TAG App Delivery – https://tag-app-delivery.cncf.io/
- \[17\] Keptn – https://keptn.sh/
- \[18\] Argo Rollouts – https://argoproj.github.io/rollouts/
- \[19\] Flagger – https://flagger.app/
- \[20\] CDEvents – https://github.com/cdevents
- \[21\] Backstage – https://backstage.io/
