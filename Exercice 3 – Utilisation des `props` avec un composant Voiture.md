# Exercice 3 – Utilisation des `props` avec un composant Voiture

## Objectifs pédagogiques :

* Savoir passer plusieurs props à un composant React
* Manipuler des fonctions passées en props
* Réagir aux événements utilisateur (clics)
* Structurer les interactions dans un composant de type classe ou fonction

<br/>

### Consignes :

1. Créez une application React à l’aide de `create-react-app`.
2. Créez un composant `Car.js` dans le dossier `src/`, de type **classe** ou **fonction**, selon votre préférence.
3. Dans `App.js`, affichez le composant `Car` en lui passant les **props suivantes** :

   ```jsx
   <Car couleur="rouge" marque="Toyota Matrix" kilometrage="100 km" />
   ```
4. Ajoutez une **prop de type fonction** à `Car`, nommée par exemple `demarrer`, qui doit **afficher un message dans la console** (ex. `console.log("La voiture démarre")`).
5. Dans le composant `Car`, ajoutez **quatre boutons** :

   * Le **premier bouton** affiche dans la console la **valeur de la prop `couleur`**
   * Le **deuxième bouton** affiche la **valeur de la prop `marque`**
   * Le **troisième bouton** affiche la **valeur de la prop `kilometrage`**
   * Le **quatrième bouton** **appelle la fonction `demarrer`** passée en prop


<br/>

# Correction

* Fichiers complets à chaque étape
* Indication claire du **fichier concerné**
* Ajouts marqués avec `// 🔽 Ajout`

<br/>

## Q1. Créer une application React

```bash
npx create-react-app exercice-voiture
cd exercice-voiture
npm start
```

---

## Q2. Créer un composant `Car.js` de type classe

### 📄 Fichier : `src/Car.js`

```jsx
import React from 'react';

class Car extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Car</h2>
      </div>
    );
  }
}

export default Car;
```

<br/>

## Q3. Appeler `Car` avec 3 props string : `couleur`, `marque`, `kilometrage`

### 📄 Fichier : `src/App.js`

```jsx
import React from 'react';
import Car from './Car';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Interface principale</h1>

        {/* 🔽 Appel de Car avec 3 props */}
        <Car
          couleur="rouge"
          marque="Toyota Matrix"
          kilometrage="100 km"
        />
      </div>
    );
  }
}

export default App;
```

<br/>

## Q4. Ajouter une prop fonction `demarrer` à `Car`

### 📄 Fichier : `src/App.js` (mise à jour complète)

```jsx
import React from 'react';
import Car from './Car';

class App extends React.Component {
  handleDemarrer = () => {
    console.log("La voiture démarre");
  };

  render() {
    return (
      <div>
        <h1>Interface principale</h1>

        {/* 🔽 Appel avec fonction en prop */}
        <Car
          couleur="rouge"
          marque="Toyota Matrix"
          kilometrage="100 km"
          demarrer={this.handleDemarrer}
        />
      </div>
    );
  }
}

export default App;
```

<br/>

## Q5. Ajouter 4 boutons dans `Car.js` pour afficher les props

### 📄 Fichier : `src/Car.js` (code complet avec interactions)

```jsx
import React from 'react';

class Car extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Car</h2>

        <p>Couleur : {this.props.couleur}</p>
        <p>Marque : {this.props.marque}</p>
        <p>Kilométrage : {this.props.kilometrage}</p>

        {/* 🔽 Boutons pour afficher les props */}
        <button onClick={() => console.log(this.props.couleur)}>
          Afficher la couleur
        </button>

        <button onClick={() => console.log(this.props.marque)}>
          Afficher la marque
        </button>

        <button onClick={() => console.log(this.props.kilometrage)}>
          Afficher le kilométrage
        </button>

        {/* 🔽 Bouton pour appeler la fonction demarrer */}
        <button onClick={this.props.demarrer}>
          Démarrer
        </button>
      </div>
    );
  }
}

export default Car;
```

