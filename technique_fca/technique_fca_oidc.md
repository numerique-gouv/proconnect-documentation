
# Comment AgentConnect utilise le protocole OpenId Connect? 

AgentConnect met en oeuvre le protocole OpenID Connect pour permettre à un Fournisseur de Services de déléguer à AgentConnect l'identificiation et l'authentification des usagers, ainsi que la gestion des consentements qui sont nécessaire à la transmission des données personnelles des utilisateurs auprès du Fournisseur de Services.  

## Les acteurs

Pour rappel, le protocole OpenID Connect défini les acteurs suivants : *User*, *Relying Party* et *OpenID Provider*. 

OpenId Connect fait intervenir 3 acteurs : 

| Acteur OpenId Connect | Acteur dans le contexte AgentConnect |
| ------ | ------ |
| User |  Usager du Fournisseur de Services |
| Relying Party | Fournisseur de Services | 
| OpenID Provider | AgentConnect |

## Flow OpenID Connect

Le protocole OpenID Connect propose différents *flow* permettant de récupérer des tokens. AgentConnect n'implémente que [Authorization code flow](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth).

Les Fournisseurs de Services doivent être service provider OpenID Connect, et les Fournisseurs d'Identité doivent être identity provider OpenID Connect. AgentConnect est une brique intermédiaire qui est à la fois identity provider (du point de vue des Fournisseurs de Services) et service provider (du point de vue des Fournisseurs d'Identité).

## Discovery Mode

Le protocole OpenId Connect permet à *l'Identity Provider* d'exposer à *Relying Party* de récupérer dynamiquement ses données de configuration (*meta-data*). 

[Plus d'information sur OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html)

AgentConnect expose ses méta-data via les discovery url suivante : 

| Environnement | Adresse |
| ------ | ------ |
| Integration | https://fca.integ01.dev-agentconnect.fr/api/v2/.well-known/openid-configuration | 
| Production | https://auth.agentconnect.gouv.fr/api/v2/.well-known/openid-configuration |

## Signature et chiffrement des jetons

Dans le cadre du niveau **Standard** , tous les échanges de jetons JWT entre le Fournisseur d'Identité et AgentConnect sont signés. 
Le chiffrement des jetons n'est actuellement pas activé. 

Les algorithmes suivants sont gérés par AgentConnect Standard : 

#### Signature de jetons par AgentConnect:

- Asymétrique : 

       - ES256 (EC + SHA256)
       - RS256 (RSA + SHA256)

- Symétrique : géré mais non recommandé

       - HS256 (HMAC + SHA256) 

**:warning: ATTENTION Ces algorithmes sont valides pour les endpoints exposant des JWT (/token et /userinfo).**

Les spécifications des algorithmes de signatures et de chiffrements utilisés sont les suivantes :

* [JWA - https://tools.ietf.org/html/rfc7518](https://tools.ietf.org/html/rfc7518)
* [JWS - https://tools.ietf.org/html/rfc7515#appendix-A.3](https://tools.ietf.org/html/rfc7515#appendix-A.3)
* [JWE - https://tools.ietf.org/html/rfc7516#appendix-A.1](https://tools.ietf.org/html/rfc7516#appendix-A.1)


#### Exposition des clés de signature

Les clés publiques de signatures de AgentConnect sont disponibles via la *JWKS URL* présente dans les méta-data de la *Discovery URL* aux adresses suivantes et sont changées régulièrement :

*Environnement Internet* : 

| Environnement | adresses du endpoint |
|---------------|----------------------|
| intégration AgentConnect | https://fca.integ01.dev-agentconnect.fr/api/v2/jwks |
| production AgentConnect |https://auth.agentconnect.gouv.fr/api/v2/jwks|

*Environnement RIE* :

| Environnement | adresses du endpoint |
|---------------|----------------------|
| intégration AgentConnect | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/jwks|
| production AgentConnect |https://auth.agentconnect.rie.gouv.fr/api/v2/jwks|


#### Exposition des clés de chiffrement

Les clés publiques de chiffrement du Fournisseur de Services doivent être exposées à AgentConnect par le Fournisseur de Services sous la forme d'une *URL* au format JWK. 

[Plus d'information sur le JWK](https://datatracker.ietf.org/doc/html/rfc7517)

---

Voir aussi : 
- [Qu'est ce que le protocole OpenID Connect?](technique_fca/technique_oidc.md)
- [Comment accéder aux différents environnements d'AgentConnect?](technique_fca/technique_fca_env.md)

