[Accueil](../README.md) > [ProConnect - Fournisseur de Service](README.md) > [Implémentation Technique](implementation_technique.md) > Test de la connexion d'un Fournisseur de Service

---


# Test de la connexion d'un Fournisseur de Service

Lorsque vous implémentez la connexion OIDC via ProConnect sur votre Fournisseur de Service, vous voudrez sans doute tester la connexion à votre Fournisseur de Service.

## 🔐 Fournisseur d'Identité de test
**En intégration** sur **Internet** et le **RIE**, ProConnect possède un Fournisseur d'Identité de test.

Pour tester la connexion sur votre Fournisseur de service :
- cliquez sur le bouton "S'identifier avec ProConnect" depuis votre Fournisseur de Service **en intégration**
- à l'arrivée sur la mire Agent Connect, entrez `test@fia1.fr`. Vous serez redirigés vers le FI de démonstration d'Agent Connect.
- entrez les informations suivantes de connexion :

Identifiant |  Mot de passe | Niveau de sécurité
--- | --- | ---
test | 123 | eidas1

- cliquez sur Valider. Vous devriez être redirigé vers votre Fournisseur de Service.

## 🔧 ProConnect Identité
**En intégration** sur **Internet** seulement, il vous est possible d'utiliser ProConnect Identité.

Pour tester la connexion sur votre Fournisseur de service :
- cliquez sur le bouton "S'identifier avec ProConnect" depuis votre Fournisseur de Service **en intégration**
- à l'arrivée sur la mire ProConnect, entrez `user@yopmail.com`. Vous serez redirigés vers la sandbox de ProConnect Identité (dont le design est identique à celui de ProConnect Fédération).
- indiquez `user@yopmail.com` également en mot de passe.
- sélectionnez l'organisation de rattachement "Direction Interministérielle du Numérique (DINUM)" Vous devriez être redirigé vers votre Fournisseur de Service.

Cette plateforme utilise de vraies données ouvertes de l'INSEE pour les données des organisations. Elle n’est cependant connectée à aucun environnement de production.

Avec toute adresse email, vous pouvez créer n’importe quel compte utilisateur en entrant n’importe quel numéro SIRET. Aussi, avec une adresse en `yopmail.com` et en `proton.me`, vous avez accès à une présélection d'organisations que vous pouvez rejoindre.

À noter que nous procédons de manière périodique à des resets de la base de données d'intégration, les comptes peuvent créés être supprimés. Il existe également [une liste de comptes « persistants »](https://github.com/numerique-gouv/moncomptepro/blob/master/scripts/fixtures.sql#L10) qui sont re-configurés à l'original plusieurs fois par semaines quel que soit l'usage qui en a été fait.