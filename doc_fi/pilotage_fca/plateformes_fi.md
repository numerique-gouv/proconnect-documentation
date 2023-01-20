# Qu'est-ce que la plateforme "Full Internet", la plateforme "Full RIE" et l'"Hybridge" ?

AgentConnect est implémenté sur deux plateformes, une dite "full RIE" et une autre dite "full Internet". Toutefois il est possible de communiquer entre les deux plateformes grâce à "l'hybridge Internet/RIE".

Le choix du positionnement sur le RIE ou sur Internet est « à la main » des Fournisseurs d'Identité et des Fournisseurs de Services.

## Les plateformes d’AgentConnect

AgentConnect met à disposition 3 plateformes pour répondre aux exigences de l’ANSSI.

### La plateforme « Full Internet »

L'agent se connecte depuis Internet, à un Fournisseur de Services Internet via un Fournisseur d'Identité Internet.

Ex : Accès à l’outil collaboratif Osmose depuis le FI Cerbère (MTE)

### La plateforme « Full RIE »

L’agent se connecte depuis le RIE, à un Fournisseur de Services RIE via un Fournisseur d'Identité RIE.

Ex : Accès au portail du CISIRH depuis l’annuaire Passage 2 (MI)

### La plateforme Hybridge AgentConnect RIE-Internet

L'Hybridge permet de relier un Fournisseur d’Identité RIE à un Fournisseur de Services Internet (et non l'inverse)

|*FI/FS* | Fournisseur de Services RIE | Fournisseur de Services Internet |
|---- | ------ | ------ | 
|**Fournisseur d'Identité RIE** | Oui | Oui (via l'Hybridge)|
|**Fournisseur d'Identité Internet**| Non | Oui |



---

Voir aussi : 
- [Quelles sont les étapes pour devenir Fournisseur d'Identité ?](../pilotage_fca/pilotage_fca_etapes_fi.md)
- [Quels sont les acteurs à impliquer dans l'intégration d'AgentConnect ?](../pilotage_fca/pilotage_fca_demarches_acteurs_fi.md)
- [Comment accéder au formulaire datapass ?](../pilotage_fca/datapass_fi.md)
- [Comment accéder aux différents environnements d'AgentConnect ?](../test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](../test_fca_fi/test_fca_demonstrateur_fi.md)