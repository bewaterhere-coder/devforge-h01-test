kind: development_task
task_id: TASK-WHOLE-PLAN-DIRECT-BRIDGE-001
title: Whole-Plan Direct Linux Bridge Product Verification
repository: bewaterhere-coder/devforge-h01-test
requirement_revision: 1
requirement:
  problem: 'DevForge PR #221 declares ChatGPT direct Linux Coco Lite Bridge tool calls
    as the default Whole-Plan path, but existing Bridge smoke and isolated controller
    fixtures do not prove a complete canonical product Task execution.'
  goal: Verify one independently authorized, isolated Whole-Plan Task can be executed
    by ChatGPT through the existing Linux Coco Lite Bridge tools with real result-driven
    continuation and honest canonical evidence boundaries.
  scope:
  - 'Bind the test to DevForge PR #221 head 975362bb0573d313654b7a6ecbc004d4e402f8b3
    and Accepted Evolution Definition Revision 2 SHA-256 946c9470bc5214e55df5650421042964e67af15ede2b38de7f27f9e9a2c41577.'
  - Use only this isolated test repository and the existing Linux Coco Lite Bridge;
    do not modify DevForge Runtime source or unrelated projects.
  - Execute a minimal deterministic test change using direct Bridge read/write/exec
    calls and use returned outputs to decide subsequent actions.
  - Verify real failure propagation and safe read-before-resume behavior without replaying
    uncertain side effects.
  - Use the existing GitHub Canonical Execution Evidence Store and contracts for Run,
    Operation Receipt, Checkpoint, Window Close and Finalization; independently read
    back every required artifact.
  - Record exact Task, Plan, candidate Runtime, repository HEAD, provider and transport
    bindings in all applicable evidence.
  acceptance_criteria:
  - A newly created canonical Task persists execution_shape=whole_plan and is independently
    read back by the exact canonical locator.
  - A Plan is reviewed and explicitly approved before implementation execution; execution
    authorization remains separate from Plan approval.
  - ChatGPT invokes the actual existing Linux Coco Lite Bridge tools directly; no
    Python execution_host is injected or required for ordinary file edits, commands
    or tests.
  - Tool results and exit codes are observed faithfully; a controlled failing operation
    remains a failure and does not produce false completion.
  - The isolated implementation/test passes and its exact source HEAD is independently
    read back.
  - The canonical evidence store is initialized or reused only through its existing
    contract, and required Run/Checkpoint/Window Close/Finalization artifacts are
    independently read back with matching identities and digests.
  - If an existing required transition cannot be invoked through an authorized current
    mechanism, the task stops at that transition and reports the exact missing capability
    without synthesizing evidence.
  - 'Historical slice_set compatibility remains untouched; Manager PR #15, its Task,
    Plan, Gate, transport, branch and historical Run remain unchanged.'
  non_goals:
  - 'Do not merge or release PR #221.'
  - 'Do not deploy production or modify Manager PR #15.'
  - Do not create another execution framework, service, daemon, Gate or evidence store.
  - Do not reuse H02/H04 fixtures as the current product Task or reuse old Run/Checkpoint/Receipt
    records.
  - Do not self-approve Feature Acceptance or fabricate any Run, Checkpoint, Window
    Close, Receipt or Finalization.
  refinement_evidence:
    depth: standard
    challenge:
    - 'Normal case: a three-step whole Plan proceeds from direct Bridge inspection
      to a small deterministic edit and a passing test using actual returned outputs.'
    - 'Counterfactual: a Bridge command returns a non-zero exit code; the failure
      must remain visible and must not be treated as completion.'
    - 'Recovery case: if a tool result or write outcome is uncertain, re-read repository
      and canonical evidence state before retry; never replay uncertain side effects.'
    - 'Boundary case: direct tool calls can perform development work but do not automatically
      prove controller-owned finalization; missing transition capability must stop
      the dependent completion claim.'
    - 'Invariant: the test stays within this repository and cannot mutate Manager
      PR #15 or DevForge main.'
    unresolved_material_decisions: []
    readiness_decision: ready_for_planning
development:
  stage: plan_review
  gates:
    requirement_ready: true
    plan_approved: false
    acceptance_approved: false
    completion_verified: false
  next_expected_actor: reviewer
  authorization:
    mode: legacy_command_scoped
artifacts:
  plan: docs/plans/TASK-WHOLE-PLAN-DIRECT-BRIDGE-001-plan.md
transport:
  type: local_file
  repository: bewaterhere-coder/devforge-h01-test
  branch: main
execution_shape: whole_plan
