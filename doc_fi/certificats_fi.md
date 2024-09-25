# Quels sont les certificats d'authentification ?

Lors de la récupération des données de l'identité pivot et des attributs complémentaires auprès du Fournisseur d'Identité, ProConnect transmet un certificat SSL client RGS * Certigna. Ce certificat permet au Fournisseur d'Identité de s'assurer que ProConnect est bien à l'origine de l'appel. Il doit donc être vérifié afin que l'authentification soit mutuelle.

Les endpoints concernés sont les endpoints `token` et `userinfo`.




