# Task T004: Codex Template Bootstrap

## Owner
Codex Lead

## Branch
`task/T004-codex-template-bootstrap`

## Objective
Bootstrap Tri_Squad into a clean reusable multi-agent project template.

## Scope
- Replace placeholder documentation with a real entry point.
- Fill `.ai/CONTEXT.md` and `.ai/DECISIONS.md`.
- Add structured handoff guidance and handoff template files.
- Add a root `.gitignore` that keeps generated runtime artifacts local.
- Harden `scripts/delegate-agent` for non-interactive delegation.
- Add `templates/agent-project/` as a clean starter layout.

## Required Output
Write final implementation notes to `.ai/outputs/T004-codex.md`.

## Verification
- `bash -n scripts/delegate-agent`
- `git status --short --branch`
