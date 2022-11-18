# Comment recevoir mes jetons de production ?

Vous souhaitez être Fournisseur de Services pour AgentConnect: 

- votre demande datapass a déjà été validée,
- vous avez implémenté AgentConnect sur vore plateforme de test, 
- la qualification de votre implémentation a été validée par l'équipe AgentConnect. 

Il est maintenant temps de passer à l'ultime étape suivante de demande de mise en production de votre Fournisseurs de Services. 

## Demander mes clés de production

Merci ne pas demander la mise en production de votre Fournisseur de Services tant que votre implémentation n'a pas été vérifiée et validée par un membre de notre équipe, comme expliqué dans les paragraphes [Quels sont les prérequis ainsi que les spécifications à respecter au moment de l'implémentation ?](../implementation_fca/spec_recette_fca.md) et [Comment faire qualifier mon implémentation ?](../recette_fca/recette.md)

L'équipe AgentConnect a mis en place des démarches sur le site [www.demarches-simplifiees.fr](https://www.demarches-simplifiees.fr/users/sign_in) pour demander la mise en production de votre service. 

Nous vous prions de bien vouloir y déposer votre demande afin qu'elle puisse être étudiée et traitée. Les démarches sont disponibles à l'adresse suivante : 

Environnement RIE: 

- [Demande de création d'un fournisseur de services sur l'environnement de production AgentConnect RIE](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-production-fca-rie)

Environnement Internet: 

- [Demande de création d'un fournisseur de services sur l'environnement de production AgentConnect Internet](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-production-fca-internet)


**:warning: ATTENTION: Les demandes envoyées directement par emails ne sont plus traitées.**

## Recevoir mes jetons de production


La clé de production de votre Fournisseur de Services sera transmise au responsable technique par email une fois la mise en production validée par notre équipe.
Le secret lui sera envoyé par SMS (au numéro renseigné dans le formulaire datapass) une fois la mise en production validée par notre équipe.

Les adresses de notre environnement de production sont les suivantes : 

*Environnement Internet* :

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://auth.agentconnect.gouv.fr/api/v2/.well-known/openid-configuration | 
| Authorization | https://auth.agentconnect.gouv.fr/api/v2/authorize |
| Token | https://auth.agentconnect.gouv.fr/api/v2/token | 
| UserInfo | https://auth.agentconnect.gouv.fr/api/v2/userinfo | 
| Logout | https://auth.agentconnect.gouv.fr/api/v2/session/end | 

*Environnement RIE* :

| EndPoint | Adresse |
| ------ | ------ |
| Discovery URL | https://auth.agentconnect.rie.gouv.fr/api/v2/.well-known/openid-configuration | 
| Authorization | https://auth.agentconnect.rie.gouv.fr/api/v2/authorize |
| Token | https://auth.agentconnect.rie.gouv.fr/api/v2/token | 
| UserInfo | https://auth.agentconnect.rie.gouv.fr/api/v2/userinfo | 
| Logout | https://auth.agentconnect.rie.gouv.fr/api/v2/session/end | 




---

Voir aussi : 
- [Quelles sont les étapes pour devenir Fournisseur de Services ?](../pilotage_fca/pilotage_fca_etapes.md)
- [Quel bouton AgentConnect intégrer et comment l'intégrer ?](../implementation_fca/bouton_fca.md)
- [Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?](../implementation_fca/spec_recette_fca.md)
- [Comment faire qualifier mon implémentation ?](../recette_fca/recette.md)
- [Comment recevoir mes jetons de production ?](../recette_fca/recette_cles_prod.md)