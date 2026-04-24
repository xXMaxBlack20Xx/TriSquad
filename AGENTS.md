# Agent Operating Guide: Fedora AI Squad

## Project Goal

Develop a coordinated multi-agent workflow on Fedora Linux that automates
software development, documentation, and testing, synchronized through GitHub.
This repository is the clean starter template for that workflow.

## Architecture

- **OS:** Fedora Linux (Workstation)
- **Primary Stack:** React, NestJS, Expo, TypeScript, Docusaurus
- **Storage:** Local Git repository synced to GitHub
- **Agent Roles:**
  - **Codex Lead:** Task decomposition, implementation, branch integration, tests, refactors, final review before merge.
  - **Gemini Reviewer / Architect:** Architecture review, long-context repo analysis, documentation, alternative designs, risk analysis, unfamiliar-code explanations.
  - **Qwen Local Assistant:** Cheap local review, documentation drafts, naming suggestions, simple refactor proposals, offline brainstorming.

Do not rely on local Qwen alone for sensitive security review unless the local
model is strong enough and the findings are manually verified.

## Current Workflow

1. The lead reads `AGENTS.md`, `.ai/CONTEXT.md`, and `.ai/BOARD.md`.
2. The lead breaks the current objective into small tasks.
3. Implementation work goes to Codex-owned task branches.
4. Architecture, research, and risk review go to Gemini.
5. Cheap local review, refactor suggestions, and documentation drafts go to Qwen.
6. Non-interactive delegated work uses `scripts/delegate-agent`.
7. Every delegated output is written to `.ai/outputs/<task-id>-<agent>.md`.
8. `.ai/BOARD.md` is updated after each delegation and before integration.
9. No merge happens until tests or verification steps are documented.

## Commands (Fedora/DNF Context)

- **Install dependencies:** `sudo dnf install <pkg>` or `npm install`
- **Context Search:** `rg "search_term"` (ripgrep)
- **Find Files:** `fd "file_name"` (fd-find)
- **GitHub Sync:** `gh pr create` / `gh status`
- **Run Dev Server:** (Add your specific command here, e.g., `npm run dev`)

## Branching

Every task starts from a clean task branch:

```bash
git checkout -b task/<task-id>-<agent-name>
```

Examples:

- `task/T004-codex-template-bootstrap`
- `task/T005-qwen-doc-review`
- `task/T006-gemini-architecture-review`

## Working Rules & Synchronization

1. **GitHub Flow:**
   - Every task must start with a branch: `git checkout -b task/<task-id>-<agent-name>`.
   - Codex commits and pushes implementation changes: `git commit -m "feat: <description>"`.
2. **Inter-Agent Communication:**
   - **Status Updates:** Update `.ai/status/<agent>.md` after every major command.
   - **Outputs:** Final reports go in `.ai/outputs/<task-id>-<agent>.md`.
   - **Handoffs:** Cross-agent transfers go in `.ai/handoffs/`.
3. **Safety Rails:**
   - Do not edit `.env` or sensitive Fedora config files.
   - Use `direnv` to manage API keys; do not hardcode them.
4. **Tooling:** Prefer `ripgrep` for searching files to save token context.

## 3. Handoffs

Files:

- `.ai/handoffs/T004-gemini-to-codex.md`
- `.ai/handoffs/T005-qwen-to-codex.md`

Template:

```markdown
# Handoff: <from> to <to>

## Task
What was reviewed or implemented?

## Findings
Important findings.

## Files touched
- path/to/file.ts

## Suggested next action
What should the next agent do?

## Verification
Commands run and results.

## Risks
Anything uncertain or unsafe.
```

This avoids the biggest multi-agent failure mode: every agent has its own
context window and starts inventing what the others are doing.

## Definition of Done (DoD)

- [ ] Code passes `npm run lint` and `npm test`.
- [ ] Documentation updated in `docs/` or `README.md`.
- [ ] Final output written to `.ai/outputs/<task-id>-<agent>.md`.
- [ ] Changes pushed to GitHub and a PR is opened via `gh pr create`.

## Safety and permissions

- Never run destructive commands such as `rm -rf`, database resets, production migrations, credential rotation, or force pushes without explicit human approval.
- Never print secrets, tokens, `.env` values, private keys, or credentials.
- Before editing, inspect relevant files.
- Before merging, show diff and verification commands.
- For database work, create migrations but do not apply to production.
- For Docker work, do not delete volumes unless explicitly requested.
