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
- [Qu'est ce que le protocole OpenID Connect ?](../technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](../technique_fca_fi/technique_fca_oidc_fi.md)
- [Quelles sont les données utilisateur que je dois fournir ?](../technique_fca_fi/donnees_utilisateurs_fi.md)
- [Quel est le détail du fonctionnement ?](../fonctionnement_fca_fi/details_fonctionnement_fi.md)
- [Quel est le détail des flux ?](../fonctionnement_fca_fi/details_flux_fi.md)
- [Quels sont les certificats d'authentification ?](../fonctionnement_fca_fi/certificats_fi.md)
- [Qu'est ce qu'eIDAS et comment utiliser les niveaux eIDAS en tant que Fournisseurs d'Identité ?](../fonctionnement_fca_fi/fca_niveau_eidas_fi.md)
- [Comment accéder aux différents environnements d'AgentConnect ?](../test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](../test_fca_fi/test_fca_demonstrateur_fi.md)
