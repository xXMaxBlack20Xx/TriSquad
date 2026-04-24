# Agent Operating Guide

## Project Objective

Replace this section with the project goal.

## Agent Roles

- **Codex Lead:** implementation, integration, tests, refactors, code review before merge, and task decomposition.
- **Gemini Architect:** architecture review, long-context analysis, documentation, alternative designs, and risk analysis.
- **Qwen Local Reviewer:** cheap local review, documentation drafts, naming suggestions, simple refactor proposals, and offline brainstorming.
- **Shell:** normal terminal work for commands and inspection.

Do not rely on local Qwen alone for sensitive security review unless the local
model is strong enough and the findings are manually verified.

## Workflow

1. Read `AGENTS.md`, `.ai/CONTEXT.md`, and `.ai/BOARD.md`.
2. Create a task branch: `git checkout -b task/<task-id>-<agent-name>`.
3. Put task prompts in `.ai/tasks/`.
4. Delegate non-interactive work with `scripts/delegate-agent`.
5. Write final reports to `.ai/outputs/<task-id>-<agent>.md`.
6. Write handoffs to `.ai/handoffs/<task-id>-<from>-to-<to>.md`.
7. Update `.ai/BOARD.md` after each delegation.
8. Document verification before merge.

## Handoff Template

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

## Definition of Done

- [ ] Code passes the project's lint command.
- [ ] Code passes the project's test command.
- [ ] Documentation is updated.
- [ ] Final output is written to `.ai/outputs/<task-id>-<agent>.md`.
- [ ] Verification steps are documented before merge.

## Verification Commands

Replace these placeholders with project-specific commands:

```bash
npm run lint
npm test
npm run build
```
