# Quels sont les endpoints sur AgentConnect ?

En environnements d'intégration et de production AgentConnect, les endpoints sont disponibles en HTTPS.

## Environnement Internet : 

| Environnement | Adresse de retour ( Redirect URI ) |
| ------ | ------ |
| intégration AC | https://fca.integ01.dev-franceconnect.fr/api/v2/oidc-callback/{fc-internal-id} |
| production AC | Envoi de l'URL de prod par mail |  


## Environnement RIE : 

| Environnement | Adresse de retour ( Redirect URI ) |
| ------ | ------ |
| intégration AC | https://fca.integ02.agentconnect.rie.gouv.fr/api/v2/oidc-callback/{fc-internal-id}  |
| production AC | Envoi de l'URL de prod par mail |  


La valeur `{AC-internal-id}` est spécifique à chaque fournisseur d'identité et sera fournie par AgentConnect.

---

Voir aussi : 
