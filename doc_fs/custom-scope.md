# Le scope custom

Ce scope optionnel permet de récupérer toutes les propriétés retournées par l'userinfo d'un Fournisseur d'Identité qui ne sont pas reconnues comme canoniques par ProConnect.

Ces propriétés "canoniques" correspondent aux claims que ProConnect récupère auprès des Fournisseurs d'identité, voici [la liste](../doc_fi/configuration.md#configurer-les-scopes) des scopes associés à ces claims.

Ces informations sont ensuites déplacées dans un objet "custom".

Quand un Fournisseur de Service demande un scope "custom" l'userinfo de ProConnect retournera cette propriété.

Si le Fournisseur d'Identité n'a retourné aucune propriété non canonique dans son userinfo, ProConnect renverra un champ "custom" retournant un objet vide:

```json
{
  "sub": "sub-proconnect",
  ...
  "custom": {}
  }

```

Si le Fournisseur d'Identité retourne des propriétés non canonique, comme par exemple:

```json
{
  "sub": "sub-idp",
  ...,
  "structure_travail": "59194",
  "site_travail": "DRHAUTS-DE-FRANCE/PFPPLATEFORMESERVICESADISTANCE(HDF0262005733)"
}
```

ProConnect placera ces valeurs dans l'objet custom:

```json
{
  "sub": "7396c91e-b9f2-4f9d-8547-5e9b3332725b",
  ...
  "custom": {
    "structure_travail": "59194",
    "site_travail": "DRHAUTS-DE-FRANCE/PFPPLATEFORMESERVICESADISTANCE(HDF0262005733)"
  }
}

```

Si le Fournisseur de Service ne demande pas de scope custom, l'objet "custom" ne sera, logiquement, pas retourné par ProConnect, même si le Fournisseur d'Identité renvoie des propriétés non canonique :

```json
{
  "sub": "7396c91e-b9f2-4f9d-8547-5e9b3332725b",
  ...
}

```
