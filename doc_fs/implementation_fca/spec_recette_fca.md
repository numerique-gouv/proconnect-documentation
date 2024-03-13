# Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?

Voici les spécifications visuelles pour réussir au mieux l'intégration d'AgentConnect.

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

Nous obligions par le passé de forcer un autre moyen de connexion à l'application. Ceci n'est plus le cas : vous pouvez mettre AgentConnect en unique moyen de connexion si cela est pertinent.

2. **Cinématique - Connexion**

La cinématique de connexion fonctionne : je peux me connecter via AgentConnect sur le service.

3. **Cinématique - Le lien "Revenir sur  ..." en haut à droite de la mire fonctionne**

Le lien situé en haut à droite de la mire indiquant "Revenir sur ..." puis le nom de votre Fournisseur de Services renvoie bien sur la page d'accueil de votre Fournisseur de Services.

4. **Cinématique - Inscription**

Le cas échéant, la cinématique d'inscription fonctionne : je peux m'inscrire via AgentConnect sur le service.

5. **Cinématique - Réconciliation de compte à la première connexion (1er accès de l’utilisateur au Fournisseur de Service)**

Existe-t-il une réconciliation des données dans le cas où le fournisseur de services dispose de comptes locaux et souhaite gérer la réconciliation entre ses données locales et celles transmises par AgentConnect.

:warning: **Attention**, il ne faut pas :

- Demander à l’usager de saisir son identifiant/mot de passe local. En effet, trop complexe, cette demande provoque l'abandon de l'usager.
- **Effectuer une réconciliation sur le SUB, car le SUB est calculé en fonction du FI utilisé.**

6. **Cinématique - Réconciliation de compte "générale" (Pour les accès suivants de l’utilisateur à ce même Fournisseur de Service)**

A partir de quelle(s) donnée(s) le traitement du Fournisseur de Service identifie l'utilisateur ?

7. **Cinématique - Déconnexion**

La déconnexion fonctionne : je peux me déconnecter d'AgentConnect et du Fournisseur d'Identité utilisé sur le service.

## Les aspects sécurité

1. **Interdiction des pop-ups et iframes**

Les fenêtres pop-ups et iframes sont interdites.

2. **Vérification de la connexion**

L'usager doit pouvoir identifier clairement qu'il est connecté et son profil accessible.

3. **Scopes**

Les scopes appelés sont les mêmes que ceux déclarés et autorisés dans le formulaire Démarches-Simplifiées.

4. **TLS**

Le service ne doit pas utiliser de version de TLS inférieur à 1.2 et doit obligatoirement utilisé des versions 1.2 ou 1.3.
