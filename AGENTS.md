# Agent Operating Guide: Fedora AI Squad

## Project Goal

To develop a coordinated multi-agent workflow on Fedora Linux that automates software development, documentation, and testing, synchronized via GitHub.

## Architecture

- **OS:** Fedora Linux (Workstation)
- **Primary Stack:** (React, NestJS, Expo, Typescript, Docusaurus)
- **Storage:** Local Git repository synced to GitHub.
- **Agent Roles:**
  - **Gemini (Lead):** Orchestrates tasks and approves GitHub PRs.
  - **Codex (Dev):** Executes feature branches and code logic.
  - **Qwen (QA):** Reviews code, runs linting, and handles documentation.

## Commands (Fedora/DNF Context)

- **Install dependencies:** `sudo dnf install <pkg>` or `npm install`
- **Context Search:** `rg "search_term"` (ripgrep)
- **Find Files:** `fd "file_name"` (fd-find)
- **GitHub Sync:** `gh pr create` / `gh status`
- **Run Dev Server:** (Add your specific command here, e.g., `npm run dev`)

## Working Rules & Synchronization

1. **GitHub Flow:** - Every task MUST start with a branch: `git checkout -b task/<task-id>-<agent-name>`.
   - **Codex** must commit and push changes: `git commit -m "feat: <description>"`.
2. **Inter-Agent Communication:**
   - **Status Updates:** Update `.ai/status/<agent>.md` after every major command.
   - **Hand-offs:** When an agent finishes, it must tag the next agent in the `README.md` or a shared `handoff.log`.
3. **Safety Rails:**
   - Do not edit `.env` or sensitive Fedora config files.
   - Use `direnv` to manage API keys; do not hardcode them.
4. **Tooling:** Prefer `ripgrep` for searching files to save token context.

## Definition of Done (DoD)

- [ ] Code passes `npm run lint` and `npm test`.
- [ ] Documentation updated in `docs/` or `README.md`.
- [ ] Final output written to `.ai/outputs/<task-id>-<agent>.md`.
- [ ] Changes pushed to GitHub and a PR is opened via `gh pr create`.
