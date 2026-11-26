# BookFlow — initial requirements
Status: proposed MVP baseline; refine with developer before implementation.

## Roles
Platform Admin (platform administration), Business Owner (organization management), Business Admin (staff/services/appointments), Employee (own availability and appointments), Customer (search and book). Tenant-scoped permissions must be enforced server-side.

## Functional epics
- EPIC-01 Identity: registration, login, token lifecycle, role-based access via Keycloak/OIDC.
- EPIC-02 Organization: tenant registration, memberships, employees, tenant isolation.
- EPIC-03 Catalog: services, pricing, duration, employee-service assignments.
- EPIC-04 Scheduling: working hours, breaks, days off, available slots, time zones.
- EPIC-05 Booking: create, reschedule, cancel, prevent overlaps, status transitions.
- EPIC-06 Notifications: confirmation, cancellation, reminders; retry failed deliveries.
- EPIC-07 Production readiness: API documentation, tests, CI, Docker, health checks and logging.

## Business rules
| ID | Rule |
|---|---|
| BR-001 | Tenants cannot access other tenants' private data. |
| BR-002 | An employee cannot have overlapping active appointments, including concurrent requests. |
| BR-003 | Appointments must fit employee availability. |
| BR-004 | Employee must be assigned to the selected service. |
| BR-005 | No bookings in the past. |
| BR-006 | Duration is captured from the service at booking time. |
| BR-007 | Cancellation releases the reserved slot. |
| BR-008 | Only permitted status transitions are allowed. |
| BR-009 | Store appointment instants consistently in UTC; retain relevant IANA time zone for local schedules. |

Proposed lifecycle: PENDING -> CONFIRMED or CANCELLED; CONFIRMED -> COMPLETED, CANCELLED or NO_SHOW. Terminal states cannot transition. Pending expiry and cancellation policies remain open decisions.

## Quality requirements
Secure tenant isolation, transactional booking consistency, concurrency tests, predictable API errors, input validation, idempotent event processing, retry and failure handling, structured logs without secrets, reproducible local startup and automated CI. Define measurable performance targets later rather than inventing SLAs.

## Conceptual entities
Organization, User (identity reference), Membership, Employee, Customer, Service, EmployeeService, WorkingHours, TimeOff, Appointment. Ownership, cardinalities and schema are to be designed in subsequent tasks.

## Later scope
Angular UI, reporting, audit enhancements and Stripe payments. No commitment to Kubernetes, Kafka or Redis unless justified.
