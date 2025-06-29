# Role: ci_quality_gates

## Purpose
Implements security and policy quality gates in the CI/CD pipeline, scanning IaC and container images for vulnerabilities and policy violations.

## Variables
- `trivy_version`: Version of Trivy to install (e.g., `0.36.1`).
- `opa_version`: Version of OPA CLI to install (e.g., `1.3.0`).
- `docker_image`: Full name of the container image to scan (e.g., `myrepo/app:latest`).

## Tasks
1. **Install Checkov**: Scans Terraform, CloudFormation, and other IaC.
2. **Install Trivy**: Scans container images for vulnerabilities.
3. **Install OPA CLI**: Evaluates policies under `policies/`.
4. **Run Checkov**: Fails on any IaC policy violations.
5. **Run OPA**: Enforces custom policies defined in `policies/`.
6. **Run Trivy**: Ensures container images have no critical vulnerabilities.

## Usage
Invoke this role in your CI pipeline after linting to ensure all infrastructure code and images comply with security and policy standards.
