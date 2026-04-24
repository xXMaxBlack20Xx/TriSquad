# Tri_Squad Context

Tri_Squad is the starter repository for a Fedora-based multi-agent software
workflow. Its primary product is the coordination system itself: task board,
agent instructions, delegation script, outputs, status files, and handoffs.

## Current Objective

Bootstrap a clean reusable template for new projects. The template must make it
obvious how Codex, Gemini, and Qwen coordinate, where task outputs live, how
handoffs work, and what verification is required before merge.

## Repository Shape

- `AGENTS.md`: operating guide for every agent.
- `GEMINI.md`: symlink to `AGENTS.md`.
- `README.md`: human entry point.
- `scripts/delegate-agent`: non-interactive delegation wrapper.
- `.ai/BOARD.md`: active work board.
- `.ai/CONTEXT.md`: durable context for future agents.
- `.ai/DECISIONS.md`: durable decisions.
- `.ai/tasks/`: task prompts.
- `.ai/outputs/`: agent final reports.
- `.ai/status/`: latest agent status.
- `.ai/handoffs/`: structured cross-agent handoffs.
- `templates/agent-project/`: clean starter template for new repositories.

## Communication Contract

Every agent reads `AGENTS.md`, `.ai/CONTEXT.md`, and `.ai/BOARD.md` before
acting. The lead updates `.ai/BOARD.md` after delegating work. Agents write
final reports to `.ai/outputs/` and write cross-agent handoffs to
`.ai/handoffs/` when another agent needs context.

## Current Branch

Active implementation branch: `task/T004-codex-template-bootstrap`.

## Verification Baseline

This repository is not yet a Node app, so `npm run lint` and `npm test` are not
available. For the current template work, verify shell scripts with
`bash -n scripts/delegate-agent` and review the generated Markdown files.
