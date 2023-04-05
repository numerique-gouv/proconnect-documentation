# Comment AgentConnect utilise le protocole OpenId Connect ? 

Le protocole OpenID Connect est au coeur du fonctionnement d'AgentConnect. C'est une surcouche d'identification au protocole OAuth 2.0. Il permet à des Clients (ici, les Fournisseurs de Services) d'accéder à l'identité des utilisateurs finaux (les internautes) par l'intermédiaire d'un serveur d'autorisation (ici, les Fournisseurs d'Identité).

## Dans le cadre d'AgentConnect 

AgentConnect implémente le flux [Authorization Code Flow](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth) d'OpenID Connect. 

Les Fournisseurs de Services doivent être clients OpenID Connect, et les fournisseurs d'identité doivent être fournisseurs OpenID Connect. AgentConnect est une brique intermédiaire qui est à la fois fournisseur (du point de vue des Fournisseurs de Services) et client (du point de vue des Fournisseurs d'Identité).

## Signature des échanges

Dans le cadre du niveau **Standard** , tous les échanges de jetons JWT entre le Fournisseurs d'Identité et AgentConnect sont signés. 

les algorithmes suivants sont gérés par AgentConnect Standard : 

**Signature de jetons par le FI** :

- Asymétrique : 

       - ES256 (EC + SHA256)
       - RS256 (RSA + SHA256)

- Symétrique : géré mais non recommandé

       - HS256 (HMAC + SHA256) 

**:warning: Ces algorithmes sont valides pour les endpoints exposant des JWT (/token et /userinfo).**

Les spécifications des algorithmes de signatures utilisés sont les suivants : 
* [JWA - https://tools.ietf.org/html/rfc7518](https://tools.ietf.org/html/rfc7518)
* [JWS - https://tools.ietf.org/html/rfc7515#appendix-A.3](https://tools.ietf.org/html/rfc7515#appendix-A.3)
* [JWE - https://tools.ietf.org/html/rfc7516#appendix-A.1](https://tools.ietf.org/html/rfc7516#appendix-A.1)
 
Les clés de signatures utilisés par le Fournisseur d'Identité doivent être disponible via la *JWKS URL* présente dans les méta-data de la *Discovery URL*. 


