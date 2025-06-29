# Role: gitops

## Purpose
This role integrates the Ansible deployment with ArgoCD for GitOps-based delivery. When merged to `main`, the desired state in this repository is automatically deployed to the Kubernetes cluster via ArgoCD.

## Variables
- `argocd_version`: Version of the ArgoCD CLI to install (e.g., `v2.7.7`).
- `argocd_server`: URL of the ArgoCD API server.
- `vault_argocd_user`: Vaulted ArgoCD username for CLI login.
- `vault_argocd_password`: Vaulted ArgoCD password for CLI login.
- `git_repo_url`: HTTPS URL of this Git repository (e.g., `https://github.com/org/repo.git`).

## Tasks
1. **Install ArgoCD CLI**: Downloads and installs the ArgoCD binary.
2. **Login to ArgoCD**: Authenticates via CLI using vaulted credentials.
3. **Create ArgoCD Application**: Defines the application pointing to this repo’s `main` branch and configures automated sync with self-heal policy.
4. **Sync Application**: Performs an initial sync to apply the current desired state.

## Usage
Invoke this role after provisioning and deploying core infrastructure to set up continuous deployment via ArgoCD. Ensure that the Kubernetes context is configured and ArgoCD server is reachable.
