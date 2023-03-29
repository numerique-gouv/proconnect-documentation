# Quelles sont les données utilisateur que je dois fournir ?

## Les données obligatoires

En plus de l'openid, qui est obligatoire, des données obligatoires sont fournies par les Fournisseurs d'Identité aux Fournisseurs de Service, via AgentConnect . Ces données permettent d'identifier un utilisateur .
                                                    
|Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
|given_name | Oui |Prénoms séparés par des espaces (standard OpenIDConnect)| UTF-8 (standard OpenIDConnect)|
|usual_name| Oui |Nom de famille d'usage (par défaut = family_name)| UTF-8 |
|email | Oui |Adresse courriel |UTF-8 (standard OpenIDConnect)|
|uid|Oui |Identifiant unique de l'agent auprès du FI| String (standard OpenIDConnect)|

En complément, il est possible d'obtenir des données complémentaires. Cependant ces données ne sont pas obligatoirement connues par tous les Fournisseurs d'Identité.

## Les données complémentaires

Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
| siren | non  | Identifiant d'entreprise  | String, 9 chiffres sans espace |
| siret | non |Identifiant d'établissement| string, 14 chiffres sans espace|
| organizational_unit  | non  | Ministère/Direction/Service d'affectation   | UTF8 |
| belonging_population  | non  | Population d'appartenance  | string, Exemple: agent, prestataire, partenaire, stagiaire |
| phone  | non  | Téléphones de contact  | Format non normé |
| chorusdt   | Non | Entité ministérielle/Matricule Agent  | string |


La liste des données complémentaires est non exhaustive et pourra être amendée si besoin 

---

Voir aussi : 
- [Qu'est ce que le protocole OpenID Connect ?](../technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](../technique_fca_fi/technique_fca_oidc_fi.md)
- [Quels sont les endpoints sur AgentConnect ?](../fonctionnement_fca_fi/endpoints_fi.md)
- [Quel est le détail du fonctionnement ?](../fonctionnement_fca_fi/details_fonctionnement_fi.md)
- [Quel est le détail des flux ?](../fonctionnement_fca_fi/details_flux_fi.md)
- [Quels sont les certificats d'authentification ?](../fonctionnement_fca_fi/certificats_fi.md)
- [Qu'est ce qu'eIDAS et comment utiliser les niveaux eIDAS en tant que Fournisseurs d'Identité ?](../fonctionnement_fca_fi/fca_niveau_eidas_fi.md)


