
---

## Mandatory Test-First Task Rules *(overrides any optional-test wording)*

Tests are **mandatory** for every feature. If any lower-priority or core template says tests are optional, this preset supersedes that wording. Create TDD tasks for production logic. Create the minimum non-duplicative scenario tasks needed to cover every `Required` BDD and ATDD evidence role; preserve justified `N/A` decisions instead of creating ceremonial scenarios.

### Core-Compatible Task Format
Every task MUST keep the core Spec Kit checkbox, task ID, parallel marker, and `[US#]` story-label format. For test and gate tasks, place the owning-suite marker as the first token of the description.

```text
- [ ] T### [P?] [US#?] [TDD|BDD|ATDD|GATE] Description with exact file path
```

Rules:
- `[TDD]`, `[BDD]`, `[ATDD]`, and `[GATE]` extend the task description; they do not replace or alter core `T###`, `[P]`, or `[US1]` identifiers.
- The suite label identifies the artifact's primary owner; it does not claim that TDD, BDD, and ATDD are mutually exclusive test types.
- If one artifact supplies multiple evidence roles, use its owning-suite label and name the additional mappings in the task description and traceability matrix.
- Never create duplicate test tasks solely to represent the same evidence under another suite label.
- A `Required` BDD or ATDD role does not require a task with that suite label when an artifact owned by another suite fully provides the required evidence.
- `[TDD]` is required for unit, component, integration, contract, property, boundary, negative, mutation, or implementation-level test tasks.
- `[BDD]` is required for Gherkin behavior feature files, step definitions, behavior fixtures, and BDD runner/report tasks.
- `[ATDD]` is required for acceptance Gherkin feature files, acceptance step definitions, and system/e2e acceptance fixtures.
- `[GATE]` is allowed only for non-product quality gates such as traceability maintenance, lint, formatting, static analysis, security validation, dependency audit, coverage aggregation, applicable runtime smoke, and evidence publishing. Each `[GATE]` task MUST state which suite outputs or governance artifact it protects.
- Production implementation tasks SHOULD NOT use a suite label unless the task directly modifies test code.

### Required Phase Shape Per User Story
Within each user story phase:

1. **Scenario specification** — create the minimum non-duplicative set of scenarios that covers all required ATDD acceptance and BDD behavior evidence roles before production implementation begins.
2. **Traceability planning update** — add planned artifact IDs, paths, commands, and behavior slices to `specs/<feature>/test-traceability.md`.
3. **Incremental behavior cycles** — divide the story into the smallest meaningful slices that can be independently verified. For each slice, tasks MUST appear in this order:
   1. **Executable evidence** — add only the ATDD/BDD bindings and TDD tests needed for the current slice.
   2. **Expected failure checkpoint** — run the new evidence, confirm it fails for the intended missing behavior, and record `Red`.
   3. **Minimal implementation** — add only the production code needed to make the current slice pass.
   4. **Passing checkpoint** — rerun the slice evidence and record `Green`.
   5. **Refactor** — improve the design and rerun the relevant evidence while it remains green.
4. **Repeat** — complete the cycle before adding executable evidence for the next slice; do not accumulate all failing tests for the story before any production implementation.
5. **Story validation checkpoint** — after all slices are green, run TDD and all executable evidence mapped to required BDD/ATDD roles, plus coverage, linting, formatting, and every gate marked `Required`.
6. **Traceability result update** — record final `Green`, `Blocked`, or approved `N/A` evidence.

Shared bindings, fixtures, or helpers MUST be created once under `tests/support/` (or the selected equivalent) and referenced by each consuming suite.

When BDD or ATDD is `N/A`, add no tasks for that practice. The story's tasks MUST reference the recorded rationale and alternative evidence; task generation MUST report a blocking gap if the rationale is missing or contradicted by the story.

### Required Example Tasks Per Story
Use the applicable lines from this example, adapted to the selected stack. The example uses distinct scenarios because its acceptance and behavior evidence differ. When one scenario fully satisfies both roles, keep only its owning-suite tasks and record both roles in traceability.

```markdown
### Tests for User Story 1 - [Title] *(MANDATORY: write before implementation)*
- [ ] T010 [P] [US1] [ATDD] Create Gherkin acceptance scenario @ATDD-US1-001 in tests/atdd/features/acceptance/[feature].feature
- [ ] T011 [P] [US1] [BDD] Create Gherkin behavior scenario @BDD-US1-001 in tests/bdd/features/user-stories/[feature].feature
- [ ] T012 [US1] [GATE] Add planned artifact IDs, paths, commands, and behavior slices to specs/<feature>/test-traceability.md

### Behavior Slice 1 - [Happy-path capability]
- [ ] T013 [P] [US1] [ATDD] Implement failing acceptance binding for @ATDD-US1-001 in tests/atdd/steps/[feature]_steps.[ext]
- [ ] T014 [P] [US1] [TDD] Create failing test TDD-US1-001 for [happy-path behavior] in tests/tdd/unit/test_[name].[ext]
- [ ] T015 [US1] [ATDD] Run @ATDD-US1-001 and record its expected Red result in task/PR/CI output and the matrix
- [ ] T016 [US1] [TDD] Run TDD-US1-001 and record its expected Red result in task/PR/CI output and the matrix
- [ ] T017 [US1] Implement the minimal production change for [happy-path capability] in src/[path]
- [ ] T018 [US1] [ATDD] Rerun @ATDD-US1-001 and record its Green result in task/PR/CI output and the matrix
- [ ] T019 [US1] [TDD] Rerun TDD-US1-001 and record its Green result in task/PR/CI output and the matrix
- [ ] T020 [US1] Refactor [module] while keeping the slice 1 evidence green in src/[path]

### Behavior Slice 2 - [Boundary or error behavior]
- [ ] T021 [P] [US1] [BDD] Implement failing behavior binding for @BDD-US1-001 in tests/bdd/steps/[feature]_steps.[ext]
- [ ] T022 [P] [US1] [TDD] Create failing test TDD-US1-002 for [failure mode] in tests/tdd/negative/test_[name].[ext]
- [ ] T023 [US1] [BDD] Run @BDD-US1-001 and record its expected Red result in task/PR/CI output and the matrix
- [ ] T024 [US1] [TDD] Run TDD-US1-002 and record its expected Red result in task/PR/CI output and the matrix
- [ ] T025 [US1] Implement the minimal production change for [boundary or error behavior] in src/[path]
- [ ] T026 [US1] [BDD] Rerun @BDD-US1-001 and record its Green result in task/PR/CI output and the matrix
- [ ] T027 [US1] [TDD] Rerun TDD-US1-002 and record its Green result in task/PR/CI output and the matrix
- [ ] T028 [US1] Refactor [module] while keeping the slice 2 evidence green in src/[path]

### User Story 1 Completion
- [ ] T029 [US1] [GATE] Run TDD, all evidence mapped to required BDD/ATDD roles, coverage, linting, formatting, and all gates marked Required; retain evidence per the plan
- [ ] T030 [US1] [GATE] Update specs/<feature>/test-traceability.md with final statuses and evidence paths
```

### Global Quality Gate Tasks
The final phase MUST include:
- `[GATE]` coverage aggregation for TDD and changed production code.
- `[GATE]` evidence report confirming 100% of scenarios mapped to required BDD and ATDD roles pass; reuse one owning-suite result when a scenario supplies both roles.
- `[GATE]` linting and formatting checks for source and tests.
- `[GATE]` required static analysis or type checking for source and tests.
- `[GATE]` required security and runtime smoke validation where applicable.
- `[GATE]` traceability review proving all FR/SC/US/EC IDs map to current statuses and execution evidence.
