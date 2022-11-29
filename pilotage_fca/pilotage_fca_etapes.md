# Quelles sont les étapes pour devenir Fournisseur de Services ? 

**1.** Vous consultez les conditions d'éligibilité à AgentConnect. Les conditions juridiques, de sécurité et de qualité de service sont détaillées dans nos conditions générales d'utilisations:

- [Conditions Générales d'Utilisation AgentConnect FS v1.2](../cgu_fca/20210528-DINUM-AC-CGU_FS-v1.2.pdf)
- [Annexe des CGU FS v1.3](../cgu_fca/20210528-DINUM-AC-Annexe%20CGU%20FS-v1.3.pdf)

**2.** Vous soumettez une demande d'habilitation via [datapass.api.gouv.fr](https://datapass.api.gouv.fr/) et vous transmettez toutes les informations nécessaires à la validation de votre demande (**respect du RGPD**, contact du responsable technique, plateforme souhaitée, données recueillies, etc). Votre demande est validée par la DINUM dans un délai moyen de 5 jours ouvrés.

Le lien pour faire une demande datapass est le suivant: 

[Demande datapass pour un Fournisseur de Services](https://datapass.api.gouv.fr/agent-connect-fs)

**3.** Si votre demande est acceptée, le responsable technique peut alors se rendre sur le site [www.demarches-simplifiees.fr](https://www.demarches-simplifiees.fr/users/sign_in) afin de remplir le formulaire adéquat de demande d'enrôlement de votre Fournisseur de Services sur notre plateforme de test (plateforme d'intégration).

Les formulaires mis à disposition sont les suivants: 

*Environnement RIE*: 

- [Demande de création d'un fournisseur de services sur l'environnement d'intégration AgentConnect RIE](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-integration-fca-rie)

*Environnement Internet*: 

- [Demande de création d'un fournisseur de services sur l'environnement d'intégration AgentConnect Internet](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-integration-fca-internet)

Une fois votre Fournisseur de Services enrôlé sur la plateforme d'intégration, l'équipe AgentConnect transmet au responsable technique les clés d'intégration (client ID par email et client secret par sms) ainsi que la documentation technique vous permettant de commencer votre phase de développement et de tests. 

**4.** Le cadre d'implémentation et d'intégration à respecter est détaillé dans le paragraphe [Quels sont les prérequis ainsi que les spécifications à respecter au moment de l'implémentation ?](../implementation_fca/spec_recette_fca.md). N'hésitez pas à soumettre vos maquettes du parcours en amont pour une pré-qualification fonctionnelle et UX anticipée.

**5.** Vous présentez vos développements pour une qualification par l'équipe AgentConnect en vous rendant sur le site [www.demarches-simplifiees.fr](https://www.demarches-simplifiees.fr/users/sign_in) afin de remplir le formulaire de demande de recette : 

- [Demande de recette d'un fournisseur de services AgentConnect RIE / Internet / ou les deux](https://www.demarches-simplifiees.fr/commencer/demande-de-recette-fs-fca-rie-internet). 

> ATTENTION, si vous implémentez AgentConnect sur le RIE, UNE RECETTE EN VISIO DEVRA SE FAIRE CAR NOUS NE POUVONS ACCÉDER A VOTRE FOURNISSEUR DE SERVICES POUR TESTER LA CINEMATIQUE ET LE PARCOURS UTILISATEUR. Merci de nous contacter aux adresses suivantes elodie.boudouin@modernisation.gouv.fr et/ou melanie.wynd@prestataire.modernisation.gouv.fr afin de fixer ce point.

La délai de traitement de votre demande de qualification dépend du respect des prérequis listés dans le paragraphe [Quels sont les prérequis ainsi que les spécifications à respecter au moment de l'implémentation ?](../implementation_fca/spec_recette_fca.md) mais est estimé environ à 3 jours ouvrés.

**6.** Avant de faire votre demande de mise en production, il est obligatoire de contacter l'équipe AgentConnect par email (support.partenaires@agentconnect.gouv.fr) afin de les informer du mariage Fournisseur de Services / Fournisseur d'Identité souhaité. L'équipe AgentConnect vous communiquera également les éléments relatifs à la politique de sécurité et de gestion des mots de passe des Fournisseurs d’identité pour que vous indiquiez à l'équipe AgentConnect le(s) Fournisseur(s) d’identité que vous autorisez à accéder à votre service. 

**7**. Si votre implémentation est validée par l'équipe AgentConnect et si les informations nécessaires listées ci-dessus ont bien été transmises, le responsable technique peut alors se rendre sur le site [www.demarches-simplifiees.fr](https://www.demarches-simplifiees.fr/users/sign_in) afin de remplir le formulaire adéquat de demande d'enrôlement de votre Fournisseur de Services sur la plateforme de production.

Les formulaires mis à disposition sont les suivants: 

*Environnement RIE*: 

- [Demande de création d'un fournisseur de services sur l'environnement de production AgentConnect RIE](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-production-fca-rie)

*Environnement Internet*: 

- [Demande de création d'un fournisseur de services sur l'environnement de production AgentConnect Internet](https://www.demarches-simplifiees.fr/commencer/demande-de-creation-fs-production-fca-internet)

Une fois votre Fournisseur de Services enrôlé sur la plateforme de production, l'équipe AgentConnect transmet au responsable technique les clés de production (client ID par email et client secret par sms). 



---

Voir aussi : 
- [Quels sont les différents acteurs que je dois faire intervenir dans mon organisation pour devenir Fournisseur de Services ?](../pilotage_fca/pilotage_fca_demarches_acteurs.md)
- [Qu'est-ce que la plateforme "Full Internet", la plateforme "Full RIE" et "l'Hybridge" ?](../pilotage_fca/plateformes.md)
- [Comment accéder au formulaire datapass ?](../pilotage_fca/datapass.md)
- [Quel bouton AgentConnect intégrer et comment l'intégrer ?](../implementation_fca/bouton_fca.md)
- [Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?](../implementation_fca/spec_recette_fca.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration d'AgentConnect ?](../test_fca/test_fca_demonstrateur.md)
- [Comment faire qualifier mon implémentation ?](../recette_fca/recette.md)
- [Comment recevoir mes jetons de production ?](../recette_fca/recette_cles_prod.md)
