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

---

## Exercice 3 – Props dynamiques et `state`

## Objectifs pédagogiques :

* Comprendre la relation entre les `props` et le `state`
* Savoir capturer des entrées utilisateur et les transférer à un composant enfant
* Gérer l'état dans un composant parent pour alimenter dynamiquement ses enfants

<br/>

### Contexte :

On souhaite améliorer le composant `Car` de l'exercice précédent pour qu’il affiche les valeurs **non plus codées en dur**, mais transmises **dynamiquement** via des champs de formulaire.

---

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

---

### Résultat attendu :

* Les informations affichées dans le composant `Car` changent **en direct** selon ce que l’utilisateur saisit dans les champs.
* Le composant `Car` reste réutilisable avec **différentes données**.
* Aucune logique d’état (`useState` ou `this.state`) ne doit être ajoutée à `Car.js`.

