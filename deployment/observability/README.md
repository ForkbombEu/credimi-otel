# Observability

Shared OTel backend for all `credimi-runner` instances.

Current split:

- Jaeger is the trace UI and trace storage for local development.
- OpenSearch stores OTLP logs for search and dashboards.
- OpenSearch Dashboards is now a logs UI only in this stack.

The services are wired into the main `credimi-2` Docker Compose flow through `docker-compose.override.yml`.

Start from the `credimi-2` repo root:

```bash
docker compose up -d --build
```

Main endpoints:

- OpenSearch Dashboards: `http://localhost:5601`
- Credimi OTel logs dashboard: `http://localhost:5601/app/dashboards#/view/credimi-otel-overview`
- Jaeger UI: `http://localhost:16686`
- OpenSearch API: `http://localhost:9200`
- OTLP HTTP ingest: `http://localhost:4318`
- OTLP gRPC ingest: `http://localhost:4317`
- Collector health: `http://localhost:13133`

Deployment notes:

- Expose `otel-collector` publicly only if external OTLP ingest is required.
- Expose `jaeger` publicly for trace inspection.
- Expose `opensearch-dashboards` publicly for log inspection.
- Keep `opensearch`, `data-prepper`, `dashboards-bootstrap`, and `otel-prometheus` internal only.
