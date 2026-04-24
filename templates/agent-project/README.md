# Agent Project Template

This template starts a new project with the Tri_Squad coordination workflow:
task board, durable context, decisions, outputs, status files, and structured
handoffs.

## First Steps

1. Fill `.ai/CONTEXT.md` with the project goal, stack, and constraints.
2. Set the current objective in `.ai/BOARD.md`.
3. Create a task branch: `git checkout -b task/<task-id>-<agent-name>`.
4. Add task prompts to `.ai/tasks/`.
5. Delegate non-interactive work with `scripts/delegate-agent`.
6. Require final reports under `.ai/outputs/`.
7. Require cross-agent transfers under `.ai/handoffs/`.
8. Document verification before merge.

## Add App Tooling

This template intentionally does not generate app dependencies. Add the actual
project stack after the objective is clear, then update `AGENTS.md` and
`.ai/CONTEXT.md` with real commands such as `npm run lint`, `npm test`, and
`npm run dev`.
