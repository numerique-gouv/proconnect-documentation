# Quels sont les prérequis pour devenir Fournisseur d'Identité pour ProConnect ?

Les prérequis sont les suivants :
-  être l'entité légitime qui gère le processus RH d'un agent jusqu'à la fin du contrat
- pouvoir déployer une cinématique au standard OpenID Connect - authorization code flow
- être en capacité de transmettre à ProConnect les 5 données obligatoires :
  - nom de famille de l'agent
  - prénom de l'agent
  - adresse e-mail professionnel de l'agent
  - identifiant technique (du FI)
  - l'identifiant SIRET (14 chiffres sans espace)
- fournir les noms de domaine des adresses emails concernées par le FI (par exemple : `@justice.fr` et `@justice.gouv.fr` pour le Ministère de la Justice)

Afin de prouver à l'équipe ProConnect que vous possédez bien le(s) nom(s) de domaine pour lesquels vous souhaitez effectuer la redirection, il vous est demandé d'ajouter un enregistrement TXT au DNS pour chaque nom de domaine concerné, contenant l'Identity Provider ID de votre Fournisseur d'Identité (que nous vous fournissons après réception de votre formulaire Démarches Simplifiées) :
- Type : TXT
- Nom/hôte : @ ou nom-de-domaine.com (selon votre interface de gestion DNS)
- Valeur : `proconnect-identity-provider-{{idp_id}}`

> [!IMPORTANT]
> Vous devez garantir l'authentification de tous les utilisateurs disposant d'une adresse e-mail valide associée à l'un des noms de domaines que vous nous fournirez. Aucune exception ne doit être faite : chaque utilisateur dont l'adresse respecte les domaines spécifiés doit pouvoir être authentifié.
