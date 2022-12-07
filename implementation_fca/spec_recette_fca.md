# Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?

Vous souhaitez être Fournisseur de Services pour AgentConnect et votre demande datapass a déjà été validée.
Avant de passer à l'étape suivante de qualification de la mise en place d'AgentConnect, il est necéssaire d'implémenter les points listés ci-dessous. 

Ceux-ci seront vérifiés un par un par l'équipe AgentConnect au moment de la recette. 

L'ensemble des prérequis doivent être respectés afin d'obtenir la validation qui vous permettra d'utiliser AgentConnect en production.

## Le visuel

1. **L'esthétique du bouton AgentConnect est respectée**

- le design, les couleurs et le label du bouton AgentConnect ne peuvent pas être modifiés,
- la taille recommandée pour une utilisation optimale est de 60 pixels de haut par 230 px de large,
- votre intégration doit respecter le référentiel général d’amélioration de l’accessibilité (RGAA),
- l’état survol du bouton pour montrer l’interaction doit être intégré. 

Voir [Quel bouton AgentConnect intégrer et comment l'intégrer?](../implementation_fca/bouton_fca.md)


2. **La phrase d'introduction à AgentConnect est placée au dessus du bouton**

*"AgentConnect vous permet d’accéder à de nombreux services en ligne en utilisant l’un de vos comptes professionnels existants."*

Cette phrase doit obligatoirement être placée dans les cas suivants: 

- différents moyens de connexion cohabitent, 
- sur des outils qui ne sont pas uniquement réservés aux agents.

3. **AgentConnect dans la section connexion**

Le bouton est présent dans la section "connexion/se connecter" du service.

4. **AgentConnect dans la section inscription (si applicable)**

Le bouton est présent dans la section "inscription/s'inscrire" du service (si applicable).

5. **AgentConnect est le premier mode de connexion/d'inscription**

Le bouton AgentConnect est situé en premier mode de connexion/d'inscription au dessus des autres moyens
d'identification.

6. **AgentConnect est séparé des autres modes de connexion/d'inscription**

- il est important de dissocier visuellement les différents moyens d’authentification : une séparation visible doit être mise en place entre eux,
- la mention "OU" doit également y figurer afin de faire comprendre à l'utilisateur qu'il peut choisir entre AgentConnect ou un autre mode de connexion/d'inscription.

7. **Lien "Qu'est-ce qu'AgentConnect ?"**

Le bouton doit être accompagné du lien « Qu’est-ce qu’AgentConnect ? » positionné à 8 pixels en dessous, en corps 13 pixels minimum et qui redirige vers l’URL https://agentconnect.gouv.fr/.

## Le parcours utilisateur

1. **Un autre moyen d'identification qu'AgentConnect est mis à disposition des agents**

Il est obligatoire de mettre à disposition des utilisateurs un moyen alternatif de connexion/d'inscription afin que ceux-ci ne dépendent pas uniquement d'AgentConnect.

2. **Cinématique - Connexion**

La cinématique de connexion fonctionne : je peux me connecter via AgentConnect sur le service.

3. **Cinématique - Inscription**

Le cas échéant, la cinématique d'inscription fonctionne : je peux m'inscrire via AgentConnect sur le service.

4. **Cinématique - Réconciliation de compte**

Existe-t-il une réconciliation des données dans le cas où le fournisseur de services dispose de comptes locaux et souhaite gérer la réconciliation entre ses données locales et celles transmises par AgentConnect.

:warning: **Attention**, il ne faut pas demander à l’usager de saisir son identifiant/mot de passe local. En effet, trop complexe, cette demande provoque l'abandon de l'usager.

5. **Cinématique - Déconnexion**

La déconnexion fonctionne : je peux me déconnecter d'AgentConnect sur le service.

## Les aspects sécurité

1. **Interdiction des pop-ups et iframes** 

Les fenêtres pop-ups et iframes sont interdites.

2. **Vérification de la connexion**

L'usager doit pouvoir identifier clairement qu'il est connecté et son profil accessible.

3. **Scopes**

Les scopes appelés sont les mêmes que ceux déclarés et autorisés dans la demande datapass.

4. **TLS**

Le service ne doit pas utiliser de version de TLS inférieur à 1.2 et doit obligatoirement utilisé des versions 1.2 ou 1.3.


---

Voir aussi : 
- [Quel bouton AgentConnect intégrer et comment l'intégrer ?](../implementation_fca/bouton_fca.md)
- [Quelles sont les étapes pour devenir Fournisseur de Services ?](../pilotage_fca/pilotage_fca_etapes.md)
- [Comment faire qualifier mon implémentation ?](../recette_fca/recette.md)
- [Comment recevoir mes jetons de production ?](../recette_fca/recette_cles_prod.md)