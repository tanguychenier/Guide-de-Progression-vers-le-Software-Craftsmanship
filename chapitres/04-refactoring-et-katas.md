[← Le Test-Driven Development en profondeur](03-le-test-driven-development-en-profondeur.md) · [↑ Sommaire](../README.md#table-des-matières) · [Collaborer : binôme, groupe, revue et estimation →](05-collaborer-binome-groupe-revue-et-estimation.md)

# 4. Refactoring et katas

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

> **Que veut dire « polymorphisme » ?**
> Le polymorphisme (du grec : « plusieurs formes ») est la capacité de plusieurs objets à répondre au même ordre, chacun à sa manière. On appelle `cout_envoi()` sans savoir s'il s'agit d'un colis standard, express ou international : chaque type sait calculer son propre coût. Comparaison du quotidien : on dit « avance » à un cheval, à une voiture et à un bateau ; chacun comprend et exécute à sa façon, sans qu'on ait à préciser comment.

Quand un `if`/`switch` se ramifie sur un type ou un état, on peut souvent le remplacer par des classes filles qui chacune connaissent leur cas. L'avantage : ajouter un nouveau cas n'oblige plus à rouvrir et risquer de casser la fonction commune.

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

Quand une méthode parle plus à une autre classe qu'à la sienne, on la déplace. Indice : elle utilise majoritairement les champs d'un autre objet (*feature envy*, « envie des fonctionnalités d'autrui » : une méthode qui s'intéresse plus aux données d'une autre classe qu'aux siennes).

### Encapsulate Field / Replace Data Value with Object

> **Que veulent dire « encapsuler » et « invariant » ?**
> **Encapsuler** signifie enfermer une donnée à l'intérieur d'un objet et contrôler les accès, plutôt que la laisser nue et manipulable de partout. Comparaison du quotidien : un distributeur de billets ne vous laisse pas plonger la main dans le coffre ; il impose un guichet avec des règles. Un **invariant** est une règle qui doit rester vraie en permanence pour qu'un objet soit valide, par exemple « une adresse e-mail contient toujours un @ » ou « la fin d'un créneau est toujours après son début ».

Une donnée nue (`string adresse_email`) finit par être validée à plusieurs endroits. Encapsuler dans un *value object* (`AdresseEmail`) concentre les invariants et élimine les validations dupliquées : la règle de validité vit en un seul endroit, impossible à contourner.

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

> **Que veut dire « property-based testing » ?**
> Le *property-based testing* (test par propriétés) ne donne pas un exemple précis attendu ; il énonce une règle générale qui doit toujours tenir, puis l'outil génère automatiquement des centaines d'entrées au hasard pour tenter de la mettre en défaut. Comparaison du quotidien : au lieu de vérifier « 3 + 5 = 8 », on affirme « additionner deux nombres positifs donne toujours un résultat plus grand que chacun d'eux » et la machine cherche un contre-exemple.
- **Lift Kata** : modélisation d'un ascenseur multi-étages avec plusieurs cabines. Conception, états, événements.

**Bonnes adresses pour des katas.** [Coding Dojo](https://codingdojo.org/), [Kata-Log](https://kata-log.rocks/), [Kata Containers (Emily Bache)](https://github.com/emilybache), [GitHub coding-katas](https://github.com/topics/coding-katas).

**Comment pratiquer un kata.** Refaire le même kata plusieurs fois, en variant la contrainte : pas de souris, pas plus de 5 lignes par méthode, en pair, dans un langage inconnu, en mob silencieux, en *ping-pong* (l'un écrit le test, l'autre le code). La contrainte révèle le geste.

## Du kata d'exhibition à la pratique quotidienne

Faire FizzBuzz en TDD strict une fois, en atelier, **n'est pas du craftsmanship**. C'est une **activité de formation**, utile pour découvrir la mécanique. Le craftsmanship, c'est ce que vous faites **lundi matin sur du code de production** quand personne ne regarde.

### Le piège du kata-vitrine

Le kata exhibition se reconnaît à plusieurs symptômes :

- On choisit un kata qu'on a déjà fait dix fois, on déroule la solution mémorisée, on récolte des « *clean* » de la salle.
- On termine le kata sans avoir échoué une seule fois. Pas de *red* surprenant, pas de *refactor* douloureux, pas d'apprentissage.
- L'environnement est idéal : un *greenfield* (projet neuf, parti de zéro, sans contrainte d'existant, par opposition au *brownfield*, un terrain déjà bâti), un énoncé de cinq lignes, des collaborateurs concentrés. Rien de comparable à la vraie journée.
- Personne ne reprend les acquis du kata dans le code de production le lendemain.

### La pratique de production : ce qui compte vraiment

La pratique craft quotidienne est plus humble :

- **Écrire un test avant un code de production aujourd'hui**, sur la fonctionnalité que vous portez, dans le contexte que vous avez (legacy, framework imposé, deadline).
- **Refactorer un module touché** ne serait-ce que d'un nom mieux choisi avant de partir, parce que vous l'avez compris en y passant.
- **Ouvrir une PR claire**, avec une description qui aide le relecteur, parce que vous savez que sa journée n'est pas votre journée.
- **Refuser une fonctionnalité bâclée** quand l'estimation et la deadline ne tiennent plus, et le formuler proprement.
- **Mentorer un collègue** sur un point que vous maîtrisez, en passant dix minutes à montrer plutôt qu'à corriger.

### Pourquoi pratiquer les katas malgré tout

Les katas restent **précieux comme banc d'essai** : on y répète un geste sans pression de livraison, on y compare des langages, des styles, des contraintes. Mais leur valeur se mesure **en transferts** vers la production :

- Le geste de TDD acquis sur Bowling Game se retrouve-t-il dans votre PR de mardi ?
- Le refactoring nommé pratiqué sur Tennis Refactoring se propose-t-il dans votre prochaine revue ?
- Le pair appris en dojo s'invite-t-il dans la séance de demain matin ?

Si la réponse est non, le kata est resté de l'exercice, pas de la pratique. **Ratio sain** : pour chaque heure de kata, viser au moins une heure d'application consciente sur du code réel dans la semaine qui suit.

---

[← Le Test-Driven Development en profondeur](03-le-test-driven-development-en-profondeur.md) · [↑ Sommaire](../README.md#table-des-matières) · [Collaborer : binôme, groupe, revue et estimation →](05-collaborer-binome-groupe-revue-et-estimation.md)
