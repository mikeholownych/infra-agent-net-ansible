# Role: blue_green

## Purpose
Implements blue/green deployments (and canary rollouts) by deploying parallel environments, running health checks, switching traffic, and tearing down the previous version.

## Variables
- None required; relies on a `loadbalancer-cli` tool in PATH.

## Tasks
1. **Determine Active Color**: Queries the load balancer to find which color (`blue`/`green`) is live.
2. **Set Target Color**: Chooses the opposite environment for deployment.
3. **Deploy Stack**: Uses Docker Compose to launch services under a namespaced project (e.g., `app_green`).
4. **Health Validation**: Waits until the newly deployed environment responds successfully.
5. **Switch Traffic**: Uses `loadbalancer-cli` to point production traffic to the new environment.
6. **Teardown Old**: Removes the previous environment’s containers to free resources.

## Usage
Include this role in a playbook when deploying new versions to minimize downtime and enable instant rollbacks if health checks fail.
