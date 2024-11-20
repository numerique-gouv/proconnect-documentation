# Comment savoir avec quel Fournisseur d'Identité s'est authentifié mon utilisateur ?

Le Fournisseur de service peut demander le scope `idp_id`, qui est systématiquement envoyé par ProConnect. Le Fournisseur de Service peut ainsi décider de quels Fournisseurs d'Identité sont autorisés pour son application.

La table de correspondance entre l'ID du Fournisseur d'Identité (colonne UID) et le nom du Fournisseur d'Identité (colonne Titre) est présente [ici](https://grist.numerique.gouv.fr/o/docs/3kQ829mp7bTy/AgentConnect-Configuration-des-Fournisseurs-dIdentite?utm_id=share-doc).

Si lorsque vous faîtes cet appel, vous recevez l'erreur "requested scope is not allowed", c'est que le scope idp_id n'a pas été autorisé par votre FS. Vous pouvez nous écrire pour nous le demander, nous l'ajouterons automatiquement.

NB: les FI présents sur le RIE et bénéficiant du "hybridge" disposent de deux `idp_id` : un pour le FI Internet, et un pour le FI RIE.
Si vous êtes un FS exposé sur Internet et souhaitez identifier les utilisateurs d'un FI "hybridgé", il vous faudra regarder l'`idp_id` du FI **Internet**.
