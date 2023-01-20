Documentation Fournisseur d'Identité

---

Vous souhaitez devenir Fournisseur d'Identité sur AgentConnect ? Vous êtes au bon endroit ! Cette documentation présente l'ensemble des informations à connaitre.

# Préambule

Cette documentation est à destination des Fournisseurs d'Identité souhaitant intégrer AgentConnect. 
AgentConnect est implémenté sur deux plateformes, une dite "full RIE" (l’agent se connecte depuis le RIE, à un FS RIE via un FI RIE) et une autre dite "full Internet" (l'agent se connecte depuis Internet, à un FS Internet via un FI Internet).
Toutefois il est possible de communiquer entre les deux plateformes grâce à "l'hybridge Internet/RIE" (l'agent se connecte depuis Internet, à un Fournisseur de Services Internet via un FI RIE).

# Je veux devenir Fournisseur d'Identité 

Vous souhaitez devenir Fournisseur d'Identité pour AgentConnect, voici les éléments à prendre en compte : 

- [Quelles sont les étapes pour devenir Fournisseur d'Identité ?](doc_fi/pilotage_fca/pilotage_fca_etapes_fi.md)
- [Quels sont les acteurs à impliquer dans l'intégration d'AgentConnect ?](doc_fi/pilotage_fca/pilotage_fca_demarches_acteurs_fi.md)
- [Qu'est-ce que la plateforme "Full Internet", la plateforme "Full RIE" et l'"Hybridge" ?](doc_fi/pilotage_fca/plateformes_fi.md)
- [Comment accéder au formulaire datapass ?](doc_fi/pilotage_fca/datapass_fi.md)

# J'intègre AgentConnect

## Je souhaite connaître le concept de base d'AgentConnect

- [Qu'est ce que le protocole OpenID Connect ?](doc_fi/technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](doc_fi/technique_fca_fi/technique_fca_oidc_fi.md)
- [Quelles sont les données utilisateur que je dois fournir ?](doc_fi/technique_fca_fi/donnees_utilisateurs_fi.md)

## Je veux savoir comment fonctionne AgentConnect et comment implémenter mon Fournisseur d'Identité

- [Quels sont les endpoints sur AgentConnect ?](doc_fi/fonctionnement_fca_fi/endpoints_fi.md)
- [Quel est le détail du fonctionnement ?](doc_fi/fonctionnement_fca_fi/details_fonctionnement_fi.md)
- [Quel est le détail des flux ?](doc_fi/fonctionnement_fca_fi/details_flux_fi.md)
- [Quels sont les certificats d'authentification ?](doc_fi/fonctionnement_fca_fi/certificats_fi.md)
- [Qu'est ce qu'eIDAS et comment utiliser les niveaux eIDAS en tant que Fournisseurs d'Identité ?](doc_fi/fonctionnement_fca_fi/fca_niveau_eidas_fi.md)









# Parcours d'utilisation de l'agent et recommandations UX

La mire de connexion du fournisseur d'identité doit tout d'abord être responsive. 

Les éléments suivants sont recommandés, afin d'éviter l'abandon de l'agent lors d'une cinématique AgentConnect :

* Lien de contact du support du fournisseur d'identité
* Lien de mot de passe oublié.

Nous recommandons également les éléments suivants sur la mire de connexion du fournisseur d'identité :

Fond grisé avec Marianne en blanc en bas à droite.
Logos d'AgentConnect et du fournisseur d'identité.
Lien "retourner sur AgentConnect" pour permettre le changement de fournisseur d'identité à l'agent.


Ci-dessous les éléments visuels nécessaires : **A compléter**

<img src="uploads/19e0c2e1d02d2a6b1a3f97a74a35c559/logo_marianne.png" alt="drawing" width="150"/>
<img src="uploads/e08be0034c2ae3b1faca59e70bbec1a1/fc_avatar.png" alt="drawing" width="150"/>

Téléchargements :

**A compléter**

* [Pack png](uploads/af84d2a6599ec7a07671d43d2f400ff3/fc_images_png.zip)
* [Pack jpg](uploads/1429d69fe3baee1cc8560ad365aaec96/fc_images_jpg.zip)


Le parcours d’identification doit être validé par l’équipe AgentConnect le plus en amont possible de la réalisation sous la forme suivante : 
* communication des maquettes ou spécifications fonctionnelles
* qualification du parcours d’identification en environnement d'intégration

Ces deux étapes sont des pré-requis à une ouverture en production. 

L’équipe AgentConnect est là pour vous aider à proposer l’expérience usager la plus adaptée. 
N'hésitez pas à la solliciter pour éviter d'impacter vos délais de mise en production.


# Glossaire

Le glossaire relatif à OpenId Connect est spécifié à l'adresse [https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.1.2](https://openid.net/specs/openid-connect-core-1_0.html#rfc.section.1.2)
