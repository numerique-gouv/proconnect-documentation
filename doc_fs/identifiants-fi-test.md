# Test de la connexion d'un Fournisseur de Service

Lorsque vous implémentez la connexion OIDC via ProConnect sur votre Fournisseur de Service, vous voudrez sans doute tester la connexion à votre Fournisseur de Service.

## Fournisseur d'Identité de test
**En intégration** sur **Internet** et le **RIE**, ProConnect possède un Fournisseur d'Identité de test.

Pour tester la connexion sur votre Fournisseur de service :
- cliquez sur le bouton "S'identifier avec ProConnect" depuis votre Fournisseur de Service **en intégration**
- à l'arrivée sur la mire Agent Connect, entrez `test@fia1.fr`. Vous serez redirigés vers le FI de démonstration d'Agent Connect.
- entrez les informations suivantes de connexion :

Identifiant |  Mot de passe | Niveau de sécurité
--- | --- | --- 
test | 123 | eidas1

- cliquez sur Valider. Vous devriez être redirigé vers votre Fournisseur de Service.

## MonComptePro
**En intégration** sur **Internet** seulement, il vous est possible d'utiliser MonComptePro.

Pour tester la connexion sur votre Fournisseur de service :
- cliquez sur le bouton "S'identifier avec ProConnect" depuis votre Fournisseur de Service **en intégration**
- à l'arrivée sur la mire Agent Connect, entrez `user@yopmail.com`. Vous serez redirigés vers la sandbox de MonComptePro (dont le design est identique à celui de ProConnect).
- indiquez `user@yopmail.com` également en mot de passe.
- sélectionnez l'organisation de rattachement "Direction Interministérielle du Numérique (DINUM)" Vous devriez être redirigé vers votre Fournisseur de Service.
