# 🆘 Troubleshooting (FS)
Le document ci-dessous récapitule les différents codes d'erreur que vous pourriez rencontrer lors de l'intégration de votre Fournisseur de service.

Code erreur | Marche à suivre
-- | --
`Y030111` | si vous appelez bien le `end_session_endpoint` avec les paramètres indiqués [ici](./implementation_technique.md), alors il est probable que la `post_logout_redirect_uri` ne correspond pas à celle renseignée dans votre formulaire Démarches Simplifiées. Attention, cette URL doit être encodée pour être passée en query parameter, correspondre exactement à celle communiquée à AgentConnect, et est sensible à la présence ou non du `/` final
