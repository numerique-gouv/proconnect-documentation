
[Accueil](../README.md) > [ProConnect - Fournisseur de Service](README.md) > [Implémentation Technique](implementation_technique.md) > Test de la connexion d'un Fournisseur de Service

---

# SSO

## 1. Vue d'ensemble

### 1.1. Qu'est-ce que le SSO ?

Le Single Sign-On (SSO) est un service d'authentification unique qui permet à un utilisateur d'accéder à plusieurs applications "ProConnectées" avec un unique email professionnel et un mot de passe.

Lorsqu'un utilisateur tente d'accéder à une application sans être authentifié, il est redirigé vers ProConnect. Ce service procède à l'authentification de l'utilisateur et le renvoie ensuite vers l'application.

Sa session active auprès de ProConnect, permet à l’utilisateur d'accéder à toutes les applications et sites web protégés connectés à ProConnect sans avoir à ressaisir leurs informations d'identification.



### 1.2. Comment cela fonctionne ?

La connexion au SSO est la suivante :

1. Lorsqu'un utilisateur se connecte à une application, celle-ci envoie une demande d'authentification au service ProConnect. 
2. ProConnect vérifie si l'utilisateur a déjà été authentifié dans le système. Si tel est le cas, il envoie une réponse de confirmation d'authentification à l'application pour accorder l'accès à l'utilisateur. 
3. Si l'utilisateur n'a pas d'informations d'identification validées, ProConnect redirige l'utilisateur vers son système de connexion et l'invite à soumettre son email professionnel et son mot de passe.
4. Lors de la soumission, ProConnect valide les informations d'identification de l'utilisateur et envoie une réponse positive à l'application. 
5. Dans le cas contraire, l'utilisateur reçoit un message d'erreur et doit saisir à nouveau ses informations d'identification.


Le Single Sign-On (SSO) simplifie l'expérience de connexion et la gestion des identifiants et mots de passe pour les utilisateurs finaux. Grâce au SSO, les utilisateurs ont moins de mots de passe à gérer et peuvent accéder à l'ensemble des services "ProConnectés" avec une seule authentification.


### 1.3. Qu'est-ce qu'il permet ?

Au-delà d’être un service d’authentification centralisé, le SSO permet de ne demander à l'utilisateur de se connecter qu'une seule fois. Les autres services connectés au SSO peuvent alors déterminer l'état de connexion de l'utilisateur sans nécessiter aucune action manuelle de sa part.

Cela offre une expérience de connexion optimale, sans action manuelle de l'utilisateur, dès lors qu'il possède déjà une session valide dans l'un des services "ProConnectés".


----
## 2. Implémentation

Dans cette section, nous explorerons deux méthodes d'implémentation du SSO. Chacune de ces méthodes offre une expérience utilisateur différente.

### 2.1. Sans landing page

Lorsqu’un utilisateur accède au service, le système commence par déterminer s’il est authentifié. Cette vérification est essentielle pour offrir une expérience utilisateur fluide et sécurisée.

Si l’utilisateur n’est pas authentifié, le service envoie automatiquement une demande d’authentification au service ProConnect. Ce processus se déroule sans intervention de l’utilisateur, éliminant ainsi la nécessité de cliquer sur un bouton pour démarrer l’authentification.

ProConnect vérifie alors si l’utilisateur est déjà authentifié. Si tel est le cas, aucun écran n’est affiché à l’utilisateur. Il est redirigé directement vers le service, où il est authentifié sans interruption, lui permettant de continuer son parcours sans friction.

En revanche, si l’utilisateur n’est pas encore authentifié, une mire de connexion lui est présentée. Une fois qu’il a validé ses informations de connexion, il est redirigé vers le service, prêt à utiliser les fonctionnalités disponibles.

#### 2.1.1. Éléments techniques

Exemple de requêtes envoyées à ProConnect :

```
https://auth.agentconnect.gouv.fr/api/v2/authorize?response_type=code&scope=openid+email&client_id=...&redirect_uri=...&state=...&acr_values=eidas1&nonce=...
```

#### 2.1.2. Exemples

Les services ci-dessous utilisent cette approche :

- regie.numerique.gouv.fr
- docs.numerique.gouv.fr


### 2.2. Avec landing page

Dans le premier cas, si l’utilisateur n’est pas authentifié auprès de ProConnect, il sera redirigé vers une mire de connexion ProConnect avant de pouvoir accéder au service. Cela peut être acceptable pour certains services, mais pas pour tous.

Certains services préfèrent afficher une page d'accueil contenant des informations destinées aux utilisateurs non authentifiés ou nouveaux. Dans ce cas, il n’est pas acceptable de bloquer les utilisateurs sur la mire de connexion ProConnect.

Pour répondre à ce besoin, le service doit authentifier l’utilisateur de manière silencieuse. Il suffit d’ajouter un paramètre supplémentaire, `prompt=none`, à la requête. Si ProConnect ne parvient pas à authentifier l’utilisateur sans action de sa part, il redirigera l’agent utilisateur vers l’URL de rappel (callback) avec une erreur ```login_required```.

Le service sera alors informé que l’utilisateur n’a pas de session d’authentification active et pourra lui afficher la page d'accueil, tout en proposant un bouton de connexion via ProConnect.

#### 2.2.1. Éléments techniques

Cette approche repose sur le paramètre `prompt`, tel que décrit dans la spécification OIDC à la section [3.1.2.1 Authentication Request](https://openid.net/specs/openid-connect-core-1_0.html#AuthRequest).

Exemple de requête envoyée à ProConnect (incluant `prompt=none`) :
```
https://auth.agentconnect.gouv.fr/api/v2/authorize?client_id=...&scope=...&response_type=code&redirect_uri=...&acr_values=eidas1&nonce=...&state=...&prompt=none
```

#### 2.2.2. Exemples 

Les services ci-dessous utilisent cette approche : 

- meet.numerique.gouv.fr
- pad.numerique.gouv.fr

