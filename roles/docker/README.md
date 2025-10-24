Ce rôle installe Docker CE sur un système Ubuntu/Debian.

Variables :

- docker_users : liste des utilisateurs à ajouter au groupe docker (par défaut : ansible_user)

Handlers :

- Redémarrer Docker si la configuration change

Pour l’utiliser, ajoute 'docker' à la liste des rôles dans ton playbook principal.
