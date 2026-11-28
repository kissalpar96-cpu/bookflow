# ADR-005: Synchronous and Asynchronous Communication

**Status:** Proposed

## Context

BookFlow needs some answers during a request, such as whether an employee is
eligible for a booking. Other work, such as sending a confirmation email, can
happen after the booking is recorded.

## Alternatives

### Synchronous API calls

The caller receives an immediate result or error. This makes request-driven
workflows easier to follow, while dependency latency and outages can affect
the original request.

### Asynchronous events

Producers publish events and consumers process them at their own pace. This
lets consumers retry independently and requires handling delayed or duplicate
delivery and monitoring failures.

## Decision

Use synchronous APIs when a workflow needs an immediate answer. For example,
if Booking needs current employee data from Organization to validate a request,
it calls the Organization API with a bounded timeout. If the required check
cannot complete, Booking returns a recoverable error and leaves the booking
unchanged.

Use asynchronous events for side effects that can complete later. When booking
notifications are introduced, Booking will record the booking and its outbox
event in one database transaction. An outbox publisher will then deliver the
event through RabbitMQ for the Notification Service to process.

## Consequences

- The booking response can confirm a committed booking before the confirmation
  email is sent. Booking enforces appointment overlap rules in its own database.
- Consumers must handle repeated event delivery without creating duplicate
  notification work. Use bounded retries and dead-letter handling for persistent
  failures.
- Introduce RabbitMQ and the outbox with the notification workflow. Sprint 0
  can proceed with the gateway, service skeletons, and their local dependencies.
