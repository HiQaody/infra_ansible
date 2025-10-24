# Rôle Ansible Portainer

Ce rôle déploie Portainer CE via Docker, avec gestion complète du port, du SSL et du mot de passe admin initial.

**Variables principales :**

- `portainer_port` : port externe d'écoute (9443 pour HTTPS, 9000 pour HTTP)
- `portainer_ssl` : active SSL si true (par défaut false)
- `portainer_ssl_cert_src` et `portainer_ssl_key_src` : chemins vers fichiers SSL à copier (laisser vide pour auto-généré)
- `portainer_data_volume` : dossier hôte pour la persistance des données
- `portainer_admin_password` : mot de passe admin initial (Portainer >=2.9)

**Comportement :**

- Si SSL activé et pas de fichiers fournis, un certificat auto-signé est généré
- Si SSL désactivé, Portainer écoute sur HTTP
- Le conteneur est relancé si besoin (upgrade ou changement config)

**Usage :**

1. Définir les variables dans `group_vars/all.yml`
2. Inclure le rôle dans votre playbook principal
3. Accéder à Portainer via :
   - https://<votre_ip>:9443 (SSL)
   - http://<votre_ip>:9000 (HTTP)

> Pour une sécurité avancée, combinez ce rôle avec un proxy Nginx/Traefik, Let's Encrypt, filtrage IP ou VPN.
