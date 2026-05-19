# Observability

Shared local OTel trace backend for `credimi-runner` instances.

Current stack:

- OpenTelemetry Collector receives OTLP traces.
- Jaeger stores and displays traces for local development.

Start from this repo root:

```bash
docker compose up -d
```

Main endpoints:

- Jaeger UI: `http://localhost:16686`
- OTLP HTTP ingest: `http://localhost:4318`
- OTLP gRPC ingest: `localhost:4317`
- Collector health: `http://localhost:13133`

Deployment notes:

- Expose `otel-collector` publicly only if external OTLP ingest is required.
- Expose `jaeger` only where trace inspection is needed.
