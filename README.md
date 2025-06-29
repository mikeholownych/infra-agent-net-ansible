# Ansible Scaffold

This repository provides a complete, production-grade Ansible scaffold for provisioning, configuring, and deploying infrastructure via roles.

## Overview

- **Provisioning**: Create VMs, containers
- **Immutable Infrastructure**: Build images with Packer
- **GitOps**: Deploy via ArgoCD
- **Blue/Green Deployments**: Switch traffic
- **Secrets Management**: Vault integration
- **Compliance & Audit**: OPA, Fluentd, SIEM
- **Self-service Portal**: ArgoCD-based portal

## Prerequisites

- Control node:
  - Ansible ≥ 2.13
  - Python 3.x
  - `ansible-lint` (for linting)
- Required CLIs (if used by roles):
  - `packer`
  - `vault`
  - `argocd`
  - `opa`
  - `fluentd`
- Inventory: `inventory/production.yml`
- Variables:
  - Global: `group_vars/all.yml` (includes `site_name`)
  - Role-specific: `roles/<role>/defaults/main.yml`

## Getting Started

```bash
# Syntax check
ansible-playbook playbook.yml --syntax-check -i inventory/production.yml

# Dry-run with diffs
ansible-playbook playbook.yml -i inventory/production.yml --check --diff

# Full run
ansible-playbook playbook.yml -i inventory/production.yml
```

## Configuration

1. Populate `group_vars/all.yml`:
   - Set `site_name`
2. Edit role defaults in `roles/<role>/defaults/main.yml` with actual values.
3. Ensure secrets are stored with Ansible Vault.

## Contributing

Contributions are welcome! Please:
1. Fork the repo
2. Create a feature branch
3. Submit a pull request with lint checks passing

