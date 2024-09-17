# Comment spécifier à ProConnect que les usagers de mon FS doivent être redirigés directement vers un Fournisseur d'Identité (FI) spécifique ?

Il peut arriver que, en tant que Fournisseur de Service (FS), vous souhaitiez qu'au clic sur le bouton "S'identifier avec ProConnect", vos usagers soient redirigés automatiquement vers un FI que vous auriez précisé en amont.

Pour ce faire :

## 1. Trouver la valeur `idp_id` correspondant au FI vers lequel rediriger les usagers

La documentation [ici](./connaitre-le-fi-utilise.md) explique comment récupérer cet identifiant.

## 2. Passer cette valeur au paramètre `idp_hint` lors de l'appel au `authorization_endpoint`

L'appel à ce endpoint est détaillé [ici](./implementation_technique.md).
