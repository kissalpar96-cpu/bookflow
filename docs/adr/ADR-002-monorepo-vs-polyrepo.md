# ADR-002: Monorepo vs. Polyrepo

**Status:** Proposed

## Context

BookFlow is a portfolio project maintained by one developer. The Organization
and Booking services need independent builds and deployments, while local
development needs a way to run them together.

## Alternatives

### Monorepo

Keep service code, documentation, and shared local development configuration in
one repository. A change to the Organization API and the corresponding update
to its Booking caller can be reviewed in one pull request. Repository access
applies to all services in the repository.

### Polyrepo

Use one repository per service. This allows each service to manage its own
repository access and CI settings. Local development requires multiple checkouts,
and an API contract change affecting both services requires coordinated pull
requests.

## Decision

Use a monorepo so one developer can start the local environment from a single
checkout and review changes spanning the Organization and Booking services in
one pull request. Revisit the repository layout if the services need separate
access policies or are maintained by different teams.

## Consequences

- The Organization and Booking services can be built, tested, and deployed
  independently. Each service produces its own deployable artifact.
- A shared CI workflow can run separate build and test jobs for each service.
- Coordinated changes can land in one pull request. Service API changes still
  need to account for callers that may be deployed on a different schedule.
