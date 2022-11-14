
# Détail du fonctionnement

![doc_fs_fca](https://user-images.githubusercontent.com/60473902/195838387-10aa22ef-f83f-4b12-abf7-dad3ec7828e4.png)

                        
La récupération de l'identité pivot doit être faite dans la suite immédiate des appels précédents (authentification et récupération du code). Le fait d'appeler ce Web service plus tard n'est aujourd'hui pas proposé.

# Détail des flux

Les flux entre AgentConnect et le Fournisseur de Services respectent ce qui est défini dans la norme OpenId Connect. Pour plus de détails, il faut se référer à la [documentation OIDC - https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth)

---

Voir aussi : 
- [Quelles sont les données que je peux récupérer par AgentConnect sur mes usagers?](projet_fca/projet_fca_donnees.md)
- [Qu'est ce qu'eIDAS et quel est le niveaux de garantie d'AgentConnect?](projet_fca/projet_fca_niveau_eidas.md)
- [Qu'est ce que le protocole OpenID Connect?](technique_fca/technique_oidc.md)
- [Comment AgentConnect utilise OpenID Connect?](technique_fca/technique_fca_oidc.md)
- [Quelles sont les données d'AgentConnect qui expirent?](technique_fca/donnees_expirent.md)
- [Comment utiliser les scopes OpenID Connect pour accéder aux données des utilisateurs? ](technique_fca/technique_fca_scope.md)
