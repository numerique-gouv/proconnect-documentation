[Accueil](../README.md) > [ProConnect - Fournisseur de Service](README.md) > Implémentation Technique

---

# 🔧 Implémentation du protocole OIDC (authorization code flow) pour un Fournisseur de Service

## 📢 1. Préambule
### 1.1. Identifiants de tests
Pour tester la configuration de votre Fournisseur de Service tout au long de l'intégration, vous aurez besoin de vous connecter via un Fournisseur d'Identité.
Vous trouverez [ici](./identifiants-fi-test.md) les identifiants pour vous connecter au Fournisseur d'Identité de test.

### 1.2. Valeur de PROCONNECT_DOMAIN
Pour savoir quelles URL appeler au cours de l'authentification, vous aurez besoin de connaître la valeur de PROCONNECT_DOMAIN qui correspond à votre environnement et votre réseau. Vous la trouverez à [ce lien](../resources/valeur_ac_domain.md).

### 1.3. Exemple d'intégration réussie

[Dépôt Github d'un client ProConnect](https://github.com/numerique-gouv/proconnect-test-client)

## 📘 2. Mode d'emploi technique
### 2.1. Intégrer le bouton ProConnect sur votre page de connexion

[Quel bouton ProConnect intégrer et comment l'intégrer ?](./bouton_proconnect.md)

### 2.2. Faire pointer le bouton ProConnect vers le `authorization_endpoint`
Si vous utilisez une bibliothèque agréée, nous vous recommandons de récupérer les URLs via notre Discovery URL : `https://PROCONNECT_DOMAIN/api/v2/.well-known/openid-configuration`.
Cette Discovery URL vous donnera notamment quatre endpoints qui vous serviront par la suite :
- `authorization_endpoint`
- `token_endpoint`
- `userinfo_endpoint`
- `end_session_endpoint`

Au clic sur le bouton ProConnect :
- générer un `state` et un `nonce` aléatoires et stockez-les dans la session du navigateur
- rediriger l'utilisateur vers le `authorization_endpoint`. Les query parameters à ajouter sont décrits ci-dessous.

<details>
 <summary><code>GET</code> <code><b>https://PROCONNECT_DOMAIN/api/v2/authorize</b></code> </summary>

##### 2.2.1.1. Description

Implémente le `Authorization Endpoint` de Openid Connect:

https://openid.net/specs/openid-connect-core-1_0.html#AuthorizationEndpoint

##### 2.2.1.2. Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `response_type` | requis | string | `code` |
> | `client_id` | requis | string | `<CLIENT_ID>` Identifiant du FS, communiqué lors de son inscription auprès de ProConnect |
> | `redirect_uri` | requis | string |`<FS_URL>/<URL_CALLBACK>` URL de retour vers le FS, communiquée dans le formulaire Démarches Simplifiées. Attention, cette URL doit être encodée pour être passée en query parameter, doit correspondre exactement à celle communiquée à ProConnect, et est sensible à la présence ou non du `/` final |
> | `scope` | requis | string | `<SCOPES>` Liste des scopes demandés séparés par des espaces (%20 au format unicode dans l'URL) ou des '+' |
> | `claims` | optionnel | string | `<CLAIMS>` Objet JSON encodé décrivant les claims demandés. Pour récupérer le claim `amr` qui indique le mode d'authentification double facteur utilisé, spécifiez la valeur `{"id_token":{"amr":{"essential":true}}}`. Cf. [quelles sont les valeurs possibles pour le champ amr ?](../resources/claim_amr.md) |
> | `state` | requis | string (minimum 32 caractères) | `<STATE>` Champ obligatoire, généré aléatoirement par le FS, que ProConnect renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par le FS. Il est utilisé afin d’empêcher l’exploitation de failles CSRF |
> | `nonce` | requis | string (minimum 32 caractères) | `<NONCE>` Champ obligatoire, généré aléatoirement par le FS que ProConnect renvoie tel quel dans la réponse à l'appel au `Token Endpoint`, pour être ensuite vérifié par le FS. Il est utilisé pour empêcher les attaques par rejeu |
> | `prompt` | optionnel | string | `login` si le FS veut forcer la reauthentification au FI. Par défaut, le FI réutilisera une session existante sans demander une reconnexion. (Single Sign-On côté FI) |
> | `idp_hint` | optionnel | string | `idp_id` désignant le FI vers lequel rediriger l'usager sans passer par la mire ProConnect (cf. [doc](./idp_hint_usage.md)) |
</details>

Le champ `scope` et sa différence avec la notion de `claims` sont expliqués [ici](./scope-claims.md). La liste des scopes que pouvez demander est spécifiée [ici](./donnees_fournies.md).

NB: tout paramètre supplémentaire dans l'URL génèrera une erreur `Y000400 : Bad Request Exception`. Il n'est pas possible d'ajouter d'autres paramètres.

### 2.3. Implémentation de la route **redirect_uri**
Il s'agit de la route vers laquelle sera redirigée votre utilisateur dans le navigateur après authentification par le Fournisseur d'Identité.

Les query parameters renvoyés dans l'URL sont décrits ci-dessous.

<details>
 <summary><code>GET</code> <code><b>redirect_uri?code=x&state=y</b></code> </summary>

##### 2.3.1.1. Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `code` | requis | string | code d'autorisation à transmettre au `token_endpoint`. |
> | `state` | requis | string (minimum 32 caractères) | `<state>` communiqué par par le FS dans l'appel au `authorization_endpoint`. Cette information est à vérifier par le FS, afin d’empêcher l’exploitation de failles CSRF |

</details>

NB : le `code` a une durée d'expiration de 30 secondes.

Votre serveur doit alors effectuer plusieurs actions en "back-channel".

#### 2.3.2. Vérification du state
Vérifier que le champ `state` récupéré en query parameter correspond bien au `state` généré précédemment et stocké dans la session du navigateur.

#### 2.3.3. Génération du token
Appeler le endpoint `token_endpoint` avec les paramètres décrits ci-dessous :

<details>
 <summary><code>POST</code> <code><b>https://PROCONNECT_DOMAIN/api/v2/token</b></code> </summary>

##### 2.3.3.1. Description

Implémente le `Token Endpoint` de Openid Connect:

https://openid.net/specs/openid-connect-core-1_0.html#TokenEndpoint

##### 2.3.3.2. Entête

> | nom | requis/optionnel | valeur |
> |----------------|--------|-------------------------------------|
> | `Content-Type` | requis | `application/x-www-form-urlencoded` |

##### 2.3.3.3. Body

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `grant_type` | requis | string | `authorization_code` |
> | `client_id` | requis | string | `<CLIENT_ID>` Identifiant du FS, communiqué lors de son inscription auprès de ProConnect |
> | `client_secret` | requis | string | `<CLIENT_SECRET>` Le secret du FS, communiqué lors de son inscription auprès de ProConnect |
> | `redirect_uri` | requis | string |` <FS_URL>%2F<URL_CALLBACK>` Url de retour vers le FS (encodée), communiqué lors de l'appel au `Authorization Endpoint` |
> | `code` | requis | string | `<AUTHZ_CODE>` code d'autorisation fourni par ProConnect après connexion |

##### 2.3.3.4. Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/json;charset=utf-8`        | La réponse contenant l'access token |
> | `400`       | `application/json;charset=utf-8`        | JSON document décrivant l'origine de l'erreur de format |

##### 2.3.3.5. Format de la réponse en succès

```
{
  'access_token': <ACCESS_TOKEN>,
  'token_type': 'Bearer',
  'expires_in': 60,
  'id_token': <ID_TOKEN>
}
```
</details>

Vous récupérez alors un JSON, qui contient notamment :
- `access_token`
- `id_token`.

L'`access_token` est un Bearer token. Sa durée de validité est de 60 secondes.

#### 2.3.4. Vérification de l'id_token et du nonce
L'`id_token` est un JWT, signé avec l'algorithme spécifié à ProConnect lors de l'enregistrement du FS (RS256, ES256 ou HS256).

Vérifier que le JWT est bien signé avec cet algorithme.

Une fois décodé, extraire le `nonce` et vérifier qu'il correspond bien au `nonce` stocké dans la session du navigateur.

#### 2.3.5. Stockage du id_token

Stocker le `id_token` dans la session du navigateur. Cette valeur sera utilisée plus tard, lors de la déconnexion auprès du serveur ProConnect.

#### 2.3.6. Récupération des user info
Appeler le endpoint `userinfo_endpoint`, en ajoutant l'`access_token` token dans l'en-tête Authorization, comme décrit ci-dessous :

<details>
 <summary><code>GET</code> <code><b>https://PROCONNECT_DOMAIN/api/v2/userinfo</b></code> </summary>

##### 2.3.6.1. Description

Implémente le `UserInfo Endpoint` de Openid Connect:

https://openid.net/specs/openid-connect-core-1_0.html#UserInfo

##### 2.3.6.2. Entête

> | nom | requis/optionnel | valeur |
> |----------------|--------|-------------------------------------|
> | `Authorization` | requis | `Bearer <access_token>` où `<access_token>` a été communiqué par le `Token Endpoint` |

##### 2.3.6.3. Paramètres

> Aucun

##### 2.3.6.4. Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/jwt`                   | JSON Web Token signé par l'algorithme spécifié à ProConnect, contenant les claims transmis par le FI  |
> | `400`       | `application/json;charset=utf-8`    | JSON document décrivant l'origine de l'erreur de format |

</details>

#### 2.3.7. Authentification de l'utilisateur
Le endpoint `user_info_endpoint` renvoie un JWT, signé avec l'algorithme spécifié à ProConnect lors de l'enregistrement du FS (RS256, ES256 ou HS256).

Vérifier que le JWT est bien signé avec cet algorithme.

Une fois en possession des informations de votre utilisateur, vous pouvez gérer comme vous le souhaitez sa session.

NB: la session Agent Connect a une durée de 12 heures.
- si vous souhaitez que vos sessions utilisateurs durent **plus** de 12 heures, c'est possible : lorsque votre session utilisateur sera expirée de votre côté, alors le clic sur le bouton "S'identifier avec ProConnect" renverra bien vers la mire d'authentification car la session ProConnect se sera terminée avant.
- si vous souhaitez que vos sessions utilisateurs durent **moins** de 12 heures, si votre utilisateur clique sur "S'identifier avec ProConnect" entre la fin de votre session et la fin de celle de ProConnect, il sera automatiquement reconnecté à votre service. Une option `max-age` est décrite dans [la spec OIDC](https://openid.net/specs/openid-connect-core-1_0.html#AuthRequest) et permet de gérer ce cas, mais celle-ci n'est pas encore implémentée sur ProConnect.

### 2.4. Déconnexion de l'utilisateur
Au clic sur votre bouton de déconnexion, effectuer les actions suivantes :

#### 2.4.1. Déconnexion auprès de ProConnect
Récupérer l'`id_token` stocké dans la session du navigateur.
Appeler le endpoint `end_session_endpoint` avec les paramètres décrits ci-dessous.

<details>
 <summary><code>GET</code> <code><b>/api/v2/session/end</b></code> </summary>

##### 2.4.1.1. Description

Implémente le `Logout Endpoint` de Openid Connect:

http://openid.net/specs/openid-connect-session-1_0.html#RPLogout

:warning: Cet appel doit être réalisé via une redirection dans le navigateur de l'agent, afin d'expirer les cookies de session ProConnect et FI.

##### 2.4.1.2. Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `id_token_hint` | requis | string | `<id_token>` contenu dans la réponse du `Token Endpoint` |
> | `state` | requis | string | `<state>` Champ obligatoire, généré aléatoirement par le FS, que ProConnect renvoie tel quel dans la redirection qui suit la déconnexion, pour être ensuite vérifié par le FS. Il est utilisé afin d’empêcher l’exploitation de failles CSRF |
> | `post_logout_redirect_uri` | requis | string | `<post_logout_redirect_uri>` URL de retour vers le FS, communiquée dans le formulaire Démarches Simplifiées. Attention, cette URL doit être encodée pour être passée en query parameter, doit correspondre exactement à celle communiquée à ProConnect, et est sensible à la présence ou non du `/` final |

##### 2.4.1.3. Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|-------------------------------------------------------------------|
> | `303`         | `text/html;charset=UTF-8`         | Redirection vers le FI pour déconnexion, puis redirection vers le FS après déconnexion |

##### 2.4.1.4. Exemple d'appel

> ```
> GET /api/v2/session/end?id_token_hint=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI3MDRlMDI0Mj
> I5MDE1ZDJiZDQ3ZjdhNWU1YWIwNWIzNWM4MzM2YWI0MDNjMzgwMjI5ODVmOGNmYWRjODZmZTkxIiwiYW1yIjpbInB3ZCJdLCJ
> hdXRoX3RpbWUiOjE2Njg1MzAzMjYsImFjciI6ImVpZGFzMSIsIm5vbmNlIjoiYWZjODFmZGExZmJiNmQzYzg3NmFmNzVjNzM3
> YTEzMDdhMWIyOWJhMDg3M2VmYTA1OWU0NTM1ZDEyMmM5ZGI1YSIsImF0X2hhc2giOiJJVEJTV1J2NW1HRmxxTGQ0Sm5nbnRnI
> iwiYXVkIjoiNjkyNWZiODE0M2M3NmVkZWQ0NGQzMmI0MGMwY2IxMDA2MDY1ZjdmMDAzZGU1MjcxMmI3ODk4NTcwNGYzOTk1MC
> IsImV4cCI6MTY2ODUzMDM4NiwiaWF0IjoxNjY4NTMwMzI2LCJpc3MiOiJodHRwczovL2ZjYS5pbnRlZzAxLmRldi1hZ2VudGN
> vbm5lY3QuZnIvYXBpL3YyIn0.hg1n4WJbzZECwz4VldAybXYreEXJ4fxpSWqDs9V4tTk&
> state=3b7bd7fb38ccab89864563f17a89c4cb3bd400164ce828b4cfc2cb01ce8ed9da&
> post_logout_redirect_uri=https%3A%2F%2Ffsa1v2.integ01.dev-agentconnect.fr%2Flogout-callback HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> ```

</details>

#### 2.4.2. Implémentation de la route `post_logout_redirect_uri`
Il s'agit de la route vers laquelle sera redirigée votre utilisateur dans le navigateur après authentification par le Fournisseur d'Identité.

Le query parameter renvoyé dans l'URL est décrit ci-dessous.

<details>
 <summary><code>GET</code> <code><b>FS_URL/POST_LOGOUT_REDIRECT_URI?state=x</b></code> </summary>

##### 2.4.2.1. Description

Redirection vers le FS après déconnexion.

ProConnect renvoie le state communiqué par le FS lors de la demande de déconnexion.

##### 2.4.2.2. Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `state` | requis | string (minimum 32 caractères) | `<state>` communiqué par par le FS dans l'appel au `Logout Endpoint`. Cette information est à vérifier par le FS, afin d’empêcher l’exploitation de failles CSRF | |

##### 2.4.2.3. Exemple d'appel

Exemple de retour vers le FS de mock à déconnexion

> ```
> GET /logout-callback?state=3b7bd7fb38ccab89864563f17a89c4cb3bd400164ce828b4cfc2cb01ce8ed9da HTTP/1.1
> Host: fsa1v2.integ01.dev-agentconnect.fr
> ```

</details>

#### 2.4.3. Vérification du state
Vérifier que le champ `state` récupéré en query parameter correspond bien au `state` généré lors de la connexion et stocké dans la session du navigateur.

#### 2.4.4. Suppression des informations de connexion
Supprimer les informations de connexion stockée dans la session du navigateur
