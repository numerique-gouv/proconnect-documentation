
# Quel bouton AgentConnect intégrer et comment l'intégrer?

## Intégration d'un bouton AgentConnect 

Les boutons d’action AgentConnect sont primordiaux dans l’usage du service. Il est obligatoire d’utiliser l’un des boutons proposés et aucun autre visuel pour la connexion des usagers. 

Pour les boutons en svg, lors de l'utilisation d'une image veuillez préciser la taille du bouton.

*Téléchargements :*

[AgentConnect-Bouton.zip](https://github.com/france-connect/Documentation-AgentConnect/files/9828293/AgentConnect-Bouton.zip)

## Règles d'intégration du bouton AgentConnect

Les règles suivantes doivent être respectées:

- le design, les couleurs et le label du bouton AgentConnect ne peuvent pas être modifiés,
- le bouton bleu AgentConnect est à utiliser en priorité,
- l'état au survol doit être implémenté,
- la taille recommandée pour une utilisation optimale est de 60 pixels de haut par 230 px de large,
- le bouton AgentConnect doit être positionné en premier mode d'authentification,
- il doit être présent dans les sections connexion et inscription (si applicable) du site,
- il doit être séparé des autres modes de connexion/d'inscription:

    Il est important de dissocier visuellement les différents moyens d’authentification : une séparation visible doit être mise en place entre eux.
    La mention "OU" doit également y figurer afin de faire comprendre à l'utilisateur qu'il peut choisir entre AgentConnect ou un autre mode de connexion/d'inscription.

- sous le bouton AgentConnect, il vous sera demandé d'ajouter systématiquement un lien avec le texte " Qu'est-ce qu'AgentConnect" qui pointera vers le site https://agentconnect.gouv.fr/,
- votre intégration doit respecter le référentiel général d’amélioration de l’accessibilité (RGAA).

![Guidelines AgentConnect](https://user-images.githubusercontent.com/60473902/196908275-3fe6872f-cb75-4c1d-92af-fea67cbf89ae.png)





---

Voir aussi : 
- [Quelles sont les étapes pour devenir Fournisseur de Services?](../pilotage_fca/pilotage_fca_etapes.md)
- [Quels sont les prérequis ainsi que les spécifications à respecter au moment de l'implémentation?](implementation_fca/spec_recette_fca.md)
- [Comment faire qualifier mon implémentation?](recette_fca/recette.md)
- [Comment recevoir mes jetons de production?](../recette_fca/recette_cles_prod.md)