# **Introduction aux services Web et à Next.js**



## <h1 id="table-des-matieres">Table des matières</h1>

1. [Définition d’un service Web](#1)
   
3. [Le protocole HTTP](#2)
   
   2.1 [Les verbes HTTP](#2-1)

   2.2 [Les codes de statut HTTP](#2-2)
   
5. [Les types d’API : REST, SOAP, GraphQL](#3)
   
   3.1 [API REST](#3-1)

   3.2 [API SOAP](#3-2)
   
   3.3 [API GraphQL](#3-3)
   
7. [Introduction à Next.js](#4) 



# <h1 id="1">1. Définition d’un service Web</h1>

Un **service Web** est une interface logicielle accessible via un réseau (souvent Internet) qui permet à deux systèmes de communiquer entre eux.
Il permet de **fournir, manipuler ou échanger des données** indépendamment des langages ou plateformes utilisés.

> Exemple courant : un site d’e-commerce qui interroge un service Web externe pour afficher les taux de change.

### Caractéristiques :

* Accessible via le protocole HTTP/HTTPS
* Utilise des formats de données standards comme **JSON** ou **XML**
* Peut être appelé par des applications Web, mobiles ou serveurs


# <h1 id="2">2. Le protocole HTTP</h1>

### <h2 id="2-1">2.1 Les verbes HTTP</h2>

| Verbe    | Description                          | Utilisation courante       |
| -------- | ------------------------------------ | -------------------------- |
| `GET`    | Récupérer une ressource              | Lire une donnée            |
| `POST`   | Créer une ressource                  | Ajouter un utilisateur     |
| `PUT`    | Remplacer une ressource existante    | Modifier un profil complet |
| `PATCH`  | Modifier partiellement une ressource | Mettre à jour un champ     |
| `DELETE` | Supprimer une ressource              | Supprimer un article       |



### <h2 id="2-2">2.2 Les codes de statut HTTP</h2>

| Code | Signification         | Exemple                  |
| ---- | --------------------- | ------------------------ |
| 200  | OK                    | Requête réussie          |
| 201  | Created               | Ressource créée          |
| 400  | Bad Request           | Données invalides        |
| 401  | Unauthorized          | Authentification requise |
| 404  | Not Found             | Ressource inexistante    |
| 500  | Internal Server Error | Erreur côté serveur      |



# <h1 id="3">3. Les types d’API : REST, SOAP, GraphQL</h1>

### <h2 id="3-1">3.1 API REST</h2>

* **Style d’architecture** basé sur les ressources (URL = ressource)
* Utilise les **verbes HTTP** (`GET`, `POST`, etc.)
* Réponses généralement en **JSON**
* Très populaire et simple à implémenter

> Exemple :
> `GET /utilisateurs/42` → Retourne l’utilisateur avec l’ID 42

**Avantages :**

* Lisible, scalable, cacheable
* Facilement consommable dans une application front-end



### <h2 id="3-2">3.2 API SOAP</h2>

* **Protocole plus ancien**, basé sur XML et enveloppes strictes
* Nécessite un **contrat WSDL**
* Utilisé dans des environnements **entreprise ou bancaires**

**Avantages :**

* Très formel et sécurisé
* Supporte les transactions complexes

**Inconvénients :**

* Verbosité
* Moins adapté aux environnements modernes Web/Mobile



### <h2 id="3-3">3.3 API GraphQL</h2>

* Développé par Facebook
* Permet de **définir précisément les données voulues**
* Utilise **un seul endpoint**
* Requêtes via un langage spécifique

> Exemple de requête GraphQL :

```graphql
{
  utilisateur(id: 42) {
    nom
    email
  }
}
```

**Avantages :**

* Réduit la sur/sous-consommation de données
* Très utile pour les interfaces riches (front-end)



## <h1 id="4">4. Introduction à Next.js</h1>

**Next.js** est un **framework JavaScript basé sur React**, conçu pour créer des applications Web performantes et modernes.

### Caractéristiques principales :

* Rendu côté serveur (**SSR**) ou statique (**SSG**)
* Prise en charge native des **API routes**
* SEO-friendly (optimisé pour les moteurs de recherche)
* Routing automatique (fichiers dans `pages/`)
* Intégration simple avec des **services Web REST ou GraphQL**

> Exemple : un projet Next.js peut exposer ses propres API via le dossier `/pages/api/`.

### Pourquoi utiliser Next.js avec des services Web ?

* Intégration facile avec des APIs externes REST ou GraphQL
* Possibilité d’héberger une application *frontend* et *backend* dans le même projet
* Excellent pour les applications modernes, performantes et bien structurées


<hr/>

# Exercice 


# <h1 id="exercice-pratique-nextjs-api">5. Exercice pratique – Appeler une API REST avec Next.js</h1>

###  Objectif :

Créer une application Next.js qui **affiche une liste d'utilisateurs** en consommant une **API REST publique**.



## <h2 id="etapes">Étapes à suivre</h2>

### 1. Créer un projet Next.js

```bash
npx create-next-app@latest mon-projet-api
cd mon-projet-api
npm run dev
```

Ouvrir [http://localhost:3000](http://localhost:3000) pour tester.



### 2. Choisir une API REST gratuite

On utilisera :
📎 [https://jsonplaceholder.typicode.com/users](https://jsonplaceholder.typicode.com/users)
Cette URL retourne une liste de 10 utilisateurs.



### 3. Modifier la page d’accueil (`pages/index.js` ou `index.tsx`)

Remplacer le contenu par :

```jsx
import React, { useEffect, useState } from 'react';

export default function Home() {
  const [utilisateurs, setUtilisateurs] = useState([]);
  const [chargement, setChargement] = useState(true);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then((res) => res.json())
      .then((data) => {
        setUtilisateurs(data);
        setChargement(false);
      });
  }, []);

  if (chargement) {
    return <p>Chargement des utilisateurs...</p>;
  }

  return (
    <div style={{ padding: '2rem' }}>
      <h1>Liste des utilisateurs</h1>
      <ul>
        {utilisateurs.map((u) => (
          <li key={u.id}>
            {u.name} ({u.email})
          </li>
        ))}
      </ul>
    </div>
  );
}
```



## <h2 id="resultat-attendu">Résultat attendu</h2>

La page d’accueil de votre app affiche dynamiquement :

```
Liste des utilisateurs
- Leanne Graham (Sincere@april.biz)
- Ervin Howell (Shanna@melissa.tv)
- ...
```



## <h2 id="points-pedagogiques">À Approfondir la prochaine séance </h2>

* Comprendre le **hook `useEffect`** pour exécuter une requête au chargement
* Utilisation de **`fetch()`** pour appeler une API REST
* Stockage de la réponse avec **`useState()`**
* Affichage conditionnel (`chargement`)



## <h2 id="pour-aller-plus-loin">Pour aller plus loin</h2>

* Ajouter une gestion d’erreur si l’API ne répond pas
* Créer une **page par utilisateur** avec `getStaticPaths`
* Afficher plus d’infos (adresse, entreprise…)


