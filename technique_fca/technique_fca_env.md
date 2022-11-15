
# Comment accéder aux différents environnements d'AgentConnect?

AgentConnect met à disposition deux environnements : 

- Intégration : à utiliser pour l'ensemble de vos développements et tests hors production,
- Production : à utiliser uniquement pour votre service en production.

## Accès à l'environnement d'intégration AgentConnect

Pour vous permettre de réaliser les développements liés à l'intégration d'AgentConnect, nous mettons à disposition un environnement d'intégration. Les accès à cet environnement se font à travers des clés qui sont communiquées au responsable technique par email et par sms. 

Pour utiliser l'environnement d'intégration, il faut au préalable avoir : 

1. Avoir fait une demande datapass et que celle-ci soit validée,
2. Avoir fait une demande de création d'un Fournisseur de Services en environnement d'intégration AgentConnect 

*Plateforme RIE*:

[Demande de création d'un Fournisseur de Services sur l'environnement d'intégration AgentConnect RIE](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-integration-fca-rie])

*Plateforme Internet*:

[Demande de création d'un Fournisseur de Services sur l'environnement d'intégration AgentConnect Internet](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-integration-fca-internet)),

3. Avoir reçu vos clés d'intégration.

Sur notre environnement d'intégration, vous pouvez utiliser le Fournisseur d'Identité "Démonstration" (il faut taper "démonstration" depuis la barre de recherche). Plusieurs IDP sont disponibles.

Pour les tests, le compte générique suivant peut être utilisé: 
 
Login : test
Mdp : 123

## Les adresses notre environnement d'intégration

Les adresses de notre environnement d'intégration sont les suivantes : 

*Environnement Internet*:

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://fca.integ01.dev-agentconnect.fr/api/v2/.well-known/openid-configuration | 
| Authorization | https://fca.integ01.dev-agentconnect.fr/api/v2/authorize |
| Token | https://fca.integ01.dev-agentconnect.fr/api/v2/token | 
| UserInfo | https://fca.integ01.dev-agentconnect.fr/api/v2/userinfo | 
| Logout | https://fca.integ01.dev-agentconnect.fr/api/v2/session/end | 

*Environnement RIE*:

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/.well-known/openid-configuration | 
| Authorization | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/authorize |
| Token | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/token | 
| UserInfo | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/userinfo | 
| Logout | https://fca.integ02.integ02.agentconnect.rie.gouv.fr/api/v2/session/end | 

## Accès à l'environnement de production d'AgentConnect

Pour avoir accès à l'environnement de production d'AgentConnect, il faut au préalable avoir : 

1. Reçu la qualification de vos développements par AgentConnect sur un environnement autre que votre production.

2. Demandé une mise en production via les formulaires à votre disposition sur sur le site [www.demarches-simplifiees.fr](https://www.demarches-simplifiees.fr/users/sign_in):

*Environnement RIE*:

[Demande de création d'un fournisseur de services sur l'environnement de production AgentConnect RIE](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-production-fca-rie)

*Environnement Internet*:

[Demande de création d'un fournisseur de services sur l'environnement de production AgentConnect Internet](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-production-fca-internet)

3. Configuré votre Fournisseur de Services de production AgentConnect avec les clés de production qui vous ont été remises au responsable technique par l'équipe AgentConnect . 

**:warning: Attention :** Il ne faut surtout pas utiliser les clés d'intégration que vous avez utilisées lors de vos développements avec votre Fournisseur de Services en production. Les clés d'intégration ne sont utilisables que sur l'environnement d'intégration AgentConnect. De même, il n'est pas possible d'utiliser des clés de production d'AgentConnect sur la plateforme d'intégration. 

## Les adresses notre environnement de production

Les adresses de notre environnement de production sont les suivantes : 

*Environnement Internet*:

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://auth.agentconnect.gouv.fr/api/v2/.well-known/openid-configuration | 
| Authorization | https://auth.agentconnect.gouv.fr/api/v2/authorize |
| Token | https://auth.agentconnect.gouv.fr/api/v2/token | 
| UserInfo | https://auth.agentconnect.gouv.fr/api/v2/userinfo | 
| Logout | https://auth.agentconnect.gouv.fr/api/v2/session/end | 

*Environnement RIE*:

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://auth.agentconnect.rie.gouv.fr/api/v2/.well-known/openid-configuration | 
| Authorization | https://auth.agentconnect.rie.gouv.fr/api/v2/authorize |
| Token | https://auth.agentconnect.rie.gouv.fr/api/v2/token | 
| UserInfo | https://auth.agentconnect.rie.gouv.fr/api/v2/userinfo | 
| Logout | https://auth.agentconnect.rie.gouv.fr/api/v2/session/end | 


---

Voir aussi : 
- [Quels démonstrateurs sont disponibles sur la plateforme intégration d'AgentConnect?](test_fca/test_fca_demonstrateur.md)