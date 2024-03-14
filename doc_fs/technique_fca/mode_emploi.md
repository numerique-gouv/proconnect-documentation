[Accueil](https://github.com/france-connect/Documentation-AgentConnect/blob/main/README.md) > [AgentConnect - Fournisseur de Service](https://github.com/france-connect/Documentation-AgentConnect/blob/main/doc_fs.md) > Je suis fournisseur de service (FS) et je veux implémenter la connexion via Agent Connect (AC) sur mon produit

___

# Je suis fournisseur de service et je veux implémenter la connexion via Agent Connect sur mon produit

## 1. 📚 À lire avant l'implémentation
- [Quelles sont les étapes pour devenir Fournisseur de Services ?](../../doc_fs/pilotage_fca/pilotage_fca_etapes.md)

## 2. 📑 À garder en onglet ouvert pendant l'implémentation
- [Quel est le détail du fonctionnement ?](../../doc_fs/fonctionnement_fca/details_fonctionnement.md)

## 3. ✅ Pré-requis techniques
Définir deux endpoints sur votre produit qu'il vous faudra implémenter. Vous devrez fournir ces endpoints lors du dépôt de demande de dossier sur Démarches Simplifiées :

  - **LOGIN** : par exemple, `<FS_URL>/oidc-login`
  - **LOGOUT** : par exemple, `<FS_URL>/logout`

## 4. ⚙️ Mode d'emploi technique
### 4.1. Implémenter le bouton AC sur votre page de connexion

- [Quel bouton AgentConnect intégrer et comment l'intégrer ?](../../doc_fs/implementation_fca/bouton_fca.md)

### 4.2. Faire pointer le bouton AC vers le endpoint AC /api/v2/authorize

L'URL AC à utiliser est définie ici : [Adresses des environnements d'intégration et de production AgentConnect](../../doc_fi/production_fca_fi/adresses_fca_fi.md)

Au clic sur le bouton AC, rediriger vers l'URL : `<AC_URL>/api/v2/authorize`.

Les query parameters à envoyer dans l'URL sont décrits ici : [OIDC endpoints](../../doc_fs/technique_fca/endpoints.md)

### 4.3. Implémenter la route **LOGIN**
Il s'agit de la route vers laquelle sera redirigée votre utilisateur après authentification par le fournisseur d'identité.

Les query parameters renvoyés dans l'URL sont décrits ici : [OIDC endpoints](../../doc_fs/technique_fca/endpoints.md)

D'abord, vérifiez que le champ `state` renvoyé correspond bien au `state` généré précédemment.

Une fois ce champ `state` vérifié, vous pouvez appeler l'URL de génération de token selon le contrat d'API décrit ici : ([OIDC endpoints](../../doc_fs/technique_fca/endpoints.md)).

Si tout se passe bien, vous récupérez alors un access_token.

Cet access_token est un Bearer token. Sa durée de validité est de 60 secondes.

Vous pouvez maintenant appeler l'URL contenant les informations de votre utilisateur en ajoutant ce Bearer token dans l'en-tête Authorization : (endpoint userInfo ici : [OIDC endpoints](../../doc_fs/technique_fca/endpoints.md)).

Vous recevrez en réponse un JWT token, que vous pourrez renvoyer au client, pour le lui faire stocker dans ses cookies.

NB: la session Agent Connect a une durée de 12 heures.
