# Exercice 1 – Utilisation des props dans une application React

### Objectif pédagogique :

Apprendre à créer des composants React de différents types (classe et fonction) et à leur transmettre des données via des **props de type `string`** et **props de type `fonction`**. Vous apprendrez également à afficher dynamiquement ces données dans l’interface utilisateur.



## Consignes :

1. Créez une nouvelle application React en utilisant l’outil `create-react-app`. Le nom du projet peut être `exercice-props`.

2. Dans le dossier `src/`, ajoutez un composant `Recherche.js` de type **classe** ou **fonction**, selon votre préférence.

3. Ajoutez un composant `Composant1.js` de type **classe**.

4. Ajoutez un composant `Composant2.js` de type **fonction**.

5. Dans le fichier `App.js`, affichez le composant `Recherche` **sans passer de props**.

6. Dans le fichier `App.js`, affichez le composant `Composant1` **sans passer de props**.

7. Dans le fichier `App.js`, affichez le composant `Composant2` **sans passer de props**.

8. Ajoutez une **prop nommée `a` de type `string`** au composant `Recherche`.

9. Ajoutez une **prop nommée `b` de type `string`** au composant `Composant1`.

10. Ajoutez une **prop nommée `c` de type `string`** au composant `Composant2`.

11. Ajoutez une **prop de type `fonction`** au composant `Recherche`. Cette fonction doit simplement afficher un message dans la console avec `console.log()`.

12. Dans le composant `Recherche`, affichez dynamiquement à l’écran la valeur de la prop `a`.

13. Dans le composant `Recherche`, ajoutez un bouton. Lorsque ce bouton est cliqué, il doit exécuter la fonction transmise par la prop (voir Q11).



## Architecture attendue

```
src/
├── App.js
├── Recherche.js        ← props : a (string), action (function)
├── Composant1.js       ← props : b (string)
└── Composant2.js       ← props : c (string)
```


