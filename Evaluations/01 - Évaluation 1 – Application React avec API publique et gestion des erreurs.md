# <h1 id="examen-react-api">Évaluation 1 – Application React avec API publique et gestion des erreurs</h1>

### <h2 id="objectif-general">Objectif général</h2>

- *Vous devez développer une **application React** qui consomme une **API publique REST**, en affichant dynamiquement les résultats dans l’interface utilisateur, tout en gérant les erreurs côté client de manière professionnelle.*



### <h2 id="contexte">Contexte</h2>

Dans le cadre de cet examen, vous devrez démontrer votre capacité à :

* intégrer une API REST publique,
* interagir avec un endpoint distant via des appels HTTP,
* afficher des données dans un composant React,
* et surtout **gérer correctement les erreurs côté client** (réseau, mauvais paramètre, API vide, etc.).



### <h2 id="instructions">Instructions</h2>

1. **Choisissez une API publique REST** parmi la [liste disponible](#liste-apis) ou toute autre API gratuite sans authentification complexe.
2. Créez un **projet React** (`create-react-app` ou `Vite`).
3. Créez **au moins deux composants** :

   * Un composant de recherche ou d'interaction (input, bouton, dropdown…)
   * Un composant d’affichage des résultats (liste, tableau, carte…)
4. Effectuez un **appel GET** vers l’API avec `fetch()` ou `axios`.
5. Affichez les **données obtenues dynamiquement**.
6. Gérez **au minimum trois cas d’erreur côté client** :

   * API inaccessible ou problème réseau
   * Paramètre invalide ou non trouvé (ex. erreur 404)
   * Réponse vide ou mal formée
7. Affichez des **messages d’erreur clairs** à l’utilisateur.
8. **Utilisez Git et réalisez des commits réguliers et structurés** :

   * **Un commit par étape majeure** du projet
   * Le message de chaque commit doit clairement indiquer l’avancement (ex. : `création composant Search`, `ajout gestion erreur 404`, `affichage résultats`…)



### <h2 id="livrables">Livrables à remettre</h2>

* **Code source complet** du projet (dépôt GitHub ou `.zip`)
* **Fichier `rapport.txt`** décrivant :

  * L’API choisie
  * Les endpoints utilisés
  * Les composants créés
  * Les erreurs gérées et comment elles ont été simulées/testées
* **Capture(s) d’écran** de l’application fonctionnelle
* **Fichier `README.md`** expliquant comment lancer le projet
* **Historique Git clair**, visible dans le dépôt ou inclus dans un fichier `.git.log.txt` si remise en `.zip`


### <h2 id="modalites">Modalités</h2>

* Travail **individuel obligatoire**
* Langage : **JavaScript avec React**
* Librairies autorisées : `axios`, `semantic-ui`, `bootstrap`, etc.
* Gestion d'état : `useState`, `useEffect` (Redux non requis)
* Git obligatoire (local ou GitHub)



### <h2 id="date-limite">Date limite de remise</h2>

**Vendredi 6 juillet 2025 à 23h59**
→ Toute remise tardive sans justification recevra la note de **0**.



### <h2 id="bareme">Barème /100</h2>

| Critère                                                   | Points |
| --------------------------------------------------------- | ------ |
| Fonctionnement de l’appel API (GET)                       | /15    |
| Création d’une interface utilisateur interactive          | /15    |
| Affichage clair et dynamique des données                  | /15    |
| Gestion des erreurs côté client (au moins 3 cas couverts) | /20    |
| Messages d’erreurs clairs et informatifs (UX)             | /10    |
| Séparation en composants bien structurés (au moins 2)     | /10    |
| **Commits Git structurés et progressifs**                 | **/5** |
| Nettoyage, clarté et commentaires du code                 | /5     |
| `rapport.txt` ou `.md` structuré et complet               | /3     |
| README clair, avec instructions d’installation            | /2     |

**Total** : **/100**



### <h2 id="details-commits">Détail – Évaluation des commits (/5)</h2>

| Sous-critère                                                                     | Points |
| -------------------------------------------------------------------------------- | ------ |
| Minimum 4 commits bien nommés                                                    | /2     |
| Commits répartis selon les grandes étapes (structure, composants, API, erreurs…) | /2     |
| Lisibilité des messages de commit                                                | /1     |


<br/>


# liste-apis


### <h1 id="liste-apis">Liste des APIs publiques </h1>

| #  | Nom de l’API                                 | URL                                                                                                                                                                                              |
| -- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1  | API Établissements Publics                   | [https://api.gouv.fr/documentation/api\_etablissements\_publics](https://api.gouv.fr/documentation/api_etablissements_publics)                                                                   |
| 2  | API Établissements Publics (Département 53)  | [https://etablissements-publics.api.gouv.fr/v3/departements/53/cci](https://etablissements-publics.api.gouv.fr/v3/departements/53/cci)                                                           |
| 3  | API RestCountries (v3)                       | [https://restcountries.com](https://restcountries.com)                                                                                                                                           |
| 4  | API GitHub                                   | [https://api.github.com](https://api.github.com)                                                                                                                                                 |
| 5  | JSONPlaceholder Posts                        | [https://jsonplaceholder.typicode.com/posts](https://jsonplaceholder.typicode.com/posts)                                                                                                         |
| 6  | JSONPlaceholder Comments                     | [https://jsonplaceholder.typicode.com/comments](https://jsonplaceholder.typicode.com/comments)                                                                                                   |
| 7  | JSONPlaceholder Albums                       | [https://jsonplaceholder.typicode.com/albums](https://jsonplaceholder.typicode.com/albums)                                                                                                       |
| 8  | JSONPlaceholder Photos                       | [https://jsonplaceholder.typicode.com/photos](https://jsonplaceholder.typicode.com/photos)                                                                                                       |
| 9  | JSONPlaceholder Todos                        | [https://jsonplaceholder.typicode.com/todos](https://jsonplaceholder.typicode.com/todos)                                                                                                         |
| 10 | JSONPlaceholder Users                        | [https://jsonplaceholder.typicode.com/users](https://jsonplaceholder.typicode.com/users)                                                                                                         |
| 11 | JSONPlaceholder Posts (userId=1)             | [https://jsonplaceholder.typicode.com/posts?userId=1](https://jsonplaceholder.typicode.com/posts?userId=1)                                                                                       |
| 12 | JSONPlaceholder Comments (postId=1)          | [https://jsonplaceholder.typicode.com/comments?postId=1](https://jsonplaceholder.typicode.com/comments?postId=1)                                                                                 |
| 13 | JSONPlaceholder Commentaire (postId=1, id=1) | [https://jsonplaceholder.typicode.com/comments?postId=1\&id=1](https://jsonplaceholder.typicode.com/comments?postId=1&id=1)                                                                      |
| 14 | Quotable API sur GitHub                      | [https://github.com/lukePeavey/quotable](https://github.com/lukePeavey/quotable)                                                                                                                 |
| 15 | Quotable API Random                          | [https://api.quotable.io/random](https://api.quotable.io/random)                                                                                                                                 |
| 16 | Quotable API Random (maxLength=20)           | [https://api.quotable.io/random?maxLength=20](https://api.quotable.io/random?maxLength=20)                                                                                                       |
| 17 | OMDb API                                     | [http://omdbapi.com/](http://omdbapi.com/)                                                                                                                                                       |
| 18 | OpenWeatherMap API                           | [https://openweathermap.org/api](https://openweathermap.org/api)                                                                                                                                 |
| 19 | Unsplash API Documentation                   | [https://unsplash.com/documentation](https://unsplash.com/documentation)                                                                                                                         |
| 20 | API Conversion Devises (Currency Converter)  | [https://api.currconv.com/api/v7/convert?q=USD\_PHP,PHP\_USD\&compact=ultra\&apiKey=YOUR\_API\_KEY](https://api.currconv.com/api/v7/convert?q=USD_PHP,PHP_USD&compact=ultra&apiKey=YOUR_API_KEY) |
| 21 | Exemple d’application 1                      | [https://friendly-payne-18ef0b.netlify.app/](https://friendly-payne-18ef0b.netlify.app/)                                                                                                         |
| 22 | Exemple d’application 2                      | [https://dazzling-edison-76c948.netlify.app/](https://dazzling-edison-76c948.netlify.app/)                                                                                                       |
| 23 | GitHub – Endpoints pour apps                 | [https://docs.github.com/en/rest/overview/endpoints-available-for-github-apps](https://docs.github.com/en/rest/overview/endpoints-available-for-github-apps)                                     |
| 24 | API COVID-19 Mathdro                         | [https://covid19.mathdro.id/api](https://covid19.mathdro.id/api)                                                                                                                                 |
| 25 | API COVID-19 Countries                       | [https://api.covid19api.com/countries](https://api.covid19api.com/countries)                                                                                                                     |
| 26 | Google Translate API (non officielle)        | [https://www.npmjs.com/package/@vitalets/google-translate-api](https://www.npmjs.com/package/@vitalets/google-translate-api)                                                                     |
| 27 | OpenWeatherMap Current Weather               | [http://api.openweathermap.org/data/2.5/weather](http://api.openweathermap.org/data/2.5/weather)                                                                                                 |
| 28 | Spotify Web API – Documentation              | [https://developer.spotify.com/documentation/web-api/](https://developer.spotify.com/documentation/web-api/)                                                                                     |
| 29 | CoinGecko – Prix BTC                         | [https://api.coingecko.com/api/v3/simple/price?ids=bitcoin\&vs\_currencies=cad](https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=cad)                                     |
| 30 | Trebble Developer API                        | [https://developer.trebble.fm/](https://developer.trebble.fm/)                                                                                                                                   |
| 31 | API RestCountries (ancienne version)         | [https://restcountries.eu/](https://restcountries.eu/)                                                                                                                                           |
| 32 | Travel Advisor via RapidAPI                  | [https://rapidapi.com/apidojo/api/travel-advisor/](https://rapidapi.com/apidojo/api/travel-advisor/)                                                                                             |
| 33 | OpenCovid Canada API                         | [https://opencovid.ca/api/](https://opencovid.ca/api/)                                                                                                                                           |
| 34 | OpenWeatherMap – Current Weather             | [https://openweathermap.org/current](https://openweathermap.org/current)                                                                                                                         |
| 35 | Open Food Facts API                          | [https://wiki.openfoodfacts.org/API](https://wiki.openfoodfacts.org/API)                                                                                                                         |
| 36 | TheCocktail DB API                           | [https://www.thecocktaildb.com/api.php](https://www.thecocktaildb.com/api.php)                                                                                                                   |
| 37 | JService (Trivia API)                        | [https://jservice.io/](https://jservice.io/)                                                                                                                                                     |
| 38 | M-Media-Group COVID-19 API                   | [https://github.com/M-Media-Group/Covid-19-API](https://github.com/M-Media-Group/Covid-19-API)                                                                                                   |
| 39 | API-Football – Vidéos de matchs (Scorebat)   | [https://www.scorebat.com/video-api/v3/](https://www.scorebat.com/video-api/v3/)                                                                                                                 |
| 40 | IMDb API                                     | [https://imdb-api.com/](https://imdb-api.com/)                                                                                                                                                   |




