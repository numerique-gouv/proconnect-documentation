# Comment déconnecter l'agent d'AgentConnect ?

## Gestion de la déconnexion

La gestion de la déconnexion n'est pas prise en charge dans la version 1.0 d'AgentConnect. Il incombe aux Fournisseurs de Services de gérer :

- la déconnexion auprès d'AgentConnect,
- la révocation de l’access token. 

## Cinématique de déconnexion par un Fournisseur de Services

AgentConnect implémente la section sur la déconnexion en cours de spécification dans la norme OpenID Connect : https://openid.net/specs/openid-connect-frontchannel-1_0.html#RPLogout

AgentConnect ne gère pas la déconnexion de l'usager au service AgentConnect à la fermeture du navigateur.

Le Fournisseur de Services doit pouvoir déconnecter l'utilisateur de sa session AgentConnect. La cinématique globale est celle-ci :

1. L' utilisateur clique sur un lien de déconnexion présenté par le Fournisseur de Services,
2. Le Fournisseur de Services doit déconnecter l'utilisateur de son application et de sa session AgentConnect,
3. L' utilisateur est redirigé vers la page de retour spécifiée par le Fournisseur de Services,
4. Le Fournisseur de Services doit préciser l'URL où l'on doit rediriger l'utilisateur une fois qu'il a choisi de se déconnecter ou non d'AgentConnect via le paramètre post_logout_redirect_uri, ainsi que passer l'id_token récupéré lors de l'authentification de l'utilisateur via le paramètre id_token_hint.

Il est obligatoire de renseigner les différentes urls de redirections de déconnexion dans les paramètres client.

---

Voir aussi : 
- [Comment révoquer l'access token ?](../deconnexion_fca/access_token.md)
