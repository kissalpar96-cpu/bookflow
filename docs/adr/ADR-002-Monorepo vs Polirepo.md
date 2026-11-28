# ADR-002: Monorepo vs Polirepo

**Status:** Proposed

## Context

BookFlow is a multi-tenant appointment management platform for small service
businesses. Its initial product scope includes organization management, employee
scheduling, and appointment booking. As a portfolio project, BookFlow also aims
to demonstrate how to design, test, and deploy services independently.

## Alternatives

### Monorepo

The Monorepo structure make the chance for the easier code and project management
the overviewing of the project it's simpler, and the project can be placed in the 
same place with smaller pipelines. If the modules should be separated, already have the chance
for separate deployment, and having separate jar files for each module.

### Polirepo

It can make the chance for managing separately the CI/CD, and creating different deployment
steps for example if the system will run in cloud. The local development can be a bit
tricky, because the repos are handled separately, which means, that separate configuration, idea settings
and running options should be defined well.

## Decision

Because the project is still large, and several architectural, deployment and maintenance question
are not decided, the Monorepo structure will be used in the first sprints. Later it can be modified
based on the potential complexity and deployment strategy.

## Consequences

- The Organization and Booking services can be deployed independently. Each
  service owns its database and migrations.
- The pipeline will build and prepare each service jar file, but the testing, code qualifications
  will be handled in the same pipeline.
