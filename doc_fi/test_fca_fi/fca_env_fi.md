
# Comment accéder aux différents environnements d'AgentConnect ?

AgentConnect met à disposition deux environnements : 

- Intégration : à utiliser pour l'ensemble de vos développements et tests hors production,
- Production : à utiliser uniquement pour votre service en production.

## Accès à l'environnement d'intégration AgentConnect

Pour vous permettre de réaliser les développements liés à l'intégration d'AgentConnect, nous mettons à disposition un environnement d'intégration. 

Pour utiliser l'environnement d'intégration, il faut au préalable avoir : 

1. Avoir fait une demande datapass et que celle-ci soit validée :
[Demande DataPass](https://datapass.api.gouv.fr/agent-connect-fi)

2. Avoir fait une demande de création d'un Fournisseur de Services en environnement d'intégration AgentConnect sur le site [www.demarches-simplifiees.fr](https://www.demarches-simplifiees.fr/users/sign_in):
[Demande de création d'un Fournisseur d'Identité AgentConnect](https://www.demarches-simplifiees.fr/commencer/demande-creation-fi-fca)


## Accès à l'environnement de production d'AgentConnect

Pour avoir accès à l'environnement de production d'AgentConnect, il faut au préalable avoir : 

1. Validé vos développements sur un environnement autre que votre production. Les deux scénarios à tester sur le démonstrateur FS sont les suivants :
- se connecter à votre fournisseur d'identité et s'assurer que la redirection vers le FS vous affiche bien les informations d'identité récupérées depuis votre FI
- se déconnecter depuis le FS, puis re-cliquer sur le bouton de connexion Agent Connect : s'assurer que l'utilisateur se voit bien re-demander ses identifiants de connexion.

2. Demandé une mise en production via le formulaire à votre disposition sur le site [www.demarches-simplifiees.fr](https://www.demarches-simplifiees.fr/users/sign_in) :
[Demande de création d'un Fournisseur d'Identité AgentConnect](https://www.demarches-simplifiees.fr/commencer/demande-creation-fi-fca)
