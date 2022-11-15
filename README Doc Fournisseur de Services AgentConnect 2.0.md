
Documentation Fournisseur de Services

---

Vous souhaitez implémenter AgentConnect sur votre site? Vous êtes au bon endroit ! Cette documentation présente l'ensemble des informations à connaitre.

# Préambule

Cette documentation est à destination des Fournisseurs de Services souhaitant intégrer AgentConnect. 
AgentConnect est implémenté sur deux plateformes, une dite "full RIE" (l’agent se connecte depuis le RIE, à un FS RIE via un FI RIE) et une autre dite "full Internet" (l'agent se connecte depuis Internet, à un FS Internet via un FI Internet).
Toutefois il est possible de communiquer entre les deux plateformes grâce à l'"hybridge Internet/RIE" (l'agent se connecte depuis Internet, à un FS Internet via un FI RIE).

# Je veux devenir Fournisseur de Services 

Vous souhaitez devenir Fournisseur de Services pour AgentConnect, voici les éléments à prendre en compte : 

- [Quelles sont les étapes pour devenir Fournisseur de Services?](pilotage_fca/pilotage_fca_etapes.md)
- [Quels sont les différents acteurs que je dois faire intervenir dans mon organisation pour devenir Fournisseur de Services?](pilotage_fca/pilotage_fca_demarches_acteurs.md)
- [Qu'est-ce que la plateforme "Full Internet", la plateforme "Full RIE" et l'"Hybridge"?](pilotage_fca/plateformes.md)
- [Comment accéder au formulaire datapass?](pilotage_fca/datapass.md)

# J'intègre AgentConnect dans mon service en ligne

## Je souhaite connaître les différentes problématiques d'intégration d'AgentConnect

- [Quelles sont les données que je peux récupérer par AgentConnect sur mes usagers?](projet_fca/projet_fca_donnees.md)
- [Qu'est ce qu'eIDAS et quel est le niveau de garantie d'AgentConnect?](projet_fca/projet_fca_niveau_eidas.md)

## Je veux savoir comment fonctionne AgentConnect

- [Qu'est ce que le protocole OpenID Connect?](technique_fca/technique_oidc.md)
- [Comment AgentConnect utilise OpenID Connect?](technique_fca/technique_fca_oidc.md)
- [Quelles sont les données d'AgentConnect qui expirent?](technique_fca/donnees_expirent.md)

## Je veux savoir comment utiliser AgentConnect

- [Comment accéder aux différents environnements d'AgentConnect?](technique_fca/technique_fca_env.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs? ](technique_fca/technique_fca_scope.md)

## Je veux savoir comment authentifier des agents via AgentConnect

- [Détail du fonctionnement](fonctionnement_fca/details_fonctionnement.md)

## Je veux savoir comment déconnecter l'agent d'AgentConnect

- [Comment déconnecter l'agent d'AgentConnect?](deconnexion_fca/deconnexion.md)
- [Comment révoquer l'access token?](deconnexion_fca/access_token.md)

## Je veux savoir comment intégrer le bouton AgentConnect

- [Quel bouton AgentConnect intégrer et comment l'intégrer?](implementation_fca/bouton_fca.md)

## Je souhaite savoir comment réaliser des tests en intégration

- [Quels démonstrateurs sont disponibles sur la plateforme intégration d'AgentConnect?](test_fca/test_fca_demonstrateur.md)

## Gestion d'erreurs entre AgentConnect et le Fournisseur de Services

- [Comment les erreurs entre AgentConnect et le Fournisseur de Services sont-elles gérées?](erreur_fca/gestion_erreur.md)

# Je souhaite faire qualifier mon implémentation d'AgentConnect

- [Quel bouton AgentConnect intégrer et comment l'intégrer?](implementation_fca/bouton_fca.md)
- [Quels sont les prérequis ainsi que les spécifications à respecter au moment de l'implémentation?](implementation_fca/spec_recette_fca.md)

# Je souhaite mettre mon Fournisseur de Services en production

- [Comment faire qualifier mon implémentation?](recette_fca/recette.md)
- [Comment recevoir mes jetons de production?](recette_fca/recette_cles_prod.md)

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
