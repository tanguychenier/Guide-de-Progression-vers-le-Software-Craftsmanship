# Guide de progression vers le Software Craftsmanship

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) [![Lang](https://img.shields.io/badge/Lang-Français-005EB8.svg)](#) [![Topic](https://img.shields.io/badge/Topic-Software%20Craftsmanship-brightgreen.svg)](#) [![Made with Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg)](https://www.markdownguide.org/)

Ce guide propose un parcours progressif pour passer du métier de développeur à celui de *software craftsman* (artisan du logiciel). L'idée du Software Craftsmanship, formalisée par le [Manifesto for Software Craftsmanship](https://manifesto.softwarecraftsmanship.org/) (2009), n'est pas un nouveau processus à appliquer mais une posture : tendre vers la maîtrise, livrer du logiciel qu'on est fier de signer, et transmettre.

Le parcours est découpé en plusieurs étapes. Chaque étape se concentre sur une dimension précise. Elles peuvent être suivies en ordre, ou piochées selon le contexte. Comptez plusieurs mois par étape pour lire, pratiquer, intégrer.

Ce document est un **guide de cours**, pas un cahier d'exercices : il vous indique quoi lire, quelles pratiques adopter, quels mots employer, et comment juger de votre progression. Les exercices, vous les rencontrerez en équipe, en *coding dojo* ou en mob. Ici, on pose le décor.

## Table des matières

- [Glossaire de référence](#glossaire-de-référence)
- [Le Manifeste du Software Craftsmanship](#le-manifeste-du-software-craftsmanship)
- [Parcours junior, confirmé, senior](#parcours-junior-confirmé-senior)
- [1. Fondamentaux du développement](#1-fondamentaux-du-développement)
- [2. Qualité du code et tests](#2-qualité-du-code-et-tests)
- [3. Conception et architecture](#3-conception-et-architecture)
- [4. Livraison et exploitation (DevOps)](#4-livraison-et-exploitation-devops)
- [Test-Driven Development en profondeur](#test-driven-development-en-profondeur)
- [Catalogue de refactorings essentiels](#catalogue-de-refactorings-essentiels)
- [Katas recommandés par difficulté](#katas-recommandés-par-difficulté)
- [Pair programming et mob programming](#pair-programming-et-mob-programming)
- [La revue de code (code review) bien faite](#la-revue-de-code-code-review-bien-faite)
- [Travailler avec du code legacy](#travailler-avec-du-code-legacy)
- [Évolution de carrière du craftsman](#évolution-de-carrière-du-craftsman)
- [Communautés et événements](#communautés-et-événements)
- [Anti-patterns du faux craft](#anti-patterns-du-faux-craft)
- [Habitudes du quotidien](#habitudes-du-quotidien)
- [Pour aller plus loin](#pour-aller-plus-loin)

## Glossaire de référence

Le craft a son vocabulaire. Avant de plonger, on l'aligne. Cette section sert de point d'ancrage : revenez-y dès qu'un terme du guide reste flou.

- **TDD** (*Test-Driven Development*, développement piloté par les tests) : on écrit d'abord un test qui échoue, puis le code minimal pour le faire passer, puis on refactorise. Cycle red-green-refactor.
- **BDD** (*Behavior-Driven Development*, développement piloté par le comportement) : variante du TDD où les tests sont exprimés en langage naturel (Given / When / Then) pour rester proches du métier. Outils typiques : Cucumber, SpecFlow, Behat.
- **Refactoring** (refactorisation) : modifier la structure interne du code sans changer son comportement observable. Toujours sous filet de sécurité de tests.
- **Code review** (revue de code) : relecture d'un changement par un autre développeur avant intégration, sur une *Pull Request* ou *Merge Request*.
- **Pair programming** (programmation en binôme) : deux développeurs, un clavier, deux rôles (driver / navigator) qui s'échangent régulièrement.
- **Mob programming** (programmation en groupe) : la même chose à trois, quatre, cinq personnes ou plus. Une seule machine, le savoir circule.
- **Kata** : exercice de programmation court, répétable, dont l'enjeu n'est pas le résultat mais la *manière* de l'atteindre. Inspiré des arts martiaux japonais.
- **Dojo** (*coding dojo*) : séance collective où l'on pratique un kata ensemble, généralement en TDD strict, en pair ou en mob.
- **Rétro** (*retrospective*, rétrospective) : réunion de fin d'itération pour inspecter ce qui a marché, ce qui n'a pas marché, et décider d'une action d'amélioration.
- **Kaizen** (改善) : terme japonais désignant l'amélioration continue par petits pas. La rétro en est l'instrument.
- **Dette technique** (*technical debt*) : raccourci pris dans le code ou la conception qui facilite la livraison aujourd'hui mais coûte demain. Métaphore de Ward Cunningham (1992).
- **Definition of Done** (DoD, définition de fini) : liste de critères qu'une tâche doit satisfaire pour être considérée comme terminée. Tests verts, revue passée, documentation à jour, déployé, etc.
- **Story point** : unité d'estimation relative d'effort, de complexité et de risque. Pas une unité de temps. Sert à comparer des tâches entre elles, pas à promettre une date.
- **PR / MR** (*Pull Request* / *Merge Request*) : demande d'intégrer une branche dans une autre, ouverte sur la forge (GitHub utilise PR, GitLab utilise MR). Support de la revue de code.
- **CI** (*Continuous Integration*, intégration continue) : pratique consistant à fusionner et tester son travail dans le tronc commun plusieurs fois par jour, automatiquement.
- **CD** (*Continuous Delivery*, livraison continue) : prolongement de la CI où chaque commit produit un artefact déployable à tout moment. *Continuous Deployment* va plus loin : chaque commit qui passe la CI est automatiquement mis en production.
- **YAGNI** (*You Aren't Gonna Need It*) : ne pas implémenter ce qui n'est pas demandé maintenant.
- **DRY** (*Don't Repeat Yourself*) : chaque connaissance doit avoir une représentation unique, faisant autorité, dans le système.
- **KISS** (*Keep It Simple, Stupid*) : préférer la solution simple à la solution clever.
- **SOLID** : cinq principes de conception objet (Single responsibility, Open/closed, Liskov substitution, Interface segregation, Dependency inversion).
- **Code smell** (mauvaise odeur du code) : symptôme qui suggère un problème de conception sans le prouver. Inventaire chez Fowler.
- **Bounded context** (contexte délimité) : frontière à l'intérieur de laquelle un modèle de domaine a un sens cohérent et un vocabulaire stable. Concept central du DDD.
- **ADR** (*Architecture Decision Record*) : court document daté qui consigne une décision d'architecture, son contexte et ses conséquences.

## Le Manifeste du Software Craftsmanship

Publié en 2009 par Robert C. Martin et un groupe de praticiens, le [Manifeste pour le Software Craftsmanship](https://manifesto.softwarecraftsmanship.org/) reprend la forme du [Manifeste Agile](https://agilemanifesto.org/iso/fr/manifesto.html) (2001) en lui ajoutant un quatrième niveau d'exigence.

> En tant qu'aspirants Software Craftsmen, nous augmentons la barre du développement professionnel de logiciel en pratiquant et en aidant les autres à apprendre le métier. À travers ce travail, nous en sommes venus à valoriser :
>
> Non seulement des logiciels qui fonctionnent, **mais aussi des logiciels bien conçus**.
> Non seulement l'adaptation aux changements, **mais aussi l'enrichissement constant de la valeur**.
> Non seulement les individus et leurs interactions, **mais aussi une communauté de professionnels**.
> Non seulement la collaboration avec le client, **mais aussi des partenariats productifs**.
>
> Ainsi, en recherchant les éléments de gauche, nous avons trouvé que ceux de droite sont indispensables.

**À retenir.** Le manifeste agile reste valable ; le craftsmanship en est une extension. Là où l'agile met l'accent sur la livraison de valeur et l'adaptation, le craft insiste sur la **manière** de livrer cette valeur : un code bien conçu, une communauté qui se forme, des partenariats au-delà de la transaction. Le craftsman ne s'oppose pas à l'agiliste, il refuse simplement le compromis « ça marche, tant pis pour le code ».

**Différence clé avec l'Agile Manifesto.** Le Manifeste Agile parle d'efficacité et d'humain dans la livraison. Le Manifeste Craftsmanship parle du **professionnalisme du producteur** : qualité intrinsèque, transmission, durabilité. Les deux sont complémentaires.

## Parcours junior, confirmé, senior

Un parcours réaliste s'étale sur plusieurs années, avec des paliers identifiables. Voici une cartographie indicative ; les durées varient selon le contexte, l'environnement et l'investissement personnel.

### Junior (0 à 2 ans)

**Mantra** : « je fais marcher, je fais lisible, je demande quand je bloque. »

- Lectures pivots : *The Pragmatic Programmer*, *Clean Code*.
- Pratiques : nommage soigné, fonctions courtes, tests unitaires sur du code neuf, premières revues de code à recevoir et à donner.
- Outils : maîtriser un IDE, Git en ligne de commande, un langage à fond plutôt que cinq survolés.
- Indicateurs de progression : vos PR passent la revue avec peu de remarques, vous savez expliquer un bug avant de le corriger.

### Confirmé (2 à 5 ans)

**Mantra** : « je conçois pour le changement, je teste avant, je laisse le code meilleur que je l'ai trouvé. »

- Lectures pivots : *Refactoring* (Fowler), *Working Effectively with Legacy Code* (Feathers), *Growing Object-Oriented Software* (Freeman & Pryce), *The Clean Coder*.
- Pratiques : TDD au quotidien, refactoring outillé, pair / mob, animation de katas internes, contribution à des décisions d'architecture documentées (ADR).
- Frontière typique : on devient *aller-chercheur* d'information sur un sujet flou, plutôt que d'attendre une spécification claire.
- Indicateurs : on vous confie la reprise de modules anciens, vous formulez des refus argumentés, vos estimations s'affinent.

### Senior et au-delà (5 ans et plus)

**Mantra** : « je fais grandir l'équipe et le système ; mon impact se mesure à ce qui tient sans moi. »

- Lectures pivots : *Domain-Driven Design* (Evans), *Implementing DDD* (Vernon), *Clean Architecture* (Martin), *Designing Data-Intensive Applications* (Kleppmann), *Accelerate* (Forsgren et al.), *Software Craftsmanship* (Mancuso), *Team Topologies* (Skelton & Pais).
- Pratiques : conception de systèmes, mentorat, animation de communautés, contribution à la stratégie technique, choix de compromis architecturaux assumés.
- Indicateurs : on vous sollicite pour arbitrer entre options techniques, vos écrits font référence dans l'équipe, des juniors progressent visiblement à votre contact.

Le passage d'un palier à l'autre n'est pas linéaire. On régresse temporairement chaque fois qu'on change de stack, de domaine ou de contexte. C'est normal.

## 1. Fondamentaux du développement

**Objectif** : disposer d'un socle solide en pratiques pragmatiques, lisibilité du code et professionnalisme.

### Livres — fondamentaux

1. **[The Pragmatic Programmer: From Journeyman to Master](https://www.amazon.fr/Pragmatic-Programmer-Journeyman-Master/dp/020161622X)** — Andrew Hunt, David Thomas
   La référence sur les bonnes pratiques transverses : DRY, orthogonalité, programmation défensive, automatisation. La 20e édition anniversaire (2019) modernise les exemples.

2. **[Clean Code: A Handbook of Agile Software Craftsmanship](https://www.amazon.fr/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)** — Robert C. Martin
   Heuristiques concrètes pour écrire du code lisible : nommage, fonctions courtes, commentaires utiles, gestion des erreurs.

3. **[The Clean Coder: A Code of Conduct for Professional Programmers](https://www.amazon.fr/Clean-Coder-Conduct-Professional-Programmers/dp/0137081073)** — Robert C. Martin
   La face professionnelle du métier : engagements, estimations, refus quand c'est nécessaire, gestion du temps et de la pression.

4. **[Software Craftsmanship: Professionalism, Pragmatism, Pride](https://www.amazon.fr/Software-Craftsmanship-Professionalism-Pragmatism-Pride/dp/0134052501)** — Sandro Mancuso
   Sandro Mancuso, fondateur de la London Software Craftsmanship Community, raconte le mouvement de l'intérieur : ce que signifie le craft, comment il se transmet, comment il s'incarne en entreprise.

### Pratique — fondamentaux

- **[Exercism](https://exercism.io/)** : exercices avec retour de mentors humains, plus de 60 langages.
- **[Codewars](https://www.codewars.com/)** : *katas* à classement, utiles pour explorer un nouveau langage rapidement.
- **Tenir un journal d'apprentissage** : quelques lignes par semaine sur ce que vous avez appris ; le cumul fait la différence.
- **Lire au moins un livre du bloc fondamentaux par trimestre**, plume à la main.

### Au sortir de l'étape Fondamentaux, vous savez

- nommer, structurer et formater un fichier de manière à ne pas faire perdre de temps au prochain lecteur ;
- repérer les *code smells* fréquents et les corriger ;
- distinguer ce qui relève de la technique pure de ce qui relève du professionnalisme.

## 2. Qualité du code et tests

**Objectif** : développer guidé par les tests, refactorer en confiance, intervenir sur du code legacy sans le casser.

### Livres — qualité et tests

1. **[Growing Object-Oriented Software, Guided by Tests](https://www.amazon.fr/Growing-Object-Oriented-Software-Guided-Tests/dp/0321503627)** — Steve Freeman, Nat Pryce
   *La* référence sur le TDD outside-in et la conception orientée objet pilotée par les tests.

2. **[Refactoring: Improving the Design of Existing Code (2nd ed.)](https://www.amazon.fr/Refactoring-Improving-Design-Existing-Code/dp/0134757599)** — Martin Fowler
   Catalogue de refactorings nommés, avec mécanique pas à pas. Édition 2018 en JavaScript.

3. **[Working Effectively with Legacy Code](https://www.amazon.fr/Working-Effectively-Legacy-Code-Feathers/dp/0131177052)** — Michael Feathers
   Comment introduire des tests sur du code qui n'en a jamais eu, technique des *seams*, refactorings sûrs.

4. **[Test Driven Development: By Example](https://www.amazon.fr/Test-Driven-Development-Kent-Beck/dp/0321146530)** — Kent Beck
   Le livre fondateur du TDD, court et démonstratif, par l'inventeur de la pratique.

5. **[xUnit Test Patterns: Refactoring Test Code](https://www.amazon.fr/xUnit-Test-Patterns-Refactoring-Code/dp/0131495054)** — Gerard Meszaros
   Le catalogue des *test smells* et des patrons de tests propres : *fixtures*, *test doubles*, *fragile tests*.

### Pratique — qualité et tests

- **[Coding Dojo](https://codingdojo.org/)** : résoudre un problème à plusieurs en TDD strict.
- **Katas classiques** : Bowling Game, Roman Numerals, Gilded Rose, Tennis Refactoring (voir la section dédiée plus bas).
- **Mob / pair programming** régulier sur du code de production.
- **Mesurer** la couverture de tests d'un projet réel et identifier les zones aveugles.

### Au sortir de l'étape Qualité et tests, vous savez

- écrire un test avant le code de production, quel que soit le contexte ;
- refactorer une fonction de 200 lignes sans la casser ;
- ajouter une fonctionnalité à un module non testé sans le réécrire de zéro.

## 3. Conception et architecture

**Objectif** : structurer un système au-delà de la classe ou du module, comprendre les compromis architecturaux et les frontières de domaine.

### Livres — conception et architecture

1. **[Domain-Driven Design: Tackling Complexity in the Heart of Software](https://www.amazon.fr/Domain-Driven-Design-Complexity-Software/dp/0321125215)** — Eric Evans (« livre rouge »)
   Le fondateur du DDD : langage ubiquitaire, *bounded contexts*, modélisation tactique et stratégique.

2. **[Implementing Domain-Driven Design](https://www.amazon.fr/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)** — Vaughn Vernon (« livre jaune »)
   Le pendant pratique d'Evans, avec du code et des recettes.

3. **[Clean Architecture: A Craftsman's Guide to Software Structure and Design](https://www.amazon.fr/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164)** — Robert C. Martin
   Synthèse des principes de découplage : SOLID, frontières, indépendance vis-à-vis du framework et de la base de données.

4. **[Designing Data-Intensive Applications](https://www.amazon.fr/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321)** — Martin Kleppmann
   Tout ce qu'il faut savoir sur le stockage, la cohérence, la réplication, le streaming et la résilience.

5. **[Building Evolutionary Architectures: Support Constant Change](https://www.amazon.fr/Building-Evolutionary-Architectures-Support-Constant/dp/1491986360)** — Neal Ford, Rebecca Parsons, Patrick Kua
   Architecture conçue pour évoluer, *fitness functions*, tests d'architecture.

6. **[Team Topologies: Organizing Business and Technology Teams for Fast Flow](https://www.amazon.fr/Team-Topologies-Organizing-Business-Technology/dp/1942788819)** — Matthew Skelton, Manuel Pais
   La conception des équipes comme conception du système (loi de Conway prise au sérieux).

### Pratique — conception et architecture

- **[System Design Primer](https://github.com/donnemartin/system-design-primer)** : exercices de conception de systèmes à grande échelle.
- **Lire l'architecture** de projets open-source dans son langage de prédilection.
- **Documenter** les décisions structurantes via des [ADR](https://adr.github.io/) (*Architecture Decision Records*).
- **Animer un Event Storming** sur un domaine que vous connaissez.

### Au sortir de l'étape Conception et architecture, vous savez

- découper un système en *bounded contexts* qui correspondent au métier ;
- choisir entre monolithe modulaire et microservices avec des arguments concrets ;
- justifier vos décisions architecturales par écrit, en explicitant les compromis.

## 4. Livraison et exploitation (DevOps)

**Objectif** : porter la qualité jusqu'en production, livrer souvent, observer ce qui tourne.

### Livres — livraison et exploitation

1. **[The Phoenix Project: A Novel About IT, DevOps, and Helping Your Business Win](https://www.amazon.fr/Phoenix-Project-DevOps-Helping-Business/dp/1942788290)** — Gene Kim, Kevin Behr, George Spafford
   Roman pédagogique qui fait comprendre les *Three Ways* du DevOps par l'histoire d'une équipe en crise.

2. **[Accelerate: The Science of Lean Software and DevOps](https://www.amazon.fr/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339)** — Nicole Forsgren, Jez Humble, Gene Kim
   Synthèse des recherches DORA : les quatre métriques (lead time, deployment frequency, MTTR, change failure rate) et leurs corrélations avec la performance d'entreprise.

3. **[Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation](https://www.amazon.fr/Continuous-Delivery-Reliable-Deployment-Automation/dp/0321601912)** — Jez Humble, David Farley
   Mécanique du *deployment pipeline*, infrastructure as code, gestion des bases de données.

4. **[Site Reliability Engineering](https://sre.google/sre-book/table-of-contents/)** — Google (gratuit en ligne)
   Disponibilité comme produit, SLI / SLO / SLA, *error budgets*, postmortems sans blâme.

### Pratique — livraison et exploitation

- **Construire son propre pipeline** sur un side-project : commit → tests → build → déploiement automatique.
- **[Kubernetes Documentation](https://kubernetes.io/docs/home/)** : l'orchestrateur de fait pour les conteneurs.
- **[The Twelve-Factor App](https://12factor.net/fr/)** : méthodologie pour des applications portables et déployables en continu.
- **Exécuter un *game day*** : couper volontairement un service pour observer la résilience du reste.

### Au sortir de l'étape Livraison et exploitation, vous savez

- mettre en place un pipeline de livraison continue depuis zéro ;
- diagnostiquer un incident en production à partir de logs, métriques et traces ;
- discuter SLO, *error budget* et coût de l'indisponibilité avec un product manager.

## Test-Driven Development en profondeur

Le TDD est plus qu'une technique de test : c'est une **boucle de feedback de conception**. Le test n'est pas la fin ; il est la pression qui pousse vers un code mieux découpé.

### Le cycle red-green-refactor

1. **Red** : écrire un test qui échoue. Si le test passe du premier coup, c'est qu'il ne testait pas grand-chose.
2. **Green** : écrire le code minimum pour faire passer le test. *Fake it till you make it.* On a le droit d'écrire le code le plus moche possible à cette étape.
3. **Refactor** : nettoyer le code et les tests, **sans ajouter de comportement**. Les tests verts sont le filet.

Trois lois de Robert Martin :
- ne pas écrire de code de production sans test rouge qui l'exige ;
- ne pas écrire plus de test qu'il n'en faut pour échouer (la non-compilation compte) ;
- ne pas écrire plus de code de production qu'il n'en faut pour passer.

### Deux écoles : Chicago (classicist) et London (mockist)

Les deux écoles sont valides. Les connaître permet de faire un choix conscient selon le contexte.

**École classique (dite « Chicago », ou « state-based »).** On part d'un test de bout en bout, on construit les objets réels au fil du test, on vérifie l'état après l'action. Le test connaît peu la structure interne. Refactoriser la structure ne casse pas les tests tant que le comportement public est stable. Référence : Kent Beck, *Test Driven Development: By Example*. Convient aux algorithmes, aux objets-valeurs, aux modèles de domaine purs.

**École londonienne (dite « mockist », ou « interaction-based »).** On part de l'extérieur, on dirige la conception par les collaborations entre objets, on remplace les collaborateurs par des *mocks* qui vérifient les interactions. Référence : Steve Freeman et Nat Pryce, *Growing Object-Oriented Software, Guided by Tests*. Convient aux objets de service, aux orchestrations, aux frontières (HTTP, queues, base de données).

**Comment choisir ?** Pour un cœur de domaine riche et stable, préférer le style Chicago : les tests survivent aux refactos. Pour un service applicatif qui orchestre des collaborateurs, le style Londres documente mieux les contrats. La plupart des codebases mûres mélangent les deux, sans complexe.

### Les tests comme feedback de conception

Si écrire un test est douloureux, le test vous dit quelque chose : trop de dépendances, trop de responsabilités, état caché, couplage. Le réflexe craft : ne pas combattre le test, écouter ce qu'il dénonce et redescendre dans le code.

### Pyramide ou trophée

La pyramide classique de Mike Cohn (beaucoup d'unitaires, quelques intégration, peu de bout-en-bout) reste un bon point de départ. Pour les applications web modernes, Kent C. Dodds propose le *testing trophy* (statique, unitaire, intégration, E2E) : la couche d'intégration y prend plus d'importance. Le bon dosage dépend du coût d'exécution et de la fiabilité des tests dans votre contexte. Le critère qui compte : un test qui échoue parle vite, et il parle juste.

## Catalogue de refactorings essentiels

Le refactoring est une activité **outillée et nommée**. Avoir le nom, c'est pouvoir le proposer en revue ou en pair sans expliquer pendant cinq minutes. Ce qui suit est un sous-ensemble du catalogue de Fowler, choisi pour son rendement immédiat.

### Extract Method (extraire une méthode)

Le plus utilisé. Transforme un bloc de code interne en méthode nommée.

Avant :
```python
def envoyer_facture(commande):
    total = 0
    for ligne in commande.lignes:
        total += ligne.quantite * ligne.prix_unitaire
    total *= 1.20  # TVA
    print(f"Facture pour {commande.client} : {total} EUR")
```

Après :
```python
def envoyer_facture(commande):
    total_ttc = calculer_total_ttc(commande)
    print(f"Facture pour {commande.client} : {total_ttc} EUR")

def calculer_total_ttc(commande):
    total_ht = sum(ligne.quantite * ligne.prix_unitaire for ligne in commande.lignes)
    return total_ht * 1.20
```

Le nom remplace le commentaire. Le code devient son propre sommaire.

### Rename (renommer)

Le refactoring le plus rentable au monde. Un bon nom économise des heures de relecture. À faire dès qu'on relit son propre code à froid : « est-ce que ce nom dit ce que ça fait, à qui ne connaît pas l'histoire ? ».

### Replace Conditional with Polymorphism (remplacer un conditionnel par du polymorphisme)

Quand un `if`/`switch` se ramifie sur un type ou un état, on peut souvent le remplacer par des classes filles qui chacune connaissent leur cas.

Avant :
```python
def cout_envoi(colis):
    if colis.type == "standard":
        return 3.50 + colis.poids * 0.5
    elif colis.type == "express":
        return 7.00 + colis.poids * 0.8
    elif colis.type == "international":
        return 15.00 + colis.poids * 1.2
```

Après :
```python
class ColisStandard:
    def cout_envoi(self):
        return 3.50 + self.poids * 0.5

class ColisExpress:
    def cout_envoi(self):
        return 7.00 + self.poids * 0.8

class ColisInternational:
    def cout_envoi(self):
        return 15.00 + self.poids * 1.2
```

L'ajout d'un nouveau type ne demande plus de modifier la fonction commune.

### Introduce Parameter Object (introduire un objet paramètre)

Quand plusieurs paramètres voyagent toujours ensemble, on en fait un objet.

Avant :
```python
def reserver(jour, mois, annee, heure_debut, heure_fin, salle):
    ...
```

Après :
```python
class CreneauReservation:
    def __init__(self, debut, fin, salle):
        self.debut = debut
        self.fin = fin
        self.salle = salle

def reserver(creneau: CreneauReservation):
    ...
```

L'objet devient le bon endroit pour porter les invariants : « la fin est après le début », « la durée est inférieure à 4 heures », etc.

### Replace Magic Number with Constant (remplacer un nombre magique par une constante)

`if duree > 86400:` devient `if duree > UNE_JOURNEE_EN_SECONDES:`. Le test reste vrai, l'intention apparaît.

### Inline (mettre en ligne)

L'inverse d'extract. Si une méthode n'apporte rien de plus que son contenu, on la dissout. Le craftsman extrait, mais sait aussi inliner quand l'abstraction n'a pas tenu ses promesses.

### Move Method / Move Field

Quand une méthode parle plus à une autre classe qu'à la sienne, on la déplace. Indice : elle utilise majoritairement les champs d'un autre objet (*feature envy*).

### Encapsulate Field / Replace Data Value with Object

Une donnée nue (`string adresse_email`) finit par être validée à plusieurs endroits. Encapsuler dans un *value object* (`AdresseEmail`) concentre les invariants et élimine les validations dupliquées.

Le réflexe à acquérir : **toujours refactorer sous filet de tests**, par micro-pas, en s'arrêtant régulièrement pour tout exécuter. Si l'IDE propose le refactoring (Rename, Extract Method, Move), s'en servir : il évite les fautes de frappe qui passent les tests.

## Katas recommandés par difficulté

Un *kata* est un exercice court, à refaire. L'enjeu n'est pas la solution mais la fluidité acquise à le résoudre, en TDD strict, en pair, en mob, dans un nouveau langage. Voici une progression.

### Niveau découverte (premiers pas en TDD)

- **FizzBuzz** ([référence](https://en.wikipedia.org/wiki/Fizz_buzz)). Le premier kata. Imprimer 1 à 100, en remplaçant les multiples de 3 par « Fizz », de 5 par « Buzz », de 15 par « FizzBuzz ». Objectif : intérioriser le cycle red-green-refactor sur un problème dont l'énoncé tient en deux lignes.
- **Leap Year** : déterminer si une année est bissextile. Petit, mais excellent pour pratiquer les cas limites (1900, 2000, 2024).
- **String Calculator** de Roy Osherove : lire une chaîne, retourner la somme. Les règles s'ajoutent par paliers, ce qui rend le kata progressif.

### Niveau intermédiaire (chaînes de tests, conception émergente)

- **Roman Numerals** : convertir un entier en chiffres romains. Excellent pour le refactoring incrémental ; on commence avec un `if` long, on finit avec une table de paires.
- **Bowling Game** d'Uncle Bob : calculer le score d'une partie de bowling. La beauté du kata est qu'une conception simpliste du début se révèle suffisante à la fin, à condition d'avoir résisté à la sur-conception.
- **Tennis Refactoring** : un code volontairement laid à refactorer sans le casser. Idéal pour s'entraîner aux mécaniques de Fowler.
- **Coffee Machine** : modélisation de commandes, tests d'interaction. Bon kata pour pratiquer le style mockist.

### Niveau confirmé (héritage, design, contraintes réelles)

- **Gilded Rose** d'Emily Bache : refactorer un code existant et ajouter une fonctionnalité, **sans casser les tests dorés** (*characterization tests*). C'est le kata legacy par excellence.
- **Mars Rover** : un robot reçoit des commandes, modifie son état, gère les obstacles. Excellent pour pratiquer les *value objects* et la séparation entre domaine et entrée/sortie.
- **Bank Kata** : tenir le compte d'un client (dépôts, retraits, relevés). Bon kata pour exercer la séparation des préoccupations et l'inversion des dépendances.
- **Game of Life** de Conway : la grille, les voisins, les règles de transition. Un kata qui invite à comparer les approches fonctionnelle et orientée objet.

### Niveau avancé (architecture, contraintes croisées)

- **Trip Service Kata** de Sandro Mancuso : refactorer un code legacy avec des dépendances statiques difficiles à isoler. Pratique des *seams* à la Feathers.
- **Diamond Kata** de Seb Rose : produire un diamant à partir d'une lettre. Court, mais redoutable pour comparer TDD bottom-up et property-based testing.
- **Lift Kata** : modélisation d'un ascenseur multi-étages avec plusieurs cabines. Conception, états, événements.

**Bonnes adresses pour des katas.** [Coding Dojo](https://codingdojo.org/), [Kata-Log](https://kata-log.rocks/), [Kata Containers (Emily Bache)](https://github.com/emilybache), [GitHub coding-katas](https://github.com/topics/coding-katas).

**Comment pratiquer un kata.** Refaire le même kata plusieurs fois, en variant la contrainte : pas de souris, pas plus de 5 lignes par méthode, en pair, dans un langage inconnu, en mob silencieux, en *ping-pong* (l'un écrit le test, l'autre le code). La contrainte révèle le geste.

## Pair programming et mob programming

Programmer ensemble n'est pas une réunion. C'est une discipline.

### Pair programming

Deux personnes, **une seule machine active**.

- Le **driver** tient le clavier. Il traduit l'intention en code.
- Le **navigator** regarde la carte : il pense au prochain test, repère les coquilles, garde l'objectif en vue.
- **On change de rôle régulièrement**, toutes les 10 à 25 minutes. Sans alternance, ce n'est plus du pair, c'est un public.

**Bénéfices.**
- Diffusion de la connaissance dans l'équipe : pas de silo, le bus factor monte.
- Revue de code permanente, en temps réel.
- Décisions de conception meilleures : deux cerveaux attrapent ce qu'un seul rate.
- Concentration accrue : on ne consulte pas son téléphone quand quelqu'un attend qu'on parle.

**Anti-patterns à connaître.**
- *Le silencieux* : l'un travaille, l'autre se tait. Ce n'est plus du pair.
- *Le dictateur* : un sénior dicte, un junior tape. C'est de la dictée, pas du pair.
- *L'écran partagé sans micro* : à distance, le partage d'écran sans audio donne du shadowing, pas du pair.
- *Le pair perpétuel* : tout faire en pair, y compris la veille technique. Le pair est une pratique, pas un dogme.

### Mob programming

Trois personnes ou plus, une seule machine. Inventé par Woody Zuill chez Hunter Industries (vers 2011). Les rôles tournent toutes les quelques minutes (souvent à la *Mob Timer*).

**Règle d'or de Llewellyn Falco** : « pour qu'une idée passe du cerveau d'un membre du mob à l'ordinateur, elle doit passer par les mains de quelqu'un d'autre ». C'est cette règle qui fait la pédagogie : le savoir circule par la voix, pas par le clavier.

**Quand mobber.**
- Démarrage d'un nouveau projet ou d'un nouveau module : aligner toute l'équipe.
- Sujet difficile, à fort impact : mieux vaut une demi-journée à cinq qu'une semaine à un.
- Onboarding d'un nouvel arrivant.
- Refacto majeure d'un cœur de domaine.

**Quand ne pas mobber.**
- Tâches mécaniques, configurations longues : le mob s'ennuie.
- Quand la fatigue est là : le mob pompe de l'énergie, il ne s'en crée pas.

**Anti-patterns du mob.**
- Pas de timer : un seul finit par tout faire.
- Aucune préparation : le mob se transforme en réunion d'analyse.
- Recadrage par hiérarchie : le sénior contredit publiquement chaque idée. Le mob ferme les bouches.

## La revue de code (code review) bien faite

Une revue de PR (ou MR) est **un acte de soin** envers le code et son auteur. Elle ne se réduit pas à pointer des défauts.

### Ce qu'on attend d'une bonne PR à relire

- Un titre qui dit l'intention.
- Une description : pourquoi, quoi, comment tester, captures s'il faut.
- Un *diff* qui tient à l'écran. Une PR de 800 lignes ne se relit pas, elle se survole.
- Des commits propres, ou un *squash* à la fusion.
- Des tests verts en CI avant qu'on commence à lire.

### Ce qu'on attend d'un bon relecteur

- **Lire le contexte** avant le diff : ticket, PR description, commit messages.
- **Distinguer trois niveaux** dans ses commentaires : bloquant, suggestion, question.
- **Préférer les questions aux assertions** : « pourquoi ce choix ? » est plus ouvert que « il fallait faire l'inverse ».
- **Approuver vite** quand c'est bon. Une PR qui dort un jour est une PR qui mourra.
- **Demander des changements rarement** ; argumenter à chaque fois.

### La grille AABBCC

Une grille mémo simple, à parcourir mentalement sur chaque PR.

- **A** comme **Architecture** : la PR respecte-t-elle les frontières et les couches ? Pas de fuite d'infrastructure dans le domaine ?
- **A** comme **API** : les contrats publics (signature, route HTTP, événement) restent-ils stables, documentés, rétro-compatibles ?
- **B** comme **Bugs** : cas limites, valeurs nulles, dates, fuseaux horaires, concurrence, idempotence.
- **B** comme **Behaviour** : le test vérifie-t-il vraiment le comportement attendu, ou juste l'implémentation ?
- **C** comme **Clarity** : nommage, structure, lisibilité du diff. Un développeur arrivant demain comprendrait-il ?
- **C** comme **Coverage** : zones non testées, tests fragiles, *test smells*.

### Bienveillance : la règle non négociable

La revue est *publique* (toute l'équipe lit). Un commentaire mal tourné peut blesser durablement. Quelques garde-fous :

- Critiquer le code, jamais la personne. « Cette méthode mélange deux responsabilités » plutôt que « tu as mélangé… ».
- Reconnaître ce qui est bon. Une PR n'est pas qu'un sac de défauts ; nommer un bon test, un bon découpage, fait grandir.
- Préférer le pair à la revue quand les remarques s'accumulent. Au-delà de cinq allers-retours, le canal écrit ne suffit plus.
- Souligner ce qui peut attendre : « *nit*, hors scope » est une politesse qui sauve des heures.

## Travailler avec du code legacy

Pour Michael Feathers, est *legacy* tout code **sans tests automatiques**. Pas tout code ancien : un code de 2010 bien testé est plus sain qu'un microservice écrit hier sans tests.

### Caractérisation : le filet avant la lame

Le **test de caractérisation** (*characterization test*, parfois *golden master*) ne vérifie pas un comportement attendu, il **fige le comportement actuel**, qu'il soit juste ou non. Mécanique :

1. Choisir un point d'entrée à isoler.
2. Lui donner une entrée.
3. Capturer la sortie observée.
4. Écrire un test qui assert sur cette sortie.
5. Itérer pour augmenter la couverture jusqu'à pouvoir refactorer sereinement.

C'est désagréable parce qu'on enchâsse même des bugs. C'est précieux parce que le filet existe avant qu'on touche au code. Une fois les tests verts, on peut refactorer ; on remplacera ensuite les tests de caractérisation par de vrais tests de comportement.

### Les *seams* (coutures)

Concept central de Feathers : une *seam* est un endroit où l'on peut **changer de comportement sans modifier le code** (par injection, héritage, lien dynamique, etc.). Identifier les seams permet d'introduire des doublures de test sans tout réécrire.

### Sprout method / Sprout class

Plutôt que d'éditer une grosse fonction non testée, **on lui greffe** une nouvelle méthode (ou classe) **bien testée**, et la fonction d'origine appelle cette greffe. Le code neuf est propre, le code ancien reste isolé. Avec le temps, la greffe grossit, l'ancien rétrécit.

### Wrap method / Wrap class

On *enveloppe* un appel existant : la méthode publique change de nom, on en crée une nouvelle qui appelle l'ancienne plus une logique additionnelle. Permet d'ajouter du comportement (logging, métriques, validation) sans toucher au cœur risqué.

### Strangler Fig (figuier étrangleur)

Patron popularisé par Martin Fowler en 2004, sur la métaphore du figuier qui pousse autour de son hôte et finit par le remplacer. On ne réécrit pas le système legacy ; on **construit le nouveau autour**, on bascule trafic et fonctionnalités progressivement, jusqu'à pouvoir éteindre l'ancien. Convient aux migrations lourdes, sans *big bang*.

### Anti-corruption layer (couche anti-corruption)

DDD. Quand un nouveau modèle doit interagir avec un legacy mal modélisé, on insère une couche de traduction qui empêche les concepts pourris de remonter dans le neuf. C'est une frontière, et elle est volontairement ennuyeuse.

### Heuristiques quotidiennes

- **Règle du boy-scout** : laisser le code un peu meilleur qu'on ne l'a trouvé. Un nom, une extraction, un test ; pas de grand soir.
- **Mikado method** : pour un changement complexe, on tente le changement, on note ce qui résiste, on backtrack, on s'attaque aux dépendances en partant des feuilles. Permet de garder le code compilable et testable à chaque pas.
- **Refuser la réécriture totale**. Joel Spolsky, Things You Should Never Do, Part I (2000) : la réécriture est presque toujours plus longue que prévu et perd tout l'apprentissage capté dans le legacy.

## Évolution de carrière du craftsman

Le craft n'oblige pas à devenir manager. Il y a au moins deux trajectoires.

### Le développeur en T (T-shaped)

Profondeur sur un domaine ou une stack, **largeur sur les sujets adjacents** : produit, ops, data, sécurité. Le T se construit en cinq à dix ans par exposition volontaire à des sujets connexes (rotations, side projects, contributions open source).

### Le leadership technique sans management

Le craft a forgé une voie distincte de l'ascension hiérarchique :

- **Tech lead** : porte la qualité technique d'une équipe, sans encadrer formellement les personnes. Anime, mentore, arbitre les compromis.
- **Staff engineer** : impact transverse à plusieurs équipes. Référence : *Staff Engineer: Leadership beyond the management track*, Will Larson.
- **Principal engineer** : impact à l'échelle de l'organisation, parfois de l'industrie. Architecture stratégique, R&D, choix technologiques majeurs.
- **Distinguished engineer** : très rare, généralement réservé aux grandes structures.

Ces titres ne sont pas universels ; chaque entreprise les définit. Ce qui importe, c'est la **levier** : à quel point votre travail rend les autres meilleurs ? Plus l'impact est large, plus on monte sur cette trajectoire.

### Trajectoire managériale

Compatible avec le craft. Le bon manager technique reste légitime sur le code parce qu'il en lit, en écrit (peu mais régulièrement), et garde le respect des praticiens. Lectures utiles : *The Manager's Path* de Camille Fournier, *An Elegant Puzzle* de Will Larson.

### Lectures pour penser sa carrière

- *Software Craftsmanship* — Sandro Mancuso (manifeste vivant).
- *The Pragmatic Programmer* — Hunt & Thomas (toujours).
- *A Philosophy of Software Design* — John Ousterhout (synthèse moderne).
- *Staff Engineer* — Will Larson.
- *The Manager's Path* — Camille Fournier (pour comprendre l'autre voie, même si on ne la prend pas).

## Communautés et événements

Apprendre seul a ses limites. La communauté du craftsmanship est active en France et dans le monde francophone. Y participer est, à terme, le meilleur accélérateur connu.

### Communautés francophones

- **[Software Craftsmanship Communauté Francophone](https://www.craftsmanship.fr/)** : annuaire des meet-ups francophones.
- **Software Crafters** : meet-ups à Paris, Lyon, Bordeaux, Nantes, Toulouse, Lille, Bruxelles, Genève, Montréal.
- **[AFUP](https://afup.org/)** : association française des utilisateurs de PHP, événements et meetups en région.
- **[Codeurs en Seine](https://www.codeursenseine.com/)** : conférence annuelle à Rouen, ambiance familiale et pointue.
- **GDS / Lecture clubs** : groupes de lecture (DDD, Refactoring, GOOS) qui se forment régulièrement dans les villes craft.

### Conférences à viser

- **[SoCraTes](https://www.socrates-conference.de/)** : *unconference* internationale de référence, plusieurs déclinaisons (FR, BE, CH, DE, UK). Format *open space*, pas de programme à l'avance, beaucoup de mob et de katas.
- **[NewCrafts](https://ncrafts.io/)** : Paris, début juin. Très orienté craft, format conférence + ateliers.
- **[Devoxx France](https://www.devoxx.fr/)** : généraliste, fort axe craft.
- **[Mix-IT](https://mixitconf.org/)** : Lyon, agile et craft.
- **[FrenchKit](https://frenchkit.fr/)** : iOS / Swift à Paris, mais l'esprit craft y circule.
- **[Kata weekend](https://katawe.com/)** : week-ends de pratique pure, en mob et pair.
- **[Devoxx BE](https://devoxx.be/)** : la grande sœur belge.

### Communautés et auteurs en ligne

- [Sandi Metz (YouTube et site)](https://sandimetz.com/) : conférences sur l'objet, la duplication, l'héritage. Lectures vivement conseillées.
- [Kent Beck (Substack)](https://tidyfirst.substack.com/) : essais courts sur la conception et le *Tidy First*.
- [Ron Jeffries](https://ronjeffries.com/) : un des signataires originaux du Manifeste Agile, écrit chaque semaine, exemples de TDD au long cours.
- [Martin Fowler](https://martinfowler.com/) : la bibliothèque de référence sur le refactoring, les patterns, les ADR.
- [Dave Farley — Continuous Delivery (YouTube)](https://www.youtube.com/@ContinuousDelivery) : co-auteur de *Continuous Delivery*, contenu hebdomadaire.
- [Emily Bache (YouTube et katas)](https://github.com/emilybache) : enseignante TDD, mainteneuse de plusieurs katas de référence.

## Anti-patterns du faux craft

La forme sans le fond ne fait pas le métier. Voici les confusions à éviter.

### Le *cargo cult* (culte du cargo)

Reproduire les rituels d'une pratique sans en comprendre le mécanisme. Source : Richard Feynman, *Cargo Cult Science* (1974). Symptômes : on adopte un outil parce qu'une grande entreprise l'utilise, sans poser le problème ; on importe un framework de tests parce qu'il est à la mode, sans s'interroger sur ses propres tests.

### « Nous faisons de l'agile parce que nous avons un stand-up »

L'agile, ce n'est pas un Daily ; le craft, ce n'est pas un kata par mois. Les rituels existent pour servir un objectif (synchronisation, apprentissage, qualité). Sans cet objectif, ce sont des charges. Si le stand-up dure quarante minutes et n'aide personne à avancer, on l'arrête.

### TDD sans pratiquer le refactor

Écrire le test, écrire le code, sauter le refactor. Le code se dégrade, les tests deviennent rigides, l'équipe finit par dire « le TDD ne marche pas ici ». La phase oubliée est celle qui paye sur la durée.

### Le *cleanivore*

Réécrire à coups de SOLID, de patterns, sans demande métier. Le code « propre » ne livre pas : seul le bon code livré fait du logiciel. *Clean Code* est un guide, pas une obligation morale. Le pragmatisme prime.

### Outils sans principes

Acheter un outil de qualité, un coverage tracker, un bug tracker, sans culture d'équipe. L'outil donne des chiffres, l'équipe ne les regarde pas, ou les regarde mal. Les outils servent une discipline ; ils ne la créent pas.

### La revue de code policière

Tout commentaire est bloquant, le ton est sec, les PR mettent trois jours. Les développeurs apprennent à minimiser leurs PR pour réduire la surface d'attaque. La qualité baisse, le rythme aussi. Une revue exigeante doit rester rapide et bienveillante (voir AABBCC).

### Le mob d'une seule voix

Le mob où le sénior dicte. Faux mob : c'est un tutorat à plusieurs spectateurs. Le mob ne fonctionne que si toutes les voix portent.

### Le kata exhibition

Faire un kata pour briller, pas pour apprendre. Symptôme : on choisit un kata déjà connu, on déroule la solution mémorisée, on ne tente rien de nouveau. La pratique délibérée demande de viser un point d'inconfort.

### Le « senior à 18 mois »

Promotion à un titre senior par pénurie ou par négociation, sans la maturité associée. Pas un drame ; juste à signaler honnêtement, pour éviter l'illusion. Le titre suit la maîtrise, pas l'inverse.

## Habitudes du quotidien

Les livres et les conférences donnent le matériel ; ce sont les habitudes qui créent la maîtrise.

- **Lire du code** une heure par semaine, pas le sien. Un projet open-source dans son langage.
- **Prendre une demi-heure** après chaque tâche pour relire son propre code à froid.
- **Faire de la veille** ciblée : un seul flux, lu régulièrement, vaut mieux que dix abandonnés.
- **Tenir un journal** des décisions techniques avec leur contexte et leur résultat à six mois.
- **Enseigner** ce que vous venez d'apprendre : un *brown bag*, un article, un kata animé. La transmission consolide la compréhension.
- **Refactorer en cours de route** plutôt qu'en grande session séparée. *Tidy first*, comme le formule Kent Beck.
- **Pratiquer la rétro** au-delà du sprint : sur soi-même, en fin de mois. Trois lignes : ce qui m'a appris, ce qui m'a coûté, ce que je teste le mois prochain.

## Pour aller plus loin

- [Manifesto for Software Craftsmanship (2009)](https://manifesto.softwarecraftsmanship.org/)
- [Manifesto for Agile Software Development (2001)](https://agilemanifesto.org/iso/fr/manifesto.html)
- [Principes SOLID — Robert C. Martin](https://en.wikipedia.org/wiki/SOLID)
- [Refactoring Guru — Design patterns et refactoring](https://refactoring.guru/)
- [The Twelve-Factor App](https://12factor.net/) : applications modernes
- [DORA — State of DevOps reports](https://dora.dev/research/)
- [Kata-Log](https://kata-log.rocks/) : annuaire de katas avec tags par compétence
- [martinfowler.com / refactoring catalog](https://refactoring.com/catalog/) : référence en ligne du catalogue de Fowler
- [c2.com (le tout premier wiki de Ward Cunningham)](https://wiki.c2.com/) : sources historiques sur la dette technique, l'extreme programming, les patterns
- Chaîne YouTube de [Continuous Delivery (Dave Farley)](https://www.youtube.com/@ContinuousDelivery)

## Contribuer

Pour proposer une ressource, corriger une erreur ou partager un retour d'expérience, ouvrez une *Pull Request* ou une *Issue*. Toutes les contributions sont les bienvenues.

## Licence

Distribué sous licence [MIT](LICENSE).

## Auteur

**Tansoftware - Tanguy Chénier** · [LinkedIn](https://www.linkedin.com/in/tanguy-chenier) · [Tan-Software](https://github.com/Tan-Software) · [Compte personnel (derniers outils)](https://github.com/tanguychenier) · [tansoftware.com](https://www.tansoftware.com)
