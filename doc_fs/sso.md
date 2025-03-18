# SSO

## 1. Vue d'ensemble

### 1.1. Qu'est-ce que le SSO ?

Le Single Sign-On (SSO) est un service d'authentification unique qui permet à un utilisateur d'accéder à plusieurs applications "ProConnectées" avec un unique email professionnel et un mot de passe.

Lorsqu'un utilisateur tente d'accéder à une application sans être authentifié, il est redirigé vers ProConnect. Ce service procède à l'authentification de l'utilisateur et le renvoie ensuite vers l'application.

Sa session active auprès de ProConnect permet à l’utilisateur d'accéder à toutes les applications et sites web protégés connectés à ProConnect sans que l'utilisateur ait à ressaisir ses informations d'identification.

### 1.2. Comment cela fonctionne ?

La connexion au SSO est la suivante :

1. Lorsqu'un utilisateur se connecte à une application, celle-ci envoie une demande d'authentification au service ProConnect. 
2. ProConnect vérifie si l'utilisateur a déjà été authentifié dans le système.
3. Deux cas de figures possibles :
- si l'utilisateur a déjà une session en cours, ProConnect envoie une réponse de confirmation d'authentification à l'application pour accorder l'accès à l'utilisateur. 
- si l'utilisateur n'a pas de session en cours, ProConnect redirige l'utilisateur vers son système de connexion en lui demandant ses informations de connexion (email et mot de passe).


Le Single Sign-On (SSO) simplifie l'expérience de connexion et la gestion des identifiants et mots de passe pour les utilisateurs finaux. Grâce au SSO, les utilisateurs ont moins de mots de passe à gérer et peuvent accéder à l'ensemble des services "ProConnectés" avec une seule authentification.


### 1.3. Qu'est-ce qu'il permet ?

Au-delà d’être un service d’authentification centralisé, le SSO permet de ne demander à l'utilisateur de se connecter qu'une seule fois. Les autres services connectés au SSO peuvent alors déterminer l'état de connexion de l'utilisateur sans nécessiter aucune action manuelle de sa part.

Cela offre une expérience de connexion optimale, sans action manuelle de l'utilisateur, dès lors qu'il possède déjà une session valide dans l'un des services "ProConnectés".


----
## 2. Implémentation du Silent Login

:warning: Le SSO fonctionne automatiquement et par défaut pour tous les Fournisseurs de Service (FS).

Il est possible de réaliser une authentification "silencieuse" dans ProConnect, c'est-à-dire ne pas avoir besoin d'afficher le bouton ProConnect sur votre FS.
Nous suivrons l'exemple ici d'un FS qui expose les trois URLs suivantes :
- `https://fs.gouv.fr/` : la page d'accueil de l'outil
- `https://fs.gouv.fr/login-callback/` : la `redirect_uri` renseignée par le FS dans la config ProConnect, i.e. celle vers laquelle sera redirigé l'utilisateur après connexion
- `https://fs.gouv.fr/login/` : la page où est affiché le bouton "S'identifier avec ProConnect"

Le parcours est le suivant, lorsque l'utilisateur se rend sur `https://fs.gouv.fr/` :

### Scénario 1 : le navigateur de l'utilisateur contient des informations de session du FS, i.e. l'utilisateur est déjà connecté au FS

-> Rien à implémenter, l'utilisateur peut utiliser l'outil

### Scénario 2 : le navigateur de l'utilisateur ne contient pas d'informations de session du FS
Le navigateur redirige l'utilisateur vers la route `/authorize` (cf. [implémentation technique](./implementation_technique.md#22-faire-pointer-le-bouton-proconnect-vers-le-authorization_endpoint)), en ajoutant le query parameter `prompt=none`.
Ce query parameter permet de faire échouer l'appel à ProConnect si l'utilisateur n'a pas de session active dans ProConnect.
Ce comportement peut être souhaitable dans le cas où vous préférez que l'utilisateur ne soit pas redirigé sur une fenêtre de connexion sans explications. 

À l'appel à la route `/authorize`, deux scénarios sont possibles :

### Scénario 2.1 : l'utilisateur a une session ProConnect en cours
ProConnect redirige l'utilisateur vers la route `https://fs.gouv.fr/login-callback/` avec les paramètres d'identification tels que décrits dans l'[implémentation technique](./implementation_technique.md).

### Scénario 2.2 : l'utilisateur n'a pas de session ProConnect en cours
ProConnect redirige l'utilisateur vers la route `https://fs.gouv.fr/login-callback/` avec plusieurs paramètres, dont `error=login_required`.
Le FS doit donc implémenter le fait que, lorsque ce paramètre est présent avec cette valeur, l'utilisateur doit être redirigé vers `https://fs.gouv.fr/login/`.

