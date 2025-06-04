# LABORATOIRE 1 (SUITE) – UNE DEUXIÈME APPLICATION REACT

---

## Étape 6 – Ajoutez de la dynamicité (STATES - ÉTATS) dans LAB 2

---

### 1 – On ajoute le `state` dans le composant

```jsx
class Recherche extends Component {
  state = { depart: "", categorie: "" }
}
```

---

### 2 – On ajoute l’attribut `value` dans les composants `<Select>` de Semantic UI React

```jsx
<Select
  placeholder="Choisissez un département"
  options={optionsDpt}
  value={this.state.depart}
/>

<Select
  placeholder="Choisissez une administration"
  options={optionsType}
  value={this.state.categorie}
/>
```

---

### 3 – Aucun élément n’a été modifié visuellement

Nous devons maintenant associer des fonctions qui permettront de **changer les états** en fonction de la sélection de l’utilisateur.

---

### 4 – Création des deux fonctions pour modifier le `state`

#### Première fonction :

```jsx
onDepartementChange = (e, data) => {
  this.setState({ depart: data.value });
}
```

#### Deuxième fonction :

```jsx
onCategorieChange = (e, data) => {
  this.setState({ categorie: data.value });
}
```

---

### 5 – Ajout des fonctions dans les composants `<Select>`

Il faut relier nos fonctions aux événements :

```jsx
<Select
  placeholder="Choisissez un département"
  options={optionsDpt}
  value={this.state.depart}
  onChange={this.onDepartementChange}
/>

<Select
  placeholder="Choisissez une administration"
  options={optionsType}
  value={this.state.categorie}
  onChange={this.onCategorieChange}
/>
```

---

### 6 – Ajout d’un `console.log` pour observer l’évolution des états

```jsx
render() {
  console.log(this.state.depart, this.state.categorie);
  ...
}
```

---

### 7 – Code complet final de `Recherche.js`

> N’oubliez pas d’examiner votre console JavaScript et de jouer avec les composants `<Select>` pour changer les valeurs.

```jsx
import { Component } from "react";
import { Button, Select } from "semantic-ui-react";

class Recherche extends Component {

  state = { depart: "", categorie: "" }

  onDepartementChange = (e, data) => {
    this.setState({ depart: data.value });
  }

  onCategorieChange = (e, data) => {
    this.setState({ categorie: data.value });
  }

  render() {
    console.log(this.state.depart, this.state.categorie);

    const optionsDpt = [
      { value: "44", key: "44", text: "Loire Atlantique" },
      { value: "49", key: "49", text: "Maine et Loire" },
      { value: "53", key: "53", text: "Mayenne" },
      { value: "72", key: "72", text: "Sarthe" },
      { value: "85", key: "85", text: "Vendée" }
    ];

    const optionsType = [
      { value: "cpam", key: "cpam", text: "Caisse primaire d'assurance maladie" },
      { value: "cci", key: "cci", text: "Chambre de commerce et d'industrie" },
      { value: "crous", key: "crous", text: "Crous et ses antennes" }
    ];

    return (
      <div className="recherche">
        <Select
          placeholder="Choisissez un département"
          options={optionsDpt}
          value={this.state.depart}
          onChange={this.onDepartementChange}
        />
        <Select
          placeholder="Choisissez une administration"
          options={optionsType}
          value={this.state.categorie}
          onChange={this.onCategorieChange}
        />
        <Button primary>
          Lancer la recherche
        </Button>
        <Button secondary>
          Vider la recherche
        </Button>
      </div>
    );
  }
}

export default Recherche;
```


### Fin de l'Étape 6 – Ajoutez de la dynamicité (STATES - ÉTATS)













<br/>
<br/>















# Étape 7 – Ajouter un peu de CSS

---

## 1. Objectif

Nous avons remarqué que les composants graphiques (les deux `<Select>` et les deux `<Button>`) sont **trop collés visuellement**.

L’objectif est de :

* Espacer correctement les éléments
* Organiser leur disposition en **ligne horizontale**
* Utiliser un fichier CSS externe

---

## 2. Où appliquer le CSS ?

Le CSS sera appliqué au composant `Recherche.js`. On créera donc un fichier `Recherche.css` **dans le même dossier** que `Recherche.js`.

**Structure mise à jour** :

```
/src
├── /Composants
│   ├── Recherche.js
│   └── Recherche.css  ← ici
```

---

## 3. Contenu du fichier `Recherche.css`

Créer un fichier nommé `Recherche.css` dans `/src/Composants/` avec le contenu suivant :

```css
.recherche {
  margin: 15px 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
}
```

---

### Explication du code CSS :

* `margin: 15px 0;` → ajoute un espacement vertical
* `width: 100%;` → la div prendra toute la largeur disponible
* `display: flex;` → les éléments enfants seront placés **en ligne**
* `justify-content: space-between;` → les éléments seront **espacés uniformément**

---

## 4. Importation du CSS dans `Recherche.js`

Dans le fichier `Recherche.js`, ajouter en haut :

```jsx
import './Recherche.css';
```

Cela permet à React d’appliquer les styles définis dans `Recherche.css`.

---

## 5. Vérification de `className`

S’assurer que la `<div>` englobant les composants dans `Recherche.js` possède bien le nom de classe défini en CSS :

```jsx
return (
  <div className="recherche">
    ...
  </div>
);
```

---

## 6. Résumé des modifications

* **Création du fichier** : `Recherche.css`
* **Ajout du style CSS** pour `.recherche`
* **Importation du fichier CSS** dans `Recherche.js`
* **Utilisation de `className="recherche"`** sur le conteneur principal

---

## 7. Code complet final de `Recherche.js` (mis à jour avec le CSS)

```jsx
import { Component } from "react";
import { Button, Select } from "semantic-ui-react";
import './Recherche.css';

class Recherche extends Component {

  state = { depart: "", categorie: "" }

  onDepartementChange = (e, data) => {
    this.setState({ depart: data.value });
  }

  onCategorieChange = (e, data) => {
    this.setState({ categorie: data.value });
  }

  render() {

    console.log(this.state.depart, this.state.categorie);

    const optionsDpt = [
      { value: "44", key: "44", text: "Loire Atlantique" },
      { value: "49", key: "49", text: "Maine et Loire" },
      { value: "53", key: "53", text: "Mayenne" },
      { value: "72", key: "72", text: "Sarthe" },
      { value: "85", key: "85", text: "Vendée" }
    ];

    const optionsType = [
      { value: "cpam", key: "cpam", text: "Caisse primaire d'assurance maladie" },
      { value: "cci", key: "cci", text: "Chambre de commerce et d'industrie" },
      { value: "crous", key: "crous", text: "Crous et ses antennes" }
    ];

    return (
      <div className="recherche">
        <Select
          placeholder="Choisissez un département"
          options={optionsDpt}
          value={this.state.depart}
          onChange={this.onDepartementChange}
        />
        <Select
          placeholder="Choisissez une administration"
          options={optionsType}
          value={this.state.categorie}
          onChange={this.onCategorieChange}
        />
        <Button primary>
          Lancer la recherche
        </Button>
        <Button secondary>
          Vider la recherche
        </Button>
      </div>
    );
  }
}

export default Recherche;
```

---

## 8. Vérification dans le navigateur

Après avoir enregistré les fichiers :

* Ouvrez votre navigateur
* Rechargez la page (Ctrl + R)
* Observez que les éléments `<Select>` et `<Button>` sont désormais bien espacés et organisés en ligne

---

## Fin de l'Étape 7 – Ajouter un peu de CSS


<br/>
<br/>

# Étape 8 – Préparation de l’appel de l’API (Partie 1)

---

## 1. Objectif

L’objectif de cette étape est de **préparer l’infrastructure de votre application React** afin de **pouvoir intégrer des appels API**. Ces appels vous permettront plus tard de **récupérer des données réelles** (établissements publics) en fonction du département et du type d’administration choisis.

---

## 2. Situation actuelle

À ce stade, vous avez :

* Un composant `Recherche.js` qui contient :

  * Deux champs `<Select>` avec des options statiques
  * Un `state` qui mémorise `depart` et `categorie`
  * Deux boutons : **Lancer la recherche** et **Vider la recherche**

Mais pour lancer une recherche réelle via une **API externe**, il faut :

* **Transférer les données du composant `Recherche` vers `App.js`**
* **Gérer l’état des données dans le composant principal `App.js`**
* **Préparer la fonction d’appel API dans `App.js`**

---

## 3. Création d’un dossier `/Composants`

> Si ce n’est pas déjà fait, créez un dossier appelé `/Composants` dans `/src` :

```
/src
├── /Composants
│   ├── Recherche.js
│   └── Recherche.css
├── App.js
```

---

## 4. Mise à jour de l’import dans `App.js`

Il faut maintenant modifier `App.js` pour importer `Recherche` à partir de son nouveau chemin :

```jsx
import Recherche from './Composants/Recherche';
```

---

## 5. Composant App : passage en composant de **type classe**

> L’appel à l’API nécessite de **gérer des états dans `App.js`**, ce qui impose d’en faire un composant **de type classe**.

### Nouveau code pour `App.js` :

```jsx
import { Component } from 'react';
import './App.css';
import Recherche from './Composants/Recherche';

class App extends Component {
  render() {
    return (
      <div className="App">
        <h1> Annuaire </h1>
        <Recherche />
      </div>
    );
  }
}

export default App;
```

---

## 6. Pourquoi passer App en composant classe ?

> Pour que `App.js` puisse contenir un `state` global, et y stocker les **données récupérées via l’API**, il faut que `App` :

* ait un `state` (ex. `data`, `error`)
* puisse passer une fonction à `Recherche.js` via des **props**
* puisse **mettre à jour ses états** à partir de l’interaction dans `Recherche.js`

---

## 7. À faire maintenant

* Passer une **fonction en props** à `Recherche.js` (voir Étape 8, Partie 2)
* Faire en sorte que cette fonction soit appelée au clic du bouton “Lancer la recherche”
* Observer dans la console si les bonnes données (département + catégorie) sont transmises

---

## 8. Résumé pédagogique

| Élément                               | Statut                                         |
| ------------------------------------- | ---------------------------------------------- |
| Composant `App`                       | Transformé en classe                           |
| Composant `Recherche`                 | Toujours enfant                                |
| Dossier `/Composants`                 | Créé                                           |
| Fichier CSS externe (`Recherche.css`) | Importé                                        |
| Objectif de cette étape               | Propager les actions de `Recherche` vers `App` |

---

## 9. Note importante

Avant de continuer avec l’intégration réelle de l’API, **vous devez parfaitement comprendre les props, le `state` et les composants de type classe**.

**Il est fortement recommandé** à ce stade de **faire l’évaluation formative** (les 3 exercices sur les props et states) avant d’aller plus loin.

---

## Fin de l’Étape 8 – Préparation de l’appel de l’API (Partie 1)




<br/>
<br/>









# Étape 8 – Préparation de l’appel de l’API (Partie 2)

---

## 1. Objectif

Dans cette deuxième partie, vous allez :

* Transférer les **états `depart` et `categorie`** de `Recherche.js` vers `App.js`
* Utiliser une **fonction passée en props**
* Préparer `App.js` à recevoir les données et à effectuer plus tard l’appel API

---

## 2. Problème : comment faire remonter un état d’un composant enfant vers un composant parent ?

En React :

* Les **props descendent** (de `App.js` vers `Recherche.js`)
* Les **actions remontent** (on envoie une fonction depuis `App.js`, qu’on appelle depuis `Recherche.js`)

---

## 3. Solution

1. Dans `App.js`, on définit une fonction nommée `onChercher(a, b)`
2. On passe cette fonction à `Recherche.js` comme une props
3. Dans `Recherche.js`, cette fonction est appelée avec les états `depart` et `categorie` lorsqu’on clique sur le bouton "Lancer la recherche"

---

## 4. Code dans `App.js`

### Définir la fonction `onChercher`

```jsx
onChercher = (a, b) => {
  console.log(a, b);  // Affiche les valeurs reçues
}
```

### Passer la fonction comme props à `Recherche`

```jsx
<Recherche onJeMetCequeJeVeux={this.onChercher} />
```

---

## 5. Code dans `Recherche.js`

### Modifier le bouton "Lancer la recherche" :

```jsx
<Button
  primary
  onClick={() => this.props.onJeMetCequeJeVeux(this.state.depart, this.state.categorie)}
>
  Lancer la recherche
</Button>
```

Cela signifie que quand l’utilisateur clique sur le bouton, on appelle la fonction reçue depuis `App.js` (via la props `onJeMetCequeJeVeux`), et on lui passe en paramètres les deux états.

---

## 6. Code complet

### `App.js`

```jsx
import { Component } from 'react';
import './App.css';
import Recherche from './Composants/Recherche';

class App extends Component {

  state = { data: [], error: '' }

  onChercher = (a, b) => {
    console.log(a, b);  // Exemple : "49", "cpam"
  }

  render() {
    return (
      <div className="App">
        <h1> Annuaire </h1>
        <Recherche onJeMetCequeJeVeux={this.onChercher} />
      </div>
    );
  }
}

export default App;
```

---

### `Recherche.js`

```jsx
import { Component } from "react";
import { Button, Select } from "semantic-ui-react";
import './Recherche.css';

class Recherche extends Component {

  state = { depart: "", categorie: "" }

  onDepartementChange = (e, data) => {
    this.setState({ depart: data.value });
  }

  onCategorieChange = (e, data) => {
    this.setState({ categorie: data.value });
  }

  render() {
    console.log(this.state.depart, this.state.categorie);

    const optionsDpt = [
      { value: "44", key: "44", text: "Loire Atlantique" },
      { value: "49", key: "49", text: "Maine et Loire" },
      { value: "53", key: "53", text: "Mayenne" },
      { value: "72", key: "72", text: "Sarthe" },
      { value: "85", key: "85", text: "Vendée" }
    ];

    const optionsType = [
      { value: "cpam", key: "cpam", text: "Caisse primaire d'assurance maladie" },
      { value: "cci", key: "cci", text: "Chambre de commerce et d'industrie" },
      { value: "crous", key: "crous", text: "Crous et ses antennes" }
    ];

    return (
      <div className="recherche">
        <Select
          placeholder="Choisissez un département"
          options={optionsDpt}
          value={this.state.depart}
          onChange={this.onDepartementChange}
        />
        <Select
          placeholder="Choisissez une administration"
          options={optionsType}
          value={this.state.categorie}
          onChange={this.onCategorieChange}
        />
        <Button
          primary
          onClick={() => this.props.onJeMetCequeJeVeux(this.state.depart, this.state.categorie)}
        >
          Lancer la recherche
        </Button>
        <Button secondary>
          Vider la recherche
        </Button>
      </div>
    );
  }
}

export default Recherche;
```

---

## 7. Résultat attendu

Lorsque vous :

* sélectionnez un **département**
* sélectionnez une **administration**
* cliquez sur **Lancer la recherche**

→ les valeurs sélectionnées sont **transmises à App.js**
→ elles s'affichent dans la **console du navigateur**

---

## 8. Vérifications à faire

* Aucun message d’erreur dans la console ?
* Le clic sur le bouton affiche bien deux valeurs ?
* Le `console.log()` dans `App.js` fonctionne ?
* Les props sont bien nommées et passées ?

---

## 9. Remarque pédagogique

À ce stade, **les données n’ont pas encore été récupérées depuis une API**, mais le **mécanisme de communication inter-composants est en place**, ce qui est fondamental pour la suite.



## Fin de l’Étape 8 – Préparation de l’appel de l’API (Partie 2)


<br/>
<br/>

# Étape 9 – L’API

---

## 1. Objectif

Après avoir transféré les données depuis le composant enfant `Recherche.js` vers le composant parent `App.js`, nous allons maintenant **remplacer le `console.log()` par un appel API réel**.

---

## 2. API utilisée

L’API utilisée est celle des **établissements publics français** :

```
https://etablissements-publics.api.gouv.fr/v3/departements/{departement}/{categorie}
```

Exemple :

```
https://etablissements-publics.api.gouv.fr/v3/departements/49/cci
```

Cette URL retourne une liste d’établissements publics pour le département 49 et la catégorie `cci`.

---

## 3. États dans `App.js`

On va utiliser deux états dans le composant `App.js` :

```jsx
state = {
  data: [],     // Pour stocker les données retournées par l’API
  error: ''     // Pour afficher une erreur s’il y en a une
}
```

---

## 4. Mise à jour de la fonction `onChercher`

On remplace le `console.log(a, b)` par un `fetch` vers l’API :

```jsx
onChercher = async (a, b) => {
  if (a && b) {
    try {
      let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
      let donnee = await reponse.json();
      console.log(donnee); // Test pour voir la structure retournée
    } catch (e) {
      // Erreur technique (réseau, API non disponible)
    }
  } else {
    // Un des deux champs est vide
  }
}
```

---

## 5. Code complet de `App.js` (mis à jour à cette étape)

```jsx
import { Component } from 'react';
import './App.css';
import Recherche from './Composants/Recherche';

class App extends Component {

  state = { data: [], error: '' }

  onChercher = async (a, b) => {
    if (a && b) {
      try {
        let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
        let donnee = await reponse.json();
        console.log(donnee); // Affichage temporaire
      } catch (e) {
        // Erreur de récupération des données (non gérée ici)
      }
    } else {
      // Erreur : un champ est vide (non gérée ici)
    }
  }

  render() {
    return (
      <div className="App">
        <h1> Annuaire </h1>
        <Recherche onJeMetCequeJeVeux={this.onChercher} />
      </div>
    );
  }
}

export default App;
```

---

## 6. Structure des données retournées

Une fois l’API appelée, le contenu de `donnee` est de la forme :

```json
{
  "features": [
    {
      "properties": {
        "id": "etablissement1",
        "nom": "CPAM de Nantes",
        "telephone": "01 02 03 04 05",
        "email": "nantes@cpam.fr"
      }
    },
    {
      "properties": {
        "id": "etablissement2",
        "nom": "CPAM de Saint-Nazaire",
        "telephone": "02 03 04 05 06",
        "email": "saintnazaire@cpam.fr"
      }
    }
  ]
}
```

> On observe que la vraie liste d'établissements est accessible via `donnee.features`.

---

## 7. Vérification dans le navigateur

* Ouvrir la console du navigateur
* Sélectionner un département et une administration
* Cliquer sur “Lancer la recherche”
* Vérifier que les données API sont affichées dans la console

---

## 8. Résumé pédagogique

| Élément                 | Rôle                                           |
| ----------------------- | ---------------------------------------------- |
| `fetch(...)`            | Appel vers l’API                               |
| `await reponse.json()`  | Conversion de la réponse                       |
| `console.log(donnee)`   | Visualisation brute des données                |
| `data: []` dans `state` | Sera utilisé à l’étape suivante pour affichage |
| `error: ''`             | Prévu pour gestion des erreurs (étape 10)      |

---

## Fin de l’Étape 9 – L’API



<br/>
<br/>








# Étape 10 – setState : États `data` + `error`, gestion des erreurs

---

## 1. Objectif

Dans l’étape précédente, nous avons affiché les données de l’API dans la console.
Dans cette étape, nous allons :

* Stocker les résultats dans `this.state.data`
* Gérer les erreurs réseau ou de validation
* Utiliser `setState()` pour mettre à jour l’interface

---

## 2. Rappel des états dans `App.js`

```jsx
state = {
  data: [],     // Liste d'établissements publics retournés
  error: ''     // Message d’erreur à afficher
}
```

---

## 3. Mise à jour de la fonction `onChercher`

Nous allons :

* Appeler l’API avec `fetch`
* Mettre à jour `data` avec `donnee.features`
* Mettre à jour `error` si nécessaire

### Nouvelle version :

```jsx
onChercher = async (a, b) => {
  if (a && b) {
    try {
      let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
      let donnee = await reponse.json();
      this.setState({ data: donnee.features, error: '' });
    } catch (e) {
      this.setState({ error: "Connexion non aboutie avec l'API" });
    }
  } else {
    this.setState({ error: "Merci de choisir les deux champs" });
  }
}
```

---

## 4. Pourquoi utiliser `donnee.features` ?

L’objet retourné par l’API contient un tableau d’établissements dans la propriété `features`.

Extrait :

```json
{
  "features": [
    { "properties": { "id": "1", "nom": "...", ... } },
    { "properties": { "id": "2", "nom": "...", ... } }
  ]
}
```

Il faut donc accéder directement à `donnee.features` pour avoir le tableau exploitable.

---

## 5. Ajouter un `console.log()` pour observer

Dans la méthode `render()` :

```jsx
render() {
  console.log(this.state.data, this.state.error);
  return (
    ...
  );
}
```

Cela permet de vérifier :

* Que les données sont bien stockées dans `data`
* Que les messages d’erreurs sont correctement envoyés dans `error`

---

## 6. Code complet de `App.js` à la fin de cette étape

```jsx
import { Component } from 'react';
import './App.css';
import Recherche from './Composants/Recherche';

class App extends Component {

  state = { data: [], error: '' }

  onChercher = async (a, b) => {
    if (a && b) {
      try {
        let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
        let donnee = await reponse.json();
        this.setState({ data: donnee.features, error: '' });
      } catch (e) {
        this.setState({ error: "Connexion non aboutie avec l'API" });
      }
    } else {
      this.setState({ error: "Merci de choisir les deux champs" });
    }
  }

  render() {
    console.log(this.state.data, this.state.error);
    return (
      <div className="App">
        <h1> Annuaire </h1>
        <Recherche onJeMetCequeJeVeux={this.onChercher} />
      </div>
    );
  }
}

export default App;
```

---

## 7. Résultat attendu

| Cas                             | Résultat                                              |
| ------------------------------- | ----------------------------------------------------- |
| Les deux sélections sont faites | Données reçues et stockées dans `state.data`          |
| Un champ est vide               | Message d’erreur `"Merci de choisir les deux champs"` |
| L’API ne répond pas             | Message d’erreur `"Connexion non aboutie avec l'API"` |

---

## 8. Résumé pédagogique

* L’état `data` permet d’afficher dynamiquement des résultats
* L’état `error` permet de prévenir l’utilisateur en cas de problème
* `setState()` est utilisé pour mettre à jour l’interface
* `render()` est automatiquement relancé à chaque mise à jour



## Fin de l’Étape 10 – setState : États `data` + `error`


<br/>
<br/>

# Étape 11 – Ajout de messages avec Semantic UI (gestion des erreurs visuelles)

---

## 1. Objectif

Nous avons stocké les erreurs dans `this.state.error` dans `App.js`.
Nous allons maintenant :

* Afficher ce message dans l’interface utilisateur
* Utiliser le composant `<Message>` de Semantic UI React

---

## 2. Le composant `<Message>` de Semantic UI

Semantic UI propose des messages stylés facilement intégrables :

```jsx
<Message warning>Texte du message</Message>
```

---

## 3. Affichage conditionnel dans `render()`

Dans `App.js`, on modifie la méthode `render()` pour afficher dynamiquement le message si une erreur existe :

```jsx
{this.state.error ? <Message warning>{this.state.error}</Message> : undefined}
```

---

## 4. Import du composant `Message`

Assurez-vous d’importer `Message` depuis `semantic-ui-react` en haut de `App.js` :

```jsx
import { Message } from 'semantic-ui-react';
```

---

## 5. Réinitialisation de l'erreur

Il faut **vider l’erreur** (mettre `''`) à chaque nouvel appel réussi à l’API :

```jsx
this.setState({ data: donnee.features, error: '' });
```

Cela évite que l’erreur reste affichée alors que la requête suivante s’est bien déroulée.

---

## 6. Code complet de `App.js` à la fin de cette étape

```jsx
import { Component } from 'react';
import { Message } from 'semantic-ui-react';
import './App.css';
import Recherche from './Composants/Recherche';

class App extends Component {

  state = { data: [], error: '' }

  onChercher = async (a, b) => {
    if (a && b) {
      try {
        let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
        let donnee = await reponse.json();
        this.setState({ data: donnee.features, error: '' });
      } catch (e) {
        this.setState({ error: "Connexion non aboutie avec l'API" });
      }
    } else {
      this.setState({ error: "Merci de choisir les deux champs" });
    }
  }

  render() {
    console.log(this.state.data, this.state.error);
    return (
      <div className="App">
        <h1> Rechercher un annuaire !</h1>

        <Recherche onJeMetCequeJeVeux={this.onChercher} />

        {this.state.error ? <Message warning>{this.state.error}</Message> : undefined}
      </div>
    );
  }
}

export default App;
```

---

## 7. Résultat attendu

| Situation      | Résultat visuel                                               |
| -------------- | ------------------------------------------------------------- |
| Erreur API     | Message jaune avec texte : *Connexion non aboutie avec l'API* |
| Champ vide     | Message jaune avec texte : *Merci de choisir les deux champs* |
| Données reçues | Message supprimé automatiquement                              |

---

## 8. Résumé pédagogique

| Élément                   | Rôle                                                  |
| ------------------------- | ----------------------------------------------------- |
| `<Message warning>`       | Affiche les erreurs de manière claire à l’utilisateur |
| `error !== ''`            | Condition qui déclenche l’affichage du message        |
| `setState({ error: '' })` | Réinitialise l’état si tout est correct               |
| `import { Message }`      | Obligation d’importer le composant de Semantic UI     |



## Fin de l’Étape 11 – Ajout de messages avec Semantic UI


<br/>
<br/>

# Étape 12 – Vider la recherche



## 1. Objectif

Ajouter un bouton "Vider la recherche" dans le composant `Recherche.js` qui :

* Vide les **résultats de l’API** (`data`)
* Supprime les **erreurs** (`error`)
* Réinitialise l’interface



## 2. Contexte

Dans `App.js`, nous avons :

```jsx
state = {
  data: [],     // Résultats API
  error: ''     // Message d’erreur
}
```

Nous voulons pouvoir réinitialiser ces deux valeurs à vide quand l’utilisateur clique sur un bouton "Vider".



## 3. Étapes à suivre

### a. Créer une fonction `onVider()` dans `App.js`

Cette fonction va vider les deux états :

```jsx
onVider = () => {
  this.setState({ data: [], error: '' });
}
```



### b. Passer cette fonction comme **props** à `Recherche.js`

Dans la méthode `render()` de `App.js`, ajouter :

```jsx
<Recherche
  onJeMetCequeJeVeux={this.onChercher}
  onEmpty={this.onVider}
/>
```


### c. Modifier `Recherche.js` pour utiliser la props `onEmpty`

Dans le bouton secondaire :

```jsx
<Button secondary onClick={() => this.props.onEmpty()}>
  Vider la recherche
</Button>
```



## 4. Code complet final de `App.js` après cette étape

```jsx
import { Component } from 'react';
import { Message } from 'semantic-ui-react';
import './App.css';
import Recherche from './Composants/Recherche';

class App extends Component {

  state = { data: [], error: '' }

  onChercher = async (a, b) => {
    if (a && b) {
      try {
        let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
        let donnee = await reponse.json();
        this.setState({ data: donnee.features, error: '' });
      } catch (e) {
        this.setState({ error: "Connexion non aboutie avec l'API" });
      }
    } else {
      this.setState({ error: "Merci de choisir les deux champs" });
    }
  }

  onVider = () => {
    this.setState({ data: [], error: '' });
  }

  render() {
    console.log(this.state.data, this.state.error);
    return (
      <div className="App">
        <h1> Rechercher un annuaire !</h1>

        <Recherche
          onJeMetCequeJeVeux={this.onChercher}
          onEmpty={this.onVider}
        />

        {this.state.error ? <Message warning>{this.state.error}</Message> : undefined}
      </div>
    );
  }
}

export default App;
```



## 5. Code final de `Recherche.js` (uniquement la section du bouton)

```jsx
<Button secondary onClick={() => this.props.onEmpty()}>
  Vider la recherche
</Button>
```



## 6. Résultat attendu

| Action                        | Résultat                                                                                                               |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Clic sur "Vider la recherche" | - Supprime les résultats affichés (à venir)<br>- Supprime le message d’erreur s’il existe<br>- Réinitialise la console |



## 7. Résumé pédagogique

| Élément           | Rôle                                                 |
| ----------------- | ---------------------------------------------------- |
| `onVider()`       | Réinitialise les états `data` et `error`             |
| `props.onEmpty()` | Appelle cette réinitialisation depuis `Recherche.js` |
| Bouton secondaire | Permet à l’utilisateur de recommencer proprement     |



## Fin de l’Étape 12 – Vider la recherche


<br/>
<br/>

# Étape 13 – Affichage des données avec des cartes (statique)

---

## 1. Objectif

Préparer l’**affichage visuel** des établissements publics avec des composants de type **carte (`Card`)** fournis par **Semantic UI React**.

Cette étape est **statique**, c’est-à-dire que nous allons afficher manuellement quelques cartes pour tester leur rendu **avant de les rendre dynamiques** dans l’étape suivante.

---

## 2. Étapes à suivre

---

### Étape 1 : Créer un nouveau composant `Etablissement.js`

Dans le dossier `src/Composants/`, créez un nouveau fichier :

```
Etablissement.js
```


### Étape 2 : Version minimale du composant

```jsx
const Etablissement = () => {
  return (
    <div>
      Je suis un établissement
    </div>
  );
}

export default Etablissement;
```

Cela sert uniquement de test pour l'import.



### Étape 3 : Remplacer le `<div>` par une vraie carte (`<Card>`)

```jsx
import { Card } from "semantic-ui-react";

const Etablissement = () => {
  return (
    <Card>
      <Card.Content>
        <Card.Header>
          Le nom de l'établissement
        </Card.Header>
        <Card.Meta>
          Numéro de téléphone : 01 02 03 04 05
        </Card.Meta>
        <Card.Meta>
          Adresse courriel : email@example.com
        </Card.Meta>
      </Card.Content>
    </Card>
  );
}

export default Etablissement;
```



### Étape 4 : Ajouter le composant dans `App.js`

Importer le composant `Etablissement` :

```jsx
import Etablissement from './Composants/Etablissement';
```

Puis, dans la méthode `render()` de `App.js`, juste après la `Recherche`, ajouter quelques cartes :

```jsx
<Etablissement />
<Etablissement />
<Etablissement />
```



### Étape 5 : Regrouper les cartes avec `<Card.Group>`

Toujours dans `App.js`, encapsulez vos cartes avec ce composant :

```jsx
<Card.Group>
  <Etablissement />
  <Etablissement />
  <Etablissement />
</Card.Group>
```



### Étape 6 : Code complet de `App.js` à la fin de cette étape

```jsx
import { Component } from 'react';
import { Message, Card } from 'semantic-ui-react';
import './App.css';
import Recherche from './Composants/Recherche';
import Etablissement from './Composants/Etablissement';

class App extends Component {

  state = { data: [], error: '' }

  onChercher = async (a, b) => {
    if (a && b) {
      try {
        let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
        let donnee = await reponse.json();
        this.setState({ data: donnee.features, error: '' });
      } catch (e) {
        this.setState({ error: "Connexion non aboutie avec l'API" });
      }
    } else {
      this.setState({ error: "Merci de choisir les deux champs" });
    }
  }

  onVider = () => {
    this.setState({ data: [], error: '' });
  }

  render() {
    console.log(this.state.data, this.state.error);
    return (
      <div className="App">
        <h1> Rechercher un annuaire !</h1>

        <Recherche
          onJeMetCequeJeVeux={this.onChercher}
          onEmpty={this.onVider}
        />

        {this.state.error ? <Message warning>{this.state.error}</Message> : undefined}

        <Card.Group>
          <Etablissement />
          <Etablissement />
          <Etablissement />
        </Card.Group>
      </div>
    );
  }
}

export default App;
```



### Étape 7 : Résultat visuel

Vous devriez maintenant voir **trois cartes d’établissement** s’afficher dans votre interface, avec les titres, téléphones et emails **statiques** (non encore liés aux données de l’API).



## 3. Résumé pédagogique

| Élément              | Rôle                                                                  |
| -------------------- | --------------------------------------------------------------------- |
| `Etablissement.js`   | Nouveau composant pour afficher les établissements                    |
| `<Card>`             | Élément visuel pour styliser chaque résultat                          |
| `<Card.Group>`       | Conteneur pour disposer les cartes côte à côte                        |
| Import dans `App.js` | Permet de tester l’intégration avant d’ajouter les données dynamiques |



## Fin de l’Étape 13 – Affichage des données avec des cartes (statique)


<br/>
<br/>




# Étape 14 – Affichage des données avec des cartes (dynamique)



## 1. Objectif

Jusqu’ici, les cartes étaient statiques.
Nous allons maintenant **générer dynamiquement une carte par établissement** à partir des données réelles fournies par l’API, grâce à la fonction `map()`.



## 2. Rappel : structure des données de l’API

```json
{
  "features": [
    {
      "properties": {
        "id": "etab1",
        "nom": "CPAM de Nantes",
        "telephone": "01 02 03 04 05",
        "email": "nantes@cpam.fr"
      }
    },
    {
      "properties": {
        "id": "etab2",
        "nom": "CCI Angers",
        "telephone": "02 41 00 00 00",
        "email": "angers@cci.fr"
      }
    }
  ]
}
```

Nous allons utiliser `.map()` sur le tableau `this.state.data`, et passer `properties` comme **props** à chaque carte.



## 3. Ajouter une fonction `retournerResultat()` dans `App.js`

Cette fonction retourne un tableau de composants `Etablissement` :

```jsx
retournerResultat = () => {
  return this.state.data.map((element) => {
    return (
      <Etablissement
        key={element.properties.id}
        properties={element.properties}
      />
    );
  });
}
```



## 4. Modifier `render()` pour afficher dynamiquement les cartes

Ajoutez ce bloc **après les messages d’erreur**, dans `App.js` :

```jsx
{this.state.data.length > 0 ? (
  <Card.Group>
    {this.retournerResultat()}
  </Card.Group>
) : undefined}
```



## 5. Mise à jour du composant `Etablissement.js`

Nous allons afficher les vraies données reçues via `props.properties`.

### Code final de `Etablissement.js` :

```jsx
import { Card } from "semantic-ui-react";

const Etablissement = (props) => {
  return (
    <Card>
      <Card.Content>
        <Card.Header>
          {props.properties.nom}
        </Card.Header>
        <Card.Meta>
          Téléphone : {props.properties.telephone}
        </Card.Meta>
        <Card.Meta>
          Courriel : {props.properties.email}
        </Card.Meta>
      </Card.Content>
    </Card>
  );
}

export default Etablissement;
```



## 6. Code complet de `App.js` après cette étape

```jsx
import { Component } from 'react';
import { Message, Card } from 'semantic-ui-react';
import './App.css';
import Recherche from './Composants/Recherche';
import Etablissement from './Composants/Etablissement';

class App extends Component {

  state = { data: [], error: '' }

  onChercher = async (a, b) => {
    if (a && b) {
      try {
        let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
        let donnee = await reponse.json();
        this.setState({ data: donnee.features, error: '' });
      } catch (e) {
        this.setState({ error: "Connexion non aboutie avec l'API" });
      }
    } else {
      this.setState({ error: "Merci de choisir les deux champs" });
    }
  }

  onVider = () => {
    this.setState({ data: [], error: '' });
  }

  retournerResultat = () => {
    return this.state.data.map((element) => {
      return (
        <Etablissement
          key={element.properties.id}
          properties={element.properties}
        />
      );
    });
  }

  render() {
    return (
      <div className="App">
        <h1> Rechercher un annuaire !</h1>

        <Recherche
          onJeMetCequeJeVeux={this.onChercher}
          onEmpty={this.onVider}
        />

        {this.state.error ? (
          <Message warning>{this.state.error}</Message>
        ) : undefined}

        {this.state.data.length > 0 ? (
          <Card.Group>
            {this.retournerResultat()}
          </Card.Group>
        ) : undefined}
      </div>
    );
  }
}

export default App;
```



## 7. Résultat attendu

| Action                                                                                                                                         | Résultat                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Sélection d’un département et d’un type → clic sur "Lancer la recherche"                                                                       | Appel de l’API → données récupérées → affichage d’un nombre de cartes correspondant aux établissements |
| Appel à [https://etablissements-publics.api.gouv.fr/v3/departements/49/cci](https://etablissements-publics.api.gouv.fr/v3/departements/49/cci) | Doit afficher 2 à 4 cartes environ selon l’API en temps réel                                           |

---

## 8. Résumé pédagogique

| Élément            | Rôle                                                                  |
| ------------------ | --------------------------------------------------------------------- |
| `map()`            | Génère dynamiquement un composant `Etablissement` pour chaque élément |
| `key`              | Clé unique pour éviter les erreurs de React                           |
| `props.properties` | Données de l’établissement à afficher                                 |
| `<Card.Group>`     | Regroupe les cartes visuellement                                      |


## Fin de l’Étape 14 – Affichage dynamique des données avec `map()`

<br/>
<br/>



# Étape 15 – Finaliser le projet



## 1. Objectif

Finaliser l’application en :

* Comprenant la **structure JSON retournée par l’API**
* Exploitant les données avec des **props bien nommées**
* Nettoyant et organisant le projet proprement
* Vérifiant la qualité pédagogique et technique de l’implémentation



## 2. Comprendre la structure JSON retournée

Appel de test :

```
https://etablissements-publics.api.gouv.fr/v3/departements/49/cci
```

Réponse (extrait) :

```json
{
  "features": [
    {
      "type": "Feature",
      "geometry": { ... },
      "properties": {
        "id": "etab-1",
        "nom": "CCI Angers",
        "telephone": "02 41 00 00 00",
        "email": "angers@cci.fr"
      }
    },
    ...
  ]
}
```

La donnée utile se trouve dans :

```jsx
element.properties.nom
element.properties.telephone
element.properties.email
```



## 3. Affichage conditionnel simple pour test

Dans `App.js`, juste avant le `return` :

```jsx
if (this.state.data[0]) {
  console.log(this.state.data[0].properties.nom);
}
```

Permet de tester si `data` est bien un tableau et s’il contient des données.



## 4. Passage des données via `props`

### Étape 1 : dans `retournerResultat()` de `App.js`

```jsx
retournerResultat = () => {
  return this.state.data.map((element) => {
    return (
      <Etablissement
        key={element.properties.id}
        properties={element.properties}
      />
    );
  });
}
```

### Variante possible :

Vous pouvez aussi choisir de renommer la props, par exemple `infos` :

```jsx
<Etablissement key={...} infos={element.properties} />
```

Et vous accéderez à `props.infos.nom` au lieu de `props.properties.nom`.



## 5. Mise à jour du composant `Etablissement.js`

### Si vous utilisez `props.properties` :

```jsx
import { Card } from "semantic-ui-react";

const Etablissement = (props) => {
  return (
    <Card>
      <Card.Content>
        <Card.Header>
          {props.properties.nom}
        </Card.Header>
        <Card.Meta>
          Téléphone : {props.properties.telephone}
        </Card.Meta>
        <Card.Meta>
          Courriel : {props.properties.email}
        </Card.Meta>
      </Card.Content>
    </Card>
  );
}

export default Etablissement;
```


### Si vous utilisez `props.infos` (variante) :

```jsx
import { Card } from "semantic-ui-react";

const Etablissement = (props) => {
  return (
    <Card>
      <Card.Content>
        <Card.Header>
          {props.infos.nom}
        </Card.Header>
        <Card.Meta>
          Téléphone : {props.infos.telephone}
        </Card.Meta>
        <Card.Meta>
          Courriel : {props.infos.email}
        </Card.Meta>
      </Card.Content>
    </Card>
  );
}

export default Etablissement;
```



## 6. Nettoyage final du projet

### Fichiers attendus :

```
/src
├── App.js
├── App.css
├── /Composants
│   ├── Recherche.js
│   ├── Recherche.css
│   └── Etablissement.js
```

### Bonnes pratiques :

* Chaque composant dans son propre fichier
* Un seul niveau de responsabilité par composant
* Les données sont passées via `props`
* Aucune logique métier dans les composants visuels (`Etablissement`)
* Les appels API centralisés dans `App.js`



## 7. Vérifications pédagogiques

| Vérification                                                               | Réponse attendue         |
| -------------------------------------------------------------------------- | ------------------------ |
| A-t-on utilisé des composants de type **classe** ?                         | Oui                      |
| Y a-t-il des **états (`state`)** gérés par `App.js` et `Recherche.js` ?    | Oui                      |
| Les composants `Recherche` et `Etablissement` sont-ils **réutilisables** ? | Oui                      |
| A-t-on bien séparé les responsabilités (API, UI, logique) ?                | Oui                      |
| L’interface est-elle **responsive** et lisible ?                           | Oui, grâce à Semantic UI |



## Fin de l’Étape 15 – Finaliser le projet



