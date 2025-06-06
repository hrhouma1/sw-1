

# Passer des props du parent vers l’enfant


### **Exercice 1 – Afficher un prénom et un âge**

**Objectif** : Passer plusieurs props à un composant enfant.

**Consigne** :
Créez un composant `App` qui contient un composant `Profil`.
Le composant `Profil` doit recevoir deux props : un prénom (`"Sophie"`) et un âge (`22`) puis les afficher dans une phrase complète, comme :
`"Sophie a 22 ans."`

---

### **Exercice 2 – Afficher les informations d’un produit**

**Objectif** : Utiliser les props pour afficher des informations de type texte + nombre.

**Consigne** :
Créez un composant `App` qui affiche un composant `Produit`.
Le composant `Produit` reçoit les props suivantes :

* nom : `"Ordinateur portable"`
* prix : `999.99`
  Dans le composant enfant, affichez :
  `"Produit : Ordinateur portable – Prix : 999.99 $"`

---

### **Exercice 3 – Afficher une couleur dans un bloc**

**Objectif** : Passer une prop qui est utilisée dans un style CSS inline.

**Consigne** :
Créez un composant `App` qui utilise un composant `BoiteColorée`.
Ce composant reçoit une prop `couleur`, par exemple `"lightblue"` ou `"yellow"`.
Le composant `BoiteColorée` doit afficher un `div` avec une largeur et hauteur de 150px, et un fond de la couleur passée en prop. Le texte à l’intérieur peut être :
`"Ceci est une boîte de couleur : lightblue"`


# Passer des props de l'enfant vers le parent

### **Exercice 4 – Envoi d’un message au parent**

**Objectif** : Utiliser une fonction passée en prop pour envoyer une chaîne de caractères du composant enfant vers le composant parent.

**Consigne** :
Créez deux composants : `App` (parent) et `Enfant`.
L’enfant contient un bouton `"Envoyer Bonjour"`.
Quand on clique, l’enfant appelle une fonction `envoyerMessage` reçue du parent avec `"Bonjour"` en paramètre.
Le parent affiche alors ce message dans une balise `<p>`.

---

### **Exercice 5 – Envoi d’un nombre cliqué**

**Objectif** : Envoyer une valeur dynamique choisie dans l’enfant au parent.

**Consigne** :
Créez un composant `App` et un composant `ChoixNombre`.
Le composant enfant affiche trois boutons : `10`, `20`, `30`.
Quand on clique sur un des boutons, le nombre est envoyé au parent via une fonction callback.
Le parent affiche : `"Nombre choisi : 20"` (ou 10 ou 30 selon le clic).

---

### **Exercice 6 – Formulaire contrôlé avec remontée de valeur**

**Objectif** : Envoyer la valeur d’un champ texte (input) au parent à chaque changement.

**Consigne** :
Créez un composant `App` et un composant `FormulaireNom`.
Le composant `FormulaireNom` contient un champ texte (`input`) dans lequel l’utilisateur écrit un nom.
À chaque modification, le composant enfant envoie la nouvelle valeur au parent.
Le parent affiche dynamiquement : `"Nom saisi : Alice"` (ou autre selon l’utilisateur).

