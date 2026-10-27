# To-Do Application — Claude Code Instructions

## Project overview
This repository contains a local, single-user To-Do application and its Agentic SDLC artifacts. The application currently uses React + Vite, Node.js + Express, and SQLite via Node's built-in `node:sqlite` module. Inspect the repository before assuming the stack or changing dependencies.

## Source of truth and artifacts
- Treat the current repository artifacts as the available source of truth. Read the relevant pages before proposing changes. The Confluence `TODO` space may be consulted only if an Atlassian MCP server is separately configured and authenticated in this Claude Code environment.
- Key artifacts: `requirements.md`, `architecture.md`, `design-review.md`, `impl-plan.md`, `README.md`, `CHANGELOG.md`, and any test/release reports.
- Preserve existing decisions and traceability. Mark missing information `OPEN`; never invent user approval, requirements, test results, or Confluence content.
- This is a standalone Claude Code project. Do not assume GitHub Copilot configuration exists; use `CLAUDE.md` and `.claude/` as the Claude Code instructions and workflow configuration.

## Application constraints
- Keep the app simple, local, and single-user unless requirements are explicitly changed.
- Do not add login, multi-user collaboration, cloud deployment, reminders, attachments, or unrelated features without approval.
- Current documented release scope includes creating, listing/filtering, viewing, and confirmation-protected deletion of tasks, SQLite persistence, input validation, and local-origin protections.
- Task editing and completion-state write operations remain deferred until their documented open decisions are resolved. Do not implement them as part of the current release unless requirements and plan are updated and approved.
- Keep the QA-007 limitation honest: standalone Chrome 155 delete-confirmation verification is incomplete. Never report it as passed without fresh evidence.
- Treat task descriptions as ordinary personal information; do not log full task content or commit local database files or secrets.

## Commands
Use the existing package scripts after inspecting `package.json`:
- `npm test`
- `npm run lint`
- `npm run build`
- `npm audit`

Run relevant checks after changes and report the actual commands and outcomes. Do not say checks passed if they were not executed.

## SDLC and approval gates
Use `/run-sdlc` to start or resume the workflow. Delegate focused stages to the project subagents in `.claude/agents/` when Claude Code supports and invokes them. Follow the stage sequence:
1. Requirements
2. Architecture
3. Independent design review
4. Implementation planning
5. Human approval before implementation
6. Implementation
7. Independent QA/code review and remediation loop
8. Release/PR preparation
9. Explicit human approval before any push or PR creation

Do not bypass a required approval gate. If an approval is outstanding, ask the user for that specific decision and resume after their response. Reuse valid completed artifacts; do not restart everything unnecessarily.

## Git safety
- Inspect `git status`, current branch, remotes, and the actual diff before staging or committing.
- Never discard user changes, use destructive Git commands, force-push, merge, or publish a PR without explicit authorization.
- Before staging, check `.gitignore` and ensure secrets, `.env` files, dependencies, build outputs, logs, and local SQLite databases/sidecars are excluded as appropriate.
- Do not invent a remote URL. Verify it from `git remote -v`.
- Approval to draft a PR is not permission to merge it.

## Integrations
The repository's existing agent instructions refer to Atlassian/Confluence MCP tools. Claude Code can read those sources only if a suitable Atlassian MCP server is configured and authenticated in the user's Claude Code environment. If unavailable, report the blocker and ask for an export or connection setup; do not pretend to have read the pages.
