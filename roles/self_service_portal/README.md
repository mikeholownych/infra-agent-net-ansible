# Role: self_service_portal

## Purpose
Deploys a Next.js-based self-service portal (or AWX survey UI) that allows non-privileged users to trigger standard workflows and spin up sandbox environments.

## Variables
- `portal_repo_url`: Git URL of the self-service portal repository.
- `portal_version`: Git branch or tag to deploy (e.g., `main`).
- `portal_port`: Port on which the portal listens (e.g., `4000`).

## Tasks
1. **Clone Repository**: Retrieves the portal code from the specified repo and version.
2. **Environment Configuration**: Renders `.env` from `roles/self_service_portal/templates/env.j2` with variables (e.g. API endpoints, auth tokens).
3. **Docker Compose Deploy**: Uses the included `docker-compose.yml` to build and run the portal.
4. **Health Check**: Polls the portal endpoint until a successful HTTP 200 response is received.

## Templates
- `env.j2`: Jinja2 template for environment variables (API URLs, auth secrets, etc.).

## Usage
Invoke this role after core services are up to deploy the self-service UI. Non-ops users can then access the portal to perform approved actions.
