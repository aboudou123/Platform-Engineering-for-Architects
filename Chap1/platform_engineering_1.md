# Ingénierie des plateformes et l’art de concevoir des plateformes

## Ingénierie des plateformes et l’art de concevoir des plateformes

Dans ce premier chapitre, nous verrons comment identifier le moment où notre organisation se trouve dans le bon état pour planifier une plateforme. Pour cela, nous clarifierons pourquoi les plateformes sont devenues un sujet aussi pertinent, comment une approche orientée produit s’y intègre, et quels sont les points de contrôle permettant de déterminer si nous sommes prêts ou non pour une plateforme. Nous examinerons les différences entre plateformes ainsi que les types de plateformes les plus couramment développés.

Ensuite, nous approfondirons les trois éléments fondamentaux d’une plateforme : le cloud omniprésent, l’expérience développeur et les principaux attributs d’une plateforme. Globalement, nous identifierons des éléments récurrents de l’ingénierie cloud-native. Cela nous amènera à nous poser la question de savoir si nous avons réellement besoin d’une couche d’abstraction supplémentaire. Nous examinerons également si une plateforme peut nous aider à surmonter le problème d’une charge cognitive élevée causée par des systèmes et des processus de développement excessivement complexes, ou si elle ne fera qu’ajouter une couche supplémentaire. Nous réfléchirons à certaines de ces couches afin de trouver notre propre réponse.

Enfin, nous aborderons des aspects qui dépassent la technologie et l’implémentation des plateformes. Il est essentiel de comprendre les aspects sociotechniques et de placer l’humain — nos véritables parties prenantes — au centre. Cela nous permet de définir un meilleur produit plateforme et de trouver des approches favorisant une collaboration étroite.

Dans ce chapitre, nous aborderons les principaux sujets suivants :

- La demande de plateformes en tant que produit
- La mise en œuvre de solutions orientées développeur et produit
- Avons-nous besoin d’une couche d’abstraction supplémentaire ?
- Les aspects sociotechniques

## La demande de plateformes en tant que produit

Dans l’environnement cloud-native, rares sont les sujets qui ont suscité autant de mythes ces dernières années que le terme « plateforme » et le rôle associé d’ingénieur plateforme. Comme lors de l’introduction des premiers pipelines CI/CD exploitables, cette ruée vers l’or a conduit à une adoption rapide, souvent sans réelle réflexion. À présent que nous sommes entrés dans la vallée de la connaissance, nous pouvons nous pencher en profondeur sur la question suivante : avez-vous besoin d’une plateforme et, si oui, comment la concevoir et l’implémenter afin qu’elle soit pérenne ?

Pour répondre à cette question, nous devons d’abord examiner ce qui constitue une plateforme. Une plateforme est la combinaison de différentes capacités nécessaires pour maîtriser les environnements traditionnels et cloud-native, de manière à soutenir l’utilisateur final dans le développement, la livraison et l’exploitation d’une application. Les plateformes peuvent servir de catalyseur pour transformer des infrastructures non cloud-native en ressources de valeur. Toutefois, la plupart des plateformes de calcul actuelles fournissent déjà une forme d’API permettant d’automatiser le déploiement et l’instrumentation des ressources disponibles, et de poser les bases d’une plateforme. Les plateformes assurent une cohérence sur tous types de ressources pour les utilisateurs finaux et donnent accès à leurs capacités via des API en libre-service, des modèles, des CLI ou d’autres solutions. L’exemple suivant met également en évidence qu’une plateforme est composée de nombreux composants.

*Figure 1.1 : Exemple de plateforme / IDP*

Nous constatons généralement que le sujet des plateformes apparaît dans le contexte du cloud-native. Pourquoi cela ? Les technologies cloud-native permettent aux organisations de concevoir et d’exécuter des applications évolutives dans des clouds publics, privés et hybrides. Cette approche est illustrée par des fonctionnalités telles que les conteneurs, l’approvisionnement standardisé de services, l’infrastructure immuable et les API déclaratives. Ces fonctionnalités donnent naissance à des systèmes faiblement couplés, résilients, gérables et observables. Elles permettent aux développeurs d’apporter des changements fréquents avec un effort minimal. En résumé, une plateforme est un catalyseur du cloud-native et s’appuie sur ses outils pour l’opérationnaliser.

## Les entreprises et les développeurs bénéficient des plateformes de manière équivalente

L’expérience d’un ingénieur logiciel sur une plateforme cloud-native diffère du développement directement orienté vers un fournisseur de cloud. Concevoir des systèmes en se concentrant sur un seul fournisseur de services cloud (CSP) vous lie à la logique de cet écosystème fermé. Un effet similaire peut se produire avec les plateformes cloud-native, souvent centrées sur Kubernetes et reposant sur une forte unification des intégrations via l’API Kubernetes. Cependant, la différence majeure est que les plateformes cloud-native offrent la même expérience sans que l’infrastructure sous-jacente ne soit perceptible. Comme la plupart des entreprises utilisent au moins deux à trois fournisseurs de cloud ou assimilés et rencontrent déjà des difficultés à s’y adapter, une plateforme cloud-native constitue un véritable changement de paradigme. Développer des logiciels sur une plateforme cloud-native modifie l’état d’esprit et l’architecture. Sans adopter cet état d’esprit, le risque d’échec est élevé.

Toutefois, une plateforme ne se limite pas à la gestion unifiée de l’infrastructure. Les plateformes sont conçues dans un but précis. La définition courante des bénéficiaires d’une plateforme et des parties prenantes des ingénieurs plateforme indique souvent qu’il s’agit exclusivement des développeurs. Cette vision est incomplète, car l’ensemble de l’organisation, les équipes opérationnelles et d’autres équipes spécialisées tirent également profit d’une plateforme. Une plateforme offre aux ingénieurs logiciels un point d’accès simple pour concevoir, tester, déployer, livrer et exploiter leurs logiciels. Elle fournit une visibilité approfondie sur l’utilisation et permet aux responsables et administrateurs de maintenir l’infrastructure, la plateforme et les intégrations en toute confiance. En termes métier, une plateforme peut accélérer la mise sur le marché, offrir davantage de flexibilité pour faire évoluer ses composants, tout en maintenant un haut niveau de fiabilité et de robustesse.

Qu’est-ce que cela signifie pour une entreprise ? Face à la pénurie de professionnels de l’IT, au rythme rapide des évolutions technologiques et à la surcharge des équipes de formation sur les technologies et fournisseurs cloud, une plateforme introduit des points de rupture pertinents en matière de compétences. Ces points de rupture sont nécessaires pour mettre fin à la tendance consistant à regrouper plusieurs disciplines dans un seul rôle, comme celui de DevOps. Par ailleurs, les ingénieurs plateforme utilisant des méthodologies DevOps ne sont pas des DevOps. Il est essentiel de protéger ce rôle afin d’éviter de répéter les erreurs commises avec le rôle DevOps et de conserver une définition claire. Les ingénieurs plateforme intègrent les capacités fournies par des experts, en simplifient l’usage pour les développeurs via la plateforme et permettent le libre-service. Aucun développeur n’a besoin de devenir expert en sécurité, observabilité, configuration et automatisation de l’infrastructure, et autres domaines. Cela contraste avec la vision courante du DevOps, qui doit maîtriser tout ce qui est nécessaire au sein de son silo pour maintenir son application en fonctionnement. Les DevOps resteront nécessaires à l’avenir pour la gestion avancée des applications, mais leur quotidien doit également être simplifié.

La plateforme fournit une couche d’intégration pour les capacités ascendantes nécessitant une expertise spécialisée — comme la sécurité, les bases de données ou le déploiement de machines virtuelles ou de serveurs bare metal — ainsi que pour l’utilisation descendante par les développeurs et les DevOps. Comme illustré dans la figure suivante, l’équipe d’ingénierie des plateformes est responsable de la fourniture de cette couche.

*Figure 1.2 : Capacités et responsabilités dans une organisation pilotée par la plateforme*

Cela implique bien sûr la formation d’une nouvelle équipe d’experts. Toutefois, une équipe relativement réduite d’ingénieurs plateforme peut généralement concevoir et exploiter des environnements très vastes. Une plateforme réduit idéalement la charge cognitive des autres équipes de l’entreprise et leur permet de se recentrer sur leur valeur métier en simplifiant les mécanismes entourant le processus de développement. Elle contribue ainsi à réduire le stress et à améliorer la transparence. Des entreprises du monde entier partagent régulièrement leur expérience des plateformes et des équipes associées, et le constat est souvent le même : elles ont résolu des problèmes auparavant insolubles ou considérablement amélioré la qualité de leurs produits et services.

Ces plateformes sont souvent appelées plateformes internes pour développeurs (Internal Developer Platforms, ou IDP), car elles sont généralement conçues pour les équipes de développement internes d’une entreprise. Tout au long de cet ouvrage, nous utiliserons de manière interchangeable les termes plateforme, IDP, produit plateforme et plateforme cloud-native. Nous mettrons toutefois davantage l’accent sur certains aspects :

- **Plateforme** : terme générique désignant la couche technologique transverse permettant l’unification des services pour les développeurs.
- **IDP** : met l’accent sur le développeur, le cycle de vie du développement logiciel (SDLC) et les outils nécessaires à la création de logiciels.
- **Produit plateforme ou plateforme en tant que produit** : souligne l’existence d’une équipe dédiée responsable de l’évolutivité, de l’engagement à long terme et de l’adoption d’un état d’esprit spécifique.
- **Plateforme cloud-native** : met l’accent sur l’abstraction et l’activation de l’utilisation d’API et d’intégrations standardisées.

Cette distinction peut sembler fine, mais le terme « plateforme » est souvent source de confusion. Une plateforme cloud est-elle aussi une plateforme ? Un logiciel en tant que service (SaaS) peut-il être considéré comme une plateforme ? Faire référence à une plateforme cloud-native ou à une IDP permet d’orienter correctement la compréhension. Selon le niveau de maturité de votre organisation, il est donc essentiel de clarifier ces termes et d’établir une compréhension, un langage et un socle de connaissances communs.

## Études de cas et réussites des plateformes

Pour illustrer l’impact positif qu’une plateforme peut avoir, examinons trois entreprises très différentes et les résultats obtenus grâce à l’utilisation d’IDP. Tous ces cas se concentrent principalement sur Backstage comme portail développeur et point d’entrée de l’IDP.

Spotify, inventeur de Backstage et pionnier du mouvement IDP, affirme que pour ses utilisateurs internes de Backstage :

- ils sont 2,3 fois plus actifs sur GitHub ;
- ils effectuent deux fois plus de modifications de code ;
- ils réalisent deux fois plus de déploiements ;
- le temps d’intégration des nouveaux développeurs est passé de 60 jours à 20 jours.

Le groupe Expedia rapporte des chiffres différents :

- la création d’un nouveau composant ou d’une nouvelle application prend en moyenne quatre minutes ;
- plus de 4 000 utilisateurs utilisent l’IDP au moins 20 minutes par jour ;
- la documentation technique est consultée plus de 50 000 fois par mois ;
- un peu plus de 15 % des outils internes pour développeurs sont intégrés à Backstage, réduisant déjà les changements de contexte.

Enfin, examinons le cas de Toyota :

- les projets livrent désormais des artefacts de manière hebdomadaire au lieu de mensuelle ;
- 8 à 12 semaines d’efforts indirects sont économisées par équipe, représentant plus de 5 millions de dollars de coûts réduits ou de temps et budget réalloués à la création de valeur ;
- la standardisation des modèles de déploiement réduit les échecs et accélère les mises en production.

Ces chiffres sont intéressants lorsqu’on les replace dans le contexte d’une entreprise née du numérique, d’un groupe de technologies du voyage et de l’un des plus grands constructeurs automobiles. Chacune de ces entreprises démontre un impact positif clair.

## Projets versus produits

Sur le plan organisationnel, l’introduction de nouvelles solutions se fait généralement sous forme de projets. À un moment donné, quelqu’un décide donc d’investir dans la création de sa propre plateforme. Cette approche se heurte à un problème fondamental : l’échéance. Les projets doivent atteindre un objectif dans un cadre de temps et de budget défini. Lorsque le projet arrive à court de temps ou de budget, il se concentre sur son exploitation et sa maintenance. Ces deux phases du cycle de vie sont traitées séparément, créant une période de montée en puissance puis de déclin. Durant la phase d’implémentation, les investissements, la communication et l’enthousiasme sont importants. Une fois l’échéance atteinte, le projet devient un objet inerte nécessitant de la maintenance. DevOps n’a pas changé ce comportement ; il lui a simplement donné de nouveaux noms, rôles et processus. En fin de compte, le budget, les ressources humaines et l’attention se déplacent vers le projet suivant, tandis qu’une fraction seulement du budget initial subsiste. Cela est frustrant pour les ingénieurs ayant travaillé dur sur l’implémentation et, à terme, pour l’organisation, lorsque les coûts de maintenance augmentent. Les personnes ayant construit la solution peuvent quitter l’entreprise ou rejoindre d’autres projets. Cette vision à court terme a lentement détruit de nombreux projets prometteurs et l’esprit d’équipe. Plus important encore, elle révèle que la valeur métier de la solution n’est pas clairement définie. Lorsqu’une implémentation, telle qu’une plateforme, apporte une valeur explicite, il ne devrait pas y avoir de raison d’en détourner l’attention.

Bien que la réalisation de nombreuses implémentations sous forme de projets soit valable, cette approche est fatale pour les plateformes. Les implémentations classiques sont finies une fois terminées. Une plateforme, en revanche, est en constante évolution, toujours mise à jour et enrichie de nouvelles fonctionnalités. En travaillant avec des logiciels open source et des fournisseurs cloud, on constate rapidement la vitesse de leurs cycles de développement : fonctionnalités, correctifs et mises à jour de sécurité sont publiés en continu. Cela représente un défi majeur pour les grandes organisations habituées à des cycles de publication beaucoup plus lents. L’avantage de suivre ce rythme est de pouvoir bénéficier fréquemment de nouvelles capacités. C’est un moteur d’innovation qui permet d’aborder les systèmes différemment et de résoudre des problèmes parfois encore insoupçonnés.

C’est ce que l’on appelle une approche orientée produit, qui s’adapte naturellement aux exigences de son environnement.

## La plateforme en tant que produit

Les plateformes conçues comme des produits sont centrées sur l’utilisateur. Elles écoutent activement la demande et mènent des recherches pour améliorer continuellement leurs services. Un produit connaît également sa valeur. À l’image d’une application mobile, il s’appuie sur cette valeur pour financer son évolution et ses nouvelles fonctionnalités. Il n’y a ni échéance ni mise hors service programmée : l’objectif est de s’améliorer à chaque version. Pour l’organisation, cela signifie disposer d’une équipe experte travaillant en continu sur un levier central de création de valeur.

Concevoir et développer une plateforme comme un produit dépasse largement l’ingénierie pure. Cela pose des défis organisationnels qu’il convient d’anticiper. Il est nécessaire de démontrer les bénéfices de la plateforme et de montrer qu’elle couvre ses propres coûts. Cet état d’esprit doit être partagé par le product owner et les ingénieurs plateforme. Il ne s’agit pas de devenir des commerciaux, mais de pouvoir communiquer clairement la raison d’être de la plateforme et, surtout, d’en faire un produit sans date de fin.

On distingue aujourd’hui trois types principaux de plateformes en tant que produit :

- **IDP** :
  - offrent une expérience de premier ordre aux ingénieurs logiciels ;
  - permettent aux équipes de développement et d’exploitation une prise en charge de bout en bout et une visibilité complète ;
  - apportent gouvernance, conformité et sécurité ;
  - instaurent le libre-service et simplifient le déploiement.

- **Plateformes de data science et de machine learning** :
  - similaires aux IDP et souvent issues de leur évolution ;
  - exploitent leur scalabilité pour analyser et traiter les données de manière rentable ;
  - simplifient des implémentations complexes et les rendent accessibles ;
  - fournissent un accès direct et sécurisé aux sources de données pertinentes.

- **Plateformes low-code / métiers** :
  - tendance forte visant à proposer des solutions permettant de développer de nouvelles fonctionnalités avec peu ou pas de code ;
  - leur présence va s’accentuer dans les années à venir.

Dans cet ouvrage, nous nous concentrerons sur une approche orientée produit pour l’architecture des IDP.

## Avez-vous besoin d’une plateforme ?

Comme pour tout environnement complexe, la première question à se poser est la suivante : avons-nous réellement besoin d’une plateforme ? Savons-nous à quoi elle servira ?

Bien que les plateformes offrent de nombreux avantages, elles ne constituent pas toujours la réponse appropriée. Les signes indiquant que vous n’êtes pas encore prêt sont les suivants :

- vous n’avez que des applications monolithiques ;
- vous ne disposez pas d’une équipe de développement interne ;
- vos équipes DevOps, systèmes ou infrastructure sont surchargées ou cloisonnées ;
- vos applications sont très simples et peuvent s’exécuter partout ;
- vous avez des difficultés à dégager un budget pour la formation ;
- vous utilisez principalement des solutions commerciales clés en main.

À l’inverse, une IDP est pertinente lorsque :

- vous avez des exigences sur plusieurs environnements d’infrastructure ou adoptez une stratégie multicloud ;
- vous avez besoin d’un contrôle avancé (sécurité, conformité, visibilité approfondie) ;
- vos équipes de développement sont surchargées de tâches sans valeur ajoutée ;
- vos équipes DevOps ou infrastructure sont curieuses et ont déjà amorcé des démarches proches d’une plateforme ;
- vos applications nécessitent une orchestration liée à une architecture microservices ;
- vous souhaitez optimiser vos coûts, votre transparence, votre qualité ou votre sécurité IT.

Avant de définir un produit plateforme, il est essentiel de répondre à l’ensemble de ces points. Une simple demande isolée ou une tendance entendue lors d’une conférence ne constitue pas une base suffisante. L’introduction d’une plateforme est un parcours qui peut rapidement devenir central pour l’entreprise. Même sous pression, il est indispensable de conserver un objectif et une direction clairs.

Nous aborderons maintenant la question de la nécessité d’une couche d’abstraction supplémentaire.

## Avons-nous besoin d’une couche d’abstraction supplémentaire ?

Récapitulons brièvement. Une plateforme englobe votre infrastructure existante et y ajoute une couche d’abstraction. Elle l’enrichit de capacités supplémentaires afin que les équipes de développement puissent l’utiliser de manière automatisée et en libre-service.

D’un point de vue technique, cela représente une nouvelle couche d’abstraction. En partant du bas, on trouve le bare metal, puis l’hyperviseur, ensuite les fournisseurs cloud. Certains ajoutent les conteneurs, Kubernetes ou le serverless, et enfin la plateforme. Cela représente au moins quatre couches, reliées par des scripts, de l’Infrastructure as Code (IaC), des bibliothèques cloud et de l’automatisation. La question est donc légitime : avons-nous vraiment besoin de cette couche supplémentaire ?

### Désencombrer les couches d’abstraction

Il n’existe pas de réponse simple. Examiner la finalité de chaque couche peut toutefois aider à se forger une opinion. Les hyperviseurs ont été introduits pour simplifier la fourniture d’hôtes et optimiser l’utilisation des serveurs. Aujourd’hui, ils remplissent toujours ce rôle, bien qu’ils puissent être remplacés par Kubernetes et les runtimes de conteneurs. L’argument principal contre ce remplacement est l’isolation et la sécurité supérieures des machines virtuelles. Des solutions comme les conteneurs Kata offrent toutefois une isolation solide. À l’avenir, WebAssembly pourrait constituer une réponse partielle à ces défis.

Les fournisseurs IaaS et les clouds publics ajoutent des capacités de stockage et de réseau définies par logiciel, réduisant la complexité de la gestion des centres de données. Ils proposent également des services courants tels que bases de données, équilibrage de charge, gestion des utilisateurs ou files de messages. Cette évolution a accéléré l’innovation, mais elle a également complexifié les environnements plus rapidement que les organisations ne peuvent s’y adapter. La plupart des entreprises utilisent aujourd’hui plusieurs fournisseurs IaaS et SaaS, ce qui accroît considérablement la complexité.

Pour maîtriser cette échelle, l’IaC et les kits de développement cloud sont devenus essentiels. Toutefois, certaines interprétations erronées des pratiques DevOps ont conduit à attendre des développeurs qu’ils configurent et maintiennent eux-mêmes l’infrastructure.

Les systèmes basés sur les conteneurs, Kubernetes ou le serverless offrent de nombreuses options de déploiement et d’exécution. Bien que cela ajoute des couches supplémentaires, cette évolution est logique pour éviter les méthodes traditionnelles de mise en production.

L’ensemble peut être représenté comme un cube multidimensionnel de complexité, où chaque couche s’additionne pour former l’environnement IT.

*Figure 1.3 : La complexité multidimensionnelle des abstractions informatiques*

Cette représentation est simplifiée, mais elle montre clairement que si une plateforme est nécessaire, elle doit encapsuler cette construction afin d’en maîtriser la complexité.

## La charge cognitive des ingénieurs logiciels et des professionnels IT

Pour gérer toutes ces couches, il faut maîtriser de nombreux outils et processus, ce qui rend difficile la concentration sur la création de valeur. Cette surcharge mentale est appelée charge cognitive. Réduire cette charge améliore la satisfaction, l’efficacité et la fiabilité. Les technologies s’empilent au fil du temps, obligeant à maintenir des systèmes existants tout en adoptant de nouveaux paradigmes.

Chaque organisation est différente : certaines sont figées dans des modèles anciens, d’autres s’adaptent en permanence. Il vous appartient donc de définir une vision et une stratégie claires pour votre plateforme.

Dans la section suivante, nous nous concentrerons sur la mise en œuvre de solutions orientées développeur et produit.

## Mise en œuvre de solutions orientées développeur et produit

Au cours des prochaines années, le cloud computing continuera d’évoluer, et les plateformes joueront un rôle clé. Le cloud deviendra omniprésent, tandis que l’expérience développeur devra être optimisée pour permettre la création de valeur. L’association de ces éléments est essentielle pour maintenir le rythme du marché.

### Le cloud omniprésent

Le cloud omniprésent regroupe un ensemble de capacités allant des centres de données privés à l’edge computing, en passant par l’IoT et les systèmes connectés. Il est également connu sous les termes d’informatique ubiquitaire ou ambiante.

Selon Gartner, six technologies façonneront ce cloud omniprésent :

- FinOps augmentés ;
- environnements de développement cloud (CDE) ;
- durabilité du cloud ;
- cloud-native ;
- extension du cloud vers l’edge ;
- WebAssembly.

Ces technologies sont déjà en cours d’adoption et nécessitent des plateformes pour en tirer pleinement parti.

### Se concentrer sur l’expérience développeur

Il n’est pas viable d’attendre des développeurs qu’ils maîtrisent l’ensemble des outils sans s’épuiser. Une plateforme bien conçue doit être intuitive, fluide et alignée sur les attentes des utilisateurs. Une approche centrée sur l’API est essentielle, car une API robuste constitue le cœur d’une bonne plateforme.

Des outils comme Kratix et Backstage illustrent cette approche. Kratix agit comme un cadre de plateforme composable, tandis que Backstage fournit un portail développeur unifié.

### Attributs des plateformes

Une plateforme doit répondre à certains attributs clés :

- **Flexibilité et composabilité** ;
- **Sécurité par défaut** ;
- **Libre-service** ;
- **Documentation et support efficaces**.

Ces attributs guident la conception et l’évolution de la plateforme.

## Comprendre les aspects sociotechniques

La réussite d’une plateforme dépend autant des facteurs humains que techniques. Comprendre les besoins des utilisateurs, favoriser la collaboration et instaurer une culture ouverte sont essentiels. Chaque décision technique a des conséquences humaines, et les plateformes doivent faciliter le travail quotidien.

### Comprendre les besoins des utilisateurs

Une plateforme doit répondre aux attentes de multiples parties prenantes : développeurs, équipes métiers, responsables opérationnels. Identifier ces besoins dès le départ et intégrer les retours utilisateurs tout au long du cycle de vie est fondamental.

### Favoriser la collaboration

La collaboration repose sur la transparence, l’accessibilité et l’accompagnement. Les équipes plateforme doivent être visibles, accessibles et actives dans la promotion de leurs solutions.

### Cultiver une culture ouverte et centrée sur la plateforme

Former, motiver et engager les utilisateurs est indispensable. Les formations, incitations et communautés internes contribuent à l’adoption et à la pérennité de la plateforme.

## Résumé

Dans ce chapitre introductif, nous avons exploré le rôle des plateformes dans le développement logiciel moderne. Nous avons montré qu’elles sont des produits à part entière, nécessitant une planification stratégique et une amélioration continue. Nous avons abordé les fondamentaux, l’importance d’une approche orientée produit, la réduction de la charge cognitive et les aspects sociotechniques.

Ces enseignements préparent à une exploration plus approfondie des architectures de plateformes et de leur conception. Dans le prochain chapitre, nous aborderons les principes, l’architecture et les indicateurs de succès d’une plateforme.

