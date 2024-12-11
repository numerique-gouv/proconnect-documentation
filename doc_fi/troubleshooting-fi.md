# 🆘 Troubleshooting (FI)
Le document ci-dessous récapitule les différents codes d'erreur que vous pourriez rencontrer lors de l'intégration de votre Fournisseur d'Identité.

Code erreur | Marche à suivre
-- | --
`Y00000 (write EPROTO C037E49CD87F0000:error:0A00010B:SSL routines:ssl3_get_record:wrong version number:../deps/openssl/openssl/ssl/record/ssl3_record.c:355)` | demandez à Agent Connect d'ouvrir le flux entre le Fournisseur d'Identité et Agent Connect. Si le blocage a lieu de votre côté, demandez à l'équipe support l'adresse IP du serveur Agent Connect, et demandez à votre DSI de l'autoriser
`Y020018` | le FI indique un niveau de sécurité différent de `eidas1`. Il vous faut renvoyer `eidas1` dans votre champ `acr`
`Y030025` | l'access_token a une durée de vie de 60 secondes, cette erreur peut survenir si vous testez le parcours manuellement au lieu de le faire via un script
`Y020025` | vous avez vraisemblablement été redirigé vers la redirect_uri du FS avec dans les query params : "error_description=Invalid+scopes". Si c'est le cas, configurez les scopes géré par votre FI comme précisé [ici](./configuration.md).
`Y020026` | l'appel au /token échoue. Il est possible que le FI renvoie un objet non signé ou un JWT signé avec un algorithme différent de celui configuré dans ProConnect.
`Y020030` | le FI indique une valeur du niveau de sécurité dans le champ `acr` qui n'est pas valide. Il vous faut renvoyer `eidas1` dans votre champ `acr`
`Y020027` | à l'appel au /user-info, le FI renvoie un objet non signé ou un JWT signé avec un algorithme différent de celui configuré dans ProConnect.
`Y500006` | à l'appel au /user-info, le FI renvoie un objet dont l'un ou plusieurs des champs ne matche pas avec ce qui est attendu
`Y020029` | à l'appel au /user-info, le FI ne renvoie pas le claim `sub` contenant l'identifiant unique de l'utilisateur
