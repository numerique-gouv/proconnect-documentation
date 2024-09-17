# Test de la configuration de votre Fournisseur d'Identité (FI)

## URL du Fournisseur de Service
Selon votre environnement et le réseau sur lequel votre Fournisseur d'Identité est, le Fournisseur de Service de test sera :
|               | Internet                          | RIE                                       |
|-|-|-|
| Intégration   | https://test.agentconnect.gouv.fr  | https://fsa1v2.integ02.agentconnect.rie.gouv.fr      |
| Production    | https://fsa1v2.dev-agentconnect.fr         | https://fsa1v2.agentconnect.rie.gouv.fr             |

## Protocole de test

- cliquez sur "S'identifier avec ProConnect"
- indiquez une adresse e-mail dont le domaine correspond à votre FI
- cliquez sur "Se connecter" : vous devriez être redirigé vers votre portail d'authentification
- connectez-vous avec des identifiants de recette sur votre FI
- vous devriez être redirigé vers l'écran principal, où devraient s'afficher les informations correspondant à votre utilisateur
