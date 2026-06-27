[← Refactoring et katas](04-refactoring-et-katas.md) · [↑ Sommaire](../README.md#table-des-matières) · [Travailler avec le code legacy →](06-travailler-avec-le-code-legacy.md)

# 5. Collaborer : binôme, groupe, revue et estimation

## Pair programming et mob programming

Programmer ensemble n'est pas une réunion. C'est une discipline.

### Pair programming

Deux personnes, **une seule machine active**.

- Le **driver** tient le clavier. Il traduit l'intention en code.
- Le **navigator** regarde la carte : il pense au prochain test, repère les coquilles, garde l'objectif en vue.
- **On change de rôle régulièrement**, toutes les 10 à 25 minutes. Sans alternance, ce n'est plus du pair, c'est un public.

> **Que veut dire « bus factor » ?**
> Le *bus factor* (facteur d'autobus) est le nombre de personnes qui peuvent disparaître de l'équipe (au sens imagé : se faire renverser par un bus) avant que le projet ne soit bloqué faute de savoir. Un *bus factor* de 1 est dangereux : une seule personne connaît un morceau critique. Programmer à deux fait monter ce nombre, car la connaissance est partagée.

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

## Quand pairer, quand ne pas pairer

Le pair programming est **merveilleux 30 % du temps, neutre 40 %, contre-productif 30 %**. Le craftsman qui pratique sait reconnaître le bon moment plutôt que d'en faire un dogme.

### Quand le pair vaut clairement son coût

- **Sujets à forte incertitude technique** : un nouveau domaine, une dette mal connue, un bug profond. Deux paires d'yeux convergent plus vite vers la cause.
- **Décisions de conception structurantes** : choisir un découpage, nommer un agrégat, poser une frontière. Le dialogue oblige à expliciter, et l'explicite est plus solide que l'implicite.

> **Que veut dire « agrégat » et « bounded context » (contexte délimité) ?**
> Un **agrégat** (terme du DDD) est un groupe d'objets qu'on traite comme un seul bloc cohérent, avec un objet « chef » par lequel passent toutes les modifications, afin de garantir les règles internes. Comparaison du quotidien : une commande et ses lignes forment un agrégat ; on n'ajoute pas une ligne directement, on passe par la commande, qui vérifie le total. Un **bounded context** (contexte délimité) est une frontière à l'intérieur de laquelle un mot a un sens précis et stable. Le mot « client » ne signifie pas la même chose pour la facturation et pour le support ; chaque contexte a son propre modèle, et une frontière nette évite les confusions.
- **Onboarding** : un nouvel arrivant absorbe en deux jours de pair ce qu'il mettrait deux semaines à comprendre seul.
- **Transmission de pratique** : faire pratiquer le TDD à quelqu'un qui n'en a jamais fait passe par le geste partagé, pas par la doc.
- **Code à fort impact** (sécurité, paiement, données sensibles) : le pair sert de *quatre yeux* en temps réel et fait gagner un *round* de revue.

### Quand le pair coûte plus qu'il ne rapporte

- **Tâches mécaniques bien comprises** : configuration, migration de syntaxe, génération de boilerplate. Une personne suffit, l'autre s'ennuie.
- **Énergie basse** : fin de semaine, lendemain d'incident, équipe fatiguée. Le pair amplifie l'énergie présente, il n'en crée pas.
- **Asymétrie radicale et non préparée** : un sénior et un junior sans cadre se retrouvent en *dictée*, pas en pair. Mieux vaut un pair junior-junior plus un mentor qui passe à intervalles, ou un cadre explicite (« je conduis, tu poses toutes les questions »).
- **Travail solitaire pertinent** : exploration libre, brouillon, veille, rédaction. La concentration solitaire a sa place.
- **Mauvaise compatibilité personnelle** documentée : tout le monde ne pair pas bien avec tout le monde. Constater, accepter, alterner les binômes plutôt que forcer.

### Critères opérationnels

Avant de démarrer un pair, posez-vous :

1. **Quel est le résultat attendu de cette session** ? Un bug réparé ? Une décision prise ? Un transfert de connaissance ?
2. **Le binôme est-il aligné** sur le résultat et la durée ?
3. **Avons-nous l'énergie** ? Si la réponse est non, mieux vaut décaler ou faire seul.
4. **Y a-t-il un rôle clair** (driver / navigator) et un rythme d'alternance convenu ?

Si l'un de ces points reste flou, la session a peu de chances d'être productive. Le craftsman expérimenté **se réserve le droit de pairer ou de ne pas pairer**, et défend ce droit avec la même fermeté qu'il défend la pratique elle-même.

## La revue de code (code review) bien faite

Une revue de PR (ou MR) est **un acte de soin** envers le code et son auteur. Elle ne se réduit pas à pointer des défauts.

### Ce qu'on attend d'une bonne PR à relire

- Un titre qui dit l'intention.
- Une description : pourquoi, quoi, comment tester, captures s'il faut.
- Un *diff* qui tient à l'écran. Une PR de 800 lignes ne se relit pas, elle se survole.
- Des commits propres, ou un *squash* à la fusion.

> **Que veulent dire « diff », « commit », « squash », « nit », « LGTM » ?**
> Un **diff** (différence) est l'affichage des lignes ajoutées et supprimées par une modification : le relecteur ne lit que ce qui change, pas tout le projet. Un **commit** est une modification enregistrée dans l'historique Git, avec un message qui en explique l'intention. **Squash** (écraser) signifie fusionner plusieurs commits en un seul, plus propre, au moment d'intégrer la branche. Un **nit** (de *nitpick*, pinaillage) est une remarque mineure, esthétique, qui ne bloque pas. **LGTM** (*Looks Good To Me*, « ça me va ») est l'abréviation par laquelle un relecteur approuve une PR.
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

> **Que veulent dire « cas limite », « concurrence », « idempotence » ?**
> Un **cas limite** (*edge case*) est une valeur aux bords du raisonnable qui fait souvent planter : une liste vide, le nombre zéro, la date du 29 février, un texte très long. La **concurrence** désigne plusieurs traitements qui s'exécutent en même temps et risquent de se marcher dessus (deux personnes réservant le dernier siège à la même seconde). L'**idempotence** est la propriété d'une opération qu'on peut répéter sans dommage : appuyer deux fois sur le bouton « payer » ne doit débiter qu'une fois. Comparaison du quotidien : le bouton d'appel d'ascenseur est idempotent, le presser dix fois ne change rien.
- **B** comme **Behaviour** : le test vérifie-t-il vraiment le comportement attendu, ou juste l'implémentation ?
- **C** comme **Clarity** : nommage, structure, lisibilité du diff. Un développeur arrivant demain comprendrait-il ?
- **C** comme **Coverage** : zones non testées, tests fragiles, *test smells*.

### Bienveillance : la règle non négociable

La revue est *publique* (toute l'équipe lit). Un commentaire mal tourné peut blesser durablement. Quelques garde-fous :

- Critiquer le code, jamais la personne. « Cette méthode mélange deux responsabilités » plutôt que « tu as mélangé… ».
- Reconnaître ce qui est bon. Une PR n'est pas qu'un sac de défauts ; nommer un bon test, un bon découpage, fait grandir.
- Préférer le pair à la revue quand les remarques s'accumulent. Au-delà de cinq allers-retours, le canal écrit ne suffit plus.
- Souligner ce qui peut attendre : « *nit*, hors scope » est une politesse qui sauve des heures.

### La revue au-delà de la technique : empathie et posture

Une bonne revue n'est pas qu'une affaire de syntaxe et de patterns. Elle est, d'abord, **une conversation entre personnes qui se respectent**. Les meilleurs relecteurs croisés sont ceux qui ont compris ces quelques principes.

- **Poser plutôt que prescrire.** « Pourquoi ce choix ici ? » ouvre un dialogue. « Il fallait faire l'inverse » ferme la discussion et attaque la légitimité de l'auteur. La question est presque toujours plus forte que l'assertion, parce qu'elle révèle l'intention sans la juger.
- **Distinguer ce qui est faux de ce qui est différent.** Un bug est un bug. Un goût personnel n'est pas un bug. Le relecteur expérimenté garde ses préférences pour lui, ou les marque explicitement comme telles : « *préférence personnelle, à prendre ou à laisser* ».
- **Reconnaître la difficulté du sujet.** « Ce code n'est pas évident, merci d'avoir tenu la complexité dans une seule classe » vaut mille « *LGTM* » mécaniques.
- **Donner du contexte à ses suggestions.** Pas seulement « extrais cette méthode », mais « cette méthode a déjà trois responsabilités, l'extraction permettrait d'isoler la partie validation ; qu'en penses-tu ? ».
- **Accepter de ne pas avoir le dernier mot.** Le relecteur conseille ; l'auteur décide, dans la limite de ce qui est bloquant. Une revue qui prétend imposer chaque détail asphyxie l'équipe.
- **Soigner la cadence.** Une revue qui arrive en deux heures est un cadeau ; une revue qui arrive en deux jours est un poids. La fréquence des revues importe autant que leur profondeur.
- **Refuser le ton sec, même par fatigue.** L'écrit n'a pas le ton ; ce qu'on perçoit comme neutre passe souvent pour froid. Une formule de politesse, un point d'interrogation, un *merci* coûtent peu et préservent la confiance.

Le craftsman expérimenté sait que **la qualité technique d'une équipe est plafonnée par la qualité de ses revues**. Une équipe qui se relit avec dureté mais sans empathie produit du code prudent et peu d'audace. Une équipe qui se relit avec exigence et chaleur produit du code et des praticiens qui grandissent.

## L'estimation honnête : story points, T-shirt, NoEstimates

Estimer fait partie du métier ; sur-estimer la valeur d'une estimation, aussi. La position craft est nuancée et mérite d'être posée.

### Les principales conventions

- **Story points** (Mike Cohn, *Agile Estimating and Planning*, 2005) : unité **relative** d'effort, de complexité et de risque. Echelle souvent Fibonacci (1, 2, 3, 5, 8, 13). Pas une unité de temps : « 5 points » ne vaut pas « 5 jours ». Sert à comparer entre eux des éléments du backlog.
- **T-shirt sizing** (XS, S, M, L, XL, XXL) : encore plus grossier, encore plus relatif. Utile en début de projet quand on n'a pas de référentiel partagé pour calibrer des points.
- **NoEstimates** (Vasco Duarte, Woody Zuill, 2012-2014) : on remplace l'estimation par le découpage régulier en petites tranches livrables (idéalement de taille comparable) et on mesure le **throughput** (combien d'éléments terminés par semaine). Si chaque ticket fait moins de quelques jours, le débit suffit à projeter.
- **#NoSpecs** *(variante implicite)* : raffiner les spécifications jusqu'à ce que l'estimation devienne triviale. À court de temps, c'est rarement faisable ; intéressant comme idéal régulateur.

### Ce qu'une estimation peut et ne peut pas

Une estimation, **bien comprise**, est un **outil de conversation** entre l'équipe technique et le métier :

- Elle révèle des écarts de compréhension. Quand l'un voit un point et l'autre treize, ce n'est pas l'estimation qui est fausse, c'est la spécification qui est ambiguë. La discussion qui suit est la vraie valeur.
- Elle aide à arbitrer les priorités à effort égal. « Ces deux features ont la même valeur ; celle-ci coûte 3, celle-là 13 ; commençons par la moins chère. »
- Elle fournit un repère de planification grossier, à grande maille (trimestre, semestre).

Une estimation **ne peut pas** :

- Servir de **promesse contractuelle** sans réserves explicites. Le contexte change, les inconnus émergent.
- Mesurer la **performance individuelle**. C'est l'usage le plus toxique : le développeur dont les estimations « passent » apprend à gonfler par défaut, et le système se rigidifie.
- Remplacer un **découpage propre**. Une grosse story floue avec une grosse estimation reste une bombe à retardement.

### La position craft

Le craftsman tient une ligne moyenne, étrangère à la fois au dogme du planning et au dogme du *NoEstimates* :

- **Estimer quand c'est utile**, en équipe, à grande maille, en assumant l'incertitude. Pas estimer ce qu'on ne peut pas raisonnablement estimer.
- **Refuser les estimations à la précision usurpée** (« 6,5 jours / homme »). L'unité doit refléter la précision réelle.
- **Privilégier le découpage** systématique : un travail découpé en tranches de moins de trois jours rend l'estimation presque superflue.
- **Distinguer l'estimation interne** (entre développeurs, pour planifier) de l'**engagement** vers le métier (qui doit inclure une marge explicite).
- **Mesurer le débit réel** plutôt que la conformité à l'estimation. Un débit régulier vaut mieux qu'une estimation parfaite.
- **Avoir le courage du « je ne sais pas »**, suivi de « voici ce que je propose pour le savoir : un *spike* de deux jours, et on rediscute ». C'est rarement bien reçu au premier abord, c'est toujours payant à terme.

> **Que veut dire « spike » et « backlog » ?**
> Un **spike** (pointe) est une courte exploration bornée dans le temps (un ou deux jours) dont le but n'est pas de livrer une fonctionnalité mais de lever une incertitude : essayer une piste, mesurer une difficulté, puis décider. Comparaison du quotidien : un sondage de terrain avant de construire. Un **backlog** (réserve de travail) est la liste ordonnée de tout ce qui reste à faire sur un produit, du plus prioritaire au moins urgent ; l'équipe y pioche au fur et à mesure.

Lectures :

- Mike Cohn, *Agile Estimating and Planning* (2005).
- Vasco Duarte, *No Estimates: How To Measure Project Progress Without Estimating* (2015).
- Allen Holub, *Why Estimates Are Always Wrong* (vidéo, conférence) : argument frontal contre les estimations détaillées.
- Martin Fowler, [*Purpose of Estimation*](https://martinfowler.com/bliki/PurposeOfEstimation.html) (2013) : une mise au point équilibrée.

---

[← Refactoring et katas](04-refactoring-et-katas.md) · [↑ Sommaire](../README.md#table-des-matières) · [Travailler avec le code legacy →](06-travailler-avec-le-code-legacy.md)
