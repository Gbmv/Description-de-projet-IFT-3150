---
title: Études préliminaires
---

<style>
    @media screen and (min-width: 76em) {
        .md-sidebar--primary {
            display: none !important;
        }
    }
</style>

# Études préliminaires

> :bulb: Cette page sert à documenter les recherches, analyses et explorations réalisées avant ou durant le projet
> Elle ne remplace pas le rapport final, mais permet de conserver une trace de votre démarche et des réflexions ayant guidé le projet.    

## Structure suggérée

 La structure suivante est donnée à titre indicatif.  
> Vous pouvez l’adapter selon la nature de votre projet.>

### Compréhension du problème

La Fédération des astronomes amateurs du Québec (FAAQ) regroupe plusieurs clubs membres répartis dans différentes régions du Québec. Elle doit gérer des membres individuels, des membres associés à des clubs, des abonnements, des communications, des paiements et des accès à certains services numériques. Actuellement, ces besoins sont couverts par plusieurs plateformes distinctes. Certaines servent à gérer les adhésions, d’autres les communications, les inscriptions à des événements, les paiements ou l’accès à l’espace membre du site web. 

Cette fragmentation complique la gestion administrative, car les données ne sont pas toujours synchronisées entre les différents outils. Le problème principal est donc l’absence d’un système centralisé permettant de gérer efficacement les membres, les clubs, les abonnements, les paiements et les accès numériques. Cette situation entraîne des tâches manuelles, des coûts récurrents, des risques d’erreurs et une dépendance envers plusieurs services externes. 

Le projet vise à répondre à ce besoin en développant une plateforme interne, plus cohérente avec la structure de la FAAQ et plus adaptée à une organisation composée d’une fédération et de plusieurs clubs autonomes.

### Analyse des solutions ou approches existantes

Plusieurs types de solutions peuvent être envisagés pour gérer des membres et des abonnements : plateformes commerciales de gestion d’associations, extensions WordPress, systèmes de paiement externes, outils d’infolettres ou solutions développées sur mesure. Les solutions existantes présentent certains avantages. Elles peuvent offrir une interface déjà disponible, des fonctionnalités de base pour la gestion des membres et une mise en service relativement rapide. 

Cependant, elles présentent aussi des limites importantes dans le contexte de la FAAQ. Les principales limites observées sont : 
- difficulté à gérer une structure fédération-clubs ; - personnalisation parfois limitée ; 
- coûts récurrents élevés ; 
- dépendance envers des fournisseurs externes ; 
- intégration incomplète avec le site web existant ; 
- synchronisation manuelle de certaines données ; - contrôle limité sur la base de données ; 
- difficulté à adapter la solution aux besoins futurs.

 Certaines solutions du marché peuvent répondre partiellement aux besoins, mais elles ne semblent pas offrir toute la flexibilité nécessaire pour gérer les membres, les clubs, les abonnements multiples, les privilèges d’accès, les paiements et les rapports selon la logique propre à la FAAQ. Le développement interne apparaît donc comme une approche pertinente, à condition que le projet soit structuré de manière progressive, sécurisée et maintenable.

### Contraintes techniques

La plateforme devra être conçue de manière sécurisée, fiable et évolutive. Elle devra permettre la gestion de plusieurs types d’utilisateurs, tout en limitant l’accès aux données sensibles selon le rôle de chaque personne.

Les principales contraintes techniques sont :

- mettre en place une authentification sécurisée ;
- gérer les rôles et les privilèges des utilisateurs ;
- séparer clairement les responsabilités entre les microservices ;
- protéger les renseignements personnels des membres ;
- permettre la communication entre les services au moyen d’API ;
- intégrer éventuellement une passerelle de paiement externe ;
- éviter le stockage de données bancaires sensibles en clair ;
- prévoir des tests unitaires, des tests d’API avec Bruno et des tests automatisés d’intégration avec MakeMake.

### Contraintes humaines

Le projet implique plusieurs personnes ayant des profils différents : développeurs, collaborateurs techniques, responsables de la FAAQ, superviseur académique et étudiants. Il sera donc important de maintenir une documentation claire afin que chaque membre de l’équipe puisse comprendre l’état du projet, les décisions prises et les prochaines étapes.

Des rencontres hebdomadaires seront prévues afin de présenter les avancées, de discuter des difficultés rencontrées et de clarifier certains aspects plus spécifiques, comme l’architecture, la sécurité, les tests, les besoins fonctionnels ou l’organisation des microservices.

Une attention particulière devra également être accordée aux utilisateurs finaux de la plateforme. Une partie du public de la FAAQ peut être composée de personnes plus âgées ou moins familières avec les outils numériques. Cette réalité devra influencer la conception de l’interface, qui devra rester simple, lisible et intuitive. Les parcours importants, comme la création d’un compte, la modification des informations personnelles, le renouvellement d’un abonnement ou le paiement, devront être faciles à comprendre et ne pas comporter trop d’étapes inutiles.

### Contraintes organisationnelles

La plateforme devra respecter la structure de la FAAQ, qui repose sur trois niveaux principaux :

1. **Membre** : gestion du profil personnel, des informations familiales et des abonnements.
2. **Club** : gestion des membres du club, des types d’abonnement, des tarifs, des rappels et des rapports.
3. **Fédération** : gestion globale des clubs, des membres, des privilèges et de la supervision du système.

Cette organisation impose une gestion précise des accès. Un club doit pouvoir gérer ses propres membres sans accéder aux données des autres clubs, tandis que la fédération doit disposer d’une vue plus globale du système.

### Contraintes liées à la sécurité

La plateforme manipulera des renseignements personnels liés aux membres, aux clubs et aux abonnements. La sécurité devra donc être intégrée dès la conception du système.

Les besoins principaux liés à la sécurité sont :

- appliquer le principe du moindre privilège ;
- limiter la collecte de données aux informations nécessaires ;
- protéger les données sensibles ;
- contrôler l’accès aux informations selon le rôle de l’utilisateur ;
- séparer les données d’affaires, les données d’authentification et les données de paiement ;
- utiliser des jetons de paiement plutôt que de stocker des numéros de carte de crédit ;
- prévoir une journalisation suffisante pour assurer le suivi des accès sans surcollecter de données.

### Contraintes liées à la migration des données

La FAAQ possède déjà des données sur ses membres, ses clubs et ses abonnements. Il faudra donc prévoir une stratégie de migration vers la nouvelle plateforme.

Cette migration devra permettre de transférer les données utiles sans créer de doublons, de pertes d’informations ou d’incohérences. Une phase de validation sera nécessaire afin de vérifier que les membres, les clubs, les statuts d’abonnement et les informations administratives sont correctement transférés.

Une approche progressive pourrait être utilisée, par exemple avec un projet pilote auprès de quelques clubs avant une migration complète.

### Contraintes temporelles

Le projet est réalisé pendant la session d’été 2026. Il doit donc être organisé autour de livrables progressifs : proposition de projet, études préliminaires, documentation, réalisation technique, tests, présentation et rapport final.

L’objectif n’est pas nécessairement de livrer toute la plateforme complète pendant la session, mais de contribuer à une base solide, documentée et évolutive pour la suite du développement.

### Explorations techniques ou conceptuelles

Les premières explorations techniques portent principalement sur l’architecture générale du système, l’organisation des microservices et les outils qui seront utilisés pour soutenir le développement et la validation du projet.

L’architecture envisagée repose sur une séparation claire des responsabilités entre plusieurs services. **Hauméa** jouera le rôle de point d’entrée principal de la plateforme et sera responsable de l’authentification, de la validation des jetons d’accès et de la gestion des privilèges. **Cérès** sera responsable des données d’affaires, comme les membres, les clubs, les abonnements, les événements et les rapports. **Chiron** sera lié à la gestion des paiements et à l’intégration avec une passerelle de paiement externe. Enfin, **MakeMake** sera utilisé pour les tests automatisés d’intégration.

Une première réflexion a aussi été menée sur les tests du système. Les API pourront être testées avec **Bruno**, afin de vérifier les requêtes, les réponses attendues, les codes de statut HTTP et certains scénarios liés à l’authentification ou aux privilèges. En complément, **MakeMake** permettra de créer des scénarios automatisés plus complets, afin de vérifier le comportement global de la plateforme et de réduire les risques de régression lors de l’ajout de nouvelles fonctionnalités.

Les explorations conceptuelles portent également sur l’expérience utilisateur. Comme la plateforme sera utilisée par des membres ayant des niveaux variés de familiarité avec les outils numériques, l’interface devra rester simple, lisible et intuitive. Les parcours essentiels, comme la création d’un compte, la modification des informations personnelles, le renouvellement d’un abonnement ou le paiement, devront être faciles à comprendre.

Enfin, la documentation du projet avec MkDocs constitue aussi une première exploration importante. Elle permet de centraliser les informations sur l’analyse, la réalisation, le suivi et l’évaluation du projet, tout en facilitant la communication entre les membres de l’équipe.


### Choix retenus

À partir des études préliminaires, plusieurs choix ont été retenus pour orienter la suite du projet.

Le premier choix est de privilégier une architecture modulaire basée sur des microservices. Cette approche permet de séparer clairement les responsabilités entre les différentes composantes du système. Hauméa sera responsable de l’authentification et de la gestion des accès, Cérès prendra en charge les données d’affaires, Chiron sera lié aux paiements, et MakeMake servira aux tests automatisés d’intégration.

Le deuxième choix est de commencer le développement par les fonctionnalités fondamentales, notamment la création de comptes, l’authentification et la gestion des privilèges. Ces éléments constituent la base nécessaire avant d’ajouter les fonctionnalités liées aux membres, aux clubs, aux abonnements, aux rapports et aux paiements.

Le troisième choix est d’intégrer les tests dès le début du projet. Les tests unitaires permettront de vérifier certaines fonctions isolées, tandis que Bruno sera utilisé pour tester les API. MakeMake servira ensuite à créer des scénarios automatisés plus complets afin de vérifier le comportement global du système et de réduire les risques de régression.

Le quatrième choix est de maintenir une documentation continue avec MkDocs. Cette documentation permettra de conserver une trace des décisions techniques, des choix d’architecture, des contraintes identifiées et de l’évolution du projet. Elle facilitera aussi la collaboration entre les membres de l’équipe.

Enfin, le projet adoptera une démarche progressive, inspirée des méthodes agiles. Les rencontres hebdomadaires permettront de présenter les avancées, de discuter des difficultés rencontrées et d’ajuster les priorités lorsque nécessaire. Cette approche devrait permettre de développer une base solide, tout en gardant la solution alignée avec les besoins réels de la FAAQ.

### Références

- Fédération des astronomes amateurs du Québec. *Plateforme de gestion des membres développée à l’interne — Livre blanc*. Document interne, 2025.

- MkDocs. *MkDocs Documentation*. Documentation utilisée pour la création du site de documentation du projet.

- Material for MkDocs. *Material for MkDocs Documentation*. Documentation utilisée pour la configuration du thème et de la navigation du site.

- Bruno. *Bruno Documentation*. Documentation utilisée pour comprendre l’utilisation de Bruno dans les tests d’API.

- Spring Boot. *Spring Boot Documentation*. Documentation utilisée pour comprendre la structure générale d’une application Spring Boot, la création d’API REST et l’organisation des composants.

- *Spring Boot Tutorial for Beginners [2025]*. Tutoriel vidéo utilisé comme ressource d’introduction pour comprendre les bases de Spring Boot.

- *Spring Boot Tutorial for Beginners | Full Course 2025*. Cours vidéo utilisé comme ressource complémentaire pour approfondir les notions de base de Spring Boot, notamment les contrôleurs, les services, les dépendances et la création d’API.

- Martin Fowler. *Microservices*. Référence générale utilisée pour comprendre les principes d’une architecture basée sur des microservices.

- OWASP Foundation. *OWASP Web Security Testing Guide*. Référence générale pour les bonnes pratiques liées aux tests et à la sécurité des applications web.


