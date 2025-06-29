# Role: cost_analytics

## Purpose
Implements usage-based billing by exporting metrics from the billing service, scraping them via Prometheus, computing cost per team, and pushing to a Pushgateway for visualization and billing.

## Variables
- None; uses default paths and hostnames. Adjust `billing_exporter` repo and script as needed.

## Tasks
1. **Deploy Exporter**: Runs a Docker Compose stack for the billing metrics exporter.
2. **Scrape Configuration**: Inserts a Prometheus scrape job for the exporter.
3. **Prometheus Reload**: Reloads the Prometheus container to pick up changes.
4. **Compute Usage**: Runs a Python script to calculate usage and cost per team.
5. **Push Metrics**: Sends the computed metrics to a Prometheus Pushgateway.

## Usage
Invoke this role after billing services are up to start collecting, computing, and exporting usage data for billing dashboards or chargeback processes.
