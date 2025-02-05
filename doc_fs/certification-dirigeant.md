# 💼 Cas de l'authentification d'un rôle (dirigeant, élu, etc.)

Ce document décrit la manière d'utiliser ProConnect en tant que **fournisseur OpenID** afin de récupérer une identité de niveau « certifié dirigeant ». Nous nous appuyons sur les spécifications [OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html).

> [!CAUTION]
> Cette documentation permet de lancer les développements pour une application. Le paramètre ne fait actuellement aucune vérification et renverra toujours `true`. Celui-ci sera fonctionnel au T2 2025. Vérifiez avec nous avant de lancer votre application en production.


## 🤔 1. Qu'est-ce que la certification dirigeant ?

Parmi les niveaux d'authentification disponibles, ProConnect propose notamment le niveau de certification suivant :

* `certification-dirigeant` : prouve le statut de dirigeant au sein d'une organisation.

Cette certification s'obtient en demandant explicitement un niveau de garantie (acr) spécifique dans le cadre d'un flux OpenID Connect.

## 2. ⚙️ Configuration du paramètre `claims`

Pour demander à l'OP ProConnect de retourner un **ID token** contenant l'**acr** du niveau « certification-dirigeant », vous devez inclure le paramètre `claims` dans la requête à l'endpoint d'**autorisation** (souvent nommé `/authorize`).

Voici un exemple de format JSON à inclure (après encodage URL si nécessaire) :

```json
{
  "claims": {
    "id_token": {
      "acr": {
        "essential": true,
        "value": "https://proconnect.gouv.fr/assurance/certification-dirigeant"
      }
    }
  }
}
```

### 2.1. Détails du paramètre

* `claims`: Paramètre défini par la spécification OpenID Connect qui permet de **demander des claims spécifiques** dans l'ID token (ou le token d'accès).
* `id_token`: Section dédiée aux réclamations (claims) que vous souhaitez intégrer à l'ID token.
* `acr`: Réclamation (claim) standard [OpenID Connect](https://openid.net/specs/openid-connect-core-1_0.html#acrSemantics) permettant de préciser le niveau d'authentification souhaité.


L'attribut `essential: true` indique que la valeur spécifiée pour `acr` est **obligatoire** pour votre service.La propriété `value` doit être égale à l'URL qui identifie le niveau d'assurance souhaité, dans cet exemple :

```
"https://proconnect.gouv.fr/assurance/certification-dirigeant"
```

## ✉️ 3. Envoi de la requête d'autorisation

Selon votre bibliothèque OpenID Connect (client OpenID) ou votre framework, vous devrez :


1. **Inclure** le bloc `claims` dans les paramètres de l'URL `/authorize` (pour un flux implicite, hybrid ou code).
2. **Encoder** correctement la valeur JSON dans le paramètre `claims` (URL-encoding).

Par exemple, une requête d'autorisation (simplifiée) pourrait ressembler à :

```http
GET /authorize?
  response_type=code&
  client_id=VOTRE_CLIENT_ID&
  scope=openid&
  redirect_uri=https%3A%2F%2Fvotre-application.fr%2Fcallback&
  claims=%7B%22id_token%22%3A%7B%22acr%22%3A%7B%22essential%22%3Atrue%2C%22value%22%3A%22https%3A%2F%2Fproconnect.gouv.fr%2Fassurance%2Fcertification-dirigeant%22%7D%7D%7D
```

*(Ici,* `claims=%7B%22id_token%22%3A...` correspond à la version encodée URL du JSON décrit plus haut.)

## 🔏 4. Traitement par ProConnect

Lorsque ProConnect reçoit cette requête :


1. Il **vérifie** la présence du paramètre `claims`.
2. Il **contrôle** la validité de la demande (client autorisé, scope, etc.).
3. Il **authentifie** l'utilisateur et **valide** son statut (dans ce cas, la certification dirigeant).
4. Il **retourne** un ID token avec le claim `acr` contenant la valeur `https://proconnect.gouv.fr/assurance/certification-dirigeant`, **si l'utilisateur possède ce niveau de certification** et que la politique de confidentialité et de sécurité le permet.

### 4.1. Exemple d'ID token (partiel)

```json
{
  "iss": "https://proconnect.gouv.fr",
  "aud": "VOTRE_CLIENT_ID",
  "exp": 1700000000,
  "iat": 1699999400,
  "sub": "248289761001",
  "acr": "https://proconnect.gouv.fr/assurance/certification-dirigeant"
}
```

## 📚 5. Références

* [OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html)
* [Utilisation du paramètre ](https://openid.net/specs/openid-connect-core-1_0.html#ClaimsParameter)`claims`
* [Semantics of the ](https://openid.net/specs/openid-connect-core-1_0.html#acrSemantics)`acr` Claim


