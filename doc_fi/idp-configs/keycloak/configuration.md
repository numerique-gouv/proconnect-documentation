# Configuration de Keycloak
## Étape 1 : connecter votre identity provider LDAP au Keycloak
### Ajout de l'Identity Provider LDAP
1. Aller dans User Federation
2. Cliquer sur Add new provider
3. Sélectionner LDAP

### Configuration

- Bind DN : compte admin du LDAP
- Bind credentials : mot de passe du compte admin

![Connection and authentication settings](ldap/connection-authentication-settings.png)

![LDAP searching and updating](ldap/ldap-searching-updating.png)

![synchronization settings](ldap/synchronization-settings.png)

![cache settings](ldap/cache-settings.png)

### Mapper les champs du LDAP aux champs du Keycloak

Dans l'écran de configuration de votre LDAP dans Keycloak, cliquez sur l'onglet Mappers :

![LDAP mappers](ldap/ldap-mappers.png)

Voici des exemples de mappers LDAP pour les champs given_name et email :

![LDAP mapper given_name](ldap/ldap-mapper-given_name.png)

![LDAP mapper email](ldap/ldap-mapper-email.png)

## Étape 2 : créer un client pour la connexion de ProConnect à votre Keycloak

### Créer un client
Client ID : `proconnect`
Valid redirect URIs : `https://PROCONNECT_DOMAIN/api/v2/oidc-callback`
où PROCONNECT_DOMAIN est défini [ici](../../../resources/valeur_ac_domain.md).

![General settings](client/general-settings.png)
![Capability config](client/capability-config.png)
![Logout settings](client/logout-settings.png)

#### Paramètre avancés
![Advanced settings 1](client/advanced/advanced-settings1.png)
![Advanced settings 2](client/advanced/advanced-settings2.png)
![Advanced settings 3](client/advanced/advanced-settings3.png)
![Fine grain open id connect configuration](client/advanced/fine-grain-openid-connect-configuration.png)
![Open ID Connect Compatiblity modes](client/advanced/openid-connect-compatibility-modes.png)

### Configurer les mappers
La valeur renvoyée par le LDAP doit être mappée aux valeurs renvoyées par le Keycloak à ProConnect.
ProConnect demande un ensemble de scopes au Fournisseur d'Identité, mais seuls un certains nombres d'entre eux sont obligatoires [liste ici à la section "Configurer les scopes"](../../configuration.md)
Trois cas :
- le champ doit être renvoyé à ProConnect, et est présent dans le LDAP
- le champ doit être renvoyé à ProConnect, et n'est présent dans le LDAP
- le champ est facultatif


#### Le champ doit être renvoyé à ProConnect, et *est* présent dans le LDAP
Exemple avec given_name : un mapping doit être effectué
![Onglet 1](client/scopes/given_name/onglet1.png)
![Onglet 2](client/scopes/given_name/onglet2.png)
![Onglet 2 - détails](client/scopes/given_name/onglet2details.png)
![Onglet 3](client/scopes/given_name/onglet3.png)

#### Le champ doit être renvoyé à ProConnect, et *n'est pas* présent dans le LDAP
Exemple avec siret : une valeur doit être renvoyée hardcodée
![Onglet 1](client/scopes/siret/onglet1.png)
![Onglet 2](client/scopes/siret/onglet2.png)
![Onglet 2 - détails](client/scopes/siret/onglet2details.png)
![Onglet 3](client/scopes/siret/onglet3.png)

#### Le champ est facultatif
Exemple avec chorusdt : une valeur peut être renvoyée hardcodée
![Onglet 1](client/scopes/chorusdt/onglet1.png)
![Onglet 2](client/scopes/chorusdt/onglet2.png)
![Onglet 2 - détails](client/scopes/chorusdt/onglet2details.png)
![Onglet 3](client/scopes/chorusdt/onglet3.png)

### Étape 3 : rassembler les informations à envoyer à ProConnect
### La discovery URL
La discovery URL est le lien « OpenID Endpoint Configuration »

### Le client ID et client secret
Le client ID a été créé à l'étape 2 : `proconnect`
Le client secret a été généré automatiquement à l'étape 2 lors de la création du client.

### Les algorithmes de signature
Celui-ci est spécifié dans les paramètres advancés de l'étape 2 : "créer un client pour la connexion de ProConnect à votre Keycloak".
Nous recommandons l'algorithme RS256 pour la signature de l'ID token et celle des user infos.
