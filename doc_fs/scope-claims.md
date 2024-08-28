
# Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs ? 

## Scope et Claims dans OpenID Connect

### Qu'est ce qu'un scope dans OpenID Connect ? 

> Les clients OpenID Connect utilisent des *scopes* tels que définis dans la section 3.3 de [OAuth 2.0 [RFC6749]](https://openid.net/specs/openid-connect-basic-1_0.html#RFC6749) pour spécifier quels privilèges d'accès sont demandés pour les *access token*. Les *scopes* associées aux *access token* déterminent les ressources qui seront disponibles lorsqu'elles sont utilisées pour accéder aux *endpoints* protégés par OAuth 2.0. Pour OpenID Connect, les *scopes* peuvent être utilisées pour demander que des ensembles d'informations spécifiques soient mis à disposition en tant que *claims*.

*Source: [OpenID Connect Basic Client Implementer's Guide 1.0](https://openid.net/specs/openid-connect-basic-1_0.html#Scopes)*

Le protocole OpenID Connect défini un certain nombre de [scopes standards](https://openid.net/specs/openid-connect-basic-1_0.html#Scopes) qu'il est possible d'étendre avec des *scopes* spécifiques supplémentaires en fonction du besoin de l'*identity provider*.

*En bref :* Les scopes permettent de définir l'ensemble des informations à disposition du Fournisseur de Services pour une cinématique. 

### Qu'est ce qu'un claim dans OpenID Connect ? 

Dans OpenId Connect, un claim est une information relative à l'utilisateur ou à la phase l'authentification. Ces informations peuvent être disponibles soit dans l'ID Token, soit dans la réponse du UserInfo. Les claims retournés dans ces jetons dépendent des scopes associés à l'*access token*. 

Le protocole OpenId Connect defini un certain nombre de [claims standards](https://openid.net/specs/openid-connect-core-1_0.html#Claims).

*En Bref :* Les claims sont les informations sur l'utilisateur ou la phase d'authentification disponible dans l'ID Token ou dans la réponse de UserInfo. 

La liste des données renvoyées par les Fournisseurs d'Identité est disponible [ici](./donnees_fournies.md)

### Les données sur l'authentification

Les claims relatifs à l'authentification disponibles par AgentConnect sont des claims standards et sont disponibles uniquement dans l'ID Token. Ces claims sont les suivants : 

- amr
- acr
- sid
- auth_time
- iss

[Plus d'informations sur ces claims](https://openid.net/specs/openid-connect-basic-1_0.html#IDToken)

### Correspondance entre scope et claims sur AgentConnect

Le tableau suivant décrit la liste des *claims* accessible en fonction des *scopes* associés à l'access token. 
Tous les Fournisseurs de Service intégrés depuis août 2024 ont accès par défaut à tous les scopes suivants:

| Scope       | Claims   |
| --- | --- |
| openid | sub |
| given_name | given_name|
| usual_name| usual_name |
| email | email |
| uid | uid|
| siret | siret |
| idp_id | idp_id|

Le claim "phone_number" existe également pour le scope phone.

| Scope       | Claims   |
| --- | --- |
| phone | phone_number |
