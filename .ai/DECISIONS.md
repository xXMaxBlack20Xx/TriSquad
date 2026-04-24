# Decisions

## 2026-04-24: Treat Tri_Squad as an orchestration template first

Tri_Squad currently contains coordination files but no application source. The
first stable deliverable is a reusable multi-agent project template rather than
a generated React/NestJS/Expo/Docusaurus app.

## 2026-04-24: Runtime artifacts stay local by default

Generated logs, status files, and agent outputs live under `.ai/`, but the root
`.gitignore` ignores runtime contents by default. Durable templates, task
prompts, handoff files, board state, context, and decisions remain trackable.

## 2026-04-24: Handoffs are structured Markdown files

Agents use `.ai/handoffs/<task-id>-<from>-to-<to>.md` for cross-agent context.
The required sections are task, findings, files touched, suggested next action,
verification, and risks.

## 2026-04-24: Verification must match the repository that exists

`npm run lint` and `npm test` are the app-project target, but this repository
does not currently define a Node package. Until app tooling exists, verification
uses shell syntax checks and Markdown review.
