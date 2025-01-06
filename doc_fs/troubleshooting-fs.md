# 🆘 Troubleshooting (FS)
Le document ci-dessous récapitule les différents codes d'erreur que vous pourriez rencontrer lors de l'intégration de votre Fournisseur de service.

Code erreur | Marche à suivre
-- | --
`Y030111` | si vous appelez bien le `end_session_endpoint` avec les paramètres indiqués [ici](./implementation_technique.md), alors il est probable que la `post_logout_redirect_uri` ne correspond pas à celle renseignée dans votre formulaire Démarches Simplifiées. Attention, cette URL doit être encodée pour être passée en query parameter, correspondre exactement à celle communiquée à ProConnect, et est sensible à la présence ou non du `/` final
`Y000404` | cette erreur est tout simplement une erreur 404 (route non trouvée). Vérifiez que l'URL que vous tentez d'appeler correspond bien à celle renseignées dans l'[implémentation technique](./implementation_technique.md)
`Y000400` | cette erreur est tout simplement une erreur 400 (mauvaise requête). Vérifiez que les paramètres envoyés à l'URL correspondent bien à ceux renseignés dans l'[implémentation technique](./implementation_technique.md)
`Y030110` | Le cookie de session n'a pas été trouvé dans la requête
`Y500015` | Le Fournisseur de Service n'est pas configuré dans ProConnect pour accepter les agents du secteur privé. Si vous êtes en intégration, ou en production et que votre demande d'autorisation du secteur privé dans le Démarches Simplifiées n'a pas été prise en compte, remontez-nous le problème et nous corrigerons rapidement la configuration.
