# Role: drift_detection

## Purpose
Implements periodic configuration drift detection and automatic remediation by running Ansible in check mode and then applying fixes if changes are found.

## Variables
None.

## Tasks
1. **Install Ansible**: Ensures Ansible is present on the control node or target.
2. **Create Wrapper Script**: Generates `drift_detect.sh` to run drift checks and apply remediation.
3. **Cron Schedule**: Sets up an hourly cron job to invoke drift detection.

## Usage
Include this role on the control host to maintain continuous configuration compliance across all managed nodes.
