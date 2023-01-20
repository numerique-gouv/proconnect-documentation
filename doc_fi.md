Documentation Fournisseur d'Identité

---

Vous souhaitez devenir Fournisseur d'Identité sur AgentConnect ? Vous êtes au bon endroit ! Cette documentation présente l'ensemble des informations à connaitre.

# Préambule

Cette documentation est à destination des Fournisseurs d'Identité souhaitant intégrer AgentConnect. 
AgentConnect est implémenté sur deux plateformes, une dite "full RIE" (l’agent se connecte depuis le RIE, à un FS RIE via un FI RIE) et une autre dite "full Internet" (l'agent se connecte depuis Internet, à un FS Internet via un FI Internet).
Toutefois il est possible de communiquer entre les deux plateformes grâce à "l'hybridge Internet/RIE" (l'agent se connecte depuis Internet, à un Fournisseur de Services Internet via un FI RIE).

# Je veux devenir Fournisseur d'Identité 

Vous souhaitez devenir Fournisseur d'Identité pour AgentConnect, voici les éléments à prendre en compte : 

- [Quelles sont les étapes pour devenir Fournisseur d'Identité ?](doc_fi/pilotage_fca/pilotage_fca_etapes_fi.md)
- [Quels sont les acteurs à impliquer dans l'intégration d'AgentConnect ?](doc_fi/pilotage_fca/pilotage_fca_demarches_acteurs_fi.md)
- [Qu'est-ce que la plateforme "Full Internet", la plateforme "Full RIE" et l'"Hybridge" ?](doc_fi/pilotage_fca/plateformes_fi.md)
- [Comment accéder au formulaire datapass ?](doc_fi/pilotage_fca/datapass_fi.md)

# J'intègre mon Fournisseur d'Identité sur AgentConnect

## Je souhaite connaître le concept de base d'AgentConnect

- [Qu'est ce que le protocole OpenID Connect ?](doc_fi/technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](doc_fi/technique_fca_fi/technique_fca_oidc_fi.md)
- [Quelles sont les données utilisateur que je dois fournir ?](doc_fi/technique_fca_fi/donnees_utilisateurs_fi.md)

## Je veux savoir comment fonctionne AgentConnect et comment implémenter mon Fournisseur d'Identité

- [Quels sont les endpoints sur AgentConnect ?](doc_fi/fonctionnement_fca_fi/endpoints_fi.md)
- [Quel est le détail du fonctionnement ?](doc_fi/fonctionnement_fca_fi/details_fonctionnement_fi.md)
- [Quel est le détail des flux ?](doc_fi/fonctionnement_fca_fi/details_flux_fi.md)
- [Quels sont les certificats d'authentification ?](doc_fi/fonctionnement_fca_fi/certificats_fi.md)
- [Qu'est ce qu'eIDAS et comment utiliser les niveaux eIDAS en tant que Fournisseurs d'Identité ?](doc_fi/fonctionnement_fca_fi/fca_niveau_eidas_fi.md)

## Je veux connaître les différents environnements disponibles

- [Comment accéder aux différents environnements d'AgentConnect ?](doc_fi/test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](doc_fi/test_fca_fi/test_fca_demonstrateur_fi.md)

# Je souhaite faire qualifier mon Fournisseur d'Identité AgentConnect

- [Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?](doc_fi/implementation_fca_fi/spec_recette_fca_fi.md)
- [Comment faire qualifier mon implémentation ?](doc_fi/implementation_fca_fi/recette_fi.md)

# Je souhaite mettre mon Fournisseur de Services en production

- [Quelles sont les adresses de l'environnement de production AgentConnect ?](doc_fi/production_fca_fi/adresses_prod_fca_fi.md)

# Glossaire

Le glossaire relatif à OpenId Connect est spécifié à l'adresse [https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.1.2](https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.1.2)
