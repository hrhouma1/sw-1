# LABORATOIRE 1 – UNE DEUXIÈME APPLICATION REACT

## ⚠️ Soumettre un projet React

1. **Ne jamais m’envoyer tout le dossier.**
2. Supprimez le dossier `node_modules`
3. Zippez le projet `.zip` ou `.rar`
4. Envoyez-moi le fichier compressé
5. Je dézippe, j’ouvre avec VS Code
6. Dans le terminal, je tape :  
   ```bash
   npm install
````

7. Cela recréera le dossier `node_modules`
8. Puis je lance l’app avec :

   ```bash
   npm start
   ```

---

## Étape 1 – Installer Semantic UI React

```bash
npx create-react-app demo2
cd demo2
npm start
```

> Ouvrez le projet dans **VS Code**
> Supprimez les lignes inutiles dans `App.js` (lignes 7 à 20)

Remplacez par :

```jsx
<h1>Bonjour groupe ! Nous allons apprendre SEMANTIC UI</h1>
```

### Installer Semantic UI :

```bash
npm install semantic-ui-react semantic-ui-css
```

Dans `package.json` :

```json
"semantic-ui-css": "^2.5.0",
"semantic-ui-react": "^2.1.3"
```

---

## Étape 2 – Ajouter le CDN

Dans `public/index.html`, avant `</head>`, ajoutez :

```html
<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.3.1/semantic.min.css" />
```

---

## Étape 3 – Un peu de style avec CSS

Dans `App.css`, remplacez le contenu par :

```css
body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  background: #d3d3d3;
  text-align: center;
}
.app {
  width: 920px;
  margin: 0 auto;
}
```

---

## Étape 4 – Appeler le composant `Recherche`

### App.js

```jsx
import './App.css';
import Recherche from './Recherche';

function App() {
  return (
    <div className="App">
      <h1>Bonjour groupe ! Nous allons apprendre SEMANTIC UI</h1>
      <Recherche />
    </div>
  );
}

export default App;
```

---

## Étape 5 – Une vraie barre de recherche

### Recherche.js

```jsx
import { Component } from "react";
import { Button, Select } from "semantic-ui-react";

class Recherche extends Component {
  render() {
    const optionsDpt = [
      { value: "44", key: "44", text: "Loire Atlantique" },
      { value: "49", key: "49", text: "Maine et Loire" },
      { value: "53", key: "53", text: "Mayenne" },
      { value: "72", key: "72", text: "Sarthe" },
      { value: "85", key: "85", text: "Vendée" },
    ];

    const optionsType = [
      { value: "cpam", key: "cpam", text: "Caisse primaire d'assurance maladie" },
      { value: "cci", key: "cci", text: "Chambre de commerce et d'industrie" },
      { value: "crous", key: "crous", text: "Crous et ses antennes" },
    ];

    return (
      <div className="recherche">
        <Select placeholder="Choisissez un département" options={optionsDpt} />
        <Select placeholder="Choisissez une administration" options={optionsType} />
        <Button primary>Lancer la recherche</Button>
        <Button secondary>Vider la recherche</Button>
      </div>
    );
  }
}

export default Recherche;
```

> ⚠️ Si une erreur survient, c’est que les imports sont manquants :
> Ajoutez ceci tout en haut :

```jsx
import { Button, Select } from "semantic-ui-react";
```

---

## Étape 6 – Ajouter de la dynamicité (avec `state`)

### Recherche.js (version avec états)

```jsx
import { Component } from "react";
import { Button, Select } from "semantic-ui-react";

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
      { value: "cpam", key: "cpam", text: "Caisse primaire d'assurance maladie" },
      { value: "cci", key: "cci", text: "Chambre de commerce et d'industrie" },
      { value: "crous", key: "crous", text: "Crous et ses antennes" },
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

export default Recherche;
```
