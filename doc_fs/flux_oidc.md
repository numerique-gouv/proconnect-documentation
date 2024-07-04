# Qu'est ce que le protocole OpenID Connect ?

Le protocole OpenID Connect est au cœur du fonctionnement d'AgentConnect. C'est une couche d'identification basée sur protocole OAuth 2.0. Il permet à des *Clients* d'accéder à l'identité des *Utilisateurs*  par l'intermédiaire d'un *Serveur d'Autorisation* .

La spécification du protocole se trouve sur http://openid.net/connect/.

Pour une référence d'implémentation OpenID Connect voici le lien : https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth

## Les flux standards

En amont, le client s'inscrit (en général manuellement) auprès du provider. Il lui fournit une URL de callback (l'URL du client vers lequel l'internaute est redirigé une fois authentifié), aussi appelée `redirect_uri`, ainsi qu'une URL de redirection après déconnexion, aussi appelée `post_logout_redirect_uri`. En retour le provider donne au client un `client_id` et un `client_secret`.

Lorsque l'internaute clique sur le bouton d'authentification du client, le flux est le suivant :

![doc_fs_fca](https://user-images.githubusercontent.com/60473902/195838387-10aa22ef-f83f-4b12-abf7-dad3ec7828e4.png)

1. Le client fait une redirection **navigateur** vers le `authorization_endpoint` du provider avec son `client_id` et sa `redirect_uri`.
2. Le provider redirige alors l'internaute vers sa mire d'authentification.
3. Si l'internaute se connecte correctement, le provider renvoie l'internaute vers la `redirect_uri` **dans le navigateur**, avec en paramètre de requête un code d'autorisation `code`.
4. Le client fait un appel **depuis son serveur** vers le `token_endpoint` du provider avec le code d'autorisation reçu, en passant en paramètres de la requête son `client_id` et son `client_secret`.
5. Le provider retourne un `access_token` (une chaîne de caractères encodée en base64) et un `id_token` (sous la forme d'un JWT).
6. Le client fait un appel **depuis son serveur** vers le `userinfo_endpoint` du provider avec l'`access_token` reçu
7. Le provider renvoie les informations de l'internaute au client.
                        
La récupération des données doit être faite dans la suite immédiate des appels précédents (authentification et récupération du code). Le fait d'appeler ce Web service plus tard n'est aujourd'hui pas proposé.

