# Set up the standalone To-Do Application Claude Code project

This is a standalone project containing the To-Do Application source, SDLC artifacts, and Claude Code instructions, specialist subagents, and Skills. It intentionally excludes GitHub Copilot configuration, the original `.git` history, `node_modules`, and build output. It is a separate folder and does not alter your saved GitHub Copilot project.

## What's included
- `CLAUDE.md` — always-on project guidance Claude Code reads from the repository root.
- `.claude/agents/` — seven focused SDLC specialist subagents adapted from the existing GitHub Copilot agents.
- `.claude/skills/run-sdlc/SKILL.md` — the `/run-sdlc` workflow entry point for the main Claude Code session.
- `.claude/skills/*/SKILL.md` — reusable architecture, review, planning, implementation, and release procedures.

This project is intentionally separate from your GitHub Copilot folder. No `.github/` Copilot configuration is included. You can initialize a separate Git repository here if you want independent version history.

## How to install on Windows
1. Extract this ZIP to a new folder, separate from your GitHub Copilot project.
2. Open the extracted `To-Do_Application_Claude_Code_Project` folder in VS Code.
3. Open PowerShell in that project root and run:

   ```powershell
   git status --short
   claude --version
   claude
   ```

   The `claude` command must be available and Claude Code must be authenticated for your environment.
4. In the Claude Code session, run `/run-sdlc`. If it is not listed, exit and reopen Claude Code from the project root, then check that `.claude/skills/run-sdlc/SKILL.md` exists.
5. Ask Claude Code to inspect the included artifacts and current Git status. This standalone folder has no inherited Git history or remote; initialize its own Git repository only if you want it version-controlled separately.

## Confluence / Atlassian access
The existing workflow reads the `TODO` Confluence space through Atlassian MCP tools. That connection does not automatically transfer from GitHub Copilot to Claude Code. If Claude Code has no configured and authenticated Atlassian MCP server, it must stop and report the blocker. Configure an approved Atlassian MCP server for Claude Code or provide the relevant Confluence page exports; do not paste tokens into chat or commit credentials.

## First prompt
After installing the files, start Claude Code in the project root and run `/run-sdlc`. If you want a plain-language prompt instead, use:

> Start the To-Do Application SDLC workflow using `CLAUDE.md` and `/run-sdlc`. Inspect the included artifacts and Git status first. Reuse completed work, respect all mandatory human approval gates, and do not claim unrun checks passed. Keep the current release scope and QA-007 limitation intact. This is a separate project folder; do not assume a Git remote exists. Do not push, create a PR, or merge anything unless the required explicit approval is obtained.

## Important safety notes
- Installing this pack does not itself configure GitHub authentication, Git identity, or Atlassian MCP.
- Do not copy `.git` from an archive over your existing repository.
- Do not commit `.env` files, tokens, local databases, logs, dependencies, or build output.
- Claude Code may ask permission before running commands or editing files; review those requests.
- This pack does not claim that the app was retested or that a PR was created.
