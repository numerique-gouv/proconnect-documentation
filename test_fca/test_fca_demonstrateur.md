
# Quels démonstrateurs sont disponibles sur la plateforme intégration d'AgentConnect ?

Pour vous permettre de réaliser les développements liés à l'intégration d'AgentConnect, nous mettons à disposition un environnement d'intégration. Les accès à cet environnement se font à travers des clés qui vous sont communiquées par l'équipe AgentConnect dans l'attente de la mise en place de votre espace partenaire. 

Sur notre environnement d'intégration, vous pourrez utiliser les fournisseurs d'identités de démonstration pour effectuer vos tests. 

Les adresses de notre environnement d'intégration sont les suivantes : 

## Compte test: 

Pour les tests, le compte générique est le suivant:
 
Login : test
Mdp : 123

## Environnement Internet : 

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://fca.integ01.dev-agentconnect.fr/api/v2/.well-known/openid-configuration  | 
| Authorization | https://fca.integ01.dev-agentconnect.fr/api/v2/authorize |
| Token | https://fca.integ01.dev-agentconnect.fr/api/v2/token | 
| UserInfo | https://fca.integ01.dev-agentconnect.fr/api/v2/userinfo  | 
| Logout |  https://fca.integ01.dev-agentconnect.fr/api/v2/session/end  | 

### Démonstrateurs Internet

*FI Internet* :

https://fia1v2.integ01.dev-agentconnect.fr

https://fia2v2.integ01.dev-agentconnect.fr

*FS Internet* :

https://fsa1v2.integ01.dev-agentconnect.fr

https://fsa2v2.integ01.dev-agentconnect.fr

https://fsa3v2.integ01.dev-agentconnect.fr


## Environnement RIE : 

 EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/.well-known/openid-configuration  | 
| Authorization | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/authorize |
| Token | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/token | 
| UserInfo | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/userinfo  | 
| Logout | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/session/end | 

### Démonstrateurs RIE

*FI RIE* :

https://fia1v2.integ02.agentconnect.rie.gouv.fr

https://fia2v2.integ02.agentconnect.rie.gouv.fr

 
*FS RIE* :

https://fsa1v2.integ02.agentconnect.rie.gouv.fr

https://fsa2v2.integ02.agentconnect.rie.gouv.fr

https://fsa3v2.integ02.agentconnect.rie.gouv.fr

---

Voir aussi : 
- [Comment accéder aux différents environnements d'AgentConnect ?](../technique_fca/technique_fca_env.md)
