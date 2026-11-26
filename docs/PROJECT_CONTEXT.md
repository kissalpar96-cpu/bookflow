# BookFlow — project context

## Purpose
A portfolio SaaS backend for small service businesses (salons, repair shops, consultants) that currently manage appointments manually. Demonstrate independent design, implementation, testing and deployment, not just CRUD. Angular is a later phase. This is a simulated client project, not a real customer engagement.

Repository: https://github.com/kissalpar96-cpu/bookflow

## Planned stack
Java 21 LTS, Spring Boot 4.x, Maven, Spring Cloud Gateway, Spring Security OAuth2 Resource Server, Keycloak (OIDC), PostgreSQL, JPA, Flyway, RabbitMQ, Resilience4j where needed, Springdoc OpenAPI, JUnit/Mockito/Testcontainers, Docker Compose, GitHub Actions, Micrometer/OpenTelemetry, Prometheus/Grafana, later Angular/TypeScript. Exact compatible versions remain to be verified.

## Repository layout
```text
bookflow/
  services/
    api-gateway/
    organization-service/
    booking-service/
    notification-service/
  infrastructure/
    keycloak/
    postgres/
    rabbitmq/
    monitoring/
      prometheus/
      grafana/
  frontend/
  docs/
    architecture/
    requirements/
    adr/
  .github/workflows/
  AGENTS.md
  CONTRIBUTING.md
  README.md
  LICENSE
  .gitignore
  pom.xml              # BF-003, planned
  docker-compose.yml   # planned
  .env.example         # planned
```

## Portfolio deliverables
Public repository, English README, architecture and database diagrams, ADRs, OpenAPI, automated tests, reproducible Docker startup, CI, public demo if feasible, short demo video and Upwork case study. Do not claim planned features are implemented.

Future independent portfolio ideas: SyncBridge (integration/webhooks/retries/idempotency) and StockPilot (inventory/orders/locking/reporting). Focus on BookFlow first.
