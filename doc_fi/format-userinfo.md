# Contrôle des identités retournés par les userinfos des FI

Pour que ProConnect reconnaisse comme valide une identité, le FI doit retourner les champs obligatoires définis [ici](https://github.com/numerique-gouv/proconnect-documentation/blob/main/doc_fi/configuration.md#configurer-les-scopes) en respectant les contraintes.


### Siret

Si un siret est fourni avec des espaces, nous supprimons les espaces. Si ce siret est reconnu comme incorrect, nous le remplaçons par le siret par défaut du FI. Ce siret par défaut est configuré dans ProConnect.


### Numéro de téléphone

Les numéros de téléphone sont optionnels. Cependant si un FI retourne un champ `phone_number` avec une chaîne de caractères vide ou qui contient plus de 256 caractères, l'identité sera considérée comme invalide et ProConnect retournera une erreur.

Si l'identité contient un `phone_number` qui respecte la contrainte définie ci-dessus mais est reconnu comme incorrect par ProConnect, ProConnect retournera une identité sans numéro de téléphone mais sans erreur.
