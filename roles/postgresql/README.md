Ce rôle installe PostgreSQL sur Ubuntu/Debian et permet la configuration du port et la création d'utilisateurs/bases.

Variables :

- postgresql_port : port d'écoute de PostgreSQL (défaut : 5432)
- postgresql_version : version majeure à installer (défaut : 15)
- postgresql_users : liste d'utilisateurs/bases à créer (voir group_vars/all.yml)

Handlers :

- Redémarrer PostgreSQL en cas de modification de la configuration

Utilisation :
Définir les variables souhaitées dans group_vars/all.yml et inclure le rôle dans votre playbook.
