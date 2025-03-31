[Accueil](README.md) > ProConnect - Fournisseur de Service

---

# ProConnect - Fournisseur de Service

Vous souhaitez implémenter ProConnect sur votre site ? Vous êtes au bon endroit ! Cette documentation présente l'ensemble des informations à connaître.

## 1. 👩‍🏫 Préambule

Cette documentation est à destination des Fournisseurs de Services souhaitant intégrer ProConnect. ProConnect est implémenté sur deux plateformes, une dite "RIE" (l’agent se connecte depuis le RIE, à un FS RIE via un FI RIE) et une autre dite "Internet" (l'agent se connecte depuis Internet, à un FS Internet via un FI Internet). Toutefois il est possible d'utiliser "l'hybridge Internet/RIE", qui permet aux agents, depuis un Fournisseur de Service **sur Internet**, de s'identifier via un Fournisseur d'Identité **sur le RIE**.

Avant toute chose, vérifiez votre [éligibilité à intégrer le bouton ProConnect sur vos services](./eligibilite_installation.md).

## 2. ⚙️ Les étapes pour intégrer ProConnect

- [ ] Je me familiarise avec le flux OIDC - authorization code flow : voir [concepts de base](../resources/flux_oidc.md). NB: si vous êtes Fournisseur de Service, ProConnect est votre _provider_ et vous êtes _client_.
- [ ] Je définis mon parcours utilisateur pour la connexion : voir [nos recommandations](./recommandation_parcours.md)
- [ ] Je souhaite lancer les développements en test : je renseigne [le formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca). L'équipe me fournit alors mon `client_id` et mon `client_secret` dans les **2 jours ouvrés**, à l'adresse e-mail associée à la demande Démarches Simplifiées. Si vous êtes identifié via FranceConnect, il s'agit alors probablement de votre adresse e-mail personnelle.
- [ ] J’ai implémenté la cinématique OIDC (Authorization Code Flow): voir l'[implémentation technique](./implementation_technique.md)
- [ ] Je contractualise officiellement ma collaboration avec la DINUM en remplissant le [DataPass dédié](./datapass-fs.md). Je peux passer à l'étape suivante même si le Datapass n'est pas encore complété ou approuvé pour gagner du temps. Après complétude, le Datapass me revient signé dans les **2 jours ouvrés**.
- [ ] Je remplis [le formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca) avec les informations de production. Après complétude, je reçois mon `client_id` et mon `client_secret` de production dans les **2 jours ouvrés**.
- [ ] Ouverture du service en production 🚀
- [ ] Je signale à l'équipe ProConnect que je souhaite apparaître sur [sa liste de services connectés](https://www.proconnect.gouv.fr/services). Si la description du service rendue a bien été remplie dans le Démarches Simplifiées (avec verbe à l'infinitif au début de la description), l'équipe mettra à jour le site.

Pour toute question technique, vous pouvez contacter l'équipe ProConnect par les deux canaux suivants :

- par mail à support+partenaires@proconnect.gouv.fr
- [sur notre chaîne Tchap](https://www.tchap.gouv.fr/#/room/!kBghcRpyMNThkFQjdW:agent.dinum.tchap.gouv.fr)

---

## 3. 💻 FAQ

- [Quels changements dois-je effectuer pour passer d'AgentConnect à ProConnect ?](./changement-agentconnect-proconnect-fs.md)
- [Quelles sont les données que je peux récupérer par ProConnect sur les agents ?](./donnees_fournies.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs ?](./scope-claims.md)
- [Comment savoir avec quel Fournisseur d'Identité s'est authentifié mon utilisateur ?](./connaitre-le-fi-utilise.md)
- [Comment spécifier à ProConnect que les usagers de mon FS doivent être redirigés directement vers un Fournisseur d'Identité spécifique ?](./idp_hint_usage.md)
- [Comment récupérer des propriétés "custom" d'un Fournisseur d'Identité?](./custom-scope.md)
- [Erreurs récurrentes](./troubleshooting-fs.md)
- [Glossaire](../resources/glossaire.md)
