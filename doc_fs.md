[Accueil](README.md) > AgentConnect - Fournisseur de Service

___

# AgentConnect - Fournisseur de Service


Vous souhaitez implémenter AgentConnect sur votre site ? Vous êtes au bon endroit ! Cette documentation présente l'ensemble des informations à connaître.

## 1. 👩‍🏫 Préambule

Cette documentation est à destination des Fournisseurs de Services souhaitant intégrer AgentConnect. AgentConnect est implémenté sur deux plateformes, une dite "RIE" (l’agent se connecte depuis le RIE, à un FS RIE via un FI RIE) et une autre dite "Internet" (l'agent se connecte depuis Internet, à un FS Internet via un FI Internet). Toutefois il est possible d'utiliser "l'hybridge Internet/RIE", qui permet aux agents, depuis un Fournisseur de Service **sur Internet**, de s'identifier via un Fournisseur d'Identité **sur le RIE**.


## 2. ⚙️ Les étapes pour intégrer AgentConnect

- [ ] Je me familiarise avec le flux OIDC - authorization code flow : voir [concepts de base](doc_fs/flux_oidc.md)
- [ ] Je souhaite lancer les développements en test : je renseigne [le formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca). L'équipe me fournit alors mon `client_id` et mon `client_secret`.
- [ ] J’ai implémenté la cinématique OIDC (Authorization Code Flow): voir l'[implémentation technique](doc_fs/implementation_technique.md)
- [ ]  Je contractualise officiellement ma collaboration avec la DINUM en remplissant le [DataPass dédié](./doc_fs/datapass-fs.md)
- [ ]  Le DataPass étant validé, j’ai récupéré mon `client_id` et mon `client_secret` de production en remplissant [le formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca) avec les informations de production
- [ ]  Ouverture du service en production 🚀

Pour toute question technique, vous pouvez contacter l'équipe AgentConnect par les deux canaux suivants :
- par mail à support.partenaires@agentconnect.gouv.fr
- [sur notre chaîne Tchap](https://www.tchap.gouv.fr/#/room/!kBghcRpyMNThkFQjdW:agent.dinum.tchap.gouv.fr)

___

## 3. 💻 FAQ
- [En tant que Fournisseur de Service, quelles sont les données que je peux récupérer par AgentConnect sur les agents ?](doc_fs/donnees_fournies.md)
- [En tant que Fournisseur de Service, comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs ? ](doc_fs/technique_fca_scope.md)
- [Erreurs récurrentes](doc_fi/troubleshooting.md)
- [Glossaire](doc_fs/glossaire.md)

