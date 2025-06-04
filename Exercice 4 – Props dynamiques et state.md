## Exercice 4 – Props dynamiques et `state`

## Objectifs pédagogiques :

* Comprendre la relation entre les `props` et le `state`
* Savoir capturer des entrées utilisateur et les transférer à un composant enfant
* Gérer l'état dans un composant parent pour alimenter dynamiquement ses enfants

<br/>

### Contexte :

On souhaite améliorer le composant `Car` de l'exercice précédent pour qu’il affiche les valeurs **non plus codées en dur**, mais transmises **dynamiquement** via des champs de formulaire.



### Consignes :

1. Dans le composant `App.js`, ajoutez **trois champs `input`** pour que l’utilisateur puisse saisir :

   * la **couleur** de la voiture
   * la **marque**
   * le **kilométrage**

2. Utilisez l’état local (`state`) de `App.js` pour stocker ces valeurs au fur et à mesure de la saisie.

3. Transmettez ces valeurs à `Car` via les props, comme suit :

   ```jsx
   <Car
     couleur={valeurCouleur}
     marque={valeurMarque}
     kilometrage={valeurKilometrage}
     demarrer={...}
   />
   ```

4. Le composant `Car` **ne doit pas être modifié**. Il doit continuer à recevoir et afficher les valeurs via `props` comme dans l’exercice 2.

<br/>

### Résultat attendu :

* Les informations affichées dans le composant `Car` changent **en direct** selon ce que l’utilisateur saisit dans les champs.
* Le composant `Car` reste réutilisable avec **différentes données**.
* Aucune logique d’état (`useState` ou `this.state`) ne doit être ajoutée à `Car.js`.








<br/ >

# Correction de l'exercice 4 : Props dynamiques et `state`


* Fichiers complets : `App.js` et `Car.js`
* Ajouts clairs avec `// 🔽`
* Architecture professionnelle et 100% fonctionnelle

##  Structure du projet

```
exercice-voiture/
├── src/
│   ├── App.js          ← Composant principal avec `state` et `input`
│   ├── Car.js          ← Composant enfant recevant les `props`
│   └── index.js        ← Point d’entrée (inchangé)
```



## 📄 Fichier : `src/Car.js`

```jsx
import React from 'react';

class Car extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Car</h2>

        {/* 🔽 Affichage des props */}
        <p>Couleur : {this.props.couleur}</p>
        <p>Marque : {this.props.marque}</p>
        <p>Kilométrage : {this.props.kilometrage}</p>

        {/* 🔽 Boutons liés aux props */}
        <button onClick={() => console.log(this.props.couleur)}>
          Afficher la couleur
        </button>

        <button onClick={() => console.log(this.props.marque)}>
          Afficher la marque
        </button>

        <button onClick={() => console.log(this.props.kilometrage)}>
          Afficher le kilométrage
        </button>

        <button onClick={this.props.demarrer}>
          Démarrer
        </button>
      </div>
    );
  }
}

export default Car;
```



## 📄 Fichier : `src/App.js`

```jsx
import React from 'react';
import Car from './Car';

class App extends React.Component {
  // 🔽 Déclaration de l'état local
  state = {
    couleur: '',
    marque: '',
    kilometrage: ''
  };

  // 🔽 Fonction transmise à Car
  handleDemarrer = () => {
    console.log("La voiture démarre dynamiquement");
  };

  // 🔽 Mise à jour du state à la saisie
  handleChange = (event) => {
    this.setState({
      [event.target.name]: event.target.value
    });
  };

  render() {
    return (
      <div>
        <h1>Saisie dynamique des données de la voiture</h1>

        {/* 🔽 Formulaire contrôlé */}
        <input
          type="text"
          name="couleur"
          placeholder="Couleur"
          value={this.state.couleur}
          onChange={this.handleChange}
        />
        <br />
        <input
          type="text"
          name="marque"
          placeholder="Marque"
          value={this.state.marque}
          onChange={this.handleChange}
        />
        <br />
        <input
          type="text"
          name="kilometrage"
          placeholder="Kilométrage"
          value={this.state.kilometrage}
          onChange={this.handleChange}
        />
        <hr />

        {/* 🔽 Appel dynamique de Car avec les valeurs du state */}
        <Car
          couleur={this.state.couleur}
          marque={this.state.marque}
          kilometrage={this.state.kilometrage}
          demarrer={this.handleDemarrer}
        />
      </div>
    );
  }
}

export default App;
```



##  Résultat attendu (fonctionnement)

* L’utilisateur entre des données dans les 3 champs texte.
* Ces données sont stockées dans le `state` de `App`.
* Les props sont automatiquement transmises à `Car`, sans avoir à recharger.
* Le composant `Car` **ne contient aucune logique d’état**.



