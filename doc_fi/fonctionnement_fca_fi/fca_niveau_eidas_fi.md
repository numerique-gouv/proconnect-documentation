# Qu'est ce qu'eIDAS et comment utiliser les niveaux eIDAS en tant que Fournisseurs d'Identité ?

## Qu'est ce que le règlement eIDAS ? 

> Le règlement n° 910/2014 sur l'identification électronique et les services de confiance pour les
transactions électroniques au sein du marché intérieur, dit règlement « eIDAS », est un règlement
européen qui a été adopté le 23 juillet 2014 par le Parlement européen et le Conseil de l'Union
Européenne. L'objectif de ce règlement est de mettre en place un cadre juridique propre à
susciter une confiance accrue dans les transactions électroniques au sein du marché intérieur. 
>
> Le règlement eIDAS s'applique à l’identification électronique et aux services de confiance
(faisant respectivement l’objet des chapitres II et III du présent document). Il accorde également
un effet juridique aux documents électroniques.

Source : [FAQ eIDAS de l'ANSSI](https://www.ssi.gouv.fr/uploads/2017/01/eidas_faq_anssi.pdf)

Pour plus d'informations à ce sujet nous vous invitons à consulter également le lien suivant :

- [FAQ eIDAS de l'ANSSI](https://www.ssi.gouv.fr/uploads/2017/01/eidas_faq_anssi.pdf)

## Utiliser les niveaux eIDAS en tant que Fournisseur d'Identité

AgentConnect s'inspire du règlement eIDAS pour définir les différents niveaux de sécurité dans les échanges avec les Fournisseurs d'Identité et les Fournisseurs de Services. 

Dans le code AgentConnect les niveaux suivants sont définis :

* eidas1 : Niveau faible
* eidas2 : Niveau renforcé
* eidas3 : Niveau élevé

Le Fournisseur d'Identité doit signifier à AgentConnect avec quel niveau eIDAS l'authentification de l'agent s'est faite. 

Dans le cadre du Fournisseur d'Identité, cela se traduit par le fait de positionner le claim "acr" dans l'ID Token renvoyé au client (http://openid.net/specs/openid-connect-core-1_0.html#rfc.section.2).

Le claim acr retourné dans l'ID Token peut être :

* eidas1 : Niveau faible
* eidas2 : Niveau renforcé
* eidas3 : Niveau élevé

**Toutefois, attention, actuellement les Fournisseurs de Services ne peuvent demander qu'un niveau 1, soit un niveau dit faible AgentConnect soit acr_values=eidas1. **

Uniquement le niveau 1 est supporté par AgentConnect pour le moment.
