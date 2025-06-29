# Role: immutable_infrastructure

## Purpose
Uses Packer to create golden LXC and VM templates in Proxmox, ensuring immutable infrastructure for faster, consistent provisioning.

## Variables
- `packer_version`: The version of Packer to install.
- Proxmox credentials: `pve_host`, `pve_user`, `pve_password`.

## Tasks
1. Download and install Packer.
2. Define Packer JSON templates for LXC (and VMs if needed).
3. Execute `packer build` to generate Proxmox templates.

## Usage
Run this role to generate or update base images before standard provisioning roles, ensuring idempotent, consistent nodes.
