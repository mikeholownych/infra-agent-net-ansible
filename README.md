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
  - `packer`, `vault`, `argocd`, `opa`, `fluentd`  
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

## Playbook Functions

This playbook leverages the following **roles** to fully automate your infrastructure and application deployments:

- **provisioning**  
  Creates virtual machines and LXC containers on Proxmox.

- **immutable_infrastructure**  
  Builds VM/container images with Packer for immutable deployments.

- **gitops**  
  Deploys applications and infrastructure via ArgoCD.

- **blue_green**  
  Manages blue/green traffic shifts for zero-downtime releases.

- **secrets_management**  
  Integrates HashiCorp Vault to securely store and fetch secrets.

- **testing_matrix**  
  Executes configuration and integration tests across multiple environments.

- **ci_quality_gates**  
  Enforces code quality with `ansible-lint`, container scanning (Trivy), and OPA policy checks.

- **multi_site**  
  Configures network interfaces for primary and DR sites with templated `network_{{ site_name }}.j2`.

- **self_service_portal**  
  Deploys an ArgoCD-powered web portal for on-demand service deployments.

- **docs_site**  
  Builds and serves documentation (e.g. via MkDocs) for your infrastructure and code.

- **audit**  
  Streams logs (Fluentd), enforces OPA audit rules, and integrates with your SIEM.

- **orchestrator**  
  Launches your orchestration application using Docker Compose v2.

- **backups**  
  Schedules daily PostgreSQL dumps and ZFS snapshots for data protection.

- **rbac**  
  Manages application users and roles via HTTP API calls.

---

## Contributing

Contributions are welcome! Please:

1. Fork the repository  
2. Create a feature branch  
3. Submit a pull request with all lint checks passing  
