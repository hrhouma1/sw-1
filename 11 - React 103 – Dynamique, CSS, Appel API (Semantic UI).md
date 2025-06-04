# <h1 id="react-103"> React 103 – Dynamique, CSS, Appel API (Semantic UI)</h1>


# <h2 id="etape6">Étape 6 – Ajouter de la dynamicité (States)</h2>

###  Objectif :

Rendre les sélections dynamiques grâce aux `states`.

```jsx
class Recherche extends Component {
  state = { depart: "", categorie: "" };

  onDepartementChange = (e, data) => {
    this.setState({ depart: data.value });
  };

  onCategorieChange = (e, data) => {
    this.setState({ categorie: data.value });
  };

  render() {
    console.log(this.state.depart, this.state.categorie);

    const optionsDpt = [
      { value: "44", key: "44", text: "Loire Atlantique" },
      { value: "49", key: "49", text: "Maine et Loire" },
      { value: "53", key: "53", text: "Mayenne" },
      { value: "72", key: "72", text: "Sarthe" },
      { value: "85", key: "85", text: "Vendée" },
    ];

    const optionsType = [
      { value: "cpam", key: "cpam", text: "Caisse primaire" },
      { value: "cci", key: "cci", text: "Chambre de commerce" },
      { value: "crous", key: "crous", text: "Crous" },
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
        <Button primary>Lancer la recherche</Button>
        <Button secondary>Vider la recherche</Button>
      </div>
    );
  }
}
```

<br/>

## <h2 id="etape7">Étape 7 – Ajout de style avec CSS</h2>

Créer un fichier `Recherche.css` :

```css
.recherche {
  margin: 15px 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
}
```

Puis l'importer :

```js
import './Recherche.css';
```

<br/>

## <h2 id="etape8">Étape 8 – Préparation appel API</h2>

###  Transformer `App` en classe :

```jsx
import { Component } from 'react';
import './App.css';
import Recherche from './Composants/Recherche';

class App extends Component {
  render() {
    return (
      <div className="App">
        <h1>Annuaire</h1>
        <Recherche />
      </div>
    );
  }
}
export default App;
```

> 💡 Ajoute `state = { data: [], error: '' }` dans App pour manipuler les données API.

<br/>

## <h2 id="etape9">Étape 9 – Appel API et liaison dynamique</h2>

###  Nouvelle version de `App.js` :

```jsx
import { Component } from 'react';
import './App.css';
import Recherche from './Composants/Recherche';

class App extends Component {
  state = { data: [], error: '' };

  onChercher = async (a, b) => {
    if (a && b) {
      try {
        let reponse = await fetch(`https://etablissements-publics.api.gouv.fr/v3/departements/${a}/${b}`);
        let donnee = await reponse.json();
        console.log(donnee); // 🔽 Affiche les vrais résultats de l'API
      } catch (e) {
        console.error("Erreur API", e);
      }
    }
  };

  render() {
    return (
      <div className="App">
        <h1>Annuaire</h1>
        <Recherche onJeMetCequeJeVeux={this.onChercher} />
      </div>
    );
  }
}

export default App;
```

<br/>

###  Nouvelle version `Recherche.js` :

```jsx
import { Component } from "react";
import { Button, Select } from "semantic-ui-react";
import './Recherche.css';

class Recherche extends Component {
  state = { depart: "", categorie: "" };

  onDepartementChange = (e, data) => {
    this.setState({ depart: data.value });
  };

  onCategorieChange = (e, data) => {
    this.setState({ categorie: data.value });
  };

  render() {
    console.log(this.state.depart, this.state.categorie); // 🔽 Suivi console

    const optionsDpt = [
      { value: "44", key: "44", text: "Loire Atlantique" },
      { value: "49", key: "49", text: "Maine et Loire" },
      { value: "53", key: "53", text: "Mayenne" },
      { value: "72", key: "72", text: "Sarthe" },
      { value: "85", key: "85", text: "Vendée" },
    ];

    const optionsType = [
      { value: "cpam", key: "cpam", text: "Caisse primaire" },
      { value: "cci", key: "cci", text: "Chambre de commerce" },
      { value: "crous", key: "crous", text: "Crous" },
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
        <Button secondary>Vider la recherche</Button>
      </div>
    );
  }
}

export default Recherche;
```

