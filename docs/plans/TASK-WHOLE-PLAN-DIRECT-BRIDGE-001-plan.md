# Whole-Plan Direct Linux Bridge Product Verification — Plan Revision 1

## Canonical Binding

- Task ID: `TASK-WHOLE-PLAN-DIRECT-BRIDGE-001`
- Task artifact: `docs/tasks/TASK-WHOLE-PLAN-DIRECT-BRIDGE-001.md`
- Task Git blob: `369e8693440b01dcaf984e657c813520335deaa6`
- Task SHA-256: `b9e771c2489c13ea9a29ef81011f361af3b290c29f60c735ac9e11e191ee069a`
- Requirement revision: `1`
- Project repository: `bewaterhere-coder/devforge-h01-test`
- Execution shape: `whole_plan`
- Plan revision: `1`
- Plan status: `Draft — Plan Review Pending`
- Plan approval: `false`
- Runtime under test: `bewaterhere-coder/DevForge` PR `#221`
- Candidate Runtime HEAD: `975362bb0573d313654b7a6ecbc004d4e402f8b3`
- Accepted Evolution: `EVO-CHATGPT-WHOLE-PLAN-LINUX-BRIDGE-EXECUTION-BINDING-V1-001`, Revision 2
- Accepted Definition SHA-256: `946c9470bc5214e55df5650421042964e67af15ede2b38de7f27f9e9a2c41577`
- Canonical evidence repository/ref: `bewaterhere-coder/devforge-h01-test` / `devforge/execution-evidence`

## Objective

Verify one isolated product Task can be executed as a complete Whole-Plan using ChatGPT's direct calls to the existing Linux Coco Lite Bridge tools, while preserving formal authorization, actual result propagation, failure recovery and canonical execution evidence boundaries.

This Plan tests the PR #221 candidate Runtime. It does not claim that PR #221 is already in DevForge main.

## Preconditions

1. The canonical Task is readable from the exact path and its `execution_shape: whole_plan` is verified.
2. The current Task content digest equals the Task digest above, and the referenced Plan path resolves to this exact Plan revision.
3. The Plan receives an explicit successful formal Plan Review before implementation begins.
4. A separate valid execution authorization is present for this exact Task, Plan revision/digest, repository and allowed file paths.
5. PR #221 is re-read and its head still equals `975362bb0573d313654b7a6ecbc004d4e402f8b3`; any drift stops execution until bindings are reviewed again.
6. Linux Coco Lite Bridge tools and required repository permissions are available; availability does not itself grant authorization.
7. The canonical evidence ref is read before use. If absent, initialize it only through the existing GitHub Canonical Execution Evidence Store. Do not manually synthesize Run or completion records.
8. Manager PR #15 is read-only and remains outside the mutation scope.

## Execution Steps

### Step 1 — Read-only Admission and Binding Check

- Re-read the canonical Task, this Plan, current test repository main/HEAD, DevForge main, PR #221 head/state, project registration, execution authorization and evidence ref.
- Verify exact Task/Plan/repository/Runtime identities and clean working tree.
- Confirm the registered candidate route is `chatgpt_direct_bridge_tool_loop` and the adapter is `adapters/development/chatgpt-local-engineering-host.md`.
- Confirm the Task-owned mutation scope is limited to `src/task_status.py` and `tests/test_task_status.py` plus required canonical evidence artifacts on the separate evidence ref.
- Stop before mutation if any binding, authorization, repository permission or candidate revision differs.

### Step 2 — Direct Bridge Whole-Plan Work

- Use ChatGPT to invoke the existing Linux Coco Lite Bridge `list`/`read` tools and observe their returned outputs.
- Use the existing Bridge write/patch operation to add a deterministic status-normalization helper in `src/task_status.py` and focused tests in `tests/test_task_status.py`.
- Use Bridge `exec` to run the focused test suite; observe the actual exit code and output before deciding whether to proceed.
- Run a deliberately failing, non-mutating command with a known non-zero exit code and verify the failure is preserved as failure, not converted to success.
- If a write or command result is uncertain, read back Git status, file bytes and process/job state before any retry. Never replay an uncertain external effect.
- Do not construct or inject a Python `execution_host` for ordinary file operations, shell commands or tests.

### Step 3 — Canonical Evidence and Completion Boundary

- Use only the existing `GitHubCanonicalExecutionEvidenceStore` and its registered controller/transition capabilities where those capabilities are genuinely callable and authorized.
- Record/read back real Operation Receipt and Checkpoint evidence using the existing contract; bind every record to this Task, this Plan revision/digest, the actual Run/Attempt, provider/transport and exact implementation HEAD.
- Verify Window Close through its real persisted evidence and Run Ledger event; independently read back both.
- Verify Run Finalization only after the existing completion reconciler can read a completed canonical Run Ledger, valid Window Close, Checkpoint and Implementation Verification Receipt.
- Re-read the evidence ref, index and every referenced changed blob; verify SHA-256/identity and canonical ref advancement.
- If a controller-owned transition has no existing authorized callable path from the current direct-tool Host, stop at that exact transition and report the missing capability. Do not hand-write substitute receipts or mark the Run/Task complete.

## Scope and Safety

- Allowed product-code paths: `src/task_status.py`, `tests/test_task_status.py` in this isolated repository only.
- Allowed evidence path: the existing `devforge/execution-evidence` branch and its contract-defined Run/index paths.
- No new execution framework, service, daemon, Gate, provider, lifecycle or evidence store.
- No changes to DevForge main or PR #221 source branch during this product test.
- No changes to Manager PR #15 code, Task, Plan, Gate, transport, branch or historical Run.
- No PR creation is required for this local-file Task transport; do not create an Issue or PR merely to expose Task state.
- No merge, release, deployment or Feature Acceptance approval.

## Acceptance Criteria

1. Direct Linux Bridge calls are evidenced by actual tool outputs and result-driven continuation.
2. Focused tests pass on the exact implementation HEAD and the HEAD is independently read back.
3. Controlled failure preserves the real non-zero result and cannot yield false completion.
4. Canonical Run/Checkpoint/Window Close/Finalization records, when claimed, are generated through existing authorized mechanisms and independently read back with matching identities and digests.
5. If a required evidence transition is not callable, the Task is explicitly blocked at that transition with a precise missing-capability report; no completion claim is made.
6. Manager PR #15 remains unchanged, and no unrelated repository/Runtime mutation occurs.

## Current Gate State

- Requirement Ready: true (Task-owned refinement evidence)
- Plan Approved: false — pending formal Plan Review
- Implementation authorization: not yet issued for this Plan revision
- Implementation: not started
- Acceptance: not approved
