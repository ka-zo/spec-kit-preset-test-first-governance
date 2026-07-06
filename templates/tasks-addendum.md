
---

## Mandatory Test-First Task Rules *(overrides any optional-test wording)*

Tests are **mandatory** for every feature. If any lower-priority or core template says tests are optional, this preset supersedes that wording. Create TDD tasks for production logic. Create BDD and ATDD tasks when the specification marks those practices `Required`; preserve justified `N/A` decisions instead of creating ceremonial scenarios.

### Extended Task Format
Every task MUST keep the Spec Kit checkbox and ID format and add a suite label when the task creates, modifies, runs, or validates tests.

```text
- [ ] T### [P?] [US#?] [TDD|BDD|ATDD|GATE] Description with exact file path
```

Rules:
- The suite label identifies the artifact's primary owner; it does not claim that TDD, BDD, and ATDD are mutually exclusive test types.
- If one artifact supplies multiple evidence roles, use its owning-suite label and name the additional mappings in the task description and traceability matrix.
- Never create duplicate test tasks solely to represent the same evidence under another suite label.
- `[TDD]` is required for unit, component, integration, contract, property, boundary, negative, mutation, or implementation-level test tasks.
- `[BDD]` is required for Gherkin behavior feature files, step definitions, behavior fixtures, and BDD runner/report tasks.
- `[ATDD]` is required for acceptance Gherkin feature files, acceptance step definitions, and system/e2e acceptance fixtures.
- `[GATE]` is allowed only for non-product quality gates such as traceability maintenance, lint, formatting, static analysis, security validation, dependency audit, coverage aggregation, applicable runtime smoke, and evidence publishing. Each `[GATE]` task MUST state which suite outputs or governance artifact it protects.
- Production implementation tasks SHOULD NOT use a suite label unless the task directly modifies test code.

### Required Phase Shape Per User Story
Within each user story phase, tasks MUST appear in this order:

1. **Required ATDD specification tasks** — Gherkin acceptance feature files under `tests/atdd/features/`.
2. **Required BDD specification tasks** — Gherkin behavior feature files under `tests/bdd/features/`.
3. **Executable test binding tasks** — ATDD/BDD step definitions, support code, and fixtures.
4. **TDD test tasks** — failing unit/component/integration/contract/property/negative tests under `tests/tdd/`.
5. **Traceability planning update** — add planned artifact IDs, paths, and commands to `specs/<feature>/test-traceability.md`.
6. **Expected failure checkpoint** — run the relevant tests, confirm they fail for the intended reason, and record `Red` evidence.
7. **Implementation tasks** — production code only after the above tests exist and fail.
8. **Refactor tasks** — improve design without changing behavior.
9. **Validation checkpoint** — run TDD, all required BDD/ATDD suites, coverage, linting, formatting, and every gate marked `Required`.
10. **Traceability result update** — record final `Green`, `Blocked`, or approved `N/A` evidence.

Shared bindings, fixtures, or helpers MUST be created once under `tests/support/` (or the selected equivalent) and referenced by each consuming suite.

When BDD or ATDD is `N/A`, add no tasks for that practice. The story's tasks MUST reference the recorded rationale and alternative evidence; task generation MUST report a blocking gap if the rationale is missing or contradicted by the story.

### Required Example Tasks Per Story
Use the applicable lines from this example, adapted to the selected stack. Omit BDD or ATDD lines only when the corresponding practice is justified `N/A`:

```markdown
### Tests for User Story N - [Title] *(MANDATORY: write before implementation)*
- [ ] T010 [P] [USN] [ATDD] Create Gherkin acceptance scenario @ATDD-USN-001 in tests/atdd/features/acceptance/[feature].feature
- [ ] T011 [P] [USN] [BDD] Create Gherkin behavior scenario @BDD-USN-001 in tests/bdd/features/user-stories/[feature].feature
- [ ] T012 [P] [USN] [ATDD] Implement failing acceptance step bindings for @ATDD-USN-001 in tests/atdd/steps/[feature]_steps.[ext]
- [ ] T013 [P] [USN] [BDD] Implement failing behavior step bindings for @BDD-USN-001 in tests/bdd/steps/[feature]_steps.[ext]
- [ ] T014 [P] [USN] [TDD] Create failing unit tests for [domain/service] happy path and boundary cases in tests/tdd/unit/test_[name].[ext]
- [ ] T015 [P] [USN] [TDD] Create failing negative/error-path tests for [validation/failure mode] in tests/tdd/negative/test_[name].[ext]
- [ ] T016 [USN] [GATE] Add planned artifact IDs, paths, and commands to specs/<feature>/test-traceability.md
- [ ] T017 [USN] [TDD] Run story TDD tests and record expected red evidence in task/PR/CI output and the matrix
- [ ] T018 [USN] [BDD] Run story BDD scenarios and record expected red evidence in task/PR/CI output and the matrix
- [ ] T019 [USN] [ATDD] Run story ATDD scenarios and record expected red evidence in task/PR/CI output and the matrix

### Implementation for User Story N
- [ ] T020 [USN] Implement minimal production code for [capability] in src/[path]
- [ ] T021 [USN] Refactor [module] after tests pass without changing behavior in src/[path]
- [ ] T022 [USN] [GATE] Run TDD, required BDD/ATDD, coverage, linting, formatting, and all gates marked Required; retain evidence per the plan
- [ ] T023 [USN] [GATE] Update specs/<feature>/test-traceability.md with final statuses and evidence paths
```

### Global Quality Gate Tasks
The final phase MUST include:
- `[GATE]` coverage aggregation for TDD and changed production code.
- `[GATE]` BDD scenario report confirming 100% planned scenario pass rate when BDD is `Required`.
- `[GATE]` ATDD scenario report confirming 100% planned acceptance scenario pass rate when ATDD is `Required`.
- `[GATE]` linting and formatting checks for source and tests.
- `[GATE]` required static analysis or type checking for source and tests.
- `[GATE]` required security and runtime smoke validation where applicable.
- `[GATE]` traceability review proving all FR/SC/US/EC IDs map to current statuses and execution evidence.
