# Recommandations de parcours utilisateur
## Généralités
ProConnect est un outil d'authentification. 
Il agit comme **un pont** entre un bouton de connexion et la partie authentifiée de votre service. 
**C'est vous qui avez le contrôle sur ce qui se passe avant et après ce pont.** 
Voici quelques recommandations pour un parcours simple et sans blocage pour les visiteurs de vos services. 
## Recommandations
### Votre service s'adresse aussi aux particuliers ?
Selon la nature de votre service, vous pouvez
- Proposez un parcours de connexion différencié pour les particuliers et les professionnels. 
    Dans votre navigation principale :
    - Espace particulier (FranceConnect)
    - Espace professionnel (ProConnect)


- Hiérarchisez les propositions comme cela sur une même page de connexion : 
    1. FranceConnect
    2. ProConnect
    3. Autre mode de connexion / compte local

#### Exemple d'implémentation
![RDV Service Public](https://storage.gra.cloud.ovh.net/v1/AUTH_0f20d409cb2a4c9786c769e2edec0e06/padnumerique/uploads/49b2c5db-7ae9-4b1a-8351-2cf9150680c3.png)
[RDV Service Public](https://rdv.anct.gouv.fr/), Parcours différencié Agent / Usager

![Exemple de Wireframe](https://storage.gra.cloud.ovh.net/v1/AUTH_0f20d409cb2a4c9786c769e2edec0e06/padnumerique/uploads/fef01174-3b9f-4eb0-8df0-be17359d661b.png)Exemple de Wireframe, Page de connexion avec accès Particulier / Professionnel et compte local.


### Votre service a des restrictions d'accès ?
Si vous autorisez uniquement le secteur public ou uniquement une liste de structures partenaires, il est indispensable d'en informer l'utilisateur AVANT le bouton ProConnect.
Reprenons l'image du pont : s'il est interdit aux camions, il faut mettre un panneau avant le pont ! 
- ajoutez un encadré qui explique qui est autorisé à utiliser ce service
- ajoutez une page d'erreur qui explique clairement aux utilisateurs non autorisés pourquoi ils sont bloqués, s'ils essaient malgré tout de se connecter. 

#### Exemple d'implémentation
![Annuaire des Entreprises](https://storage.gra.cloud.ovh.net/v1/AUTH_0f20d409cb2a4c9786c769e2edec0e06/padnumerique/uploads/4af46883-7692-48b8-8809-28869cecd282.png)
[Annuaire des Entreprises](https://annuaire-entreprises.data.gouv.fr/lp/agent-public), Page de connexion dédiée avec explication des restrictions d'accès.

### Votre site propose plusieurs modes de connexion ? 
Hiérarchisez les boutons de connexion comme ceci : 
1. ProConnect
2. Autre mode de connexion / compte local

#### Exemple d'implémentation
![FranceTransfert](https://storage.gra.cloud.ovh.net/v1/AUTH_0f20d409cb2a4c9786c769e2edec0e06/padnumerique/uploads/c0a188b1-a451-4828-8b58-4d8f80cec50f.png)
[FranceTransfert](https://francetransfert.numerique.gouv.fr/connect), Page de connexion dédiée avec ProConnect puis un compte local.


### Où placez le bouton ProConnect ?
1. Vous avez des utilisateurs particulier et professionnels ou vous avez plusieurs modes de connexion : pour que l'utilisateur comprenne facilement quel est le meilleur choix pour lui, faites **une page de connexion dédiée**. Les informations contextuelles seront vues et lues plus facilement.
2. Vous utilisez exclusivement ProConnect : placez le bouton ProConnect directement sur votre page d'accueil. 



## Questions
Vous avez des questions ?
Votre cas ne rentre pas dans cette liste ? 
Contactez-nous ! Cela nous permettra de vous conseiller et d'améliorer cette documentation. 