# 🆘 Troubleshooting (FI)
Le document ci-dessous récapitule les différents codes d'erreur que vous pourriez rencontrer lors de l'intégration de votre Fournisseur d'Identité.

Code erreur | Marche à suivre
-- | --
`Y000000` | ProConnect ne parvient pas à effectuer l'appel vers le endpoint concerné. Cette erreur survient généralement lorsque le serveur ou le endpoint du FI est down, ou bien que le flux n'est pas ouvert entre les deux serveurs (pare-feu, WAF, etc.)
`Y020018` | le FI indique un niveau de sécurité différent de `eidas1`. Il vous faut renvoyer `eidas1` dans votre champ `acr`
`Y500017` | la configuration du FI est désactivée côté ProConnect. Il nous faut l'activer 
`Y030025` | l'access_token a une durée de vie de 60 secondes, cette erreur peut survenir si vous testez le parcours manuellement au lieu de le faire via un script
`Y020025` | vous avez vraisemblablement été redirigé vers la redirect_uri du FS avec dans les query params : "error_description=Invalid+scopes". Si c'est le cas, configurez les scopes géré par votre FI comme précisé [ici](./configuration.md).
`Y020026` | l'appel au /token échoue. Il est possible que le FI renvoie un objet non signé ou un JWT signé avec un algorithme différent de celui configuré dans ProConnect. Il est aussi possible que l'authentification de notre serveur auprès du FI ait échoué (mauvais credentials, mauvaise client authentication method,...)
`Y020030` | le FI indique une valeur du niveau de sécurité dans le champ `acr` qui n'est pas valide. Il vous faut renvoyer `eidas1` dans votre champ `acr`
`Y020027` | à l'appel au /user-info, le FI renvoie un objet non signé ou un JWT signé avec un algorithme différent de celui configuré dans ProConnect.
`Y500006` | à l'appel au /user-info, le FI renvoie un objet dont l'un ou plusieurs des champs ne matche pas avec ce qui est attendu (cf. [contraintes sur les scopes renvoyés](./configuration.md#configurer-les-scopes))
`Y020029` | à l'appel au /user-info, le FI ne renvoie pas le claim `sub` contenant l'identifiant unique de l'utilisateur
