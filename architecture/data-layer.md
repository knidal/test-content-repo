# Data Layer

The data layer manages all persistent storage, caching, and data access patterns across the Acme Platform.

## Database Strategy

Each microservice owns a dedicated PostgreSQL schema. Migrations are managed with Flyway and run automatically on service startup. Cross-service data access is strictly prohibited — services must use APIs or consume events to access data owned by other services.

Connection pooling is handled by PgBouncer, configured in transaction mode. Each service maintains a pool of 20 connections by default, tunable via environment variables.

## Caching

The platform uses a two-tier caching strategy:

- **L1 (in-process):** Caffeine caches with a 5-minute TTL for frequently accessed reference data like feature flags and tenant configurations.
- **L2 (distributed):** Redis cluster for session data, rate limiting counters, and cross-service shared state.

Cache invalidation follows a write-through pattern. When a service updates its primary data store, it also invalidates the corresponding cache entries. For eventual consistency use cases, TTL-based expiration is preferred over active invalidation.

## Event Store

Domain events are persisted in a dedicated append-only event store before being published to the message bus. This guarantees at-least-once delivery and enables event replay for rebuilding projections or debugging production issues.

## See Also

For the overall system design, see the [Architecture Overview](overview). For how we monitor data layer health, see the [Monitoring Guide](../guides/monitoring).
