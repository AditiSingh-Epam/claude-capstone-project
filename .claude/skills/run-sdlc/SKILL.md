---
name: run-sdlc
description: Start or resume the To-Do Application requirements-to-PR workflow, reuse existing artifacts, delegate specialist stages, and stop at required human approval gates.
argument-hint: "[start or resume; optional focus]"
---

# Run or resume the To-Do Application SDLC

Use this skill in the main Claude Code session to coordinate the full workflow. Do not claim a subagent was used unless Claude Code actually invoked it and returned results.

## Start-up checks
1. Inspect `git status --short --branch`, current branch if any, `git remote -v`, repository structure, `CLAUDE.md`, and `.claude/agents/`. This is a standalone Claude Code project; do not expect `.github/` Copilot configuration to exist.
2. Inspect `requirements.md`, `architecture.md`, `design-review.md`, `impl-plan.md`, README/changelog, and relevant test/release reports. Reuse valid artifacts; identify which stage is actually current.
3. Check whether the configured Atlassian/Confluence MCP tools are available before reading the `TODO` space. If unavailable, state the blocker and ask for a page export or configuration; never invent retrieved content.
4. Maintain a concise stage ledger with status, artifact, evidence, approvals, open decisions, and next action.

## Required stage order
1. Requirements Agent → `requirements.md`.
2. Architecture Agent → `architecture.md`.
3. Design Review Agent → `design-review.md`, then update architecture only after decisions are agreed.
4. Planning Agent → `impl-plan.md`.
5. **Stop for explicit human approval before implementation.** Summarize planned scope, risks, affected areas, unresolved decisions, and checks.
6. Implementation Agent → code and tests, only after approval.
7. QA & Review Agent → execute relevant tests/checks and independently review the actual diff. If findings require fixes, route them to Implementation Agent and rerun affected checks.
8. Release Agent → PR draft, changelog/release evidence, known limitations, and reviewer checklist.
9. **Stop at the final PR gate.** Show the complete PR-readiness summary and ask explicitly whether the user approves creating the PR. Do not push, create a PR, or merge without the required explicit approval.

## Human approvals and open questions
- Never infer approval from silence, prior unrelated approval, or a draft being shown.
- If a mandatory approval is missing, stop at that gate, ask the smallest necessary question, and resume from that checkpoint after the user responds.
- Do not bypass open product decisions. In particular, task editing and completion-state writes remain out of the current release scope until their documented Q9 decisions are resolved and approved.
- Keep the app simple and local. Do not introduce login, multi-user support, cloud deployment, notifications, or other scope without approval.

## Evidence and Git safety
- Verify every claimed artifact and test result. Report commands and results; distinguish passed, failed, not run, and blocked.
- Keep the QA-007 standalone Chrome 155 verification limitation explicit; never call it passed without fresh evidence.
- Before staging/committing, inspect the actual diff and exclude secrets, dependencies, build outputs, logs, and local databases. Do not overwrite remote `main`, discard user changes, force-push, or invent a remote URL.
- If GitHub authentication, identity, a remote, or PR tools are unavailable, report the exact blocker and safe next steps.

## Delegation
Use the project subagents for focused stages when available: `requirements-agent`, `architecture-agent`, `design-review-agent`, `planning-agent`, `implementation-agent`, `qa-review-agent`, and `release-agent`. Provide each with the exact input artifacts, required output, constraints, and acceptance criteria. The main session remains responsible for stage order, approvals, checking the produced artifacts, and final reporting.

## Final report
Include stage-by-stage status; artifacts created/updated; branch/commit/remote/PR status only when verified; tests actually run; findings resolved/open; approvals obtained/pending; known limitations; and the next action.
