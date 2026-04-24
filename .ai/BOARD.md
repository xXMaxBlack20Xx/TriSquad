# AI Agent Board

## Current objective

Bootstrap Tri_Squad into a clean reusable multi-agent project template with
explicit handoffs, documented roles, branch discipline, and verification gates.

## Active tasks

| ID | Owner | Branch | Status | Summary |
|---|---|---|---|---|
| T004 | Codex Lead | task/T004-codex-template-bootstrap | Complete | Added project template docs, handoff conventions, branch/bootstrap files, and delegation hardening. |
| T005 | Qwen | TBD | Ready for delegation | Cheap local review and documentation draft pass after Codex bootstrap. |
| T006 | Gemini | TBD | Ready for delegation | Architecture/reviewer pass before merge or PR approval. |

## Blockers

None.

## Integration queue

T004 is ready for review. Do not merge until Qwen and Gemini verification is
documented and reviewer handoffs are updated under `.ai/handoffs/`.

## Rules

- Each agent owns one branch/worktree.
- Lead agent reviews outputs before merge.
- No agent edits another agent's branch.
- Every delegated task writes its final report to `.ai/outputs/<task-id>-<agent>.md`.
- Every cross-agent transfer writes a handoff file under `.ai/handoffs/`.
