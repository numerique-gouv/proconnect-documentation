# Qu'est ce que le protocole OpenID Connect?

Le protocole OpenID Connect est au cœur du fonctionnement d'AgentConnect. C'est une couche d'identification basée sur protocole OAuth 2.0. Il permet à des *Clients* d'accéder à l'identité des *Utilisateurs*  par l'intermédiaire d'un *Serveur d'Autorisation* .

La spécification du protocole se trouve sur http://openid.net/connect/.

Pour une référence d'implémentation OpenID Connect voici le lien : https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth

## Les flux standards

Le protocole OpenID Connect définit 3 appels REST faits par le client, et 4 endpoints (un du côté client, et trois du côté provider).

En amont, le client s'inscrit (en général manuellement) auprès du provider. Il lui fournit une URL de callback (l'URL du client vers lequel l'internaute est redirigé une fois authentifié), aussi appelée "callback endpoint". En retour le provider donne au client un client ID et un client secret.

Lorsque l'internaute clique sur le bouton d'authentification du client, le flux est le suivant :

Le client fait une redirection vers le "authorization endpoint" du provider avec son client id et son url de callback. Le provider redirige alors l'internaute vers sa mire d'authentification. Si l'internaute se loggue correctement, le provider renvoie un code d'autorisation au client.
Le client fait un appel Web service vers le "token endpoint" du provider avec le code d'autorisation reçu, et authentifie cette requête avec son client id et son client secret. Le provider retourne un access token (une chaîne de caractères encodée en base64), un id token (sous la forme d'un Json Web Token), et parfois un refresh token (une chaîne de caractères en base64).
Le client fait un appel Web service vers le "userInfo endpoint" du provider avec l'access token reçu, et le provider renvoie les informations de l'internaute au client.

## Qu'est ce que le protocole OAuth 2.0

OAuth 2.0 est un protocole destiné délégué les accès à des resources. Son objectif est de décrire comment l'accès à des ressources, des données, exposées par exemple sous la forme d'API sécurisé, peut être délégué à un client, une application ou un service en ligne, en ayant recueilli l'autorisation de l'utilisateur. 

Ce protocole fait intervenir quatre acteurs : 

* *Resource owner* : il s'agit de la personne qui est propriétaire des resources, le plus souvent c'est l'utilisateur; 
* *Resource server* : il s'agit du serveur qui héberge les resources du *Resource owner*; 
* *Client* : il s'agit de l'application ou du service qui souhaite accéder aux ressources
* *Authorization Server* : Il s'agit du serveur qui recueiller les autorisations des propriétaires des ressources et génère le jeton d'autorisation qui sont utilisé pour accéder aux ressources. 

Le serveur d'autorisation gère deux types de jetons : 
* *access token* : jeton qui permet de valider l'accès à un ressource. La durée de validité de ce jeton est limité et généralement de l'ordre de quelques minutes; 
* *refresh token* : jeton qui permet de renouveller l'autorisation sans la demander à nouveau au propriétaire de la ressource. Il permet de récupérer un nouvel *access token*. La durée de validité de ce jeton est généralement de plusieurs jours voir de plusieurs mois. Ce jeton doit être stocké de manière sécurisé par le client.

Les clients doivent être déclarés auprès du serveur d'autorisation. Les informations à fournir par le client sont : 
- le nom de l'application
- la liste des urls de redirections : il s'agit des urls vers lesquelles les utilisateurs vont être redirigé par le serveur d'autorisation, une fois l'autorisation accordé.
- les types d'autorisation qui pourront être utilisé par le client

Une fois déclarée, le serveur d'autorisation fourni au client un couple de client_id / client_secret qui permettra d'autthenfier le client auprès du serveur d'autorisation. 

Le diagramme de séquence représente de manière générale les intégrations dans une cinématique OAuth 2.0

<img src="../diagrams/diagram-sequence-oauth.png" alt="drawing" />

1. Le client demande un accès au ressource auprès du proriétaire des ressources ( *resource owner ) en précisant le périmètre de la demande à l'aide de scopes. Le client s'identifie à l'aide de son client_id et indique le type d'autorisation demandée. 

2. Si le propriétaire de la ressource accepte d'accorder l'accès à ces ressources, une autorisation d'accès est délivrer au client

3. Le client demande auprès du serveur d'autorisation un jeton d'accès ( *access token* ) en s'authentifiant et en fournissant l'autorisation d'accès reçu à l'étape précédente. 

4. Le serveur d'autorisation fourni un jeton d'accès après avoir authentifié le client et vérifier la validité de l'autorisation d'accès. 

5. Le client demande des ressources au serveur de ressources en fournissant l'access token fourni par le serveur d'autorisations.

6. Le serveur de ressources retournes les ressources demandés en ayant au préalable vérifié la validité de l'access token. 

OAuth 2.0 propose les types d'autorisations suivants: authorization code, implicit, resource owner credentials, client credentials.

Il faut noter que le protocole OAuth 2.O ne gère pas l'authentification de l'utilisateur. L'identité de l'utilisateur ne permet pas au client d'accéder au informations d'identités de l'utilisateur. Afin de rajouter ces informations, le protocole Openid Connect étant OAuth 2.0 pour intégrer l'accès aux informations d'identités de l'utilisateur. 

## Qu'apporte OpenId Connect à OAuth 2.0 ? 

Le protocole OpenId Connect s'appuie sur OAuth 2.0 en ajoutant des fonctionnalités supplémentaires : 

- La gestion d'information sur l'authentification,
- l'ajout d'un ID Token,
- la gestion d'un SSO et d'un déconnection,
- une API pour récupérer les informations sur l'utilisateur (/userinfo),
- un standard sur les informations sur l'utilisateur,
- un service de découverte des informations du serveur OpenID. 

### Quels sont les acteurs qui interviennent dans  OpenId Connect ?

OpenId Connect fait intervenir 3 acteurs : 

| Acteur OpenId Connect | Acteur similaire dans OAuth 2.0 |
| ------ | ------ |
| User |  Resource Owner |
| Relying Party | Client | 
| OpenID Provider | Authorization Server |

### Qu'est ce que l'ID Token ?

L'ID token est un jeton au format JWT qui est fourni en même temps que l'*access token*, il contient
- des information sur l'authtentification 
   - dates d'expiration, d'authentification, de création
   - des moyens de contrôle permettant de valider l'ID Token et l'Access Token
- des attributs ( claims ) sur l'utilisateurs, qui peuvent être : 
   - standard : profile, email, address, phone, ...
   - personnalisés par le serveur OpenId Connect. 


**Exemple d'ID Token :**

```json
{
  "sub": "4d327dd1e427daf4d50296ab71d6f3fc82ccc40742943521d42cb2bae4df41afv1",
  "amr": [ "fc" ],
  "auth_time": 1619605379,
  "acr": "eidas3",
  "nonce": "8c1696f884cac760436c9551ce34be81a3ab61171bf486dd31a58d2bc23a7bbd",
  "at_hash": "zc4hJ6cxMmrkb8KQn9UXbg",
  "aud": "6925fb8143c76eded44d32b40c0cb1006065f7f003de52712b78985704f39950",
  "exp": 1619605440,
  "iat": 1619605380,
  "iss": "https://corev2.docker.dev-franceconnect.fr/api/v2"
}
```

[Plus d'information sur l'ID Token](https://openid.net/developers/specs/)

### Quels sont les endpoints d'OpenId Connect ? 

Le protocole OpenID Connect propose les endpoints suivants : 

- **authorization** : permet de demander une authentification de l'utilisateur
- **token** : permet de demander un tocket ( *access token*, *refresh token*, *id token* )
- **userinfo** : permet de récupérer les informations sur l'utilisateur
- **revocation** : permet de révoquer un token  (*access token*, *refresh token*)
- **introspection** : permet de valider un jeton (*access token*, *refresh token*)
- **discovery** : permet de récupérer des informations sur le serveur OpenId Connect

### Comment récupérer les tokens ? 

OpenId proposte 3 types de flow qui permettent de récupérer des tokens : 

- **Authorization code flow** : l'appel au endpoint *authorization* permet de récupérer un code d'autorisation qui est utilisé pour récupérer les tokens. 
- **Implicit flow** : l'appel au endpoint *authorization* permet de récupérer directement les tokens, le refresh token ne peut pas être récupéré.
- **Hybrid flow** : Il s'agit d'un mix entre les deux. 

---

Voir aussi : 
- [Comment AgentConnect utilise OpenID Connect?](../technique_fca/technique_fca_oidc.md)
- [Quelles sont les données que je peux récupérer par AgentConnect sur mes usagers?](../projet_fca/projet_fca_donnees.md)
- [Quel est le détail du fonctionnement?](../fonctionnement_fca/details_fonctionnement.md)
- [Quelles sont les données que je peux récupérer par AgentConnect sur mes usagers?](../projet_fca/projet_fca_donnees.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs? ](../technique_fca/technique_fca_scope.md)
- [Quelles sont les données d'AgentConnect qui expirent?](../technique_fca/donnees_expirent.md)
- [Qu'est ce qu'eIDAS et quel est le niveau de garantie d'AgentConnect?](../projet_fca/projet_fca_niveau_eidas.md)