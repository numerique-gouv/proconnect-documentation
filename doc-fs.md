

| Version | Résumé des modifications | Modifié par | Date |
| ------ | ------ | ------ | ------ |
| v1 | Rédaction de la documentation FI | Khadija BOURHALEB | 08/12/2020 |


[[_TOC_]]


# Préambule

Cette documentation est à destination des Fournisseurs de Services souhaitant intégrer AgentConnect. 

AgentConnect est implémenté sur deux plateformes, une dite "full RIE" et une autre "hybride Internet/RIE"

Le choix du positionnement est laissé aux Fournisseurs de Services. 

# Je veux devenir Fournisseurs de Services 

## Quelles sont les étapes pour devenir Fournisseur de Services ? 

1. Vous consultez les conditions d'éligibilité à AgentConnect. Les conditions juridiques, de sécurité et de qualité de service sont détaillées dans nos [conditions générales d'utilisation](https://partenaires.agentconnect.gouv.fr/cgu) **A COMPLETER**  
Le cadre d'implémentation et d'intégration est détaillé dans nos [spécifications ergonomiques](https://partenaires.agentconnect.gouv.fr/) **A COMPLETER** 

2. Vous pouvez soumettre une demande de financement par le SNAP 2 AgentConnect, les renseignements sont disponibles sur le site https://france-relance.transformation.gouv.fr/953d-simplifier-lauthentification-des-agents-grace et en déposant une demande depuis le site https://www.demarches-simplifiees.fr

3. Vous soumettez une demande d'habilitation via [datapass.api.gouv.fr](https://datapass.api.gouv.fr/) et vous transmettez toutes les informations nécessaires à la validation de votre demande (**respect du RGPD**, contact du responsable technique, données d'identité recueillies, etc). Votre demande est validée par la DINUM dans un délai moyen de 5 jours ouvrés.

3. Si votre demande est acceptée, votre responsable technique reçoit un mail lui donnant accès à l'[espace partenaire](https://partenaires.agentconnect.gouv.fr/login) **A COMPLETER** . Cet espace vous permettra d'accéder aux ressources de développement et de test.

4. Vous présentez vos développements pour une qualification par l'équipe AgentConnect. La durée de cette phase de qualification dépend du [respect des prérequis](https://partenaires.Agentconnect.gouv.fr/monprojet/recetter/)(techniques, sécurité, fonctionnels, UX...) **A mettre à jour avec le lien**.
 N'hésitez pas à soumettre vos maquettes du parcours en amont pour une pré-qualification fonctionnelle et UX anticipée.

5. Si votre implémentation est validée par notre équipe technique, vous recevez vos secrets pour passer en production.

## Accès à l'environnement d'intégration AgentConnect 

Pour vous permettre de réaliser les développements liés à l'intégration d'AgentConnect, nous mettons à disposition un environnement d'intégration. Les accès à cet environnement se font à travers des clés qui vous sont communiquées par la DINUM dans l'attente de la mise en place de votre espace partenaire. 

Sur notre environnement d'intégration, vous pourrez utiliser les fournisseurs d'identités de démonstratation pour effectuer vos tests. 


Les adresses de notre environnement d'intégration sont les suivantes : 

Environnement Internet : 

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://fca.integ01.dev-agentconnect.fr/api/v2/.well-known/openid-configuration  | 
| Authorization | https://fca.integ01.dev-agentconnect.fr/api/v2/authorize |
| Token | https://fca.integ01.dev-agentconnect.fr/api/v2/token | 
| UserInfo | https://fca.integ01.dev-agentconnect.fr/api/v2/userinfo  | 
| Logout | https://fca.integ01.dev-agentconnect.fr/api/v2/logout | 

**Démonstrateurs Internet** 

FI Internet :

https://fia1v2.integ01.dev-agentconnect.fr

https://fia2v2.integ01.dev-agentconnect.fr

FS Internet :

https://fsa1v2.integ01.dev-agentconnect.fr

https://fsa2v2.integ01.dev-agentconnect.fr

https://fsa3v2.integ01.dev-agentconnect.fr


Environnement RIE : 

 EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/.well-known/openid-configuration  | 
| Authorization | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/authorize |
| Token | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/token | 
| UserInfo | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/userinfo  | 
| Logout | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/logout | 

**Démonstrateurs RIE** 


FI RIE :

https://fia1v2.integ02.agentconnect.rie.gouv.fr

https://fia2v2.integ02.agentconnect.rie.gouv.fr

 
FS RIE :

https://fsa1v2.integ02.agentconnect.rie.gouv.fr

https://fsa2v2.integ02.agentconnect.rie.gouv.fr

https://fsa3v2.integ02.agentconnect.rie.gouv.fr


## Mettre en production mon Fournisseur de Services

Pour mettre en production votre Fournisseur de Services, il faut au préalable avoir : 

1. Reçu la qualification de vos développements par AgentConnect sur un environnement autre que votre production. 
2. Demandé une mise en production à l'équipe AgentConnect, **En attente de la mise en place de l'espace partenaires**
3. Utilisé les clés de production qui vous ont été fournies par AgentConnect. 

**Attention :** Il ne faut surtout pas utiliser les clés d'intégration que vous avez utilisées lors de vos développements avec votre Fournisseur de Services en production. Les clés d'intégration ne sont utilisables que sur l'environnement d'intégration AgentConnect.

Les adresses de notre environnement de production sont les suivantes : 

Environnement Internet : 

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://**TBD**/api/v2/.well-known/openid-configuration  | 
| Authorization | https://**TBD**/api/v2/authorize |
| Token | https://**TBD**/api/v2/token | 
| UserInfo | https://**TBD**/api/v2/userinfo  | 
| Logout | https://**TBD**/api/v2/logout | 


Environnement RIE : 

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://**TBD**/api/v2/.well-known/openid-configuration  | 
| Authorization | https://**TBD**/api/v2/authorize |
| Token | https://**TBD**/api/v2/token | 
| UserInfo | https://**TBD**/api/v2/userinfo  | 
| Logout | https://**TBD**/api/v2/logout | 



# Concepts de base
## Le protocole OpenID Connect
### Introduction

Le protocole OpenID Connect est au cœur du fonctionnement d'AgentConnect. C'est une couche d'identification basée sur protocole OAuth 2.0. Il permet à des Clients (ici, les Fournisseur de Service) d'accéder à l'identité des Utilisateurs finaux (les internautes) par l'intermédiaire d'un serveur d'autorisation (ici, les Fournisseurs d'Identité).

La spécification du protocole se trouve sur http://openid.net/connect/.

Pour une référence d'implémentation OpenID Connect voici le lien : https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth

### Les flux standards

Le protocole OpenID Connect définit 3 appels REST faits par le client, et 4 endpoints (un du côté client, et trois du côté provider).

En amont, le client s'inscrit (en général manuellement) auprès du provider. Il lui fournit une URL de callback (l'URL du client vers lequel l'internaute est redirigé une fois authentifié), aussi appelée "callback endpoint". En retour le provider donne au client un client ID et un client secret.

Lorsque l'internaute clique sur le bouton d'authentification du client, le flux est le suivant :

1. Le client fait une redirection vers le "authorization endpoint" du provider avec son client id et son url de callback. Le provider redirige alors l'internaute vers sa mire d'authentification. Si l'internaute se loggue correctement, le provider renvoie un code d'autorisation au client.
2. Le client fait un appel Web service vers le "token endpoint" du provider avec le code d'autorisation reçu, et authentifie cette requête avec son client id et son client secret. Le provider retourne un access token (une chaîne de caractères encodée en base64), un id token (sous la forme d'un Json Web Token), et parfois un refresh token (une chaîne de caractères en base64).
3. Le client fait un appel Web service vers le "userInfo endpoint" du provider avec l'access token reçu, et le provider renvoie les informations de l'internaute au client.

### Dans le cadre d'AgentConnect

L'enregistrement des Fournisseurs de Service auprès d'AgentConnect s'effectue en déposant une demande sur le site [datapass.api.gouv.fr](https://datapass.api.gouv.fr/)

AgentConnect implémente le flux [Authorization Code Flow](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth) d'OpenID Connect. 

Les fournisseurs de service doivent être *service provider* OpenID Connect, et les fournisseurs d'identité doivent être *identity provider* OpenID Connect. AgentConnect est une brique intermédiaire qui est à la fois *identity provider* (du point de vue des FS) et *service provider* (du point de vue des FI).

### Chiffrement et signature des échanges

Dans le cadre du niveau **Standard** , tous les échanges de jetons JWT entre le FI et AC sont signés. 
Le chiffrement des jetons n'est actuellement pas activé. 

les algorithmes suivants sont gérés par AgentConnect Standard : 

**Signature de jetons par AgentConnect** :

- Asymétrique : 

       - ES256 (EC + SHA256)
       - RS256 (RSA + SHA256)

- Symétrique : géré mais non recommandé

       - HS256 (HMAC + SHA256) 

**:warning: Ces algorithmes sont valides pour les endpoints exposant des JWT (/token et /userinfo).**


Les spécifications des algorithmes de signatures et de chiffrements utilisés sont les suivantes :

* [JWA - https://tools.ietf.org/html/rfc7518](https://tools.ietf.org/html/rfc7518)
* [JWS - https://tools.ietf.org/html/rfc7515#appendix-A.3](https://tools.ietf.org/html/rfc7515#appendix-A.3)
* [JWE - https://tools.ietf.org/html/rfc7516#appendix-A.1](https://tools.ietf.org/html/rfc7516#appendix-A.1)


Les clés publiques de signatures de AgentConnect sont disponibles via la *JWKS URL* présente dans les méta-data de la *Discovery URL* aux adresses suivantes et sont changées régulièrement :


Environnement Internet : 

| Environnement | adresses du endpoint |
|---------------|----------------------|
| intégration AC | https://fca.integ01.dev-agentconnect.fr/api/v2/jwks |
| production AC |**A compléter** |

Environnement RIE :

| Environnement | adresses du endpoint |
|---------------|----------------------|
| intégration AC | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/jwks|
| production AC |**A compléter** |


## Les données Agent
Les données Agent sont fournies par les Fournisseurs d'Identité aux Fournisseurs de Service, via AgentConnect, conformément à l'habilitation obtenue via [datapass.api.gouv.fr](https://datapass.api.gouv.fr), et le choix des données réalisé par le fournisseur de service dans cette demande.

L'identité pivot permet d'identifier un agent.

### L'identité pivot

En plus de l'openid, qui est obligatoire, l'identité pivot fait partie des données usagers fournies par les Fournisseurs d'Identité aux Fournisseurs de Service, via AgentConnect . Elle permet d'identifier un utilisateur particulier.
                                                    

|Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
|given_name | Oui |Prénoms séparés par des espaces (standard OpenIDConnect)| UTF-8 (standard OpenIDConnect)|
|usual_name| Oui |Nom de famille d'usage (par défaut = family_name)| UTF-8 |
|email | Oui |Adresse courriel |UTF-8 (standard OpenIDConnect)|
|uid|Oui |Identifiant unique de l'agent auprès du FI| String (standard OpenIDConnect)|

L'uid est une donnée technique qui ne peut pas être demandé par le FS.

En complément, il est possible d'obtenir des données complémentaires. Cependant ces données ne sont pas obligatoirement connues par tous les Fournisseurs d'Identité.


### Les données complémentaires

Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
|Siren | non  | Identifiant d'entreprise  | String, 9 chiffres sans espace |
|Siret | non |Identifiant d'établissement| string, 14 chiffres sans espace|
|Organizational_unit  | non  | Ministère/Direction/Service d'affectation   | UTF8 |
|Belonging_population  | non  | Population d'appartenance  | string, Exemple: agent, prestataire, partenaire, stagiaire |
| phone  | non  | Téléphones de contact  | Format non normé |
| chorusdt:societe   | Non | Entité ministérielle  | string |
| chorusdt:matricule | Non | Matricule Agent       | string |


La liste des données complémentaires est non exhaustive et pourra être amendée si besoin.


AgentConnect transmet systématiquement au Fournisseur de Service un identifiant unique pour chaque agent : 

* Cet identifiant est spécifique à chaque Fournisseur de Service. Un même utilisateur aura donc un identifiant unique différent pour chacun des Fournisseurs de Service auxquels il accède. 

* Cet identifiant est le même quelque soit le Fournisseur d'Identité qui est utilisé par l'agent. 


### Liste des scopes disponible lors de l'étape d'authentification AgentConnect

AgentConnect a étendu le mécanisme de scopes pour qu'il soit plus modulaire.

* Un seul scope est obligatoire : openid. Il permet de récupérer le sub (identifiant unique technique) de l'utilisateur.
* Il est possible de récupérer individuellement chaque propriété de l'identité pivot en utilisant leurs scopes dédiés.
* Il est possible de combiner plusieurs scopes de son choix pour récupérer seulement les informations dont a besoin le FS.


Cette liste de scopes est définie par la norme OpenIDConnect : http://openid.net/specs/openid-connect-core-1_0.html#ScopeClaims

# Je veux authentifier des utilisateurs via AgentConnect

# Intégration d'un bouton AgentConnect 

Les boutons d’action AgentConnect sont primordiaux dans l’usage du service. Il est obligatoire d’utiliser l’un des boutons proposé et aucun autre visuel pour la connexion des usagers.

Pour les boutons en svg, lors de l'utilisation d'une image veuillez préciser la taille du bouton.

Téléchargements :


Bouton Bleu AgentConnect : à utiliser en priorité 


![ac-bouton-bleu](https://user-images.githubusercontent.com/78731004/109621703-9cddca80-7b3b-11eb-821c-c3e3618232e0.jpg)
![ac-bouton-bleu](https://user-images.githubusercontent.com/78731004/109621705-9d766100-7b3b-11eb-97e4-ad096d49b8cd.png)
![ac-bouton-bleu@2x](https://user-images.githubusercontent.com/78731004/109621707-9d766100-7b3b-11eb-8d9d-a7f6afe5c983.jpg)
![ac-bouton-bleu@2x](https://user-images.githubusercontent.com/78731004/109621708-9d766100-7b3b-11eb-9f84-089532d5467c.png)

Bouton blanc AgentConnect :

![ac-bouton-blanc](https://user-images.githubusercontent.com/78731004/109621823-bda62000-7b3b-11eb-98fe-95afe625e47d.jpg)
![ac-bouton-blanc](https://user-images.githubusercontent.com/78731004/109621826-bda62000-7b3b-11eb-8399-f7c8964d04e8.png)
![ac-bouton-blanc@2x](https://user-images.githubusercontent.com/78731004/109621827-be3eb680-7b3b-11eb-8c72-bacf30b3f258.jpg)
![ac-bouton-blanc@2x](https://user-images.githubusercontent.com/78731004/109621829-be3eb680-7b3b-11eb-9d32-1547b7cda7d0.png)

Pour le format SVG, merci de contacter l'équipe produit. 

## Détail du fonctionnement


![image](https://user-images.githubusercontent.com/78731004/109619444-132cfd80-7b39-11eb-9e69-e372cdd8ff39.png)


                        
La récupération de l'identité pivot doit être faite dans la suite immédiate des appels précédents (authentification et récupération du code). Le fait d'appeler ce Web service plus tard n'est aujourd'hui pas proposé.

### Détail des flux

Les flux entre AgentConnect et le Fournisseur de Service respectent ce qui est défini dans la norme OpenId Connect. Pour plus de détails, il faut se référer à la [documentation OIDC - https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth)


## Utiliser les niveaux eIDAS en tant que FS AgentConnect

eIDAS est un standard européen visant à normaliser et à améliorer la sécurité de l'identification sur Internet. Il propose notamment 3 niveaux de garantie sur les moyens utilisés pour l'identification. Vous pouvez, en tant que Fournisseur de Service, utiliser les niveaux eIDAS afin de récupérer une identité avec le niveau de garantie correspondant à votre besoin.

AgentConnect s'inspire du règlement eIDAS pour définir les différents niveaux de sécurité dans les échanges avec les FI et les FS.

Actuellement les fournisseurs de services ne peuvent demander qu'un niveau eIDAS 1, soit un niveau dit faible à AgentConnect

Comme la norme OpenID Connect ne prévoit pas aujourd'hui de mesures techniques particulières pour préciser le niveau souhaité, AgentConnect utilise le claim optionnel "acr" (http://openid.net/specs/openid-connect-basic-1_0.html#RequestParameters) de la norme OpenID Connect. 

Pour le Fournisseur de Service, cela veut dire remplir le claim optionnel acr_values lors de la demande d'authentification (appel à l'endpoint /api/v2/authorize).


le Fournisseur d'Identité renverra par le biais de AgentConnect le niveau eIDAS avec lequel l'authentification a eu lieu. 



# Je veux déconnecter l'agent de AgentConnect

La gestion de la déconnexion n'est pas prise en charge dans la version 1.0 d'AgentConnect.
Il incombe aux fournisseurs de Services de la gérer :

* la déconnexion auprès d'AgentConnect
* la révocation de l’accès token


# Gestion d'erreurs entre AgentConnect et le Fournisseur de Service

En tant qu'OpenID Connect provider, AgentConnect peut renvoyer toutes sortes d'erreurs à une application cliente. Pour ce faire, AgentConnect passe par le mécanisme de retour d'erreurs d'un fournisseur d'identité openid connect tel que décrit dans la norme ( http://openid.net/specs/openid-connect-core-1_0.html#AuthError, en particulier les sections 3.1.2.6 (authentification), 3.1.3.4 (jeton d'accès), 5.3.3 (service d'informations utilisateur) )


# Les données d’AgentConnect qui expirent

AgentConnect gère plusieurs types de données ayant une durée de vie limitée lors du déroulé d'une authentification par OpenID Connect ou de la fourniture d'un jeton d'accès à une ressource protégée (cinématique OAuth2 classique). Chacune de ces données possède une durée de vie qui lui est propre au-delà de laquelle elle doit être régénérée. En voici le détail :


| Type | Utilisé lors de ... | Durée de vie |
| ------ | ------ | ------ |
| Access Token | Récupération d'informations (phase 3 cinématique d'authentification / cinématique OAuth2) | 60 secondes |
| Authorization code | Code fourni lors du début de la démarche d'authentification, il sert ensuite à récupérer l'access token | 30 secondes |



# Glossaire


* **AC_URL :**  URL d’AgentConnect 
* **FS_URL :** Votre URL, en tant que fournisseur de service  
* **FD_URL :** URL du fournisseur de données
* **CALLBACK_URL_DATA :** le callback du FS, communiqué lors de son inscription auprès d’AC 
* **POST_LOGOUT_REDIRECT_URI :** L'URL de redirection après la demande de déconnexion AC 
* **CLIENT_ID :** Identifiant du FS, communiqué lors de son inscription auprès de AC 
* **CLIENT_SECRET :** Le secret du FS, communiqué lors de son inscription auprès de AC 
* **AUTHZ_CODE :** Code retourné (dans l'URL) par AC au FS lorsque ce dernier fait un appel sur le endpoint AC_URL/api/v1/authorize. Il est ensuite passé (dans le corps de la requête HTTP POST) lors de l'appel sur le endpoint AC_URL/api/v1/token
* **ACCESS_TOKEN :** oken retourné (dans le corps HTTP) par l'appel au endpoint AC_URL/api/v2/token. Il est ensuite passé lors de l'appel au endpoint AC_URL/api/v2/userinfo 
* **SCOPES :** Liste des scopes demandés séparés par des espaces (donc par %20 au format unicode dans l'URL)  
	
Voici la liste supportée par AgentConnect :

    * openid : obligatoire, permet de demander l'identifiant technique de l'utilisateur au format OpenIDConnect
    * profile : obligatoire, permet de récupérer l'essentiel de l'identité pivot 
    * email : obligatoire, permet de récupérer l'adresse électronique de l’agent

Cette liste de scopes est définie par la norme OpenIDConnect

* **ID_TOKEN :** Objet JWT retourné par l'appel au endpoint AC_URL/api/21/token. L'objet JWT est un objet JSON formaté et signé. Le JSON doit contenir ces six clés : aud,exp,iat,iss,sub et nonce.

Exemple :

```
{
    'aud':'895fae591ccae777094931e269e46447',
    'exp':1412953984,
    'iat':1412950384,
    'iss':http://Agentconnect.gouv.fr,
    'sub':YWxhY3JpdMOp,
    'idp':'AC',
    'nonce':'12344354597459'
}
```
Les champs *aud, exp, iat, iss, sub* sont des champs obligatoires de la norme OpenId Connect. Le *nonce* est un  paramètre obligatoirement envoyé lors de l'appel à `/authorization`. Le FS doit impérativement vérifier que la valeur correspond bien à celle qu'il a envoyée, et qui doit être liée à la session de l'utilisateur.

Si vous utilisez une librairie pour transformer le json en JWT, il génèrera une chaîne de caractères constitué de 3 chaînes base64 séparées par un point.

* **ID_TOKEN_HINT :** Objet JWT identique au format ID_TOKEN qui a été reçu lors de l'échange avec l'appel à AC_URL/api/v1/token et doit être passé en paramètre lors de l'appel à AC_URL/api/v2/logout
* **USER_INFO :**  Voir la section identité pivot
* **STATE :** Champ obligatoire, généré aléatoirement par le FS, que AC renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par le FS. Il est utilisé afin d’empêcher l’exploitation de failles CSRF
* **NONCE :**	Champ obligatoire, généré aléatoirement par le FS que AC renvoie tel quel dans la réponse à l'appel à /token, pour être ensuite vérifié par le FS. Il est utilisé pour empêcher les attaques par rejeu
* **SUB :** Identifiant technique (unique et stable dans le temps pour un individu donné) fourni par AgentConnect au FS. Le SUB est présent dans l'IdToken retourné au FS ainsi que dans les informations d'identité. Le SUB retourné par AgentConnect est spécifique à chaque fournisseur de service (i.e: Un usager aura toujours le même SUB pour un Fournisseur de Service donné, en revanche il aura un SUB différent par Fournisseur de Service qu'il utilise).
