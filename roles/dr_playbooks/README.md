# Role: dr_playbooks

## Purpose
Provides disaster recovery runbooks automating data restoration and service failover into a DR site, enabling rapid recovery of core services.

## Variables
- `dr_vars` loaded from `site_vars/dr.yml` including `db_host`, `db_user`, `db_password`, and `orchestrator_host`.

## Tasks
1. **DR Variables**: Loads site_vars for the DR environment.
2. **Backup Restore**: Restores the latest Postgres dump into the DR database.
3. **Service Deployment**: Deploys orchestrator stack in the DR cluster via Docker Compose.
4. **GitOps Sync**: Triggers ArgoCD app sync for DR to align state.
5. **Health Verification**: Checks DR service readiness before marking recovery complete.

## Usage
Run this role in the event of primary site failure, passing `-e site_name=dr` to target DR configurations. Ensures data and services are restored and verified.
