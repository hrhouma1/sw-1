## <h2 id="ex1">Exercice 2 – Passage de données via les props en React</h2>

### Objectifs pédagogiques :

* Créer plusieurs composants React (classe et fonction).
* Comprendre et manipuler les props (`string`, `function`).
* Intégrer et structurer les appels de composants dans une architecture modulaire.



### Consignes :

1. Créez une nouvelle application React à l’aide de la commande `create-react-app`.
2. Ajoutez un composant `MoteurRecherche.js`, de type **classe** ou **fonction** (selon votre choix).
3. Ajoutez un composant `FicheProduit.js`, de type **classe**.
4. Ajoutez un composant `ProfilClient.js`, de type **fonction**.
5. Dans `App.js`, affichez le composant `MoteurRecherche` **sans lui passer de props**.
6. Dans `App.js`, affichez le composant `FicheProduit` **sans lui passer de props**.
7. Dans `App.js`, affichez le composant `ProfilClient` **sans lui passer de props**.
8. Ajoutez une prop nommée `titre` (type `string`) au composant `MoteurRecherche`.
9. Ajoutez une prop nommée `nomProduit` (type `string`) au composant `FicheProduit`.
10. Ajoutez une prop nommée `nomClient` (type `string`) au composant `ProfilClient`.
11. Ajoutez une prop de type `fonction` au composant `MoteurRecherche` (ex. une fonction qui affiche un message dans la console).
12. Modifiez le composant `MoteurRecherche` afin d’afficher la valeur de la prop `titre`.
13. Dans `MoteurRecherche`, ajoutez un bouton qui déclenche la fonction reçue en props lors du clic.



### Architecture attendue :

```
App.js
├── MoteurRecherche.js      ← props : titre (string), action (fonction)
├── FicheProduit.js         ← props : nomProduit (string)
└── ProfilClient.js         ← props : nomClient (string)
```


