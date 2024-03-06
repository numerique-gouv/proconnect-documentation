# AgentConnect - Fournisseur de Service

Vous souhaitez implémenter AgentConnect sur votre site? Vous êtes au bon endroit ! Cette documentation présente l'ensemble des informations à connaitre.

## 1. 👩‍🏫 Préambule

Cette documentation est à destination des Fournisseurs de Services souhaitant intégrer AgentConnect. AgentConnect est implémenté sur deux plateformes, une dite "RIE" (l’agent se connecte depuis le RIE, à un FS RIE via un FI RIE) et une autre dite "Internet" (l'agent se connecte depuis Internet, à un FS Internet via un FI Internet). Toutefois il est possible de communiquer entre les deux plateformes grâce à "l'hybridge Internet/RIE" (l'agent se connecte depuis Internet, à un Fournisseur de Services Internet via un FI RIE).


## 2. ⚙️ Les étapes pour intégrer AgentConnect


Vous souhaitez devenir Fournisseur de Services pour AgentConnect, voici les éléments à prendre en compte :

- [Quelles sont les étapes pour devenir Fournisseur de Services ?](doc_fs/pilotage_fca/pilotage_fca_etapes.md)

___

**🤓 TL;DR**

Voici un résumé des étapes pour être fournisseur de service AgentConnect :

- [ ] Je me familiarise avec la cinématique OpenIDConnect : voir [concepts de base](https://github.com/france-connect/Documentation-AgentConnect/blob/main/doc_fs.md#31-je-souhaite-conna%C3%AEtre-le-concept-de-base-dagentconnect)
- [ ] [_Optionnel_] Je contacte l'équipe AgentConnect pour qu'elle puisse répondre à mes questions si j'en ai : support.partenaires@agentconnect.gouv.fr ou [sur notre chaîne Tchap](https://www.tchap.gouv.fr/#/room/!kBghcRpyMNThkFQjdW:agent.dinum.tchap.gouv.fr)
- [ ] Je souhaite lancer les développements en test, pour ceci je renseigne à l'équipe AgentConnect les informations techniques comme les `redirect_uris` ou `post_logout_redirect_uris` en remplissant [un formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca)
- [ ] J’ai récupéré mon `client_id` et mon `client_secret` de test auprès de l’équipe AgentConnect
- [ ] J’affiche un bouton AgentConnect conforme sur mon application en environment de développement : voir [Spécifications visuelles](https://github.com/france-connect/Documentation-AgentConnect/blob/main/doc_fs/implementation_fca/spec_recette_fca.md)
- [ ] J’ai installé et paramétré mon client OpenID sur mon application en développement : voir [Spécifications techniques](https://github.com/france-connect/Documentation-AgentConnect/blob/main/doc_fs.md#3--jint%C3%A8gre-agentconnect-dans-mon-service-en-ligne)
- [ ]  Mon implémentation fonctionne
- [ ]  Je contractualise officiellement ma collaboration avec la Dinum en remplissant le [DataPass dédié](https://datapass.api.gouv.fr/agent-connect-fs)
- [ ]  Le DataPass étant validé, j’ai récupéré mon `client_id` et mon `client_secret` de production en remplissant [le formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca) avec les informations de production
- [ ]  Mise en production 🚀

___



## 3. 💻 J'intègre AgentConnect dans mon service en ligne

### 3.1. Je souhaite connaître le concept de base d'AgentConnect

- [Qu'est ce que le protocole OpenID Connect ?](doc_fs/technique_fca/technique_oidc.md)
- [Comment AgentConnect utilise OpenID Connect ?](doc_fs/technique_fca/technique_fca_oidc.md)
- [Quelles sont les données que je peux récupérer par AgentConnect sur les agents ?](doc_fs/projet_fca/projet_fca_donnees.md)

### 3.2. Je veux savoir comment fonctionne AgentConnect et comment identifier/authentifier les agents

- [Quel est le détail du fonctionnement ?](doc_fs/fonctionnement_fca/details_fonctionnement.md)
- [Quels sont les endpoints sur AgentConnect (le contrat d'API) ?](doc_fs/technique_fca/endpoints.md)
- [Quelles sont les données que je peux récupérer par AgentConnect sur mes usagers ?](doc_fs/projet_fca/projet_fca_donnees.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs ? ](doc_fs/technique_fca/technique_fca_scope.md)
- [Quelles sont les données d'AgentConnect qui expirent ?](doc_fs/technique_fca/donnees_expirent.md)
- [Qu'est ce qu'eIDAS et quel est le niveau de garantie d'AgentConnect ?](doc_fs/projet_fca/projet_fca_niveau_eidas.md)

### 3.3. Je veux savoir comment intégrer le bouton AgentConnect

- [Quel bouton AgentConnect intégrer et comment l'intégrer ?](doc_fs/implementation_fca/bouton_fca.md)

### 3.4. Je veux savoir comment déconnecter l'agent d'AgentConnect

- [Comment déconnecter l'agent d'AgentConnect ?](doc_fs/deconnexion_fca/deconnexion.md)
- [Comment révoquer l'access token ?](doc_fs/deconnexion_fca/access_token.md)

### 3.5. Je veux connaître les différents environnements disponibles

- [Comment accéder aux différents environnements d'AgentConnect ?](doc_fs/technique_fca/technique_fca_env.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](doc_fs/test_fca/test_fca_demonstrateur.md)

### 3.6. Je souhaite obtenir des informations sur la gestion d'erreurs entre AgentConnect et le Fournisseur de Services

- [Comment les erreurs entre AgentConnect et le Fournisseur de Services sont-elles gérées ?](doc_fs/erreur_fca/gestion_erreur.md)

### 3.7. Je souhaite connaitre les spécifications visuelles d'AgentConnect

- [Quel bouton AgentConnect intégrer et comment l'intégrer ?](doc_fs/implementation_fca/bouton_fca.md)
- [Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?](doc_fs/implementation_fca/spec_recette_fca.md)

## 4. 🚀 Je souhaite mettre mon Fournisseur de Services en production

- [Comment faire qualifier mon implémentation ?](doc_fs/recette_fca/recette.md)
- [Comment recevoir mes jetons de production ?](doc_fs/recette_fca/recette_cles_prod.md)



## 5. 📚 Ressources supplémentaires

- [Quels sont les acteurs à impliquer dans l'intégration d'AgentConnect ?](doc_fs/pilotage_fca/pilotage_fca_demarches_acteurs.md)
- [Qu'est-ce que la plateforme "Internet", la plateforme "RIE" et l'"Hybridge" ?](doc_fs/pilotage_fca/plateformes.md)
- [Contrat d'API AgentConnect](doc_fs/./technique_fca/endpoints.md)

## 6. 📑 Glossaire

#### 6.1.1. **AC_URL:**

URL d’AgentConnect.

#### 6.1.2. **FS_URL:**

Votre URL, en tant que Fournisseur de Services.

#### 6.1.3. **REDIRECT_URI:**

Le callback du Fournisseur de Services, communiqué lors de son inscription auprès d’AgentConnect.

#### 6.1.4. **POST_LOGOUT_REDIRECT_URI:**

L'URL de redirection après la demande de déconnexion AgentConnect.

#### 6.1.5. **CLIENT_ID:**

Identifiant du Fournisseur de Services, communiqué lors de son inscription auprès de AgentConnect.

#### 6.1.6. **CLIENT_SECRET:**

Le secret du Fournisseur de Services, communiqué lors de son inscription auprès de AgentConnect.

#### 6.1.7. **AUTHZ_CODE:**

Code retourné (dans l'URL) par AgentConnect au Fournisseur de Services lorsque ce dernier fait un appel sur le endpoint AC_URL/api/v2/authorize. Il est ensuite passé (dans le corps de la requête HTTP POST) lors de l'appel sur le endpoint AC_URL/api/v2/token.

#### 6.1.8. **ACCESS_TOKEN:**

Token retourné (dans le corps HTTP) par l'appel au endpoint AC_URL/api/v2/token. Il est ensuite passé lors de l'appel au endpoint AC_URL/api/v2/userinfo.

#### 6.1.9. **SCOPES:**

Liste des scopes demandés séparés par des espaces (donc par "%20"  ou "+" au format unicode dans l'URL).

Voici la liste supportée par AgentConnect :

    * openid : obligatoire, permet de demander l'identifiant technique de l'utilisateur au format OpenIDConnect
    * email : obligatoire, permet de récupérer l'adresse électronique de l’agent

Cette liste de scopes est définie par la norme OpenIDConnect.

#### 6.1.10. **ID_TOKEN:**

Objet JWT retourné par l'appel au endpoint AC_URL/api/v2/token. L'objet JWT est un objet JSON formaté et signé. Le JSON doit contenir ces six clés : aud,exp,iat,iss,sub et nonce.

Exemple :

```json
{
    'aud':'895fae591ccae777094931e269e46447',
    'exp':1412953984,
    'iat':1412950384,
    'iss':http://Agentconnect.gouv.fr,
    'sub':YWxhY3JpdMOp,
    'idp':'AC',
    'nonce':'12344354597459'
}
```
Les champs *aud, exp, iat, iss, sub* sont des champs obligatoires de la norme OpenId Connect. Le *nonce* est un  paramètre obligatoirement envoyé lors de l'appel à `api/v2/authorize`. Le Fournisseur de Services doit impérativement vérifier que la valeur correspond bien à celle qu'il a envoyée, et qui doit être liée à la session de l'utilisateur.

Si vous utilisez une librairie pour transformer le json en JWT, il génèrera une chaîne de caractères constituée de 3 chaînes de caractères encodées en base64 séparées par des points (ex: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c).

#### 6.1.11. **ID_TOKEN_HINT:**

Objet JWT identique au format ID_TOKEN qui a été reçu lors de l'échange avec l'appel à AC_URL/api/v2/token et doit être passé en paramètre lors de l'appel à AC_URL/api/v2/logout.

#### 6.1.12. **USERINFO:**

Objet JWT retourné par l'appel au endpoint AC_URL/api/v2/userinfo. L'objet JWT est un objet JSON formaté et signé. Le JSON doit contenir ces six clés : aud,exp,iat,iss,sub.

Exemple :

```json
{
  "sub": "704e024229015d2bd47f7a5e5ab05b35c8336ab403c38022985f8cfadc86fe91",
  "uid": "1",
  "given_name": "Angela Claire Louise",
  "usual_name": "DUBOIS",
  "email": "test@abcd.com",
  "siren": "343293775",
  "siret": "34329377500037",
  "organizational_unit": "comptabilite",
  "belonging_population": "agent",
  "phone_number": "+331-12-44-45-23",
  "chorusdt:matricule": "USER_AGC",
  "chorusdt:societe": "CHT",
  "idp_id": "fia1v2",
  "idp_acr": "eidas1",
  "aud": "6925fb8143c76eded44d32b40c0cb1006065f7f003de52712b78985704f39950",
  "exp": 1668779720,
  "iat": 1668779660,
  "iss": "https://fca.integ01.dev-agentconnect.fr/api/v2"
}
```
Les champs *aud, exp, iat, iss, sub* sont des champs obligatoires de la norme OpenId Connect.

Si vous utilisez une librairie pour transformer le json en JWT, il génèrera une chaîne de caractères constituée de 3 chaînes de caractères encodées en base64 séparées par des points.

#### 6.1.13. **STATE:**

Champ obligatoire, généré aléatoirement par le Fournisseur de Services, que AgentConnect renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par le Fournisseur de Services. Il est utilisé afin d’empêcher l’exploitation de failles CSRF.

#### 6.1.14. **NONCE:**

Champ obligatoire, généré aléatoirement par le Fournisseur de Services que AgentConnect renvoie tel quel dans la réponse à l'appel à /token, pour être ensuite vérifié par le Fournisseur de Services. Il est utilisé pour empêcher les attaques par rejeu.

#### 6.1.15. **SUB:**

Identifiant technique (unique et stable dans le temps pour un individu donné) fourni par AgentConnect au Fournisseur de Services. Le SUB est présent dans l'IdToken retourné au Fournisseur de Services ainsi que dans les informations d'identité (/userinfo). Le SUB retourné par AgentConnect est spécifique à chaque Fournisseur de Services et à chaque Fournisseur d'Identité: un même utilisateur aura toujours le même SUB pour un Fournisseur d'Identité donné, en revanche il aura un SUB différent pour chaque Fournisseur de Services qu'il utilisera.