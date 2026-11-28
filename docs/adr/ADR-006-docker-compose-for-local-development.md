# ADR-006: Docker Compose for Local Development

**Status:** Proposed

## Context

BookFlow needs a reproducible local environment for its services and their
dependencies. In Sprint 0, Organization and Booking each need a logical
PostgreSQL database. Keycloak and RabbitMQ will be introduced when their
workflows are implemented.

## Alternatives

### Install dependencies directly on each workstation

Developers install, configure, and start the dependencies themselves. This
avoids a container runtime, while dependency versions and configuration can
drift between workstations.

### Docker Compose

Keep a shared description of local dependencies in the repository. Developers
can start the same set of containers from a checkout. This requires a Docker
runtime with Compose support and consumes local CPU, memory, and disk space.

## Decision

Use Docker Compose for local development. Start with one PostgreSQL instance
that hosts the separate Organization and Booking databases, each with its own
database access as defined in ADR-003. Developers can run the Java services
from their IDE during development.

Keep shared configuration and example environment values in version control.
Supply local credentials through ignored environment files. Add Keycloak and
RabbitMQ as their use cases reach implementation.

## Consequences

- Developers can start and stop local dependencies consistently. Define
  health checks so startup instructions can distinguish a running container
  from a database that is ready to accept connections.
- Database data can persist in a local volume across container restarts.
  Maintainers need to document how to reset that state when necessary.
- Integration tests use PostgreSQL Testcontainers to manage their own database
  lifecycle independently of the local Compose environment. Production
  deployment configuration will be decided separately.
