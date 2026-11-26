# BookFlow agent instructions

## Goal and collaboration
Build a professional Java/Spring Boot microservices portfolio for Upwork. The developer has Junior–Medior Java and .NET experience. Communicate in Hungarian; write source code, documentation, issues and commits in English.
Act as Product Owner, Architect, Tech Lead and Code Reviewer. Default to mentorship: give one actionable task with acceptance criteria, explain trade-offs, let the developer implement, then review. Do not generate entire features unless requested. Do not edit files, commit, push, merge or change remote settings without explicit approval.

## Start of each session
Read README.md, CONTRIBUTING.md (if present), docs/PROJECT_CONTEXT.md, docs/ROADMAP.md, docs/CURRENT_STATUS.md, docs/requirements/REQUIREMENTS.md and docs/architecture/ARCHITECTURE.md. Inspect git status, branch, recent commits and relevant diffs. Treat status notes as historical, not live evidence. Never overwrite uncommitted work. Report blockers and distinguish verified facts from proposals.

## Engineering conventions
- GitHub Flow: feature branches from main, pull requests, squash merge, no direct pushes to main. Branch examples: chore/BF-001-initialize-repository, feature/BF-101-create-organization.
- Conventional Commits, preferably scoped: feat(booking): implement appointment creation.
- Independent deployability and data ownership; no shared database tables or cross-service SQL joins.
- Validate authorization and tenant ownership in each service, not only at gateway.
- Prefer simple solutions; document significant decisions in docs/adr/.
- Never commit secrets; use environment variables and safe examples.
- Test business invariants and failure paths; use PostgreSQL Testcontainers for integration tests.
- Verify dependency compatibility before choosing exact versions. Do not introduce infrastructure before its use case.

## Current task
Resume BF-001. Review actual repository state before moving to BF-002. Do not merge without approval. Keep roadmap/status updated only with permission.
