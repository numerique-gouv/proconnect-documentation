[Accueil](README.md) > ProConnect - Fournisseur de Service

---

# ProConnect - Fournisseur de Service

Vous souhaitez implémenter ProConnect sur votre site ? Vous êtes au bon endroit ! Cette documentation présente l'ensemble des informations à connaître.

## 1. 👩‍🏫 Préambule

Cette documentation est à destination des Fournisseurs de Services souhaitant intégrer ProConnect. ProConnect est implémenté sur deux plateformes, une dite "RIE" (l’agent se connecte depuis le RIE, à un FS RIE via un FI RIE) et une autre dite "Internet" (l'agent se connecte depuis Internet, à un FS Internet via un FI Internet). Toutefois il est possible d'utiliser "l'hybridge Internet/RIE", qui permet aux agents, depuis un Fournisseur de Service **sur Internet**, de s'identifier via un Fournisseur d'Identité **sur le RIE**.

## 2. ⚙️ Les étapes pour intégrer ProConnect

- [ ] Je me familiarise avec le flux OIDC - authorization code flow : voir [concepts de base](resources/flux_oidc.md). NB: si vous êtes Fournisseur de Service, ProConnect est votre _provider_ et vous êtes _client_.
- [ ] Je souhaite lancer les développements en test : je renseigne [le formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca). L'équipe me fournit alors mon `client_id` et mon `client_secret`, à l'adresse e-mail associée à la demande Démarches Simplifiées. Si vous êtes identifié via FranceConnect, il s'agit alors probablement de votre adresse e-mail personnelle.
- [ ] J’ai implémenté la cinématique OIDC (Authorization Code Flow): voir l'[implémentation technique](/doc_fs/implementation_technique.md)
- [ ] Je contractualise officiellement ma collaboration avec la DINUM en remplissant le [DataPass dédié](/doc_fs/datapass-fs.md)
- [ ] Le DataPass étant validé, j’ai récupéré mon `client_id` et mon `client_secret` de production en remplissant [le formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca) avec les informations de production
- [ ] Ouverture du service en production 🚀

Pour toute question technique, vous pouvez contacter l'équipe ProConnect par les deux canaux suivants :

- par mail à support.partenaires@agentconnect.gouv.fr
- [sur notre chaîne Tchap](https://www.tchap.gouv.fr/#/room/!kBghcRpyMNThkFQjdW:agent.dinum.tchap.gouv.fr)

---

## 3. 💻 FAQ

- [Quels changements dois-je effectuer pour passer d'AgentConnect à ProConnect ?](./doc_fs/changement-agentconnect-proconnect-fs.md)
- [Quelles sont les données que je peux récupérer par ProConnect sur les agents ?](doc_fs/donnees_fournies.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs ?](doc_fs/scope-claims.md)
- [Comment savoir avec quel Fournisseur d'Identité s'est authentifié mon utilisateur ?](doc_fs/connaitre-le-fi-utilise.md)
- [Comment spécifier à ProConnect que les usagers de mon FS doivent être redirigés directement vers un Fournisseur d'Identité spécifique ?](doc_fs/idp_hint_usage.md)
- [Comment récupérer des propriétés "custom" d'un Fournisseur d'Identité?](doc_fs/custom-scope.md)
- [Erreurs récurrentes](doc_fs/troubleshooting-fs.md)
- [Glossaire](resources/glossaire.md)
