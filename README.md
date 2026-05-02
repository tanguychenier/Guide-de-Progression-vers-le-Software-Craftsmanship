# Guide de progression vers le Software Craftsmanship

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) [![Lang](https://img.shields.io/badge/Lang-Français-005EB8.svg)](#) [![Topic](https://img.shields.io/badge/Topic-Software%20Craftsmanship-brightgreen.svg)](#) [![Made with Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg)](https://www.markdownguide.org/)

Ce guide propose un parcours progressif pour passer du métier de développeur à celui de *software craftsman*. L'idée du Software Craftsmanship, formalisée par le [Manifesto for Software Craftsmanship](https://manifesto.softwarecraftsmanship.org/) (2009), n'est pas un nouveau processus à appliquer mais une posture : tendre vers la maîtrise, livrer du logiciel qu'on est fier de signer, et transmettre.

Le parcours est découpé en quatre étapes, chacune se concentrant sur une dimension précise. Elles peuvent être suivies en ordre, ou piochées selon le contexte. Comptez plusieurs mois par étape pour lire, pratiquer et intégrer.

## Table des matières

- [1. Fondamentaux du développement](#1-fondamentaux-du-développement)
- [2. Qualité du code et tests](#2-qualité-du-code-et-tests)
- [3. Conception et architecture](#3-conception-et-architecture)
- [4. Livraison et exploitation (DevOps)](#4-livraison-et-exploitation-devops)
- [Communautés et événements](#communautés-et-événements)
- [Habitudes du quotidien](#habitudes-du-quotidien)
- [Pour aller plus loin](#pour-aller-plus-loin)

## 1. Fondamentaux du développement

**Objectif** : disposer d'un socle solide en pratiques pragmatiques, lisibilité du code et professionnalisme.

### Livres

1. **[The Pragmatic Programmer: From Journeyman to Master](https://www.amazon.fr/Pragmatic-Programmer-Journeyman-Master/dp/020161622X)** — Andrew Hunt, David Thomas
   La référence sur les bonnes pratiques transverses : DRY, orthogonalité, programmation défensive, automatisation. La 20e édition anniversaire (2019) modernise les exemples.

2. **[Clean Code: A Handbook of Agile Software Craftsmanship](https://www.amazon.fr/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)** — Robert C. Martin
   Heuristiques concrètes pour écrire du code lisible : nommage, fonctions courtes, commentaires utiles, gestion des erreurs.

3. **[The Clean Coder: A Code of Conduct for Professional Programmers](https://www.amazon.fr/Clean-Coder-Conduct-Professional-Programmers/dp/0137081073)** — Robert C. Martin
   La face professionnelle du métier : engagements, estimations, refus quand c'est nécessaire, gestion du temps et de la pression.

### Pratique

- **[Exercism](https://exercism.io/)** — exercices avec retour de mentors humains, plus de 60 langages.
- **[Codewars](https://www.codewars.com/)** — *katas* ranking-based, utile pour explorer un nouveau langage rapidement.
- **Tenir un journal d'apprentissage** — quelques lignes par semaine sur ce que vous avez appris ; le cumul fait la différence.

### Au sortir de cette étape, vous savez

- nommer, structurer et formater un fichier de manière à ne pas faire perdre de temps au prochain lecteur ;
- repérer les *code smells* fréquents et les corriger ;
- distinguer ce qui relève de la technique pure de ce qui relève du professionnalisme.

## 2. Qualité du code et tests

**Objectif** : développer guidé par les tests, refactorer en confiance, intervenir sur du code legacy sans le casser.

### Livres

1. **[Growing Object-Oriented Software, Guided by Tests](https://www.amazon.fr/Growing-Object-Oriented-Software-Guided-Tests/dp/0321503627)** — Steve Freeman, Nat Pryce
   *La* référence sur le TDD outside-in et la conception orientée objet pilotée par les tests.

2. **[Refactoring: Improving the Design of Existing Code (2nd ed.)](https://www.amazon.fr/Refactoring-Improving-Design-Existing-Code/dp/0134757599)** — Martin Fowler
   Catalogue de refactorings nommés, avec mécanique pas à pas. Édition 2018 en JavaScript.

3. **[Working Effectively with Legacy Code](https://www.amazon.fr/Working-Effectively-Legacy-Code-Feathers/dp/0131177052)** — Michael Feathers
   Comment introduire des tests sur du code qui n'en a jamais eu, technique des *seams*, refactorings sûrs.

### Pratique

- **[Coding Dojo](https://codingdojo.org/)** — résoudre un problème à plusieurs en TDD strict.
- **Katas classiques** : Bowling Game, Roman Numerals, Gilded Rose, Tennis Refactoring.
- **Mob/Pair programming** régulier sur du code de production.
- **Mesurer** la couverture de tests d'un projet réel et identifier les zones aveugles.

### Au sortir de cette étape, vous savez

- écrire un test avant le code de production, quel que soit le contexte ;
- refactorer une fonction de 200 lignes sans la casser ;
- ajouter une fonctionnalité à un module non testé sans le réécrire de zéro.

## 3. Conception et architecture

**Objectif** : structurer un système au-delà de la classe ou du module, comprendre les compromis architecturaux et les frontières de domaine.

### Livres

1. **[Domain-Driven Design: Tackling Complexity in the Heart of Software](https://www.amazon.fr/Domain-Driven-Design-Complexity-Software/dp/0321125215)** — Eric Evans (« livre rouge »)
   Le fondateur du DDD : langage ubiquitaire, bounded contexts, modélisation tactique et stratégique.

2. **[Implementing Domain-Driven Design](https://www.amazon.fr/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)** — Vaughn Vernon (« livre jaune »)
   Le pendant pratique d'Evans, avec du code et des recettes.

3. **[Clean Architecture: A Craftsman's Guide to Software Structure and Design](https://www.amazon.fr/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164)** — Robert C. Martin
   Synthèse des principes de découplage : SOLID, frontières, indépendance vis-à-vis du framework et de la base de données.

4. **[Designing Data-Intensive Applications](https://www.amazon.fr/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321)** — Martin Kleppmann
   Tout ce qu'il faut savoir sur le stockage, la cohérence, la réplication, le streaming et la résilience.

5. **[Building Evolutionary Architectures: Support Constant Change](https://www.amazon.fr/Building-Evolutionary-Architectures-Support-Constant/dp/1491986360)** — Neal Ford, Rebecca Parsons, Patrick Kua
   Architecture conçue pour évoluer, *fitness functions*, tests d'architecture.

### Pratique

- **[System Design Primer](https://github.com/donnemartin/system-design-primer)** — exercices de conception de systèmes à grande échelle.
- **Lire l'architecture** de projets open-source dans son langage de prédilection.
- **Documenter** les décisions structurantes via des [ADR](https://adr.github.io/) (*Architecture Decision Records*).
- **Animer un Event Storming** sur un domaine que vous connaissez.

### Au sortir de cette étape, vous savez

- découper un système en *bounded contexts* qui correspondent au métier ;
- choisir entre monolithe modulaire et microservices avec des arguments concrets ;
- justifier vos décisions architecturales par écrit, en explicitant les compromis.

## 4. Livraison et exploitation (DevOps)

**Objectif** : porter la qualité jusqu'en production, livrer souvent, observer ce qui tourne.

### Livres

1. **[The Phoenix Project: A Novel About IT, DevOps, and Helping Your Business Win](https://www.amazon.fr/Phoenix-Project-DevOps-Helping-Business/dp/1942788290)** — Gene Kim, Kevin Behr, George Spafford
   Roman pédagogique qui fait comprendre les *Three Ways* du DevOps par l'histoire d'une équipe en crise.

2. **[Accelerate: The Science of Lean Software and DevOps](https://www.amazon.fr/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339)** — Nicole Forsgren, Jez Humble, Gene Kim
   Synthèse des recherches DORA : les quatre métriques (lead time, deployment frequency, MTTR, change failure rate) et leurs corrélations avec la performance d'entreprise.

3. **[Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation](https://www.amazon.fr/Continuous-Delivery-Reliable-Deployment-Automation/dp/0321601912)** — Jez Humble, David Farley
   Mécanique du *deployment pipeline*, infrastructure as code, gestion des bases de données.

4. **[Site Reliability Engineering](https://sre.google/sre-book/table-of-contents/)** — Google (gratuit en ligne)
   Disponibilité comme produit, SLI/SLO/SLA, *error budgets*, postmortems sans blâme.

### Pratique

- **Construire son propre pipeline** sur un side-project : commit → tests → build → déploiement automatique.
- **[Kubernetes Documentation](https://kubernetes.io/docs/home/)** — l'orchestrateur de fait pour les conteneurs.
- **[The Twelve-Factor App](https://12factor.net/fr/)** — méthodologie pour des applications portables et déployables en continu.
- **Exécuter un game day** : couper volontairement un service pour observer la résilience du reste.

### Au sortir de cette étape, vous savez

- mettre en place un pipeline de livraison continue depuis zéro ;
- diagnostiquer un incident en production à partir de logs, métriques et traces ;
- discuter SLO, *error budget* et coût de l'indisponibilité avec un product manager.

## Communautés et événements

Apprendre seul a ses limites. La communauté du craftsmanship est active en France et dans le monde francophone.

- **[Software Craftsmanship Communauté Francophone](https://www.craftsmanship.fr/)** — annuaire des meet-ups francophones.
- **Meet-ups** : Software Crafters Paris, Lyon, Bordeaux, Nantes, Toulouse, Bruxelles, Genève, Montréal.
- **Conférences** :
  - [SoCraTes](https://www.socrates-conference.de/) — *unconference* internationale, plusieurs déclinaisons (FR, BE, CH).
  - [NewCrafts](https://ncrafts.io/) — Paris, début juin chaque année.
  - [Devoxx France](https://www.devoxx.fr/) — généraliste, fort axe craft.
- **Coding dojos d'entreprise** — beaucoup d'entreprises en organisent, parfois ouvertes aux externes.

## Habitudes du quotidien

Les livres et les conférences donnent le matériel ; ce sont les habitudes qui créent la maîtrise.

- **Lire du code** une heure par semaine, pas le sien — un projet open-source dans son langage.
- **Prendre une demi-heure** après chaque tâche pour relire son propre code à froid.
- **Faire de la veille** ciblée : un seul flux, lu régulièrement, vaut mieux que dix abandonnés.
- **Tenir un journal** des décisions techniques avec leur contexte et leur résultat à six mois.
- **Enseigner** ce que vous venez d'apprendre — un *brown bag*, un article, un kata animé. La transmission consolide la compréhension.

## Pour aller plus loin

- [Manifesto for Software Craftsmanship](https://manifesto.softwarecraftsmanship.org/)
- [Principes SOLID — Robert C. Martin](https://en.wikipedia.org/wiki/SOLID)
- [Refactoring Guru — Design patterns et refactoring](https://refactoring.guru/)
- [The Twelve-Factor App](https://12factor.net/) — applications modernes
- [DORA — State of DevOps reports](https://dora.dev/research/)
- Chaîne YouTube de [Continuous Delivery (Dave Farley)](https://www.youtube.com/@ContinuousDelivery)

## Contribuer

Pour proposer une ressource, corriger une erreur ou partager un retour d'expérience, ouvrez une *Pull Request* ou une *Issue*. Toutes les contributions sont les bienvenues.

## Licence

Distribué sous licence [MIT](LICENSE).

## Auteur

**Tansoftware - Tanguy Chénier** · [LinkedIn](https://www.linkedin.com/in/tanguy-chenier) · [Tan-Software](https://github.com/Tan-Software) · [Compte personnel (derniers outils)](https://github.com/tanguychenier) · [tansoftware.com](https://www.tansoftware.com)
