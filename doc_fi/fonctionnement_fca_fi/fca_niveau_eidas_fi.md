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

AgentConnect est concerné uniquement par le volet identification électronique du règlement. 

## Qu'est ce que les niveaux de garantie eIDAS ?

Le niveau de garantie eIDAS permettre d'apporter une garantie sur l'identité qui est fournie au Fournisseur de Services. Ils sont définis par le règlement eIDAS avec chacun des exigences différentes. 

> * **Faible :** à ce niveau, l’objectif est simplement de réduire le risque d’utilisation abusive ou d’altération de l’identité ;
> * **Substantiel :** à ce niveau, l’objectif est de réduire substantiellement le risque d’utilisation abusive ou d’altération de l’identité ;
> * **Élevé :** à ce niveau, l’objectif est d’empêcher l’utilisation abusive ou l’altération de l’identité.

Source : [Présentation du règlement eIDAS par l'ANSSI](https://www.ssi.gouv.fr/administration/reglementation/confiance-numerique/le-reglement-eidas/#:~:text=Substantiel%20%3A%20%C3%A0%20ce%20niveau%2C%20l,'alt%C3%A9ration%20de%20l'identit%C3%A9.)

Le détail des exigeances est défini par [le règlement d’exécution n°2015/1502 du 8 septembre 2015](http://eur-lex.europa.eu/legal-content/FR/TXT/PDF/?uri=CELEX:32015R1502&from=FR)

## Utiliser les niveaux eIDAS en tant que Fournisseur d'Identité

AgentConnect s'inspire du règlement eIDAS pour définir les différents niveaux de sécurité dans les échanges avec les FI et les FS. 

Dans le code AgentConnect les niveaux suivants sont définis :

* eidas1 : Niveau faible
* eidas2 : Niveau renforcé
* eidas3 : Niveau élevé

Le Fournisseur d'Identité doit signifier à AgentConnect avec quel niveau eIDAS l'authentification de l'agent s'est faite. 

Dans le cadre du Fournisseur d'Identité, cela se traduit par le fait de positionner le claim "acr" dans l'ID Token renvoyé au client (http://openid.net/specs/openid-connect-core-1_0.html#rfc.section.2). De la même manière que pour un FS demandant à AgentConnect de filtrer les FIs compatibles avec un niveau eIDAS particulier.

Le claim acr retourné dans l'ID Token peut être :

* eidas1 : Niveau faible
* eidas2 : Niveau renforcé
* eidas3 : Niveau élevé

Cette donnée est retournée à AgentConnect, qui lui la retourne au Fournisseur de Services sans la modifier.
Elle contribue à autoriser ou non l'accès aux ressources. 

---

Voir aussi : 
- [Qu'est ce que le protocole OpenID Connect ?](doc_fi/technique_fca_fi/technique_oidc_fi.md)
- [Comment AgentConnect utilise OpenID Connect ?](doc_fi/technique_fca_fi/technique_fca_oidc_fi.md)
- [Quelles sont les données utilisateur que je dois fournir ?](doc_fi/technique_fca_fi/donnees_utilisateurs_fi.md)
- [Quels sont les endpoints sur AgentConnect ?](doc_fi/fonctionnement_fca_fi/endpoints_fi.md)
- [Quel est le détail du fonctionnement ?](doc_fi/fonctionnement_fca_fi/details_fonctionnement_fi.md)
- [Quel est le détail des flux ?](doc_fi/fonctionnement_fca_fi/details_flux_fi.md)
- [Quels sont les certificats d'authentification ?](doc_fi/fonctionnement_fca_fi/certificats_fi.md)
- [Comment accéder aux différents environnements d'AgentConnect ?](doc_fi/test_fca_fi/fca_env_fi.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](doc_fi/test_fca_fi/test_fca_demonstrateur_fi.md)