# Task T006: Gemini Architecture Review

## Owner
Gemini Reviewer / Architect

## Objective
Review the multi-agent workflow architecture before integration.

## Inputs
- `AGENTS.md`
- `README.md`
- `.ai/CONTEXT.md`
- `.ai/BOARD.md`
- `.ai/DECISIONS.md`
- `scripts/delegate-agent`
- `.ai/handoffs/`
- `templates/agent-project/`

## Required Output
Write findings to `.ai/outputs/T006-gemini.md` and handoff notes to
`.ai/handoffs/T004-gemini-to-codex.md`.

## Review Focus
- Branch/worktree model
- Delegation flow
- Board update rules
- Handoff contract
- Verification gates
- Risks before merge
