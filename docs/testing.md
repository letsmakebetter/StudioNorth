# Studio North — Verification Plan

## Existing baseline

The initial Next.js project passed:

- npm run lint
- npm run build

## Unit tests

- Overdue calculation: past date and not Done is overdue.
- Due today is not overdue.
- Done tasks are not overdue.
- Invalid status transitions are rejected where transitions are restricted.

## Integration tests

- Workspace queries do not return records from another workspace.
- A task cannot reference a milestone belonging to another project.
- Status and activity records are written atomically.
- Comments persist with author and timestamp.

## Security tests

- Observer mutation requests are rejected server-side.
- A user without workspace access cannot read workspace data.
- Invalid request bodies are rejected.
- Failed writes do not produce misleading success responses.

## End-to-end tests

- Create a workspace, project, milestone and task.
- Move a task through Ready, Doing and Done.
- Refresh and verify persisted state.
- Add a comment and verify activity history.
- Verify the overdue filter and workspace separation.

The test frameworks and automated test scripts will be added
before these test cases are considered implemented.
