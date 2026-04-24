# Tri_Squad

Tri_Squad is a Fedora-first multi-agent development template. It coordinates
Codex, Gemini, and Qwen through Git branches plus the `.ai/` task board,
outputs, status files, and handoffs.

The repository currently provides the operating layer for future projects. It
does not yet contain a generated React, NestJS, Expo, or Docusaurus app.

## Quick Start

1. Read `AGENTS.md`, `.ai/CONTEXT.md`, and `.ai/BOARD.md`.
2. Create a task branch with `git checkout -b task/<task-id>-<agent-name>`.
3. Put task prompts in `.ai/tasks/`.
4. Delegate non-interactive work with `scripts/delegate-agent`.
5. Require each agent to write its final report to `.ai/outputs/`.
6. Write cross-agent context transfers under `.ai/handoffs/`.
7. Update `.ai/BOARD.md` before and after delegation.
8. Document verification before merge.

## Agent Roles

- **Codex Lead:** implementation, integration, tests, refactors, code review before merge, and task decomposition.
- **Gemini Reviewer / Architect:** architecture review, long-context analysis, documentation, alternative designs, and risk analysis.
- **Qwen Local Assistant:** cheap local review, documentation drafts, naming suggestions, simple refactor proposals, and offline brainstorming.

Do not use local Qwen as the only source for sensitive security review unless
the model and findings are manually verified.

## Communication Files

- `.ai/BOARD.md`: current objective, task ownership, blockers, and integration queue.
- `.ai/CONTEXT.md`: durable project context that every agent should read first.
- `.ai/DECISIONS.md`: architecture and workflow decisions.
- `.ai/tasks/`: prompts for delegated work.
- `.ai/outputs/`: generated agent reports.
- `.ai/status/`: current agent status files.
- `.ai/handoffs/`: structured cross-agent handoffs.
- `.ai/logs/`: raw delegate command logs.

## Delegation

Use:

```bash
scripts/delegate-agent <codex|gemini|qwen> <task-id> <prompt-file>
```

Example:

```bash
scripts/delegate-agent qwen T005 .ai/tasks/T005-qwen-review.md
```

After every delegation, update `.ai/BOARD.md` with the owner, branch, status,
and expected output file.

## Launcher Commands

Install the reusable template and commands:

```bash
scripts/install-trisquad
```

Then run from any git project:

```bash
trisquad
```

`trisquad` moves to the project root, initializes the AI workspace if needed,
and opens Claude Squad. `ai-project-init` can also be run directly when you
only want to add `AGENTS.md`, `GEMINI.md`, and `.ai/` context files.

## Starter Template

`templates/agent-project/` contains a clean starting layout for new projects
that want the same agent workflow without inheriting this repository's runtime
logs or prior task history.

## Releases

Release history is tracked in `CHANGELOG.md`, with detailed release records in
`.ai/releases/`.

## Verification

For app projects, the default Definition of Done is:

```bash
npm run lint
npm test
```

This orchestration template has no Node project yet, so verification starts with
shell syntax checks and documentation review until app tooling is added.
