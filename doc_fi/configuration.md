# Configurer OpenID Connect (OIDC) pour ProConnect en tant que Fournisseur d'Identité (FI)

## Test de la connexion à votre FI
Vous pouvez à tout moment tester l'intégration de votre FI à la fédération ProConnect. Vous trouverez les informations de test [ici](./test-configuration-fi.md).
En cas d'erreur, deux documents vous permettront d'analyser vos erreurs :
- [le troubleshooting](./troubleshooting-fi.md)
- [la liste des codes d'erreurs possibles renvoyés par ProConnect](https://github.com/france-connect/sources/blob/main/back/_doc/erreurs.md)

## Trouver la Discovery URL
La Discovery URL est une URL **publique** fournie par le FI qui expose un ensemble d'informations nécessaires à la bonne interaction avec les clients OIDC. Elle se termine nécessairement par `/.well-known/openid-configuration`.

À titre d'exemple, la Discovery URL de l'INSEE est la suivante : https://auth.insee.net/auth/realms/insee/.well-known/openid-configuration

Cette URL doit être conservée pour être envoyée à ProConnect par le FI une fois la configuration faite.

## Créer un client
Commencez par créer un client OIDC pour ProConnect. Vous pouvez choisir comme `client_id` "proconnect" par exemple. Pour le `client_secret`, vous pouvez le générer de votre côté ou à l'aide d'outils en ligne comme [randomgenerate.io](https://randomgenerate.io/random-string-generator).
Ces deux valeurs doivent être conservées de votre côté pour être envoyées à ProConnect une fois la configuration faite.

La `redirect_uri` (ou "adresse de redirection de connexion") à indiquer est la suivante :
https://PROCONNECT_DOMAIN/api/v2/oidc-callback 

Vous pouvez retrouver la valeur de PROCONNECT_DOMAIN qui vous correspond [ici](../resources/valeur_ac_domain.md). Si votre FI est présent sur le RIE et bénéficie de l'hybridge, il vous faut alors indiquer les `redirect_uri` correspondant aux domaines des réseaux RIE et Internet.

Il peut également vous être demandé de renseigner la "post_logout_redirect_uri" (ou "adresse de redirection post-déconnexion"). Dans ce cas, renseignez la suivante :
https://PROCONNECT_DOMAIN/api/v2/client/logout-callback

## Utiliser le paramètre `login_hint`
À l'appel au `authorization_endpoint`, ProConnect envoie en query param `login_hint`, qui contient l'email renseigné par l'utilisateur sur la mire ProConnect.
Pour simplifier le parcours de l'utilisateur, il est demandé au FI d'utiliser la valeur fournie pour pré-remplir le champ email de sa mire d'authentification lorsque cela est pertinent.

## Renseigner le claim `amr` 
Il est nécessaire de renseigner dans le claim `amr` la valeur correspondant au mode d'authentification utilisé. Cela permet, par exemple, aux Fournisseurs de Service d'épargner à l'usager le recours à une nouvelle authentification multi-facteur une fois retourné sur le FS.

Vous trouverez les valeurs possibles pour ce claim [ici](../resources/claim_amr.md).

## Configurer la signature des échanges entre ProConnect et le FI
Les appels aux endpoints de création de jeton (`/token`) et de récupération des informations utilisateur (`/user-info`) par ProConnect doivent être signés.
ProConnect gère trois algorithmes de signatures :
- Asymétrique : 

       - ES256 (EC + SHA256)
       - RS256 (RSA + SHA256)

- Symétrique : géré mais non recommandé

       - HS256 (HMAC + SHA256) 

Si vous sélectionnez un algorithme de signature asymétrique, les clefs de signatures doivent être disponible via la *JWKS URL* présente dans les méta-data de la *Discovery URL*. 


Les spécifications des algorithmes de signatures utilisés sont les suivants : 
* [JWA - https://tools.ietf.org/html/rfc7518](https://tools.ietf.org/html/rfc7518)
* [JWS - https://tools.ietf.org/html/rfc7515#appendix-A.3](https://tools.ietf.org/html/rfc7515#appendix-A.3)
* [JWE - https://tools.ietf.org/html/rfc7516#appendix-A.1](https://tools.ietf.org/html/rfc7516#appendix-A.1)

## Configurer les scopes
La liste des scopes demandés par ProConnect est la suivante :
| Scopes       |
| --- | 
| openid | 
| given_name |
| usual_name| 
| email |
| uid | 
| siren | 
| siret | 
| organizational_unit | 
| belonging_population | 
| phone |
| chorusdt |

Parmi ces champs, seuls sont obligatoires :
|Champs  | Description| Format |
|----  | ------ | ------ |
|given_name  |Prénoms séparés par des espaces (standard OpenIDConnect)| UTF-8 (standard OpenIDConnect)|
|usual_name |Nom de famille d'usage (par défaut = family_name)| UTF-8 |
|email  |Adresse courriel |UTF-8 (standard OpenIDConnect)|
|uid |Identifiant unique de l'agent auprès du FI| String (standard OpenIDConnect)|

Les autres champs, si vous ne possédez pas l'information correspondante dans votre annuaire, doivent être **ignorés**. (cf. [RFC OIDC](https://openid.net/specs/openid-connect-core-1_0.html#IDToken) : *Any Claims used that are not understood MUST be ignored.*)
Selon votre Fournisseur d'Identité, il est possible qu'il vous faille spécifier, pour chacun des scopes demandés, une valeur de retour nulle, indéfinie, ou simplement ignorée.

## Configurer le champ `acr`
Le champ `acr` renvoyé par le Fournisseur d'Identité doit valoir `eidas1`.

## Configurations spécifiques
Certains logiciels nécessitent des configurations particulières pour fonctionner avec ProConnect. Vous pouvez consulter ces spécificités si votre logiciel se trouve dans la liste ci-dessous :
- [LemonLDAP](./idp-configs/lemon-ldap.md)
