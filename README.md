# grafana-dashboards

This repository stores Grafana dashboard JSON files managed via **GitSync**.

## Overview

Grafana's GitSync feature enables version-controlled dashboard management by syncing dashboard JSON definitions directly from a Git repository. Any changes committed here are automatically reflected in Grafana, enabling peer review, rollback, and audit trails for all dashboard changes.

## Repository Structure

```
grafana-dashboards/
├── README.md
└── dashboards/
    └── demo-dashboard.json   # Example dashboard with Prometheus metrics
```

## How GitSync Works

1. Grafana connects to this repository via GitSync configuration.
2. On each sync interval, Grafana pulls the latest commit from the configured branch.
3. Dashboard JSON files in the `dashboards/` directory are provisioned automatically.
4. Deleting a JSON file from this repo removes the corresponding dashboard from Grafana.

## Adding a New Dashboard

1. Export the dashboard JSON from Grafana (Dashboard settings → JSON Model).
2. Save the file under `dashboards/<your-dashboard-name>.json`.
3. Ensure the JSON contains a unique `uid` field.
4. Open a pull request, get it reviewed, and merge to `main`.

## Dashboard Requirements

- Each file must be valid Grafana dashboard JSON.
- The `uid` field must be unique across all dashboards.
- Use `schemaVersion: 39` or higher.
- Datasource references should use the provisioned datasource UID or the `${DS_PROMETHEUS}` variable.
