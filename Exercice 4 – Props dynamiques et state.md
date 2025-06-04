



## Exercice 4 – Props dynamiques et `state`

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
