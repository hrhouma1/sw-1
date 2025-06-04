## <h1 id="introduction">Introduction</h1>

Le **rendu d’une interface web** peut se faire de deux grandes façons : **côté serveur (Server-Side Rendering, SSR)** ou **côté client (Client-Side Rendering, CSR)**. Le choix entre ces deux paradigmes dépend de plusieurs critères : performance, interactivité, référencement (SEO), accessibilité, et complexité du projet.

<br/>

## <h2 id="ssr">1. Rendu côté serveur (SSR – Server-Side Rendering)</h2>

### Définition

Le **rendu côté serveur** consiste à **générer le HTML complet d'une page sur le serveur**, avant de l'envoyer au navigateur. Le client reçoit ainsi une page prête à être affichée sans attendre l'exécution de JavaScript.

### Fonctionnement

1. Le navigateur envoie une requête HTTP (ex. `/produits`).
2. Le serveur traite la requête, appelle éventuellement une base de données.
3. Le serveur utilise un **template HTML** (ex. Jinja2, Twig, Blade) pour injecter les données.
4. Il renvoie le **HTML complet** au navigateur.
5. Le navigateur affiche immédiatement le contenu.

### Technologies courantes

* **PHP** (WordPress, Laravel, Symfony)
* **Python** : Flask + Jinja2, Django
* **Ruby on Rails**
* **ASP.NET MVC**
* **Next.js** (lorsqu'utilisé en mode SSR)

### Exemple avec Flask + Jinja2

```python
@app.route('/utilisateur/<int:id>')
def utilisateur(id):
    utilisateur = get_user_by_id(id)
    return render_template("profil.html", user=utilisateur)
```

Et le template Jinja2 :

```html
<h1>Bonjour {{ user.nom }}</h1>
```

<br/>

## <h2 id="csr">2. Rendu côté client (CSR – Client-Side Rendering)</h2>

### Définition

Le **rendu côté client** consiste à envoyer une page HTML minimale au navigateur (souvent un `<div id="root"></div>`), puis à utiliser **JavaScript** pour générer dynamiquement toute l’interface à partir de composants, souvent en se basant sur des appels API.

### Fonctionnement

1. Le serveur renvoie un squelette HTML vide (ex. un `<div>`).
2. Le navigateur télécharge le bundle JavaScript (React, Vue...).
3. Ce JavaScript construit l’interface via le DOM virtuel.
4. Les données sont chargées via des appels API (souvent REST ou GraphQL).
5. Le contenu s’affiche dynamiquement après que tout le JS est chargé.

### Technologies courantes

* **React** (SPA classique)
* **Vue.js**
* **Angular**
* **Svelte**
* **Next.js en mode CSR**

### Exemple avec React

```jsx
import { useEffect, useState } from 'react';

function ProfilUtilisateur({ id }) {
  const [utilisateur, setUtilisateur] = useState(null);

  useEffect(() => {
    fetch(`/api/utilisateur/${id}`)
      .then(res => res.json())
      .then(data => setUtilisateur(data));
  }, [id]);

  if (!utilisateur) return <p>Chargement...</p>;

  return <h1>Bonjour {utilisateur.nom}</h1>;
}
```

<br/>

## <h2 id="comparaison">3. Comparaison des technologies</h2>

| Technologie              | Type de rendu     | Niveau d’interactivité | Exécution        | Données dynamiques      | Temps au premier affichage |
| ------------------------ | ----------------- | ---------------------- | ---------------- | ----------------------- | -------------------------- |
| PHP (Laravel, WordPress) | SSR               | Faible à moyenne       | Serveur          | Facile à intégrer       | Très rapide                |
| Flask + Jinja2           | SSR               | Faible à moyenne       | Serveur          | Simple                  | Très rapide                |
| Django                   | SSR               | Moyenne                | Serveur          | ORM intégré             | Rapide                     |
| React                    | CSR               | Très élevée            | Navigateur       | API obligatoire         | Plus lent                  |
| Vue.js                   | CSR               | Très élevée            | Navigateur       | API obligatoire         | Plus lent                  |
| Next.js                  | SSR ou CSR ou SSG | Élevée + SEO optimisé  | Serveur + client | API ou data pré-générée | Optimisé selon config      |

<br/>

## <h2 id="cas-pratiques">4. Cas pratiques</h2>

### Cas 1 : Page statique avec peu d’interactions (ex. page de présentation)

**Solution recommandée** : PHP, Flask + Jinja2, ou Next.js en mode statique (SSG)

### Cas 2 : Application avec formulaires et filtrage en temps réel (ex. tableau de bord)

**Solution recommandée** : React, Vue.js, Angular (CSR) ou Next.js avec hydratation côté client

### Cas 3 : Site devant être bien indexé par les moteurs de recherche (ex. blog, ecommerce)

**Solution recommandée** : Next.js en SSR ou SSG, Flask avec cache HTML, Django avec cache

<br/>

## <h2 id="avantages">5. Avantages et inconvénients</h2>

### Rendu côté serveur (SSR)

**Avantages :**

* Temps de chargement initial rapide
* Bon pour le SEO (le contenu est visible sans JavaScript)
* Moins de JS à télécharger (sauf avec hydratation)

**Inconvénients :**

* Moins fluide pour les interactions
* Chaque action nécessite une requête serveur complète
* Moins modulaire pour les gros systèmes

<br/>

### Rendu côté client (CSR)

**Avantages :**

* Interactions riches et instantanées
* Expérience utilisateur fluide (SPA)
* Architecture découplée (API + UI)

**Inconvénients :**

* Mauvais SEO si mal configuré
* Lenteur du premier affichage (JS lourd à charger)
* Problèmes d’accessibilité si JS désactivé

<br/>

## <h2 id="conclusion">6. Conclusion</h2>

Le choix entre **CSR** et **SSR** dépend de vos **objectifs** :

| Objectif                            | Approche recommandée                    |
| ----------------------------------- | --------------------------------------- |
| Chargement rapide + SEO             | SSR (Next.js, Flask, Django, PHP)       |
| Application réactive type dashboard | CSR (React, Vue.js, Angular)            |
| Blog ou site statique               | SSG (Next.js en `getStaticProps`, Hugo) |
| API indépendante + UI modulable     | CSR + API REST ou GraphQL               |


