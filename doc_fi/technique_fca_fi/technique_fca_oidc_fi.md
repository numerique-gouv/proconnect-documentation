# Comment AgentConnect utilise le protocole OpenId Connect ? 

Le protocole OpenID Connect est au coeur du fonctionnement d'AgentConnect. C'est une surcouche d'identification au protocole OAuth 2.0. Il permet à des Clients (ici, les Fournisseurs de Services) d'accéder à l'identité des utilisateurs finaux (les internautes) par l'intermédiaire d'un serveur d'autorisation (ici, les Fournisseurs d'Identité).


## Dans le cadre d'AgentConnect 

AgentConnect implémente le flux [Authorization Code Flow](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth) d'OpenID Connect. 

Les Fournisseurs de Services doivent être clients OpenID Connect, et les fournisseurs d'identité doivent être fournisseurs OpenID Connect. AgentConnect est une brique intermédiaire qui est à la fois fournisseur (du point de vue des Fournisseurs de Services) et client (du point de vue des Fournisseurs d'Identité).

## Chiffrement et signature des échanges

Dans le cadre du niveau **Standard** , tous les échanges de jetons JWT entre le FI et AC sont signés. 
Le chiffrement des jetons est recommandé mais non obligatoire. 

les algorithmes suivants sont gérés par AgentConnect Standard : 

**Signature de jetons par le FI** :

- Asymétrique : 

       - ES256 (EC + SHA256)
       - RS256 (RSA + SHA256)

- Symétrique : géré mais non recommandé

       - HS256 (HMAC + SHA256) 

**Chiffrement des jetons (jwe+jws)** :

- Hybride :

      - RSA-OEAP + AES256-GCM 
      - ECDH-ES + AES256-GCM

**:warning: Ces algorithmes sont valides pour les endpoints exposant des JWT (/token et /userinfo).**

Les spécifications des algorithmes de signatures et de chiffrements utilisés sont les suivants : 
* [JWA - https://tools.ietf.org/html/rfc7518](https://tools.ietf.org/html/rfc7518)
* [JWS - https://tools.ietf.org/html/rfc7515#appendix-A.3](https://tools.ietf.org/html/rfc7515#appendix-A.3)
* [JWE - https://tools.ietf.org/html/rfc7516#appendix-A.1](https://tools.ietf.org/html/rfc7516#appendix-A.1)

Les clés publiques de chiffrement d'AgentConnect sont disponibles à ces adresses et seront changées régulièrement 

### Environnement Internet : 


| Environnement | adresses du endpoint |
| ------ | ------ |
| intégration AC | https://fca.integ01.dev-agentconnect.fr/api/v2/client/.well-known/keys |
| production AC | Envoi de l'URL de prod par mail|  


**Démonstrateurs Internet**

*FI Internet* :

https://fia1v2.integ01.dev-agentconnect.fr

https://fia2v2.integ01.dev-agentconnect.fr

*FS Internet* :

https://fsa1v2.integ01.dev-agentconnect.fr

https://fsa2v2.integ01.dev-agentconnect.fr

https://fsa3v2.integ01.dev-agentconnect.fr



### Environnement RIE : 

| EndPoint | Adresse |
| ------ | ------ |
| intégration AC | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/client/.well-known/keys |
| production AC | Envoi de l'URL de prod par mail |  


**Démonstrateurs RIE**

*FI RIE* :

https://fia1v2.integ02.agentconnect.rie.gouv.fr

https://fia2v2.integ02.agentconnect.rie.gouv.fr

*FS RIE* :

https://fsa1v2.integ02.agentconnect.rie.gouv.fr

https://fsa2v2.integ02.agentconnect.rie.gouv.fr

https://fsa3v2.integ02.agentconnect.rie.gouv.fr


les clés de signatures utilisés par le Fournisseur d'Identité doivent être disponible via la *JWKS URL* présente dans les méta-data de la *Discovery URL*. 

---

Voir aussi : 


