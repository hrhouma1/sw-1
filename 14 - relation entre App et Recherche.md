## Explication de la relation entre `App` et `Recherche`

### 1. Structure des composants

#### a. `App` (composant **parent**)

* Contient l’état principal :

  ```js
  state = { data: [], error: '' }
  ```
* Contient la fonction `onChercher` qui fait un appel à une API.
* Passe cette fonction à l’enfant via une prop :

  ```jsx
  <Recherche onPropagateToParent={this.onChercher} />
  ```

#### b. `Recherche` (composant **enfant**)

* Contient un état local :

  ```js
  state = { depart: "", categorie: "" }
  ```
* Contient deux fonctions `onDepartementChange` et `onCategorieChange` qui mettent à jour cet état.
* Utilise la prop `onPropagateToParent` pour appeler la fonction du parent avec les valeurs sélectionnées par l'utilisateur :

  ```js
  this.props.onPropagateToParent(this.state.depart, this.state.categorie)
  ```



### 2. Communication entre parent et enfant

#### a. Du **parent vers l’enfant**

* Le parent transmet une fonction en tant que prop :

  ```jsx
  <Recherche onPropagateToParent={this.onChercher} />
  ```

#### b. De l’**enfant vers le parent**

* L’enfant appelle la fonction reçue via `props` :

  ```js
  onClick={() => this.props.onPropagateToParent(this.state.depart, this.state.categorie)}
  ```
* Cela permet à l’enfant de signaler une action utilisateur (ex. clic sur un bouton), sans modifier directement l’état du parent.



### 3. Pourquoi cette architecture est correcte

* En React, la communication est **unidirectionnelle** (de haut en bas).
* Un composant enfant **ne peut pas modifier l’état du parent**, mais il peut **lui transmettre des données** via une fonction passée en prop.
* Cela permet de **centraliser la logique** (appel API, traitement de données) dans le parent, tout en gardant la gestion de l’interface (sélections) dans l’enfant.



### 4. Résumé du fonctionnement

| Élément                               | Localisation          | Fonction                                                     |
| ------------------------------------- | --------------------- | ------------------------------------------------------------ |
| `onChercher(a, b)`                    | Composant `App`       | Fonction qui appelle l’API avec les données choisies.        |
| `onPropagateToParent` (prop)          | Composant `Recherche` | Prop contenant `onChercher`, transmise par `App`.            |
| `this.props.onPropagateToParent(...)` | Composant `Recherche` | Appelle la fonction du parent avec les sélections locales.   |
| `depart`, `categorie` (state)         | Composant `Recherche` | État local avec les données sélectionnées par l’utilisateur. |




<br/>



# Annexe 1

```
                 +---------------------------+
                 |        App (Parent)       |
                 |---------------------------|
                 |                           |
                 |  state = {                |
                 |    data: [],              |
                 |    error: ''              |
                 |  }                        |
                 |                           |
                 |  onChercher(a, b) {       |
                 |    fetch(...)             |
                 |  }                        |
                 |                           |
                 |  render() {               |
                 |    <Recherche             |
                 |      onPropagateToParent= |
                 |        {this.onChercher}  |
                 |    />                     |
                 |  }                        |
                 +------------|--------------+
                              |
                              |  props.onPropagateToParent = onChercher
                              v
         +--------------------|---------------------+
         |              Recherche (Enfant)          |
         |------------------------------------------|
         |                                          |
         |  state = { depart: "", categorie: "" }   |
         |                                          |
         |  onDepartementChange(e, data) {          |
         |    setState({ depart: data.value })      |
         |  }                                       |
         |                                          |
         |  onCategorieChange(e, data) {            |
         |    setState({ categorie: data.value })   |
         |  }                                       |
         |                                          |
         |  render() {                              |
         |    <Select onChange={onDepartementChange}|
         |    <Select onChange={onCategorieChange}  |
         |    <Button onClick={() =>                |
         |       props.onPropagateToParent(         |
         |         state.depart, state.categorie    |
         |       )} />                              |
         |  }                                       |
         +------------------------------------------+
```

### Lecture du schéma :

* `App` passe une fonction `onChercher` à `Recherche` via une prop appelée `onPropagateToParent`.
* `Recherche` contient un état local pour suivre les sélections de l’utilisateur (`depart`, `categorie`).
* Lors du clic sur le bouton, `Recherche` appelle la fonction `onPropagateToParent` avec les valeurs de son propre `state`.
* Cette fonction est en réalité `onChercher` du parent, ce qui permet de déclencher un appel API depuis le composant parent.


<br/>



# Annexe 2 - Schéma complet : relations, méthodes, flux de données

```
                                (Données choisies)
                           depart = "44", categorie = "cpam"
                                       ▲
                                       |
                +----------------------+------------------+
                |                                         |
                |          Fonction appelée dans          |
                |     Recherche (enfant) au clic bouton   |
                |                                         |
                |   props.onPropagateToParent(            |
                |     this.state.depart,                  |
                |     this.state.categorie                |
                |   )                                     |
                |                                         |
                +----------------------+------------------+
                                       |
                                       v
                          +------------|-------------+
                          |       App (Parent)       |
                          |--------------------------|
                          |                          |
                          | onChercher(a, b) {       |
                          |   fetch(.../a/b)         |
                          |   console.log(...)       |
                          | }                        |
                          |                          |
                          +------------|-------------+
                                       ^
                                       |
                          Fonction passée comme prop :
                          onPropagateToParent = this.onChercher
                                       |
                                       v
+---------------------------------------------------------------+
|                      Recherche (Enfant)                       |
|---------------------------------------------------------------|
| - state = { depart: "", categorie: "" }                       |
|                                                               |
| - onDepartementChange(e, data) => setState({ depart })        |
| - onCategorieChange(e, data)  => setState({ categorie })      |
|                                                               |
| - Appel du parent :                                           |
|   this.props.onPropagateToParent(this.state.depart, ...)      |
|                                                               |
+---------------------------------------------------------------+
```



## Résumé du **flux de données et méthodes**

| Direction                | De                      | Vers                        | Contenu transmis                          |
| ------------------------ | ----------------------- | --------------------------- | ----------------------------------------- |
| Fonction (via props)     | `App` (parent)          | `Recherche` (enfant)        | `onPropagateToParent = this.onChercher`   |
| Données dynamiques       | `Recherche` (enfant)    | `App` (parent)              | `depart`, `categorie` via `this.props...` |
| Appel utilisateur (clic) | Bouton dans `Recherche` | Appel de fonction du parent | `this.props.onPropagateToParent(...)`     |



