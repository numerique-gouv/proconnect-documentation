# Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?

Vous souhaitez être Fournisseur d'Identité pour AgentConnect et votre demande datapass a déjà été validée.
Avant de passer à l'étape suivante de qualification de la mise en place de votre Fournisseur d'Identité, il est necéssaire d'implémenter les points listés ci-dessous. 

Ceux-ci seront vérifiés un par un par l'équipe AgentConnect au moment de la recette. 

L'ensemble des prérequis doivent être respectés afin d'obtenir la validation qui vous permettra de passer en production.

Pour rappel, vous pouvez demander la recette de votre Fournisseur d'Identité en vous rendant sur le lien suivant : 

- **[Demande de recette d'un Fournisseur d'Identité AgentConnect](https://www.demarches-simplifiees.fr/commencer/demande-recette-fi-fca)**

## Parcours d'utilisation de l'agent et recommandations UX

La mire de connexion du fournisseur d'identité doit tout d'abord être responsive. 

Les éléments suivants sont recommandés, afin d'éviter l'abandon de l'agent lors d'une cinématique AgentConnect :

* Lien de contact du support du fournisseur d'identité
* Lien de mot de passe oublié.

Nous recommandons également les éléments suivants sur la mire de connexion du Fournisseur d'Identité :

- Fond grisé avec Marianne en blanc en bas à droite.
- Logos d'AgentConnect et du fournisseur d'identité.
- Lien "retourner sur AgentConnect" pour permettre le changement de Fournisseur d'Identité à l'agent.

Ci-dessous les éléments visuels nécessaires : 

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

## L'accès à votre environnement de recette

*Fournisseur d'Identité Internet* 

Si possible, afin de nous permettre de réaliser les tests en toute autonomie, merci de: 
- créer un ou plusieurs compte(s) test temporaire(s) ou permanent(s) pour l'équipe AgentConnect (ou un membre en particulier de l'équipe),
ou
- nous fournir une identité test générique.

Si vous ne pouvez pas nous fournir une identité de test, une recette en visio devra alors se faire car nous ne serons pas en mesure de tester votre Fournisseur d'Identité. 
Merci de nous contacter aux adresses suivantes elodie.boudouin@modernisation.gouv.fr et/ou melanie.wynd@prestataire.modernisation.gouv.fr afin de fixer ce point.

*Fournisseur d'Identité RIE*

Si vous implémentez votre Fournisseur d'Identité AgentConnect sur le RIE, une recette en visio devra se faire car nous ne pouvons pas tester la cinématique et accéder à votre  Fournisseur d'Identité. 
Merci de nous contacter aux adresses suivantes elodie.boudouin@modernisation.gouv.fr et/ou melanie.wynd@prestataire.modernisation.gouv.fr afin de fixer ce point.

## Points à vérifier

**1. Homologation RGS**

Votre Fournisseur d'Identité à été homologué RGS.
Dans le cas contraire, merci de nous indiquer s'il est prévu que vous fassiez homologuer votre Fournisseur d'Identité. Et si oui, merci de nous communiquer la date prévisionnelle de l'homologation.

**2. Cinématique - Connexion**

En tant qu'utilisateur je peux me connecter sur le Fournisseur de Services en utilisant le Fournisseur d'Identité. La cinématique fonctionne de bout en bout et je suis authentifié auprès du Fournisseur de Services.

**3. Il n'y a pas d'erreur technique au retour du Fournisseur d'Identité**

En tant qu'utilisateur, une fois que je me suis authentifié auprès du Fournisseur de Service, je tombe sur le service et non sur une page d'erreur (ex: erreur technique Yxxxxx).

**4. Cinématique - Déconnexion**

La déconnexion fonctionne : il est nécessaire de vérifier que lorsque l'utilisateur se déconnecte sur le service, il est déconnecté du service, d'AgentConnect et du Fournisseur de Service.

---

Voir aussi : 
