# Comment recevoir mes jetons de production ?

Vous souhaitez être Fournisseur de Services pour AgentConnect:

- votre demande datapass a déjà été validée,
- vous avez implémenté AgentConnect sur vore plateforme de test,
- la qualification de votre implémentation a été validée par l'équipe AgentConnect.

Il est maintenant temps de passer à l'ultime étape suivante de demande de mise en production de votre Fournisseurs de Services.

## Demander mes clés de production

L'équipe AgentConnect a mis en place des démarches sur le site [www.demarches-simplifiees.fr](https://www.demarches-simplifiees.fr/users/sign_in) pour demander la mise en production de votre service.

Nous vous prions de bien vouloir y déposer votre demande afin qu'elle puisse être étudiée et traitée. La démarche est disponible à l'adresse suivante :

- [Demande de création d'un Fournisseur de Services sur AgentConnect](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca)


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
