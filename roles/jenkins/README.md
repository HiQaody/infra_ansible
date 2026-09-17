Ce rôle installe Jenkins sur Rocky Linux 10.

Variables :

- jenkins_port : le port sur lequel Jenkins écoute (défaut : 8080, peut être surchargé dans group_vars/all.yml).

Handlers :

- Redémarrer Jenkins si le port change.

Utilisation :
Ajoute 'jenkins' à la section roles: de ton playbook principal.
