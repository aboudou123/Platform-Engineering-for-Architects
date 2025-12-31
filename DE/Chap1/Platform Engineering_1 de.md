***Im Rahmen meiner Masterarbeit befasse ich mich mit dem Thema Plattform-Engineering in einem der führenden Robotikunternehmen Bayerns***.
***Dieses GitHub-Repository dient der schrittweisen Dokumentation meiner Forschungsarbeit sowie der strukturierten Aufbereitung von Methoden, Ergebnissen und gewonnenen Erkenntnissen***.

***Interessierte Leserinnen und Leser sind eingeladen, den Entstehungsprozess nachzuvollziehen. Konstruktive Anmerkungen, fachliche Hinweise und weiterführende Ideen sind ausdrücklich willkommen***



# Plattform-Engineering und die Kunst, Plattformen zu entwickeln #

In diesem ersten Kapitel lernen wir, wie wir erkennen können, wann unser Unternehmen bereit ist, eine Plattform zu planen. Dazu klären wir, warum Plattformen zu einem so wichtigen Thema geworden sind, wie eine produktorientierte Denkweise dazu passt und anhand welcher Kriterien wir feststellen können, ob wir für eine Plattform bereit sind oder nicht. Wir lernen die Unterschiede zwischen Plattformen kennen und erfahren, welche Plattformtypen am häufigsten aufgebaut werden.

Als Nächstes werden wir uns mit den drei Kernelementen einer Plattform befassen: der allgegenwärtigen Cloud, der Entwicklererfahrung und den Hauptmerkmalen einer Plattform. Insgesamt werden wir wiederkehrende Elemente des Cloud-Native-Engineering sehen. Dies führt uns zu der Frage, ob wir wirklich noch eine weitere Abstraktionsschicht benötigen. Wir werden auch überlegen, ob eine Plattform uns helfen wird, das Problem einer hohen kognitiven Belastung durch übertechnisierte komplexe Systeme und Entwicklungsprozesse zu überwinden, oder ob sie am Ende nur eine weitere Schicht sein wird. Wir werden über einige dieser Schichten nachdenken, um eine Antwort für uns selbst zu finden.

Abschließend werden wir auf Aspekte eingehen, die über die Technologie und die Implementierung von Plattformen hinausgehen. Es ist entscheidend, die soziotechnischen Aspekte zu verstehen und den Menschen, unseren eigentlichen Stakeholdern, in den Mittelpunkt zu stellen. Dies ermöglicht es uns, ein besseres Plattformprodukt zu definieren und Ansätze für eine enge Zusammenarbeit zu finden.

In diesem Kapitel behandeln wir die folgenden Hauptthemen:

- Die Nachfrage nach Plattformen als Produkt
- Implementierung von entwickler- und produktorientierten Lösungen
- Brauchen wir noch eine weitere Abstraktionsschicht?
- Soziotechnische Aspekte

# **Die Nachfrage nach Plattformen als Produkt**

In der Cloud-nativen Umgebung hat kaum ein anderes Thema in den letzten Jahren einen solchen Mythos aufgebaut wie der Begriff Plattform und die damit verbundene Rolle des Plattform-Ingenieurs. Wie bei der Einführung der ersten brauchbaren CI/CD-Pipelines führte dieser Goldrausch zu einer raschen Anpassung, oft ohne Sinn und Verstand. Jetzt, da wir im Tal des Wissens „ ” angekommen sind, können wir uns ausführlich mit der Frage beschäftigen: Brauchen Sie eine Plattform, und wenn ja, wie gestalten und implementieren Sie sie, damit sie auch in Zukunft Bestand hat?

Um diese Frage zu beantworten, sollten wir uns zunächst ansehen, was eine solche Plattform ausmacht. Eine Plattform ist die Kombination verschiedener Fähigkeiten, die erforderlich sind, um traditionelle und Cloud-native Umgebungen zu beherrschen, sodass sie den Endbenutzer bei der Entwicklung, Bereitstellung und dem Betrieb einer Anwendung unterstützt. Plattformen können ein Wegbereiter sein, um nicht-Cloud-native Infrastrukturen in wertvolle Ressourcen zu verwandeln. Die meisten Computing-Plattformen bieten heute jedoch eine Art API, mit der die Bereitstellung und Instrumentierung der verfügbaren Ressourcen automatisiert und die Grundlage einer Plattform geschaffen werden kann. Plattformen bieten Endbenutzern Konsistenz über alle Arten von Ressourcen hinweg und gewähren Zugriff auf ihre Funktionen über eine Self-Service-API, Vorlagen, CLI oder andere Lösungen. Das folgende Beispiel verdeutlicht auch, dass eine Plattform aus vielen Komponenten besteht:


<img width="1059" height="608" alt="image" src="https://github.com/user-attachments/assets/734d4133-b1fd-4230-972b-817798f1df61" />


Abbildung 1.1: Beispiel für eine Plattform/IDP

Das Thema Plattform taucht in der Regel im Zusammenhang mit Cloud-Native auf, aber warum ist das so? Cloud-Native-Technologien ermöglichen es Unternehmen, skalierbare Anwendungen in öffentlichen, privaten und hybriden Clouds zu erstellen und auszuführen. Dieser Ansatz lässt sich am besten anhand von Funktionen wie Containern, standardisierter Servicebereitstellung, unveränderlicher Infrastruktur und deklarativen APIs veranschaulichen. Solche Funktionen realisieren lose gekoppelte System en, die widerstandsfähig, verwaltbar und beobachtbar sind. Diese ermöglichen es Entwicklern, mit minimalem Aufwand häufige Änderungen vorzunehmen. Kurz gesagt, eine Plattform ist ein Enabler für Cloud-Native-Computing und nutzt ihre Tools, um es zu instrumentalisieren.

# **Unternehmen und Entwickler profitieren gleichermaßen von Plattformen**

Die Erfahrung eines Softwareentwicklers auf einer Cloud-nativen Plattform unterscheidet sich von der Entwicklung von Software, die nativ auf einen Cloud-Anbieter ausgerichtet ist. Der Aufbau von Systemen, die sich auf einen **Cloud-Service-Provider** (**CSP**) konzentrieren, bindet Sie an die Logik dieses geschlossenen Ökosystems. Einen ähnlichen Effekt haben Sie sicherlich auch, wenn Sie auf Cloud-nativen Plattformen aufbauen, da diese oft Kubernetes-zentriert sind und die starke Vereinheitlichung der Integrationen in Richtung der Kubernetes-API nutzen. Der Haken dabei ist jedoch, dass Cloud-native Plattformen die gleiche Erfahrung bieten, ohne dass Sie die zugrunde liegende Infrastruktur erkennen. Da die meisten Unternehmen mindestens zwei bis drei Cloud- oder Cloud-ähnliche Dienstleister haben und bereits Schwierigkeiten bei der Anpassung dieser haben, ist eine Cloud-native Plattform ein Game Changer \[1\]. Die Entwicklung von Software auf einer Cloud-nativen Plattform verändert die Denkweise und die Architektur. Ohne diese Denkweise ist die Wahrscheinlichkeit eines Scheiterns jedoch hoch.

Bei einer Plattform sind jedoch mehr Aspekte zu berücksichtigen als nur das einheitliche Infrastrukturmanagement. Plattformen müssen für einen bestimmten Zweck entwickelt werden. Die gängige Definition, für wen Plattformen entwickelt werden und wer die Stakeholder für Plattformingenieure sind, besagt, dass dies ausschließlich Entwickler sind. Diese Definitionen lassen jedoch außer Acht, dass auch die gesamte Organisation, die Betriebsteams und andere Spezialistenteams von einer Plattform profitieren. Eine Plattform bietet Softwareentwicklern einen einfachen Zugangspunkt zum Erstellen, Testen, Bereitstellen, Veröffentlichen und Betreiben ihrer Software. Sie liefert tiefe Einblicke in die Nutzung und ermöglicht es den Betreuern und Administratoren, die Infrastruktur, die Plattform und die Integrationen ohne Bedenken zu warten. In der Geschäftssprache ausgedrückt kann eine Plattform eine schnellere Markteinführung ermöglichen, mit mehr Flexibilität bei der Änderung und Anpassung ihrer Komponenten, während gleichzeitig die Zuverlässigkeit und Robustheit hoch bleiben.

Was bedeutet das für ein Unternehmen heute? Aufgrund des Mangels an IT-Fachkräften auf dem Markt, des rasanten Wandels in der IT und der Überlastung der Schulungsteams für Cloud-Technologien und -Anbieter bietet eine Plattform die richtigen Anknüpfungspunkte für Kompetenzen. Wir brauchen diese Trennlinien, um dem Trend entgegenzuwirken, mehrere Disziplinen in einer einzigen Rolle wie DevOps zusammenzufassen. Außerdem sind Plattformingenieure, die DevOps-Methoden anwenden, keine DevOps. Wir müssen diese Rolle aktiv davor schützen, die Fehler der DevOps-Rolle zu wiederholen, und ihre Definition klar definieren. Plattformingenieure integrieren die von Experten bereitgestellten Funktionen, vereinfachen deren Nutzung durch ihre Plattform für Entwickler und ermöglichen den Ingenieuren einen Self-Service. Allerdings muss kein Entwickler ein Experte in mehreren Bereichen wie Sicherheit, Beobachtbarkeit, Infrastrukturkonfiguration und Automatisierung usw. werden. Dies steht im Gegensatz zu einem gängigen Bild von DevOps, die Experten für alles werden müssen, was innerhalb ihres Silos für ihre Anwendung erforderlich ist, um sie am Leben zu erhalten. Wir werden DevOps in Zukunft für die fortgeschrittene Handhabung von Anwendungen benötigen, aber wir müssen ihnen auch das Leben erleichtern.

Die Plattform bietet eine Integrationsschicht für die Bottom-up-Funktionen, die spezielle Kenntnisse erfordern, wie Sicherheit, Datenbanken oder sogar die Bereitstellung von VMs oder Bare-Metal-Servern, sowie für die Top-down-Nutzung durch Entwickler und DevOps. Wie in der folgenden Abbildung dargestellt, ist das Plattform-Engineering-Team für die Bereitstellung dieser Schicht verantwortlich.


<img width="968" height="510" alt="image" src="https://github.com/user-attachments/assets/e4966dc3-638b-4d39-b099-aed2082494fe" />



Abbildung 1.2: Fähigkeiten und Verantwortlichkeiten in einer plattformorientierten Organisation

Das bedeutet natürlich auch, dass ein weiteres Team von Experten geschult und ausgebildet werden muss. Allerdings kann ein vergleichsweise kleines Team von Plattformingenieuren in der Regel riesige Umgebungen aufbauen und betreiben. Eine Plattform reduziert im Idealfall die kognitive Belastung für alle anderen Teams innerhalb des Unternehmens und ermöglicht es ihnen, sich wieder auf ihren Kernwert zu konzentrieren, indem sie die Abläufe rund um den Entwicklungsprozess vereinfacht. Diese Plattform trägt dazu bei, Stress zu reduzieren und die Transparenz zu verbessern. Unternehmen aus aller Welt tauschen häufig ihre Erfahrungen mit Plattformen und Plattformteams aus, wobei der Tenor in der Regel lautet, wie sie bisher unlösbare Probleme gelöst haben ( ) oder wie sehr dies die Qualität ihrer Produkte und Dienstleistungen verbessert hat.

Diese Plattformen werden oft als **interne Entwicklerplattformen** (**Internal Developer Platforms**, **IDPs**) bezeichnet, da sie in der Regel für das interne Entwicklungsteam eines Unternehmens erstellt werden. In diesem Buch werden wir die Begriffe Plattform, IDP, Plattformprodukt und Cloud-native Plattform synonym verwenden. Zunächst möchten wir jedoch einige Aspekte etwas näher beleuchten:

- **Plattform**: Allgemeiner Begriff für die übergreifende Technologieebene, die eine Vereinheitlichung der Dienste für Entwickler ermöglicht.
- **IDP**: Betonung des Aspekts der Entwickler, **des Softwareentwicklungslebenszyklus** (**SDLC**) und der für die Softwareentwicklung erforderlichen Tools
- **Plattformprodukt oder Plattform als Produkt**: Hervorhebung des engagierten Teams, das sich um die Weiterentwicklungsfähigkeit und das langfristige Engagement einer Plattform kümmert und eine andere Denkweise etabliert.
- **Cloud-native Plattform**: Fokus auf der Abstraktion und der Möglichkeit, standardisierte APIs und Integrationen zu nutzen.

Diese Sichtweise mag detailliert erscheinen, aber der Begriff „Plattform“ selbst führt oft zu Verwirrung. Eine Cloud-Plattform ist doch auch eine Plattform, oder? Auch **Software as a Service** (**SaaS**) könnte als Plattform angesehen werden. Der Verweis auf eine Cloud-native Plattform oder IDP gibt die richtige Richtung vor und sorgt für Verständnis. Je nach Reifegrad Ihres Unternehmens ist es daher auch wichtig, diese Begriffe zu klären und ein gemeinsames Verständnis, eine gemeinsame Sprache und gemeinsames Wissen zu etablieren.

# **Fallstudien und Erfolgsgeschichten zu Plattformen**

Um die positiven Auswirkungen einer Plattform hervorzuheben, können wir uns drei völlig unterschiedliche Unternehmen und ihre Ergebnisse aus der Nutzung von IDPs ansehen. Alle diese Fälle konzentrieren sich in erster Linie auf Backstage als Entwicklerportal und Einstiegspunkt für die IDP.

Spotify, der Erfinder von Backstage und Vorreiter der IDP-Bewegung, behauptet, dass für seine internen Backstage-Nutzer Folgendes gilt:

- 2,3-mal aktiver auf GitHub
- 2x mehr Codeänderungen
- 2x mehr Bereitstellungen
- Die Einarbeitungszeit für neue Entwickler sank von 60 auf 20 Tage

Die Expedia Group meldet andere Zahlen:

- Die Erstellung einer neuen Komponente oder App dauert durchschnittlich vier Minuten
- Über 4.000 Benutzer nutzen das IDP mindestens 20 Minuten pro Tag
- Die technische Dokumentation wird über 50.000 Mal pro Monat aufgerufen
- Etwas mehr als 15 % der internen Entwicklertools sind in Backstage integriert, wodurch bereits weniger Kontextwechsel erforderlich sind

Das letzte Unternehmen, das wir uns ansehen sollten, ist Toyota:

- Projekte liefern nun wöchentlich statt monatlich Ergebnisse
- Pro Team werden 8 bis 12 Wochen an Overhead-Aufwand eingespart, was zu einer Kosten- oder Zeitersparnis von über 5 Millionen US-Dollar führt, die für die Wertschöpfung genutzt werden können
- Standardisierte Bereitstellungsvorlagen reduzieren Fehler und beschleunigen die Bereitstellung

All diese Zahlen sind im Kontext eines digital-nativen Unternehmens, eines Reise-Technologieunternehmens und eines der größten Automobilhersteller interessant. Jedes dieser Unternehmen kann einen klaren positiven Effekt vorweisen \[2\].

# **Projekte versus Produkte**

Was die Organisation betrifft, so wird die Einführung neuer Lösungen in der Regel als Projekt durchgeführt. Irgendwann hat also jemand beschlossen, Geld in den Aufbau einer eigenen Plattform zu investieren. Dieser Ansatz steht vor einem grundlegenden Problem: der Frist. Projekte müssen innerhalb eines vorgegebenen Zeit- und Budgetrahmens ein Ziel erreichen. Wenn das Projekt keine Zeit oder kein Geld mehr hat, konzentriert es sich auf den Betrieb und die Wartung. Diese beiden Teile eines Lebenszyklus werden als separate Dinge behandelt, was zu einer Phase des Aufschwungs und des Niedergangs führt. Um dies etwas zu verdeutlichen: Während der Implementierungsphase gibt es hohe Investitionen, viel Kommunikation und große Begeisterung. Nach Ablauf der Frist wird das Projekt jedoch zu einem toten Objekt, das gewartet werden muss. DevOps hat dieses Verhalten nicht geändert, sondern lediglich neue Namen, neue Rollen und andere Prozesse eingeführt. Letztendlich werden jedoch Budget, Personal und Aufmerksamkeit auf das nächste Projekt verlagert, während nur ein Bruchteil des ursprünglichen Budgets übrig bleibt. Dies ist frustrierend für Ingenieure, die hart an der Umsetzung gearbeitet haben, und wird mit der Zeit auch für das Unternehmen frustrierend, wenn die Kosten für die reine Wartung weiter steigen. Dennoch könnten die Personen, die „ ” aufgebaut haben, das Unternehmen verlassen oder sich anderen Projekten anschließen. Diese kurzfristige Sichtweise auf die Implementierung von Systemen hat langsam viele gute Projekte und den Teamgeist zerstört. Noch wichtiger ist, dass sie zeigt, dass der geschäftliche Nutzen der Lösung nicht klar ist. Wenn eine Implementierung, wie z. B. eine Plattform, einen eindeutigen Mehrwert bieten kann, sollte es keinen Grund geben, die Aufmerksamkeit abzuwenden und ihr Ende herbeizuführen.

Während es bei vielen Implementierungen als Projekte ein gültiger Ansatz ist, ist dies bei Plattformimplementierungen das Todesurteil. Reguläre Implementierungen sind funktionsfähig; sie können nach ihrer Fertigstellung weiterbestehen. Eine Plattform hingegen ist ständig in Bewegung, wird ständig aktualisiert und implementiert ständig neue Funktionen. Bei der Zusammenarbeit mit Open-Source- und Cloud-Anbietern lernen Sie früh, wie schnell Tools und Software in ihrem eigenen Entwicklungszyklus sind. Funktionen, Fehlerbehebungen und Sicherheitspatches werden kontinuierlich veröffentlicht. Dies ist eine große Herausforderung für größere Unternehmen, da sie noch an weitaus langsamere Release-Zyklen gewöhnt sind. Der Vorteil, mit dieser rasanten Entwicklung Schritt zu halten, besteht darin, dass Sie als Unternehmen häufig von neuen Funktionen und Möglichkeiten profitieren können. Dies ist ein Innovationsmotor und -förderer, der es Ihnen ermöglicht, Systeme auf andere Weise zu implementieren und Probleme zu lösen, die Ihnen vielleicht gar nicht bewusst sind. Ist ein Problem, das für Sie nicht schmerzhaft ist, ein echtes Problem? Unternehmen neigen dazu, solche Dinge nicht als Probleme zu betrachten, da sie es gewohnt sind, nur schmerzhafte Prozesse und Ansätze zu identifizieren.

Schauen wir uns ein Beispiel an. Im laufenden Jahr (2024) hat die Europäische Union ein Gesetz zur Verbesserung der Berichterstattung von Unternehmen über ihre CO2-Emissionen verabschiedet. Auf hoher Ebene umfasst dies auch IT-Ressourcen. Außerdem wurden in den letzten Jahren mehrere Open-Source-Stiftungen und -Projekte ins Leben gerufen, um Transparenz in den Energieverbrauch von Software zu bringen. Vor einem Jahr hätten wir nur sehr grobe, hochgeschätzte Zahlen zum Energieverbrauch eines Rechenzentrums, eines Servers und mit etwas manueller Bearbeitung auch einer Software melden können. Heute können wir detaillierte Informationen für jede Anwendung erhalten, die auf Bare Metal, Hypervisor oder containerisiert innerhalb von Kubernetes läuft, da sich die Tools weiterentwickelt haben, um diese Daten bereitzustellen. Öffentliche CSPs bieten immer mehr Einblicke in ihren eigenen Energieverbrauch. Was können wir für das kommende Jahr erwarten? Wir können noch bessere Zahlen erwarten, einschließlich des regionalen CO2-Mixes der Energie und der durchgängigen Sichtbarkeit und Transparenz dieser Zahlen. Mit Plattformen und Plattform-Engineering-Teams wird sich diese Transparenz im Laufe der Zeit ganz natürlich einstellen. Dazu ist kein Projekt erforderlich, das die IT auf den Kopf stellt. Wenn die Nachfrage danach laut wird, werden die Plattform-Engineering-Teams diese Funktionen in den Kern der Plattform implementieren, sodass alle, die diese Plattform zum Erstellen, Bereitstellen, Veröffentlichen und Betreiben von Software nutzen, davon profitieren.

Dies wird als Produktdenken bezeichnet, und es erscheint nur natürlich, dass sich Plattformen an die Anforderungen ihrer Umgebung anpassen.

# **Plattform als Produkt**

Plattformen als Produkt sind nutzerorientiert, hören auf die Anforderungen der Endnutzer und recherchieren diese aktiv, um ihre Dienste kontinuierlich zu verbessern. Ein Produkt ist sich auch seines Wertes bewusst. Ähnlich wie jede App auf Ihrem Mobiltelefon nutzt es seinen eigenen Wert, um die weitere Entwicklung und neue Funktionen zu finanzieren. Hier gibt es keine Fristen und keine Auslauftermine. Das Ziel ist einfach, mit jeder neuen Version besser zu werden. Das Ergebnis für ein Unternehmen ist ein Expertenteam, das aktiv an der zentralen Bereitstellung einer Plattform zur Wertschöpfung für Ihr Unternehmen arbeitet.

Das Entwerfen und Entwickeln einer Plattform als Produkt geht über den reinen technischen Aspekt hinaus. Es stellt organisatorische Herausforderungen dar, die berücksichtigt werden sollten, wenn Sie sich aktiv für den Aufbau einer Plattform entscheiden. Tatsächlich müssen Sie valide Zahlen zu Ihren Vorteilen liefern und zeigen, dass Ihre Plattform ihre eigenen Kosten trägt. Dies muss in der Denkweise des Produktverantwortlichen und der Plattformingenieure verankert sein. Dabei geht es nicht darum, zu Geschäftsleuten zu werden, sondern darum, den Grund für die Existenz klar zu kommunizieren und, was noch wichtiger ist, ein Produkt zu sein, das keine Frist hat.

Derzeit gibt es drei verschiedene Arten von Plattformen als Produkte:

- **IDPs**:
    - Bieten Softwareentwicklern ein erstklassiges Erlebnis
    - Ermöglichen den Entwicklungs- und Betriebsteams eine durchgängige Unterstützung und Transparenz ihrer Software
    - Sorgen für Governance, Compliance und Sicherheit
    - Bieten einen Self-Service für die Entwicklungsteams und vereinfachen den Bereitstellungsprozess
- **Datenwissenschafts- und Machine-Learning-Plattformen**:
    - Ähnlich wie IDPs und oft aus diesen hervorgegangen
    - Nutzen Sie ihre Skalierbarkeit, um Daten kosteneffizient zu recherchieren, zu analysieren und zu verarbeiten
    - Überwinden Sie komplexe Implementierungen und machen Sie sie allgemein verfügbar
    - Bieten Sie direkten, sicheren Zugriff auf relevante Datenquellen
- **Low-Code-/Business-Plattformen**:
    - Starker Trend zur Bereitstellung von Plattformen, die Lösungen bieten, mit denen neue Funktionen mit relativ geringem bis fast keinem Programmieraufwand implementiert werden können
    - Wir werden sie in den kommenden Jahren vermehrt sehen.

In unserem Buch konzentrieren wir uns auf die produktorientierte Sichtweise der Architektur von IDPs.

# **Benötigen Sie eine Plattform?**

Wie bei jeder anderen komplexen Umgebung müssen wir uns zunächst fragen: Brauchen wir wirklich eine Plattform? Wissen wir, wofür wir sie nutzen werden?

Obwohl Plattformen viele Vorteile bieten können, sind sie nicht immer die Antwort auf Ihre organisatorischen Fragen. Die folgenden Anzeichen deuten darauf hin, dass Sie noch nicht bereit für eine Plattform sind:

- Sie haben nur monolithische Anwendungen
- Sie haben kein eigenes Entwicklungsteam
- Ihr DevOps-, SysAdmin- oder Infrastrukturteam ist stark überlastet oder isoliert
- Sie haben sehr einfache Anwendungen, die überall ausgeführt werden können
- Es fällt Ihnen schwer, ein Budget für Schulungen zur Weiterentwicklung der Fähigkeiten Ihrer Teams bereitzustellen
- Sie verwenden in der Regel kommerzielle Standardlösungen

Wann ist ein IDP hingegen für Sie sinnvoll? Die folgenden Kriterien sind Indikatoren dafür, dass Sie für ein IDP bereit sind:

- Sie haben Anforderungen an mehrere Infrastrukturumgebungen oder verfolgen eine Multi-Cloud-Strategie
- Sie benötigen eine erweiterte Kontrolle über Ihre Umgebungen (Sicherheit, Compliance und tiefe Einblicke in das Verhalten der Infrastruktur und Anwendungen)
- Ihr Entwicklungsteam ist ständig mit nicht wertschöpfenden Aufgaben überlastet.
- Sie haben ein neugieriges und interessiertes DevOps- oder Infrastrukturteam, das ohne es zu wissen die ersten Schritte in Richtung einer Plattform unternommen hat
- Ihre Anwendung erfordert aufgrund der Microservice-Architektur eine gewisse Orchestrierung, da viele Komponenten oder verschiedene Integrationen gut zusammenarbeiten müssen
- Sie möchten Ihrem Unternehmen ermöglichen, Ihre IT hinsichtlich Kosten, Transparenz, Qualität oder Sicherheit zu optimieren

Bevor Sie ein Plattformprodukt für Ihr Unternehmen definieren, sollten Sie alle Punkte auf der Checkliste beantworten. Es ist sinnvoll, mehrere Punkte zu haben, die veranschaulichen, warum Sie es benötigen. Wenn beispielsweise ein Team nach einem IDP fragt oder jemand erwähnt, dass er auf einer Konferenz davon gehört hat, ist das keine solide Grundlage für eine solche Entscheidung. Die Einführung von Plattformen ist ein langer Weg, und unserer Erfahrung nach kann sie in relativ kurzer Zeit zum zentralen Schwerpunkt eines Unternehmens werden. Unter diesem Druck müssen Sie dennoch ein Ziel und eine Richtung haben.

Nachdem wir nun gelernt haben, wie wir den Zweck unserer Plattform definieren können, müssen wir die Frage diskutieren, ob wir diese zusätzliche Abstraktionsschicht wirklich brauchen.

# **Brauchen wir noch eine weitere Abstraktionsschicht?**

Fassen wir kurz zusammen, was wir bisher gesehen haben. Eine Plattform umschließt Ihre bestehende Infrastruktur und Ihre Umgebungen und legt eine Abstraktionsschicht darüber. Die Plattform erweitert sie um weitere Funktionen, sodass Ihre Entwicklungsteams sie automatisiert und selbstständig nutzen können.

Aus technischer Sicht stellt dies die nächste Abstraktionsebene dar. Daher ist es nur richtig, diese neue Struktur, die wir darüber legen, zu diskutieren. Von unten nach oben sehen wir die Bare-Metal-Infrastruktur, gefolgt vom Hypervisor für die Virtualisierung; darüber liegen die Cloud-Anbieter. Einige fügen vielleicht Container, Kubernetes oder serverlose Komponenten hinzu – und nun fügen wir unsere Plattform hinzu. Das sind mindestens vier Schichten, von denen jede verspricht, die darunterliegende Schicht einfacher zu machen, und die durch eine schwer zu definierende Metaebene aus Skripten, **Infrastructure as Code** (**IaC**), Cloud-Bibliotheken und Automatisierung miteinander verbunden sind. Brauchen wir also wirklich diese weitere Schicht, oder nutzen wir sie nur, um uns mit dem Aufbau von Dingen zu beschäftigen?

# **Entrümpeln Sie die Abstraktionsschichten**

Es gibt keine einfache Antwort auf diese Frage, aber wenn Sie sich den Zweck jeder Ebene ansehen, können Sie vielleicht Ihr eigenes Verständnis davon erweitern.

Hypervisoren wurden ursprünglich eingeführt, um die Bereitstellung von Hosts zu vereinfachen, damit Software ausgeführt werden und Server besser genutzt werden konnten. Heute dienen sie immer noch dem gleichen Zweck, könnten aber durch Kubernetes und Container-Laufzeiten ersetzt werden. Ein wichtiges Argument gegen diesen Ersatz ist, dass eine virtuelle Maschine eine bessere Isolierung und höhere Sicherheit bietet. Ohne zu sehr in diese Diskussion einzusteigen, gibt es Optionen, um eine sehr solide Isolierung zu erreichen, beispielsweise mit Kata-Containern. Die einzige Komponente, die Kopfzerbrechen bereitet, ist der Container mit dem Betriebssystem und seiner Laufzeitumgebung. Mit Blick auf die nächsten Jahre könnte **WebAssembly** (**Wasm**) ein Teil der Antwort auf dieses Problem sein. Ohne ein Betriebssystem im Container und mit reinen Binärdateien gibt es fast keine Angriffsmöglichkeiten. Aber lassen wir dem Ganzen noch etwas Zeit.

**Infrastructure as a Service** (**IaaS**)-Anbieter und öffentliche Cloud-Anbieter verbessern dies durch softwaredefinierten Speicher und Netzwerke, wodurch die Komplexität des Aufbaus eines eigenen Rechenzentrums und der Verwaltung aller physischen Abhängigkeiten reduziert wird. Darüber hinaus bieten sie weitere Funktionen für häufig verwendete Szenarien, wie Datenbanken, Lastenausgleich, Benutzerverwaltung, Nachrichtenwarteschlangen oder ML-Playgrounds und vortrainierte KI-Modelle. Dies ist eine sehr nützliche Implementierung, die zu einer raschen Entwicklung der Branche und einer Erweiterung der Möglichkeiten führt. Allerdings hat dies auch die gesamte Branche in eine problematische Richtung bewegt. Die Technologie entwickelt sich schneller, als Menschen und insbesondere Organisationen sich daran anpassen können. Wir sehen, dass es weltweit einen Mangel an professionellen Ingenieuren gibt, während Unternehmen jedes Jahr mehr digitale Dienste anbieten möchten. Lösungen und ihre Abhängigkeiten werden daher nativ für die Cloud entwickelt. Der Ertrag dieser Bemühungen kann erheblich sein. Sie sind in der Lage, jede Art von Infrastruktur und Dienstleistungen mit einer relativ kleinen Gruppe von Mitarbeitern weltweit zu verwalten. Die Realität sieht jedoch auch so aus, dass ein durchschnittliches Unternehmen über zwei bis drei IaaS- und öffentliche CPS-Anbieter verfügt, dazu (oft) noch eigene Rechenkapazitäten sowie etwa 10 SaaS-Anbieter, wobei diese Zahl bei großen Unternehmen auf bis zu 50 steigen kann \[1\]. CSPs bieten außerdem zwischen 40 und 200 verschiedene Dienste an. Mit anderen Worten: Wir können heute viel erreichen, aber die Komplexität dieser Umgebungen ist ebenfalls erheblich gestiegen.

Um diese Größenordnung zu bewältigen, sind IaC und **Cloud Development Kits** (**CDKs**) zu den Tools der Wahl geworden, um Ihre Landing Zones und Software-Integrationen zu verwalten. Das Lustige daran ist, dass Praktiken wie DevOps, die häufig falsch interpretiert werden, die Situation noch verschlimmert haben. Diese Fehlinterpretationen haben nun zu der unerwarteten Erwartung geführt, dass Entwickler auch die Infrastruktur für ihre Softwareanforderungen einrichten und warten sollen ( ).

Zu guter Letzt gibt es noch Systeme, die auf Containern, Kubernetes oder Serverless basieren. Für jedes dieser Systeme gibt es Dutzende von Optionen, um diese Umgebungen bereitzustellen, den Code zu implementieren und die Komponenten auszuführen. Es ist verständlich, dass es zu viele Ebenen gibt, um die man sich kümmern muss. Ihre Entwicklung ist jedoch sinnvoll, da man nicht mehr auf die alte Art und Weise Software zum Laufen bringen möchte. Das Pushen von Code in Images und von dort in eine von Ihnen gewählte Laufzeitumgebung vereinfacht den Bereitstellungsprozess.

Um die Komplexität darzustellen, können wir uns ein dreidimensionales Objekt wie einen Würfel aus Würfeln vorstellen. Die folgende Abbildung zeigt die verschiedenen Service-Ebenen, die unterschiedliche Reifegrade der Abstraktion darstellen, und wie Ebene für Ebene zusammenkommen, um eine IT-Umgebung zu bilden.

<img width="1028" height="534" alt="image" src="https://github.com/user-attachments/assets/569c863a-4f46-4176-bc75-18bbdbfbcc24" />


Abbildung 1.3: Die mehrdimensionale Komplexität der Abstraktion und Vereinfachung in der Datenverarbeitung

Nun ist diese Zahl stark vereinfacht, wenn man bedenkt, dass es in jeder Dimension Hunderte und Tausende von Optionen gibt. Dennoch gibt sie einen ersten guten Anhaltspunkt: Wenn Sie eine Plattform benötigen, bauen Sie eine Hülle um diese Konstruktion herum und zähmen Sie ihre immense Komplexität, um ihre Leistungsfähigkeit zu nutzen.

# **Die kognitive Belastung für Softwareentwickler und andere IT-Fachleute**

Um all diese Ebenen zu verwalten, müssen wir viele Tools kennen und einsetzen sowie verschiedene Prozesse befolgen. Es wird schwierig, sich auf die eigentliche Arbeit zu konzentrieren und Werte zu schaffen, wenn man viel Zeit für Dinge aufwenden muss, die unsere Arbeit eigentlich vereinfachen sollten. Dies wird als **kognitive Belastung** bezeichnet. Der Begriff, der ursprünglich von Daniel Bryant geprägt wurde, fasst die Arbeitsüberlastung und den mentalen Stress vieler Entwickler sowie anderer IT-Spezialisten zusammen. Die Verringerung der kognitiven Belastung bringt den Ingenieuren mehr Zufriedenheit und Freude, aber auch mehr Effektivität und Zuverlässigkeit. Die folgende Grafik vereinfacht die Perspektive auf das, was als Fachkraft über die verschiedenen Jahrzehnte hinweg zu bewältigen ist. In Zukunft müssen wir diese Belastung jedoch reduzieren. KI könnte neben neuen Konzepten für die Ausführung von Rechenprozessen und natürlich Plattformen ein Teil davon sein.

<img width="972" height="489" alt="image" src="https://github.com/user-attachments/assets/3feca999-5a3d-45b9-b034-20dd76949d49" />

Abbildung 1.4: Die erweiterte kognitive Belastung mit einer Prognose für eine ideale Zukunft

Technologie verändert sich nicht nur im Laufe der Zeit, sondern häuft sich auch an. Das bedeutet, dass wir Legacy-Systeme betreiben und warten müssen, während wir gleichzeitig Architekturstile ändern und neue Programmierparadigmen und neue Tools einführen. Dies verändert auch die Verantwortlichkeiten und erweitert sie weit über die typischen Grenzen der Stellenbeschreibung von vor einigen Jahren hinaus. Die Aufschlüsselung dieses Problems kann eine Antwort auf die Frage liefern, ob wir eine Plattform zur Lösung unserer Probleme benötigen oder ob deren Implementierung die Komplexität erneut erhöhen würde.

Letztendlich ist jede Organisation anders. Einige sind in den frühen 2000er Jahren stehen geblieben, andere versuchen kontinuierlich, sich an das anzupassen, was als Nächstes kommt. Selbst innerhalb derselben Organisation gibt es oft drastische Unterschiede. Eine Abteilung betreibt möglicherweise alles auf einigen VMs in ihrem eigenen Rechenzentrum, während eine andere Funktionen innerhalb eines globalen CDN oder Edge-Anbieters bereitstellt. Daher liegt es an Ihnen, eine Vision, Strategie und ein Ziel für Ihre Plattform zu entwickeln, wenn Sie diese wirklich benötigen.

Die Komplexität, mit der wir konfrontiert sind, und der Druck, der auf den Ingenieuren lastet, müssen angegangen werden, da die IT mit der Zeit immer komplizierter wird. Im nächsten Abschnitt konzentrieren wir uns auf die Implementierung der richtigen Lösung für Entwickler, um diese schwierige Entwicklung zu überwinden, die sogar zu Burnout führen kann.

# **Implementierung von entwickler- und produktorientierten Lösungen**

In den nächsten Jahren werden wir eine Weiterentwicklung des Cloud Computing erleben. In diesem Zusammenhang werden Plattformen eine entscheidende Rolle spielen. Einerseits wird die Cloud allgegenwärtig sein und zu einer Abstraktion für die Infrastruktur werden. Dabei spielt es keine Rolle, ob dies in Form von Edge-Computing oder sehr spezialisierten Diensten oder Angeboten geschieht. Andererseits müssen wir uns, wie wir im vorigen Abschnitt gelernt haben, darauf konzentrieren, Umgebungen bereitzustellen, die Entwicklern und anderen Rollen die bestmögliche Erfahrung ermöglichen, damit diese sich auf die Wertschöpfung konzentrieren können. Die praktische Zusammenführung dieser Elemente ist der Schlüssel dafür, dass eine IT-Organisation mit dem Markt Schritt halten und gleichzeitig kontinuierlich Wert für Ihr Unternehmen schaffen kann.

# **Die allgegenwärtige Cloud**

Die **allgegenwärtige Cloud** ist keine einzelne Lösung. Sie bündelt eine Vielzahl von Cloud-Computing-Funktionen, die einen transformativen Wandel durchlaufen, um Unternehmen und Innovationen maßgeblich voranzutreiben. Die wichtigsten Fortschritte konzentrieren sich auf die Integration von Cloud-Technologien überall, von privaten Rechenzentren über verteilte Rechnernetzwerke bis hin zum Edge. Die allgegenwärtige Cloud geht jedoch noch darüber hinaus. Sie folgt Konzepten zur Überbrückung physischer Lücken durch Sensoren, IoT-Komponenten, mobile Geräte und andere intelligente vernetzte Lösungen. Daher ist sie auch unter anderen Begriffen wie **Ubiquitous Computing**, **Ambient Intelligence** oder **Everywhere** bekannt.

Das Forschungsunternehmen Gartner geht davon aus, dass sechs weitere Technologien die allgegenwärtige Cloud prägen und ihre Natur definieren werden \[3\]:

- **Augmented FinOps**: Kombiniert DevOps-Methoden mit Kostenoptimierung und Budgetierung
- **Cloud Development Environments** (**CDEs**): Vereinfachen und vereinheitlichen die Entwicklungsumgebung, reduzieren menschliche Fehler und gewährleisten Reproduzierbarkeit
- **Cloud-Nachhaltigkeit**: Erzielung ökologischer, sozialer und wirtschaftlicher Vorteile, Verringerung der schädlichen Auswirkungen der stark wachsenden Cloud-Computing-Technologie und Nutzung ihrer Leistungsfähigkeit für gute Zwecke
- **Cloud-native**: Implementierung der zuvor definierten Cloud-Eigenschaften
- **Cloud-out to the edge**: CSP-Fähigkeiten, die bis an den Rand erweitert wurden
- **Wasm**: Die potenziell allgegenwärtige Laufzeitumgebung und das Binärformat für überall, aber nicht unbedingt für alles

Wir müssen uns jedoch fragen, warum dies für uns als Plattformingenieure, Architekten und Entwickler jetzt relevant ist.

Erstens finden sich viele der Technologien, an denen wir bereits arbeiten, in diesen Definitionen und Annahmen wieder. Cloud-native, FinOps, Edge und CDEs sind tägliche Realität, während nachhaltige IT und Wasm in den letzten Jahren eine starke Entwicklung erfahren haben. All dies ist relevant, um deutlich zu machen, dass wir nicht über Science-Fiction-Technologien diskutieren, die in den nächsten 100 Jahren nicht realisierbar sein werden. Es geschieht gerade jetzt und ist einsatzbereit. Wir entwickeln und innovieren all diese Grundlagen; sie sind nur vielleicht nicht so sichtbar und prominent wie GenAI.

Zweitens müssen Unternehmen, um den maximalen Wert aus ihren Cloud-Investitionen zu ziehen, eine automatisierte operative Skalierung einführen, Cloud-native Plattform-Tools nutzen und eine effektive Governance implementieren. Diese Plattformen integrieren wichtige Dienste wie SaaS, **Platform as a Service** (**PaaS**) und IaaS, um umfassende Produktangebote mit modularen Funktionen zu schaffen. IT-Führungskräfte werden ermutigt, die Modularität dieser Plattformen zu nutzen, um angesichts schneller Marktveränderungen anpassungsfähig und agil zu bleiben. Stellen Sie sich die Komplexität solcher Umgebungen ohne eine Plattform vor, die diesen großen Bewegungsspielraum zähmt. Trotz dieser Komplexität müssen wir uns weiterhin auf die Produktperspektive konzentrieren, da es sonst schwierig sein wird, auch in Zukunft zuverlässige IT-Services und -Lösungen anzubieten.

<img width="986" height="542" alt="image" src="https://github.com/user-attachments/assets/e73ef7ab-ce8a-4e43-866a-3e856db1b18e" />

Abbildung 1.5: Cloud-Konzepte sind in einer allgegenwärtigen Cloud überall zu finden

Wenn Sie sich das vorstehende Diagramm ansehen, finden Sie überall Elemente der allgegenwärtigen Cloud. Wir sollten diese Abbildung nicht so betrachten, als handele es sich um separate Elemente. Alles ist miteinander verbunden. Apps auf Smartphones kommunizieren mit Diensten in der Cloud oder in lokalen Hubs, Unternehmen verfügen über mehrere Netzwerke, die verschiedene Computing-Umgebungen miteinander verbinden, und wir haben hier völlig fortschrittlichere Konzepte wie **Web3** außer Acht gelassen.

**Wichtiger Hinweis**

Die IT, wie wir sie heute kennen, befindet sich sowohl im sichtbaren als auch im unsichtbaren Bereich in einem tiefgreifenden Wandel. Mit jedem Schritt, den wir unternehmen, erhöhen wir ihre Komplexität und sehen uns gleichzeitig demografischem Druck und einem Mangel an Fachkräften gegenüber. Früher oder später werden die meisten Unternehmen eine eigene Plattform benötigen. Wenn sie keine haben, werden sie sie als Dienstleistung kaufen.

# **Fokus auf Entwicklererfahrung**

Es ist nicht nachhaltig zu hoffen, dass jeder Entwickler in der Lage sein wird, die extrem breite Landschaft an Tools und Technologien abzudecken, ohne innerhalb weniger Jahre auszubrennen. Daher ist die Qualität der Benutzererfahrung entscheidend für die Akzeptanz und den Erfolg einer Plattform. Eine gut gestaltete Plattform ist intuitiv, leicht zu navigieren und entspricht den Erwartungen und Arbeitsabläufen der Entwickler. Die Verbesserung der Entwicklererfahrung umfasst die Optimierung von Interaktionen, die Minimierung von Reibungspunkten und die Bereitstellung einer visuell, technisch und funktional ansprechenden Umgebung. Dies verbessert nicht nur die Benutzerzufriedenheit, sondern steigert auch die Produktivität und das Engagement. Die Frage ist, wie dies erreicht werden kann.

Wir müssen berücksichtigen, dass jeder Entwickler bei der Gestaltung der Plattform unterschiedliche Präferenzen haben kann. Das beginnt direkt mit dem Problem der Interaktion zwischen der Plattform und dem Benutzer. Entwickler könnten verschiedene Fragen stellen, wie zum Beispiel die folgenden: Müssen wir ein Portal einrichten? Reicht es aus, Code auf einen Git-Dienst zu übertragen? Kann ich über die CLI mit der Plattform interagieren? Das ist schwer zu sagen, aber erfolgreiche Plattformen bieten all diese Interaktionen. Wenn man mit einem API-zentrierten Ansatz beginnt, kann gleichzeitig jeder andere Weg eingeschlagen werden. Eine starke API ist das Herzstück einer guten Plattform. In der Realität bieten die meisten Plattformen immer noch mehrere verschiedene Schnittstellen. Die rasante Entwicklung von Tools zur Vereinheitlichung wird solche Herausforderungen überwinden, und wenn man davon ausgeht, dass sie auf einer grünen Wiese aufgebaut werden, können sie direkt in den Kern integriert werden.

Ein Beispiel für einen solchen Kern ist Kratix. Die unter Apache 2.0 lizenzierte Open-Source-Plattform beschreibt sich selbst als „... Plattform-Framework für den Aufbau komponierbarer IDPs“. In der folgenden Abbildung sehen Sie, wie sich Kratix zwischen allen gängigen Tools, die wir heute verwenden, positioniert und einen einzigen Einstiegspunkt bietet.

<img width="965" height="702" alt="image" src="https://github.com/user-attachments/assets/c48fc1be-6f63-4db0-91c2-c21df6f6c924" />


Abbildung 1.6: Kratix-Übersicht als zentrale Integrationskomponente

Kratix erreicht dies durch das Konzept der Promises, bei denen es sich technisch gesehen um ein YAML-Dokument handelt, das einen Vertrag zwischen der Plattform und den Benutzern definiert. Jedes Team muss einen komplexen Onboarding-Prozess durchlaufen, nicht wegen der Plattform selbst, sondern wegen anderer Abhängigkeiten wie CI/CD, Git-Repositorys und der Verknüpfung aller Komponenten. Mit Kratix Promises können Sie all diese Schritte kapseln oder mehrere Promises zu einer einzigen kombinieren.

Kratix unterstützt nun die Vereinfachung der Plattformgrundlage für die Entwicklererfahrung, doch etwas fehlt noch. Die andere Seite der Medaille ist ein Entwicklerportal. Backstage ist ein Beispiel für eine von Spotify entwickelte Open-Source-Lösung mit Apache-2.0-Lizenz. Kratix und Backstage arbeiten gut zusammen und lassen sich nahtlos integrieren. Backstage ist ein Framework, mit dem GUIs deklarativ erstellt werden können, um Infrastruktur-Tools, Dienste und Dokumentation zu vereinheitlichen und so eine fantastische Entwicklererfahrung zu schaffen. Backstage verfügt über drei Kernfunktionen: die Dienstdefinition, den Backstage-Dienstkatalog und sein Plugin-System, über das Sie weitere Funktionen wie Dokumente aktivieren können.


<img width="1000" height="606" alt="image" src="https://github.com/user-attachments/assets/881114d5-9fe7-49e3-866b-a4102965525a" />

Abbildung 1.7: Die drei Kernfunktionen von Backstage

An dieser Stelle haben wir die Herausforderungen gesehen, die es zu lösen gilt, und einen ersten Blick auf den Lösungsraum geworfen. Das sollte uns ein Gefühl für die aktuellen Möglichkeiten vermitteln, bevor wir uns in den nächsten Kapiteln mit den Details befassen.

# **Attribute von Plattformen**

Eine Plattform muss bestimmte Eigenschaften erfüllen und einige Kernkomponenten bereitstellen, die es uns ermöglichen, dem Endnutzer Funktionen zur Verfügung zu stellen. Bisher haben wir gelernt, wie komplex die Handhabung ist, welche Integrationen erforderlich sind und wie wichtig es ist, sich auf den Endnutzer zu konzentrieren und ihn in den Mittelpunkt zu stellen, um das bestmögliche Erlebnis und Produkt zu schaffen. All dies muss mit einem technischen, prozessualen oder methodischen Ansatz in Form von Eigenschaften einhergehen. Für die Entwicklung einer Idee für Ihre Plattform können wir Ihnen nur empfehlen, sich mit den Eigenschaften auseinanderzusetzen und dann die für Sie beste Lösung zu wählen, anstatt eine Lösung zu nehmen und deren Nützlichkeit für Ihren Fall zu konstruieren.

Einige Attribute, wie z. B. die Reduzierung der kognitiven Belastung, die Plattform als Produkt oder die Entwickler-/Benutzererfahrung, sind gut abgedeckt. Es gibt jedoch noch weitere Aspekte zu berücksichtigen:

- **Flexibilität, Anpassungsfähigkeit und Kombinierbarkeit**: Plattformen sollten Flexibilität in ihrer Nutzung und Integration mit anderen Systemen bieten. Durch die Unterstützung eines modularen und kombinierbaren Designs können Benutzer die Plattform mit optionalen Funktionen an ihre spezifischen Bedürfnisse anpassen und erweitern, ohne von unnötigen Funktionen überfordert zu werden. Dieser Ansatz ermöglicht es der Plattform, eine breite Nutzerbasis mit unterschiedlichen Anforderungen zu bedienen und gleichzeitig Einfachheit und Verwaltbarkeit zu gewährleisten.
- **Sicherheit**: Sicherheit ist ein entscheidendes Merkmal, das in das Design und die Architektur der Plattform integriert sein muss. **„Secure by default”** bedeutet, dass die Plattform von Haus aus die besten Sicherheitspraktiken und -konfigurationen verwendet. Benutzer sollten über robuste Sicherheitsmaßnahmen verfügen, ohne diese umfangreich konfigurieren zu müssen. Dazu gehören Datenverschlüsselung, sichere Zugriffskontrollen und regelmäßige Sicherheitsupdates zum Schutz vor Schwachstellen.
- **Self-Service**: Durch die Aktivierung einer Self-Service-Funktion können Benutzer Aufgaben wie das Einrichten von Umgebungen, das Bereitstellen von Anwendungen und den Zugriff auf Dienste ausführen, ohne auf den IT-Support warten zu müssen. Diese Funktion beschleunigt nicht nur die Arbeitsabläufe, sondern reduziert auch die operative Belastung der Plattformteams. Self-Service-Portale sollten benutzerfreundlich sein und alle notwendigen Tools und Berechtigungen bereitstellen, damit Benutzer ihre Aufgaben selbstständig verwalten können.
- **Dokumentation und Support**: Eine effektive Dokumentation und Einarbeitung sind unerlässlich, um Benutzer zu befähigen und die anfängliche Lernkurve im Zusammenhang mit einer Plattform zu verringern. Eine umfassende, klare und zugängliche Dokumentation stellt sicher, dass Benutzer Probleme selbstständig lösen und die Funktionen der Plattform ohne externe Hilfe verstehen können. Einarbeitungsprozesse sollten neue Benutzer durch die Kernfunktionen und -funktionalitäten der Plattform führen, damit sie sich von Anfang an kompetent und sicher im Umgang mit der Plattform fühlen.

Wie Sie vielleicht bemerkt haben, entsprechen diese Eigenschaften in gewisser Weise dem Aufbau dieses Buches und sind daher unsere Leitsterne auf dem Weg zur Gestaltung und Planung einer Plattform.

Manchmal sind solche Eigenschaften jedoch zu vage, um als Referenz für die Umsetzung zu dienen. Eine Alternative dazu wurde von der internen Entwicklerplattform-Community ( [https://internaldeveloperplatform.org/](https://internaldeveloperplatform.org/"%20\t%20"_blank) ) als die fünf Kernkomponenten eines

IDP \[4\] beschrieben, die wir Ihnen als alternative Quelle empfehlen:

- **Anwendungskonfigurationsmanagement**: Verwalten Sie die Anwendungskonfiguration auf dynamische, skalierbare und zuverlässige Weise.
- **Infrastruktur-Orchestrierung**: Orchestrieren Sie die Infrastruktur dynamisch und intelligent in Abhängigkeit vom Kontext
- **Umgebungsmanagement**: Ermöglichen Sie Entwicklern, bei Bedarf neue und vollständig bereitgestellte Umgebungen zu erstellen
- **Bereitstellungsmanagement**: Implementieren Sie eine Delivery-Pipeline für kontinuierliche Bereitstellung oder sogar kontinuierliche Implementierung
- **Rollenbasierte Zugriffskontrolle**: Verwalten Sie auf skalierbare Weise, wer was tun darf

In „[,„](https://subscription.packtpub.com/book/cloud-and-networking/9781836203599/2) “, gehen wir detailliert auf die organisatorischen und technischen Aspekte sowie die Entwicklung eines umsetzbaren Plans für die Gestaltung Ihrer Plattform als Produkt ein.

Der Fokus auf die Entwicklerperspektive bedeutet, Einfluss auf die Organisation und damit auf die Menschen zu nehmen, die für sie arbeiten. Als Nächstes werden wir uns mit den soziotechnischen Aspekten befassen, die wir bei der Erstellung von Plattformen berücksichtigen müssen.

# **Die soziotechnischen Aspekte verstehen**

Die Entwicklung einer erfolgreichen Plattform erfordert weit mehr als nur technisches Know-how. Sie erfordert ein tiefes Verständnis für die vielfältigen Bedürfnisse der Nutzer, die Förderung und Motivation zur Zusammenarbeit von Anfang an und die Schaffung einer offenen Umgebung, die eine plattformorientierte Kultur begünstigt. Diese soziotechnischen Aspekte der Plattformentwicklung sind entscheidende Perspektiven, die nicht nur die technischen Komponenten einer Plattform, sondern auch die menschlichen Elemente betonen – wie Einzelpersonen und Gruppen mit dem System interagieren und wie es ihre Arbeit und ihr Verhalten beeinflusst. Es ist wichtig, diesen oft unsichtbaren Teil der Plattformentwicklung zu verstehen. Er ist das Bindeglied, das die Relevanz technologisch robuster Systeme definiert und die tief integrierten täglichen Arbeitsabläufe und Verhaltensweisen der Nutzer bestimmt. Die Berücksichtigung dieser fast schon meta-artigen Ebene bedeutet eine Steigerung der Produktivität und eine Förderung der Akzeptanz durch hohe Zufriedenheit. Wir müssen uns bewusst sein, dass jede technische Entscheidung Konsequenzen hat, sowohl in technologischer Hinsicht als auch für den Menschen. Daher ist es wichtig, Plattformen zu entwickeln, die bei ihren Nutzern Anklang finden, eine Kultur der Zusammenarbeit fördern, Innovationen vorantreiben und einfach die tägliche Arbeit erleichtern. Durch die Konzentration auf diese soziotechnischen Aspekte können Plattformingenieure anpassungsfähigere, nachhaltigere und nutzerorientierte Systeme schaffen, die sich in einer sich ständig weiterentwickelnden Cloud-nativen Landschaft bewähren.

Wir müssen uns jedoch bewusst sein, dass wir innerhalb eines soziotechnischen Systems interagieren. Die Herausforderung besteht darin, dass wir in unserem beruflichen, persönlichen und privaten Umfeld ständig Reibungen und Optimierungen erleben. Das berufliche Umfeld repräsentiert das, was in Ihrem beruflichen Kontext geschieht. Das persönliche Umfeld ist eine „Ich“-zentrierte Perspektive, die die Erfahrungen mit allen teilt, die mit Ihnen in Kontakt stehen, sei es im beruflichen oder privaten Bereich. Das private Umfeld schließlich ist das, was andere einschätzen und beobachten können, also das, was hinter verschlossenen Türen geschieht, aber Auswirkungen auf Ihre Meinungen und Perspektiven haben kann. Diese ständigen Veränderungen und Anpassungen finden zwischen der Unternehmens- oder Projektstruktur, den Menschen, der Technologie und ihren Aufgaben statt. Dabei gibt es unterschiedliche Einflüsse und Motivationsfaktoren. Die folgende Darstellung soll diese kontinuierliche Bewegung veranschaulichen. Subsysteme und Systeme selbst haben ihre eigenen Regeln, Aktivitäten und Befugnisse.

<img width="1026" height="645" alt="image" src="https://github.com/user-attachments/assets/fa5671f1-6f14-489f-9b38-dc6ef41d6950" />


Abbildung 1.8: Soziotechnisches System, Trancossi et al.

Wenn wir daran arbeiten, den besten Ansatz für die Implementierung einer Plattform zu finden, versuchen, die Bedürfnisse und Anforderungen herauszufinden, eine Community aufzubauen und für Offenheit zu werben, müssen wir uns bewusst sein, dass all dies von einem soziotechnischen System beeinflusst wird und innerhalb dieses Systems stattfindet. Manchmal werden wir vielleicht blockiert oder in eine andere Richtung gedrängt, oder es fällt uns schwer, Menschen zu motivieren. Das ist der richtige Zeitpunkt, um sich etwas Mühe zu geben, das Subsystem und die externen Systeme zu verstehen, die Sie beeinflussen.

# **Verstehen Sie die Bedürfnisse der Nutzer beim Plattformdesign**

Ein Plattformdesign muss von Natur aus flexibel sein, um einem breiteren Spektrum von Interessengruppen als nur Entwicklern gerecht zu werden. Wir können es nicht oft genug sagen: Die Implementierung einer Plattform ist eine Entscheidung, die alle betrifft. Softwareentwickler, Produktverantwortliche, Geschäftsinteressenten und operative Teams haben alle einzigartige Anforderungen und Herausforderungen, die sie von der Plattform erwarten. Entwickler suchen möglicherweise nach einfachen Tools für die Bereitstellung und das Testen, während Endbenutzer intuitive Schnittstellen und nahtlose Interaktion benötigen. Geschäftliche Stakeholder hingegen konzentrieren sich wahrscheinlich in erster Linie auf **den Return on Investment** (**ROI**), Sicherheit, Governance, Compliance und Skalierbarkeit. Als Plattformingenieur und -architekt liegt es in Ihrer Verantwortung, diese Anforderungen zu identifizieren und sie während des gesamten Lebenszyklus der Plattform auszugleichen.

Der erste Schritt bei der benutzerorientierten Plattformgestaltung besteht also darin, die verschiedenen Stakeholder-Gruppen, die mit der Plattform interagieren, genau zu identifizieren und zu verstehen. In der Anfangsphase können Sie Interviews und Umfragen durchführen, um sich ein klares Bild zu verschaffen. Betrachten Sie das Ganze aus einer 360-Grad-Perspektive und bedenken Sie, dass es besser ist, eine Person zu viel zu befragen als insgesamt zu wenige Personen. In späteren Phasen ist es hilfreich, sich stärker an Daten zu orientieren und Nutzungsdaten für die verschiedenen Komponenten der Plattform heranzuziehen. Serviceanfragen und offene Probleme und Fragen beim Helpdesk sind ein guter Indikator für die Benutzerfreundlichkeit der Plattform. An diesem Punkt wird es wichtig, die Plattform als Produkt zu betrachten und eine Produktmentalität zu entwickeln, da Sie das Feedback der Nutzer von den frühesten Entwicklungsstadien an und während des gesamten Produktlebenszyklus berücksichtigen müssen, um sicherzustellen, dass die Plattform zugänglich, intuitiv und effizient ist. Ein falsches Gefühl der Eitelkeit wird Ihre Bemühungen definitiv in die falsche Richtung lenken. Es ist hilfreich, Prinzipien wie Transparenz oder Einfachheit zu definieren, die Sie durch den Entwicklungs- und Entscheidungsprozess führen. Im nächsten Kapitel werden wir dieses Thema ausführlich behandeln.

Um relevant und effizient zu bleiben, müssen sich Plattformen weiterentwickeln. Denken Sie daran, dass Projekte sterben, wenn sie die Deadline erreichen; Produkte entwickeln sich mit jeder Veröffentlichung und jedem Nutzer-Feedback weiter. Die Einrichtung einer robusten Release-Dokumentation und von Feedback-Schleifen ist für diesen iterativen Verbesserungsprozess von entscheidender Bedeutung. Welcher Kanal für Ihr Unternehmen und Ihre Nutzer am besten geeignet ist, müssen Sie selbst entscheiden, aber es gibt viele Möglichkeiten, die über Umfragen und Interviews hinausgehen. Beispiele hierfür sind direkte Interaktionen über Kommunikationswerkzeuge, Benutzerforen, Support-Lösungen, sogar interne soziale Medien des Unternehmens oder in extremen Fällen eingebettete Feedback-Mechanismen innerhalb der Plattform selbst. Regelmäßige Updates und Upgrades, die sich an den tatsächlichen Benutzererfahrungen und Herausforderungen orientieren, stellen sicher, dass die Plattform den Benutzeranforderungen und Industriestandards entspricht und fördern so die Loyalität und das nachhaltige Engagement.

# **Förderung und Verbesserung der Zusammenarbeit**

Das Problem transparenter, offener Feedback-Schleifen ist, dass sie eine gut funktionierende Zusammenarbeit erfordern. Andernfalls wirken sie künstlich und in gewisser Weise wie der traditionelle Ansatz des Requirements Engineering. Als Plattformentwickler müssen wir diese klassischen Methoden in einen persönlicheren und einladenderen Ansatz verpacken. Effektive Zusammenarbeit ist der Grundstein jeder erfolgreichen Plattform. Durch die Integration der richtigen Kommunikationswerkzeuge, die Schaffung einer fantastischen Benutzererfahrung durch Anpassung und die Förderung funktionsübergreifender Teamarbeit können Plattformen mehr als nur Technologielösungen sein – sie können zu einem Ort der Zusammenarbeit zwischen verschiedenen Entwicklungsteams und zu einem Motor für Organisationen und Innovation werden.

Um die Zusammenarbeit zu fördern, müssen Ihr Team und die Plattform offen und einladend sein. Reduzieren Sie alle Hindernisse für die Einarbeitung eines neuen Produktteams und bieten Sie ihnen unterschiedlich gestaltete Einstiegsmöglichkeiten. Es muss klar sein, wie und wo Ihr Team bei Fragen erreichbar ist. Dies ist in der Anfangsphase wichtig, wenn ein neues Endbenutzerteam zu Ihrer Plattform stößt. Beseitigen Sie jede implizite Erwartung, dass klar ist, wo und wie Ihr Team zu finden ist, da dies in der Regel nicht der Fall ist, insbesondere in größeren Organisationen. Dazu müssen Sie und Ihr Team neben internen öffentlichen Dokumentationen und Landing Pages auch zu Fürsprechern der Plattform werden. Sie müssen hinausgehen, mit anderen Teams zusammenarbeiten, ihnen zuhören, wenn sie über ihre Herausforderungen sprechen, und ihnen Ihre Lösungen zeigen. Wenn möglich, müssen Sie Ihre Organisation über neue Funktionen und Anwendungsfälle informieren und ihnen immer wieder zeigen, wie einfach der Einstieg ist.

# **Eine offene, plattformorientierte Kultur pflegen**

Die Förderung einer offenen und plattformorientierten Kultur ist vielleicht der schwierigste Teil. Dazu ist neben Ihrem Engagement auch die Zustimmung anderer Budgetverantwortlicher in Ihrem Unternehmen erforderlich. Die Förderung basiert auf Schulungen, Motivation (die durch Anreize gefördert werden kann) und der Einbindung Ihrer Community oder Benutzergruppe. All diese Aktivitäten gehen über Ihre Budgetverantwortung hinaus.

Schulungen mögen wie eine teure, zeitaufwändige Aktivität erscheinen, die schnell veraltet ist, aber es gibt kaum einen besseren Weg, um in engen und wirklich offenen Kontakt mit Ihren Endnutzern zu treten. Umfassende Schulungsprogramme kombinieren verschiedene Ansätze und Quellen:

- Persönliche Workshops, die sich auf verschiedene Komponenten Ihrer Plattform konzentrieren
- Praktische Sitzungen für die Einarbeitung und ein gutes erstes Projekt oder eine spezifische Integration, die weniger kompliziert ist
- Do-it-yourself-Tutorials
- Online-/Video-Tutorials für allgemeine Themen
- Online-/Video-Tutorials für Ihre spezifischen Anforderungen

Wie Sie sehen, müssen Sie nicht alles selbst machen. Kaufen Sie Kurse und Schulungen für allgemeines Wissen und bieten Sie eigene an, um dieses Wissen zu vertiefen und die Besonderheiten Ihrer Plattform zu vermitteln. Erwägen Sie außerdem die Erstellung eines Repositorys und eines Wikis mit Ressourcen wie FAQs, Leitfäden für bewährte Verfahren, Tipps zur Fehlerbehebung, Code-Schnipsel und Beispiele, Empfehlungen für Anwendungsfälle von „ “ und Nachbesprechungen. Dies kann dazu beitragen, dass sich die Benutzer besser informiert fühlen und die Lernkurve für die Einführung neuer Technologien verkürzt wird.

Um die Motivation aufrechtzuerhalten, können das Training und die Nutzung der Plattform mit Anreizen kombiniert werden. Es gibt verschiedene Motivationsstrategien wie Gamification, Anerkennungsprogramme und leistungsbasierte Belohnungen, die zur aktiven Nutzung der Plattform anregen können. In großen Organisationen haben wir sogar interne Badge-Programme und Cloud-Führerscheine gesehen, die immer mit offiziellen Zertifizierungen kombiniert werden können. Gleichzeitig muss man jedoch darauf achten, keine künstlich hohen Barrieren zu schaffen. Das wäre kontraproduktiv. Im Idealfall sollten Ihre Anreize neue Nutzer motivieren und Experten herausfordern. Sie können beispielsweise in bestehende Leistungskennzahlen integriert werden, um eine Kultur zu stärken, die kontinuierliche Verbesserung und den effektiven Einsatz von Technologie wertschätzt. Auf diese Weise können Sie auch Unternehmensziele durch definierte KPIs wie Kostensenkung, Leistungsverbesserung und Stabilität beeinflussen.

Letztendlich müssen wir all diese Ansätze kombinieren. Der beste Weg, dies zu erreichen, ist die Schaffung einer Community. Wir können eine solche Community durch Benutzergruppen, regelmäßige Treffen und Foren aufbauen, die es den Benutzern ermöglichen, Wissen auszutauschen, Probleme gemeinsam zu lösen und sich gegenseitig zu unterstützen. Um eine Community zu fördern, empfehlen wir Ihnen dringend, sich die Unterstützung Ihrer Führungskräfte und Ihres Marketingteams zu sichern. Es mag einfach klingen, Menschen zusammenzubringen, und es mag so aussehen, als wäre damit alles geregelt. In Wahrheit ist es jedoch eine ganze Disziplin, die es erfordert, Strategien zur Einbindung der Community-Mitglieder zu erforschen, produktive Diskussionen zu ermöglichen und ein Gefühl der Zugehörigkeit und Eigenverantwortung unter den Nutzern zu fördern.

Ohne Menschen und ohne Respekt für ihre Bedürfnisse wird Ihre Plattform entweder schnell aufgegeben oder gar nicht erst Fuß fassen. Strategische Initiativen mit Schwerpunkt auf Schulungen, Anreizen und einer florierenden Community können eine offene, plattformorientierte Kultur beschleunigen. Um die Effektivität einer Plattform zu steigern, müssen Sie über die reine technische Bereitstellung hinausgehen. Dieser ganzheitliche Ansatz stellt sicher, dass die Plattform zu einem grundlegenden Bestandteil des Unternehmens wird und Innovation und Effizienz auf allen Ebenen und bei allen Beteiligten fördert, von Entwicklern und dem Betrieb bis hin zu Geschäfts- und Prozessverantwortlichen.

**Zusammenfassung**

In diesem ersten Kapitel haben wir die Rolle von Plattformen in der modernen Softwareentwicklung, insbesondere in Cloud-nativen Umgebungen, untersucht. Wir haben festgestellt, dass Plattformen nicht nur Infrastrukturkomponenten sind, sondern elementare Produkte, die eine strategische Planung und kontinuierliche Weiterentwicklung erfordern, um mit den sich wandelnden technologischen und geschäftlichen Anforderungen Schritt zu halten.

Sie haben die Grundlagen von Plattformen kennengelernt und erkennen nun den umfassenden Charakter von Plattformen, die Softwareentwicklung, Betrieb und Bereitstellung in einer einheitlichen Umgebung vereinen. Darauf aufbauend haben Sie gesehen, warum die Plattform als Produkt eine Schlüsselkomponente ist. Sie erfordert kontinuierliche Weiterentwicklung, Nutzerinteraktion und Reaktionsfähigkeit auf Feedback, um ihre Relevanz und ihren Wert zu erhalten.

Anschließend haben wir die Bedeutung der Vereinfachung der Interaktionen der Entwickler mit der Plattform diskutiert, wodurch die kognitive Belastung und die Komplexität des Betriebs erheblich reduziert werden. Zwei kurze Tool-Beispiele sollen Ihre Neugier und Ihr Interesse an den folgenden Kapiteln wecken, Ihnen aber auch zeigen, dass all diese Komplexitäten und Herausforderungen lösbar sind.

Im letzten Teil haben wir etwas über die soziotechnischen Aspekte und die offensichtliche Relevanz des Faktors Mensch gelernt. Plattformen müssen sowohl technische Fähigkeiten als auch menschliche Faktoren berücksichtigen, um sicherzustellen, dass sie die Arbeitsabläufe, die Zusammenarbeit und die Produktivität ihrer Nutzer unterstützen. Dazu haben wir die drei Säulen vorgestellt, auf denen aufgebaut werden muss: Verständnis der Nutzerbedürfnisse vor dem Entwurf einer Lösung, Förderung und Verbesserung der Zusammenarbeit sowie Pflege einer offenen, plattformorientierten Kultur.

Diese Lektionen sollten Sie motivieren, sich eingehender mit Plattformarchitekturen und deren Aufbau zu befassen, da sie die betriebliche Effizienz steigern und Innovation und Agilität innerhalb von Organisationen fördern. Durch die Verinnerlichung dieser Konzepte können Plattformingenieure und -architekten Lösungen entwerfen, die robust, benutzerorientiert und anpassungsfähig sind und gleichzeitig einen echten Mehrwert für ihre Organisationen bieten.

Nachdem wir uns nun mit den menschlichen Aspekten befasst haben, werden wir im nächsten Kapitel entdecken, wie man die Prinzipien und den Zweck einer Plattform definiert, wie man die Plattformarchitektur definiert und wie man den Erfolg der Plattform misst. weiter [Chap2](https://github.com/aboudou123/Platform-Engineering-for-Architects/blob/main/DE/Chap2/Platform%20Engineering_2%20de.md)




Weiterführende Literatur

- \[1\] CNCF-Jahresumfrage 2023: https://www.cncf.io/reports/cncf-annual-survey-2023
- \[2\] Fallstudien zum Erfolg von IDP:
    - Spotify: https://engineering.atspotify.com/2024/04/supercharged-developer-portals/
    - Expedia: https://backstage.io/blog/2023/08/17/expedia-proof-of-value-metrics-2/
    - Toyota: https://backstage.spotify.com/discover/blog/adopter-spotlight-toyota/
- \[3\] Gartner 2023 Hype Cycle für neue Technologien: https://www.gartner.com/en/articles/what-s-new-in-the-2023-gartner-hype-cycle-for-emerging-technologies
- \[4\] Die 5 Kernkomponenten einer internen Entwicklerplattform (IDP): https://internaldeveloperplatform.org/core-components/
