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



