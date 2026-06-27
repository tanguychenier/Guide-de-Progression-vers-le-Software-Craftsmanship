# Guide de progression vers le Software Craftsmanship

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) [![Lang](https://img.shields.io/badge/Lang-Français-005EB8.svg)](#) [![Topic](https://img.shields.io/badge/Topic-Software%20Craftsmanship-brightgreen.svg)](#) [![Made with Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg)](https://www.markdownguide.org/)

Le *Software Craftsmanship* (en français : artisanat du logiciel) désigne une posture professionnelle plutôt qu'une méthode.

> **Que veut dire « Software Craftsmanship » ?**
> *Software* signifie « logiciel ». *Craftsmanship* vient de *craft*, le métier manuel, l'artisanat. Un *craftsman* est un artisan : la personne qui connaît son métier au point de signer son travail sans rougir. Comparaison du quotidien : un bon menuisier ne se contente pas qu'une étagère tienne au mur ; il soigne aussi les coupes invisibles à l'arrière, parce que c'est ainsi qu'on reconnaît le travail bien fait. L'artisan du logiciel applique la même exigence au code que personne ne verra directement.

Cette posture a été formalisée par le [Manifesto for Software Craftsmanship](https://manifesto.softwarecraftsmanship.org/) (2009). Elle tient en trois engagements : tendre vers la maîtrise, livrer du logiciel qu'on est fier de signer, transmettre son savoir aux autres.

Le parcours se découpe en étapes, chacune centrée sur une dimension précise. Elles se suivent dans l'ordre ou se piochent selon le contexte. Comptez plusieurs mois par étape pour lire, pratiquer, intégrer, car une compétence technique ne s'acquiert pas par la seule lecture : elle se grave par la répétition.

Les exercices se vivent en équipe, en *coding dojo* (séance d'entraînement collective, définie plus bas) ou en mob (programmation en groupe). Le texte qui suit pose le décor et donne le vocabulaire.

## Table des matières

1. [Fondations et vocabulaire du craft](chapitres/01-fondations-et-vocabulaire-du-craft.md)
   - [Glossaire de référence](chapitres/01-fondations-et-vocabulaire-du-craft.md#glossaire-de-référence)
   - [Le Manifeste du Software Craftsmanship](chapitres/01-fondations-et-vocabulaire-du-craft.md#le-manifeste-du-software-craftsmanship)
   - [Les racines XP : d'où vient le craft](chapitres/01-fondations-et-vocabulaire-du-craft.md#les-racines-xp-doù-vient-le-craft)
   - [Parcours junior, confirmé, senior](chapitres/01-fondations-et-vocabulaire-du-craft.md#parcours-junior-confirmé-senior)
2. [Le parcours en quatre étapes](chapitres/02-le-parcours-en-quatre-etapes.md)
   - [1. Fondamentaux du développement](chapitres/02-le-parcours-en-quatre-etapes.md#1-fondamentaux-du-développement)
   - [2. Qualité du code et tests](chapitres/02-le-parcours-en-quatre-etapes.md#2-qualité-du-code-et-tests)
   - [3. Conception et architecture](chapitres/02-le-parcours-en-quatre-etapes.md#3-conception-et-architecture)
   - [4. Livraison et exploitation (DevOps)](chapitres/02-le-parcours-en-quatre-etapes.md#4-livraison-et-exploitation-devops)
3. [Le Test-Driven Development en profondeur](chapitres/03-le-test-driven-development-en-profondeur.md)
   - [Test-Driven Development en profondeur](chapitres/03-le-test-driven-development-en-profondeur.md#test-driven-development-en-profondeur)
   - [Le côté sombre du TDD : sur-tester et abîmer la conception](chapitres/03-le-test-driven-development-en-profondeur.md#le-côté-sombre-du-tdd-sur-tester-et-abîmer-la-conception)
4. [Refactoring et katas](chapitres/04-refactoring-et-katas.md)
   - [Catalogue de refactorings essentiels](chapitres/04-refactoring-et-katas.md#catalogue-de-refactorings-essentiels)
   - [Katas recommandés par difficulté](chapitres/04-refactoring-et-katas.md#katas-recommandés-par-difficulté)
   - [Du kata d'exhibition à la pratique quotidienne](chapitres/04-refactoring-et-katas.md#du-kata-dexhibition-à-la-pratique-quotidienne)
5. [Collaborer : binôme, groupe, revue et estimation](chapitres/05-collaborer-binome-groupe-revue-et-estimation.md)
   - [Pair programming et mob programming](chapitres/05-collaborer-binome-groupe-revue-et-estimation.md#pair-programming-et-mob-programming)
   - [Quand pairer, quand ne pas pairer](chapitres/05-collaborer-binome-groupe-revue-et-estimation.md#quand-pairer-quand-ne-pas-pairer)
   - [La revue de code (code review) bien faite](chapitres/05-collaborer-binome-groupe-revue-et-estimation.md#la-revue-de-code-code-review-bien-faite)
   - [L'estimation honnête : story points, T-shirt, NoEstimates](chapitres/05-collaborer-binome-groupe-revue-et-estimation.md#lestimation-honnête-story-points-t-shirt-noestimates)
6. [Travailler avec le code legacy](chapitres/06-travailler-avec-le-code-legacy.md)
   - [Travailler avec du code legacy](chapitres/06-travailler-avec-le-code-legacy.md#travailler-avec-du-code-legacy)
   - [Petits pas en territoire legacy : éviter la paralysie d'analyse](chapitres/06-travailler-avec-le-code-legacy.md#petits-pas-en-territoire-legacy-éviter-la-paralysie-danalyse)
7. [Livraison continue, mentorat et carrière](chapitres/07-livraison-continue-mentorat-et-carriere.md)
   - [Continuous Delivery comme aboutissement du craft](chapitres/07-livraison-continue-mentorat-et-carriere.md#continuous-delivery-comme-aboutissement-du-craft)
   - [Mentorat : enseigner est un métier en soi](chapitres/07-livraison-continue-mentorat-et-carriere.md#mentorat-enseigner-est-un-métier-en-soi)
   - [Évolution de carrière du craftsman](chapitres/07-livraison-continue-mentorat-et-carriere.md#évolution-de-carrière-du-craftsman)
8. [Soutenabilité, communauté et pratique quotidienne](chapitres/08-soutenabilite-communaute-et-pratique-quotidienne.md)
   - [Burnout et perfectionnisme du craftsman](chapitres/08-soutenabilite-communaute-et-pratique-quotidienne.md#burnout-et-perfectionnisme-du-craftsman)
   - [Communautés et événements](chapitres/08-soutenabilite-communaute-et-pratique-quotidienne.md#communautés-et-événements)
   - [Anti-patterns du faux craft](chapitres/08-soutenabilite-communaute-et-pratique-quotidienne.md#anti-patterns-du-faux-craft)
   - [Habitudes du quotidien](chapitres/08-soutenabilite-communaute-et-pratique-quotidienne.md#habitudes-du-quotidien)

---

## Pour aller plus loin

- [Manifesto for Software Craftsmanship (2009)](https://manifesto.softwarecraftsmanship.org/)
- [Manifesto for Agile Software Development (2001)](https://agilemanifesto.org/iso/fr/manifesto.html)
- [Principes SOLID, Robert C. Martin](https://en.wikipedia.org/wiki/SOLID)
- [Refactoring Guru : design patterns et refactoring](https://refactoring.guru/)
- [The Twelve-Factor App](https://12factor.net/) : applications modernes
- [DORA : State of DevOps reports](https://dora.dev/research/)
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
