


# **Passer des données du parent vers l'enfant**

##  Exercice 1 – Afficher un prénom et un âge

```jsx
import React from "react";

class Profil extends React.Component {
  render() {
    return (
      <p>
        {this.props.prenom} a {this.props.age} ans.
      </p>
    );
  }
}

class App extends React.Component {
  render() {
    return (
      <div>
        <Profil prenom="Sophie" age={22} />
      </div>
    );
  }
}

export default App;
```

<br/>

##  Exercice 2 – Afficher les informations d’un produit

```jsx
import React from "react";

class Produit extends React.Component {
  render() {
    return (
      <p>
        Produit : {this.props.nom} – Prix : {this.props.prix} $
      </p>
    );
  }
}

class App extends React.Component {
  render() {
    return (
      <div>
        <Produit nom="Ordinateur portable" prix={999.99} />
      </div>
    );
  }
}

export default App;
```

<br/>

##  Exercice 3 – Afficher une couleur dans un bloc

```jsx
import React from "react";

class BoiteColoree extends React.Component {
  render() {
    const style = {
      width: "150px",
      height: "150px",
      backgroundColor: this.props.couleur,
      display: "flex",
      justifyContent: "center",
      alignItems: "center",
      border: "1px solid black",
      margin: "20px"
    };

    return (
      <div style={style}>
        Ceci est une boîte de couleur : {this.props.couleur}
      </div>
    );
  }
}

class App extends React.Component {
  render() {
    return (
      <div>
        <BoiteColoree couleur="lightblue" />
      </div>
    );
  }
}

export default App;
```





<br/>
<br/>

# **Passer des données de l’enfant vers le parent**


<br/>

# **Exercice 4 – Envoi d’un message au parent**

**Objectif** : L’enfant envoie "Bonjour" au parent en cliquant sur un bouton. Le parent affiche le message.

### Code complet

```jsx
import React from "react";

class Enfant extends React.Component {
  envoyerMessage = () => {
    // Appelle la fonction fournie par le parent avec le message "Bonjour"
    this.props.envoyer("Bonjour");
  };

  render() {
    return (
      <div>
        <button onClick={this.envoyerMessage}>
          Envoyer "Bonjour"
        </button>
      </div>
    );
  }
}

class App extends React.Component {
  constructor(props) {
    super(props);
    // Initialisation du message vide
    this.state = {
      message: ""
    };
  }

  recevoirMessage = (valeur) => {
    // Met à jour le message dans le state du parent
    this.setState({ message: valeur });
  };

  render() {
    return (
      <div>
        <h1>Message reçu : {this.state.message}</h1>
        <Enfant envoyer={this.recevoirMessage} />
      </div>
    );
  }
}

export default App;
```

<br/>

##  **Exercice 5 – Envoi d’un nombre cliqué**

**Objectif** : L’enfant contient trois boutons (10, 20, 30). Quand on clique, la valeur est envoyée au parent qui l’affiche.

### Code complet

```jsx
import React from "react";

class ChoixNombre extends React.Component {
  envoyer = (valeur) => {
    // Envoie le nombre cliqué au parent
    this.props.envoyerValeur(valeur);
  };

  render() {
    return (
      <div>
        <button onClick={() => this.envoyer(10)}>10</button>
        <button onClick={() => this.envoyer(20)}>20</button>
        <button onClick={() => this.envoyer(30)}>30</button>
      </div>
    );
  }
}

class App extends React.Component {
  constructor(props) {
    super(props);
    // Valeur choisie initialement vide
    this.state = {
      valeurChoisie: null
    };
  }

  mettreAJourValeur = (nombre) => {
    // Met à jour la valeur reçue
    this.setState({ valeurChoisie: nombre });
  };

  render() {
    return (
      <div>
        <h1>
          Nombre choisi :{" "}
          {this.state.valeurChoisie !== null
            ? this.state.valeurChoisie
            : "aucun"}
        </h1>
        <ChoixNombre envoyerValeur={this.mettreAJourValeur} />
      </div>
    );
  }
}

export default App;
```

<br/>

##  **Exercice 6 – Formulaire contrôlé avec remontée de valeur**

**Objectif** : À chaque saisie dans un champ texte dans l’enfant, le parent reçoit la valeur et l’affiche.

### Code complet

```jsx
import React from "react";

class FormulaireNom extends React.Component {
  handleChange = (event) => {
    // À chaque changement, on envoie la nouvelle valeur au parent
    this.props.onChangeNom(event.target.value);
  };

  render() {
    return (
      <div>
        <input
          type="text"
          placeholder="Entrez un nom"
          onChange={this.handleChange}
        />
      </div>
    );
  }
}

class App extends React.Component {
  constructor(props) {
    super(props);
    // Nom vide au départ
    this.state = {
      nom: ""
    };
  }

  mettreAJourNom = (nouveauNom) => {
    // Met à jour le nom dans le parent
    this.setState({ nom: nouveauNom });
  };

  render() {
    return (
      <div>
        <h1>Nom saisi : {this.state.nom}</h1>
        <FormulaireNom onChangeNom={this.mettreAJourNom} />
      </div>
    );
  }
}

export default App;
```


