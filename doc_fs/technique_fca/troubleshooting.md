[Accueil](https://github.com/france-connect/Documentation-AgentConnect/blob/main/README.md) > [AgentConnect - Fournisseur de Service](https://github.com/france-connect/Documentation-AgentConnect/blob/main/doc_fs.md) > Troubleshooting

___

# 🆘 Troubleshooting

VOus suivez l'installation d'AgentConnect, tout se passe bien, jusqu'à ce que vous tombez sur une erreur. Cette note vous donnera des clés de résolution pour vous débloquer.


Code erreur | Marche à suivre
-- | --
`Y00000 (write EPROTO C037E49CD87F0000:error:0A00010B:SSL routines:ssl3_get_record:wrong version number:../deps/openssl/openssl/ssl/record/ssl3_record.c:355)` | demandeZ à Agent Connect d'ouvrir le flux entre le Fournisseur d'Identité et Agent Connect. Si le blocage a lieu de votre côté, demandez à l'équipe support l'adresse IP du serveur Agent Connect, et demandez à votre DSI de l'autoriser
`Y020018` | le FI indique un niveau de sécurité différent de eidas1. Il vous faut indiquer eidas1 dans votre configuration
`Y030025` | l'access_token a une durée de vie de 60 secondes, cette erreur peut survenir si vous testez le parcours manuellement au lieu de le faire via un script
`Y020023` | le FS n'autorise pas la connexion via ce FI. Si vous pensez qu'il s'agit d'une erreur, veuillez nous contacter en nous précisant le FS auquel vous tentez de vous connecter et via quel FI.


