# Standalone To-Do Application — Claude Code Project

This folder is intentionally separate from the GitHub Copilot project. It contains the application source, tests, project artifacts, and Claude Code configuration only. It does not include `.github/` Copilot files, `.git` history, `node_modules`, or generated `dist` output.

## Main files
- `CLAUDE.md`: project-wide Claude Code instructions
- `.claude/agents/`: SDLC specialist subagents
- `.claude/skills/run-sdlc/SKILL.md`: `/run-sdlc` workflow entry point
- `requirements.md`, `architecture.md`, `design-review.md`, `impl-plan.md`: current project artifacts
- `CLAUDE_CODE_SETUP.md`: setup and first-run instructions

## Start
1. Open this folder in VS Code.
2. Ensure a compatible Node.js version and npm are installed.
3. Run `npm install`.
4. Run `claude` from this folder and use `/run-sdlc`.
5. Review every approval request; never bypass a required human gate.

This extracted folder has no inherited Git history or configured remote. It will not change your existing GitHub Copilot folder.
