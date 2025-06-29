# Role: dynamic_inventory

## Purpose
Automatically discovers Proxmox VMs and LXCs via the Proxmox API and builds an Ansible inventory at runtime.

## Variables
- `PVE_HOST`, `PVE_USER`, `PVE_PASS`: Proxmox API credentials (from environment or vault).

## Tasks
1. Installs the `proxmoxer` Python library for API access.
2. Deploys a custom dynamic inventory script to `/usr/local/bin`.
3. Updates `ansible.cfg` to use the new inventory script.

## Usage
Include this role early in the playbook or invocation to replace static inventory with dynamic discovery.
