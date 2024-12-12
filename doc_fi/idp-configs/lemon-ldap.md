# Configuration spécifique à LemonLDAP

## Service OpenID Connect
### Sécurité
### Envoyer tous les attributs exportés
Activer

### Contexte d'authentification
Il vous faut créer un mapping :
| Clef  | Valeur|
|----  | ------ |
|eidas1  | 1 |
|eidas2  | 2 |
|eidas3  | 3 |


Le client doit être `public`.
