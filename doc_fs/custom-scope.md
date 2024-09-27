# Le scope custom

Ce scope optionnel permet de récupérer toutes les propriétés retournées à l'appel au `userinfo_endpoint` d'un Fournisseur d'Identité qui ne sont pas reconnues comme *canoniques* par ProConnect.

> Les propriétés *canoniques* sont les claims que ProConnect récupère auprès des Fournisseurs d'identité. Vous trouverez [ici](../doc_fi/configuration.md#configurer-les-scopes) la liste des scopes associés à ces claims.

Ces propriétés *non canoniques* sont ensuites déplacées dans un objet `custom`.

Quand un Fournisseur de Service demande un scope `custom`, l'appel au `userinfo_endpoint` de ProConnect retournera ces propriétés dans un objet `custom`.

### Cas n°1 : le Fournisseur d'Identité n'a retourné aucune propriété *non canonique* lors de l'appel à son `userinfo_endpoint`

ProConnect renverra un objet `custom` vide :

```json
{
  "sub": "sub-proconnect",
  ...
  "custom": {}
  }

```

### Cas n°2 : le Fournisseur d'Identité a retourné des propriétés *non canoniques* lors de l'appel à son `userinfo_endpoint`

Par exemple:

```json
{
  "sub": "sub-idp",
  ...,
  "structure_travail": "59194",
  "site_travail": "DRHAUTS-DE-FRANCE/PFPPLATEFORMESERVICESADISTANCE(HDF0262005733)"
}
```

Dans ce cas, ProConnect placera ces valeurs dans l'objet `custom`:

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

NB: Si le Fournisseur de Service ne demande pas de scope `custom`, alors l'objet `custom` ne sera, logiquement, pas retourné par ProConnect, même si le Fournisseur d'Identité renvoie des propriétés *non canoniques*. L'appel au `userinfo_endpoint` de ProConnect renverra donc :

```json
{
  "sub": "7396c91e-b9f2-4f9d-8547-5e9b3332725b",
  ...
}

```
