# Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs ?

## Scope et Claims dans OpenID Connect

### Qu'est ce qu'un scope dans OpenID Connect ?

> Les clients OpenID Connect utilisent des _scopes_ tels que définis dans la section 3.3 de [OAuth 2.0 [RFC6749]](https://openid.net/specs/openid-connect-basic-1_0.html#RFC6749) pour spécifier quels privilèges d'accès sont demandés pour les _access token_. Les _scopes_ associées aux _access token_ déterminent les ressources qui seront disponibles lorsqu'elles sont utilisées pour accéder aux _endpoints_ protégés par OAuth 2.0. Pour OpenID Connect, les _scopes_ peuvent être utilisées pour demander que des ensembles d'informations spécifiques soient mis à disposition en tant que _claims_.

_Source: [OpenID Connect Basic Client Implementer's Guide 1.0](https://openid.net/specs/openid-connect-basic-1_0.html#Scopes)_

Le protocole OpenID Connect défini un certain nombre de [scopes standards](https://openid.net/specs/openid-connect-basic-1_0.html#Scopes) qu'il est possible d'étendre avec des _scopes_ spécifiques supplémentaires en fonction du besoin de l'_identity provider_.

_En bref :_ Les scopes permettent de définir l'ensemble des informations à disposition du Fournisseur de Services pour une cinématique.

### Qu'est ce qu'un claim dans OpenID Connect ?

Dans OpenId Connect, un claim est une information relative à l'utilisateur ou à la phase l'authentification. Ces informations peuvent être disponibles soit dans l'ID Token, soit dans la réponse du UserInfo. Les claims retournés dans ces jetons dépendent des scopes associés à l'_access token_.

Le protocole OpenId Connect defini un certain nombre de [claims standards](https://openid.net/specs/openid-connect-core-1_0.html#Claims).

_En Bref :_ Les claims sont les informations sur l'utilisateur ou la phase d'authentification disponible dans l'ID Token ou dans la réponse de UserInfo.

La liste des données renvoyées par les Fournisseurs d'Identité est disponible [ici](./donnees_fournies.md)

### Les données sur l'authentification

Les claims relatifs à l'authentification disponibles par ProConnect sont des claims standards et sont disponibles uniquement dans l'ID Token. Ces claims sont les suivants :

- amr
- acr
- sid
- auth_time
- iss

[Plus d'informations sur ces claims](https://openid.net/specs/openid-connect-basic-1_0.html#IDToken)

### Correspondance entre scope et claims sur ProConnect

Le tableau suivant décrit la liste des _claims_ accessible en fonction des _scopes_ associés à l'access token.
Tous les Fournisseurs de Service intégrés depuis août 2024 ont accès par défaut à tous les scopes suivants:

| Scope      | Claims     |
| ---------- | ---------- |
| openid     | sub        |
| given_name | given_name |
| usual_name | usual_name |
| email      | email      |
| uid        | uid        |
| siret      | siret      |
| idp_id     | idp_id     |

#### Le scope "phone"

Le claim "phone_number" existe également pour le scope phone.

| Scope | Claims       |
| ----- | ------------ |
| phone | phone_number |

#### Le scope "custom"

| Scope  | Claims |
| ------ | ------ |
| custom | custom |

Les Fournisseurs de Service qui le souhaitent peuvent appeler le scope optionnel "custom". Pour plus d'informations, lire l'[article dédié](./custom-scope.md).
