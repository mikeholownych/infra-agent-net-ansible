# Role: multi_site

## Purpose
Allows deployment across multiple Proxmox clusters or sites (e.g., primary and DR) by loading site-specific variables and grouping hosts accordingly.

## Variables
- `site_name`: Name of the site context, e.g., `primary` or `dr`.
- `site_vars/<site_name>.yml`: Contains host lists, cluster names, network configs for each site.

## Tasks
1. **Load Site Variables**: Reads the YAML file for the current site.
2. **Group Hosts**: Dynamically creates inventory groups (`primary_site`, `dr_site`).
3. **Site Network Config**: Applies network templates specific to each site.
4. **Deploy Across Sites**: Runs the main playbook tasks against both groups.

## Usage
Invoke this role with `-e site_name=primary` and then `-e site_name=dr` in separate runs, or loop over site names in a master playbook for multi-site orchestration.
