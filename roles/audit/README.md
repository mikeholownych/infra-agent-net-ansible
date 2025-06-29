# Role: audit

## Purpose
Integrates comprehensive audit logging and policy enforcement using OpenPolicyAgent (OPA) and the Linux audit framework, forwarding critical events to a SIEM for compliance and traceability.

## Variables
- `opa_version`: Version of OPA CLI to install (e.g., `1.3.0`).
- Vaulted SIEM endpoint and credentials for Fluentd.
- Paths for log files and policy directories.

## Tasks
1. **Install OPA CLI**: Downloads and installs the OPA binary for policy evaluation.
2. **Deploy OPA Server**: Runs an OPA container to serve policy APIs and decision logs.
3. **Load Policies**: Pushes local policy files into the OPA server.
4. **Configure Fluentd**: Templates and deploys Fluentd configuration to forward Ansible and system logs to the SIEM.
5. **Install auditd**: Ensures the Linux audit daemon is present and enabled.
6. **Apply Audit Rules**: Deploys custom audit rules to track system changes and accesses.

## Templates
- `templates/fluentd.conf.j2`: Fluentd configuration for SIEM forwarding.
- `templates/audit.rules`: System audit rules for critical file and login events.

## Usage
Include this role in the playbook to enforce and monitor policy compliance, ensuring that all Ansible runs and system events are auditable and centrally collected.
