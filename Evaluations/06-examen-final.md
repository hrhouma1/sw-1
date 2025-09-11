# Énoncé académique — Prolongement du **Lab2**

## « Services Web : Authentification (NextAuth **ou** JWT **ou** Clerk) »


## 1) Objet

Poursuivre votre **Lab2** ou un projet existant en y intégrant une **authentification** centrée **services web** avec l’une des trois approches suivantes (au choix) :

* **Option A — NextAuth (sessions)**
* **Option B — JWT (stateless, signé côté serveur)**
* **Option C — Clerk (sessions gérées par un fournisseur)**

> L’évaluation porte sur le **back-end/service web** : endpoints, middleware, cookies/JWT, sécurité, contrôle d’accès **côté serveur**, journalisation, et **documentation**. L’UI n’est pas l’axe principal.



## 2) Résultats d’apprentissage

À l’issue du projet, vous devez être capable de :

1. Mettre en œuvre un **flux d’authentification** robuste (login, session/token, logout).
2. Protéger des **routes** (API & pages) par **middleware** et contrôles **serveur**.
3. Gérer **cookies/JWT** de manière **sécurisée** (HttpOnly, Secure, SameSite, exp/refresh).
4. Rédiger une **documentation exécutable** (README pas-à-pas, OpenAPI/Postman, schémas).
5. Prouver le fonctionnement via **tests** (succès/erreurs) et **logs**.



## 3) Contraintes (obligatoires)

* **Service web first** : toute vérification d’accès se fait **au serveur** (route handlers/middleware/server actions).
* **Contrat d’API** : fournir **OpenAPI (YAML/JSON)** *ou* **Collection Postman** (+ exemples cURL).
* **`.env.example`** documenté ; **aucune clé réelle** dans le dépôt.
* **Validation d’entrée** (zod/yup/DTO) et **statuts HTTP** cohérents (200/201/400/401/403/409/422/500).
* **Schémas** requis :

  * **Architecture** (Client → API/middleware → store/DB/fournisseur),
  * **Séquence** (login → session/token → ressource protégée → logout → expiry/refresh).
* **Journal de tests** (tableau) et **logs** (INFO/ERROR) sans fuite de secrets/PII.



## 4) Spécifications minimales par option

### Option A — **NextAuth (sessions)**

* Au moins **un provider** (Email/OAuth/Credentials).
* **Cookies** de session (`HttpOnly`, `Secure` en prod, `SameSite`).
* **Middleware** protégeant un espace (ex. `/admin/*`) + contrôles dans **server actions**.
* **Logout** invalide la session.
* Si rôle requis : persistance `role` en DB et vérification **serveur**.

**Esquisse (indicative)**

```js
// /app/api/auth/[...nextauth]/route.js
import NextAuth from "next-auth";
import Credentials from "next-auth/providers/credentials";
export const authOptions = {
  providers: [Credentials({ /* authorize: vérif serveur */ })],
  session: { strategy: "jwt" }, // ou "database"
  pages: { signIn: "/login" }
};
const handler = NextAuth(authOptions);
export { handler as GET, handler as POST };

// middleware.js
export { default } from "next-auth/middleware";
export const config = { matcher: ["/admin/:path*"] };
```



### Option B — **JWT (stateless)**

* Endpoint `POST /api/auth/login` → retourne un **JWT signé** (en-tête `Authorization: Bearer` ou **cookie HttpOnly** signé).
* **Middleware** de vérification JWT (signature, `exp`, éventuellement `aud/iss`).
* **Refresh** (optionnel mais recommandé) : couple `access` (court) + `refresh` (long) avec rotation.
* **Logout** : liste de révocation (en mémoire/DB) **ou** invalidation côté client + rotation stricte.

**Esquisse (indicative)**

```js
// /app/api/auth/login/route.js
import jwt from "jsonwebtoken";
export async function POST(req) {
  const { email, password } = await req.json();
  // Vérif serveur...
  const token = jwt.sign({ sub:"userId123", role:"user" }, process.env.JWT_SECRET, { expiresIn:"15m" });
  return new Response(JSON.stringify({ token }), { status:200 });
}

// middleware.js
import jwt from "jsonwebtoken";
export async function middleware(req) {
  const auth = req.headers.get("authorization") || "";
  const token = auth.startsWith("Bearer ") ? auth.slice(7) : null;
  if (!token) return new Response("Unauthorized", { status:401 });
  try { jwt.verify(token, process.env.JWT_SECRET); return; }
  catch { return new Response("Unauthorized", { status:401 }); }
}
export const config = { matcher:["/admin/:path*","/api/protected/:path*"] };
```



### Option C — **Clerk (sessions gérées)**

* Configuration du projet dans Clerk (callback URLs, clés env).
* **Middleware Clerk** pour imposer la session et récupérer l’identité côté serveur.
* Protection **serveur** d’API/pages et mapping **rôles** (via claims/metadata) si requis.
* **Logout** via SDK Clerk.

**Esquisse (indicative)**

```js
// middleware.js
import { authMiddleware } from "@clerk/nextjs";
export default authMiddleware({ publicRoutes: ["/login","/"] });
export const config = { matcher: ["/((?!.*\\..*|_next).*)"] };

// Exemple route handler
import { auth } from "@clerk/nextjs";
export async function GET() {
  const { userId, sessionId } = auth(); // côté serveur
  if (!userId) return new Response("Unauthorized", { status:401 });
  return new Response(JSON.stringify({ ok:true }), { status:200 });
}
```


## 5) Livrables

1. Rapport avec documentation complète, commandes à exécuter et les imprimes écrans
   * **Procédure pas-à-pas** (installation → env → exécution → vérifications).
   * **Contrat d’API** (OpenAPI/Postman) + **exemples cURL**.
   * **Schémas** (architecture + séquence).

3. **`.env.example`** commenté.
4. **Preuve** : déploiement ou **vidéo** 3–6 min montrant **appels API** (login/session ou JWT), réponses HTTP, protections 401/403, logout.



## 6) Barème (100 points)

| Axe (Services Web)     | Critères                                                        |    Pts |
| ---------------------- | --------------------------------------------------------------- | -----: |
| **Documentation**      | README pas-à-pas, structure académique, reproductibilité        | **40** |
| **Contrat d’API**      | OpenAPI/Postman complet + cURL alignés                          | **10** |
| **Conception d’API**   | Nommage, verbes, statuts HTTP, validation d’entrées             | **5** |
| **Sessions/JWT**       | Création/lecture/invalidation, cookies/JWT sûrs, expiry/refresh | **15** |
| **Protection serveur** | Middleware & contrôles serveur, 401/403 corrects                | **30** |


**Total : 100** — **Bonus +5** : mapping de rôles (user/admin) avec garde serveur propre et testé.



## 7) Plan de tests — gabarit à inclure

| Cas                            | Pré-conditions  | Requête                                    | Attendu            |
| ------------------------------ | --------------- | ------------------------------------------ | ------------------ |
| Login valide                   | User existe     | `POST /api/auth/login` ou sign-in provider | `200` + cookie/JWT |
| Login invalide                 | —               | Id/Pwd faux                                | `401`              |
| Session absente                | —               | `GET /api/auth/session`                    | `401`              |
| Accès protégé sans auth        | —               | `GET /api/admin/users`                     | `401`              |
| Accès protégé rôle insuffisant | Session `user`  | `GET /api/admin/users`                     | `403`              |
| Accès protégé rôle ok          | Session `admin` | `GET /api/admin/users`                     | `200`              |
| Logout                         | Session active  | `POST /api/auth/logout`                    | `204/200`          |
| Expiration                     | TTL dépassé     | Ressource protégée                         | `401`              |



## 8) Checklist sécurité (à cocher dans le README)

* [ ] **Contrôles d’accès côté serveur** (middleware/route handlers) opérationnels.
* [ ] **Cookies** : `HttpOnly`, `Secure` (prod), `SameSite` ajusté.
* [ ] **JWT** : `exp`, alg signé, secret en env, pas de PII dans le payload.
* [ ] **Validation** des entrées (zod/yup/DTO) et messages d’erreurs sobres.
* [ ] **Logs** sans secrets, niveau INFO/ERROR.
* [ ] **.env.example** complet, secrets non commit.





### Conseils

* Commencez par **le serveur** (endpoints + middleware), testez avec **cURL/Postman**, puis branchez l’UI.
* Faites d’abord passer les **tests 401/403** (sans UI), puis finalisez le login/logout.
* Gardez les logs clairs et brefs;
