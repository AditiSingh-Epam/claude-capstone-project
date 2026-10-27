# Changelog

All notable changes to this project should be recorded here.

## [Unreleased]
- QA-007 resolved: standalone Chrome 155.0.8059.85 delete-confirmation verification completed and passed on 2026-10-27 (create, filter, view, and delete-with-confirmation all verified; DELETE request completed with 204, no aborted network request). This closes the limitation accepted on 2026-10-22; see `impl-plan.md` for the evidence record.

## [0.1.0] - 2026-10-27
- Implement the approved limited task flows for creating, listing/filtering, viewing, and confirmation-protected deletion. QA reports automated checks passing (56/56 tests, lint, build, 0 audit vulnerabilities); standalone Chrome 155 delete-confirmation verification remains partial and was accepted as a documented limitation for release preparation on 2026-10-22. Editing/completion writes remain blocked by open Q9 decisions.
- Initial Agentic SDLC configuration and project artifacts.
