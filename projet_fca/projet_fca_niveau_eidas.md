# Qu'est ce qu'eIDAS et quel est le niveau de garantie d'AgentConnect?

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


## Quel est le niveaux eIDAS supporté par la plateforme AgentConnect

AgentConnect s'inspire du règlement eIDAS pour définir les différents niveaux de sécurité dans les échanges avec les Fournisseurs d'Identité et les Fournisseurs de Services.

Dans le code AgentConnect les niveaux suivants sont définis :

* eidas1 : Niveau faible
* eidas2 : Niveau renforcé
* eidas3 : Niveau élevé

Actuellement les Fournisseurs de Services ne peuvent demander qu'un niveau 1, soit un niveau dit faible AgentConnect.

Comme la norme OpenID Connect ne prévoit pas aujourd'hui de mesures techniques particulières pour préciser le niveau souhaité, AgentConnect utilise le claim "acr" (http://openid.net/specs/openid-connect-basic-1_0.html#RequestParameters) de la norme OpenID Connect. 

Pour le Fournisseur de Services, cela veut dire remplir le claim acr_values lors de la demande d'authentification (appel à l'endpoint /api/v2/authorize). Ce claim est **obligatoire** sur AgentConnect. 

acr_values=eidas1

Le Fournisseur d'Identité renverra par le biais d'AgentConnect le niveau eIDAS avec lequel l'authentification a eu lieu. 

---

Voir aussi : 
- [Quel est le détail du fonctionnement?](../fonctionnement_fca/details_fonctionnement.md)
- [Quels sont les endpoints sur AgentConnect (le contrat d'interface)?](../technique_fca/endpoints.md)
- [Quelles sont les données que je peux récupérer par AgentConnect sur mes usagers?](../projet_fca/projet_fca_donnees.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs? ](../technique_fca/technique_fca_scope.md)
- [Quelles sont les données d'AgentConnect qui expirent?](../technique_fca/donnees_expirent.md)
