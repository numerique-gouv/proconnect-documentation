# Quelles sont les données que je peux récupérer par AgentConnect sur les agents ?

Les données Agent sont fournies par les Fournisseurs d'Identité aux Fournisseurs de Services, via AgentConnect, conformément à l'habilitation obtenue via [datapass.api.gouv.fr](https://datapass.api.gouv.fr), et le choix des données réalisé par le Fournisseur de Services dans cette demande.


## Les données obligatoires

En plus de l'openid, qui est obligatoire, des données obligatoires sont fournies par les Fournisseurs d'Identité aux Fournisseurs de Services via AgentConnect. Ces données permettent d'identifier un utilisateur.
                                                    

|Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
|given_name | Oui |Prénoms séparés par des espaces (standard OpenIDConnect)| UTF-8 (standard OpenIDConnect)|
|usual_name| Oui |Nom de famille d'usage (par défaut = family_name)| UTF-8 |
|email | Oui |Adresse courriel |UTF-8 (standard OpenIDConnect)|
|uid|Oui |Identifiant unique de l'agent auprès du FI| String (standard OpenIDConnect)|

L'uid est une donnée technique qui ne peut pas être demandée par le Fournisseur de Services.

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


La liste des données complémentaires est non exhaustive et pourra être amendée si besoin.

AgentConnect transmet systématiquement au Fournisseur de Services un identifiant unique pour chaque agent (le sub) : 

* Cet identifiant (appelé sub) est spécifique à chaque Fournisseur de Services et à chaque Fournisseur d'Identité. 
- Un même utilisateur aura toujours le même SUB pour un Fournisseur d'Identité donné, en revanche il aura un SUB différent pour chaque Fournisseur de Services qu'il utilisera.

## La liste des scopes disponibles lors de l'étape d'authentification AgentConnect

AgentConnect a étendu le mécanisme de scopes pour qu'il soit plus modulaire.

* Un seul scope est obligatoire : openid. Il permet de récupérer le sub (identifiant unique technique) de l'utilisateur.
* Il est possible de combiner plusieurs scopes de son choix pour récupérer seulement les informations dont a besoin le FS.


Cette liste de scopes est définie par la norme OpenIDConnect : http://openid.net/specs/openid-connect-core-1_0.html#ScopeClaims


---

Voir aussi : 
- [Quel est le détail du fonctionnement ?](../fonctionnement_fca/details_fonctionnement.md)
- [Quels sont les endpoints sur AgentConnect (le contrat d'API) ?](../technique_fca/endpoints.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs ? ](../technique_fca/technique_fca_scope.md)
- [Quelles sont les données d'AgentConnect qui expirent ?](../technique_fca/donnees_expirent.md)
- [Qu'est ce qu'eIDAS et quel est le niveau de garantie d'AgentConnect ?](../projet_fca/projet_fca_niveau_eidas.md)