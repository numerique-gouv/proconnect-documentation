# Quelles sont les adresses de l'environnement d'intégration et de production AgentConnect (endpoints) ?

En environnements d'intégration et de production AgentConnect, les endpoints sont disponibles en HTTPS.

## Intégration

### Environnement Internet : 

Les adresses de notre environnement d'intégration Internet sont les suivantes : 

| Adresse d'intégration | redirect_uri | post_logout_redirect_uri | URL de découverte des JWK |
| ------ | ------ | ------ | ------ |
| https://fca.integ01.dev-agentconnect.fr | https://fca.integ01.dev-agentconnect.fr/api/v2/oidc-callback/ | https://fca.integ01.dev-agentconnect.fr/api/v2/client/logout-callback | https://fca.integ01.dev-agentconnect.fr/api/v2/client/.well-known/keys |

**Démonstrateurs Internet**

*Fournisseurs d'Identité Internet* :

https://fia1v2.integ01.dev-agentconnect.fr

https://fia2v2.integ01.dev-agentconnect.fr

*Fournisseurs de Services Internet* :

https://fsa1v2.integ01.dev-agentconnect.fr

https://fsa2v2.integ01.dev-agentconnect.fr

https://fsa3v2.integ01.dev-agentconnect.fr


### Environnement RIE : 

Les adresses de notre environnement d'intégration RIE sont les suivantes : 

| Adresse d'intégration | redirect_uri | post_logout_redirect_uri | URL de découverte des JWK |
| ------ | ------ | ------ | ------ |
| https://fca.integ02.agentconnect.rie.gouv.fr | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/oidc-callback/ | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/client/logout-callback | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/client/.well-known/keys |

**Démonstrateurs RIE**

*Fournisseurs d'Identité RIE* :

https://fia1v2.integ02.agentconnect.rie.gouv.fr

https://fia2v2.integ02.agentconnect.rie.gouv.fr

*Fournisseurs de Services RIE* :

https://fsa1v2.integ02.agentconnect.rie.gouv.fr

https://fsa2v2.integ02.agentconnect.rie.gouv.fr

https://fsa3v2.integ02.agentconnect.rie.gouv.fr


## Production

### Environnement Internet : 

Les adresses de notre environnement de production Internet sont les suivantes : 

| Adresse de production | redirect_uri | post_logout_redirect_uri | URL de découverte des JWK |
| ------ | ------ | ------ | ------ |
| https://auth.agentconnect.gouv.fr | https://auth.agentconnect.gouv.fr/api/v2/oidc-callback | https://auth.agentconnect.gouv.fr/api/v2/client/logout-callback | https://auth.agentconnect.gouv.fr/api/v2/client/.well-known/keys |

**Démonstrateurs Internet**

*Fournisseur de Services Internet* :

https://fsa1v2.dev-agentconnect.fr/

### Environnement RIE : 

Les adresses de notre environnement de production RIE sont les suivantes : 

| Adresse de production | redirect_uri | post_logout_redirect_uri | URL de découverte des JWK |
| ------ | ------ | ------ | ------ |
| https://auth.agentconnect.rie.gouv.fr | https://auth.agentconnect.rie.gouv.fr/api/v2/oidc-callback | https://auth.agentconnect.rie.gouv.fr/api/v2/client/logout-callback | https://auth.agentconnect.rie.gouv.fr/api/v2/client/.well-known/keys |

**Démonstrateurs RE**

*Fournisseur de Services RIE* :

https://fsa1v2.agentconnect.rie.gouv.fr/

---

Voir aussi : 
- [Quelles sont les étapes pour devenir Fournisseur d'Identité ?](../pilotage_fca/pilotage_fca_etapes_fi.md)
- [Comment accéder aux différents environnements d'AgentConnect ?](../test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](../test_fca_fi/test_fca_demonstrateur_fi.md)
- [Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?](../implementation_fca_fi/spec_recette_fca_fi.md)
- [Comment faire qualifier mon implémentation ?](../implementation_fca_fi/recette_fi.md)
