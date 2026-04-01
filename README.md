<!-- NOTE -->
---
title: Explications du concept

tags:
  - concept
---

Le principe est simple : utilise cette structure pour créer des notes.

structure des notes:
```
<!-- NOTE -->
---
title: X

tags:
  - Y
  - Z
---

Contenu...
```

Je vais mettre ce qui m'est utile : TP, commandes, révision, etc.<br>
Je créerai un script qui vérifie si la structure du fichier est valide.

<!-- NOTE -->
---
title: Le dollar $ sur Excel

tags:
  - Excel
---

En gros, quand tu utilises le dollar, tu verrouilles une référence de cellule selon son emplacement.

- $A1 : colonne verrouillée
- A$1 : ligne verrouillée
- $A$1 : ligne et colonne verrouillées

conditions :

style typique:
```
=SI(condition ; valeur_si_vrai ; valeur_si_faux)
```
exemple:
```
=SI(E1>100 ; "OK" ; "Pas OK")
```
bien entendu on peut faire des imbrications:
```
=SI(E1>100 ; "Bon" ; SI(E1>80 ; "Assez bon" ; "Problème"))
```

Le quartile c'est quoi ?
- Q1 est la médiane de la moitié inférieure des données,
- Q2 correspond à la médiane
- et Q3 est la médiane de la moitié supérieure

Quand le nombre de données est impair, on exclut la médiane pour calculer Q1 et Q3.

Trier les données ?<br>
sur l'onglet Acceuil > trier<br>
si c'est pour une seule colonne tu la séléctionne et basta<br>
si plusieurs il faut toutes les sélectionner. Par défaut ca trie selon la première colonne choisie mais dans tri si tu click sur personalisé tu peux changer pas mal de choses, la colonne, et tu peux meme trier selon plusieurs trucs

pourcentile ?<br>
Les quartiles sont des cas particuliers de centiles :
- Q1 = 25e centile
- Q2 = 50e centile (médiane)
- Q3 = 75e centile

Exemples:
```
=PERCENTILE.INC(A1:A10 ; 0,25)   → 25%
=PERCENTILE.INC(A1:A10 ; 0,5)    → médiane
=PERCENTILE.INC(A1:A10 ; 0,9)    → 90%
```
Rq: en pratique on utilise toujours .INC ne cherche meme pas à comprendre .EXC

<!-- NOTE -->
---
title: X

tags:
  - Y
  - Z
---

éléments à maitriser du TP 1
- Utiliser les fonctions statistiques : MIN, MAX, MOYENNE, MEDIANE
- Calculer et interpréter les quartiles (Q1, Q2, Q3)
- Utiliser QUARTILE.INC et PERCENTILE.INC
- Comprendre la différence entre .INC et .EXC
- Manipuler correctement les plages de données (ex : B$2:B$1288)
- Écrire des formules copiables sur plusieurs cellules
- Maîtriser la fonction SI (conditions simples et imbriquées)
- Utiliser ET pour combiner plusieurs conditions
- Transformer une variable quantitative en qualitative
- Méthode des intervalles de même largeur
- Méthode des intervalles de même effectif (quantiles)
- Construire des catégories à partir de seuils (quartiles, percentiles)
- Optimiser les conditions pour éviter les tests inutiles
- Utiliser des résultats d’une feuille dans une autre (liaison de données)
- Comprendre la logique globale d’analyse de données et d’automatisation
