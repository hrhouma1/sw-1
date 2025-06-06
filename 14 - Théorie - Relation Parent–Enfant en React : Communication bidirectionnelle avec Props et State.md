# Partie 1


<br/>




##  Objectif :

* Comprendre le passage de **props (chaînes, nombres, booléens, fonctions)** du parent à l’enfant.
* Utiliser un composant enfant pour afficher des données et appeler une fonction du parent.



##  Exemple 

### 🗂 Fichier `App.js` (Composant Parent)

```jsx
import React, { Component } from "react";
import Enfant from "./Enfant"; // On importe le composant enfant

class App extends Component {
  // Fonction à passer à l'enfant comme prop
  direBonjour = () => {
    console.log("Bonjour depuis le parent !");
  };

  render() {
    return (
      <div>
        <h1>Composant Parent</h1>

        {/* On passe différentes données à l'enfant :
            - une chaîne
            - un nombre
            - un booléen
            - une fonction */}
        <Enfant
          nom="Alice"
          age={12}
          estConnecte={true}
          action={this.direBonjour}
        />
      </div>
    );
  }
}

export default App;
```



### 🧒 Fichier `Enfant.js` (Composant Enfant)

```jsx
import React, { Component } from "react";

class Enfant extends Component {
  render() {
    // On récupère les props envoyées par le parent
    const { nom, age, estConnecte, action } = this.props;

    return (
      <div>
        <h2>Composant Enfant</h2>

        {/* Affichage des props */}
        <p>Nom : {nom}</p>
        <p>Âge : {age} ans</p>
        <p>
          Statut : {estConnecte ? "Connecté(e)" : "Déconnecté(e)"}
        </p>

        {/* Bouton qui appelle la fonction transmise en prop */}
        <button onClick={action}>Appeler le parent</button>
      </div>
    );
  }
}

export default Enfant;
```



##  Ce qu’il faut retenir

| Élément             | Description                                      |
| ------------------- | ------------------------------------------------ |
| `props.nom`         | Chaine transmise au composant enfant             |
| `props.age`         | Nombre transmis                                  |
| `props.estConnecte` | Booléen transmis                                 |
| `props.action`      | Fonction passée comme prop, appelée par l’enfant |



##  Résultat attendu

Lorsque l’application est lancée :

1. Le composant `App` affiche le composant `Enfant`.
2. Le composant `Enfant` affiche le nom, l'âge, le statut.
3. Un bouton permet d’exécuter la fonction `direBonjour` du parent.
4. Un message s’affiche dans la console du navigateur :
   👉 **"Bonjour depuis le parent !"**



<br/>

# Partie 2 - flux inverse

##  Objectif pédagogique :

* Comprendre **le flux inverse** : comment **un enfant peut informer un parent** d’un événement.
* Utiliser une **fonction passée par le parent** que l’enfant va appeler avec **des données**.



## Étape 1 – Mise à jour du fichier `App.js` (composant parent)

```jsx
import React, { Component } from "react";
import Enfant from "./Enfant";

class App extends Component {
  // Fonction que l'enfant pourra appeler en lui passant un message
  recevoirMessage = (message) => {
    console.log("Message reçu de l'enfant :", message);
  };

  render() {
    return (
      <div>
        <h1>Composant Parent</h1>

        {/* En plus des anciennes props, on passe la nouvelle fonction à l’enfant */}
        <Enfant
          nom="Alice"
          age={12}
          estConnecte={true}
          action={() => console.log("Bonjour depuis le parent !")}
          envoyerMessage={this.recevoirMessage}
        />
      </div>
    );
  }
}

export default App;
```



## 🧒 Étape 2 – Mise à jour du fichier `Enfant.js` (composant enfant)

```jsx
import React, { Component } from "react";

class Enfant extends Component {
  // Fonction appelée lorsqu'on clique sur le bouton
  envoyerInfoAuParent = () => {
    const message = "Papa, j’ai cliqué sur le bouton !";
    
    // Appelle de la fonction que le parent a fournie
    this.props.envoyerMessage(message);
  };

  render() {
    const { nom, age, estConnecte, action } = this.props;

    return (
      <div>
        <h2>Composant Enfant</h2>

        <p>Nom : {nom}</p>
        <p>Âge : {age} ans</p>
        <p>
          Statut : {estConnecte ? "Connecté(e)" : "Déconnecté(e)"}
        </p>

        <button onClick={action}>Appeler le parent</button>

        {/* Nouveau bouton pour envoyer un message au parent */}
        <button onClick={this.envoyerInfoAuParent}>
          Envoyer un message au parent
        </button>
      </div>
    );
  }
}

export default Enfant;
```



##  Résultat attendu

Quand tu cliques sur :

1. **"Appeler le parent"** → `console.log("Bonjour depuis le parent !")`
2. **"Envoyer un message au parent"** → `console.log("Message reçu de l'enfant : Papa, j’ai cliqué sur le bouton !")`



##  Ce qu’on a appris

| Élément                  | Rôle                                                 |
| ------------------------ | ---------------------------------------------------- |
| `envoyerMessage`         | Fonction définie dans le parent                      |
| `props.envoyerMessage()` | Appelée par l’enfant pour envoyer des données        |
| `console.log(...)`       | Représente une action possible du parent en réaction |



<br/>

# Partie 3 - le composant enfant modifie dynamiquement un `state` du parent** via une fonction passée en `props`.

##  Objectif 

* Comprendre comment **le parent délègue à l’enfant une fonction pour modifier son propre état (`state`)**.
* Voir en action **la mise à jour dynamique du `state` dans le parent**, en réponse à une action dans l’enfant.



## Étape 1 – Mise à jour du `App.js` (le parent gère un `state`)

```jsx
import React, { Component } from "react";
import Enfant from "./Enfant";

class App extends Component {
  // 🔽 Le parent a maintenant un état local
  state = {
    messageDepuisEnfant: ""
  };

  // 🔽 Fonction que l'enfant utilisera pour mettre à jour le state
  mettreAJourMessage = (nouveauMessage) => {
    this.setState({ messageDepuisEnfant: nouveauMessage });
  };

  render() {
    return (
      <div>
        <h1>Composant Parent</h1>

        {/* 🔽 Affichage de l’état mis à jour par l’enfant */}
        <p><strong>Message de l’enfant :</strong> {this.state.messageDepuisEnfant}</p>

        {/* 🔽 Passage de la fonction de mise à jour comme prop */}
        <Enfant
          nom="Alice"
          age={12}
          estConnecte={true}
          action={() => console.log("Bonjour depuis le parent !")}
          envoyerMessage={this.mettreAJourMessage}
        />
      </div>
    );
  }
}

export default App;
```



##  Étape 2 – Mise à jour du `Enfant.js` (l’enfant déclenche une mise à jour du parent)

```jsx
import React, { Component } from "react";

class Enfant extends Component {
  // 🔽 Fonction appelée lorsqu’on clique sur le bouton
  envoyerInfoAuParent = () => {
    const message = "Bonjour Papa ! J'ai appuyé sur le bouton.";
    
    // 🔽 Appel de la fonction que le parent a passée
    this.props.envoyerMessage(message);
  };

  render() {
    const { nom, age, estConnecte, action } = this.props;

    return (
      <div>
        <h2>Composant Enfant</h2>

        <p>Nom : {nom}</p>
        <p>Âge : {age} ans</p>
        <p>
          Statut : {estConnecte ? "Connecté(e)" : "Déconnecté(e)"}
        </p>

        <button onClick={action}>Appeler le parent</button>

        {/* 🔽 Bouton qui modifie le state du parent */}
        <button onClick={this.envoyerInfoAuParent}>
          Modifier le message du parent
        </button>
      </div>
    );
  }
}

export default Enfant;
```



##  Résultat attendu dans le navigateur

* Le parent affiche :

  ```txt
  Message de l’enfant :
  ```
* L’enfant clique sur le bouton "Modifier le message du parent" → le texte devient :

  ```txt
  Message de l’enfant : Bonjour Papa ! J'ai appuyé sur le bouton.
  ```



##  Ce qu’on a appris

| Élément                         | Rôle                                            |
| ------------------------------- | ----------------------------------------------- |
| `state.messageDepuisEnfant`     | État local du parent                            |
| `mettreAJourMessage()`          | Fonction dans le parent qui modifie le state    |
| `props.envoyerMessage(message)` | L’enfant appelle cette fonction avec une valeur |
| `setState(...)`                 | Déclenche le rendu dynamique du parent          |



