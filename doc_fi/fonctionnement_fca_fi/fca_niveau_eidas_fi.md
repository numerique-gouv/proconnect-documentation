# Qu'est ce qu'eIDAS et comment utiliser les niveaux eIDAS en tant que Fournisseurs d'Identité ?

## Qu'est ce que le règlement eIDAS ? 

Pour plus d'informations à ce sujet nous vous invitons à consulter les liens suivants :

- [Présentation du règlement eIDAS par l'ANSSI](https://www.ssi.gouv.fr/administration/reglementation/confiance-numerique/le-reglement-eidas/#:~:text=Substantiel%20%3A%20%C3%A0%20ce%20niveau%2C%20l,'alt%C3%A9ration%20de%20l'identit%C3%A9.)
- [FAQ eIDAS de l'ANSSI](https://www.ssi.gouv.fr/uploads/2017/01/eidas_faq_anssi.pdf)

## Utiliser les niveaux eIDAS en tant que Fournisseur d'Identité

AgentConnect s'inspire du règlement eIDAS pour définir les différents niveaux de sécurité dans les échanges avec les Fournisseurs d'Identité et les Fournisseurs de Services. 

Dans le code AgentConnect les niveaux suivants sont définis :

* eidas1 : Niveau faible
* eidas2 : Niveau renforcé
* eidas3 : Niveau élevé

Le Fournisseur d'Identité doit signifier à AgentConnect avec quel niveau eIDAS l'authentification de l'agent s'est faite. 

Dans le cadre du Fournisseur d'Identité, cela se traduit par le fait de positionner le claim "acr" dans l'ID Token renvoyé au client (http://openid.net/specs/openid-connect-core-1_0.html#rfc.section.2).

Le claim acr retourné dans l'ID Token peut être :

* eidas1 : Niveau faible
* eidas2 : Niveau renforcé
* eidas3 : Niveau élevé

Toutefois, attention, actuellement les Fournisseurs de Services ne peuvent demander qu'un niveau 1, soit un niveau dit faible AgentConnect soit acr_values=eidas1. 

Uniquement le niveau 1 est supporté par AgentConnect pour le moment.


---

Voir aussi : 
- [Qu'est ce que le protocole OpenID Connect ?](../technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](../technique_fca_fi/technique_fca_oidc_fi.md)
- [Quelles sont les données utilisateur que je dois fournir ?](../technique_fca_fi/donnees_utilisateurs_fi.md)
- [Quels sont les endpoints sur AgentConnect ?](../fonctionnement_fca_fi/endpoints_fi.md)
- [Quel est le détail du fonctionnement ?](../fonctionnement_fca_fi/details_fonctionnement_fi.md)
- [Quel est le détail des flux ?](../fonctionnement_fca_fi/details_flux_fi.md)
- [Quels sont les certificats d'authentification ?](../fonctionnement_fca_fi/certificats_fi.md)
- [Comment accéder aux différents environnements d'AgentConnect ?](../test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](../test_fca_fi/test_fca_demonstrateur_fi.md)