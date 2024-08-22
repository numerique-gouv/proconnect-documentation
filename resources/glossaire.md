[Accueil](../README.md) > [AgentConnect - Fournisseur de Service](../doc_fs.md) > Glossaire

___

# 📑 Glossaire

## 1. `AC_URL`

URL d’AgentConnect.

## 2. `FS_URL`

Votre URL, en tant que Fournisseur de Services.

## 3. `REDIRECT_URI`

Le callback du Fournisseur de Services, communiqué lors de son inscription auprès d’AgentConnect.

## 4. `POST_LOGOUT_REDIRECT_URI`

L'URL de redirection après la demande de déconnexion AgentConnect.

## 5. `CLIENT_ID`

Identifiant du Fournisseur de Services, communiqué lors de son inscription auprès de AgentConnect.

## 6. `CLIENT_SECRET`

Le secret du Fournisseur de Services, communiqué lors de son inscription auprès de AgentConnect.

## 7. `AUTHORIZATION_CODE`

Code retourné (dans l'URL) par AgentConnect au Fournisseur de Services lorsque ce dernier fait un appel sur le endpoint AC_URL/api/v2/authorize. Il est ensuite passé (dans le corps de la requête HTTP POST) lors de l'appel sur le endpoint AC_URL/api/v2/token.

## 8. `ACCESS_TOKEN`

Token retourné (dans le corps HTTP) par l'appel au endpoint AC_URL/api/v2/token. Il est ensuite passé lors de l'appel au endpoint AC_URL/api/v2/userinfo.

## 9. `SCOPES`

Liste des scopes demandés séparés par des espaces (donc par "%20"  ou "+" au format unicode dans l'URL).

Voici la liste supportée par AgentConnect :

    * openid : obligatoire, permet de demander l'identifiant technique de l'utilisateur au format OpenIDConnect
    * email : obligatoire, permet de récupérer l'adresse électronique de l’agent

Cette liste de scopes est définie par la norme OpenIDConnect.

## 10. `ID_TOKEN`

L'ID token est un jeton au format JWT qui est fourni en même temps que l'*access token* par l'appel au endpoint AC_URL/api/v2/token, il contient
- des information sur l'authentification
   - dates d'expiration, d'authentification, de création
   - des moyens de contrôle permettant de valider l'ID Token et l'Access Token
- des attributs ( claims ) sur l'utilisateurs, qui peuvent être :
   - standard : profile, email, address, phone, ...
   - personnalisés par le serveur OpenId Connect.

Le JSON doit contenir ces six clés : aud,exp,iat,iss,sub et nonce.

Exemple :

```json
{
    "aud":"895fae591ccae777094931e269e46447",
    "exp":1412953984,
    "iat":1412950384,
    "iss":"http://Agentconnect.gouv.fr",
    "sub":"YWxhY3JpdMOp",
    "idp":"AC",
    "nonce":"12344354597459"
}
```
Les champs *aud, exp, iat, iss, sub* sont des champs obligatoires de la norme OpenId Connect. Le *nonce* est un  paramètre obligatoirement envoyé lors de l'appel à `api/v2/authorize`. Le Fournisseur de Services doit impérativement vérifier que la valeur correspond bien à celle qu'il a envoyée, et qui doit être liée à la session de l'utilisateur.

Si vous utilisez une librairie pour transformer le json en JWT, il génèrera une chaîne de caractères constituée de 3 chaînes de caractères encodées en base64 séparées par des points (ex: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c).

## 11. `ID_TOKEN_HINT`

Objet JWT identique au format ID_TOKEN qui a été reçu lors de l'échange avec l'appel à AC_URL/api/v2/token et doit être passé en paramètre lors de l'appel à AC_URL/api/v2/logout.

## 12. `USERINFO`

Objet JWT retourné par l'appel au endpoint AC_URL/api/v2/userinfo. L'objet JWT est un objet JSON formaté et signé. Le JSON doit contenir ces six clés : aud,exp,iat,iss,sub.

Exemple :

```json
{
  "sub": "704e024229015d2bd47f7a5e5ab05b35c8336ab403c38022985f8cfadc86fe91",
  "uid": "1",
  "given_name": "Angela Claire Louise",
  "usual_name": "DUBOIS",
  "email": "test@abcd.com",
  "siren": "343293775",
  "siret": "34329377500037",
  "organizational_unit": "comptabilite",
  "belonging_population": "agent",
  "phone_number": "+331-12-44-45-23",
  "chorusdt:matricule": "USER_AGC",
  "chorusdt:societe": "CHT",
  "idp_id": "fia1v2",
  "idp_acr": "eidas1",
  "aud": "6925fb8143c76eded44d32b40c0cb1006065f7f003de52712b78985704f39950",
  "exp": 1668779720,
  "iat": 1668779660,
  "iss": "https://fca.integ01.dev-agentconnect.fr/api/v2"
}
```
Les champs *aud, exp, iat, iss, sub* sont des champs obligatoires de la norme OpenId Connect.

Si vous utilisez une librairie pour transformer le json en JWT, il génèrera une chaîne de caractères constituée de 3 chaînes de caractères encodées en base64 séparées par des points.

## 13. `STATE`

Champ obligatoire, généré aléatoirement par le Fournisseur de Services, que AgentConnect renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par le Fournisseur de Services. Il est utilisé afin d’empêcher l’exploitation de failles CSRF.

## 14. `NONCE`

Champ obligatoire, généré aléatoirement par le Fournisseur de Services que AgentConnect renvoie tel quel dans la réponse à l'appel à /token, pour être ensuite vérifié par le Fournisseur de Services. Il est utilisé pour empêcher les attaques par rejeu.

## 15. `SUB`

Identifiant technique (unique et stable dans le temps pour un individu donné) fourni par AgentConnect au Fournisseur de Services. Le SUB est présent dans l'IdToken retourné au Fournisseur de Services ainsi que dans les informations d'identité (/userinfo).
