# AgentConnect Endpoints

AgentConnect met en oeuvre le protocole OpenID Connect pour permettre à un Fournisseur de Services de déléguer à AgentConnect l'identification et l'authentification des agents.

#### Openid Configuration Endpoints

<details>
 <summary><code>GET</code> <code><b>/api/v2/.well-known/openid-configuration</b></code> </summary>

##### Description

Implémente la requête de `Provider Configuration`

https://openid.net/specs/openid-connect-discovery-1_0.html#ProviderConfigurationRequest

##### Paramètres

> Aucun

##### Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/json;charset=utf-8`        | Document JSON décrivant la configuration d'AgentConnect |

##### Exemple d'appel

> ```
> GET /api/v2/.well-known/openid-configuration HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> ```

Configuration AgentConnect sur l'environnement d'intégration: 

https://fca.integ01.dev-agentconnect.fr/api/v2/.well-known/openid-configuration

</details>

<details>
 <summary><code>GET</code> <code><b>/api/v2/jwks</b></code> </summary>

##### Description

Liste les clés de signature utilisées par AgentConnect

##### Paramètres

> Aucun

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/json;charset=utf-8`        | Document JSON décrivant les clés de signature d'AgentConnect |

##### Exemple d'appel

> ```
> GET /api/v2/jwks HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> ```

Clés AgentConnect sur l'environnement d'intégration: 

https://fca.integ01.dev-agentconnect.fr/api/v2/jwks

</details>

#### Authorization Endpoint

<details>
 <summary><code>GET</code> <code><b>/api/v2/authorize</b></code> </summary>

##### Description

Implémente le `Authorization Endpoint` de Openid Connect:

https://openid.net/specs/openid-connect-core-1_0.html#AuthorizationEndpoint

##### Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `response_type` | requis | string | `code` |
> | `client_id` | requis | string | `<CLIENT_ID>` Identifiant du FS, communiqué lors de son inscription auprès de AC |
> | `redirect_uri` | requis | string |` <FS_URL>%2F<URL_CALLBACK>` Url de retour vers le FS (encodée), communiquée lors de son inscription auprès de AC |
> | `acr_values` | requis | string | `eidas1` AgentConnect ne garantie que le niveau faible d'eIDAS |
> | `scope` | requis | string | `<SCOPES>` Liste des scopes demandés séparés par des espaces (%20 au format unicode dans l'URL) ou des '+' |
> | `claims` | optionnel | string | `<CLAIMS>` Objet JSON encodé décrivant les claims demandés ([Voir spécification Openid Connect](https://openid.net/specs/openid-connect-core-1_0.html#ClaimsParameter)) |
> | `state` | requis | string (minimum 32 caractères) | `<STATE>` Champ obligatoire, généré aléatoirement par le FS, que AC renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par le FS. Il est utilisé afin d’empêcher l’exploitation de failles CSRF |
> | `nonce` | requis | string (minimum 32 caractères) | `<NONCE>` Champ obligatoire, généré aléatoirement par le FS que AC renvoie tel quel dans la réponse à l'appel au `Token Endpoint`, pour être ensuite vérifié par le FS. Il est utilisé pour empêcher les attaques par rejeu |
> | `prompt` | optionnel | string | `login` si le FS veut forcer la reauthentification au FI. Par défaut, le FI réutilisera une session existante sans demander une reconnexion. (Single Sign-On côté FI) |

##### Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `303` (succès)        | `text/html;charset=UTF-8`        | Redirection vers la page de recherche des FI `/api/v2/interaction/{interactionHash}` où {interactionHash} est un hash lié à la session de l'usager |
> | `303` (erreur) | `text/html;charset=UTF-8`        | [Redirection vers le FS après erreur de connexion](#redirection-vers-le-fs-après-erreur-de-connexion) |
> | `400` (mauvais format)| `text/html;charset=UTF-8`        | La page d'erreur avec code `Y000400` est affichée en cas de mauvais format |

##### Exemple d'appel

> ```
> GET /api/v2/authorize?response_type=code&prompt=login&acr_values=eidas1&
> scope=openid+uid+given_name+usual_name+email&
> claims=%7B%22id_token%22%3A%7B%22amr%22%3A%7B%22essential%22%3Atrue%7D%7D%7D&
> client_id=6925fb8143c76eded44d32b40c0cb1006065f7f003de52712b78985704f39950&
> redirect_uri=https%3A%2F%2Ffsa1v2.integ01.dev-agentconnect.fr%2Foidc-callback&
> state=9ed67ae42fdc5d0a6867a5425a284745f4f73ce8b6edf76e453487aa1b73cc89&
> nonce=7db9b35458f2288bade947791f1c8fa2d02954f8eb7d9909dc68784f7c4aea29 HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> ```

</details>

<details>
 <summary><code>POST</code> <code><b>/api/v2/authorize</b></code> </summary>

##### Description

Implémente le `Authorization Endpoint` de Openid Connect:

https://openid.net/specs/openid-connect-core-1_0.html#AuthorizationEndpoint

##### Entête

> | nom | requis/optionnel | valeur |
> |----------------|--------|-------------------------------------|
> | `Content-Type` | requis | `application/x-www-form-urlencoded` |

##### Body

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `response_type` | requis | string | `code` |
> | `client_id` | requis | string | `<CLIENT_ID>` Identifiant du FS, communiqué lors de son inscription auprès de AC |
> | `redirect_uri` | requis | string |`<FS_URL>%2F<URL_CALLBACK>` Url de retour vers le FS (encodée), communiquée lors de son inscription auprès de AC |
> | `acr_values` | requis | string | `eidas1` AgentConnect ne garantie que le niveau faible d'eIDAS |
> | `scope` | requis | string | `<SCOPES>` Liste des scopes demandés séparés par des espaces (%20 au format unicode dans l'URL) ou des '+' |
> | `claims` | optionnel | string | `<CLAIMS>` Objet JSON encodé décrivant les claims demandés ([Voir spécification Openid Connect](https://openid.net/specs/openid-connect-core-1_0.html#ClaimsParameter)) |
> | `state` | requis | string (minimum 32 caractères) | `<STATE>` Champ obligatoire, généré aléatoirement par le FS, que AC renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par le FS. Il est utilisé afin d’empêcher l’exploitation de failles CSRF |
> | `nonce` | requis | string (minimum 32 caractères) | `<NONCE>` Champ obligatoire, généré aléatoirement par le FS que AC renvoie tel quel dans la réponse à l'appel au `Token Endpoint`, pour être ensuite vérifié par le FS. Il est utilisé pour empêcher les attaques par rejeu |
> | `prompt` | optionnel | string | `login` si le FS veut forcer la reauthentification au FI. Par défaut, le FI réutilisera une session existante sans demander une reconnexion. (Single Sign-On côté FI) |

##### Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `303` (succès)        | `text/html;charset=UTF-8`        | Redirection vers la page de recherche des FI `/api/v2/interaction/{interactionHash}` où {interactionHash} est un hash lié à la session de l'usager |
> | `303` (erreur) | `text/html;charset=UTF-8`        | [Redirection vers le FS après erreur de connexion](#redirection-vers-le-fs-après-erreur-de-connexion) |
> | `400` (mauvais format)| `text/html;charset=UTF-8`        | La page d'erreur avec code `Y000400` est affichée en cas de mauvais format |

##### Exemple d'appel

> ```
> POST /api/v2/authorize HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> Content-Type: application/x-www-form-urlencoded
>
> response_type=code&prompt=login&acr_values=eidas1&
> scope=openid+uid+given_name+usual_name+email&
> claims=%7B%22id_token%22%3A%7B%22amr%22%3A%7B%22essential%22%3Atrue%7D%7D%7D&
> client_id=6925fb8143c76eded44d32b40c0cb1006065f7f003de52712b78985704f39950&
> redirect_uri=https%3A%2F%2Ffsa1v2.integ01.dev-agentconnect.fr%2Foidc-callback&
> state=9ed67ae42fdc5d0a6867a5425a284745f4f73ce8b6edf76e453487aa1b73cc89&
> nonce=7db9b35458f2288bade947791f1c8fa2d02954f8eb7d9909dc68784f7c4aea29
> ```

</details>

#### Redirection vers le FS après erreur de connexion

<details>
 <summary><code>GET</code> <code><b>&lt;FS_URL&gt;/&lt;URL_CALLBACK&gt;</b></code> </summary>

##### Description

Redirection vers le FS après une erreur de connexion.

AgentConnect renvoie le code d'erreur, la description de l'erreur et le state.

##### Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `error` | requis | string | code d'erreur |
> | `error_description` | requis | string | description de l'erreur |
> | `state` | requis | string (minimum 32 caractères) | `<STATE>` communiqué par par le FS dans l'appel au `Authorization Endpoint`. Cette information est à vérifier par le FS, afin d’empêcher l’exploitation de failles CSRF |

##### Exemple d'appel

Exemple de retour vers le FS de mock

> ```
> GET /oidc-callback?state=9ed67ae42fdc5d0a6867a5425a284745f4f73ce8b6edf76e453487aa1b73cc89
> error_description=User+auth+aborted&error=access_denied HTTP/1.1
> Host: fsa1v2.integ01.dev-agentconnect.fr
> ```

</details>


#### Redirection vers le FS après connexion

<details>
 <summary><code>GET</code> <code><b>&lt;FS_URL&gt;/&lt;URL_CALLBACK&gt;</b></code> </summary>

##### Description

Redirection vers le FS après connexion chez le FI.

AgentConnect renvoie le code d'autorisation et le state.

##### Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `code` | requis | string | `<AUTHZ_CODE>` code d'autorisation à transmettre au `Token Endpoint` |
> | `state` | requis | string (minimum 32 caractères) | `<STATE>` communiqué par par le FS dans l'appel au `Authorization Endpoint`. Cette information est à vérifier par le FS, afin d’empêcher l’exploitation de failles CSRF |

##### Exemple d'appel

Exemple de retour vers le FS de mock

> ```
> GET /oidc-callback?code=_DOF10msXreojwyScrXmfqvwp8q3p1G7ZIzatMj60it&
> state=9ed67ae42fdc5d0a6867a5425a284745f4f73ce8b6edf76e453487aa1b73cc89 HTTP/1.1
> Host: fsa1v2.integ01.dev-agentconnect.fr
> ```

</details>

#### Token Endpoint

<details>
 <summary><code>POST</code> <code><b>/api/v2/token</b></code> </summary>

##### Description

Implémente le `Token Endpoint` de Openid Connect:

https://openid.net/specs/openid-connect-core-1_0.html#TokenEndpoint

##### Entête

> | nom | requis/optionnel | valeur |
> |----------------|--------|-------------------------------------|
> | `Content-Type` | requis | `application/x-www-form-urlencoded` |

##### Body

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `grant_type` | requis | string | `authorization_code` |
> | `client_id` | requis | string | `<CLIENT_ID>` Identifiant du FS, communiqué lors de son inscription auprès de AC |
> | `client_secret` | requis | string | `<CLIENT_SECRET>` Le secret du FS, communiqué lors de son inscription auprès de AC |
> | `redirect_uri` | requis | string |` <FS_URL>%2F<URL_CALLBACK>` Url de retour vers le FS (encodée), communiqué lors de l'appel au `Authorization Endpoint` |
> | `code` | requis | string | `<AUTHZ_CODE>` code d'autorisation fourni par AgentConnect après connexion |

##### Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/json;charset=utf-8`        | La réponse contenant l'access token |
> | `400`       | `application/json;charset=utf-8`        | JSON document décrivant l'origine de l'erreur de format |

##### Format de la réponse en succès

```
{
  'access_token': <ACCESS_TOKEN>,
  'token_type': 'Bearer',
  'expires_in': 60,
  'id_token': <ID_TOKEN>
}
```

Voir le format de l'[id_token](../doc_fs.md#id_token).

</details>

#### UserInfo Endpoint

<details>
 <summary><code>GET</code> <code><b>/api/v2/userinfo</b></code> </summary>

##### Description

Implémente le `UserInfo Endpoint` de Openid Connect:

https://openid.net/specs/openid-connect-core-1_0.html#UserInfo

##### Entête

> | nom | requis/optionnel | valeur |
> |----------------|--------|-------------------------------------|
> | `Authorization` | requis | `Bearer <ACCESS_TOKEN>` où `<ACCESS_TOKEN>` a été communiqué par le `Token Endpoint` |

##### Paramètres

> Aucun

##### Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/jwt`                   | JSON Web Token contenant les claims transmis par le FI  |
> | `400`       | `application/json;charset=utf-8`    | JSON document décrivant l'origine de l'erreur de format |

Voir le format de [userinfo](../doc_fs.md#userinfo).

</details>

#### Logout Endpoint

<details>
 <summary><code>GET</code> <code><b>/api/v2/session/end</b></code> </summary>

##### Description

Implémente le `Logout Endpoint` de Openid Connect:

http://openid.net/specs/openid-connect-session-1_0.html#RPLogout

:warning: Cet appel doit être réalisé via une redirection dans le navigateur de l'agent, afin d'expirer les cookies de session AgentConnect et FI.

##### Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `id_token_hint` | requis | string | `<ID_TOKEN>` contenu dans la réponse du `Token Endpoint` |
> | `state` | requis | string | `<STATE>` Champ obligatoire, généré aléatoirement par le FS, que AC renvoie tel quel dans la redirection qui suit la déconnexion, pour être ensuite vérifié par le FS. Il est utilisé afin d’empêcher l’exploitation de failles CSRF |
> | `post_logout_redirect_uri` | requis | string | `<POST_LOGOUT_REDIRECT_URI>` L'URL de redirection vers le FS après la déconnexion à AgentConnect |

##### Réponses

> | code http     | content-type                      |réponse                                                            |
> |---------------|-----------------------------------|-------------------------------------------------------------------|
> | `303`         | `text/html;charset=UTF-8`         | Redirection vers le FI pour déconnexion, puis [redirection vers le FS après déconnexion](#redirection-vers-le-fs-après-déconnexion) |

##### Exemple d'appel

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

#### Redirection vers le FS après déconnexion

<details>
 <summary><code>GET</code> <code><b>&lt;FS_URL&gt;/&lt;POST_LOGOUT_REDIRECT_URI&gt;</b></code> </summary>

##### Description

Redirection vers le FS après déconnexion.

AgentConnect renvoie le state communiqué par le FS lors de la demande de déconnexion.

##### Paramètres

> | nom | requis/optionnel | type de données | description |
> |--------|-----------|----------------|------------------------------------------------------|
> | `state` | requis | string (minimum 32 caractères) | `<STATE>` communiqué par par le FS dans l'appel au `Logout Endpoint`. Cette information est à vérifier par le FS, afin d’empêcher l’exploitation de failles CSRF | |

##### Exemple d'appel

Exemple de retour vers le FS de mock à déconnexion

> ```
> GET /logout-callback?state=3b7bd7fb38ccab89864563f17a89c4cb3bd400164ce828b4cfc2cb01ce8ed9da HTTP/1.1
> Host: fsa1v2.integ01.dev-agentconnect.fr
> ```

</details>
