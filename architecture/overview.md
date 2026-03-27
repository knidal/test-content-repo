# Architecture Overview

The Acme Platform follows a modular microservices architecture. Each service is independently deployable, communicates over gRPC, and stores its data in a dedicated PostgreSQL schema.

## Core Principles

The architecture is built around three core principles:

1. **Separation of concerns** — each service owns its domain logic and data store. No service reads another service's database directly.
2. **Event-driven communication** — services publish domain events to a shared message bus. Consumers subscribe to events they care about and maintain their own projections.
3. **Infrastructure as code** — all cloud resources are defined in Terraform modules, versioned alongside application code.

## Service Mesh

All inter-service communication flows through an Envoy-based service mesh. The mesh provides automatic retries, circuit breaking, mutual TLS, and distributed tracing without requiring changes to application code.

Traffic policies are defined in YAML configuration files and applied via the control plane. Each service registers itself on startup and receives its routing rules dynamically.
