# Comment préremplir l'adresse email dans la mire de connexion ProConnect ?

En tant que Fournisseur de Service (FS), vous pouvez faciliter l'authentification de vos usagers en préremplissant automatiquement leur adresse email dans la mire de connexion ProConnect.

Pour ce faire :

## 1. Déterminer l'adresse email de l'usager

Vous devez connaître l'adresse email de l'usager que vous souhaitez préremplir. Cette information peut provenir :

- Des données utilisateur stockées lors d'une précédente connexion
- D'un formulaire rempli par l'utilisateur avant de cliquer sur le bouton ProConnect
- D'autres sources de données légitimes dont vous disposez

## 2. Passer cette valeur au paramètre `login_hint` lors de l'appel au `authorization_endpoint`

L'appel à ce endpoint est détaillé [ici](./implementation_technique.md).

Exemple d'URL avec le paramètre `login_hint` :

```http
https://PROCONNECT_DOMAIN/api/v2/authorize?response_type=code&client_id=<CLIENT_ID>&redirect_uri=<REDIRECT_URI>&scope=<SCOPES>&state=<STATE>&nonce=<NONCE>&login_hint=utilisateur@exemple.fr
```

## 3. Comportement attendu

Lorsque l'utilisateur est redirigé vers la mire de connexion ProConnect, le champ d'adresse email sera automatiquement rempli avec la valeur fournie dans le paramètre `login_hint`.

## Remarques importantes

- Ce paramètre est entièrement optionnel
- L'utilisateur peut toujours modifier l'adresse email préremplie s'il souhaite se connecter avec un autre compte