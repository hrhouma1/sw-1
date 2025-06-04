## <h1 id="composant">1. C’est quoi un composant React ?</h1>

Un **composant React** est **une brique de base de l’interface utilisateur**. C’est une **fonction JavaScript** (ou une classe) qui **retourne du JSX** (un mélange de HTML et JavaScript).

👉 Exemple simple :

```jsx
function Bonjour() {
  return <h1>Bonjour, monde !</h1>;
}
```

Ce composant peut ensuite être utilisé comme une balise HTML :

```jsx
<Bonjour />
```

###  En résumé :

* Un composant = une fonction qui retourne de l’interface.
* On peut **composer des interfaces complexes** à partir de composants simples.
* Chaque composant est **indépendant** et **réutilisable**.

<br/>

## <h1 id="props">2. C’est quoi les props ?</h1>

Les **props** (abréviation de *properties*) sont des **valeurs que l’on transmet à un composant depuis son parent**. C’est comme **les arguments d’une fonction**.

👉 Exemple :

```jsx
function Bonjour(props) {
  return <h1>Bonjour, {props.nom} !</h1>;
}
```

Utilisation :

```jsx
<Bonjour nom="Alice" />
<Bonjour nom="Bob" />
```

###  En résumé :

* Les props permettent de **personnaliser le comportement ou l’affichage** d’un composant.
* **Immuables** : un composant **ne peut pas modifier ses props**.

<br/>

## <h1 id="state">3. C’est quoi le state ?</h1>

Le **state** (état) est une **donnée interne au composant** qui **peut changer au cours du temps**. On l’utilise pour gérer des **interactions dynamiques** : clics, formulaires, etc.




## <h2 id="ex-compteur-classe-modern"> Exemple moderne : Compteur avec classe</h2>

```jsx
import React from 'react';

class Compteur extends React.Component {
  // Définition directe du state comme propriété de classe
  state = {
    compteur: 0
  };

  // Méthode fléchée pour garder le bon contexte `this`
  incrementer = () => {
    this.setState({ compteur: this.state.compteur + 1 });
  };

  render() {
    return (
      <div>
        <p>Valeur : {this.state.compteur}</p>
        <button onClick={this.incrementer}>
          Incrémenter
        </button>
      </div>
    );
  }
}
```




###  En résumé :

* Le state permet de **garder en mémoire des données locales** au composant.
* Pour modifier le state, on utilise une **fonction spéciale** (`setCompteur`, etc.).
* À chaque mise à jour du state, **le composant se re-render** (réaffiche).



## <h1 id="conclusion">Conclusion</h1>

| Notion    | Description                   | Exemple clé               |
| --------- | ----------------------------- | ------------------------- |
| Composant | Fonction qui retourne du JSX  | `<MonComposant />`        |
| Props     | Données passées par le parent | `<Bonjour nom="Alice" />` |
| State     | Données internes modifiables  | `useState(0)` + bouton    |

