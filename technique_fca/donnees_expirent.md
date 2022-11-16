
# Les données d’AgentConnect qui expirent

AgentConnect gère plusieurs types de données ayant une durée de vie limitée lors du déroulé d'une authentification par OpenID Connect ou de la fourniture d'un jeton d'accès à une ressource protégée (cinématique OAuth2 classique). Chacune de ces données possède une durée de vie qui lui est propre au-delà de laquelle elle doit être régénérée. En voici le détail :


| Type | Utilisé lors de ... | Durée de vie |
| ------ | ------ | ------ |
| Access Token | Récupération d'informations (phase 3 cinématique d'authentification / cinématique OAuth2) | 60 secondes |
| Authorization code | Code fourni lors du début de la démarche d'authentification, il sert ensuite à récupérer l'access token | 30 secondes |

---

Voir aussi : 
- [Qu'est ce que le protocole OpenID Connect?](../technique_fca/technique_oidc.md)
- [Comment AgentConnect utilise OpenID Connect?](../technique_fca/technique_fca_oidc.md)