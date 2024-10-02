# Quelles sont les valeurs possibles pour le champ amr ?

Pour éviter à un usager d'avoir à s'authentifier auprès de votre Fournisseur de Service avec un second facteur alors qu'il a déjà utilisé une authentification multi-facteur sur un autre Fournisseur de Service, il est possible de récupérer via le claim `amr` la liste des méthodes d'authentification et d'adapter votre parcours en fonction.

Par défaut ce claim `amr` n'est pas retourné dans l'idToken, il doit être demandé explicitement par le Fournisseur de Service. En plus des autres paramètres envoyés lors de l'appel au `authorization_endpoint`, il est nécessaire pour le Fournisseur de Service de passer la valeur suivante :

| clé          | valeur  |
|--------------|---------|
| `id_token`   | `{"id_token":{"auth_time":{"essential":true}}}` |

Les valeurs possibles pour `amr` sont les suivantes :

| valeur amr | description                                                                                                                                |
|------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| pwd        | Authentification par mot de passe. En complément d'un mot de passe, l'utilisateur a authentifié son navigateur avec un one-time password envoyé par mail |
| mail       | Authentification par lien de connexion  "lien magique".                                                                                   |
| totp       | Authentification avec une application  "authenticator" comme FreeOTP.                                                                     |
| pop        | Authentification avec une clé d'accès (Passkey) ou carte agent.                                                                                           |
| mfa        | Authentification à deux facteurs.                     

Vous trouverez de plus amples informations sur [la documentation de FranceConnect](https://docs.partenaires.franceconnect.gouv.fr/fs/fs-technique/fs-technique-amr/#quels-sont-les-differents-methodes-d-authentification-qui-peuvent-etre-utilisees).
