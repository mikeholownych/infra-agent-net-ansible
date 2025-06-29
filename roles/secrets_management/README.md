# Role: secrets_management

## Purpose
Implements Secret Zero by retrieving dynamic credentials from HashiCorp Vault at runtime, avoiding static storage of sensitive information.

## Variables
- `vault_version`: Version of Vault CLI to install.
- `vault_addr`: URL of the Vault server (e.g., `https://vault.example.com`).
- `vault_token`: Initial root or AppRole token to authenticate with Vault (must be provided securely via CI/CD or environment).

## Tasks
1. **Install Vault CLI**: Downloads and installs the Vault binary.
2. **Authenticate to Vault**: Logs in using a one-time token.
3. **Retrieve Secrets**: Reads secrets for DB, ArgoCD, Slack, etc., from Vault KV engine.
4. **Set Facts**: Exposes retrieved secrets as Ansible facts for use by other roles.

## Usage
Run this role at the start of playbook execution so that all roles can consume dynamic secrets via the established facts.
