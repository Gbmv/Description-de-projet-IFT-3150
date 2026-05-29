---
title: Vue d'ensemble du projet
---

<style>
    @media screen and (min-width: 76em) {
        .md-sidebar--primary {
            display: none !important;
        }
    }
</style>

# Vue d'ensemble du projet

!!! info "Informations générales"
    **Session**: Été 2026  
    **Auteur(s)**: Gabriel Barroso Magno Viana - 20283304 
    **Thème(s)**:Gestion des membres, microservices, sécurité, paiements en ligne, architecture web
    **Superviseur(s)**: Louis Edouard Lafontant
    **Collaborateur(s):** Jasmin Robert , Marc St-Pierre, Marc-Antoine , Normand Rivard, Yassine Azmani

## Description du projet

> :bulb: N'oubliez pas d'effacer ou mettre en commentaires les notes (`>`) en début de section

### Contexte
La Fédération des astronomes amateurs du Québec (FAAQ) regroupe 26 clubs membres répartis dans 15 régions du Québec, pour environ 2000 astronomes amateurs, membres de clubs ou membres individuels. .

Actuellement, plusieurs outils distincts sont utilisés pour répondre aux besoins de la fédération : gestion des adhésions, accès à l’espace membre du site web, communication par infolettres, inscriptions à des événements, sondages et paiements. Ces plateformes ne sont pas toujours synchronisées entre elles, ce qui entraîne des tâches manuelles, des coûts récurrents, des difficultés de maintenance et une gestion moins efficace des données.

La FAAQ souhaite donc moderniser son environnement numérique en développant une plateforme interne de gestion des membres. Cette plateforme devra être sécurisée, fiable, intuitive, et conforme aux exigences québécoises en matière de protection des renseignements personnels.

### Problématique

Le problème central est l’absence d’un système unifié permettant de gérer efficacement les membres, les clubs, les abonnements, les paiements et les accès numériques de la FAAQ.

Les solutions actuellement utilisées sont fragmentées. Certaines données doivent être mises à jour manuellement dans plusieurs systèmes, notamment entre la plateforme d’adhésion et l’espace membre du site web. Cette situation augmente le risque d’erreurs, complique la gestion administrative et limite l’autonomie de la fédération et des clubs.

Les solutions disponibles sur le marché ne répondent pas entièrement aux besoins spécifiques de la FAAQ ou impliquent des coûts élevés. Le développement d’une solution interne apparaît donc comme une option pertinente pour créer un système mieux adapté à la structure fédération-clubs et aux besoins à long terme de l’organisation.


### Proposition et objectifs

Le projet propose le développement d’une plateforme web modulaire de gestion des membres pour la FAAQ. Cette plateforme aura pour objectif de centraliser les informations et les opérations actuellement réparties entre plusieurs outils, tout en respectant la structure particulière de la fédération, composée de membres, de clubs et d’un niveau fédéral d’administration.

La solution sera organisée autour de trois niveaux d’utilisation :

1. **Membre** : création de compte, modification des informations personnelles, gestion des membres familiaux, abonnement à un ou plusieurs clubs et consultation du statut d’adhésion.
2. **Club** : gestion des membres du club, création de nouveaux membres, gestion des types d’abonnement, configuration des tarifs, rappels automatisés et production de rapports.
3. **Fédération** : gestion globale des clubs et des membres, création de clubs, attribution des privilèges et supervision de l’ensemble du système.

Les objectifs principaux du projet sont :

- centraliser la gestion des membres et des clubs ;
- réduire les tâches manuelles liées à l’utilisation de plusieurs plateformes ;
- permettre l’abonnement à plusieurs clubs ;
- intégrer une gestion sécurisée des paiements ;
- produire des rapports configurables ;
- gérer différents niveaux de privilèges ;
- assurer la protection des renseignements personnels ;
- développer une architecture modulaire, maintenable et évolutive.

L’approche proposée répond à la problématique en développant une plateforme adaptée aux besoins réels de la FAAQ, plutôt qu’en obligeant l’organisation à s’adapter aux limites d’un outil commercial externe.

### Architecture en microservices prévue

La solution proposée repose sur une architecture modulaire organisée autour de plusieurs microservices. Chaque microservice aura une responsabilité précise afin de limiter le couplage entre les composants, d’améliorer la sécurité et de faciliter la maintenance du système.

Les principaux microservices prévus sont :

- **Hauméa** : microservice d’authentification et de sécurité. Il agit comme point d’entrée principal du système. Il sera responsable de la connexion des utilisateurs, de la validation des jetons d’accès et de la gestion des privilèges.

- **Cérès** : microservice de gestion des données d’affaires. Il sera responsable de la gestion des membres, des clubs, des abonnements, des événements et des rapports. Ce service ne stockera pas les mots de passe ni les données bancaires sensibles.

- **Chiron** : microservice de gestion des paiements. Il sera responsable des transactions, des paiements en ligne, des reçus et de l’intégration avec une passerelle de paiement. Les numéros de carte de crédit ne seront pas stockés en clair ; le système utilisera plutôt des jetons fournis par le service de paiement.

- **MakeMake** : sous-système de tests d’intégration automatisés. Il permettra de créer des scénarios de tests afin de vérifier le bon fonctionnement de l’ensemble de la plateforme et de réduire les risques de régression lors du développement.

Cette séparation permet de mieux protéger les données sensibles, car chaque microservice accède uniquement aux informations nécessaires à son fonctionnement. Elle rend également le projet plus évolutif, puisque de nouvelles fonctionnalités pourront être ajoutées sans modifier toute la plateforme.


### Méthodologie

Le projet sera réalisé selon une démarche progressive inspirée des méthodes agiles. L’objectif est de diviser le développement en étapes plus petites afin de pouvoir tester régulièrement les fonctionnalités, valider les choix techniques et ajuster la solution selon les besoins réels de la FAAQ.

Des rencontres hebdomadaires seront organisées afin de présenter les avancées réalisées, discuter les difficultés rencontrées et ajuster les priorités de développement lorsque nécessaire. Ces rencontres permettront également d’aborder des sujets plus spécifiques, comme la gestion des accès, la sécurité des données, l’architecture des microservices, la migration des données ou l’intégration des paiements.

La démarche prévue comprend les grandes étapes suivantes :

1. **Analyse des besoins** : comprendre les besoins des membres, des clubs et de la fédération, en tenant compte des limites des outils actuellement utilisés.
2. **Définition de l’architecture** : organiser la solution autour de microservices ayant des responsabilités claires.
3. **Développement de la couche d’accès** : mettre en place l’authentification, la création de comptes et la gestion des privilèges.
4. **Développement des fonctionnalités métier** : ajouter progressivement la gestion des membres, des clubs, des abonnements et des événements.
5. **Intégration des paiements** : prévoir une communication sécurisée avec une passerelle de paiement externe.
6. **Mise en place des tests** : créer des scénarios de tests manuels et automatisés afin de limiter les régressions.
7. **Documentation continue** : documenter les décisions techniques, les fonctionnalités développées et l’évolution du projet.

Le développement commencera par les fonctionnalités les plus fondamentales, comme la gestion des comptes, l’authentification et les privilèges. Les fonctionnalités liées aux clubs, aux abonnements, aux rapports et aux paiements seront ensuite intégrées progressivement.

### Validation et Évaluation

La validation du projet se fera de façon continue tout au long du développement. Elle reposera à la fois sur des tests techniques, sur des scénarios d’usage et sur les retours obtenus lors des rencontres hebdomadaires avec les collègues et collaborateurs du projet.

Des **tests unitaires** seront prévus afin de vérifier le bon fonctionnement des différentes fonctions développées séparément. Par exemple, ils pourront servir à valider la création d’un compte, la gestion des rôles, la modification des informations d’un membre ou certaines règles liées aux abonnements.

Pour les tests d’API, l’outil **Bruno** sera utilisé afin de documenter, exécuter et valider les requêtes vers les différents services. Il permettra de tester les endpoints, les réponses attendues, les codes de statut HTTP, ainsi que certains scénarios liés à l’authentification, aux privilèges et à la communication entre les services.

Le sous-système **MakeMake** sera utilisé pour les tests automatisés d’intégration. Il permettra de créer des scénarios plus complets afin de vérifier le bon fonctionnement de l’ensemble de la plateforme et de réduire les risques de régression lors de l’ajout de nouvelles fonctionnalités.

La validation prendra aussi en compte les commentaires des collègues lors des rencontres hebdomadaires. Ces échanges permettront de présenter les avancées, d’identifier les problèmes rencontrés, de discuter de choix techniques plus spécifiques et d’ajuster certaines priorités si nécessaire.

L’évaluation du projet reposera donc sur une combinaison de tests unitaires, de tests d’API avec Bruno, de tests automatisés d’intégration avec MakeMake, de scénarios d’usage et de retours qualitatifs obtenus pendant les rencontres de suivi.


## Équipe


| Membre | Rôle principal | Responsabilités |
|---|---|---|
| **Gabriel Barroso Magno Viana** | Étudiant / développeur | Participation au développement, documentation du projet, suivi des livrables et intégration progressive des fonctionnalités |
| **Marc St-Pierre** | Développeur chef | Encadrement technique du développement, orientation des choix d’architecture et soutien à la conception des microservices |
| **Normand Rivard** | Webmestre | Contribution à l’intégration avec l’environnement web existant de la FAAQ et appui aux aspects liés au site web |
| **Marc-Antoine** | Stagiaire | Appui au développement, aux tests, à la documentation ou aux tâches techniques selon les besoins du projet |
| **Yassine Azmani** | Étudiant à l’Université de Montréal | Contribution au développement, aux tests ou à l’analyse technique du projet |
| **Jasmin Robert** | Directeur général de la FAAQ | Validation des besoins organisationnels, suivi des priorités de la FAAQ et contribution à l’évaluation fonctionnelle de la solution |
| **Louis Edouard Lafontant** | Superviseur | Encadrement académique du projet, suivi pédagogique et validation des livrables |

## Échéancier

!!! info
    Le suivi complet est disponible dans la page [Suivi de projet](suivi.md).

| Activités                      | Début   |   Fin   | Livrable                            | Statut      |
|--------------------------------|---------|---------|-------------------------------------|-------------|
| Ouverture de projet            | 4 mai   | 15 mai  | Proposition de projet               | ✅ Terminé  |
| Études préliminaires           | 4 mai   | 22 mai  | Document d'analyse                  | 🔄 En cours |
| Présentation + Rapport         | 7 aout  | 14 aout | Présentation + Rapport              | ⏳ À venir  |
