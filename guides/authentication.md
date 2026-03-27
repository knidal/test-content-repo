# Authentication

The platform uses OAuth 2.0 with OpenID Connect for all user authentication. Identity is managed by an internal auth service backed by a dedicated user store.

## Login Flow

When a user visits the application, the client redirects them to the auth service's authorize endpoint. After successful credential verification, the auth service issues a short-lived access token (15 minutes) and a refresh token (7 days).

Access tokens are JWTs signed with RS256. They contain the user's ID, email, tenant ID, and a list of granted scopes. The client includes the access token in the Authorization header of every API request.

## Token Refresh

When the access token expires, the client silently exchanges the refresh token for a new token pair. If the refresh token itself has expired, the user is redirected to the login page. Refresh tokens are single-use — each exchange invalidates the old refresh token and issues a new one.

## Multi-Tenant Isolation

Each user belongs to exactly one tenant. The tenant ID in the JWT is validated on every request by the API gateway. A user cannot access resources belonging to another tenant, even if they somehow obtain a valid token — the gateway enforces tenant-scoped routing at the network level.

## API Keys

For service-to-service and programmatic access, the platform supports API keys. Keys are generated per tenant, scoped to specific permissions, and rotated every 90 days. API key authentication bypasses the OAuth flow but enforces the same authorization rules.
