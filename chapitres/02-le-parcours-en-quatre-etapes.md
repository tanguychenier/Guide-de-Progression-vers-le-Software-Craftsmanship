[← Fondations et vocabulaire du craft](01-fondations-et-vocabulaire-du-craft.md) · [↑ Sommaire](../README.md#table-des-matières) · [Le Test-Driven Development en profondeur →](03-le-test-driven-development-en-profondeur.md)

# 2. Le parcours en quatre étapes

## 1. Fondamentaux du développement

**Objectif** : disposer d'un socle solide en pratiques pragmatiques, lisibilité du code et professionnalisme.

> **Que veut dire « heuristique » ?**
> Une heuristique est une règle pratique, pas une loi absolue : un raccourci de bon sens qui marche dans la plupart des cas, sans garantie parfaite. Comparaison du quotidien : « si le ciel est gris le matin, prends un parapluie ». Ce n'est pas toujours vrai, mais c'est un bon réflexe. La plupart des conseils de ce texte sont des heuristiques, pas des dogmes.

### Livres : fondamentaux

1. **[The Pragmatic Programmer: From Journeyman to Master](https://www.amazon.fr/Pragmatic-Programmer-Journeyman-Master/dp/020161622X)**, Andrew Hunt, David Thomas
   La référence sur les bonnes pratiques transverses : DRY, orthogonalité, programmation défensive, automatisation. La 20e édition anniversaire (2019) modernise les exemples.

   > **Que veulent dire « DRY », « orthogonalité », « programmation défensive » ?**
   > **DRY** (*Don't Repeat Yourself*, ne vous répétez pas) : chaque information ou règle ne doit exister qu'à un seul endroit du code, sinon une modification oblige à corriger plusieurs copies et on en oublie toujours une. **Orthogonalité** : organiser le code en parties indépendantes qui ne se gênent pas, de sorte que modifier l'une ne casse pas les autres. Comparaison du quotidien : les boutons d'une télécommande sont orthogonaux : changer le volume n'éteint pas la télévision. **Programmation défensive** : écrire du code qui se méfie des données reçues (vérifier qu'une valeur n'est pas absente, qu'un nombre n'est pas négatif) pour éviter qu'une erreur lointaine ne fasse tout planter.

2. **[Clean Code: A Handbook of Agile Software Craftsmanship](https://www.amazon.fr/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)**, Robert C. Martin
   Heuristiques concrètes pour écrire du code lisible : nommage, fonctions courtes, commentaires utiles, gestion des erreurs.

3. **[The Clean Coder: A Code of Conduct for Professional Programmers](https://www.amazon.fr/Clean-Coder-Conduct-Professional-Programmers/dp/0137081073)**, Robert C. Martin
   La face professionnelle du métier : engagements, estimations, refus quand c'est nécessaire, gestion du temps et de la pression.

4. **[Software Craftsmanship: Professionalism, Pragmatism, Pride](https://www.amazon.fr/Software-Craftsmanship-Professionalism-Pragmatism-Pride/dp/0134052501)**, Sandro Mancuso
   Sandro Mancuso, fondateur de la London Software Craftsmanship Community, raconte le mouvement de l'intérieur : ce que signifie le craft, comment il se transmet, comment il s'incarne en entreprise.

### Pratique : fondamentaux

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

### Livres : qualité et tests

1. **[Growing Object-Oriented Software, Guided by Tests](https://www.amazon.fr/Growing-Object-Oriented-Software-Guided-Tests/dp/0321503627)**, Steve Freeman, Nat Pryce
   *La* référence sur le TDD outside-in et la conception orientée objet pilotée par les tests.

   > **Que veulent dire « TDD outside-in » et « orienté objet » ?**
   > **TDD outside-in** (de l'extérieur vers l'intérieur) : on commence par écrire le test du comportement visible par l'utilisateur, puis on descend progressivement vers les détails internes, en laissant les tests guider la découpe. **Orienté objet** : un style de programmation où l'on regroupe les données et les actions qui les concernent dans des « objets » (par exemple un objet *Commande* qui sait calculer son total). Comparaison du quotidien : plutôt qu'une grosse liste d'instructions, on organise le programme comme une équipe d'employés ayant chacun un rôle clair.

2. **[Refactoring: Improving the Design of Existing Code (2nd ed.)](https://www.amazon.fr/Refactoring-Improving-Design-Existing-Code/dp/0134757599)**, Martin Fowler
   Catalogue de refactorings nommés, avec mécanique pas à pas. Édition 2018 en JavaScript.

3. **[Working Effectively with Legacy Code](https://www.amazon.fr/Working-Effectively-Legacy-Code-Feathers/dp/0131177052)**, Michael Feathers
   Comment introduire des tests sur du code qui n'en a jamais eu, technique des *seams*, refactorings sûrs.

4. **[Test Driven Development: By Example](https://www.amazon.fr/Test-Driven-Development-Kent-Beck/dp/0321146530)**, Kent Beck
   Le livre fondateur du TDD, court et démonstratif, par l'inventeur de la pratique.

5. **[xUnit Test Patterns: Refactoring Test Code](https://www.amazon.fr/xUnit-Test-Patterns-Refactoring-Code/dp/0131495054)**, Gerard Meszaros
   Le catalogue des *test smells* et des patrons de tests propres : *fixtures*, *test doubles*, *fragile tests*.

   > **Que veulent dire « fixtures » et « test doubles » ?**
   > Une **fixture** est le décor d'un test : les données et objets préparés avant de lancer la vérification (par exemple un client fictif avec un panier rempli). Un **test double** (doublure de test) est un faux objet qui remplace une vraie dépendance pendant le test, comme une doublure remplace un acteur pour une cascade. On l'utilise quand la vraie chose est lente, coûteuse ou imprévisible (une vraie base de données, un vrai paiement bancaire). Les mocks, vus plus loin, sont une sorte de doublure.

### Pratique : qualité et tests

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

### Livres : conception et architecture

1. **[Domain-Driven Design: Tackling Complexity in the Heart of Software](https://www.amazon.fr/Domain-Driven-Design-Complexity-Software/dp/0321125215)**, Eric Evans (« livre rouge »)
   Le fondateur du DDD : langage ubiquitaire, *bounded contexts*, modélisation tactique et stratégique.

   > **Que veut dire « DDD » et « langage ubiquitaire » ?**
   > **DDD** (*Domain-Driven Design*, conception pilotée par le domaine) est une manière de concevoir un logiciel en partant du métier qu'il sert (le « domaine ») plutôt que de la technique. On modélise le code avec les mêmes mots que les experts métier. Le **langage ubiquitaire** est justement ce vocabulaire commun, partagé par les développeurs et les experts du domaine, utilisé à la fois dans les discussions et dans le code. Comparaison du quotidien : si une banque parle de « découvert autorisé », le code doit contenir un concept nommé `DecouvertAutorise`, pas un vague `limite2`. Ainsi tout le monde se comprend.

2. **[Implementing Domain-Driven Design](https://www.amazon.fr/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)**, Vaughn Vernon (« livre jaune »)
   Le pendant pratique d'Evans, avec du code et des recettes.

3. **[Clean Architecture: A Craftsman's Guide to Software Structure and Design](https://www.amazon.fr/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164)**, Robert C. Martin
   Synthèse des principes de découplage : SOLID, frontières, indépendance vis-à-vis du framework et de la base de données.

   > **Que veut dire « SOLID » ?**
   > SOLID est un moyen mnémotechnique pour cinq principes de conception orientée objet, formulés par Robert C. Martin. Chacun limite les dégâts d'une future modification.
   > - **S**, *Single Responsibility* (responsabilité unique) : une classe ne fait qu'une seule chose, pour une seule raison de changer.
   > - **O**, *Open/Closed* (ouvert/fermé) : on peut ajouter un comportement sans modifier le code existant, en ajoutant du neuf à côté.
   > - **L**, *Liskov Substitution* (substitution de Liskov) : une sous-classe doit pouvoir remplacer sa classe parente sans surprise. Comparaison : un canard en plastique qui « est un canard » mais ne nage pas casse cette règle.
   > - **I**, *Interface Segregation* (ségrégation des interfaces) : mieux vaut plusieurs petits contrats ciblés qu'un gros contrat fourre-tout qui force à implémenter des choses inutiles.
   > - **D**, *Dependency Inversion* (inversion des dépendances) : le code métier important ne dépend pas des détails techniques ; ce sont les détails qui s'adaptent à lui. Approfondi plus loin.

4. **[Designing Data-Intensive Applications](https://www.amazon.fr/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321)**, Martin Kleppmann
   Tout ce qu'il faut savoir sur le stockage, la cohérence, la réplication, le streaming et la résilience.

5. **[Building Evolutionary Architectures: Support Constant Change](https://www.amazon.fr/Building-Evolutionary-Architectures-Support-Constant/dp/1491986360)**, Neal Ford, Rebecca Parsons, Patrick Kua
   Architecture conçue pour évoluer, *fitness functions*, tests d'architecture.

6. **[Team Topologies: Organizing Business and Technology Teams for Fast Flow](https://www.amazon.fr/Team-Topologies-Organizing-Business-Technology/dp/1942788819)**, Matthew Skelton, Manuel Pais
   La conception des équipes comme conception du système (loi de Conway prise au sérieux).

   > **Que veut dire « loi de Conway » ?**
   > Énoncée par Melvin Conway en 1968 : un système logiciel finit par ressembler à la structure de communication de l'organisation qui le construit. Comparaison du quotidien : si quatre équipes qui se parlent peu écrivent un compilateur, il aura tendance à se découper en quatre morceaux mal raccordés. La conséquence pratique : pour obtenir une certaine architecture, organisez d'abord les équipes en conséquence.

### Pratique : conception et architecture

- **[System Design Primer](https://github.com/donnemartin/system-design-primer)** : exercices de conception de systèmes à grande échelle.
- **Lire l'architecture** de projets open-source dans son langage de prédilection.
- **Documenter** les décisions structurantes via des [ADR](https://adr.github.io/) (*Architecture Decision Records*).
- **Animer un Event Storming** sur un domaine que vous connaissez.

> **Que veut dire « Event Storming » ?**
> L'*Event Storming* (tempête d'événements) est un atelier collaboratif inventé par Alberto Brandolini : on réunit développeurs et experts métier devant un grand mur, et chacun colle des notes adhésives représentant les événements importants du métier (« commande payée », « colis expédié »), dans l'ordre, pour découvrir ensemble comment le domaine fonctionne réellement. Comparaison du quotidien : reconstituer collectivement le déroulé d'un mariage en plaçant les étapes sur une frise, pour repérer qui fait quoi et quand.

### Au sortir de l'étape Conception et architecture, vous savez

- découper un système en *bounded contexts* qui correspondent au métier ;
- choisir entre monolithe modulaire et microservices avec des arguments concrets ;
- justifier vos décisions architecturales par écrit, en explicitant les compromis.

## 4. Livraison et exploitation (DevOps)

**Objectif** : porter la qualité jusqu'en production, livrer souvent, observer ce qui tourne.

> **Que veulent dire « production », « DevOps », « pipeline » ?**
> La **production** (souvent « la prod ») est l'environnement réel où tourne le logiciel utilisé par les vraies personnes, par opposition aux environnements de test. Une erreur en production touche des utilisateurs réels. **DevOps** est la contraction de *Development* (développement) et *Operations* (exploitation, c'est-à-dire faire tourner et surveiller les serveurs) : un mouvement qui réunit ces deux métiers longtemps séparés, pour que ceux qui écrivent le code participent aussi à sa mise en service. Un **pipeline** (chaîne de traitement) est la suite automatisée d'étapes par lesquelles passe chaque modification : compilation, tests, puis déploiement. Comparaison du quotidien : une chaîne de montage où le code avance d'un poste à l'autre, chaque poste vérifiant quelque chose avant de laisser passer.

### Livres : livraison et exploitation

1. **[The Phoenix Project: A Novel About IT, DevOps, and Helping Your Business Win](https://www.amazon.fr/Phoenix-Project-DevOps-Helping-Business/dp/1942788290)**, Gene Kim, Kevin Behr, George Spafford
   Roman pédagogique qui fait comprendre les *Three Ways* du DevOps par l'histoire d'une équipe en crise.

2. **[Accelerate: The Science of Lean Software and DevOps](https://www.amazon.fr/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339)**, Nicole Forsgren, Jez Humble, Gene Kim
   Synthèse des recherches DORA : les quatre métriques (lead time, deployment frequency, MTTR, change failure rate) et leurs corrélations avec la performance d'entreprise.

3. **[Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation](https://www.amazon.fr/Continuous-Delivery-Reliable-Deployment-Automation/dp/0321601912)**, Jez Humble, David Farley
   Mécanique du *deployment pipeline*, infrastructure as code, gestion des bases de données.

4. **[Site Reliability Engineering](https://sre.google/sre-book/table-of-contents/)**, Google (gratuit en ligne)
   Disponibilité comme produit, SLI / SLO / SLA, *error budgets*, postmortems sans blâme.

   > **Que veulent dire « SRE », « SLI / SLO / SLA » et « postmortem sans blâme » ?**
   > **SRE** (*Site Reliability Engineering*, ingénierie de la fiabilité des sites) est une discipline née chez Google qui traite la fiabilité d'un service comme une fonctionnalité à part entière, avec des mesures et des objectifs chiffrés. Les trois sigles suivants encadrent justement cette fiabilité. **SLI** (*Service Level Indicator*, indicateur de niveau de service) : une mesure concrète, par exemple le pourcentage de requêtes qui répondent en moins d'une seconde. **SLO** (*Service Level Objective*, objectif de niveau de service) : la cible qu'on se fixe sur cet indicateur, par exemple « 99,9 % des requêtes en moins d'une seconde ». **SLA** (*Service Level Agreement*, accord de niveau de service) : l'engagement contractuel envers le client, avec des pénalités s'il n'est pas tenu. Un **postmortem sans blâme** est le compte rendu écrit après un incident, qui cherche les causes du problème dans le système et non un coupable, pour que chacun ose dire la vérité et que l'équipe apprenne réellement.

### Pratique : livraison et exploitation

- **Construire son propre pipeline** sur un side-project : commit → tests → build → déploiement automatique.

> **Que veulent dire « conteneur » et « orchestrateur » (Kubernetes) ?**
> Un **conteneur** est un colis logiciel qui emballe une application avec tout ce dont elle a besoin pour tourner (bibliothèques, configuration), de sorte qu'elle fonctionne à l'identique sur n'importe quelle machine. Comparaison du quotidien : un conteneur maritime standardisé se charge sur n'importe quel bateau ou camion sans souci de son contenu. Un **orchestrateur** comme **Kubernetes** est le chef d'orchestre qui démarre, arrête, répartit et redémarre automatiquement des centaines de ces conteneurs sur un parc de serveurs, sans intervention humaine permanente.

- **[Kubernetes Documentation](https://kubernetes.io/docs/home/)** : l'orchestrateur de fait pour les conteneurs.
- **[The Twelve-Factor App](https://12factor.net/fr/)** : méthodologie pour des applications portables et déployables en continu.
- **Exécuter un *game day*** : couper volontairement un service pour observer la résilience du reste.

### Au sortir de l'étape Livraison et exploitation, vous savez

- mettre en place un pipeline de livraison continue depuis zéro ;
- diagnostiquer un incident en production à partir de logs, métriques et traces ;
- discuter SLO, *error budget* et coût de l'indisponibilité avec un product manager.

---

[← Fondations et vocabulaire du craft](01-fondations-et-vocabulaire-du-craft.md) · [↑ Sommaire](../README.md#table-des-matières) · [Le Test-Driven Development en profondeur →](03-le-test-driven-development-en-profondeur.md)
