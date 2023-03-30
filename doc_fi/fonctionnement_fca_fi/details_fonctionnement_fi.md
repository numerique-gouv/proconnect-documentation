# Quel est le détail du fonctionnement ?

## Fontionnenement 

![doc_fi_fca](https://user-images.githubusercontent.com/60473902/195837241-6c7f24f6-df00-4462-bb03-59c89223ab40.png)


Les access token fournis par le FI doivent être de préférence à usage unique ou si cela n'est pas possible avec une durée de vie très courte [https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.16.18](https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.16.18)

## Détail des flux

Les flux entre AgentConnect et le Fournisseur d'Identité respectent ce qui est défini dans la norme OpenId Connect. Pour plus de détails, il faut se référer à la [documentation OIDC - https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth)

---

Voir aussi : 
- [Qu'est ce que le protocole OpenID Connect ?](../technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](../technique_fca_fi/technique_fca_oidc_fi.md)
- [Quelles sont les données utilisateur que je dois fournir ?](../technique_fca_fi/donnees_utilisateurs_fi.md)
- [Quelles sont les adresses de l'environnement d'intégration et de production AgentConnect (endpoints) ?](../production_fca_fi/adresses_fca_fi.md)
- [Quels sont les certificats d'authentification ?](../fonctionnement_fca_fi/certificats_fi.md)
- [Qu'est ce qu'eIDAS et comment utiliser les niveaux eIDAS en tant que Fournisseurs d'Identité ?](../fonctionnement_fca_fi/fca_niveau_eidas_fi.md)
- [Comment accéder aux différents environnements d'AgentConnect ?](../test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](../test_fca_fi/test_fca_demonstrateur_fi.md)