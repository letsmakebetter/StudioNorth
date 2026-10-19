# Studio North — Data Model

## Main entities

- User: a named user identity.
- Workspace: a boundary for project data.
- WorkspaceMembership: associates a user with a workspace and role.
- Project: belongs to exactly one workspace.
- Milestone: belongs to exactly one project.
- Task: belongs to exactly one project and optionally one milestone.
- TaskComment: a persistent comment on a task.
- TaskActivity: an append-only record of task status changes.

## Relationships and integrity

- Every task references one project.
- A task milestone, when present, must belong to the same project.
- Membership must be unique for each workspace/user pair.
- Status and priority values must be restricted to documented values.
- Foreign keys and appropriate database constraints protect relationships.
- Workspace separation must be enforced in server-side queries.

## Task status history

A status change records the task, previous status, new status,
actor and timestamp. The task update and activity insertion must
succeed or fail together in one database transaction.

## Derived values

A task is overdue when its due date is earlier than the current
application date and its status is not Done. Overdue is not stored
as a manually edited Boolean field.

Open-task workload, if implemented, is calculated from task records.
