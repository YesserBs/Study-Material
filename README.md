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
title: Avancement cour et TP

tags:
  - Excel
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

TP 2 c'est les régressions linéaires, on s'est également interessé à (...) et Chi_2

Chi_2 c'est en gros le score de bizarrerie (par rapport à ce que tu attends comme valeurs)

Chi_au_carré = somme( (valeur_observée - valeur_attendue)**2 / valeur_attendue )

Chi est bas -> C'est bon signe

Mais Chi2 seul ne suffit pas car ca dépend d'un certain **degré de liberté** je te balance seulement des mots clés: tolérance au hasard, ddl = 2 ou ddl = 1

Donc on calcule une p-value (probabilité que ca soit grave):
- p < 0.05 → 🚨 “c’est louche !!”
- p > 0.05 → 😌 “ça passe”

sur Excel Khideux et p-value devraient etre:
```
=TEST.KHIDEUX(observé; attendu)
```
```
=LOI.KHIDEUX.DROITE(chi2; ddl)
```

quand utilisée ?
- check si notre hypothès (par ex: loi uniforme) est correcte (pas trop irl)
- comparaison aux années précedentes
- nous dit si c'est juste du bruit et qu'il n'y a pas a s'inquieter meme si on voit du 25 au lieu de 33
ou pas (long term it's fine: attendu : 33 / 33 / 33 observé : 35 / 30 / 34) 

Détail juste à connaitre:
- dans le cas ou on utilise Chi pour deux variables ca nous renseigne sur l'indpéndence


Le reste on le verra une autre fois :

une liste des differentes notions à comprendre (encore au format ChatGPT pour l'instant):
```
# 🧠 📌 COURS 1 — (collecte + stats descriptives)

👉 Je ne mets que ce qui peut tomber / ce qui demande de réfléchir

## 🔹 Collecte des données

* Méthodes d’échantillonnage :

  * aléatoire
  * stratifié
  * systématique
  * grappes
  * quotas
    ➡️ savoir **les distinguer + reconnaître dans un exercice**

* Différence :

  * enquête vs expérimentation

* Notion de **facteur** :

  * qualitatif vs quantitatif

---

## 🔹 Excel / tableur

* Références :

  * relative vs absolue ($) ⚠️ classique d’examen

* Fonctions :

  * MOYENNE
  * SOMME
  * SI
  * NB.SI
  * SOMMEPROD
    ➡️ surtout comprendre **quand les utiliser**

---

## 🔹 Statistiques descriptives

* Moyenne (arithmétique, géométrique, harmonique)
  ➡️ savoir **quand utiliser laquelle**

* Médiane / quartiles
  ➡️ interprétation (distribution)

* Variance / écart-type
  ➡️ mesure de dispersion

* Coefficient de variation
  ➡️ comparer des séries

---

# 🧠 📌 COURS 2 — (le plus important)

👉 Celui-là est **beaucoup plus stratégique pour l’examen**

---

## 🔹 Variables quantitatives

### 1. Covariance

* Signe (positif / négatif)
* Limite : difficile à interpréter

---

### 2. Corrélation linéaire (r) ⭐⭐⭐

* Interprétation :

  * proche de 1 → forte relation +
  * proche de -1 → forte relation -
  * proche de 0 → pas de lien linéaire

* ⚠️ piège :

  * r = 0 ≠ indépendance

---

### 3. Normalisation

* Centrage
* Réduction (écart-type)
  ➡️ comprendre **pourquoi on le fait**

---

### 4. Régression linéaire ⭐⭐⭐

* Modèle :

  * y = ax + b

* Idée :

  * prédire y à partir de x
  * minimiser l’erreur

➡️ savoir interpréter :

* a (pente)
* b (origine)

---

### 5. Coefficient de détermination (r²) ⭐⭐⭐

* Interprétation :

  * part de variance expliquée

➡️ savoir répondre :

* “le modèle explique X% de y”

---

## 🔹 Variables qualitatives

### 6. Tableau de contingence ⭐⭐

* Lire un tableau
* Comprendre :

  * effectifs croisés
  * totaux

---

### 7. Indépendance ⭐⭐⭐

* Comprendre l’idée :

  * X et Y indépendants ou non

---

### 8. Test du χ² ⭐⭐⭐

* Logique :

  * comparer observé vs attendu

* Calcul attendu :

  * (total ligne × total colonne) / total

* Interprétation :

  * χ² élevé → dépendance
  * χ² faible → indépendance

---

# 🔥 PRIORITÉS (TRÈS IMPORTANT)

Si tu veux optimiser ton temps :

## 🎯 Niveau 1 (indispensable)

* Corrélation (r)
* r²
* Régression linéaire
* Test du χ²
* Méthodes d’échantillonnage

---

## 🎯 Niveau 2 (important)

* Variance / écart-type
* Quartiles
* Tableau de contingence
* Normalisation

---

## 🎯 Niveau 3 (secondaire)

* Covariance (juste compréhension)
* Moyennes géométrique / harmonique

---

# 🧠 RÉSUMÉ FINAL

👉 Tu dois surtout savoir répondre à ces questions :

* Est-ce que 2 variables sont liées ? → r ou χ²
* Est-ce que je peux prédire ? → régression
* Est-ce que mon modèle est bon ? → r²
* Comment j’ai obtenu mes données ? → échantillonnage
```



<!-- NOTE -->
---
title: entrée sortie I/O Java IO

tags:
  - Java
---

It's still too CharGPTish, i will change it, mais au moins ca avance:

# 🗒️ POST-IT JAVA IO (ultra simple)

## 📂 Fichiers (base)

* **`FileInputStream (fis)`** → lire un fichier (byte par byte)
* **`FileOutputStream (fos)`** → écrire dans un fichier

👉 À utiliser quand :

* tu manipules des fichiers simples (texte, image, etc.)
* tu veux lire/écrire des données brutes

---

## ⚡ Buffer (performance)

* **`BufferedInputStream`** → lire plus vite
* **`BufferedOutputStream`** → écrire plus vite

👉 À utiliser quand :

* fichiers gros
* optimisation nécessaire
* (souvent en wrap autour de fis/fos)

---

## 🔢 Données typées

* **`DataInputStream`** → lire `int`, `double`, `boolean`, `String`
* **`DataOutputStream`** → écrire ces types

👉 À utiliser quand :

* tu veux stocker des données structurées
* tu connais l’ordre lecture/écriture

⚠️ Toujours lire dans le même ordre que l’écriture

---

## 🧬 Objets (sérialisation)

* **`ObjectOutputStream`** → écrire un objet (`writeObject`)
* **`ObjectInputStream`** → lire un objet (`readObject`)

👉 À utiliser quand :

* tu veux sauvegarder un objet complet
* (classe doit `implements Serializable`)

---

## 🧠 Règle simple à retenir

* fichier simple → **FileStream**
* performance → **Buffered**
* types (`int`, etc.) → **DataStream**
* objet complet → **ObjectStream**

---

## 🧩 Schéma mental

```
File → FileStream → (Buffered) → (Data ou Object)
```


<!-- NOTE -->
---
title: l'adresse mail de l'univ avec sorbonne

tags:
  - univ_stuff
---

edu.sorbonne-paris-nord.fr



<!-- NOTE -->
---
title: Partie stats en proba

tags:
  - proba
---

J'expliquerais une autre fois :
## Estimateurs

Un estimateur est une valeur calculée à partir des données pour approximer un paramètre inconnu.

Exemple :
La moyenne empirique :

$$
\hat{\mu} = \frac{1}{n} \sum X_i
$$

---

## Méthode des moments

On égalise les moments théoriques avec les moments empiriques.

Exemple :
E(X) = μ → on remplace par la moyenne empirique

Donc :
μ ≈ moyenne des données

---

## Maximum de vraisemblance (MLE)

Objectif : trouver le paramètre qui rend les données les plus probables.

### Étapes :
1. Écrire la vraisemblance :
   produit des probabilités ou densités
2. Prendre le logarithme
3. Dériver
4. Résoudre : dérivée = 0
5. Vérifier que la dérivée seconde est négative (maximum)
