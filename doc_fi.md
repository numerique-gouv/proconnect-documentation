# Documentation Fournisseur d'Identité

Cette documentation est à destination des Fournisseurs d'Identité souhaitant intégrer AgentConnect.

## Je veux devenir Fournisseur d'Identité 

Vous souhaitez devenir Fournisseur d'Identité pour AgentConnect, voici les éléments à prendre en compte : 

- [Quelles sont les étapes pour devenir Fournisseur d'Identité ?](https://agentconnect.gouv.fr/fi#documentation-fi)
- [Qu'est-ce que la plateforme "Internet", la plateforme "RIE" et l'"Hybridge" ?](doc_fi/pilotage_fca/plateformes_fi.md)

## J'intègre mon Fournisseur d'Identité sur AgentConnect

### Je souhaite connaître le concept de base d'AgentConnect

- [Qu'est-ce que le protocole OpenID Connect ?](doc_fi/technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](doc_fi/technique_fca_fi/technique_fca_oidc_fi.md)
- [Quelles sont les données utilisateur que je dois fournir ?](doc_fi/technique_fca_fi/donnees_utilisateurs_fi.md)

### Je veux savoir comment fonctionne AgentConnect et comment implémenter mon Fournisseur d'Identité

- [Quel est le détail du fonctionnement ?](doc_fi/fonctionnement_fca_fi/details_fonctionnement_fi.md)
- [Quels sont les certificats d'authentification ?](doc_fi/fonctionnement_fca_fi/certificats_fi.md)
- [Qu'est-ce qu'eIDAS et comment utiliser les niveaux eIDAS en tant que Fournisseurs d'Identité ?](doc_fi/fonctionnement_fca_fi/fca_niveau_eidas_fi.md)
- [Quelles sont les adresses de l'environnement d'intégration et de production AgentConnect (endpoints) ?](doc_fi/production_fca_fi/adresses_fca_fi.md)

### Je veux connaître les différents environnements disponibles

- [Comment accéder aux différents environnements d'AgentConnect ?](doc_fi/test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](doc_fi/test_fca_fi/test_fca_demonstrateur_fi.md)

## Glossaire

Le glossaire relatif à OpenId Connect est spécifié à l'adresse [https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.1.2](https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.1.2)

#### **AC_URL:**  

URL d’AgentConnect. 

#### **FI_URL:** 

Votre URL, en tant que Fournisseur d'Identité.  

#### **CLIENT_ID:** 

Identifiant d'AgentConnect, communiqué par le Fournisseur d'Identité à AgentConnect lors de son inscription.

#### **CLIENT_SECRET:** 

Secret d'AgentConnect, communiqué par le Fournisseur d'Identité à AgentConnect lors de son inscription.

#### **AUTHZ_CODE:** 

Code retourné (dans l'URL) par le Fournisseur d'Identité à AgentConnect lorsque ce dernier fait un appel sur le endpoint FI_URL/user/authorize. Il est ensuite passé (dans le corps de la requête HTTP POST) lors de l'appel sur le endpoint FI_URL/user/token.

#### **ACCESS_TOKEN:** 

Token retourné (dans le corps HTTP) par l'appel au endpoint FI_URL/user/token. Il est ensuite passé lors de l'appel au endpoint FI_URL/api/user.

#### **REFRESH_TOKEN:** 

Token retourné (dans le corps HTTP) par l'appel au endpoint FI_URL/user/token. Il n'est pas utilisé par la suite.

#### **SCOPES:** 

Cela correspond au périmètre des données demandées.
Liste des scopes demandés séparés par des espaces (donc par "%20" ou "+" au format unicode dans l'URL).
	
Voici la liste supportée par AgentConnect :

    * openid : obligatoire, permet de demander l'identifiant technique de l'utilisateur au format OpenIDConnect
    * email : obligatoire, permet de récupérer l'adresse électronique de l’agent

Cette liste de scopes est définie par la norme OpenIDConnect.

#### **ID_TOKEN:** 

Objet JWT retourné par l'appel au endpoint AC_URL/api/v2/token. L'objet JWT est un objet JSON formaté et signé. Le JSON doit contenir ces six clés : aud,exp,iat,iss,sub et nonce.

Exemple :

```
{
    'aud':'895fae591ccae777094931e269e46447',
    'exp':1412953984,
    'iat':1412950384,
    'iss':http://Agentconnect.gouv.fr,
    'sub':YWxhY3JpdMOp,
    'idp':'AC',
    'nonce':'12344354597459'
}
```

Les champs aud, exp, iat, iss, sub sont des champs obligatoires de la norme OpenId Connect. Le nonce est un paramètre obligatoirement envoyé lors de l'appel à api/v2/authorize. Le Fournisseur de Services doit impérativement vérifier que la valeur correspond bien à celle qu'il a envoyée, et qui doit être liée à la session de l'utilisateur.

Si vous utilisez une librairie pour transformer le json en JWT, il génèrera une chaîne de caractères constituée de 3 chaînes de caractères encodées en base64 séparées par des points (ex: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c).

#### **USERINFO:**  

Objet JWT retourné par l'appel au endpoint AC_URL/api/v2/userinfo. L'objet JWT est un objet JSON formaté et signé. Le JSON doit contenir ces six clés : aud,exp,iat,iss,sub.

Exemple :

```
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

#### **STATE:** 

Champ obligatoire, généré aléatoirement par AgentConnect, que Fournisseur d'Identité renvoie tel quel dans la redirection qui suit l'authentification, pour être ensuite vérifié par AgentConnect. Il est utilisé afin d’empêcher l’exploitation de failles CSRF.

#### **NONCE:**	

Champ obligatoire, généré aléatoirement par AgentConnect que le Fournisseur d'Identité renvoie tel quel dans la réponse à l'appel à /token, pour être ensuite vérifié par AgentConnect. Il est utilisé pour empêcher les attaques par rejeu.

#### **UID (SUB FI):** 

Identifiant technique (unique et stable dans le temps pour un individu donné) fourni par le Fournisseur d'Identité à AgentConnect. Le sub doit être présent dans l'IdToken retourné à AgentConnect ainsi que dans les informations d'identité. Pour plus d'informations sur le rôle et la description du "sub", se référer à la documentation OpenID Connect http://openid.net/specs/openid-connect-basic-1_0.html (section 2.2)
