# Quels sont les certificats d'authentification ?

Lors de la récupération des données de l'identité pivot et des attributs complémentaires auprès du Fournisseur d'Identité, AgentConnect transmet un certificat SSL client RGS * Certigna. Ce certificat permet au Fournisseur d'Identité de s'assurer qu'AgentConnect est bien à l'origine de l'appel. Il doit donc être vérifié afin que l'authentification soit mutuelle.

Les endpoints concernés sont les endpoints `token`et `userinfo`.

---

Voir aussi : 
- [Qu'est ce que le protocole OpenID Connect ?](../technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](../technique_fca_fi/technique_fca_oidc_fi.md)
- [Quelles sont les données utilisateur que je dois fournir ?](../technique_fca_fi/donnees_utilisateurs_fi.md)
- [Quel est le détail du fonctionnement ?](../fonctionnement_fca_fi/details_fonctionnement_fi.md)

