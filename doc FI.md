| Version | Résumé des modifications | Modifié par | Date |
| ------ | ------ | ------ | ------ |
| v1 | Rédaction de la documentation FI | Khadija BOURHALEB | 08/12/2020 |



Cette documentation est à destination des fournisseurs d'identités des plateformes AgentConnect 

[[_TOC_]]

# Concepts de base

## Le protocole OpenID Connect

### Introduction

Le protocole OpenID Connect est au coeur du fonctionnement d'AgentConnect. C'est une surcouche d'identification au protocole OAuth 2.0. Il permet à des Clients (ici, les FS) d'accéder à l'identité des Utilisateurs finaux (les internautes) par l'intermédiaire d'un serveur d'autorisation (ici, les FIs).

Les FS doivent donc être des clients OpenID Connect (aussi appelés relying parties), et les FIs doivent être des fournisseurs OpenID Connect (aussi appelés providers).

La spécification du protocole se trouve sur http://openid.net/connect/.

Pour une référence d'implémentation OpenID Connect voici le lien : https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth

### Les flux standards

Le protocole OpenID Connect définit 3 appels REST faits par le client, et 4 endpoints (un du côté client, et trois du côté provider).

En amont, le client s'inscrit (en général manuellement) auprès du provider. Il lui fournit une URL de callback (l'URL du client vers lequel l'internaute est redirigé une fois authentifié), aussi appelée "callback endpoint". En retour le provider donne au client un client ID et un client secret.

Lorsque l'utilisateur clique sur le bouton d'authentification du client, le flux est le suivant :

Le client fait une redirection vers le "authorization endpoint" du provider avec son client id et son url de callback. Le provider redirige alors l'internaute vers sa mire d'authentification. 

Si l'internaute se loggue correctement, le provider renvoie un code d'autorisation au client.

Le client fait un appel Web service vers le "token endpoint" du provider avec le code d'autorisation reçu, et authentifie cette requête avec son client id et son client secret. 

Le provider retourne un access token (une chaîne de caractères encodée en base64), un id token (sous la forme d'un Json Web Token, voir https://developer.atlassian.com/cloud/jira/service-desk/understanding-jwt/), et parfois un refresh token (une chaîne de caractères en base64).

Le client fait un appel Web service vers le "userInfo endpoint" du provider avec l'access token reçu, et le provider renvoie les informations de l'internaute au client.

### Dans le cadre d'AgentConnect 

AgentConnect implémente le flux [Authorization Code Flow](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth) d'OpenID Connect. 

Les fournisseurs de service doivent être clients OpenID Connect, et les fournisseurs d'identité doivent être fournisseurs OpenID Connect. AgentConnect est une brique intermédiaire qui est à la fois fournisseur (du point de vue des FS) et client (du point de vue des FI).

### Chiffrement et signature des échanges

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

Environnement Internet : 


| Environnement | adresses du endpoint |
| ------ | ------ |
| intégration AC | https://fca.integ01.dev-agentconnect.fr/api/v2/client/.well-known/keys |
| production AC | https://**A compléter** |  


**Démonstrateurs Internet**

FI Internet :

https://fia1v2.integ01.dev-agentconnect.fr

https://fia2v2.integ01.dev-agentconnect.fr

FS Internet :

https://fsa1v2.integ01.dev-agentconnect.fr

https://fsa2v2.integ01.dev-agentconnect.fr

https://fsa3v2.integ01.dev-agentconnect.fr




Environnement RIE : 

| EndPoint | Adresse |
| ------ | ------ |
| intégration AC | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/client/.well-known/keys |
| production AC | https://**A compléter** |  


**Démonstrateurs RIE**

FI RIE :

https://fia1v2.integ02.agentconnect.rie.gouv.fr

https://fia2v2.integ02.agentconnect.rie.gouv.fr

FS RIE :

https://fsa1v2.integ02.agentconnect.rie.gouv.fr

https://fsa2v2.integ02.agentconnect.rie.gouv.fr

https://fsa3v2.integ02.agentconnect.rie.gouv.fr


les clés de signatures utilisés par le Fournisseur d'Identité doivent être disponible via la *JWKS URL* présente dans les méta-data de la *Discovery URL*. 


## Les données utilisateur

### L'identité pivot

En plus de l'openid, qui est obligatoire, l'identité pivot fait partie des données usagers fournies par les Fournisseurs d'Identité aux Fournisseurs de Service, via AgentConnect . Elle permet d'identifier un utilisateur particulier.
                                                    

|Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
|given_name | Oui |Prénoms séparés par des espaces (standard OpenIDConnect)| UTF-8 (standard OpenIDConnect)|
|usual_name| Oui |Nom de famille d'usage (par défaut = family_name)| UTF-8 |
|email | Oui |Adresse courriel |UTF-8 (standard OpenIDConnect)|
|uid|Oui |Identifiant unique de l'agent auprès du FI| String (standard OpenIDConnect)|

L'uid est une donnée technique qui ne peut pas être demandé par le FS.


### Les données complémentaires 

Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
|Siren | non  | Identifiant d'entreprise  | String, 9 chiffres sans espace |
|Siret | non |Identifiant d'établissement| string, 14 chiffres sans espace|
|Organizational_unit  | non  | Ministère/Direction/Service d'affectation   | UTF8 |
|Belonging_population  | non  | Population d'appartenance  | string, Exemple: agent, prestataire, partenaire, stagiaire, etc |
| phone  | non  | Téléphones de contact  | Format non normé |
| chorusdt:societe   | Non | Entité ministérielle  | string |
| chorusdt:matricule | Non | Matricule Agent       | string |


La liste des données complémentaires est non exhaustive et pourra être mise à jour si besoin. 


# Je veux être fournisseur d'identité AgentConnect
Pour devenir fournisseur d'identité FranceConnect, envoyer votre demande à l'adresse support.partenaires@agentconnect.gouv.fr avec les éléments suivants :

* Nom du fournisseur d'identité
* Titre (tel qu'il apparaîtra aux agents)
* Email de contact 
* URL du endpoint d'authentification et d'autorisation
* URL du endpoint de demande de token
* URL du endpoint de demande des informations agent (identité pivot)
* URL du endpoint de logout ( norme OIDC )
* URL de endpoint de métadonnée '.well-known/openid-configuration'
* Status URL (URL pour tester l'état du FI)
* Client ID
* Client secret

## Nos Endpoints

En environnements d'intégration et de production AgentConnect, les endpoints sont disponibles en HTTPS.

Environnement Internet : 

| Environnement | Adresse de retour ( Redirect URI ) |
| ------ | ------ |
| intégration AC | https://fca.integ01.dev-franceconnect.fr/api/v2/oidc-callback/{fc-internal-id} |
| production AC | **A compléter** |  


Environnement RIE : 

| Environnement | Adresse de retour ( Redirect URI ) |
| ------ | ------ |
| intégration AC | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/oidc-callback/{fc-internal-id}  |
| production AC | **A compléter** |  


La valeur `{AC-internal-id}` est spécifique à chaque fournisseur d'identité et sera fournie par AgentConnect.


## Détail du fonctionnement


![image](https://user-images.githubusercontent.com/78731004/109618890-6783ad80-7b38-11eb-9d8d-08034d3ce00f.png)



Les access token fournis par le FI doivent être de préférence à usage unique ou si cela n'est pas possible avec une durée de vie très courte [https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.16.18](https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.16.18)

## Détail des flux

Les flux entre AC et le FI respectent ce qui est défini dans la norme OpenId Connect. Pour plus de détails, il faut se référer à la [documentation OIDC - https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth)


## Certificats d'authentification 

Lors de la récupération les données de l'identité pivot et des attributs complémentaires auprès du FI, AgentConnect transmet un certificat SSL client RGS * Certigna pour la vérification de l'authentification.
 
## Utiliser les niveaux eIDAS en tant que FI

eIDAS est un standard européen visant à normaliser et à améliorer la sécurité de l'identification sur Internet. Il propose notamment 3 niveaux de garantie sur les moyens utilisés pour l'identification. En tant que FI, il est nécessaire de retourner à AgentConnect le niveau eIDAS avec lequel l'utilisateur vient de s'authentifier.

AgentConnect s'inspire du règlement eIDAS pour définir les différents niveaux de sécurité dans les échanges avec les FI et les FS. 

le FI doit signifier à AgentConnect avec quel niveau eIDAS l'authentification de l'agent s'est faite. 

Dans le cadre du FI, cela se traduit par le fait de positionner le claim "acr" dans l'ID Token renvoyé au client (http://openid.net/specs/openid-connect-core-1_0.html#rfc.section.2). De la même manière que pour un FS demandant à AgentConnect de filtrer les FIs compatibles avec un niveau eIDAS particulier.

Le claim acr retourné dans l'ID Token peut être :

* eidas1 : niveau faible
* eidas2 : niveau substantiel 
* eidas3 : niveau élevé 

Cette donnée est retournée à AgentConnect, qui lui même la retourne au FS sans la modifier.
Elle contribue à autoriser ou non l'accès aux ressources. 


# Parcours d'utilisation de l'agent et recommandations UX

La mire de connexion du fournisseur d'identité doit tout d'abord être responsive. 

Les éléments suivants sont recommandés, afin d'éviter l'abandon de l'agent lors d'une cinématique AgentConnect :

* Lien de contact du support du fournisseur d'identité
* Lien de mot de passe oublié.

Nous recommandons également les éléments suivants sur la mire de connexion du fournisseur d'identité :

Fond grisé avec Marianne en blanc en bas à droite.
Logos d'AgentConnect et du fournisseur d'identité.
Lien "retourner sur AgentConnect" pour permettre le changement de fournisseur d'identité à l'agent.


Ci-dessous les éléments visuels nécessaires : **A compléter**

<img src="uploads/19e0c2e1d02d2a6b1a3f97a74a35c559/logo_marianne.png" alt="drawing" width="150"/>
<img src="uploads/e08be0034c2ae3b1faca59e70bbec1a1/fc_avatar.png" alt="drawing" width="150"/>

Téléchargements :

**A compléter**

* [Pack png](uploads/af84d2a6599ec7a07671d43d2f400ff3/fc_images_png.zip)
* [Pack jpg](uploads/1429d69fe3baee1cc8560ad365aaec96/fc_images_jpg.zip)


Le parcours d’identification doit être validé par l’équipe AgentConnect le plus en amont possible de la réalisation sous la forme suivante : 
* communication des maquettes ou spécifications fonctionnelles
* qualification du parcours d’identification en environnement d'intégration

Ces deux étapes sont des pré-requis à une ouverture en production. 

L’équipe AgentConnect est là pour vous aider à proposer l’expérience usager la plus adaptée. 
N'hésitez pas à la solliciter pour éviter d'impacter vos délais de mise en production.


# Glossaire

Le glossaire relatif à OpenId Connect est spécifié à l'adresse [https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.1.2](https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.1.2)
