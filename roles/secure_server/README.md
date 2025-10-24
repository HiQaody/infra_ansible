Ce rôle installe pgAdmin4 en mode sécurisé :

- Reverse proxy Nginx avec SSL (auto-signé par défaut ou cert fourni)
- Redirection HTTP→HTTPS
- Accès restreint aux IPs listées dans `pgadmin_allowed_ips`
- Headers HTTP de sécurité activés

Variables de sécurité :

- pgadmin_ssl_enabled : active le SSL (défaut true)
- pgadmin_ssl_cert_src / pgadmin_ssl_key_src : chemins des fichiers fournis (ou vide pour auto-signé)
- pgadmin_allowed_ips : liste blanche d’IP autorisées (deny all par défaut)

Pour utiliser tes propres certificats, place-les dans `roles/pgadmin/files/` et renseigne leur chemin dans `group_vars/all.yml`.

Pour un accès sécurisé, adapte la liste d’IP à tes besoins et utilise des vrais certificats en prod.
