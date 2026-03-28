# Monitoring Guide

Observability is a first-class concern in the Acme Platform. Every service emits structured logs, metrics, and distributed traces that feed into a centralized observability stack.

## Logging

All services use structured JSON logging with consistent field names: `timestamp`, `level`, `service`, `traceId`, `message`, and optional `context` fields. Logs are shipped to Elasticsearch via Fluentd sidecars and searchable through Kibana.

Log levels follow a strict convention:
- **ERROR** — something broke and needs immediate attention
- **WARN** — degraded behavior that should be investigated
- **INFO** — significant business events (user signup, payment processed)
- **DEBUG** — detailed diagnostic information, disabled in production

## Metrics

Prometheus scrapes metrics from each service's `/metrics` endpoint every 30 seconds. Key dashboards in Grafana track request rate, error rate, p50/p95/p99 latency, and resource utilization per service.

Custom business metrics (signups per hour, API calls per tenant) are also exposed as Prometheus counters and gauges.

## Alerting

Alerts are defined in Prometheus Alertmanager rules and routed to PagerDuty for critical issues and Slack for warnings. The on-call rotation is managed through PagerDuty schedules. Every alert includes a runbook link with troubleshooting steps.

## Distributed Tracing

OpenTelemetry instrumentation propagates trace context across all services. Traces are collected by Jaeger and visualized in the Grafana Tempo backend. Every API request generates a trace ID that appears in logs, metrics, and error reports for end-to-end correlation.

## Health Checks

Every service exposes a `/health` endpoint that returns the service status along with dependency checks (database connectivity, cache availability, external API reachability). The orchestration layer polls these endpoints and automatically removes unhealthy instances from the load balancer rotation. Health check responses include version information for deployment verification.

## Related Topics

For authentication-specific monitoring and login flow metrics, see the [Authentication Guide](authentication). For initial setup instructions, see the [Getting Started](../getting-started) guide.
