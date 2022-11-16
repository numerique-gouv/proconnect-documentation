# AgentConnect Endpoints

AgentConnect met en oeuvre le protocole OpenID Connect pour permettre à un Fournisseur de Services de déléguer à AgentConnect l'identificiation et l'authentification des usagers.

#### Openid Configuration Endpoints

<details>
 <summary><code>GET</code> <code><b>/api/v2/.well-known/openid-configuration</b></code> </summary>

##### Description

Implémente la requête de `Provider Configuration`
https://openid.net/specs/openid-connect-discovery-1_0.html#ProviderConfigurationRequest

##### Paramètres

> Aucun

##### Responses

> | http code     | content-type                      |response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/json;charset=utf-8`        | Document JSON décrivant la configuration d'AgentConnect |

##### Example d'appel

> ```
> GET /api/v2/.well-known/openid-configuration HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> ```

</details>

<details>
 <summary><code>GET</code> <code><b>/api/v2/jwks</b></code> </summary>

##### Description

Liste les clés de signatures utilisés par AgentConnect

##### Paramètres

> Aucun

> | http code     | content-type                      |response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/json;charset=utf-8`        | Document JSON décrivant les clés de signature d'AgentConnect |

##### Example d'appel

> ```
> GET /api/v2/jwks HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> ```

</details>

#### Authorization Endpoint

<details>
 <summary><code>GET</code> <code><b>/api/v2/authorize</b></code> </summary>

##### Description

Implémente le `Authorization Endpoint` de Openid Connect: https://openid.net/specs/openid-connect-core-1_0.html#AuthorizationEndpoint

##### Paramètres

> | nom | requis/optionnel | type de données | descriptif |
> |--------|-----------|----------------|------------------------------------------------------|
> | `response_type` | requis | string | `code` |
> | `client_id` | requis | string | `<CLIENT_ID>` Identifiant du FS, communiqué lors de son inscription auprès de AC |
> | `redirect_uri` | requis | string |` <FS_URL>%2F<URL_CALLBACK>` Url de retour vers le FS (encodée), communiqué lors de son inscription auprès de AC |
> | `acr_values` | requis | string | `eidas1` AgentConnect ne garantie qu'un niveau faible |
> | `scope` | requis | string | `<SCOPES>` Liste des scopes demandés séparés par des espaces (%20 au format unicode dans l'URL) ou des '+' |
> | `claims` | optionnel | string | `<CLAIMS>` Objet JSON encodé décrivant les claims demandés |
> | `state` | requis | string (minimum 32 caractères) | `<STATE>` Champ obligatoire, généré aléatoirement par le FS, que AC renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par le FS. Il est utilisé afin d’empêcher l’exploitation de failles CSRF |
> | `nonce` | requis | string (minimum 32 caractères) | `<NONCE>` Champ obligatoire, généré aléatoirement par le FS que FC renvoie tel quel dans la réponse à l'appel à /token, pour être ensuite vérifié par le FS. Il est utilisé pour empêcher les attaques par rejeu |
> | `prompt` | optionnel | string | `login` si le FS veut forcer la reauthentification au FI. Par défaut, le FI réutilisera une session existante sans demander une reconnexion. |

##### Responses

> | http code     | content-type                      |response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `303` (succès)        | `text/html;charset=UTF-8`        | Redirection vers `/api/v2/interaction/{interactionHash}` où {interactionHash} est un hash lié à la session de l'usager |
> | `303` (erreur) | `text/html;charset=UTF-8`        | Redirection vers `{redirect_uri}?error=<ERROR_CODE>&error_description=<ERROR_DESCRIPTION>&state=<STATE>`<br>où `<ERROR_CODE>` est le code d'erreur,<br>`<ERROR_DESCRIPTION>` est la description de l'erreur,<br>`<STATE>` est le state fourni à l'appel `/api/v2/authorize` |
> | `400` (mauvais format)| `text/html;charset=UTF-8`        | La page d'erreur avec code `Y000400` est affichée en cas de mauvais format |

##### Example d'appel

> ```
> GET /api/v2/authorize?scope=openid+uid+given_name+usual_name+email+siren+siret+organizational_unit+belonging_population+phone+chorusdt+idp_id+idp_acr&acr_values=eidas1&claims=%7B%22id_token%22%3A%7B%22amr%22%3A%7B%22essential%22%3Atrue%7D%7D%7D&client_id=6925fb8143c76eded44d32b40c0cb1006065f7f003de52712b78985704f39950&redirect_uri=https%3A%2F%2Ffsa1v2.integ01.dev-agentconnect.fr%2Foidc-callback&prompt=login&response_type=code&state=9ed67ae42fdc5d0a6867a5425a284745f4f73ce8b6edf76e453487aa1b73cc89&nonce=7db9b35458f2288bade947791f1c8fa2d02954f8eb7d9909dc68784f7c4aea29 HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> ```

</details>

<details>
 <summary><code>POST</code> <code><b>/api/v2/authorize</b></code> </summary>

##### Description

Implémente le `Authorization Endpoint` de Openid Connect: https://openid.net/specs/openid-connect-core-1_0.html#AuthorizationEndpoint

##### Entête

> | nom | requis/optionnel | valeur |
> |----------------|--------|-------------------------------------|
> | `Content-Type` | requis | `application/x-www-form-urlencoded` |

##### Body

> | nom | requis/optionnel | type de données | descriptif |
> |--------|-----------|----------------|------------------------------------------------------|
> | `response_type` | requis | string | `code` |
> | `client_id` | requis | string | `<CLIENT_ID>` Identifiant du FS, communiqué lors de son inscription auprès de AC |
> | `redirect_uri` | requis | string |` <FS_URL>%2F<URL_CALLBACK>` Url de retour vers le FS (encodée), communiqué lors de son inscription auprès de AC |
> | `acr_values` | requis | string | `eidas1` AgentConnect ne garantie qu'un niveau faible |
> | `scope` | requis | string | `<SCOPES>` Liste des scopes demandés séparés par des espaces (%20 au format unicode dans l'URL) ou des '+' |
> | `claims` | optionnel | string | `<CLAIMS>` Objet JSON encodé décrivant les claims demandés |
> | `state` | requis | string (minimum 32 caractères) | `<STATE>` Champ obligatoire, généré aléatoirement par le FS, que AC renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par le FS. Il est utilisé afin d’empêcher l’exploitation de failles CSRF |
> | `nonce` | requis | string (minimum 32 caractères) | `<NONCE>` Champ obligatoire, généré aléatoirement par le FS que FC renvoie tel quel dans la réponse à l'appel à /token, pour être ensuite vérifié par le FS. Il est utilisé pour empêcher les attaques par rejeu |
> | `prompt` | optionnel | string | `login` si le FS veut forcer la reauthentification au FI. Par défaut, le FI réutilisera une session existante sans demander une reconnexion. |

##### Responses

> | http code     | content-type                      |response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `303` (succès)        | `text/html;charset=UTF-8`        | Redirection vers `/api/v2/interaction/{interactionHash}` où {interactionHash} est un hash lié à la session de l'usager |
> | `303` (autre erreur) | `text/html;charset=UTF-8`        | Redirection vers `{redirect_uri}?error=<ERROR_CODE>&error_description=<ERROR_DESCRIPTION>&state=<STATE>`<br>où `<ERROR_CODE>` est le code d'erreur,<br>`<ERROR_DESCRIPTION>` est la description de l'erreur,<br>`<STATE>` est le state fourni à l'appel `/api/v2/authorize` |
> | `400` (mauvais format)| `text/html;charset=UTF-8`        | La page d'erreur avec code `Y000400` est affichée en cas de mauvais format |

##### Example d'appel

> ```
> POST /api/v2/authorize HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> Content-Type: application/x-www-form-urlencoded
>
> scope=openid+uid+given_name+usual_name+email+siren+siret+organizational_unit+belonging_population+phone+chorusdt+idp_id+idp_acr&acr_values=eidas1&claims=%7B%22id_token%22%3A%7B%22amr%22%3A%7B%22essential%22%3Atrue%7D%7D%7D&client_id=6925fb8143c76eded44d32b40c0cb1006065f7f003de52712b78985704f39950&redirect_uri=https%3A%2F%2Ffsa1v2.integ01.dev-agentconnect.fr%2Foidc-callback&prompt=login&response_type=code&state=9ed67ae42fdc5d0a6867a5425a284745f4f73ce8b6edf76e453487aa1b73cc89&nonce=7db9b35458f2288bade947791f1c8fa2d02954f8eb7d9909dc68784f7c4aea29
> ```

</details>

#### Token Endpoint

<details>
 <summary><code>POST</code> <code><b>/api/v2/token</b></code> </summary>

##### Description

Implémente le `Token Endpoint` de Openid Connect: https://openid.net/specs/openid-connect-core-1_0.html#TokenEndpoint

##### Entête

> | nom | requis/optionnel | valeur |
> |----------------|--------|-------------------------------------|
> | `Content-Type` | requis | `application/x-www-form-urlencoded` |

##### Body

> | nom | requis/optionnel | type de données | descriptif |
> |--------|-----------|----------------|------------------------------------------------------|
> | `grant_type` | requis | string | `authorization_code` |
> | `client_id` | requis | string | `<CLIENT_ID>` Identifiant du FS, communiqué lors de son inscription auprès de AC |
> | `client_secret` | requis | string | `<CLIENT_SECRET>` Le secret du FS, communiqué lors de son inscription auprès de AC |
> | `redirect_uri` | requis | string |` <FS_URL>%2F<URL_CALLBACK>` Url de retour vers le FS (encodée), communiqué lors de l'appel à `/api/v2/authorize` |
> | `code` | requis | string | `<AUTHZ_CODE>` Authorization code provided by AC when returning to the FS |

##### Responses

> | http code     | content-type                      |response                                                            |
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
</details>

#### UserInfo Endpoint

<details>
 <summary><code>GET</code> <code><b>/api/v2/userinfo</b></code> </summary>

##### Description

Implémente le `Token Endpoint` de Openid Connect: https://openid.net/specs/openid-connect-core-1_0.html#TokenEndpoint

##### Entête

> | nom | requis/optionnel | valeur |
> |----------------|--------|-------------------------------------|
> | `Authorization` | requis | `Bearer <ACCESS_TOKEN>` où `ACCESS_TOKEN` a été communiqué par `/api/v2/token` |

##### Paramètres

> Aucun

##### Responses

> | http code     | content-type                      |response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`       | `application/json;charset=utf-8`        | La réponse contenant les claims transmis par le FI |
> | `400`       | `application/json;charset=utf-8`        | JSON document décrivant l'origine de l'erreur de format |

</details>

#### Logout Endpoint

<details>
 <summary><code>GET</code> <code><b>/api/v2/session/end</b></code> </summary>

##### Description

Implémente le `Logout Endpoint` de Openid Connect: http://openid.net/specs/openid-connect-session-1_0.html#RPLogout

##### Paramètres

> | nom | requis/optionnel | type de données | descriptif |
> |--------|-----------|----------------|------------------------------------------------------|
> | `id_token_hint` | requis | string | `<ID_TOKEN>` fourni lors de l'appel à `/api/v2/token` |
> | `state` | requis | string | `<STATE>` state à communiquer au FS lors du retour post déconnexion. Le FS doit vérifier qu'il correspond au state généré pour la déconnexion. |
> | `post_logout_redirect_uri` | requis | string | `<POST_LOGOUT_REDIRECT_URI>` L'URL de redirection après la demande de déconnexion AC |

##### Responses

> | http code     | content-type                      |response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `303`       | `text/html;charset=UTF-8`        | La réponse contenant les claims transmis par le FI |
> | `400`       | `application/json;charset=utf-8`        | JSON document décrivant l'origine de l'erreur de format |


##### Example d'appel

> ```
> GET /api/v2/session/end?id_token_hint=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI3MDRlMDI0MjI5MDE1ZDJiZDQ3ZjdhNWU1YWIwNWIzNWM4MzM2YWI0MDNjMzgwMjI5ODVmOGNmYWRjODZmZTkxIiwiYW1yIjpbInB3ZCJdLCJhdXRoX3RpbWUiOjE2Njg1MzAzMjYsImFjciI6ImVpZGFzMSIsIm5vbmNlIjoiYWZjODFmZGExZmJiNmQzYzg3NmFmNzVjNzM3YTEzMDdhMWIyOWJhMDg3M2VmYTA1OWU0NTM1ZDEyMmM5ZGI1YSIsImF0X2hhc2giOiJJVEJTV1J2NW1HRmxxTGQ0Sm5nbnRnIiwiYXVkIjoiNjkyNWZiODE0M2M3NmVkZWQ0NGQzMmI0MGMwY2IxMDA2MDY1ZjdmMDAzZGU1MjcxMmI3ODk4NTcwNGYzOTk1MCIsImV4cCI6MTY2ODUzMDM4NiwiaWF0IjoxNjY4NTMwMzI2LCJpc3MiOiJodHRwczovL2ZjYS5pbnRlZzAxLmRldi1hZ2VudGNvbm5lY3QuZnIvYXBpL3YyIn0.hg1n4WJbzZECwz4VldAybXYreEXJ4fxpSWqDs9V4tTk&post_logout_redirect_uri=https%3A%2F%2Ffsa1v2.integ01.dev-agentconnect.fr%2Flogout-callback&state=188d025fb53ca637c2b8002fa6085caac0dea6a9c3c91ede7a0bb69cc330d3c7 HTTP/1.1
> Host: fca.integ01.dev-agentconnect.fr
> ```

</details>