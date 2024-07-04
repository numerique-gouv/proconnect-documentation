# En tant que Fournisseur de Service, quelles sont les données que je peux récupérer par AgentConnect sur les agents ?

Les données Agent sont fournies par les Fournisseurs d'Identité aux Fournisseurs de Services, via AgentConnect, conformément à l'habilitation obtenue via [datapass.api.gouv.fr](https://datapass.api.gouv.fr), et le choix des données réalisé par le Fournisseur de Services dans cette demande.


## Les données obligatoires

En plus de l'openid, qui est obligatoire, des données sont **systématiquement** fournies par les Fournisseurs d'Identité aux Fournisseurs de Services via AgentConnect. Ces données permettent d'identifier un utilisateur.

|Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
|given_name | Oui |Prénoms séparés par des espaces (standard OpenIDConnect)| UTF-8 (standard OpenIDConnect)|
|usual_name| Oui |Nom de famille d'usage (par défaut = family_name)| UTF-8 |
|email | Oui |Adresse courriel |UTF-8 (standard OpenIDConnect)|
|uid|Oui |Identifiant unique de l'agent auprès du FI| String (standard OpenIDConnect)|
| siret | Oui |Identifiant d'établissement| string, 14 chiffres sans espace|

Il vous est possible d'obtenir des données complémentaires à celles-ci. Cependant ces données ne sont pas obligatoirement fournies par tous les Fournisseurs d'Identité, et leur format est plus sujet à fluctuation selon la qualité de l'annuaire du Fournisseur d'Identité.


## Les données complémentaires

Champs | Obligatoire | Description| Format |
|---- | ------ | ------ | ------ |
| siren | non  | Identifiant d'entreprise  | String, 9 chiffres sans espace |
| organizational_unit  | non  | Ministère/Direction/Service d'affectation   | UTF8 |
| belonging_population  | non  | Population d'appartenance  | string, Exemple: agent, prestataire, partenaire, stagiaire |
| phone  | non  | Téléphone de contact  | Format non normé |
| chorusdt   | Non | Entité ministérielle/Matricule Agent  | string |

## Le champ sub

AgentConnect transmet systématiquement au Fournisseur de Services un identifiant unique pour chaque agent (le `sub`) : cet identifiant est spécifique **à chaque couple** Fournisseur de Services / Fournisseur d'Identité. Il ne peut donc pas être utilisé pour faire de la réconciliation d'identité : nous vous recommandons l'utilisation de l'email professionnel pour cet usage.

:warning: **Attention**

## La liste des scopes disponibles lors de l'étape d'authentification AgentConnect

AgentConnect a étendu le mécanisme de scopes pour qu'il soit plus modulaire.

* Un seul scope est obligatoire : openid. Il permet de récupérer le sub (identifiant unique technique) de l'utilisateur.
* Il est possible de combiner plusieurs scopes de son choix pour récupérer seulement les informations dont a besoin le FS.

Cette liste de scopes est définie par la norme OpenIDConnect : http://openid.net/specs/openid-connect-core-1_0.html#ScopeClaims
