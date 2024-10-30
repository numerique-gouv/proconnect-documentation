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

## ProConnect Identité
**En intégration** sur **Internet** seulement, il vous est possible d'utiliser ProConnectIdentité avec des identités de test.

Pour tester la connexion sur votre Fournisseur de service :
- cliquez sur le bouton "S'identifier avec ProConnect" depuis votre Fournisseur de Service **en intégration**
- à l'arrivée sur la mire Agent Connect, entrez `user@yopmail.com`. Vous serez redirigés vers la sandbox de MonComptePro (dont le design est identique à celui de ProConnect).
- indiquez `user@yopmail.com` également en mot de passe.
- sélectionnez l'organisation de rattachement "Direction Interministérielle du Numérique (DINUM)" Vous devriez être redirigé vers votre Fournisseur de Service.

### Ajouter un compte de test à ProConnect Identité en intégration
Il existe un ensemble de comptes de test présents sur ProConnect Identité.
Ces users sont présents dans un ensemble de fixtures dans le fichier suivant : https://github.com/numerique-gouv/moncomptepro/blob/master/scripts/fixtures.sql#L6

Si vous souhaitez ajouter un user à ProConnect Identité et le lier au SIRET d'une entreprise, il vous est possible de soumettre une Pull Request sur ce repository.
