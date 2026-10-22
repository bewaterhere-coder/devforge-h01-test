# Whole-Plan Direct Linux Bridge Product Verification — Plan Revision 2

## Canonical Binding

- Task ID: **TASK-WHOLE-PLAN-DIRECT-BRIDGE-001**
- Task artifact: **docs/tasks/TASK-WHOLE-PLAN-DIRECT-BRIDGE-001.md**
- Task Git blob at remediation admission: **ee5804c54c16609fb229c906bea6afcdf88ef0f4**
- Task SHA-256 at remediation admission: **fbdb34dd35c65422771fc45aaa6a251f2a9c9e1f459db75170a6b6fdaac90f58**
- Requirement revision: **1**
- Canonical Requirement JSON SHA-256: **de5a2791c45c787b05799de54aac92ae1ab8d322cb51b0d2ef06f55e90a41991**
- Project repository: **bewaterhere-coder/devforge-h01-test**
- Project ID: **devforge-h01-test**
- Canonical transport: **local_file**, repository **bewaterhere-coder/devforge-h01-test**, branch **main**
- Execution shape: **whole_plan**
- Canonical Plan path: **docs/plans/TASK-WHOLE-PLAN-DIRECT-BRIDGE-001-plan.md**
- Plan revision: **2**
- Plan status: **Draft — Plan Review Pending**
- Plan approval: **false**
- Predecessor Plan Revision 1 Git blob: **e0dedb6ce6f816b68c84ddfedeae7dc08b10465d**
- Predecessor Plan Revision 1 SHA-256: **352339e5721cb5e3ba500e58bd8cdeeee02e94e4fb2d0d04c11810156dcceb7e**
- Predecessor rejected review: **docs/reviews/TASK-WHOLE-PLAN-DIRECT-BRIDGE-001-plan-v1-review.json**
- Predecessor review Git blob: **c0e00bb005a493aeb02d22d592675d970b077b1f**
- Predecessor review SHA-256: **5f3cda759461f9ebb77fc062b12e0422d7ee34bc7ed9ffbde69cbd3404640346**
- Candidate Runtime: **bewaterhere-coder/DevForge PR #221**, exact head **975362bb0573d313654b7a6ecbc004d4e402f8b3**
- Candidate PR state at remediation: **open, Draft, not merged**
- Candidate PR base ref: **main**; API-reported base snapshot: **5a5e2d1e85b41d725a9d152f8bf1bd6f300bfd37**
- Current DevForge main at remediation: **af5ef1f4589e8020adf38d5af177e5d09a537773**
- Accepted Evolution: **EVO-CHATGPT-WHOLE-PLAN-LINUX-BRIDGE-EXECUTION-BINDING-V1-001**, Revision 2
- Accepted Definition SHA-256: **946c9470bc5214e55df5650421042964e67af15ede2b38de7f27f9e9a2c41577**
- Canonical execution evidence repository/ref: **bewaterhere-coder/devforge-h01-test / devforge/execution-evidence**
- Authorization mode at remediation admission: **legacy_command_scoped**
- Durable authorization reference at remediation admission: **absent**

Revision 1 remains historical in Git and its rejected review remains immutable. Revision 2 supersedes the current contents at the same canonical Plan path; it does not create a new Task, Requirement, repository, branch, PR, Run, or evidence store.

## Objective

Verify whether one independently authorized, isolated Whole-Plan Task can be executed by ChatGPT through the existing Linux Coco Lite Bridge tools with real result-driven continuation and honest canonical evidence boundaries. Keep the current Task, Requirement revision, transport identity, and original acceptance criteria unchanged.

This Plan evaluates the exact PR #221 candidate separately from current DevForge main. It must not claim that the candidate route is already the current main route.

## Remediation of PBR-001 — Deterministic Status Contract and Test Oracle

The isolated test helper is defined as follows before implementation:

- Function contract: **normalize_status(value: str) -> str**.
- Accepted canonical statuses: **pending**, **running**, **succeeded**, **failed**.
- Normalization: trim leading/trailing whitespace, then lowercase the string.
- A normalized accepted value is returned unchanged in canonical lowercase form.
- No aliases, coercion, I/O, persistence, or side effects are allowed.
- A non-string input raises **TypeError**.
- An empty or whitespace-only string raises **ValueError**.
- A normalized value outside the accepted set raises **ValueError**.
- The helper is test-fixture behavior for this isolated repository; it does not declare a production application-wide status contract.

Required table-driven cases and expected outcomes:

| Input | Expected result |
| --- | --- |
| **pending** | **pending** |
| ** RUNNING ** | **running** |
| **Succeeded** | **succeeded** |
| **FAILED** | **failed** |
| empty string | **ValueError** |
| whitespace-only string | **ValueError** |
| **unknown** | **ValueError** |
| **None** | **TypeError** |

The tests must assert both returned values and exception types. These cases are the test oracle for the proposed helper and do not change Requirement revision 1.

## Remediation of PBR-002 — Candidate Runtime Route Validation

### Pinned route identity

Before any product-code mutation, re-read and verify:

1. The Task, this Plan Revision 2, the canonical transport, and the current Task Gate from the test repository's remote main.
2. PR #221 state and exact candidate HEAD **975362bb0573d313654b7a6ecbc004d4e402f8b3**.
3. Current DevForge main independently; at remediation it is **af5ef1f4589e8020adf38d5af177e5d09a537773**, not the candidate HEAD.
4. At the exact candidate commit, resolve the existing route across **system/runtime-router.yaml**, **system/capability-registry.yaml**, **system/command-registry.yaml**, and **adapters/development/chatgpt-local-engineering-host.md**.
5. The candidate route declaration must resolve Whole-Plan execution to **chatgpt_direct_bridge_tool_loop** and the existing **direct_existing_bridge_tool_calls** adapter mapping. The route is ChatGPT-Host behavior, not a new Python entry point.
6. Compare with current main's actual declaration. At remediation, current main still maps Whole-Plan execution to **tools/whole_plan_host_artifact_store.py::execute_registered_whole_plan** and the existing Python controller path; it must not be described as already using the candidate default.

### Observable live-route proof

After Plan approval and separate execution authorization, the route test must use an existing authorized mechanism that can actually select the exact candidate Runtime revision. The execution evidence must, using fields supported by the existing canonical evidence contract, bind all of the following:

- candidate repository, PR number, and exact candidate HEAD;
- current DevForge main HEAD as a distinct baseline;
- the route actually selected by the Host and the exact adapter path;
- proof that the selected path is **chatgpt_direct_bridge_tool_loop**, rather than the current-main Python-controller route;
- each actual Linux Coco Lite Bridge tool operation, its observed result/exit status, and the subsequent decision that was based on that result;
- exact Task, Plan revision/digest, repository, transport, and implementation HEAD lineage.

A registry declaration, a static adapter read, or a successful direct Bridge command alone is not proof that the registered candidate route was selected. Do not model-author a route-success flag or add a new evidence schema/store merely to make the test pass.

**Fail-closed route boundary:** if no existing authorized Host mechanism can select and independently evidence the exact candidate route, stop before changing product files. Report the precise missing dispatch/readback capability. Direct Bridge operations may be reported as direct tool operations only; they must not be represented as a successful formal candidate-route invocation. Do not claim the candidate Runtime was product-tested when it was not.

### Direct Bridge operation sequence, only after route admission

1. Use the existing Linux Coco Lite Bridge read/list operations to inspect the isolated repository, current files, Git state, and test environment. Observe the returned outputs.
2. Restrict product-code mutation to **src/task_status.py** and **tests/test_task_status.py**. No other product-code paths are in scope.
3. Implement the helper and table-driven tests exactly as defined under PBR-001.
4. Run the focused test suite with the existing Bridge exec operation. Capture the real command, output, and exit code; decide whether to continue only after observing that result.
5. Run a deliberately failing, non-mutating command with a known non-zero exit code. Verify the actual failure remains a failure and cannot be reported as successful completion.
6. If any write or command outcome is uncertain, read back Git status, file contents, process/job status, and canonical evidence state before deciding whether a retry is safe. Never replay an uncertain side effect.

## Remediation of PBR-003 — Authorization and Write-Scope Separation

The Task currently uses **legacy_command_scoped** and has no durable authorization reference. This remediation does not issue, upgrade, or broaden authorization and does not change the Task's authorization mode.

Before any later product-code mutation, the following separate authorization precondition applies:

1. First, the revised Plan must pass an independent **#开发评审**. Plan approval alone does not grant execution authorization.
2. Because the Task's Requirement requires independently authorized execution, the only existing registered issuer for a Durable Development Authorization is the explicit **#开发** command resolving to **development.task**, governed by **system/durable-development-authorization-contract.md**. Use that issuer on this exact existing Task only if the current registered path admits it; do not create an authorization file manually or infer issuer authority from this remediation command.
3. The issuer must persist the canonical authorization artifact using the project's registered transport-specific path, update the same Task's **development.authorization.ref**, and independently read back both. Do not hardcode or guess an authorization path.
4. Readback must verify the exact repository and Task subject, unchanged Requirement revision/digest, active lifecycle state, and the authorized actions required for the planned implementation/verification. Once Plan Revision 2 is approved, any supported Plan binding may narrow to this exact Plan path and revision; it cannot broaden allowed actions.
5. Durable Development Authorization does **not** grant or encode Host, provider, tool, filesystem, sandbox, Git, or per-file write scope. The execution Host must separately admit the exact write scope **src/task_status.py** and **tests/test_task_status.py** under its existing mutation-scope and live operational checks.
6. If the registered **#开发** issuer cannot establish and independently read back the required authorization for this existing Task, stop before product-code mutation and report the exact missing capability. Do not silently keep treating an absent authorization reference as durable authority and do not fall back to manually fabricated authorization.

The current legacy mode remains unchanged throughout this remediation. No authorization artifact is created or modified by this Plan Revision.

## Execution Steps

### Step 1 — Read-only admission and binding

- Re-read the canonical Task, embedded Requirement, this Plan, predecessor review/remediation history, project registration, and remote repository HEAD.
- Verify Task ID, Requirement revision and digest, transport identity, **execution_shape: whole_plan**, Plan revision/digest, and the exact candidate/current-main bindings above.
- Read the existing **devforge/execution-evidence** ref and inspect it through the existing canonical evidence contract/store before use. If it is absent, initialize it only through the existing registered store mechanism; never hand-write a substitute ledger or completion record.
- Read Manager PR #15 as read-only and record its current HEAD before the product test. Re-read it afterward and confirm this Task made no change to its PR, Task, Plan, Gate, transport, branch, or historical Run.
- Stop before product mutation on any Task/Plan/Requirement/transport drift, dirty or uncertain worktree, changed candidate HEAD, missing required permission, unresolved authorization, or failed route-admission proof.

### Step 2 — Candidate route and authorization admission

- Complete the observable candidate route check defined under PBR-002.
- Complete the separate authorization readback defined under PBR-003 after the revised Plan has been approved.
- Re-resolve the exact Task Gate, current approved Plan revision/digest, current repository HEAD, and Host write-scope admission immediately before the first product-code mutation.
- Do not begin implementation if any of these checks is unavailable, inconsistent, or unauthorized.

### Step 3 — Whole-Plan implementation and verification

- Perform only the two scoped file changes, using actual Bridge tool calls and observed results.
- Verify every table-driven status case and the controlled non-zero exit case.
- Run the focused test suite; preserve actual stdout/stderr and exit status.
- Independently read back the exact source/test bytes and Git HEAD after the edits. No unrelated files may be modified.
- Keep direct tool-operation evidence distinct from proof of formal route selection and from proof of canonical Run completion.

### Step 4 — Canonical execution evidence and completion boundary

- Use only the existing **GitHubCanonicalExecutionEvidenceStore** and the current **system/github-canonical-execution-evidence-store-contract.md** on **devforge/execution-evidence** for canonical Run, Operation Receipt, Checkpoint, Window Close, verification, and Finalization records.
- Persist and independently read back each required record through existing authorized operations, preserving the contract's operation-receipt-before-checkpoint and window-close-before-run-completion ordering.
- Bind evidence to the exact Task, Requirement revision/digest, Plan Revision 2/digest, candidate Runtime HEAD, repository/transport, actual Run/Attempt, selected route, and implementation HEAD wherever the existing schema supports those fields.
- Re-read the evidence ref/index and every referenced changed blob; verify identities, digests, and ref advancement before making any completion claim.
- If a required controller-owned or canonical evidence transition is not callable through the existing authorized interface, stop at that exact transition and report the missing capability. Do not synthesize Run, Operation Receipt, Checkpoint, Window Close, verification, Finalization, or completion projections.
- A passing test suite or successful direct Bridge command alone is not Task completion, formal candidate-route proof, Acceptance, merge, or release.

## Scope and Safety

- Product-code paths allowed: **src/task_status.py**, **tests/test_task_status.py**.
- Canonical execution evidence: the existing **devforge/execution-evidence** ref and contract-defined artifact paths only.
- Planning/remediation artifacts: the current Task's existing Plan path plus the same Task's remediation/review evidence paths.
- No DevForge Runtime source changes.
- No Manager PR #15 changes.
- No new Task, Requirement, PR, branch, Run, execution framework, route registry, service, daemon, Gate, or evidence store.
- No implementation before independent Plan approval and separate execution authorization.
- No Plan self-approval, Acceptance approval, merge, release, or deployment.
- No authorization issuance, expansion, or mode migration during Plan remediation.

## Acceptance Criteria

1. The same canonical Task is read back with **execution_shape: whole_plan** and unchanged Requirement revision 1/digest and transport identity.
2. The Plan is independently reviewed and explicitly approved before implementation; execution authorization remains separate from Plan approval.
3. The exact PR #221 candidate route is either evidenced by an actual authorized Host invocation and real Bridge result lineage, or the Task stops at the precise unavailable route boundary without claiming the route was tested.
4. Actual Linux Coco Lite Bridge calls are used for product work; no Python execution_host is constructed or injected for ordinary file edits, commands, or tests.
5. The status helper follows the exact PBR-001 contract and every table-driven expected case passes.
6. The controlled non-mutating failure preserves the actual non-zero exit result.
7. The focused tests pass on the exact implementation HEAD, which is independently read back.
8. Canonical execution evidence is produced only through the existing store/contract and independently read back; unsupported transitions block the dependent completion claim.
9. Manager PR #15 remains unchanged; no DevForge Runtime source or unrelated project is mutated.

## Current Gate State

- Requirement Ready: true, from the existing Task-owned readiness evidence.
- Plan Revision 2 approval: **false — pending independent Plan Review**.
- Task authorization at remediation entry: **legacy_command_scoped**, no durable reference.
- Authorization issued by this remediation: **no**.
- Implementation started: **no**.
- Acceptance approved: **no**.
- Merge/release/deployment: **not authorized**.

## Revision History

- **Revision 1:** rejected by the formal Plan Review on 2026-10-22; PBR-001, PBR-002, and PBR-003 are the authoritative remediation inputs.
- **Revision 2:** defines a deterministic status test oracle, adds a candidate-specific route selection/readback gate with explicit fail-closed behavior, and separates the registered authorization issuer from Host write-scope admission. It is ready for independent review only; it is not approved for execution.
