# Role: testing_matrix

## Purpose
Provides a comprehensive testing matrix using Molecule and Testinfra to validate roles across multiple OS platforms, plus integration tests against a disposable Proxmox lab.

## Variables
- `role_name`: The role under test (e.g., `orchestrator`).
- Molecule scenario names (`ubuntu2004`, `ubuntu2204`, `centos8`).

## Tasks
1. **Install Dependencies**: Installs Molecule, Testinfra, and Docker libraries.
2. **Initialize Scenarios**: Sets up Molecule scenarios for targeted OS images.
3. **Run Molecule Tests**: Executes converge, idempotence, and verify steps for each scenario.
4. **Integration Tests**: Runs pytest suites against the dynamic inventory of Proxmox lab.

## Usage
Invoke this role during CI pipelines or locally to ensure roles work on all supported distributions and real infrastructure.
