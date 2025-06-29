# Role: hardening

## Purpose
Applies OS and container security hardening as well as performance tuning based on CIS benchmarks and best practices.

## Variables
None.

## Tasks
1. **Sysctl Tuning**: Sets optimized kernel parameters for networking and memory.
2. **AppArmor Enforcement**: Installs and ensures AppArmor profiles are enforced.
3. **SSH Hardening**: Applies CIS-compliant SSH configuration.
4. **Docker Lockdown**: Configures Docker daemon options to reduce attack surface.

## Templates
- `templates/sshd_config_cis`: Hardened SSH configuration file according to CIS.

## Usage
Include this role to enforce security and performance baseline across all hosts before deploying application components.
