# Project Context

## Product / Project
DevForge H01/H02 Isolated Test Fixtures (`devforge-h01-test`). This repository is a small test-fixture repository, not the DevForge Runtime implementation and not a production application.

## Current Goal
Maintain isolated fixture artifacts for validating DevForge canonical Task discovery and concurrency-safe state transitions. The current repository contains three minimal Task fixture files: `H02-LIVE-TEST-001`, `H04-CAS-RACE-001`, and `H04-CAS-RACE-002`.

The current registration purpose is to prepare this repository as a separate project boundary for a future, independently authorized Whole-Plan execution-path test. That test has not been created or run.

## Current Model
- `README.md` identifies the repository as DevForge H01/H02 isolated test fixtures.
- `docs/tasks/` contains minimal historical test-fixture Task identifiers, not a complete current Approved Plan or authorization package.
- `main` is the canonical default branch.
- This repository does not contain the DevForge Runtime implementation or a canonical product execution Run ledger.

## Important Constraints
- Existing H02/H04 fixture files do not by themselves authorize development execution and must not be treated as an Approved Plan, active authorization, or product-level execution evidence.
- Any future Whole-Plan execution test requires its own canonical Task, Approved Plan, exact candidate Runtime binding, explicit execution authorization, and independently read-back-verified evidence.
- Keep test changes isolated to this repository. Do not modify DemonTD Manager PR #15, its Task, Plan, Gate, or historical Run.
- Project registration does not create a Task, Plan, Issue, PR, or Run and does not approve Feature Acceptance.

## Confirmed Decisions
- Canonical project ID: `devforge-h01-test`.
- Canonical Git repository identity: `git|github.com|bewaterhere-coder/devforge-h01-test`.
- Default branch: `main`.
- Project execution binding is maintained as DevForge routing metadata; this context file does not select a machine, workspace, provider implementation, or grant execution permission.

## Open Questions
- A separate test Task and Approved Plan for the Whole-Plan direct Bridge route remain uncreated.
- The candidate route in DevForge PR #221 is not yet the current DevForge main route; any test must bind and record the exact candidate revision and must not claim that main already contains it.
