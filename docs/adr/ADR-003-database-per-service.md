# ADR-003: Database per Service

**Status:** Proposed

## Context

The Organization Service owns organizations, memberships, and employee records.
The Booking Service owns schedules and appointments. Both services need clear
data ownership and a way to access data owned by the other service.

## Alternatives

### Shared tables

Both services can query the same tables and use SQL joins to retrieve related
data. A schema change can affect queries in both services and require coordinated
releases.

### Database per service

Each service owns its database and can evolve its schema independently. When a
service needs data owned by another service, it uses that service's API or
consumes its events.

## Decision

Give the Organization and Booking services separate logical PostgreSQL databases
so each service can evolve its schema independently. Each service uses a
database role with access limited to its own database and owns its migrations.
For local development, both databases can run on the same PostgreSQL instance.

## Consequences

- When Booking needs employee data, it calls the Organization API. The API
  call adds a dependency whose failures Booking must handle.
- Each service can apply its migrations independently. Direct cross-service
  SQL queries and joins are prohibited.
- Booking uses its own database to prevent overlapping active appointments,
  including when booking requests arrive concurrently.
