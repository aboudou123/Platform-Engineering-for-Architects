**Teil 2 – Entwerfen und Erstellen von Plattformen**

In Teil 2 befassen wir uns mit den technischen Grundlagen einer Plattform und führen Sie durch die relevanten Entscheidungspunkte während des Entwurfsprozesses. Dazu lernen Sie die vier Hauptkomponenten einer Plattform kennen: die Kernkomponenten und Infrastruktur, die durch Kubernetes repräsentiert werden, die für eine Plattform erforderliche Automatisierung, die relevanten Komponenten für eine selbstbedienungsorientierte, entwicklerfreundliche Plattform und die Schritte, die zum Aufbau sicherer und konformer Umgebungen erforderlich sind.

Entwurf des Plattformkerns – Kubernetes als einheitliche Schicht

Als Plattform-Engineering-Team müssen Sie eine wichtige Entscheidung über den zugrunde liegenden Technologie-Stack Ihrer Kernplattform treffen. Diese Entscheidung wird langfristige Auswirkungen auf Ihr Unternehmen haben, da sie die Fähigkeiten und Ressourcen bestimmt, die Sie für den Aufbau einer Plattform benötigen, die aktuelle und zukünftige Self-Service-Anwendungsfälle unterstützt.

**Kubernetes** – kurz **K8s** – ist nicht die Lösung für alle Probleme, aber beim Aufbau von Plattformen kann Kubernetes die Grundlage bilden.

In diesem Kapitel erhalten Sie Einblicke, warum Kubernetes für viele Plattform-Engineering-Teams die erste Wahl ist. Wir erklären das Konzept der Promise-Theorie, auf der Kubernetes basiert, und die Vorteile, die sich aus der Art und Weise ergeben, wie es implementiert wurde.

Sie erhalten ein besseres Verständnis dafür, wie Sie sich im Ökosystem **der Cloud Native Computing Foundation** (**CNCF**) zurechtfinden, da es für Sie entscheidend sein wird, die richtigen Projekte auszuwählen, die Sie bei der Implementierung Ihrer eigenen Plattform unterstützen.

Sobald Sie mit den Vorteilen von Kubernetes und dem Ökosystem vertraut sind, lernen Sie die Überlegungen kennen, die bei der Definition der Kernschicht Ihrer Plattform zu berücksichtigen sind, wie z. B. die Vereinheitlichung von Infrastruktur-, Anwendungs- und Servicefunktionen. Sie lernen, wie Sie die Interoperabilität mit Ihren zentralen Unternehmensdiensten außerhalb Ihrer neuen Plattform gestalten und wie Sie Flexibilität, Zuverlässigkeit und Robustheit erreichen.

Daher behandeln wir in diesem Kapitel die folgenden Hauptthemen:

- Warum Kubernetes eine wichtige Rolle spielt und warum es (nicht) für jeden geeignet ist
- Nutzung und Verwaltung der Infrastrukturfunktionen von Kubernetes
- Entwerfen für Flexibilität, Zuverlässigkeit und Robustheit

Warum Kubernetes eine wichtige Rolle spielt und warum es (nicht) für jeden geeignet ist

Im Moment konzentrieren wir uns auf Kubernetes, aber es gibt auch andere Möglichkeiten, eine Plattform für die Ausführung Ihrer Workloads bereitzustellen. Neben vielen verschiedenen Varianten von Kubernetes, wie z. B. OpenShift, gibt es Alternativen wie Nomad, CloudFoundry, Mesos und OpenNebula. Sie alle haben ihre Daseinsberechtigung, aber nur eine hat sich fast überall durchgesetzt: Kubernetes!

Neben diesen Plattformen können Sie virtuelle Maschinen oder Dienste von öffentlichen Cloud-Anbietern für serverlose Anwendungen, App-Engines und einfache Containerdienste nutzen. In vielen Fällen nutzen auch Plattformen diese Dienste, wenn sie benötigt werden. Eine exklusive All-in-Kubernetes-Strategie könnte einige Jahre länger dauern, da es eine Weile dauert, bis sich Unternehmen vollständig darauf festlegen. Es gibt jedoch zwei aktuelle Trends, die Sie beobachten können:

- Verwaltung virtueller Maschinen über Kubernetes
- Migration zu virtuellen Clustern und von Clustern verwalteten virtuellen Maschinen, um Kostenexplosionen für Hypervisor-Lizenzen zu vermeiden

Kubernetes verfügt über ein wichtiges Ökosystem und eine wichtige Community, eine Vielzahl von Anwendungsfällen, die von anderen Unternehmen implementiert wurden, und hochmotivierte Mitwirkende, die sich den nächsten Herausforderungen von Kubernetes stellen.

Kubernetes – ein Anfang, aber nicht das Endziel!

„Kubernetes ist eine Plattform zum Aufbau von Plattformen. Es ist ein Anfang, aber nicht das Endziel“, so Kelsey Hightower, der 2014 bei Google arbeitete, als Kubernetes der Welt vorgestellt wurde. Kubernetes spielt zwar eine wichtige Rolle beim Aufbau moderner Cloud-nativer Plattformen, aber das bedeutet nicht, dass es für jeden die perfekte Lösung ist. Erinnern Sie sich an den produktorientierten Ansatz für die Plattformentwicklung? Dieser beginnt damit, die Schwachstellen Ihrer Nutzer in Bezug auf „ “ zu verstehen. Sobald wir die Schwachstellen kennen, können wir daran arbeiten, wie wir die Anwendungsfälle implementieren und welche Technologieentscheidungen wir treffen.

Schauen Sie sich noch einmal den ersten Abschnitt in [Kapitel 1](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap1/Platform%20Engineering_1%20de.md) mit dem Titel „Brauchen Sie wirklich eine Plattform?“ an, in dem wir einen Fragebogen bereitgestellt haben, der Ihnen bei der Entscheidung hilft, was der Kern der Plattform sein soll. Die Antwort könnte Kubernetes lauten, muss es aber nicht. Beginnen wir mit einem Blick auf unseren eigenen Anwendungsfall von Financial One ACME.

Würde Financial One ACME sich für Kubernetes entscheiden?

Wenn wir über den Anwendungsfall von Financial One ACME nachdenken, „Einfacherer Zugriff auf Protokolle in der Produktion zur Problembeseitigung“, erfordert die Verwendung der vorgeschlagenen Lösung nicht unbedingt Kubernetes als zugrunde liegende Plattform.

Wenn Kubernetes in unserem Unternehmen noch nicht eingesetzt wird und wir lediglich einen neuen Automatisierungsdienst benötigen, der sich in die verschiedenen Protokollierungslösungen integrieren lässt, sollten wir Kubernetes möglicherweise nicht als zugrunde liegende Kernplattform vorschlagen. Denn dies würde ein neues Maß an Komplexität in ein Unternehmen bringen, das noch nicht über die erforderliche Erfahrung verfügt. Wir könnten die Lösung implementieren und mit allen vorhandenen Tools und Teams betreiben; vielleicht könnten wir sie neben anderen Tools, über die wir bereits verfügen, einsetzen und dabei die gleichen Betriebsprozesse für Bereitstellung, Upgrades, Überwachung usw. befolgen.

Wenn jedoch bereits Kenntnisse vorhanden sind oder vielleicht sogar Kubernetes bereits verfügbar ist, würde die Verwendung von Kubernetes als Kernplattform zur Orchestrierung dieses neuen Dienstes viele Probleme lösen, beispielsweise durch die Bereitstellung der folgenden Funktionen:

- Neue Dienstcontainer als Pods
- Automatisierte Zustandsprüfungen für diese Dienste
- Ausfallsicherheit und Skalierbarkeit durch Konzepte wie ReplicaSets und Auto-Scaling
- Externer Zugriff über Ingress-Controller und Gateway-API
- Grundlegende Beobachtbarkeit dieser Dienste durch Prometheus oder OpenTelemetry

Aber müssen wir wirklich unseren eigenen Kubernetes-Cluster betreiben, wenn wir nur einen einfachen Dienst bereitstellen müssen? Die Antwort lautet: Nein! Es gibt Alternativen, beispielsweise die Ausführung der Implementierung unter Verwendung der Funktionen Ihres bevorzugten Cloud-Anbieters:

- **Serverlos**: Die Lösung könnte als eine Reihe von serverlosen Funktionen implementiert werden, die über ein API-Gateway verfügbar sind. Der Status oder die Konfiguration können in Cloud-Speicherdiensten gespeichert werden und sind über eine API leicht zugänglich.
- **Container**: Wenn die Lösung in einem Container implementiert wird, kann dieser Container leichtgewichtig sein und seine Endpunkte können einfach über ein API-Gateway verfügbar gemacht werden. Es ist kein vollwertiger Kubernetes-Cluster erforderlich, der von jemandem gewartet werden muss.

Dieser einzelne Anwendungsfall für Financial One ACME führt möglicherweise nicht dazu, dass wir Kubernetes als Kernplattform wählen. Bei dieser wichtigen Entscheidung darüber, was zum Kern Ihrer zukünftigen Plattform werden soll, müssen wir jedoch über den ersten Anwendungsfall hinausblicken. Die Plattformentwicklung wird viele weitere Anwendungsfälle lösen, indem sie den internen Entwicklungsteams zahlreiche Self-Service-Funktionen zur Verfügung stellt, um ihre tägliche Arbeit zu verbessern.

Es ist eine schwierige und weitreichende Entscheidung, die ein gutes Gleichgewicht zwischen Weitsicht und Überengineering erfordert. Um diese Entscheidung zu erleichtern, wollen wir uns die Vorteile der Wahl von Kubernetes als Kernplattform ansehen.

Vorteile der Wahl von Kubernetes als Kernplattform

Um die wichtige Entscheidung für den Kern einer zukünftigen Plattform zu erleichtern, wollen wir uns ansehen, warum andere Unternehmen Kubernetes als zentralen Baustein wählen. Das Verständnis dieser Gründe, der Vorteile und auch der Herausforderungen sollte es Architekten erleichtern, diese wichtige Entscheidung zu treffen.

Deklarativer Sollzustand – Promise-Theorie

Traditionelle IT-Abläufe verwenden das **Verpflichtungsmodell**, bei dem ein externes System das Zielsystem anweist, bestimmte Dinge zu tun. Dieses Modell erfordert, dass viel Logik in das externe System, z. B. eine automatisierte Pipeline, eingebracht wird. Eine skriptbasierte Pipeline, sei es auf Basis von Jenkins, GitHub Actions oder anderen Lösungen, muss nicht nur Änderungen am Zielsystem vornehmen. Die Pipeline muss auch mit unvorhergesehenen Ergebnissen und Fehlern außerhalb des Systems, das sie verändert, umgehen können. Was tun wir beispielsweise, wenn die Bereitstellung einer neuen Softwareversion innerhalb einer bestimmten Zeit nicht funktioniert? Sollten wir sie zurückrollen? Wie würde die Pipeline das bewerkstelligen?

In der Kubernetes-Dokumentation Teil 1 (https://www.youtube.com/watch?v=BE77h7dmoQU) erklärte Kelsey Hightower das Promise-Theory-Modell, dem Kubernetes folgt, mit einer großartigen Analogie. Es lautet in etwa so:

Wenn Sie einen Brief schreiben, ihn in einen Umschlag stecken und die Zieladresse und die richtigen Briefmarken darauf kleben, verspricht die Post, diesen Brief innerhalb einer bestimmten Zeit an den Bestimmungsort zu liefern. Ob diese Lieferung mit Lkw, Zug, Flugzeug oder einer anderen Transportart erfolgt, spielt für den Verfasser des Briefes keine Rolle. Die Post wird alles tun, um das Zustellversprechen einzuhalten. Wenn ein Lkw eine Panne hat, wird ein anderer Lkw die Fahrt fortsetzen, bis der Brief an seinem endgültigen Bestimmungsort angekommen ist.

Das gleiche Prinzip gilt für Kubernetes! In unserer Analogie ist der Brief ein Container-Image, das wir in einen Umschlag stecken. Der Umschlag in der Welt von Kubernetes ist eine benutzerdefinierte Ressource einer bestimmten **Custom Resource Definition** (**CRD**). Um ein Image zu liefern, könnte dies eine Definition einer Bereitstellung sein, die den Verweis auf das Image, die Anzahl der Replikate, den Namespace, in dem dieses Image bereitgestellt werden soll, und die Ressourcenanforderungen (CPU und Speicher) für die korrekte Ausführung des Images enthält. Kubernetes unternimmt dann alles in seiner Macht Stehende, um das Versprechen der Bereitstellung dieses Images zu erfüllen, indem es den richtigen Kubernetes-Knoten findet, der alle Anforderungen erfüllt, um das Container-Image mit der angegebenen Anzahl von Replikaten und der erforderlichen CPU- und Speicherleistung auszuführen.

Ein weiteres Beispiel ist ein Ingress, der einen bereitgestellten Dienst nach außen hin verfügbar macht. Durch Anmerkungen ist es möglich, das Verhalten bestimmter Objekte zu steuern. Bei einem Ingress könnte dies die automatische Erstellung eines TLS-Zertifikats für die Domain sein, die verwendet werden soll, um die entsprechenden Dienste über HTTPS zugänglich zu machen. Das folgende Beispiel zeigt ein Ingress-Objekt für fund-transfer-service, um das Objekt über eine bestimmte Domain nach außen hin sichtbar zu machen, wobei der Certificate Manager – ein zentrales Tool des Kubernetes-Ökosystems – verwendet wird, um ein gültiges TLS-Zertifikat von LetsEncrypt zu erstellen:

apiVersion: networking.k8s.io/v1

kind: Ingress

metadata:

&nbsp; name: fund-transfer-service

&nbsp; namespace: prod-useast-01

&nbsp; Anmerkungen:

&nbsp;   cert-manager.io/issuer: „letsencrypt-prod”

Spezifikation:

&nbsp; ingressClassName: nginx

&nbsp; tls:

&nbsp; - hosts:

&nbsp;   - fundtransfer-prod-useast-01.finone.acme

&nbsp;     secretName: finone-acme-tls

&nbsp; Regeln:

&nbsp; - host: fundtransfer-prod-useast-01.finone.acme

&nbsp;   http:

&nbsp;   ...

KopierenErklären

Eine vollständig funktionierende Ingress-Objektbeschreibung umfasst etwas mehr als das, was in diesem Manifest \[1\]-Beispiel gezeigt wird. Dieses Beispiel erklärt jedoch sehr gut, wie eine Definition von Kubernetes in die tatsächlichen Aktionen übersetzt wird, die man erwarten würde – und erfüllt damit das Versprechen.

Nun stellt sich die Frage: „Wie funktioniert diese ganze Magie?“ Um dies zu beantworten, werden wir zunächst die Konzepte von Controllern und Operatoren untersuchen.

Kubernetes-Controller und -Operatoren

Kubernetes-Controller sind im Wesentlichen Regelkreise, die die Versprechungstheorie von Kubernetes erfüllen. Mit anderen Worten: Controller automatisieren das, was IT-Administratoren oft manuell tun: Sie beobachten kontinuierlich den aktuellen Zustand eines Systems, vergleichen ihn mit dem erwarteten Zustand und führen Korrekturmaßnahmen durch, um das System am Laufen zu halten!

Eine Kernaufgabe von Kubernetes-Controllern ist daher die kontinuierliche Abstimmung. Diese kontinuierliche Aktivität ermöglicht es ihnen, den gewünschten Zustand durchzusetzen, beispielsweise indem sie sicherstellen, dass der gewünschte Zustand, der im Beispiel der Ingress-Definition aus dem vorherigen Abschnitt zum Ausdruck kommt, mit dem aktuellen Zustand übereinstimmt. Wenn sich entweder der gewünschte Zustand oder der aktuelle Zustand ändert, bedeutet dies, dass sie nicht mehr synchron sind. Der Controller versucht dann, die beiden Zustände zu synchronisieren, indem er Änderungen am verwalteten Objekt vornimmt, bis der aktuelle Zustand wieder mit dem gewünschten Zustand übereinstimmt!

Die folgende Abbildung zeigt, wie ein Controller den gewünschten Zustand (ausgedrückt durch Manifeste und gespeichert in etcd) überwacht, ihn mit dem aktuellen Zustand (dem in etcd gespeicherten Zustand) vergleicht und die verwalteten Objekte (z. B. Ingress, Deployments, SSL-Zertifikate usw.) verwaltet:

Abbildung 4.1: Abgleich und Selbstheilung durch Kubernetes-Controller

Diese Abbildung zeigt bereits die Kernkonzepte und die Leistungsfähigkeit von Controllern und verdeutlicht, wie die automatisierte Abgleichschleife eine automatisierte Selbstheilung durch Design gewährleistet. Controller erfüllen jedoch noch weitere Funktionen: Sie überwachen den Zustand von Clustern und Knoten, setzen Ressourcenbeschränkungen durch, führen Jobs nach einem Zeitplan aus, verarbeiten Lebenszyklusereignisse und verwalten Deployment-Rollouts und -Rollbacks.

Lassen Sie uns nun über Kubernetes-Operatoren sprechen. Operatoren sind eine Unterkategorie von Controllern und konzentrieren sich in der Regel auf einen bestimmten Bereich. Ein gutes Beispiel ist der OpenTelemetry-Operator, der OpenTelemetry-Kollektoren und die automatische Instrumentierung von Workloads verwaltet. Dieser Operator verwendet dieselbe Abgleichschleife, um sicherzustellen, dass die gewünschte Konfiguration für OpenTelemetry immer angewendet wird. Wenn die Konfiguration geändert wird oder wenn es ein Problem mit dem aktuellen OpenTelemetry Collector oder der Instrumentierung gibt, wird der Operator sein Bestes tun, um das Versprechen einzuhalten, dass der gewünschte Zustand auch der tatsächliche Zustand ist. Weitere Informationen finden Sie auf der OpenTelemetry-Website unter https://opentelemetry.io/docs/kubernetes/operator/.

Andere Anwendungsfälle für Operatoren beziehen sich in der Regel auf die Verwaltung und Automatisierung von Kernservices und -anwendungen wie Datenbanken, Speicher, Service Meshes, Backup und Wiederherstellung, CI/CD und Messaging-Systemen.

Wenn Sie mehr über Controller und Operatoren erfahren möchten, werfen Sie einen Blick auf die CNCF Operator Working Group und deren Whitepaper unter https://github.com/cncf/tag-app-delivery/tree/main/operator-wg. Eine weitere hervorragende Übersicht finden Sie im Kong-Blogbeitrag mit dem Titel „What’s the Difference: Kubernetes Controllers vs Operators“. Dieser Blog enthält auch einige großartige Beispiele für Controller und Operatoren: https://konghq.com/blog/learning-center/kubernetes-controllers-vs-operators

Nachdem wir nun mehr über Controller und Operatoren wissen, wollen wir uns ansehen, wie sie auch für die integrierte Ausfallsicherheit aller Kubernetes-Komponenten und -Bereitstellungen sorgen!

Integrierte Ausfallsicherheit durch Probes

Controller überprüfen kontinuierlich, ob sich unser System im gewünschten Zustand befindet, indem sie den Zustand des Kubernetes-Clusters sowie seiner Knoten und aller bereitgestellten Pods überwachen. Wenn eine der überwachten Komponenten nicht in Ordnung ist, versucht das System, sie durch bestimmte automatisierte Maßnahmen wieder in einen fehlerfreien Zustand zu versetzen. Nehmen wir zum Beispiel Pods. Wenn Pods nicht mehr fehlerfrei sind, werden sie schließlich neu gestartet, um die Ausfallsicherheit des gesamten Systems zu gewährleisten. Das Neustarten von Komponenten ist oft auch die Standardmaßnahme, die ein IT-Administrator nach dem Motto „Schalten wir es aus und wieder ein und schauen wir, was passiert!“ ergreift.

Genau wie IT-Administratoren, die wahrscheinlich nicht einfach wahllos Dinge ein- und ausschalten, verfolgt Kubernetes einen ausgefeilteren Ansatz, um die Ausfallsicherheit unserer Kubernetes-Cluster, Knoten und Workloads zu gewährleisten.

Kubelet – eine Kernkomponente von Kubernetes – beobachtet kontinuierlich den Lebenszyklus und den Gesundheitszustand von Pods mithilfe verschiedener Arten von Probes: Startup, Readiness und Liveness. Die folgende Abbildung zeigt die verschiedenen Gesundheitszustände, in denen sich ein Pod je nach den Ergebnissen der Startup-, Readiness- und Liveness-Probe-Prüfungen befinden kann:

Abbildung 4.2: Kubelet ermittelt den Gesundheitszustand von Pods mithilfe von Probes

Sobald Pods nicht mehr fehlerfrei sind, versucht Kubernetes, die Pods neu zu starten und sie wieder in einen fehlerfreien Zustand zu versetzen. Es gibt viele verschiedene Einstellungen sowohl für die Auswertung der Prüfergebnisse als auch für die Neustartrichtlinien, mit denen Sie sich vertraut machen müssen, um die integrierte Ausfallsicherheit von Kubernetes voll auszuschöpfen. Alle diese Einstellungen werden in Ihren Deployment- und Pod-Definitionen deklariert.

Wenn Sie mehr darüber erfahren möchten, wie Kubelet die verschiedenen Sonden verwaltet, und einige Best Practices kennenlernen möchten, empfehlen wir Ihnen Blog-Beiträge wie den von Roman Belshevits über Liveness-Sonden: [https://dev.to/otomato_io/liveness-probes-feel-the-pulse-of-the-app-133e](https://dev.to/otomato_io/liveness-probes-feel-the-pulse-of-the-app-133e%0A)

Eine weitere hervorragende Quelle ist die offizielle Kubernetes-Dokumentation zur Konfiguration von Liveness-, Readiness- und Startup-Probes: https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/

Zustandsprüfungen sind nur innerhalb von Kubernetes gültig

Es ist wichtig zu verstehen, dass alle diese Zustandsprüfungen nur innerhalb des Kubernetes-Clusters durchgeführt werden und uns nicht sagen, ob ein Dienst, der über einen Ingress für unsere Endbenutzer verfügbar ist, auch aus Sicht der Endbenutzer als funktionsfähig gilt. Eine bewährte Vorgehensweise besteht darin, die Integrität und Verfügbarkeit zusätzlich aus einer „Outside-In”-Perspektive als externe Kontrolle zu überprüfen. Sie können beispielsweise synthetische Tests verwenden, um zu überprüfen, ob alle exponierten Endpunkte erreichbar sind und erfolgreiche Antworten zurückgeben.

Nachdem wir nun die integrierte Ausfallsicherheit für Pods kennengelernt haben, wie sieht es mit komplexeren Konstrukten aus, z. B. Anwendungen, die in der Regel aus mehreren verschiedenen Pods und anderen Objekten wie Ingress und Speicher bestehen?

Workload- und Anwendungslebenszyklus-Orchestrierung

Wie wir gelernt haben, bietet Kubernetes eine integrierte Orchestrierung des Lebenszyklus von Pods, wie im vorherigen Abschnitt erläutert. Geschäftsanwendungen, die wir auf Kubernetes bereitstellen, bestehen jedoch in der Regel aus mehreren voneinander abhängigen Pods und Workloads. Nehmen wir als Beispiel unser Unternehmen Financial One ACME: Die Finanzdienstleistungsanwendungen, die zur Unterstützung seiner Kunden bereitgestellt werden, enthalten mehrere Komponenten, wie z. B. ein Frontend, ein Backend, Caches, Datenbanken und Ingress. Leider gibt es in Kubernetes kein Konzept für Anwendungen. Zwar gibt es mehrere Initiativen und Arbeitsgruppen, die sich mit der Definition einer Anwendung befassen, doch müssen wir uns derzeit auf andere Ansätze für die Verwaltung von Anwendungen verlassen, die aus mehreren Komponenten bestehen.

Im Abschnitt „Änderungen bündeln, um Abhängigkeiten zu bekämpfen“ in [Kapitel 5](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/5) lernen wir Tools wie Crossplane kennen. Mit Crossplane können Sie sogenannte Composites definieren, die es Anwendungsbesitzern erleichtern, einzelne Komponenten einer Anwendung zu definieren und dann einzelne Instanzen bereitzustellen, wie im folgenden Beispiel gezeigt:

apiVersion: composites.financialone.acme/v1alpha1

kind: FinancialBackend

metadata:

&nbsp; name: tenantABC-eu-west

spec:

&nbsp; service-versions:

&nbsp;   Überweisung: 2.34.3

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

CopyExplain

Crossplane bietet Anwendungs- und Infrastruktur-Orchestrierung und nutzt das Operator-Muster, um kontinuierlich sicherzustellen, dass jede Anwendungsinstanz – wie in der Zusammensetzung definiert – wie erwartet ausgeführt wird.

Ein weiteres Tool, über das wir in [Kapitel 5](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/5) mehr erfahren werden, ist das Keptn-CNCF-Projekt. Keptn bietet automatisierte, anwendungsorientierte Lebenszyklus-Orchestrierung und Beobachtbarkeit. Es gibt Ihnen die Möglichkeit, vor und nach der Bereitstellung Prüfungen deklarativ zu definieren (Abhängigkeiten validieren, Tests ausführen, Zustand bewerten, SLO-basierte Qualitätskontrollen durchsetzen usw.), ohne dass Sie einen eigenen Kubernetes-Operator schreiben müssen, um diese Aktionen zu implementieren. Keptn bietet außerdem automatisierte Beobachtbarkeit der Bereitstellung, um besser zu verstehen, wie viele Bereitstellungen stattfinden, wie viele erfolgreich sind und wo und warum sie fehlschlagen, indem es OpenTelemetry-Traces und -Metriken ausgibt, um die Fehlerbehebung und Berichterstellung zu vereinfachen.

Kubernetes bietet viele Bausteine für die Erstellung resilienter Systeme. Sie können zwar eigene Operatoren schreiben, um dies auf Ihren eigenen Problembereich auszuweiten, aber Sie können auch vorhandene CNCF-Tools wie Crossplane oder Keptn verwenden, da diese eine einfachere deklarative Möglichkeit bieten, das Konzept der Promise-Theorie auf komplexere Anwendungen und Infrastrukturkompositionen anzuwenden.

Das Neustarten von Komponenten ist eine Möglichkeit, Ausfallsicherheit zu gewährleisten, aber es gibt noch weitere. Werfen wir einen Blick auf die automatische Skalierung, die ein weiteres kritisches Problem in dynamischen Umgebungen löst!

Automatische Skalierung von Clustern und Workloads

In den meisten Branchen ist die zu erwartende Auslastung eines Systems nicht gleichmäßig über alle Tage des Jahres verteilt. Es gibt immer eine gewisse Saisonalität: Der Einzelhandel verzeichnet Spitzen am Black Friday und Cyber Monday, Steuerdienstleister am Stichtag für die Steuererklärung und Finanzdienstleister oft, wenn die Gehaltszahlungen anstehen. Das Gleiche gilt für unsere eigenen Financial One ACME-Kunden. Als Finanzdienstleistungsunternehmen gibt es immer einen gewissen Grundverkehr von Endnutzern, aber zu Monatsanfang und -ende kommt es zu Spitzen.

Kubernetes bietet mehrere Möglichkeiten zur Skalierung von Anwendungs-Workloads: manuell (z. B. durch Festlegen von ReplicaSets) oder automatisch durch Tools wie **Horizontal Pod Autoscaler** (**HPA**), **Vertical Pod Autoscaler** (**VPA**) oder **Kubernetes Event Driven Autoscaler** (**KEDA**). Mit diesen Skalierungsoptionen können Sie skalieren, wenn Ihre Workloads wenig CPU-Leistung oder Speicher haben, wenn Anwendungen einen Anstieg des eingehenden Datenverkehrs verzeichnen oder wenn die Antwortzeit zu steigen beginnt!

Neben den Workloads können und müssen Sie höchstwahrscheinlich auch die Größe Ihrer Cluster und Knoten skalieren, entweder mithilfe von Tools wie **Cluster Autoscaler** (**CA**) oder **Karpenter** \[2\] oder über Optionen, die Ihnen Ihr Managed-Kubernetes-Cloud-Anbieter zur Verfügung stellt.

Als Plattform-Engineering-Team müssen Sie sich mit all den verschiedenen Optionen vertraut machen, aber auch alle Überlegungen berücksichtigen:

- **Festlegen von Grenzen**: Lassen Sie Anwendungen nicht unbegrenzt skalieren. Sie haben die Möglichkeit, Höchstgrenzen pro Anwendung, Workload, Namespace und mehr festzulegen.
- **Kostenkontrolle**: Automatische Skalierung ist großartig, hat aber ihren Preis. Stellen Sie sicher, dass Sie die Kosten an die Anwendungsbesitzer melden.
- **Herunterskalieren**: Hochskalieren ist einfach! Definieren Sie auch Indikatoren dafür, wann herunterskaliert werden soll. So bleiben die Kosten unter Kontrolle.

Weitere Informationen hierzu finden Sie in der Dokumentation: [https://kubernetes.io/docs/concepts/workloads/autoscaling/](https://kubernetes.io/docs/concepts/workloads/autoscaling/%0A)

Nachdem wir nun die Optionen für die Skalierung innerhalb einer Kubernetes-Umgebung kennengelernt haben, wie wäre es mit einer Skalierung auf andere Kubernetes-Cluster?

Einmal deklarieren – überall ausführen (theoretisch)

Das Versprechen von Kubernetes als offenem Standard besteht darin, dass sich jeder deklarierte Zustand (Ingress, Workloads, Secrets, Speicher, Netzwerk usw.) gleich verhält, unabhängig davon, ob Sie ihn auf einem einzelnen Cluster oder auf mehreren Clustern ausführen, um bestimmte Anforderungen zu erfüllen, wie z. B. die Trennung von Phasen (Entwicklung, Staging und Produktion) oder die Trennung von Regionen (USA, Europa und Asien).

Das gleiche Versprechen gilt theoretisch unabhängig davon, ob Sie Ihren eigenen Kubernetes-Cluster betreiben, OpenShift verwenden oder einen verwalteten Kubernetes-Dienst von einem der Cloud-Anbieter nutzen. Was bedeutet „theoretisch“ in diesem Zusammenhang? Es gibt einige spezifische technische Unterschiede zwischen den verschiedenen Angeboten, die Sie berücksichtigen müssen. Je nach Angebot können sich Netzwerk oder Speicher geringfügig unterschiedlich verhalten, da die zugrunde liegende Implementierung vom Cloud-Anbieter abhängt. Bestimmte Angebote umfassen auch spezifische Versionen von Kern-Kubernetes-Diensten, Service Meshes und Operatoren, die mit einer verwalteten Installation geliefert werden. Bei einigen Angeboten müssen Sie herstellerspezifische Anmerkungen von verwenden, um das Verhalten bestimmter Dienste zu konfigurieren. Deshalb funktioniert die Anwendung derselben deklarativen Zustandsdefinition bei verschiedenen Anbietern theoretisch – in der Praxis müssen Sie jedoch bestimmte kleine Unterschiede berücksichtigen, die eine herstellerspezifische Konfiguration erfordern!

Da sich die technischen Details und Unterschiede ständig ändern, wäre es nicht sinnvoll, einen aktuellen Vergleich als Teil dieses Buches anzubieten. Sie müssen verstehen, dass Sie zwar theoretisch jedes Kubernetes-Objekt nehmen und auf jeder Kubernetes-Variante bereitstellen können, das Ergebnis und Verhalten jedoch je nach Bereitstellungsort leicht unterschiedlich sein kann. Aus diesem Grund empfehlen wir Ihnen, einige technische Recherchen zu dem ausgewählten Kubernetes-Angebot und dessen Unterschieden zu anderen Angeboten durchzuführen, falls Sie sich für Multi-Cloud/Multi-Kubernetes entscheiden möchten, da sich dieselben Kubernetes-Objekte möglicherweise leicht unterschiedlich verhalten!

Die gute Nachricht ist, dass die globale Community daran arbeitet, dieses Problem zu lösen, indem sie bessere Anleitungen und Tools bereitstellt, um das Versprechen „einmal deklarieren – überall ausführen“ Wirklichkeit werden zu lassen.

Wir haben uns viele Vorteile der Wahl von Kubernetes als Kernplattform angesehen. Es gibt jedoch noch einen weiteren guten Grund, warum Kubernetes in den letzten 10 Jahren seit seiner ersten Veröffentlichung so große Akzeptanz gefunden hat: die globale Community und die CNCF!

Globale Community und CNCF

Kubernetes wurde im Juni 2014 von Google angekündigt, und die Version 1.0 wurde am 21. Juli 2015 veröffentlicht. Google arbeitete dann mit der Linux Foundation zusammen und gründete die CNCF mit Kubernetes als ihrem ersten Projekt! Seitdem haben die Community und die Projekte die Welt im Sturm erobert!

Zehn Jahre später (zum Zeitpunkt der Erstellung dieses Buches) umfasst die CNCF 188 Projekte, 244.000 Mitwirkende, 16,6 Millionen Beiträge und Mitglieder in 193 Ländern weltweit. Viele Präsentationen, die Kubernetes und die CNCF vorstellen, beginnen oft mit einer Darstellung der CNCF-Landschaft: [https://landscape.cncf.io/](https://landscape.cncf.io/%0A)

Die Landschaft ist zwar beeindruckend, aber sie war auch Quelle vieler Memes darüber, wie schwierig und komplex es ist, sich in der Landschaft aller Projekte zurechtzufinden, an denen diese globale Community arbeitet. Aber keine Angst: Die globale CNCF-Community ist Teil der Linux Foundation und hat die Aufgabe, schnell wachsende Cloud-native Projekte wie Kubernetes, Envoy und Prometheus zu unterstützen, zu beaufsichtigen und zu lenken.

Hier sind einige Dinge, die Sie beachten sollten, da sie Ihnen helfen werden, sich in der ständig wachsenden Liste der CNCF-Projekte in der Projektlandschaft zurechtzufinden:

- **Projektstatus**: Die CNCF verfolgt aktiv den Status und die Aktivitäten jedes Projekts. Die Anzahl der Mitwirkenden und Anwender sowie die Aktivität der Entwicklung eines Projekts sind gute Indikatoren dafür, ob Sie sich ein Projekt genauer ansehen sollten. Projekte, die veraltet sind, nur einen einzigen Betreuer haben oder kaum Anwender finden, sind möglicherweise nicht von Nutzen, wenn Sie sich für Tools entscheiden, die Ihnen langfristig auf Ihrer Plattform helfen sollen.
- **Reifegrad**: Die CNCF gibt auch einen Reifegrad von „Sandbox”, „Incubating” oder „Graduated” an, der den Stufen „Innovators”, „Early Adopters” und „Early Majority” des Crossing-the-Chasm-Diagramms (https://en.wikipedia.org/wiki/Crossing_the_Chasm) entspricht. Graduierte Projekte sind in verschiedenen Branchen weit verbreitet und stellen eine sichere Wahl für die von ihnen unterstützten Anwendungsfälle dar. Inkubierende Projekte haben den Sprung vom technischen Spielfeld geschafft und werden von einer wachsenden Zahl unterschiedlicher Maintainer erfolgreich eingesetzt. Weitere Informationen zu den Kriterien für die CNCF-Reife und dazu, wer sich auf welcher Stufe befindet, finden Sie auf der offiziellen Website unter https://www.cncf.io/project-metrics/.
- **Anwender**: Jedes CNCF-Projekt ist bestrebt, die Akzeptanz zu steigern und zu verfolgen. Eine Möglichkeit hierfür besteht darin, dass Organisationen, die ein Projekt aktiv übernehmen, sich in die Datei ADOPTERS.md eintragen, die jedes CNCF-Projekt in der Regel in seinem GitHub-Repository hat. Wenn Sie sich entscheiden, eines dieser Projekte zu übernehmen, empfehlen wir Ihnen, Ihren Namen ebenfalls in die Liste der Anwender aufzunehmen, indem Sie einen Pull-Request öffnen. Dies hilft dem Projekt und anderen Organisationen bei der Entscheidung, ob es sich um ein lohnenswertes Projekt handelt!

Kubernetes ist aufgrund seiner Community unverzichtbar

Kubernetes verfügt zwar über eine starke technologische Basis, aber es sind vor allem die Community und das Ökosystem, die in den letzten mehr als zehn Jahren aufgebaut wurden, die Kubernetes zu einer praktikablen Option für Plattformingenieure machen, die es als ihre Kernplattform nutzen möchten.

Wir haben nun besser verstanden, was Kelsey Hightower meinte, als er sagte: „Kubernetes ist eine Plattform zum Aufbau von Plattformen. Es ist ein Anfang, aber nicht das Endziel.“ Die Wahl von Kubernetes als Kernplattform bietet viele Vorteile, insbesondere da es auf dem Konzept der Promise-Theorie basiert. Kubernetes bietet automatisierte Ausfallsicherheit, Skalierung, und Lebenszyklusmanagement von Komponenten. Die stetig wachsende Community bietet Lösungen für viele gängige Probleme durch Hunderte von Open-Source-CNCF-Projekten, die jede Organisation nutzen kann.

Während wir uns oft auf die Vorteile von Kubernetes für die Bereitstellung und Orchestrierung von Anwendungen konzentrieren, wollen wir uns nun ansehen, wie wir Kubernetes nutzen können, um unsere Infrastrukturkapazitäten auf unsere zukünftige Plattform zu übertragen!

Nutzung und Verwaltung der Infrastrukturkapazitäten von Kubernetes

In [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) wurden Ihnen das Plattform-Referenzkomponentenmodell und die Fähigkeitsebene vorgestellt. Wenn wir über die Übertragung von Infrastrukturkapazitäten auf Kubernetes schreiben, werden dem Endbenutzer diese Kapazitäten bei der Nutzung der Plattform bewusst. Wir müssen zwischen Ressourcen unterscheiden, die in Kubernetes integriert werden müssen, und solchen, die durch in Kubernetes bereitgestellte Spezifikationen konfiguriert und außerhalb des Clusters manipuliert oder neu erstellt werden. In der folgenden Abbildung finden Sie Beispiele im Abschnitt „Ressourcenintegration und Netzwerk“, die eine solide Integration erfordern, da sie sonst eine nützliche und funktionierende Plattform aktiv verhindern.

Abbildung 4.3: Funktionsbereich mit Beispiel-Tools

Integration von Infrastrukturressourcen

Wir werden die grundlegenden Komponenten und Designentscheidungen besprechen, die Sie für die zugrunde liegenden Technologien der Plattform treffen müssen. Erstens sind Sie aufgrund der Leistungsfähigkeit von Kubernetes flexibler in Ihrer Toolauswahl und können diese nach Bedarf erweitern. Dies ist besonders hilfreich, wenn Sie die Funktionen der Plattform für verschiedene Anwendungsfälle anpassen.

Container-Speicherschnittstelle

Die **Container Storage Interface** (**CSI**) bietet Zugriff auf die Speichertechnologie, die mit dem Cluster oder den Knoten, auf denen der Cluster ausgeführt wird, verbunden ist. In der CSI-Entwicklerdokumentation \[3\] finden Sie einen Treiber für fast jeden Speicheranbieter. Die Liste enthält Treiber für Cloud-Anbieter wie AWS **Elastic Block Storage** (**EBS**), softwaredefinierten Speicher wie Ceph oder einen Konnektor für kommerzielle Lösungen wie NetApp. Darüber hinaus unterstützt der CSI-Treiber auch toolspezifische Treiber wie cert-manager und HashiCorp Vault. Kurz gesagt, das CSI ist unverzichtbar für alle Daten, die länger als der Container, zu dem sie gehören, bestehen bleiben sollen und nicht in einer Datenbank gespeichert sind oder für die Speicherung in einer Datenbank benötigt werden.

Die Installation des Treibers hängt von der Infrastruktur und der Speichertechnologie ab. Für einen Cloud-Anbieter benötigen Sie beispielsweise in der Regel Folgendes:

- Ein Dienstkonto oder Berechtigungsrichtlinien
- Konfiguration für Start-Taints und Toleranzen
- Vorinstallierter externer Snapshotter
- Die Treiberinstallation selbst

Aufgrund ihrer Komplexität werden diese Komponenten mit Helm oder anderen Paketverwaltungslösungen bereitgestellt. Manchmal erfordern sie mehr Berechtigungen auf dem Knoten, was bei der Gestaltung der Plattform ein Sicherheitsrisiko darstellen kann. Sie müssen auch berücksichtigen, wie auf den Speicher zugegriffen wird:

- **ReadWriteOnce** (**RWO**): Ein Pod beansprucht einen Teil des verfügbaren Speichers, auf den er lesen und schreiben kann, während andere Pods nur dann darauf zugreifen können, wenn der ursprüngliche Pod den Speicher freigibt.
- **ReadWriteMany** (**RWM**): Mehrere Pods können einen Teil des verfügbaren Speichers beanspruchen. Sie können darauf lesen und schreiben und diesen Speicher mit anderen teilen.
- **ReadOnlyMany** (**ROM**): Mehrere Pods können einen Teil des Speichers beanspruchen, aber nur zum Lesen.
- **ReadWriteOncePod** (**RWOP**): Kann nur von einem Pod beansprucht werden; kein anderer Pod kann ihn beanspruchen, und er erlaubt Lese- und Schreibvorgänge.

Die Übersicht über den CSI-Treiber enthält weitere Informationen darüber, welche Zugriffsmodi unterstützt werden. Da es keine einheitliche Lösung gibt, müssen Sie Ihre Optionen für den Benutzer transparent machen und deren Verwendung erklären.

Die wichtigsten Elemente, die Ihre Benutzer kennen und verstehen müssen, sind StorageClass, PersistentVolume und PersistentVolumeClaim. Wenn ein Pod/Deployment ein Volume benötigt, löst StorageClass die Erstellung eines neuen Volumes aus. Falls ein Pod/Deployment bereits einmal ein Volume beansprucht hat und dieses nicht zerstört wurde, weist die Kubernetes-Steuerungsebene das Volume erneut dem Pod/Deployment zu.

Abbildung 4.4: Dynamische Bereitstellung neuer persistenter Volumes

Sie definieren StorageClass als Plattformteam, idealerweise in Zusammenarbeit mit Ihren Speicherexperten. Das folgende Beispiel zeigt die gängige Definition von StorageClass. Bei der Konfiguration gibt es viel Raum für Fehler. Wenn Sie beispielsweise keine reclaimPolicy festlegen, wird standardmäßig das später erstellte und angehängte Volume gelöscht. StorageClass unterstützt Sie jedoch bei der dynamischen Erstellung von Volumes für vom Benutzer angeforderte PersistantVolumeClaim und ist daher ein starker Wegbereiter für Self-Service:

apiVersion: storage.k8s.io/v1

kind: StorageClass

metadata:

&nbsp; name: ultra-fast

&nbsp; annotations:

&nbsp;   storageclass.kubernetes.io/is-default-class: „false”

Bereitsteller: csi-driver.example-vendor.example

Rückforderungsrichtlinie: Beibehalten # Standardwert ist Löschen

allowVolumeExpansion: true

mountOptions:

&nbsp; - discard

volumeBindingMode: WaitForFirstConsumer

parameters:

&nbsp; guaranteedReadWriteLatency: „true“ # providerspezifisch

CopyExplain

Der Nachteil dabei ist, dass Sie menschliches Versagen berücksichtigen müssen, das Ihre Plattform lahmlegen kann, indem es den Speicher füllt, bis das System einfriert.

Herausforderungen für CSI

Die Definition eines CSI ist ein relativ neuer Ansatz, aber die zugrunde liegenden Technologien des Speichermanagements und des softwaredefinierten Speichers sind viel älter als Kubernetes. Wir können dies auch in vielen CSI-Treibern feststellen, die nichts anderes als eine Shim-Wrapper-Lösung für Legacy-Code sind. Für weniger flexible und skalierbare Cluster ist dies möglicherweise kein Problem, aber in Umgebungen, in denen viel los ist, möchten Sie kein CSI in Ihrem System haben, das zum Engpass wird. Einige CSIs haben sogar Einschränkungen und Begrenzungen, um ihren Ausfall bei großem Umfang zu verhindern. Fairerweise muss man sagen, dass dies in der Regel bei lokalen Installationen und einigen älteren Speichertechnologien der Fall ist. Bei diesen kommen noch die Darstellung **der Logical Unit Number** (**LUN**) und Verbindungsbeschränkungen als weitere zu berücksichtigende Faktoren hinzu. Die LUN dient den Pods dazu, Anfragen an den Speicherraum zu stellen und Daten abzurufen. Es gibt Beschränkungen hinsichtlich der Anzahl der Verbindungen, die ein physischer Server zum Speicher herstellen kann. Auch dies ist wichtig, wenn Sie Ihren eigenen Speicher und Ihre eigenen SANs verwalten.

Warum sind einige CSIs so schlecht? Die CSI bietet mehr als nur Speicherkapazität. Sie kommuniziert mit dem Speicheranbieter, verspricht die Verfügbarkeit der angeforderten Kapazität und wartet, bis der RAID-Controller, das Backup und die Snapshot-Mechanismen einsatzbereit sind ( ). In großen Speichersystemen erhalten wir sogar noch mehr: Wir finden Verfahren zur Zuweisung und Optimierung von Speicherkapazität.

Um solche Probleme zu überwinden, müssen Sie den Speicher, insbesondere die Speichertreiber, hinsichtlich ihrer Cloud-nativen Speicherfunktionen bewerten. Dies erfordert umfangreiche Leistungstests und eine enorme Anzahl erstellter Volumes. Der CSI-Treiber sollte keine Einschränkungen oder Leistungseinbußen verursachen, und das erstellte Volume sollte im Millisekundenbereich liegen.

Stellen Sie außerdem sicher, dass der Treiber speicher- und cloud-/infrastrukturübergreifende Migrationen ermöglicht, synchrone und asynchrone Replikation zwischen diesen verschiedenen Infrastrukturen bietet, Funktionsparität über Standorte hinweg gewährleistet und bei Bedarf lokale Speichertypen unterstützt, beispielsweise für Edge-Szenarien.

Ein guter CSI ermöglicht es Ihrer Plattform, überall zu funktionieren und eine Vielzahl von Anwendungsfällen zu unterstützen.

Container-Netzwerkschnittstelle

Die **Container-Netzwerkschnittstelle** (**CNI**) kann zur relevantesten Komponente einer Plattform werden, wird jedoch häufig unterschätzt. Bei vielen Projekten, die wir gesehen haben, ist es einigen Plattformteams egal, welche CNI sie verwenden, und sie nutzen auch keine Netzwerkrichtlinien, Verschlüsselung oder detaillierte Netzwerkkonfigurationen. Dank der einfachen Abstraktion der Netzwerkschicht ist der Einstieg nicht überwältigend. Andererseits gibt es viele Anwendungsfälle, in denen die CNI die wichtigste Komponente ist. Ich habe sogar Projekte gesehen, die aufgrund der Dynamik einer CNI gescheitert sind, die nicht mit dem sehr traditionellen und veralteten Ansatz der Netzwerkimplementierung kompatibel war.

Ein CNI erfordert immer eine dedizierte Implementierung, da es sich um eine Reihe von Spezifikationen und Bibliotheken zum Schreiben von Plugins zur Konfiguration von Netzwerkschnittstellen handelt. Das CNI befasst sich nur mit der Netzwerkkonnektivität von Linux-Containern und dem Entfernen zugewiesener Ressourcen, wenn der Container gelöscht wird. Aufgrund dieses Fokus bieten CNIs eine breite Palette an Unterstützung, und die Spezifikationen sind einfach zu implementieren.

Daher sollten wir Architekten CNI niemals als „nur ein weiteres Objekt in Kubernetes” betrachten. Wir müssen es bewerten und einführen. Einige CNIs sind auf einfache Wartung und einen soliden, aber einfachen Funktionsumfang ausgelegt. Wenn der Schwerpunkt beispielsweise auf Layer 3 liegt, sollten Sie Flannel in Betracht ziehen. Andere CNIs, wie Calico, sind eine absolut zuverlässige Wahl mit einem umfangreichen Funktionsumfang. Cilium hat die Verwendung von eBPF eingeführt, um eine noch schnellere und sicherere Netzwerk en zu ermöglichen. Wenn Ihnen die Wahl zwischen diesen Optionen immer noch schwerfällt, weil Sie möglicherweise zusätzliche Anforderungen haben, wie z. B. die Bereitstellung verschiedener Netzwerkebenen, dann hat die Community auch dafür eine Antwort für Sie: Multus. Nehmen Sie sich Zeit und entdecken Sie Ihre Optionen. Es gibt Dutzende von CNIs.

Das CNI kann erhebliche Auswirkungen auf Ihre Plattformen haben:

- **Sicherheit**: CNIs können unterschiedliche Funktionen für Netzwerkrichtlinien bieten, um eine detaillierte Kontrolle über Ihr Netzwerk zu erreichen. Sie können über zusätzliche Verschlüsselungsfunktionen, Integrationen in Identitäts- und Zugriffsmanagementsysteme und detaillierte Beobachtungsmöglichkeiten verfügen.
- **Skalierbarkeit**: Je größer der Cluster wird, desto mehr Kommunikation findet im gesamten Netzwerk statt. Das CNI muss Ihr Wachstumsziel unterstützen und auch bei komplexem Routing und Chatten über die Leitungen effizient bleiben.
- **Leistung**: Wie schnell und direkt kann die Pod-zu-Pod-Kommunikation sein? Wie komplex ist die CNI? Wie effizient kann sie die Kommunikation verarbeiten? Kann sie mit vielen komplexen Netzwerkrichtlinien umgehen?
- **Bedienbarkeit**: Hochwertige CNIs sind nicht sehr invasiv und einfach zu warten. Leistungsstarke CNIs können theoretisch ersetzt werden, solange sie der CNI-Spezifikation entsprechen, aber jedes CNI verfügt über eigene Funktionen, die oft nicht ersetzbar sind.

Beachten Sie, dass nicht jedes CNI alle diese Funktionen unterstützt. Einige bieten beispielsweise nicht einmal Unterstützung für Netzwerkrichtlinien. Andere CNIs sind cloudanbieterspezifisch, lassen sich nur mit einem Cloudanbieter integrieren und ermöglichen einige cloudanbieterspezifische Funktionen.

Architektonische Herausforderungen – CNI-Verkettung und mehrere CNIs

Plattformen sind für CNI-Verkettung prädestiniert. CNI-Verkettung führt die sequenzielle Verwendung mehrerer CNIs ein. Die Reihenfolge, in der CNIs verwendet werden, und der Zweck dafür werden im Verzeichnis /etc/cni/net.d definiert und vom Kubelet verarbeitet. Auf diese Weise kann das Plattformteam einen Teil des Netzwerks verwalten und einen geschützten Ansatz bieten, während Plattformbenutzer ihr Netzwerk auf einer höheren Ebene frei konfigurieren können. Beispielsweise kann ein Plattformnutzer auf Antrea als CNI zugreifen, um sein Netzwerk bis zu einem gewissen Grad zu konfigurieren. Er kann auch Netzwerkrichtlinien und Egress-Konfigurationen anwenden, um zu verhindern, dass seine Anwendung mit allen kommuniziert. Auf der anderen Seite der Plattform verwaltet das Plattform -Engineering-Team über Cilium die globale clusterübergreifende Kommunikation sowie die Netzwerkverschlüsselung, um bewährte Sicherheitsverfahren durchzusetzen. Darüber hinaus werden die von Cilium sichtbaren Netzwerkdaten den Betriebs- und Sicherheitsteams zur Verfügung gestellt. Am besten eignen sich diese Anwendungsfälle für die Interaktion mit den eigenen CNIs der Cloud-Anbieter. Diese ermöglichen oft eine bessere Integration zwischen der Plattform und der Cloud, verfügen jedoch auf der anderen Seite nicht über viele erweiterte Funktionen.

Ein weiterer zu evaluierender Ansatz wäre die Zuweisung mehrerer Netzwerkschnittstellen zu einem Pod über Multus oder CNI-Genie. Normalerweise verfügt ein Pod nur über eine Schnittstelle, aber mit Multus könnten dies beispielsweise mehrere Netzwerkschnittstellen sein. Wann ist dies relevant? Die folgenden Fälle sind Beispiele dafür, wann dies relevant ist:

- Trennung von Steuerungs- und Betriebsdaten von Anwendungsdaten
- Bereitstellung flexibler Netzwerkoptionen für eine extrem heterogene Arbeitslast
- Multi-Tenancy auf eine neue Ebene heben, indem jedem Mandanten völlig unterschiedliche Netzwerke zugewiesen werden
- Unterstützung ungewöhnlicher Netzwerkprotokolle und -verbindungen, z. B. in Edge-Szenarien oder Telekommunikationsumgebungen
- **Netzwerkfunktionsvirtualisierung** (**NFV**), die aufgrund ihrer Komplexität mehrere Netzwerke erfordert

Das Multus CNI ist eine Art Meta-Plugin auf dem Knoten und befindet sich zwischen den eigentlichen CNIs und den Pod-Netzwerkschnittstellen, wie in der folgenden Abbildung dargestellt. Es verbindet die verschiedenen Netzwerkschnittstellen auf der einen Seite mit dem Pod und übernimmt auf der anderen Seite die Verbindung zu den erwarteten CNIs für die richtige Netzwerkschnittstelle.

Abbildung 4.5: Multus-Meta-CNI-Plugin

Beide Ansätze müssen sorgfältig evaluiert werden. Sie haben erhebliche Auswirkungen auf die Komplexität, Leistung und Sicherheit Ihres Netzwerks.

Bereitstellung verschiedener CPU-Architekturen

Kubernetes unterstützt mehrere CPU-Architekturen: AMD64, ARM64, 386, ARM, ppc64le und sogar Mainframes mit s390x. Viele Cluster laufen heute auf AMD64, aber zum Zeitpunkt der Erstellung dieses Artikels sorgt ein starkes Interesse an ARM64 für eine Verschiebung. Bei dieser Diskussion geht es in erster Linie darum, Kosten zu sparen und ein wenig zusätzliche Leistung zu gewinnen, während gleichzeitig der Gesamtstromverbrauch gesenkt wird. Zumindest auf dem Papier ist dies eine Win-Win-Win-Situation. Nicht nur „ “ ist ARM64 eine mögliche Veränderung in der Infrastruktur, auch das Open-Source-Architekturprojekt RISC-V gewinnt an Fahrt und ist der erste Cloud-Anbieter, der RISC-V-Angebote erstellt \[4\].

Als Plattformingenieure können wir diese Migrationen und Änderungen ermöglichen. Ein Kubernetes-Cluster kann mehrere Architekturen gleichzeitig ausführen – nicht auf demselben Knoten, sondern mit verschiedenen Knotengruppen. Beachten Sie, dass diese Änderung auch eine Anpassung beim Container-Build erfordert. Bei einigen Softwarekomponenten können Sie einen Multi-Architektur-Build durchführen, bei anderen sind möglicherweise Anpassungen erforderlich, bevor der Container für eine andere Architektur erstellt werden kann.

Um die Architektur auszuwählen, auf der eine Bereitstellung erfolgen soll, müssen Sie lediglich einen nodeSelector wie diesen zum Abschnitt „Spec“ der YAML-Datei für die Bereitstellung hinzufügen:

nodeSelector:

kubernetes.io/arch: arm64

KopierenErklären

Eine bevorstehende Alternative zur Bereitstellung verschiedener Container-Images ist die Kompilierung der Software als **WebAssembly** (**Wasm**)-Container.

Wasm-Laufzeit

Die Verwendung von Wasm als alternatives Containerformat hat im letzten Jahr drastisch zugenommen. Wasm ist ein binäres Befehlsformat für eine stapelbasierte virtuelle Maschine. Stellen Sie es sich als eine Zwischenebene zwischen verschiedenen Programmiersprachen und vielen verschiedenen Ausführungsumgebungen vor. Sie können Code, der in über 30 verschiedenen Sprachen geschrieben ist, in eine \*.wasm-Datei kompilieren und diese Datei dann auf jeder Wasm-Laufzeitumgebung ausführen.

Der Name WebAssembly ist jedoch irreführend. Ursprünglich entwickelt, um Code schnell im Web auszuführen, kann er heute überall ausgeführt werden. Warum sollten wir ihn verwenden? Wasm ist standardmäßig sicher und sandboxed. In einem Wasm-Container gibt es kein Betriebssystem oder sonst etwas außer dem kompilierten Binärcode. Das bedeutet, dass es nichts gibt, in das man eindringen oder dessen Kontext oder Dienstkonto man beanspruchen könnte. Wasm hat auch eine unglaublich schnelle Startzeit, wobei die Grenzen eher durch die Laufzeit als durch das Modul gesetzt werden. Einige Laufzeiten behaupten, dass sie etwa 50 ms schnell sind. Im Vergleich dazu benötigt Ihr Gehirn >110 ms, um zu erkennen, ob etwas vor Ihren Augen vorbeizieht. Darüber hinaus beträgt die Größe eines Wasm-Containers etwa 0,5 MB bis 1,5 MB, während ein sehr schlanker Container etwa 5 MB groß sein kann. Auf dem Markt finden wir jedoch in der Regel Bildgrößen im Bereich von 300 MB – 600 MB, 1 GB – 3 GB oder manchmal sogar über 10 GB. Mit dieser reduzierten Bildgröße hat ein Wasm-Container auch einen drastisch reduzierten Speicherbedarf. Wasm ist außerdem hardwareunabhängig. Das exakt gleiche Bild kann überall ausgeführt werden, solange Sie über eine Wasm-Laufzeitumgebung verfügen.

Im Zusammenhang mit Kubernetes unterstützen die OCI- und CRI-Laufzeiten Wasm. Das bedeutet, dass Sie einen Wasm-Container neben einem regulären Container ausführen können. Wie Sie in der folgenden Abbildung sehen können, sind keine weiteren Änderungen erforderlich. Das Wasm-App-Image wird auf Knotenebene gespeichert und von den darüber liegenden Schichten ausgeführt.

Abbildung 4.6: Wasm auf einem Kubernetes-Knoten

Um Wasm auf Ihrer Plattform ausführbar und verfügbar zu machen, müssen Sie eine Laufzeitklasse angeben und deren Verwendung auf Deployment-/Pod-Ebene definieren. Im folgenden Beispiel sehen Sie links die Spezifikation für crun als RuntimeClass und rechts eine Pod-Definition, in der wir für spec.runtimeClassName crun zuweisen. Für crun müssen wir außerdem eine Anmerkung hinzufügen, um crun mitzuteilen, dass dieser Pod über ein Wasm-Image verfügt:

|     |     |
| --- | --- |
| apiVersion: node.k8s.io/v1<br><br>kind: RuntimeClass<br><br>metadata:<br><br>name: crun<br><br>scheduling:<br><br>Knotenselektor:<br><br>Laufzeit: crun<br><br>Handler: crun | apiVersion: v1<br><br>Art: Pod<br><br>Metadaten:<br><br>&nbsp; name: wasm-demo-app<br><br>&nbsp; Anmerkungen:<br><br>&nbsp; module.wasm.image/variant: compat<br><br>Spezifikation:<br><br>&nbsp; runtimeClassName: crun<br><br>&nbsp; Container:<br><br>&nbsp;   name: wasm-demo-app<br><br>&nbsp;   image:<br><br>&nbsp;   docker.io/cr7258/wasm-demo-app:v1 |

Tabelle 4.1: Definition einer RuntimeClass und eines Pods, die in der Wasm-Laufzeit ausgeführt werden

Als Alternative dazu bieten neue Entwicklungen wie SpinKube eine ganze Reihe von Tools, um Kubernetes-Ressourcen optimal zu nutzen \[5\]. Dieser Ansatz ermöglicht die Integration der Entwicklungserfahrung in die Bereitstellung und Ausführung der containerisierten Wasm-Anwendung. Die folgende Abbildung zeigt den Workflow und wie die verschiedenen Komponenten zusammenarbeiten. Dies vereinfacht den Entwicklungsprozess und bringt eine schnelle, aber robuste neue Laufzeitumgebung auf die Plattform.

Abbildung 4.7: SpinKube-Übersicht \[6\]

Aber ist Wasm wirklich eine Technologie, die von der Branche angenommen wurde? Hier sind nur einige Beispiele und Anwendungsfälle, die ihre Akzeptanz zeigen:

- **Interoperabilität**: Figma läuft als Wasm auf jedem Computer
- **Plugin-System**: Sie können Erweiterungen in Wasm für Envoy schreiben
- **Sandboxing**: Ein Firefox- oder Chrome-Browser kann Wasm in einer Sandbox-Umgebung ausführen, um Ihr System zu schützen
- **Blockchain**: CosmWasm oder das ICP verwenden Versionen von Wasm, um Anwendungen auszuführen
- **Container**: WasmCloud hat ein anderes Konzept zur Ausführung von Containern, oder SpinKube, eine Wasm-Laufzeitumgebung mit einer CLI für einen einfachen Entwicklungsprozess
- **Serverlose Plattformen**: Cloudflare Workers oder Fermyon Cloud führen Ihre Wasm-basierte App aus

Wasm ist noch kein Ersatz für Container. Es handelt sich um einen evolutionären Schritt, der für einige Fälle sehr gut geeignet ist, aber es mangelt an Akzeptanz und es gibt Probleme beim Debugging-Prozess. Es ist jedoch nur eine Frage der Zeit, bis diese Hindernisse überwunden sind.

Plattformen für die GPU-Nutzung aktivieren

Ähnlich wie die Unterstützung für verschiedene CPU-Architekturen oder die Erweiterung der Container-Laufzeitumgebung um Wasm ist in letzter Zeit auch die GPU-Aktivierung für Benutzer äußerst relevant geworden. Es muss ein Geräte-Plugin installiert werden, das für den jeweiligen GPU-Typ spezifisch ist, z. B. AMD, Intel oder Nvidia. Dadurch werden benutzerdefinierte planbare Ressourcen wie nvidia.com/gpu für Kubernetes und seine Benutzer verfügbar gemacht. Außerdem sind wir keine Experten für GPUs und ihre Fähigkeiten. Aus Sicht der Plattformtechnik haben die verschiedenen Anbieter unterschiedliche Funktionssätze und Erweiterungen für ihre Plugins entwickelt.

Ich empfehle dringend, Experten für diesen Bereich zu entwickeln oder zu finden, wenn Ihre Benutzer GPUs benötigen. Der Bereich der KI und LLMs befindet sich in einer rasanten Expansion. Hardware- und Softwareanbieter entwickeln monatlich neue Tools, Systeme und Ansätze, um diese Technologien zu nutzen. Jedes Szenario hat seine ganz spezifischen Anforderungen. Das Training eines Modells erfordert eine enorme Menge an Daten, GPUs, Speicherplatz und Arbeitsspeicher. Die Feinabstimmung eines Modells hängt in erster Linie davon ab, wie groß das zu trainierende Modell sein soll. Ein Modell mit sieben Milliarden Parametern passt in einen 14-GB-VRAM, aber durch eine Erhöhung der Präzision kann seine Größe leicht auf 24 GB oder mehr ansteigen. Schließlich erfordert die Bereitstellung einer Inferenz-Engine für die Bereitstellung eines LLM für Benutzer eine Menge Netzwerkkommunikation.

Wichtiger Hinweis

Inferenz bedeutet, eine Eingabeaufforderung an ein LLM zu senden. Die meisten Menschen glauben, dass das LLM dann wie ein Mensch eine Geschichte erstellt. Tatsächlich muss das LLM jedoch nach jedem Wort die gesamte Eingabeaufforderung, einschließlich der neuen Wörter, erneut an das LLM senden, damit es über das nächste Wort entscheiden kann, das dem Satz hinzugefügt wird.

Als Faustregel gilt, dass Sie für die benötigten GPU-VRAMs (Video-RAM ist der Speicher der GPU) die Größe des Modells verdoppeln müssen. Hier sind einige weitere Beispiele:

- Llama-2-70b benötigt 2 \* 70 GB = 140 GB VRAM
- Falcon-40b benötigt 2 \* 40 GB = 80 GB VRAM
- MPT-30b benötigt 2 \* 30 GB = 60 GB VRAM
- bigcode/starcoder benötigt 2 \* 15,5 = 31 GB VRAM

Daher ist eine Zusammenarbeit zwischen der Plattform und dem Machine-Learning-Team erforderlich. Je nach den Modellen, die sie verwenden möchten, entspricht die von Ihnen gewählte Hardware möglicherweise nicht mehr den Anforderungen.

Architektonische Herausforderungen

Die Integration von GPUs ist zwar sehr einfach, es gibt jedoch einige Aspekte, die besprochen werden müssen. Sie sollten sich über Folgendes im Klaren sein:

- **GPU-Kosten**: Günstige GPUs mit geringer VRAM-Kapazität und Rechenleistung sind möglicherweise nicht für Ihre Anwendungsfälle geeignet. Außerdem nutzen Sie eine GPU möglicherweise nicht rund um die Uhr, sollten aber über dynamischere und flexiblere Möglichkeiten nachdenken. Wenn Ihr Anwendungsfall GPU-Rechenleistung erfordert, kann der Besitz von GPUs jedoch auf lange Sicht günstiger sein als der Einsatz herkömmlicher CPUs.
- **Privilegierte Rechte**: Viele Machine-Learning-Tools erfordern weitere Anpassungen und Optimierungen, insbesondere hinsichtlich der erforderlichen Rechte.
- **Anforderungen der Endbenutzer**: Neben der Modellgröße hängt es stark vom tatsächlichen Anwendungsfall ab, den die Datenwissenschaftler und Machine-Learning-Ingenieure mit dem Modell umsetzen möchten. Jede geringfügige Änderung des Ansatzes kann die Plattform unbrauchbar machen. Dies muss bei der Architektur einer solchen Plattform berücksichtigt werden, um möglichst viele Ressourcen und eine größtmögliche Skalierbarkeit zu gewährleisten.
- **Externe Modelle**, die **in den Cluster gezogen werden**: Wie bei Containern ist es gängige Praxis, Modelle von Seiten wie HuggingFace zu ziehen. Dies sollten Sie im Netzwerk einer Plattform berücksichtigen, die Machine-Learning-Aktivitäten unterstützt.

Die Erstellung von Plattformen, die für maschinelles Lernen und LLM-Operationen geeignet sind, erfordert ein neues Maß an Optimierung. Nicht ausgelastete GPUs sind Geldverschwendung. Schlecht genutzte GPUs sind Geldverschwendung. Aus Sicht der Infrastruktur müssen wir jedoch noch mehr sicherstellen: Datenschutz, Plattformsicherheit und spezielle Beobachtbarkeit für die Modelle. Meiner Meinung nach sind maschinelles Lernen und LLMs ein spannender Anwendungsfall und bieten Plattformingenieuren einen Spielplatz.

Lösungsraum

Um die GPU-Nutzung zu optimieren, gibt es einige Ansätze:

- **Multi-Process Server** (**MPS**)
- **Multi-Instance-GPU** (**MIG**)
- **Zeiteinteilung/Freigabe**

Je nach GPU-Treiber stehen Ihnen zahlreiche Möglichkeiten zur Verfügung, ähnlich wie bei Nvidia. Andere GPU-Treiber sind möglicherweise noch nicht ausgereift oder bieten noch nicht so viele Funktionen, aber Sie sollten dies natürlich regelmäßig überprüfen.

Time-Slicing ist die schlechteste Option. Es ist zwar besser als nichts, aber MPS wäre mindestens doppelt so effizient wie der Time-Slice-Ansatz. MPS hat jedoch einen großen Nachteil: Prozesse sind nicht streng isoliert, was zu korrelierten Ausfällen zwischen den Slices führt. Hier kommt MIG ins Spiel. Es bietet eine gute Prozessisolierung und eine statische Partitionierung der GPU. Statisch auf einem superdynamischen, skalierbaren und jederzeit anpassbaren Kubernetes-Cluster? Ja, denn Machine-Learning-Training läuft nicht nur für ein paar Sekunden oder Minuten \[7\].

Die folgende Abbildung zeigt die Speicherpartitionen der GPU auf hoher Ebene, denen verschiedene Workloads zugewiesen werden können.

Abbildung 4.8: Beispiel für die Aufteilung einer GPU in drei GPU-Instanzen

Diese GPU-Instanzen können entweder von einem einzelnen Pod, einem Pod mit einem Container, auf dem mehrere Prozesse laufen (nicht ideal), oder unter Verwendung von beispielsweise CUDA von Nvidia genutzt werden. CUDA ist ein MPS, sodass Sie die verschiedenen Ansätze kombinieren können, wie in der folgenden Abbildung dargestellt:

Abbildung 4.9: Beispiel für die parallele Verwendung von drei GPU-Instanzen

An dieser Stelle können wir einen Blick auf den Forschungs- und Experimentierbereich werfen, in dem Sie Kubernetes **Dynamic Resource Allocation** (**DRA**) mit MIG kombinieren können. Dies bietet einen „ ”-Ansatz, um bei der Zuweisung flexibel zu sein und gleichzeitig die Ressourcen für die Bereitstellungen sicherzustellen. DRA wurde mit Kubernetes v1.26 eingeführt und befindet sich noch in der Alpha-Phase, sodass bei jeder Version mit API-Änderungen zu rechnen ist. Es gibt einige interessante Artikel und Vorträge zu diesem Thema. Je nachdem, wann Sie dies lesen, könnte es bereits veraltet sein \[8\].

Cluster-Skalierbarkeit aktivieren

Wie bereits in diesem Kapitel erwähnt, ist die Fähigkeit eines Kubernetes-Clusters, seine Größe anzupassen, für verschiedene Anforderungen von Vorteil, von der Ausfallsicherheit über das Wachstum mit der Arbeitslast bis hin zur Fallback-Neustartfunktion und der Bereitstellung der höchsten Verfügbarkeit über Rechenzentren und Verfügbarkeitszonen hinweg. Im Kern unterscheiden wir zwischen dem horizontalen und vertikalen Autoscaler, der auf die Pods abzielt, und dem horizontalen CA, der die Anzahl der Knoten anpasst.

Wie bei vielen Funktionen stellt Kubernetes die Spezifikation bereit, erwartet jedoch, dass jemand anderes sie implementiert. Dies gilt zumindest für den VPA und den CA, die mindestens einen Metrikserver erfordern, der auf Cluster-Ebene läuft.

Der HPA ist jedoch funktionsreich und ermöglicht eine metrikbasierte Skalierung. Sehen Sie sich das folgende Beispiel für einen HPA an. Mit stabilizationWindowsSeconds können wir Kubernetes auch anweisen, auf vorherige Aktionen zu warten, um Flapping zu verhindern. Flapping wird gemäß der Kubernetes-Dokumentation wie folgt definiert:

Bei der Verwaltung der Skalierung einer Gruppe von Replikaten mit dem HorizontalPodAutoscaler kann es vorkommen, dass die Anzahl der Replikate aufgrund der Dynamik der ausgewerteten Metriken häufig schwankt. Dies wird manchmal als Thrashing oder Flapping bezeichnet. Es ähnelt dem Konzept der Hysterese in der Kybernetik.

Wir können die folgende Konfiguration für einen HPA verwenden. Sie sieht einfach aus, aber Sie können sehen, dass sich das Verhalten aufgrund der Richtlinien drastisch ändern kann. Wenn Sie beispielsweise 10 % der Pods reduzieren und gleichzeitig eine große Bereitstellung mit Hunderten von Replikaten haben, sollten Sie sehr vorsichtig sein. Die gezeigte Konfiguration für die Verkleinerung verhindert, dass mehr als zwei Pods gleichzeitig gelöscht werden:

apiVersion: autoscaling/v2

kind: HorizontalPodAutoscaler

spec:

&nbsp; maxReplicas: 7 #maximale Anzahl von Replikaten, auf die skaliert werden kann

&nbsp; minReplicas: 3 #erwartete minimale Anzahl an Replikaten

scaleTargetRef: ...

&nbsp; targetCPUUtilizationPercentage: 75 #Metrik, auf die reagiert werden soll

&nbsp; Verhalten:

&nbsp;   scaleDown:

&nbsp;    stabilizationWindowSeconds: 300 #300 Sekunden warten

&nbsp;    Richtlinien:

&nbsp;    - Typ: Prozent

&nbsp;      Wert: 10 #Reduzierung um 10 % der Pods

&nbsp;      periodSeconds: 60 #pro Minute

&nbsp;    - Typ: Pods

&nbsp;      Wert: 5 #Reduzierung um nicht mehr als

&nbsp;      periodSeconds: 60 #als 2 Pods pro Minute

&nbsp;    selectPolicy: Min

&nbsp;  scaleUp:

&nbsp;    stabilizationWindowSeconds: 0

&nbsp;    Richtlinien:

&nbsp;    - Typ: Prozent

&nbsp;      Wert: 75 #Pod um 75 % erhöhen

&nbsp;      periodSeconds: 15 #alle 15 Sekunden

&nbsp;    selectPolicy: Max

CopyExplain

Probleme mit VPA, HPA und CA

Es gibt einige Einschränkungen, die Sie bei der Autoscaler-Familie berücksichtigen müssen:

- **HPA**:
    - Sie müssen CPU- und Speichergrenzen sowie Anforderungen für Pods korrekt festlegen, um Ressourcenverschwendung oder häufig beendete Pods zu vermeiden.
    - Wenn HPA die Grenze der verfügbaren Knoten erreicht, kann es keine weiteren Pods mehr planen. Es kann jedoch alle verfügbaren Ressourcen nutzen, was zu Problemen führen kann.
- **VPA**:
    - VPA und HPA sollten nicht für die Skalierung auf Basis derselben Metrik verwendet werden. Beispielsweise können beide die CPU-Auslastung verwenden, um eine Skalierung nach oben auszulösen, aber HPA stellt mehr Pods bereit, während VPA die CPU-Grenzen für vorhandene Pods erhöht, was zu einer übermäßigen Skalierung auf Basis derselben Metrik führen kann. Wenn Sie also sowohl VPA als auch HPA verwenden, sollten Sie für das eine die CPU und für das andere beispielsweise den Arbeitsspeicher verwenden.
    - VPA empfiehlt möglicherweise die Verwendung von mehr Ressourcen, als innerhalb des Clusters oder des Knotens verfügbar sind. Dies führt dazu, dass der Pod nicht mehr planbar ist.
- **CA**:
    - Die CA-Skalierungen basieren auf den Anforderungen und Grenzen der Pods. Dies kann zu vielen ungenutzten Ressourcen, schlechter Auslastung und hohen Kosten führen.
    - Wenn eine CA einen Skalierungsbefehl an den Cloud-Anbieter auslöst, kann es Minuten dauern, bis neue Knoten für den Cluster bereitgestellt werden. Während dieser Zeit verschlechtert sich die Anwendungsleistung. Im schlimmsten Fall wird sie unbrauchbar.

Lösungsansatz

Als Plattformingenieure möchten wir sicherstellen, dass der Benutzer das Skalierungsverhalten definieren kann, ohne die Plattform zu gefährden. Die Verwendung von HPA, VPA und CA erfordert eine perfekte Konfiguration und Steuerung, Schutzvorrichtungen durch eine Policy-Engine und eine genaue Überwachung. Es ist von entscheidender Bedeutung, die Skalierung und Deskalierung des Clusters zu steuern und gleichzeitig die automatische Skalierung innerhalb des Namespace für Ihre Benutzer zu ermöglichen.

Um die Skalierung Ihres Kubernetes-Clusters bei Cloud-Anbietern zu verwalten, müssen Sie sich mit CA und den verschiedenen verfügbaren Cloud-Integrationen dafür befassen. Wenn Sie die **Cluster-API** (**CAPI**) verwenden, können Sie außerdem auf deren Funktionen für die automatische Cluster-Skalierung aufbauen.

Netzwerkfunktionen und Erweiterungen

Betrachten wir nun die endgültige Ressourcenintegration von Kubernetes und der zugrunde liegenden Infrastruktur. Dazu beginnen wir mit den Cluster-Netzwerkmechanismen und arbeiten uns bis zum DNS und Lastenausgleich vor. DNS und Lastenausgleich können innerhalb des Clusters und in Abstimmung mit der Infrastruktur, auf der Kubernetes läuft, erfolgen.

Ingress – die alte Methode

Ingress ist die alte Definition dafür, wie eine Endbenutzeranfrage von außerhalb des Clusters in das System und zu der exponierten Anwendung weitergeleitet wird. Fast ein Jahrzehnt lang war dies die gängige Methode, um eingehenden Netzwerkverkehr zu definieren. Der Ingress wird in der Regel durch einen Ingress-Controller wie NGINX, HAProxy oder Envoy dargestellt, um nur einige zu nennen. Diese übernehmen inhärent die als Standardressource von Kubernetes definierten Routing-Regeln und verwalten den Rest. Wie Sie in der folgenden Abbildung sehen können, wird der Datenverkehr von dort aus an den richtigen Dienst weitergeleitet, der ihn an den Pod weiterleitet. Physisch gesehen fließt der Datenverkehr von der Netzwerkschnittstelle zum Ingress-Controller und dann zum Pod, aber so gut Kubernetes als Orchestrator auch ist, dazwischen gibt es einige logische Schritte.

Abbildung 4.10: Ingress-Controller (Quelle: Kubernetes-Dokumentation)

Obwohl er skalierbar und robust für einige der größten Bereitstellungen ist, hat er einige Nachteile:

- Die Ingress-API unterstützt nur TLS-Terminierung und einfaches contentbasiertes Request-Routing von HTTP-Datenverkehr.
- Er ist in seiner verfügbaren Syntax eingeschränkt und sehr einfach gehalten.
- Sie erfordert Anmerkungen für die Erweiterbarkeit.
- Sie verringert die Portabilität, da jede Implementierung ihren eigenen Ansatz dafür hat

Die Einrichtung eines Multi-Tenant-Clusters ist schwieriger, da Ingress in der Regel auf Cluster-Ebene angesiedelt ist und über ein unzureichendes Berechtigungsmodell verfügt. Außerdem unterstützt es Konfigurationen mit Namespaces, ist jedoch nicht für Multi-Teams und gemeinsam genutzte Load-Balancing-Infrastrukturen geeignet.

Ein Teil der Vorzüge des Ingress-Ansatzes liegt in seiner breiten Unterstützung und Integration mit anderen Tools, wie z. B. dem Cert-Manager für die Zertifikatsverwaltung und die Handhabung des externen DNS, auf die wir gleich noch eingehen werden. Außerdem behauptet der Kubernetes-Maintainer, dass es keine Pläne gibt, Ingress zu veralten, da es einfachen Webdatenverkehr auf unkomplizierte Weise perfekt unterstützt.

Gateway-API – der neue Weg

Im Herbst 2023 wurde die Gateway-API allgemein verfügbar. Anstelle einer einzigen Ressource besteht die Gateway-API aus mehreren Ressourcentypen, die einem Muster folgen, das bereits in anderen kritischen Integrationen verwendet wurde:

- Gateway: Cluster-Einstiegspunkt für eingehenden Datenverkehr
- GatewayClass: Definiert den Gateway-Steuerungstyp, der das Gateway verwaltet
- \*Route: Implementiert die Weiterleitung des Datenverkehrs vom Gateway zum Dienst:
    - HTTPRoute
    - GRPCRoute
    - TLSRoute
    - TCPRoute
    - UDPRoute

Wenn wir das folgende Diagramm mit dem Ingress-Ansatz vergleichen, sehen wir die beiden Schritte für eingehenden Datenverkehr, der durch das Gateway geleitet und von \*Route umgeleitet wird.

Abbildung 4.11: Gateway-API

Wie lassen sie sich vergleichen?

|     |     |     |
| --- | --- | --- |
|     | **Ingress** | **Gateway-API** |
| Protokolle | Nur HTTP/HTTPS | L4- und L7-Protokolle |
| Mandantenfähigkeit | Schwierige/benutzerdefinierte Erweiterungen | Multi-Tenant-Design |
| Spezifikationen | Annotationsbasiert, controllerspezifisch | Controllerunabhängig, eigene Ressource, standardisiert |
| Definition/Ressource | Eingangsressource | Gateway, GatewayClass, \*Route-Ressourcen |
| Routing | Host-/Pfad-basiert | Unterstützt Header |
| Verkehrsmanagement | Auf den Anbieter beschränkt | Integriert/definiert |

Tabelle 4.2: Vergleich zwischen Ingress und der Gateway-API

Dieser umfangreiche Funktionsumfang ist ein echter Game-Changer für alle, die Plattformen entwickeln müssen. Bisher mussten die meisten dieser Funktionen kommerziell erworben oder mit einigen Hacker-Workarounds und selbst entwickelten Tools brutal in den Cluster gezwungen werden. Mit der Gateway-API wird jedoch eine Vielzahl von Protokollen unterstützt, und sie verfügt über zwei interessante Zusatzfunktionen.

Mit der Gateway-API können Sie namensraumübergreifende Routen erstellen, entweder mit ReferenceGrant oder mit AllowedRoutes. Die zulässigen Routen werden über Referenzbindungen implementiert, die vom Gateway-Eigentümer definiert werden müssen, aus welchen Namensräumen Datenverkehr erwartet wird. In der Praxis wird die Gateway-Konfiguration wie folgt erweitert:

Namespaces:

&nbsp; from: Selector

&nbsp; selector:

&nbsp;   matchExpressions:

&nbsp;   - Schlüssel: kubernetes.io/metadata.name

&nbsp;     operator: In

&nbsp;     Werte:

&nbsp;     - alpha

&nbsp;     - omega

KopierenErklären

Dadurch wird der Datenverkehr aus den Namespaces alpha und omega zugelassen.

Alternativ können wir einen ReferenceGrant verwenden, der wie folgt beschrieben wird:

ReferenceGrant kann verwendet werden, um namensraumübergreifende Verweise innerhalb der Gateway-API zu ermöglichen. Insbesondere können Routen Datenverkehr an Backends in anderen Namespaces weiterleiten oder Gateways können auf Secrets in einem anderen Namespace verweisen.

Das klingt ähnlich, ist es aber nicht. Vergleichen wir sie:

- ReferenceGrant: Ein Gateway und eine Route im Namespace A gewähren einem Dienst im Namespace B die Weiterleitung von Datenverkehr.
- AllowedRoutes: Eine Route zu Namespace B wird in einem Gateway in Namespace C konfiguriert

Neben diesen zusätzlichen Sicherheitsstufen über Namespaces hinweg verfügt die Gateway-API auch über eigene Erweiterungsfunktionen. Mit ihnen können Sie Ihre eigene PolicyAttachment definieren, z. B. BackendTLSPolicy, um die ordnungsgemäße Verwendung von TLS zu überprüfen.

Eine letzte Anmerkung, bevor wir fortfahren. Die Gateway-API verfügt über Personas. Personas sind vordefinierte Rollen, die eine detaillierte Nutzung der Gateway-Funktionen ermöglichen. Ingress hat nur eine Persona, einen Benutzer, unabhängig davon, ob es sich um einen Administrator oder einen Entwickler handelt. Die folgende Tabelle zeigt die Schreibberechtigungen dieser Personas in einem vierstufigen Modell:

Abbildung 4.12: Schreibberechtigungen für ein erweitertes vierstufiges Modell

An dieser Stelle ist die Gateway-API der wahre Retter unzähliger Nächte, in denen es darum ging, den eingehenden Datenverkehr richtig zu gestalten und eine Multi-Tenant-Plattform mit einem klaren und transparenten Ansatz aufzubauen.

ExternalDNS

Das von den Kubernetes-Mitwirkenden entwickelte ExternalDNS-Projekt ist ein Tool, das häufig in Cloud-basierten Kubernetes-Clustern verwendet wird, aber dennoch nicht oft als relevante Implementierung hervorgehoben wird. Es überbrückt jedoch die Lücke zwischen einigen zufälligen IPs von Pods im Cluster, leitet sie an ein öffentlich oder privat erreichbares DNS weiter und leitet den Datenverkehr an die Anwendung innerhalb der Plattform weiter. ExternalDNS bietet Unterstützung für fast alle Cloud- und Cloud-ähnlichen Umgebungen sowie für verkehrs- und inhaltsorientierte Dienste wie CloudFlare.

ExternalDNS ist jedoch kein DNS. Überraschung! Es liest die Ressourcen aus der Kubernetes-API und konfiguriert das externe DNS so, dass es auf die öffentlichen Endpunkte des Clusters verweist. Man könnte auch sagen, dass ExternalDNS es Ihnen ermöglicht, DNS-Einträge dynamisch über Kubernetes-Ressourcen auf eine DNS-Anbieter-unabhängige Weise zu steuern.

Schauen wir uns einmal an, wie ExternalDNS mit dem CoreDNS von Kubernetes und dem Cloud DNS Service zusammenarbeitet. In der nächsten Abbildung sehen Sie links das verwaltete Kubernetes. In diesem Fall werden AWS EKS und CoreDNS auf Kubernetes ausgeführt, um interne DNS-Aufrufe aufzulösen. Wenn ExternalDNS bereitgestellt wird, beobachtet es die Gateway-, Ingress- und Service-Ressourcen. Wenn Änderungen vorgenommen werden oder neue Dienste hinzukommen, aktualisiert ExternalDNS die DNS-Einträge beim Cloud-Anbieter oder DNS-Dienstanbieter.

Abbildung 4.13: Externes DNS

Bei der Suche nach einem alternativen Ansatz stehen Ihnen jedoch in der Regel nur zwei Ausweichmöglichkeiten zur Verfügung: Sie erstellen die DNS-Einträge selbst (manuell) oder Sie automatisieren diesen Vorgang auf irgendeine Weise mit einem benutzerdefinierten Controller oder einer Funktion oder während des Erstellungsprozesses der Infrastruktur.

Daher ist es doppelt schmerzhaft, die Einschränkungen von ExternalDNS zu sehen:

- Es fehlt eine fein abgestimmte Kontrolle; beispielsweise erstellt ExternalDNS DNS-Einträge für alle Dienste und Ingresses aus jedem Namespace.
- ExternalDNS bietet Ihnen nur A-Einträge; wenn Sie einen TXT- oder CNAME-Eintrag benötigen, müssen Sie dies manuell tun
- Sie erhalten Standard-DNS-Konfigurationen für den DNS-Namen; andernfalls müssen Sie diese manuell definieren.

Darüber hinaus können auch erhöhte Kosten (aufgrund des unangemessenen Verhaltens bei der Erstellung von DNS-Einträgen) und zusätzliche Komplexität oder Latenz auftreten. Ich kann diesen Problemen nicht vollständig zustimmen, da es eine Frage der Handhabung ist.

Erwägen Sie die Verwendung von ExternalDNS nur, wenn Sie andere Teile des Kubernetes-Netzwerks beherrschen und in der Lage sind, Netzwerkrichtlinien und die Gateway-API detailliert zu verwalten, sodass Sie strenge Kontrolle darüber haben, welche Dienste erreichbar sind und wie. Erwägen Sie außerdem, die DNSSEC-Funktion zu aktivieren und eine DNS-Überwachung einzurichten.

Lastenausgleich, EndpointSlices und topologiebewusstes Routing

Zum Abschluss des Abschnitts über Netzwerke werden wir kurz auf **Lastenausgleich**, **EndpointSlices** und **topologiebewusstes Routing** eingehen.

Der Lastenausgleich wird vom Ingress-Controller oder der Gateway-API innerhalb des Clusters übernommen. Dies kann in Kombination mit einem Cloud-Anbieter an einen externen Lastenausgleich ausgelagert werden. Alle großen Cloud-Anbieter haben ihren eigenen Ansatz, in der Regel über einen eigenen Controller, um den Managed Service Load Balancer zu verwalten. Was ist der Unterschied zwischen diesen Optionen? Wenn Sie Ihren eigenen Load Balancer innerhalb von Kubernetes betreiben, bedeutet dies zunächst, dass der gesamte Datenverkehr zu diesem Einstiegspunkt geleitet wird. Bei korrekter Einrichtung kann es sich dabei um mehrere Knoten mit einer sehr einfachen Lastverteilung handeln. Der Nachteil ist, dass ein Knoten, der aus irgendeinem Grund überlastet ist, dennoch den Datenverkehr verarbeiten und intern verteilen muss. Ein Cloud-Load Balancer verteilt die Last auf mehrere Knoten und erkennt je nach Art der Integration, ob ein Knoten mehr Last verarbeiten kann oder ob diese an einen anderen Knoten umgeleitet werden sollte. Ein Nachteil des öffentlichen Cloud-Load Balancers ist, dass Sie dafür auch bezahlen müssen.

EndpointSlices sind für große Cluster relevant. Endpunkte sind API-Objekte, die eine Liste von IP-Adressen und Ports definieren. Diese Adressen gehören zu den Pods, die einem Dienst dynamisch zugewiesen werden. Wenn ein Dienst erstellt wird, erstellt Kubernetes automatisch ein zugehöriges Endpunkt-Objekt. Das Endpunkt-Objekt verwaltet die IP-Adressen und Portnummern der Pods, die den Auswahlkriterien des Dienstes entsprechen. EndpointSlices wurden in Kubernetes 1.16 eingeführt. Sie bieten eine Möglichkeit, die Netzwerkendpunkte auf mehrere Ressourcen zu verteilen, wodurch die Belastung des Kubernetes-API-Servers reduziert und die Leistung großer Cluster verbessert wird. Während in der Vergangenheit ein einzelnes großes Endpunkt-Objekt für einen Dienst langsam wurde, werden nun mehrere kleine EndpointSlice-Objekte erstellt, die jeweils einen Teil der Endpunkte repräsentieren.

Die Steuerungsebene erstellt und verwaltet EndpointSlices so, dass nicht mehr als 100 Endpunkte pro Slice vorhanden sind. Dies kann bis zu einem Maximum von 1.000 geändert werden. Für den kube-proxy ist ein EndpointSlice die Quelle der Wahrheit für das Routing des internen Datenverkehrs.

EndpointSlices sind auch für das Topology-Aware Routing erforderlich. Mit Topology-Aware Routing können Sie den Datenverkehr innerhalb der **Availability Zone** (**AZ**) des Cloud-Anbieters halten. Dies hat zwei wesentliche Vorteile: Es reduziert die Netzwerkkosten und verbessert die Leistung. Anstatt dass ein Pod in AZ 1 mit einem anderen Pod in AZ 2 kommuniziert und dabei große Datenmengen sendet, kommuniziert der Pod in AZ 1 nun mit einer Replik (sofern verfügbar), die sich ebenfalls in AZ 1 befindet. Damit dies optimal funktioniert, sollte der eingehende Datenverkehr über einen externen Load Balancer gleichmäßig verteilt werden und Sie sollten mindestens drei Endpunkte pro Zone haben. Andernfalls kann der Controller diesen Endpunkt mit einer Wahrscheinlichkeit von etwa 50 % nicht zuweisen.

Kubernetes als Teil der Plattform-Steuerungsebene

Wenn wir auf das zweite Kapitel zurückblicken, sehen wir in der Referenzarchitektur, dass eine Plattform stark verteilt sein kann und auf vielen Diensten basiert, die aus einer übergeordneten Perspektive betrachtet vielleicht gar nicht zusammen gehören. Wir haben diskutiert, dass Kubernetes oft zu einem zentralen Bestandteil Ihrer Plattform werden kann. Aber wie zentral kann es werden? Wie bereits erwähnt, dient Kubernetes nicht nur dazu, Workloads auszuführen, sondern ist eine Plattform (basierend auf der Promise-Theorie und einem standardisierten Modell und einer API) zum Aufbau von Plattformen. Dadurch rückt Kubernetes mit einem Bein in die Plattform-Steuerungsebene und tut dies auf zwei Arten: als Ressourcen-Controller und als Plattform-Orchestrator.

Steuerung von Ressourcen aus Kubernetes heraus

Das Open-Source-Projekt Crossplane ist die einzige Anbieter-unabhängige Lösung für die Verwaltung von Cloud-Ressourcen innerhalb von Kubernetes. Ursprünglich entwickelt, um andere Kubernetes-Cluster innerhalb von Kubernetes zu verwalten, wurde es schnell zur universellen Lösung für den Umgang mit Cloud-Ressourcen. Cloud-Ressourcen sind als CRDs verfügbar und können über eine Spezifikationsdatei als Kubernetes-native Ressourcen definiert werden. Dies gibt Benutzern die Möglichkeit, ihre Anforderungen zu definieren und die Erstellung der Ressourcen der Promise-Theorie von Kubernetes zu überlassen. Für die verschiedenen Clouds stehen sogenannte Provider zur Verfügung, die die verfügbaren Ressourcen definieren. Ein Benutzer kann einzelne Ressourcen oder ganze Kompositionen erstellen, bei denen es sich um mehrere zusammengehörige Ressourcen handelt.

Das Problem der externen gegenüber intern definierten Ressourcen

Was ist der richtige Ansatz für die Verwaltung von Ressourcen? Sollten sie von einem Infrastrukturteam oder anhand von Eingaben aus Nachfrageformularen definiert werden? Können sie vom Benutzer über die Plattform definiert werden? Alles ist möglich, aber es gibt keine einfache Antwort.

Schauen wir uns die beiden Ansätze einmal an. Betrachten wir zunächst ein Szenario bei Financial One ACME, das aus einem eher traditionellen, konservativen Umfeld stammt: Die Infrastrukturteams haben in den letzten Jahren um Automatisierung und einen deklarativen Ansatz gekämpft. Während sie ihre lokalen Umgebungen über Ansible verwalten, haben sie sich für die Cloud-Anbieter für eine einfachere Lösung entschieden: Terraform (oder OpenTofu). Wir werden nicht den gesamten Stack durchgehen, aber bis wir zur Kubernetes-Plattform kommen, wird alles über klassische CI/CD-Push-Prinzipien und IaC über Terraform orchestriert.

Finanzwesen ACME startet ein neues Projekt zur Entwicklung einer maßgeschneiderten Software für den internen Gebrauch. Das Team wird die ACME-Plattform nutzen und an der Basisarchitektur des Systems arbeiten. Es hat festgelegt, dass es einen bestimmten Dateispeicher, einen Cache, eine relationale Datenbank, einen Benachrichtigungsdienst und einen Nachrichten-Streaming-Dienst benötigt. Da die Plattform einen gewissen Self-Service bietet, kann das Team die Terraform-Module in sein Repository kopieren. Von hier aus übernimmt eine vordefinierte CI/CD-Pipeline die Konfiguration und stellt die Ressourcen in den definierten Umgebungen bereit. Diese selbst definierten, aber dennoch extern verwalteten Ressourcen sind in gewisser Weise vom Rest des Systems isoliert. Sie befinden sich zwar im selben Repository oder derselben Hierarchie und werden vom Team verwaltet, sind jedoch nicht stark integriert.

Auf der anderen Seite bieten sie ein gewisses Maß an Stabilität. Innerhalb des Benutzerbereichs der Plattform sind diese Ressourcen unsichtbar, außer dass ein Erkennungsdienst existiert. Wenn eine Organisation reift, können die Pipelines ohne Benachrichtigung des Eigentümers oder Benutzers angepasst werden. Infrastruktur und Anwendung sind jedoch klar voneinander getrennt, was aufgrund der völlig unterschiedlichen Lebenszyklen der Elemente von Vorteil ist.

Schneller Vorlauf: Financial One ACME hat eine Cloud-native Transformation durchlaufen und dabei Plattform-Engineering und IDPs maximal genutzt. Nun planen sie erneut ein internes Projekt, das sich natürlich völlig vom vorherigen unterscheidet, aber irgendwie genau die gleichen Anforderungen hat. Das Verhalten einiger Unternehmen wird sich nie ändern. Dieses Mal hat das Projektteam ein neues Projekt in seinem Entwicklerportal erstellt. Automatisch werden alle grundlegenden Anforderungen in ein neues Git-Repository übertragen. Die ausgewählten Ressourcen werden ausgewählt und an die Plattform übertragen, wo ein Controller entscheidet, wo diese Ressourcen bereitgestellt werden. Einige landen als Managed Services beim Cloud-Anbieter, andere in einem Shared-Service-Konto eines spezialisierten Teams und einige wenige im Namespace des Projekts. Nach einiger Zeit erkannte das Team, dass es die falsche Konfiguration gewählt hatte, und aufgrund der Anpassungen fand eine Migration zum neuen Dienst statt. Dieses Szenario kann genauso realistisch sein wie das vorherige, hat jedoch andere Auswirkungen.

Das Team muss genauer wissen, welche Anforderungen es hat; andererseits muss es den vordefinierten Bereitstellungen und Konfigurationen vertrauen. Das Plattform-Engineering-Team hat in Zusammenarbeit mit dem Betriebsteam Best Practices mit Leitplanken definiert, die die Funktionsfähigkeit gewährleisten, aber auch fast alle Anforderungen der Benutzer erfüllen. Innerhalb des Cluster-Benutzerbereichs kann das Team alle bereitgestellten Ressourcen finden und sie als Dienst innerhalb der Plattform behandeln, auch wenn sie nicht darin ausgeführt werden. Plötzliche Änderungen auf der Benutzerseite können jedoch dazu führen, dass Ressourcen an anderen Stellen plötzlich stark ansteigen oder gelöscht werden. Managed-Service-Teams müssen solche Änderungen ohne Vorwarnung bewältigen. Insgesamt verhalten sich alle abhängigen Ressourcen extrem volatil und dynamisch, sind schwer vorhersehbar und schwierig zu verwalten. Andererseits kann sich das Projekt voll und ganz auf den Ablauf und den Fortschritt konzentrieren, da externe Ressourcen innerhalb des Clusters verwaltet werden, anstatt zu lernen, wie man diese mit Ressourcenmanagementlösungen außerhalb des Clusters wie IaC verwaltet.

Beide Ansätze sind in Ordnung. Beide haben Vor- und Nachteile, und welcher für Ihr Unternehmen am besten geeignet ist, hängt oft mehr vom menschlichen Faktor als von technologischen Faktoren ab. Klar ist jedoch, dass intern definierte Cluster-Ressourcen dynamischer sind und weiter nach links, in die Verantwortung des Benutzers, verlagert werden als extern definierte Ressourcen.

Letztendlich wird es zu einer philosophischen Diskussion. Extern definierte Ressourcen sind traditioneller, während der intern definierte Ansatz progressiv und zukunftsorientiert ist. Allerdings haben wir nicht allzu viele Optionen, um clusterinterne Bereitstellungsprozesse auszuführen. Neben Crossplane gibt es viele Meta-Implementierungs-Controller, die beispielsweise benutzerdefinierte Ressourcen aus dem Cluster lesen und CI/CD-Pipelines auslösen. Das ist eine schlechte Notlösung, wenn man mich fragt.

In diesem Abschnitt haben wir uns mit den grundlegenden Funktionen befasst, die für Kubernetes erforderlich sind, den damit verbundenen Herausforderungen und wie wir diese lösen können. Außerdem fühlen sie sich nicht wie eine dieser verrückten Implementierungen an, die man auf Konferenzen sieht. Wenn man diese Grundlagen richtig hinbekommt, macht das den Unterschied und entscheidet darüber, ob alles andere darauf ein Vergnügen oder eine Qual ist. Als Nächstes schließen wir dieses Kapitel mit einem Blick auf den Ansatz zur Ermittlung der richtigen Knotengrößen und die Auswirkungen auf Flexibilität und Zuverlässigkeit.

Entwerfen für Flexibilität, Zuverlässigkeit und Robustheit

Im vorherigen Teil haben wir die Skalierbarkeit von Clustern und das Zusammenspiel von VPA, HPA und CA besprochen. Dies trägt dazu bei, ein flexibles, zuverlässiges und robustes System zu schaffen. Ein wichtiger Aspekt dabei ist auch, dass Anpassungen möglich sind, solange sie Ihrem System nicht schaden. Die Komponenten des Clusters müssen nahtlos zusammenarbeiten, aber bei Bedarf auch austauschbar sein. Dies ist ein heikles Thema: Auf der einen Seite haben Sie einen atmenden Cluster, dessen Anforderungen im Laufe der Zeit wachsen und schrumpfen, und auf der anderen Seite haben Sie alle Erweiterungen auf und um den Cluster herum, mit denen Sie die bestmöglichen Funktionen für Ihren Anwendungsfall bereitstellen können. Außerdem gibt es die sich ständig weiterentwickelnde Open-Source-Community, die regelmäßig Updates und neue Entwicklungen bereitstellt, die integriert und Ihren Benutzern zur Verfügung gestellt werden sollten. Wie wir Ihnen bereits gesagt haben, müssen Sie deshalb eine Produktmentalität haben – um die bestmögliche Plattform für Ihre Benutzer zu entwickeln ( ). Werfen Sie Dinge weg, die Sie nicht brauchen oder die veraltet sind, aber behalten Sie das gesamte System als Ihren Kern.

Aus irgendeinem Grund gibt es immer noch Diskussionen darüber, ob Sie Ihre gesamte Arbeitslast auf Kubernetes verlagern sollten und ob dies zuverlässig ist. Wir müssen diese Diskussion aus zwei Perspektiven betrachten: bottom-up ausgehend von der Infrastruktur und den Kernaufgaben von Kubernetes und top-down ausgehend von dem, was der Benutzer sehen und erleben kann.

Verbrauch optimieren oder genügend Spielraum lassen

Wie wir in [Kapitel 2](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) gelernt haben, stehen der Kubernetes-Cluster und die von ihm verwaltete Arbeitslast in einer interessanten Beziehung zueinander und beeinflussen sich gegenseitig. Einige Anwendungen benötigen mehr CPU-Leistung, andere skalieren stattdessen nach oben, und der Rest läuft einfach nach Bedarf. Die richtige Balance zu finden ist nicht einfach, aber ein ideales Ziel ist ein hoher Ressourcenverbrauch, da dadurch die Nutzung der verfügbaren Ressourcen und damit die Kosten optimiert werden.

Wie man die richtige Größe für Cluster findet

Die richtige Größe für den Cluster zu ermitteln, ist immer eine Herausforderung. Die richtige Lösung zu finden, hängt ganz klar von den jeweiligen Umständen ab. Nehmen wir das Beispiel von Financial One ACME, das einen neuen Cluster bereitstellen muss. Wir wissen nicht viel über die zu erwartende Workload, nur dass sie etwas Speicherplatz benötigt und einige bewegliche Teile hat, die nicht so ressourcenintensiv sind. Daher können wir eine der folgenden Optionen wählen:

- 1x 16 vCPU, 64 GB Arbeitsspeicher
- 2x 8 vCPU, 32 GB Arbeitsspeicher
- 4x 4 vCPU, 16 GB Arbeitsspeicher
- 8x 2 vCPU, 8 GB Arbeitsspeicher

Aus Gründen der Verfügbarkeit wäre die erste Option keine gute Idee. Wenn Sie ein Update im Cluster durchführen und das gesamte System ausfällt oder Sie einen neuen Knoten bereitstellen müssen, müssen Sie alle Anwendungen verschieben und den alten Knoten herunterfahren. Option 4 umfasst viele Knoten. Aufgrund ihrer geringen Größe kann dies zu einer Ressourcenknappheit führen, da einige für den Cluster erforderliche Basiskomponenten einen Teil der CPU und des Arbeitsspeichers beanspruchen. Darüber hinaus kann es je nach Cloud-Anbieter sein, dass Sie andere Einschränkungen haben, wie z. B. verfügbare IP-Adressen, Bandbreite und Speicherkapazität. Wenn Sie außerdem eine Anwendung haben, die 1 vCPU benötigt und auf 1,5 bis 2,0 vCPU skaliert werden kann, würde dies einen gesamten Knoten lahmlegen.

Wie viele Ressourcen werden jedoch pro Knoten von Kubernetes verwendet? Standardmäßig können wir für die CPU die folgenden Regeln verwenden:

- 6 % des ersten Kerns
- 1 % des zweiten Kerns
- 0,5 % der nächsten beiden Kerne
- 0,25 % ab dem 5. Kern

Wir haben auch einige grobe Regeln für den Speicher:

- 25 % der ersten 4 GB
- 20 % der folgenden 4 GB
- 10 % der nächsten 8 GB
- 6 % der nächsten 112 GB (bis zu 128 GB)
- 2 % von allem über 128 GB
- Wenn der Knoten über weniger als 1 GB Arbeitsspeicher verfügt, beträgt der Wert 255 MiB

Darüber hinaus hat jeder Knoten eine Eviction-Schwelle von 100 MB. Wenn die Ressourcen vollständig ausgelastet sind und die Schwelle überschritten wird, beginnt Kubernetes mit der Bereinigung einiger Pods, um einen vollständigen Speicherausfall zu verhindern. Bei learnk8s finden Sie einen sehr detaillierten Blogbeitrag zu diesem Thema (https://learnk8s.io/kubernetes-node-size).

Visualisieren wir diese Zahlen:

|     |     |     |     |
| --- | --- | --- | --- |
|     | **2 vCPU 8 GB RAM** | **4 vCPU 16 GB RAM** | **8 vCPU 32 GB RAM** |
| **Kubelet + OS vCPU** | 70 m oder 0,07 vCPU | 80 m oder 0,08 vCPU | 90 m oder 0,09 vCPU |
| **Kubelet + Betriebssystemspeicher** | 1,8 GB | 2,6 GB | 3,56 GB |
| **Eviction-Schwelle** | 100 MB | 100 MB | 100 MB |
| **Verfügbare vCPU** | 1930 m oder 1,9 vCPU | 3920 m oder 3,9 vCPU | 7910n oder 7,9 vCPU |
| **Verfügbarer Speicher** | 6,1 GB | 13,3 GB | 28,34 GB |

Tabelle 4.3: Ressourcenverbrauch und verfügbare Ressourcen für verschiedene Knotengrößen

Von diesen verfügbaren Ressourcen müssen Sie auch alles abziehen, was für das Clustering erforderlich ist, wie z. B. DaemonSet für die Protokollierung und Überwachung, kube-proxy, Speichertreiber usw.

Rechnerisch gesehen ist die Basisebene der verwendeten Ressourcen bei vielen kleinen Knoten größer als bei großen Knoten. Sehen wir uns ein Beispiel an. Zwei Knoten mit 2 vCPU und 8 GB RAM benötigen insgesamt 140 m CPU und 3,6 GB RAM, während ein Knoten mit 4 vCPU und 16 GB RAM nur 80 m CPU und 2,6 GB RAM benötigt. Das sind die Kosten für eine höhere Verfügbarkeit, aber im direkten Vergleich der verfügbaren Ressourcen benötigt ein einzelner Knoten weniger Ressourcen, die Kubernetes zugewiesen werden müssen. Idealerweise wird ein Knoten jedoch mit seiner maximalen Kapazität ausgelastet; wir betreiben keine virtuelle Maschine, bei der 80 % ungenutzter Ressourcen Standard sind! Eine Auslastung von mindestens 80 % eines Knotens wäre das Ziel, um das beste Preis-Leistungs-Verhältnis zu erzielen. Dies liegt auch an der Energieproportionalität eines Servers. Der Energiebedarf einer CPU skaliert nicht linear mit der Arbeitslast.

Stellen Sie sich vor, dass ein Server bis zu 200 Watt verbrauchen kann. Dann würden die meisten Server zwischen 150 und 180 Watt für eine CPU-Auslastung von etwa 50 % benötigen. Das bedeutet: Je mehr ein Server ausgelastet ist, desto besser ist das Verhältnis zwischen Energieverbrauch und CPU-Auslastung, was auch kosteneffizienter und nachhaltiger ist.

Bei der Auswahl der Knotengrößen für den Cluster müssen wir weitere Faktoren berücksichtigen:

- Wenn Sie nur wenige große Knoten bereitstellen, der Benutzer jedoch eine Anti-Affinität definiert, sodass auf jedem Knoten nur ein Pod einer Replik ausgeführt wird, und Sie nicht über genügend Knoten verfügen, weil die erwarteten Replikate zu hoch sind, können einige Pods nicht mehr geplant werden.
- Große Knoten werden häufig nicht ausreichend ausgelastet, sodass Sie mehr Geld für etwas ausgeben, das Sie nicht nutzen.
- Wenn Sie zu viele kleine Knoten haben und ständig auf ausstehende Pods stoßen, für die jeder Cluster skaliert werden muss, könnte dies die Benutzer verärgern, da die Skalierung neuer Knoten immer Zeit in Anspruch nimmt. Außerdem könnte dies die Verfügbarkeit einer App beeinträchtigen, wenn sie ständig unter Ressourcenbeschränkungen läuft.
- Viele Knoten verursachen ein höheres Maß an Netzwerkkommunikation, Container-Image-Pulls und doppelten Image-Speicher auf jedem Knoten. Andernfalls ziehen Sie im schlimmsten Fall immer wieder ein Image aus einer Registry. Bei einem kleinen Cluster ist das kein Problem, aber bei einer großen Anzahl von Knoten wird dies zu einem ziemlichen Kommunikationsaufwand.
- Je mehr Knoten vorhanden sind, desto mehr Kommunikation findet zwischen ihnen und der Steuerungsebene statt. Ab einer bestimmten Anzahl von Anfragen bedeutet dies, dass die Knotengrößen der Steuerungsebene erhöht werden müssen.

Die richtige Knoten- und Clustergröße zu finden, ist eine Wissenschaft für sich. Keines der beiden Extreme ist gut. Beginnen Sie damit, sich die Art der zu erwartenden Arbeitslast anzusehen. Wenn Sie sich nicht sicher sind, beginnen Sie mit einer mittleren Größe und passen Sie die Knotengrößen bei Bedarf an. Denken Sie auch daran, immer etwas mehr Speicher zur Verfügung zu haben. Die Kernkomponenten von Kubernetes pro Knoten benötigen nicht viel CPU, aber mindestens 2 bis 3 GB Speicher plus alle anderen Standardkomponenten.

Lösungsraum

Die meisten Public-Cloud-Anbieter bieten die Möglichkeit, mehrere Instanztypen für Kubernetes-Knoten auszuführen. Dies ist für verschiedene Anwendungsfälle hilfreich, von der Isolierung von Workloads über die Optimierung der Auslastung bis hin zur Migration von einer CPU-Architektur zu einer anderen. Wir haben auch über die GPU-Auslastung gesprochen, die Sie in solchen Szenarien kombinieren können, um Nicht-GPU-Workloads auf CPU-Knoten auszuführen, während Sie das Modelltraining auf den GPU-Instanzen durchführen.

Dazu müssen Sie die Knoten korrekt verwalten und kennzeichnen und den Benutzern einen transparenten Ansatz und Unterstützung für die Definition ihrer Affinitätseinstellungen bieten.

Um die richtigen Knotengrößen zu ermitteln, bietet learnk8s Ihnen auch einen Instanzrechner (https://learnk8s.io/kubernetes-instance-calculator), den Sie in Betracht ziehen sollten, bevor Sie mit der Erstellung Ihrer eigenen Excel-Tabelle für die Berechnungen beginnen.

Auch wenn die Definition der Clustergröße und -skalierung nicht so relevant erscheint, können Sie mit den richtigen Knotengrößen einen direkten Einfluss auf Kosten, Auslastung, Anwendungsverfügbarkeit, Benutzererfahrung und die Anzahl der zusätzlichen Implementierungen nehmen, die Sie durchführen müssen, um potenzielle Nachteile auszugleichen.

Zusammenfassung

In diesem Kapitel haben wir uns mit einigen der relevanten Komponenten von Kubernetes als Eckpfeiler Ihrer Plattform näher befasst. Zunächst haben wir untersucht, ob Kubernetes die richtige Wahl ist, und uns angesehen, warum es oft der richtige Weg ist. Mit der Promise-Theorie als Kernstück und vielen robusten Funktionen für den Betrieb und die Erweiterung einer Plattform ist Kubernetes eine nahezu perfekte Grundlage für eine Plattform. Von hier aus haben wir uns einige der grundlegenden Elemente von Kubernetes angesehen: Speicher, Netzwerk, CPU-Architekturen und GPU-Unterstützung. In diesem Zusammenhang haben wir einige Designüberlegungen und Probleme kennengelernt, mit denen wir bei der Implementierung von Kubernetes konfrontiert sein könnten. Auch wenn sich Kubernetes als Grundlage in jeder Umgebung anders anfühlen mag, ist es möglich, eine einheitliche Erfahrung zu schaffen. Dies bringt jedoch erhebliche Nachteile mit sich, wie z. B. den Verlust der Funktionen bestimmter Cloud-Anbieter, Flexibilität und Anpassbarkeit.

Als Nächstes haben wir darüber gesprochen, wie man die Balance zwischen einem sehr starren und einem sehr flexiblen System findet. Beide können als robust und zuverlässig angesehen werden, bringen jedoch sehr unterschiedliche Herausforderungen und Probleme mit sich. Daher haben wir ein kurzes Gedankenexperiment durchgeführt, um die richtigen Clustergrößen und Knotentypen zu finden, bevor wir diesen Abschnitt mit einer Diskussion über Ansätze zur Implementierung von Schutzvorrichtungen für den Benutzerbereich abgeschlossen haben. Dies hilft uns, Flexibilität innerhalb des Benutzerbereichs zu bieten, schützt die Plattform jedoch vor Fehlverhalten und falsch konfigurierten Diensten durch Benutzer. Das haben wir in diesem Kapitel gelernt.

Im nächsten Kapitel konzentrieren wir uns auf die Automatisierung von Plattformen. Neben der Infrastruktur ist die Automatisierung ein wichtiger Bestandteil einer Plattform und kann, wie Sie später sehen werden, langfristig zu einem Engpass und Kostentreiber werden. Sie lernen, wie Sie einen geeigneten Release-Prozess entwerfen, wie Sie ihn in CI/CD und GitOps implementieren und wie Sie diese Kombination für den Lebenszyklus der Plattform-Artefakte nutzen können. Wir zeigen Ihnen auch, wie Sie diesen Prozess effektiv beobachten können.

Weiterführende Literatur

- \[1\] Objekte in Kubernetes: [https://kubernetes.io/docs/concepts/overview/working-with-objects/](https://kubernetes.io/docs/concepts/overview/working-with-objects/%0A)
- \[2\] Karpenter: [https://karpenter.sh/](https://karpenter.sh/%0A)
- \[3\] CSI-Treiber-Index: [https://kubernetes-csi.github.io/docs/drivers.html](https://kubernetes-csi.github.io/docs/drivers.html%0A)
- \[4\] RISC-V-Kubernetes-Knoten auf Scaleway: [https://www.scaleway.com/en/docs/bare-metal/elastic-metal/how-to/kubernetes-on-riscv/](https://www.scaleway.com/en/docs/bare-metal/elastic-metal/how-to/kubernetes-on-riscv/%0A)
- \[5\] SpinKube: [https://www.spinkube.dev/](https://www.spinkube.dev/%0A)
- \[6\] SpinKube-Übersicht: [https://www.spinkube.dev/docs/overview/](https://www.spinkube.dev/docs/overview/%0A)
- \[7\] Nvidia – Verbesserung der GPU-Auslastung in Kubernetes: https://developer.nvidia.com/blog/improving-gpu-utilization-in-kubernetes/
- \[8\] DRA mit GPU:
    - https://docs.google.com/document/d/1BNWqgx_SmZDi-va_V31v3DnuVwYnF2EmN7D-O_fB6Oo/edit#heading=h.bxuci8gx6hna
    - https://static.sched.com/hosted_files/colocatedeventseu2024/83/Best%20Practices%20for%20LLM%20Serving%20with%20DRA.pdf
    - https://github.com/NVIDIA/k8s-dra-driver?tab=re
