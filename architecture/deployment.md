# Deployment

All services are deployed to Kubernetes clusters managed by EKS. The deployment pipeline is fully automated through GitHub Actions.

## CI/CD Pipeline

Every push to the main branch triggers the following pipeline:

1. **Build** — compiles the application, runs unit tests, and produces a Docker image tagged with the commit SHA.
2. **Integration tests** — spins up dependent services in a temporary namespace and runs end-to-end test suites.
3. **Deploy to staging** — the new image is rolled out to the staging cluster using a blue-green deployment strategy.
4. **Smoke tests** — automated health checks and critical path tests run against staging.
5. **Deploy to production** — after staging validation passes, the same image is promoted to production with a canary rollout.

## Rollback

If a canary deployment detects elevated error rates or latency, it automatically rolls back to the previous stable version. Manual rollbacks can be triggered via the ops dashboard or by running `acme rollback <service> <version>`.

## Configuration

Runtime configuration is stored in AWS Parameter Store and injected as environment variables at deploy time. Secrets are stored in AWS Secrets Manager and mounted as files in the pod filesystem. No secrets are ever baked into Docker images.
