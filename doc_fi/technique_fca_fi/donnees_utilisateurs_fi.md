# Quelles sont les données utilisateur que je dois fournir ?

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

## Les données obligatoires

En plus de l'openid, qui est obligatoire, des données obligatoires sont fournies par les Fournisseurs d'Identité aux Fournisseurs de Service, via AgentConnect. Ces données permettent d'identifier un utilisateur.

Les données obligatoires sont des informations qui doivent être renvoyées systématiquement si elles sont demandées par AgentConnect.
                                                    
| Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
|given_name | Oui |Prénoms séparés par des espaces (standard OpenIDConnect)| UTF-8 (standard OpenIDConnect)|
|usual_name| Oui |Nom de famille d'usage (par défaut = family_name)| UTF-8 |
|email | Oui |Adresse courriel |UTF-8 (standard OpenIDConnect)|
|uid|Oui |Identifiant unique de l'agent auprès du FI| String (standard OpenIDConnect)|

En complément, il est possible d'obtenir des données complémentaires. Cependant ces données ne sont pas obligatoirement connues par tous les Fournisseurs d'Identité.

## Les données complémentaires

Les données complémentaires sont des informations qui sont renvoyées uniquement si celles-ci sont disponibles chez le Fournisseur d'Identité.

| Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
| siren | non  | Identifiant d'entreprise  | String, 9 chiffres sans espace |
| siret | non |Identifiant d'établissement| string, 14 chiffres sans espace|
| organizational_unit  | non  | Ministère/Direction/Service d'affectation   | UTF8 |
| belonging_population  | non  | Population d'appartenance  | string, Exemple: agent, prestataire, partenaire, stagiaire |
| phone  | non  | Téléphones de contact  | Format non normé |
| chorusdt   | Non | Entité ministérielle/Matricule Agent  | string |


La liste des données complémentaires est non exhaustive et pourra être amendée si besoin.

### Les données sur l'authentification

Les claims relatifs à l'authentification disponibles par AgentConnect sont des claims standards et sont disponibles uniquement dans l'ID Token. Ces claims sont les suivants : 

- amr
- acr
- sid
- auth_time
- iss

[Plus d'informations sur ces claims](https://openid.net/specs/openid-connect-basic-1_0.html#IDToken)

### Correspondance entre scope et claims sur AgentConnect

Le tableau suivant décris la liste des *claims* accessible en fonction des *scopes* associés à l'access token.

| Scope       | Claims   |
| --- | --- |
| openid | sub |
| given_name | given_name|
| usual_name| usual_name |
| email | email |
| uid | uid|
| siren | siren |
| siret | siret |
| organizational_unit | organizational_unit |
| belonging_population | belonging_population |
| phone | phone_number |
| chorusdt | chorusdt:matricule, chorusdt:societe |
| idp_id | idp_id|
| idp_acr | idp_acr|
---



