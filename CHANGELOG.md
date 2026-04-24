# Changelog

All notable Tri_Squad changes are recorded here. Release detail files live in
`.ai/releases/`.

## v0.2.0 - 2026-04-24

Reusable launcher release.

### Added

- Repo-managed `scripts/ai-project-init` command for initializing any git
  project with the TriSquad AI workspace.
- Repo-managed `scripts/trisquad` command for initializing and launching Claude
  Squad from a project root.
- `scripts/install-trisquad` for installing the global template and launcher
  commands into `~/.config/ai-project-template` and `~/.local/bin`.
- Template `.ai/README.md` and `GEMINI.md -> AGENTS.md` symlink for installed
  templates.
- User-facing README with ASCII logo, purpose, installation, daily usage,
  generated files, roles, delegation, release history, and verification notes.

## v0.1.0 - 2026-04-24

Initial usable Tri_Squad template release.

### Added

- Multi-agent operating guide for Codex Lead, Gemini Reviewer / Architect, and
  Qwen Local Assistant.
- Real README with quick start, delegation, communication files, starter
  template, and verification guidance.
- Durable `.ai/CONTEXT.md` and `.ai/DECISIONS.md`.
- Structured handoff template and initial Gemini/Qwen handoff files.
- Task prompts for template bootstrap and follow-up reviews.
- Hardened `scripts/delegate-agent` with validation, failure status reporting,
  command checks, and interactive-auth detection.
- Clean starter template under `templates/agent-project/`.
- Root `.gitignore` for dependencies, build outputs, local env files, and AI
  runtime artifacts.

### Verification

- `bash -n scripts/delegate-agent`
- `bash -n templates/agent-project/scripts/delegate-agent`
- `git diff --check`

### Known Review Status

- Qwen local review ran but produced procedural output, so it is inconclusive.
- Gemini architecture review was blocked by interactive browser authentication.
- User approved merging the first version with these risks documented.
