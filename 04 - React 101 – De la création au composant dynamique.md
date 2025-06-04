# <h1 id="toc">Table des matières – Cours React 1</h1>

<h1 id="toc">Table des matières – Cours React 1</h1>
<ul>
  <li><a href="#prerequis">Prérequis</a></li>
  <li><a href="#stack">Stack Web – Architecture MERN, LAMP, MEAN...</a></li>
  <li><a href="#intro-mern">Laboratoire – Introduction à la Stack MERN</a></li>
  <li><a href="#historique-react">Historique de React et concepts clés</a></li>
  <li><a href="#etape1-node">Étape 1 – Installer Node.js et créer une application</a></li>
  <li><a href="#etape2-vscode">Étape 2 – Installer Visual Studio Code</a></li>
  <li><a href="#etape3-exploration">Étape 3 – Explorer la structure du projet</a></li>
  <li><a href="#etape4-extensions">Étape 4 – Ajouter des extensions utiles</a></li>
  <li><a href="#etape5-nettoyage">Étape 5 – Nettoyer le projet React</a></li>
  <li><a href="#etape6-composants">Étape 6 – Comprendre les composants React</a></li>
  <li><a href="#etape7-classes">Étape 7 – Transformer un composant fonctionnel en classe</a></li>
  <li><a href="#etape8-stateless">Étape 8 – Ajouter des composants stateless</a></li>
  <li><a href="#etape9-props">Étape 9 – Props simples</a></li>
  <li><a href="#etape10-children">Étape 10 – Utiliser props.children</a></li>
  <li><a href="#etape11-props-alternative">Étape 11 – Autre syntaxe avec props</a></li>
  <li><a href="#etape12-state">Étape 12 – Travailler avec state</a></li>
  <li><a href="#etape13-setstate">Étape 13 – Modifier l’état avec setState</a></li>
  <li><a href="#etape14-suite">À venir – Hooks, routing, formulaires…</a></li>
</ul>




# Prérequis

* **Node.js** : [https://nodejs.org/en/download](https://nodejs.org/en/download)
* **Visual Studio Code** : [https://code.visualstudio.com/](https://code.visualstudio.com/)

<br/>

# Stack

Une stack web classique se compose :

* Base de données : MySQL, MariaDB, PostgreSQL, MongoDB...
* Serveur web : Nginx, Apache, Express, Tomcat, IIS...
* Langage côté client : React (ou Next.js), Angular...
* Langage côté serveur : PHP, ASP.NET, JSP, Node.js...

### Exemples de stacks populaires :

* **MERN** = MongoDB + Express + React + Node.js
* **MEAN** = MongoDB + Express + Angular + Node.js
* **LAMP** = Linux + Apache + MySQL + PHP
* **WAMP** = Windows + Apache + MySQL + PHP
* **MAMP** = Mac + Apache + MySQL + PHP
* **WEMP** = Windows + Nginx + MySQL + PHP

<br/>

# Laboratoire – Introduction à la Stack MERN

* **M** = MongoDB
* **E** = Express (backend léger avec Node.js)
* **R** = React (vue dans le modèle MVC)
* **N** = Node.js (serveur JS côté backend)

<br/>

# Historique de React

* Bibliothèque JavaScript développée par **Facebook (Meta)** en 2013
* Grande mise à jour en 2019 avec **Hooks**
* Utilisée pour créer des **SPA** (Single Page Applications)
* Utilise du **JSX** (JavaScript XML)

<br/>

# Étape 1 – Installer Node.js et créer une application

```bash
node -v
npm -v

cd C:\projetsreact
npm install -g create-react-app
npx create-react-app demo1
cd demo1
npm start
```

<br/>

# Étape 2 – Installer Visual Studio Code

* Télécharger : [https://code.visualstudio.com/](https://code.visualstudio.com/)
* Ouvrir le dossier du projet `demo1`

<br/>

# Étape 3 – Explorer le projet

* `node_modules/` : dépendances
* `public/` : contient `index.html`
* `src/` : tout le code React
* `App.js` : premier composant
* `index.js` : point d’entrée

<br/>

# Étape 4 – Ajouter des extensions

* **React Developer Tools (Chrome)**
* **Standard JS** (VS Code)
* **Simple React Snippets** (VS Code)

<br/>

# Étape 5 – Nettoyer le projet

Dans `src/index.js`, enlever `<React.StrictMode>`
Dans `src/App.js`, supprimer `logo.svg` et les imports inutiles

<br/>
# Étape 6 – Comprendre les composants React

Deux types :

* **Fonctionnels** : `const App = () => { ... }`
* **Classes** : `class App extends Component { render() { ... } }`

<br/>

# Étape 7 – Transformer un composant fonctionnel en classe

Avant :

```jsx
const App = () => {
  return <h1>Bonjour</h1>;
}
```

Après :

```jsx
import { Component } from 'react';

class App extends Component {
  render() {
    return <h1>Bonjour</h1>;
  }
}
```

---

# Étape 8 – Ajouter des composants sans état (stateless)

```jsx
const College = () => <div>Je suis un college</div>;
const Ordinateur = () => <div>Je suis un ordinateur de bureau</div>;

class App extends Component {
  render() {
    return (
      <>
        <College />
        <Ordinateur />
      </>
    );
  }
}
```

<br/>

# Étape 9 – Props simples

```jsx
const College = ({ categorie, endroit }) => (
  <div>
    Je suis un college de type {categorie} à {endroit}.
  </div>
);

class App extends Component {
  render() {
    return (
      <>
        <College categorie="public" endroit="Montréal" />
        <College categorie="privé" endroit="Québec" />
      </>
    );
  }
}
```

<br/>

# Étape 10 – `props.children`

```jsx
<College categorie="public" endroit="Montréal">
  Je suis fermé le weekend.
</College>
```

```jsx
const College = ({ categorie, endroit, children }) => (
  <div>
    Type : {categorie}, Lieu : {endroit} <br />
    {children}
  </div>
);
```

<br/>

# Étape 11 – Deuxième façon d'utiliser `props`

```jsx
const College = (props) => (
  <div>
    Type : {props.categorie}, Lieu : {props.endroit}
    {props.children}
  </div>
);
```

---

# Étape 12 – Travailler avec `state`

```jsx
class App extends Component {
  state = { cat: "public", lieu: "Gaspesie" };

  render() {
    return (
      <College
        categorie={this.state.cat}
        endroit={this.state.lieu}
      />
    );
  }
}
```

<br/>

# Étape 13 – Modifier l’état avec un bouton

```jsx
class App extends Component {
  state = { cat: "public", lieu: "Gaspesie" };

  changerCollege = () => {
    this.setState({ cat: "privé" });
  };

  render() {
    return (
      <>
        <College categorie={this.state.cat} endroit={this.state.lieu} />
        <button onClick={this.changerCollege}>Changer le college</button>
      </>
    );
  }
}
```

<br/>

# À Venir

* Étape 14 – Props fonctions (ex: bouton qui appelle une fonction parente)
* Étape 15 – Champs dynamiques (`input`, `onChange`)
* Étape 16 – Composants contrôlés (formulaire)
* Étape 17 – `event.preventDefault()`
* Étape 18 – Hooks : `useState`, `useEffect`
* Étape 19 – Routing avec `react-router-dom`
* Étape 20 – Mini projet


