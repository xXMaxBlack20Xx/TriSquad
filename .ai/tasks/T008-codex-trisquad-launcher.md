# Task T008: Tri_Squad Launcher Commands

## Owner
Codex Lead

## Branch
`task/T008-codex-trisquad-launcher`

## Objective
Create reusable `ai-project-init` and `trisquad` commands so any git project can
be initialized with the Tri_Squad AI workspace and launched through Claude Squad.

## Scope
- Add repo-managed launcher scripts.
- Add installer for global template and command installation.
- Improve the reusable project template where needed.
- Install commands locally for this machine.
- Verify syntax and smoke-test initialization without launching the interactive TUI.

## Required Output
Write final notes to `.ai/outputs/T008-codex.md`.

## Verification
- `bash -n scripts/ai-project-init`
- `bash -n scripts/trisquad`
- `bash -n scripts/install-trisquad`
- Smoke-test `ai-project-init` in a temporary git repository.
