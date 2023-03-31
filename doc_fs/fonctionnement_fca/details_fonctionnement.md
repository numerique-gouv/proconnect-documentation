# Quel est le détail du fonctionnement ?

![doc_fs_fca](https://user-images.githubusercontent.com/60473902/195838387-10aa22ef-f83f-4b12-abf7-dad3ec7828e4.png)

                        
La récupération des données obligatoires doit être faite dans la suite immédiate des appels précédents (authentification et récupération du code). Le fait d'appeler ce Web service plus tard n'est aujourd'hui pas proposé.

# Détail des flux

Les flux entre AgentConnect et le Fournisseur de Services respectent ce qui est défini dans la norme OpenId Connect. Pour plus de détails, il faut se référer à la [documentation OIDC - https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth)
