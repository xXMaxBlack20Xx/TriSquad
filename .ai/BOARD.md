# AI Agent Board

## Current objective

Bootstrap Tri_Squad into a clean reusable multi-agent project template with
explicit handoffs, documented roles, branch discipline, and verification gates.

## Active tasks

| ID | Owner | Branch | Status | Summary |
|---|---|---|---|---|
| T004 | Codex Lead | task/T004-codex-template-bootstrap | Complete | Added project template docs, handoff conventions, branch/bootstrap files, and delegation hardening. |
| T005 | Qwen | task/T004-codex-template-bootstrap | Inconclusive | Delegated through Ollama; output was procedural, not a concrete review. |
| T006 | Gemini | task/T004-codex-template-bootstrap | Blocked | Gemini CLI requested interactive browser authentication during non-interactive delegation. |

## Blockers

None.

## Integration queue

Draft PR: https://github.com/xXMaxBlack20Xx/TriSquad/pull/1

T004 is ready for review, but do not merge until Qwen and Gemini verification
is meaningful and documented. Current T005 is inconclusive and T006 is blocked
by Gemini authentication.

## Rules

- Each agent owns one branch/worktree.
- Lead agent reviews outputs before merge.
- No agent edits another agent's branch.
- Every delegated task writes its final report to `.ai/outputs/<task-id>-<agent>.md`.
- Every cross-agent transfer writes a handoff file under `.ai/handoffs/`.
