# Quelles sont les adresses de l'environnement de production AgentConnect ?

### Environnement Internet : 

Les adresses de notre environnement de production Internet sont les suivantes : 

- l'adresse de production sur Internet pour AgentConnect: https://auth.agentconnect.gouv.fr

- les URI de redirection à autoriser :

--> redirect_uri : https://auth.agentconnect.gouv.fr/api/v2/oidc-callback

--> post_logout_redirect_uri : https://auth.agentconnect.gouv.fr/api/v2/client/logout-callback

--> l'URL de découverte des JWK : https://auth.agentconnect.gouv.fr/api/v2/client/.well-known/keys


### Environnement RIE : 

Les adresses de notre environnement de production RIE sont les suivantes : 

- l'adresse de production sur le RIE pour AgentConnect: https://auth.agentconnect.rie.gouv.fr

- les URI de redirection à autoriser :

--> redirect_uri : https://auth.agentconnect.rie.gouv.fr/api/v2/oidc-callback

--> post_logout_redirect_uri : https://auth.agentconnect.rie.gouv.fr/api/v2/client/logout-callback

--> l'URL de découverte des JWK : https://auth.agentconnect.rie.gouv.fr/api/v2/client/.well-known/keys


---

Voir aussi : 
- [Quelles sont les étapes pour devenir Fournisseur d'Identité ?](doc_fi/pilotage_fca/pilotage_fca_etapes_fi.md)
- [Comment accéder aux différents environnements d'AgentConnect ?](doc_fi/test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](doc_fi/test_fca_fi/test_fca_demonstrateur_fi.md)
- [Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?](doc_fi/implementation_fca_fi/spec_recette_fca_fi.md)
- [Comment faire qualifier mon implémentation ?](doc_fi/implementation_fca_fi/recette_fi.md)
