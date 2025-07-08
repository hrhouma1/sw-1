# EXAMEN PARTIE 2

- **Nom de l'étudiant** : \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
- **Groupe** : \_\_\_\_\_\_\_\_\_\_\_
- **Durée** : 1h45
- **Technologie autorisée : React (create-react-app)**
- **Aucun usage de Git requis**



## CONSIGNES

* Travail **individuel**, à faire dans un projet React généré avec `create-react-app`.
* Utilisez uniquement des composants **fonctionnels** avec `useState`, `useEffect`.
* Le rendu doit contenir :

  * Les fichiers `.js` fonctionnels
  * Le fichier `App.js` testant votre composant
  * Un export `.zip` ou `.docx` contenant tout le code
* Aucun framework CSS ni bibliothèque externe ne doit être utilisé.



## PARTIE 2 : FILTRAGE DE PRODUITS PAR CATÉGORIE

### 1. CONTEXTE

Vous devez construire une mini-application React qui permet d’afficher des produits provenant d’une API distante, puis de les filtrer selon leur catégorie.

Vous utiliserez cette **API publique** :

```
https://fakestoreapi.com/products
```

Chaque produit retourné est de la forme :

```json
{
  "id": 1,
  "title": "Fjallraven Backpack",
  "price": 109.95,
  "category": "men's clothing",
  "image": "https://fakestoreapi.com/img/..."
}
```



### 2. OBJECTIF

Créez un composant nommé `FiltreProduits.js` qui :

1. Utilise `fetch()` avec `useEffect` pour récupérer les produits.
2. Stocke les produits dans un `useState`.
3. Détecte dynamiquement les **catégories uniques** présentes dans les produits.
4. Affiche une liste déroulante (`<select>`) permettant de filtrer par catégorie.
5. Affiche uniquement les produits de la catégorie sélectionnée.
6. Chaque produit affiché doit inclure :

   * Le **titre** (`title`)
   * Le **prix** (`price`)
   * L’**image** (`image`)



### 3. AFFICHAGE ATTENDU

Le composant doit afficher quelque chose comme :

```
Sélectionnez une catégorie : [Papeterie] [Informatique] [...]

Titre : Clé USB
Prix : 10.99$
[Image]

Titre : Souris
Prix : 14.50$
[Image]
```



### 4. BONUS (si temps)

* Affichez un message `"Chargement..."` ou barre de chargement tant que les produits ne sont pas encore chargés.
* Affichez `"Aucun produit pour cette catégorie"` si la liste filtrée est vide.
* Stylisez légèrement les produits avec une bordure ou un fond.



### 5. STRUCTURE ATTENDUE

* `src/components/FiltreProduits.js` : Composant principal
* `App.js` : Intègre et teste le composant



### 6. FICHIER À REMETTRE

Un fichier `.zip` pour le code et `.docx` avec les imprimes-écrans de votre application nommé :

```
tp_react_filtrage_NOM_PRENOM.zip
```

Il doit contenir :

* Le code complet de `FiltreProduits.js`
* Le fichier `App.js` avec l'intégration du composant
* Vos commentaires éventuels dans le code



### 7. QUESTIONS À RÉDIGER DANS `questions.txt` ou dans le `.docx`

1. Pourquoi place-t-on l’appel `fetch()` dans `useEffect()` ?
2. Quelle est la différence entre `useState()` et `useEffect()` ?
3. À quoi sert la `key` dans `.map()` ?
4. Quelle est la structure minimale d’un composant fonctionnel React ?
5. Quelle est la différence entre props et state ?

