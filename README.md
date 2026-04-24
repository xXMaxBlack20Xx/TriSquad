# TriSquad

```text
 _______     _  _____                 _
|__   __|   (_)/ ____|               | |
   | |_ __  _| (___   __ _ _   _  __| |
   | | '__|| |\___ \ / _` | | | |/ _` |
   | | |   | |____) | (_| | |_| | (_| |
   |_|_|   |_|_____/ \__, |\__,_|\__,_|
                         | |
                         |_|
```

**Version:** `v0.2.0`

TriSquad is a reusable multi-agent project launcher for git repositories. You
enter any project, run `trisquad`, and get a shared AI workspace plus Claude
Squad sessions for Codex, Gemini, Qwen, and a normal shell.

## Purpose

TriSquad solves the setup problem for multi-agent development. Instead of
recreating `AGENTS.md`, `GEMINI.md`, task boards, handoffs, and status folders
for every project, TriSquad installs one reusable template and one launcher
command.

The target workflow is:

```text
Enter any git project
        |
Run: trisquad
        |
TriSquad initializes shared AI context if needed
        |
Claude Squad opens from the project root
        |
Launch Codex, Gemini, Qwen, or shell sessions
```

## How It Works

TriSquad has three layers:

- **Global Claude Squad config:** `~/.claude-squad/config.json`
  Defines launch profiles such as `codex-lead`, `gemini-architect`,
  `qwen-local-chat`, and `shell`.
- **Reusable project template:** `~/.config/ai-project-template/`
  Stores the template files copied into each project.
- **Launcher commands:** `~/.local/bin/trisquad` and
  `~/.local/bin/ai-project-init`
  Initialize project context and launch Claude Squad.

## Requirements

Install and verify these commands are available on `PATH`:

```bash
which cs
which codex
which gemini
which ollama
which tmux
which git
```

For Qwen, the default profile expects this Ollama model:

```bash
ollama list
```

Expected model:

```text
qwen2.5-coder:7b
```

## Install TriSquad

From this repository:

```bash
scripts/install-trisquad
```

This installs:

- `~/.config/ai-project-template`
- `~/.local/bin/ai-project-init`
- `~/.local/bin/trisquad`

Make sure `~/.local/bin` is on `PATH`:

```bash
echo "$PATH"
```

If it is missing:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## Use It

For a new project:

```bash
mkdir my-project
cd my-project
git init
trisquad
```

For an existing project:

```bash
cd my-project
trisquad
```

From a nested folder:

```bash
cd my-project/src/some/deep/folder
trisquad
```

`trisquad` automatically moves to the git root before launching Claude Squad.

## What Gets Created

On first run inside a project, TriSquad creates:

```text
AGENTS.md
GEMINI.md -> AGENTS.md
.ai/
  BOARD.md
  CONTEXT.md
  DECISIONS.md
  README.md
  tasks/
  status/
  outputs/
  handoffs/
  logs/
  decisions/
  releases/
scripts/
  delegate-agent
```

Existing files are skipped by default. Use `ai-project-init --force` only when
you intentionally want to refresh managed template files.

## Agent Roles

- **Codex Lead:** implementation, integration, tests, refactors, code review
  before merge, and task decomposition.
- **Gemini Architect:** architecture review, long-context analysis,
  documentation, alternative designs, and risk analysis.
- **Qwen Local Reviewer:** cheap local review, documentation drafts, naming
  suggestions, simple refactor proposals, and offline brainstorming.
- **Shell:** normal terminal work for commands and inspection.

Do not use local Qwen as the only source for sensitive security review unless
the model and findings are manually verified.

## Shared Context Files

- `.ai/BOARD.md`: active work, owners, branches/worktrees, blockers, and
  integration queue.
- `.ai/CONTEXT.md`: project stack, architecture, directories, milestone, and
  notes for agents.
- `.ai/DECISIONS.md`: durable architecture and workflow decisions.
- `.ai/tasks/`: prompts for delegated work.
- `.ai/outputs/`: final agent reports.
- `.ai/status/`: latest agent status files.
- `.ai/handoffs/`: structured agent-to-agent context transfers.
- `.ai/logs/`: raw delegation command logs.

## Delegation

Inside an initialized project:

```bash
scripts/delegate-agent <codex|gemini|qwen> <task-id> <prompt-file>
```

Example:

```bash
scripts/delegate-agent qwen T005 .ai/tasks/T005-qwen-review.md
```

Every delegated task should write its final report to
`.ai/outputs/<task-id>-<agent>.md`.

## Release History

Release history is tracked in `CHANGELOG.md`, with detailed release records in
`.ai/releases/`.

Current version: `v0.2.0`, which adds the `trisquad` launcher workflow.

## Verification

This repository is a shell/template project, so verification focuses on script
syntax and launcher smoke tests:

```bash
bash -n scripts/ai-project-init
bash -n scripts/trisquad
bash -n scripts/install-trisquad
bash -n scripts/delegate-agent
git diff --check
```

For projects initialized by TriSquad, replace the placeholder verification
commands in `AGENTS.md` with project-specific commands such as:

```bash
npm run lint
npm test
npm run build
```
