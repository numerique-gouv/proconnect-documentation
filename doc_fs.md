[Accueil](https://github.com/france-connect/Documentation-AgentConnect/blob/main/README.md) > AgentConnect - Fournisseur de Service

___

# AgentConnect - Fournisseur de Service



Vous souhaitez implémenter AgentConnect sur votre site? Vous êtes au bon endroit ! Cette documentation présente l'ensemble des informations à connaître.

## 1. 👩‍🏫 Préambule

Cette documentation est à destination des Fournisseurs de Services souhaitant intégrer AgentConnect. AgentConnect est implémenté sur deux plateformes, une dite "RIE" (l’agent se connecte depuis le RIE, à un FS RIE via un FI RIE) et une autre dite "Internet" (l'agent se connecte depuis Internet, à un FS Internet via un FI Internet). Toutefois il est possible de communiquer entre les deux plateformes grâce à "l'hybridge Internet/RIE" (l'agent se connecte depuis Internet, à un Fournisseur de Services Internet via un FI RIE).


## 2. ⚙️ Les étapes pour intégrer AgentConnect


Vous souhaitez devenir Fournisseur de Services pour AgentConnect, voici les éléments à prendre en compte :

- [Quelles sont les étapes pour devenir Fournisseur de Services ?](doc_fs/pilotage_fca/pilotage_fca_etapes.md)

___

**🤓 TL;DR**

Voici un résumé des étapes pour être fournisseur de service AgentConnect :

- [ ] Je me familiarise avec la cinématique OpenIDConnect : voir [concepts de base](https://github.com/france-connect/Documentation-AgentConnect/blob/main/doc_fs.md#31-je-souhaite-conna%C3%AEtre-le-concept-de-base-dagentconnect)
- [ ] [_Optionnel_] Je contacte l'équipe AgentConnect pour qu'elle puisse répondre à mes questions si j'en ai : support.partenaires@agentconnect.gouv.fr ou [sur notre chaîne Tchap](https://www.tchap.gouv.fr/#/room/!kBghcRpyMNThkFQjdW:agent.dinum.tchap.gouv.fr)
- [ ] Je souhaite lancer les développements en test, pour ceci je renseigne à l'équipe AgentConnect les informations techniques comme les `redirect_uris` ou `post_logout_redirect_uris` en remplissant [un formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca)
- [ ] J’ai récupéré mon `client_id` et mon `client_secret` de test auprès de l’équipe AgentConnect
- [ ] J’affiche un bouton AgentConnect conforme sur mon application en environment de développement : voir [Spécifications visuelles](https://github.com/france-connect/Documentation-AgentConnect/blob/main/doc_fs.md#37-je-souhaite-connaitre-les-sp%C3%A9cifications-visuelles-dagentconnect)
- [ ] J’ai installé et paramétré mon client OpenID sur mon application en développement : voir [Spécifications techniques](https://github.com/france-connect/Documentation-AgentConnect/blob/main/doc_fs.md#3--jint%C3%A8gre-agentconnect-dans-mon-service-en-ligne)
- [ ]  Mon implémentation fonctionne
- [ ]  Je contractualise officiellement ma collaboration avec la Dinum en remplissant le [DataPass dédié](https://datapass.api.gouv.fr/agent-connect-fs)
- [ ]  Le DataPass étant validé, j’ai récupéré mon `client_id` et mon `client_secret` de production en remplissant [le formulaire dédié](https://www.demarches-simplifiees.fr/commencer/demande-creation-fs-fca) avec les informations de production
- [ ]  Mise en production 🚀

___



## 3. 💻 J'intègre AgentConnect dans mon service en ligne

### 3.1. Je souhaite connaître le concept de base d'AgentConnect

- [Qu'est ce que le protocole OpenID Connect ?](doc_fs/technique_fca/technique_oidc.md)
- [Comment AgentConnect utilise OpenID Connect ?](doc_fs/technique_fca/technique_fca_oidc.md)
- [Quelles sont les données que je peux récupérer par AgentConnect sur les agents ?](doc_fs/projet_fca/projet_fca_donnees.md)

### 3.2. Je veux savoir comment fonctionne AgentConnect et comment identifier/authentifier les agents

- [Quel est le détail du fonctionnement ?](doc_fs/fonctionnement_fca/details_fonctionnement.md)
- [Quels sont les endpoints sur AgentConnect (le contrat d'API) ?](doc_fs/technique_fca/endpoints.md)
- [Quelles sont les données que je peux récupérer par AgentConnect sur mes usagers ?](doc_fs/projet_fca/projet_fca_donnees.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs ? ](doc_fs/technique_fca/technique_fca_scope.md)
- [Quelles sont les données d'AgentConnect qui expirent ?](doc_fs/technique_fca/donnees_expirent.md)
- [Qu'est ce qu'eIDAS et quel est le niveau de garantie d'AgentConnect ?](doc_fs/projet_fca/projet_fca_niveau_eidas.md)

### 3.3. Je veux savoir comment intégrer le bouton AgentConnect

- [Comment intégrer AgentConnect techniquement](doc_fs/./technique_fca/mode_emploi.md)
- [Quel bouton AgentConnect intégrer et comment l'intégrer visuellement ?](doc_fs/implementation_fca/bouton_fca.md)
- [Troubleshooting](doc_fs/./technique_fca/troubleshooting.md)

### 3.4. Je veux savoir comment déconnecter l'agent d'AgentConnect

- [Comment déconnecter l'agent d'AgentConnect ?](doc_fs/deconnexion_fca/deconnexion.md)
- [Comment révoquer l'access token ?](doc_fs/deconnexion_fca/access_token.md)

### 3.5. Je veux connaître les différents environnements disponibles

- [Comment accéder aux différents environnements d'AgentConnect ?](doc_fs/technique_fca/technique_fca_env.md)
- [Quels démonstrateurs sont disponibles sur la plateforme intégration (test) d'AgentConnect ?](doc_fs/test_fca/test_fca_demonstrateur.md)

### 3.6. Je souhaite obtenir des informations sur la gestion d'erreurs entre AgentConnect et le Fournisseur de Services

- [Comment les erreurs entre AgentConnect et le Fournisseur de Services sont-elles gérées ?](doc_fs/erreur_fca/gestion_erreur.md)

### 3.7. Je souhaite connaitre les spécifications visuelles d'AgentConnect

- [Quel bouton AgentConnect intégrer et comment l'intégrer ?](doc_fs/implementation_fca/bouton_fca.md)
- [Quels sont les prérequis et les spécifications à respecter pour réussir  l'implémentation ?](doc_fs/implementation_fca/spec_recette_fca.md)

## 4. 🚀 Je souhaite mettre mon Fournisseur de Services en production

- [Comment recevoir mes jetons de production ?](doc_fs/recette_fca/recette_cles_prod.md)



## 5. 📚 Ressources supplémentaires

- [Quels sont les acteurs à impliquer dans l'intégration d'AgentConnect ?](doc_fs/pilotage_fca/pilotage_fca_demarches_acteurs.md)
- [Qu'est-ce que la plateforme "Internet", la plateforme "RIE" et l'"Hybridge" ?](doc_fs/pilotage_fca/plateformes.md)
- [Contrat d'API AgentConnect](doc_fs/./technique_fca/endpoints.md)
- [Glossaire](doc_fs/./technique_fca/glossaire.md)

