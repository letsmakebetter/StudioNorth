# Studio North — Security Baseline

## Identity and authorization

- Use server-maintained identity and session state.
- Never accept a role or actor identity from a mutation request as proof of authorization.
- Check role and workspace membership at the server boundary.
- An Observer must be rejected by mutation handlers, even if a request bypasses the UI.
- Return only records the current user is authorized to access.

## Input and database safety

- Validate mutation inputs with Zod on the server.
- Use Prisma queries and parameterized database operations.
- Enforce relational integrity with database constraints.
- Use a transaction for task status changes and their activity events.
- Do not expose stack traces, connection strings or secrets to clients.

## Secrets

- Keep database credentials in local environment configuration.
- Commit only placeholder values in .env.example.
- Never commit .env, .env.local or real credentials.
- Use a database account with only the privileges required by the application.

## Errors and logging

- Give users clear, non-sensitive error messages.
- Do not report a save as successful unless it actually succeeded.
- Avoid recording passwords, session tokens or other secrets in logs.

## Dependency audit — 19 October 2026

The initial full npm audit reported five high-severity findings
in the development dependency tree, involving braces@3.0.3 through
the ESLint dependency chain. The production-only audit reported
zero vulnerabilities.

The upstream advisory currently lists no patched braces release.
Do not use npm audit fix --force to downgrade unrelated framework
packages. Re-run the full audit after dependency changes and review
the advisory for an upstream fix.
