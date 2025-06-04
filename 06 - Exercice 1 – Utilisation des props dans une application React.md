# Exercice 1 – Utilisation des props dans une application React

### Objectif pédagogique :

Apprendre à créer des composants React de différents types (classe et fonction) et à leur transmettre des données via des **props de type `string`** et **props de type `fonction`**. Vous apprendrez également à afficher dynamiquement ces données dans l’interface utilisateur.



## Consignes :

1. Créez une nouvelle application React en utilisant l’outil `create-react-app`. Le nom du projet peut être `exercice-props`.

2. Dans le dossier `src/`, ajoutez un composant `Recherche.js` de type **classe** ou **fonction**, selon votre préférence.

3. Ajoutez un composant `Composant1.js` de type **classe**.

4. Ajoutez un composant `Composant2.js` de type **fonction**.

5. Dans le fichier `App.js`, affichez le composant `Recherche` **sans passer de props**.

6. Dans le fichier `App.js`, affichez le composant `Composant1` **sans passer de props**.

7. Dans le fichier `App.js`, affichez le composant `Composant2` **sans passer de props**.

8. Ajoutez une **prop nommée `a` de type `string`** au composant `Recherche`.

9. Ajoutez une **prop nommée `b` de type `string`** au composant `Composant1`.

10. Ajoutez une **prop nommée `c` de type `string`** au composant `Composant2`.

11. Ajoutez une **prop de type `fonction`** au composant `Recherche`. Cette fonction doit simplement afficher un message dans la console avec `console.log()`.

12. Dans le composant `Recherche`, affichez dynamiquement à l’écran la valeur de la prop `a`.

13. Dans le composant `Recherche`, ajoutez un bouton. Lorsque ce bouton est cliqué, il doit exécuter la fonction transmise par la prop (voir Q11).



## Architecture attendue

```
src/
├── App.js
├── Recherche.js        ← props : a (string), action (function)
├── Composant1.js       ← props : b (string)
└── Composant2.js       ← props : c (string)
```


<br/>

# Correction: 

Chaque étape précise :

* Le **fichier concerné**
* Le **code complet**
* Les **modifications localisées** avec `// 🔽 Ajout`

<br/>

## Q1. Créer une application React avec `create-react-app`

```bash
npx create-react-app exercice-props
cd exercice-props
npm start
```

<br/>

## Q2. Ajouter un composant `Recherche.js` (classe ou fonction)

### Fichier : `src/Recherche.js` (version classe)

```jsx
import React from 'react';

class Recherche extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Recherche</h2>
      </div>
    );
  }
}

export default Recherche;
```

<br/>

## Q3. Ajouter un composant `Composant1.js` (classe)

### Fichier : `src/Composant1.js`

```jsx
import React from 'react';

class Composant1 extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant 1 (classe)</h2>
      </div>
    );
  }
}

export default Composant1;
```

<br/>

## Q4. Ajouter un composant `Composant2.js` (fonction)

### 📄 Fichier : `src/Composant2.js`

```jsx
import React from 'react';

const Composant2 = () => {
  return (
    <div>
      <h2>Composant 2 (fonction)</h2>
    </div>
  );
};

export default Composant2;
```

<br/>

## Q5–Q7. Appeler les composants dans `App.js` sans props

###  Fichier : `src/App.js`

```jsx
import React from 'react';
import Recherche from './Recherche';
import Composant1 from './Composant1';
import Composant2 from './Composant2';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Application principale</h1>

        {/* 🔽 Appels sans props */}
        <Recherche />
        <Composant1 />
        <Composant2 />
      </div>
    );
  }
}

export default App;
```

<br/>

## Q8–Q10. Ajouter les props `a`, `b`, `c` (type string)

###  Fichier : `src/App.js` (mise à jour)

```jsx
import React from 'react';
import Recherche from './Recherche';
import Composant1 from './Composant1';
import Composant2 from './Composant2';

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Application principale</h1>

        {/* 🔽 Ajout de la prop a */}
        <Recherche a="Bienvenue dans Recherche" />

        {/* 🔽 Ajout de la prop b */}
        <Composant1 b="Ceci est Composant1" />

        {/* 🔽 Ajout de la prop c */}
        <Composant2 c="Voici Composant2" />
      </div>
    );
  }
}

export default App;
```

<br/>

## Q11. Ajouter une prop `action` (fonction) à `Recherche`

### 📄 Fichier : `src/App.js` (ajout final)

```jsx
<Recherche
  a="Bienvenue dans Recherche"
  action={() => console.log("Fonction appelée depuis App")}
/>
```

<br/>

## Q12. Afficher la prop `a` dans `Recherche.js`

###  Fichier : `src/Recherche.js` (mise à jour)

```jsx
import React from 'react';

class Recherche extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Recherche</h2>

        {/* 🔽 Affichage de la prop a */}
        <p>{this.props.a}</p>
      </div>
    );
  }
}

export default Recherche;
```

<br/>

## Q13. Appeler la fonction `action` dans `Recherche.js`

###  Fichier : `src/Recherche.js` (final)

```jsx
import React from 'react';

class Recherche extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant Recherche</h2>

        <p>{this.props.a}</p>

        {/* 🔽 Appel de la fonction passée en props */}
        <button onClick={this.props.action}>
          Lancer l'action
        </button>
      </div>
    );
  }
}

export default Recherche;
```

<br/>

## Bonus – Affichage des props dans Composant1 et Composant2

###  Fichier : `src/Composant1.js` (avec affichage de `b`)

```jsx
import React from 'react';

class Composant1 extends React.Component {
  render() {
    return (
      <div>
        <h2>Composant 1 (classe)</h2>

        {/* 🔽 Affichage de la prop b */}
        <p>{this.props.b}</p>
      </div>
    );
  }
}

export default Composant1;
```

<br/>

###  Fichier : `src/Composant2.js` (avec affichage de `c`)

```jsx
import React from 'react';

const Composant2 = (props) => {
  return (
    <div>
      <h2>Composant 2 (fonction)</h2>

      {/* 🔽 Affichage de la prop c */}
      <p>{props.c}</p>
    </div>
  );
};

export default Composant2;
```


