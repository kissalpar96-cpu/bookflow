# ADR-004: Use Keycloak for Identity

**Status:** Proposed

## Context

BookFlow needs user sign-in and access tokens for its APIs. It also needs to
enforce tenant-specific permissions, such as whether a business administrator
may manage appointments for a given organization.

## Alternatives

### Application-managed identity

BookFlow could manage credentials, account recovery, and token issuance itself.
This gives it full control over sign-in and account flows, while making the
project responsible for implementing and maintaining those security features.

### External identity provider

An OpenID Connect provider can handle sign-in and token issuance. A hosted
provider reduces operational work and introduces an external dependency.
Self-hosted Keycloak can run locally, with setup and maintenance owned by
BookFlow.

## Decision

Use Keycloak as the OpenID Connect provider starting in Sprint 1. Running it
locally lets BookFlow demonstrate an OIDC integration from a local checkout.
BookFlow takes responsibility for configuring and maintaining the provider.
Keycloak handles authentication and issues OAuth 2.0 access tokens. The
Organization Service owns tenant memberships and business roles.

Each business service acts as an OAuth 2.0 resource server. It validates the
access token signature, issuer, audience, and expiry, then enforces tenant
membership and permissions for the requested resource. A tenant ID supplied by
the caller does not establish permission to access that tenant.

## Consequences

- BookFlow can use standard identity protocols and keep credential management
  out of its business services.
- BookFlow must configure and maintain Keycloak, including realm and client
  settings. Keep credentials and client secrets outside version control.
- Authorization tests need to cover invalid tokens and cross-tenant access,
  including requests that reach a service directly.
