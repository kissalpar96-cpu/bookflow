# BookFlow roadmap

## Sprint 0 — foundation
Historical estimate: 18 hours total; estimates are rough.
| ID | Task | Hours | Status at last review |
|---|---|---:|---|
| BF-001 | Initialize GitHub repository | 1 | In progress |
| BF-002 | Define architecture and initial ADRs | 2 | Pending |
| BF-003 | Configure Maven multi-module project | 1 | Pending |
| BF-004 | Initialize Organization Service | 1 | Pending |
| BF-005 | Initialize Booking Service | 1 | Pending |
| BF-006 | Configure PostgreSQL databases | 2 | Pending |
| BF-007 | Configure Flyway and application profiles | 2 | Pending |
| BF-008 | Configure API Gateway | 2 | Pending |
| BF-009 | Configure health checks and OpenAPI | 1 | Pending |
| BF-010 | Configure Testcontainers | 2 | Pending |
| BF-011 | Configure GitHub Actions | 2 | Pending |
| BF-012 | Finalize initial documentation | 1 | Pending |

Sprint 0 done when a fresh clone can build, start the initial services and databases, access health/API documentation, run tests and pass CI. No business logic required yet.

## Subsequent sprints (provisional)
1. Identity and Organization: Keycloak, JWT, memberships, tenant isolation.
2. Services and Scheduling: catalog, employee assignments, availability and time zones.
3. Appointment Management: lifecycle, concurrency, transactions, idempotency.
4. Notifications and Testing: RabbitMQ, outbox, consumers, failure paths, observability.
5. Deployment and Portfolio: documentation, demo, case study, operational readiness.
6+. Angular frontend and optional reporting/payments.

Earlier estimates were approximately one week per implementation sprint; revisit for microservice complexity and actual availability. Create issues with acceptance criteria before each task. Do not advance automatically while a prior task is awaiting review.
