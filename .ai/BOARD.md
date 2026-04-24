# AI Agent Board

## Current objective

Maintain Tri_Squad as a clean reusable multi-agent project template with
explicit handoffs, documented roles, branch discipline, release history, and
verification gates.

## Active tasks

| ID | Owner | Branch | Status | Summary |
|---|---|---|---|---|
| T004 | Codex Lead | task/T004-codex-template-bootstrap | Complete | Added project template docs, handoff conventions, branch/bootstrap files, and delegation hardening. |
| T005 | Qwen | task/T004-codex-template-bootstrap | Inconclusive | Delegated through Ollama; output was procedural, not a concrete review. |
| T006 | Gemini | task/T004-codex-template-bootstrap | Blocked | Gemini CLI requested interactive browser authentication during non-interactive delegation. |
| T007 | Codex Lead | task/T004-codex-template-bootstrap | Complete | Added release tracking and merged first Tri_Squad version. |
| T008 | Codex Lead | task/T008-codex-trisquad-launcher | Complete | Added reusable `ai-project-init`, `trisquad`, installer commands, README docs, and v0.2.0 release notes. |

## Blockers

None.

## Integration queue

PR #1 merged: <https://github.com/xXMaxBlack20Xx/TriSquad/pull/1>

Version `v0.1.0` is the first Tri_Squad template release. Version `v0.2.0`
documents and adds the `trisquad` launcher workflow. Current T005 is
inconclusive and T006 is blocked by Gemini authentication.

## Rules

- Each agent owns one branch/worktree.
- Lead agent reviews outputs before merge.
- No agent edits another agent's branch.
- Every delegated task writes its final report to `.ai/outputs/<task-id>-<agent>.md`.
- Every cross-agent transfer writes a handoff file under `.ai/handoffs/`.
