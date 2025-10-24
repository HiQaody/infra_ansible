# Rôle Ansible : Kubernetes (kubectl & Docker)

Ce rôle installe les outils nécessaires pour intégrer Jenkins à un cluster Kubernetes :  
- `kubectl` (client Kubernetes)
- `docker` (pour les actions de build/push d’image dans Jenkins)

## Prérequis

- Jenkins installé sur le serveur cible
- Accès administrateur (sudo/root)
- Accès au cluster Kubernetes (K3s/K8s)
- Compte Docker Hub si besoin

## Variables

Les principales variables à définir (dans `group_vars/all.yml`) :

```yaml
kubernetes_kubectl_url: "https://dl.k8s.io/release/{{ kubectl_version }}/bin/linux/amd64/kubectl"
kubectl_version: "{{ lookup('url', 'https://dl.k8s.io/release/stable.txt') | trim }}"
kubectl_bin_path: "/usr/local/bin/kubectl"
docker_package: docker.io
```

## Tâches réalisées

- Mise à jour du système
- Installation de Docker
- Récupération et installation de la dernière version stable de `kubectl`
- Vérification des installations (`docker --version`, `kubectl version --client`)

## Exemple d’utilisation dans playbook

```yaml
- hosts: jenkins
  roles:
    - kubernetes
```

## Accès

- Docker : `docker --version`
- kubectl : `kubectl version --client`

## Notes

- Pour accéder à un cluster distant, configurez le fichier `~/.kube/config` sur la machine Jenkins.
- Pour installer d’autres utilitaires Kubernetes (helm, kustomize…), adaptez le rôle ou ajoutez des tâches.
