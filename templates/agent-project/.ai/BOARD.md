# AI Agent Board

## Current objective

TBD

## Active tasks

| ID | Owner | Branch | Status | Summary |
|---|---|---|---|---|

## Blockers

None.

## Integration queue

None.

## Rules

- Each agent owns one branch/worktree.
- Lead agent reviews outputs before merge.
- No agent edits another agent's branch.
- Every delegated task writes its final report to `.ai/outputs/<task-id>-<agent>.md`.
- Every cross-agent transfer writes a handoff file under `.ai/handoffs/`.
