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





<br/>



# Correction -  Exercice React – Passage de props (string et fonction)


<br/>

## Q1. Créer l’application React

**Commande à exécuter :**

```bash
npx create-react-app exercice-props
cd exercice-props
npm start
```

<br/>

## Q2. Créer le composant `MoteurRecherche.js` (classe)

###  Fichier : `src/MoteurRecherche.js`

```jsx
import React from 'react';

class MoteurRecherche extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Moteur de Recherche</h2>
      </div>
    );
  }
}

export default MoteurRecherche;
```

<br/>

## Q3. Créer le composant `FicheProduit.js` (classe)

###  Fichier : `src/FicheProduit.js`

```jsx
import React from 'react';

class FicheProduit extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Fiche Produit</h2>
      </div>
    );
  }
}

export default FicheProduit;
```

<br/>

## Q4. Créer le composant `ProfilClient.js` (fonction)

###  Fichier : `src/ProfilClient.js`

```jsx
import React from 'react';

const ProfilClient = () => {
  return (
    <div>
      <h2>Composant Profil Client</h2>
    </div>
  );
};

export default ProfilClient;
```

<br/>

## Q5 à Q7. Appeler les 3 composants dans `App.js` sans props

###  Fichier : `src/App.js`

```jsx
import React from 'react';
import MoteurRecherche from './MoteurRecherche';
import FicheProduit from './FicheProduit';
import ProfilClient from './ProfilClient';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Interface principale</h1>

        {/* 🔽 Appels sans props */}
        <MoteurRecherche />
        <FicheProduit />
        <ProfilClient />
      </div>
    );
  }
}

export default App;
```

<br/>

## Q8. Ajouter une prop `titre` (string) à `MoteurRecherche`

###  Fichier : `src/App.js`

```jsx
import React from 'react';
import MoteurRecherche from './MoteurRecherche';
import FicheProduit from './FicheProduit';
import ProfilClient from './ProfilClient';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Interface principale</h1>

        {/* 🔽 Ajout de la prop titre */}
        <MoteurRecherche titre="Recherche des produits disponibles" />

        <FicheProduit />
        <ProfilClient />
      </div>
    );
  }
}

export default App;
```


<br/>

## Q9. Ajouter une prop `nomProduit` (string) à `FicheProduit`

###  Fichier : `src/App.js`

```jsx
import React from 'react';
import MoteurRecherche from './MoteurRecherche';
import FicheProduit from './FicheProduit';
import ProfilClient from './ProfilClient';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Interface principale</h1>

        <MoteurRecherche titre="Recherche des produits disponibles" />

        {/* 🔽 Ajout de la prop nomProduit */}
        <FicheProduit nomProduit="Ordinateur portable Dell" />

        <ProfilClient />
      </div>
    );
  }
}

export default App;
```

<br/>

## Q10. Ajouter une prop `nomClient` (string) à `ProfilClient`

###  Fichier : `src/App.js`

```jsx
import React from 'react';
import MoteurRecherche from './MoteurRecherche';
import FicheProduit from './FicheProduit';
import ProfilClient from './ProfilClient';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Interface principale</h1>

        <MoteurRecherche titre="Recherche des produits disponibles" />
        <FicheProduit nomProduit="Ordinateur portable Dell" />

        {/* 🔽 Ajout de la prop nomClient */}
        <ProfilClient nomClient="Jean Dupont" />
      </div>
    );
  }
}

export default App;
```

<br/>

## Q11. Ajouter une prop `action` (fonction) à `MoteurRecherche`

###  Fichier : `src/App.js`

```jsx
import React from 'react';
import MoteurRecherche from './MoteurRecherche';
import FicheProduit from './FicheProduit';
import ProfilClient from './ProfilClient';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Interface principale</h1>

        {/* 🔽 Ajout de la prop action */}
        <MoteurRecherche
          titre="Recherche des produits disponibles"
          action={() => console.log("Recherche lancée depuis App")}
        />

        <FicheProduit nomProduit="Ordinateur portable Dell" />
        <ProfilClient nomClient="Jean Dupont" />
      </div>
    );
  }
}

export default App;
```

<br/>

## Q12. Afficher la prop `titre` dans `MoteurRecherche.js`

###  Fichier : `src/MoteurRecherche.js`

```jsx
import React from 'react';

class MoteurRecherche extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Moteur de Recherche</h2>

        {/* 🔽 Affichage de la prop titre */}
        <p>{this.props.titre}</p>
      </div>
    );
  }
}

export default MoteurRecherche;
```


<br/>

## Q13. Utiliser la prop `action` via un bouton dans `MoteurRecherche.js`

###  Fichier : `src/MoteurRecherche.js`

```jsx
import React from 'react';

class MoteurRecherche extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Moteur de Recherche</h2>

        <p>{this.props.titre}</p>

        {/* 🔽 Bouton déclenchant la fonction passée via props */}
        <button onClick={this.props.action}>
          Lancer la recherche
        </button>
      </div>
    );
  }
}

export default MoteurRecherche;
```


