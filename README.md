# g-oss-observability · Platform telemetry (Prometheus + Grafana + Loki + Tempo + OTel)

**Audience:** O&G CIOs/CTOs and SRE/ops leads  
**Goal:** Replace/offset Splunk/Datadog licensing with OSS for metrics, logs, and traces across the data platform.

---

## Executive summary
- **What it is:** **Prometheus** scrapes metrics; **Grafana** visualizes them. **Loki** ingests logs (with **Promtail**). **Tempo** stores traces. **OTel Collector** standardizes ingestion.  
- **What it replaces:** Splunk/Datadog for platform‑level telemetry (keep vendor tools if they’re enterprise‑mandated; use OSS for new workloads and cost relief).

## Where it fits
```
[Airflow/Connect/Trino/Kafka/...]
      | metrics/logs/traces via OTel
      v
 Prometheus + Loki + Tempo ----> Grafana dashboards/alerts
```

## What’s included
- Base configs for Prometheus/Loki/Tempo/Promtail and Grafana datasources.  
- Ready to wire alerts for **pipeline SLOs** and **CDC lag**.

## Pilot SLOs
- **SLO dashboard availability:** ≥ 99.9% business hours.  
- **Alert latency:** < 60s for critical breaches.

## Security & compliance
- Restrict access; enable SSO via reverse proxy (Keycloak).  
- Apply retention policies for logs/traces (e.g., 14–30 days).

## Cost model
- Storage‑heavy for logs/traces; control with retention/filters.  
- Use OpenSearch (see `g-oss-search`) for long‑term log search if needed.

## KPIs for leadership
- Incidents caught by SLO alerts, MTTR improvements, log storage $/GB vs. prior.

## Quick start
```bash
docker compose up -d
# Grafana: http://localhost:3000  (admin/admin)
```
