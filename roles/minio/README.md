# Rôle Ansible MinIO

Ce rôle déploie MinIO standalone via Docker.

**Variables principales :**

- `minio_port` : port externe (défaut 9001)
- `minio_data_dir` : dossier hôte pour la persistance des données
- `minio_access_key` : clé d'accès root (auto-générée si vide)
- `minio_secret_key` : clé secrète root (auto-générée si vide)
- `minio_ssl` : active SSL si true (disabled par défaut)
- `minio_ssl_cert_src` et `minio_ssl_key_src` : chemins vers fichiers SSL à copier (laisser vide pour auto-signé)

**Comportement :**

- Génère des credentials robustes si rien n'est fourni
- Prend en charge le SSL (auto-signé si rien n'est fourni)
- Persistance des données docker dans `minio_data_dir`
- Affiche les accès root à la fin

**Utilisation :**

1. Définir les variables dans `group_vars/all.yml`
2. Inclure le rôle dans votre playbook
3. Accéder à MinIO via :
   - http(s)://<ip>:<minio_port> (console web)
