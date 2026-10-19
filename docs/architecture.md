# Studio North — Architecture

## Project goal

A workspace-based project and task management application.
Core functionality takes priority over optional features.

## Technology stack

- Next.js App Router and React
- TypeScript
- PostgreSQL
- Prisma ORM (version 7 configuration)
- Zod for server-side input validation
- Vitest for unit and integration tests
- Playwright for end-to-end tests

Testing and database dependencies will be installed in dedicated steps.

## Application layers

1. App Router: routes, layouts, pages and HTTP handlers.
2. Features: feature-specific UI, input schemas and presentation logic.
3. Application services: business rules and use cases.
4. Authorization: identity, role and workspace access checks.
5. Repositories: scoped database queries.
6. PostgreSQL: persistent records and relational integrity.

## Architecture rules

- UI components must not access the database directly.
- Client-side code must not import server-only modules.
- Validate untrusted input on the server.
- Perform authorization for every protected read and mutation.
- Scope workspace queries to the authorized workspace.
- Save a task status change and its activity event atomically.
- Calculate overdue state from due date and current status.
- Never treat browser-supplied role or actor identifiers as trusted identity.

## Delivery order

1. Foundation and configuration
2. Database schema, migrations and seed data
3. Authentication and authorization
4. Workspace, project and milestone management
5. Tasks and status board
6. Comments, activity and filtering
7. Automated verification and documentation
