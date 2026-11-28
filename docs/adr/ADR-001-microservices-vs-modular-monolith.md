# ADR-001: Microservices vs. Modular Monolith

**Status:** Proposed

## Context

BookFlow is a multi-tenant appointment management platform for small service
businesses. Its initial product scope includes organization management, employee
scheduling, and appointment booking. As a portfolio project, BookFlow also aims
to demonstrate how to design, test, and deploy services independently.

## Alternatives

### Modular monolith

Organize the application into modules within a single deployable application.
This would simplify local development, integration testing, and deployment.
Modules could still define clear boundaries and own their data, with releases
coordinated as one application.

### Microservices

Deploy services independently and give each service ownership of its data.
Services communicate through explicit APIs or events. This requires more work to
test service contracts, handle network failures, and diagnose requests that cross
service boundaries.

## Decision

Use microservices to demonstrate independent deployment, service-owned data,
and testing across service boundaries.

The Organization Service owns organizations, memberships, and employee records.
The Booking Service owns employee schedules and appointments. Keeping schedules
and appointments in the same service allows it to enforce the rule against
overlapping active appointments within its own database transaction.

Sprint 0 starts with an API Gateway and skeletons for the Organization and
Booking services. Introduce RabbitMQ when a workflow requires asynchronous
messaging.

## Consequences

- The Organization and Booking services can be deployed independently. Each
  service owns its database and migrations.
- Each service needs integration tests. Cross-service workflows also need
  contract and failure-path tests for situations such as dependency timeouts.
- Local startup and troubleshooting involve multiple processes. Sprint 0 limits
  this cost by keeping the application scope small and using Docker Compose
  for local dependencies.
