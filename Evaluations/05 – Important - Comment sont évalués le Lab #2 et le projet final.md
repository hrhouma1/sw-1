<h1 id="explication-evaluations">Explication claire des évaluations : Laboratoire #2 et Projet intégrateur</h1>

Bonjour à toutes et à tous,

Afin d'éviter toute confusion et clarifier définitivement l’organisation des évaluations dans le cours, voici des précisions importantes concernant le **Laboratoire #2** et le **Projet intégrateur final** :

# 1 - Situation annoncée en classe

| Évaluation         | Contenu promis initialement                                               | Pondération |
| ------------------ | ------------------------------------------------------------------------- | ----------- |
| Laboratoire #2     | Création des services web uniquement (API REST créée par vous)            | **20 %**    |
| Projet intégrateur | Création + Consommation (Stripe) + Documentation API + Présentation orale | **40 %**    |

### Clarification importante (à lire attentivement)

**Vous allez réaliser un seul et unique projet intégrateur complet, divisé clairement en deux étapes :**

1. **Laboratoire #2 (20%) :**
   Vous rendrez une première version intermédiare du projet intégrateur. Cette remise concerne **uniquement la partie création des services web** (routes API REST créées par vous-mêmes : authentification, gestion des photos, interface administrateur, etc.).

   À ce stade, **vous ne serez évalués que sur les parties où vous jouez le rôle de "producteur" d’une API REST**.

2. **Projet intégrateur final (40%) :**
   Vous allez continuer et compléter votre projet intégrateur pour remettre une version finale exhaustive comprenant :

   * La partie **création d’API** (qui aura déjà été évaluée dans le Lab #2 mais devra être complétée et améliorée si nécessaire).
   * La partie **consommation** (intégration complète du paiement Stripe, création des sessions de paiement et gestion des webhooks).
   * La **documentation complète de votre API** avec Postman (ou Swagger).
   * Une courte **présentation orale** accompagnée d’un fichier PPT (PowerPoint), où vous présentez brièvement votre projet, votre architecture, les services web créés et consommés, ainsi que votre expérience sur Stripe.

### Résumé sous forme de tableau synthétique :

| Évaluation                   | Éléments évalués                                                                            | Pondération |
| ---------------------------- | ------------------------------------------------------------------------------------------- | ----------- |
| **Laboratoire #2**           | **Création uniquement : API REST** (authentification, photos, routes privées/admin)         | **20 %**   |
| **Projet intégrateur final** | **Création (finalisée) + Consommation (Stripe) + Documentation + Présentation orale (PPT)** | **40 %**   |

**Important :**

* Le **Laboratoire #2** représente une première version de votre projet intégrateur (partie création seulement). Vous aurez du feedback sur cette étape, ce qui vous permettra d'améliorer votre travail pour le projet intégrateur final.
* Le **projet intégrateur final** inclut tout le projet : création finale (avec prise en compte du feedback), consommation Stripe, documentation et présentation orale.

N'hésitez pas à me contacter si vous avez des questions complémentaires ou besoin d'une clarification.

Bon courage à tous !




# 2 - Grilles d’évaluation 

> Ces deux tableaux sont indépendants :
> – **TP2** évalue exclusivement la **création** des services web.
> – **Projet intégrateur final** évalue l’ensemble du projet (création finalisée + consommation Stripe + documentation + présentation).



# 2.1. Grille d’évaluation — **TP2 : Création des services web**

| # | Critère évalué                                                                                     | Poids |
| - | -------------------------------------------------------------------------------------------------- | ----: |
| 1 | Modélisation et schéma Prisma (User, Photo, rôles)                                                 |  20 % |
| 2 | Routes API Auth : `/api/register`, `/api/login`, `/api/logout`  (validation, hashage mot de passe) |  20 % |
| 3 | Routes CRUD Photos : `/api/photos`, `/api/photos/:id` (upload, update, delete sécurisés)           |  20 % |
| 4 | Middleware de sécurité (vérification JWT/cookie, protection des routes privées)                    |  20 % |
| 5 | Qualité du code & organisation (conventions Next.js, gestion des erreurs HTTP)                     |  10 % |
| 6 | Tests manuels Postman (collection fournie et fonctionnelle)                                        |  10 % |
|   | **Total TP2**                                                                                      | 100 % |



# 2.2. Grille d’évaluation — **Projet intégrateur final**

| # | Critère évalué                                                                                |  Poids |
| - | --------------------------------------------------------------------------------------------- | -----: |
| 1 | API REST finalisée (corrections TP2 appliquées, interface admin complète)                     |   25 % |
| 2 | Intégration Stripe Checkout (création de session, gestion des erreurs)                        |   20 % |
| 3 | Webhook Stripe (vérification de signature, attribution des photos achetées)                   |   15 % |
| 4 | Documentation API (collection Postman ou Swagger complète et à jour)                          | 12,5 % |
| 5 | Interface utilisateur (pages Next.js fonctionnelles : register, login, gallery, dashboard)    |   10 % |
| 6 | Présentation orale + support PPT (architecture, démo fluide en ≈ 5 min)                       |   10 % |
| 7 | Qualité du code, déploiement & README (variables d’environnement, procédure de mise en route) |  7,5 % |
|   | **Total Projet intégrateur**                                                                  |  100 % |



