# Test-First Tasks Wrapper

Apply these requirements in addition to the core task-generation workflow.

## Critical Override: Tests Are Not Optional
If the core command or template says tests are optional, replace that rule with this preset rule: tests are mandatory. Generate TDD tasks for production logic. Generate ATDD and BDD tasks when the specification marks them `Required`; preserve justified `N/A` decisions and report missing or contradictory rationales as blocking gaps.

## Mandatory Task Ordering
For each user story, create tasks in this exact sequence:
1. Required `[ATDD]` Gherkin acceptance scenarios.
2. Required `[BDD]` Gherkin behavior scenarios.
3. `[ATDD]` and `[BDD]` executable step bindings/support fixtures.
4. `[TDD]` failing unit/component/integration/contract/property/negative tests.
5. `[GATE]` update `specs/<feature>/test-traceability.md` with planned artifact IDs, paths, and commands.
6. `[TDD]`, `[BDD]`, `[ATDD]` red-state execution tasks proving tests fail for expected reasons and updating matrix status to `Red`.
7. Production implementation tasks.
8. Refactor tasks.
9. `[GATE]` validation tasks for the full test suite, coverage, linting, formatting, and every gate marked `Required`.
10. `[GATE]` update matrix results to `Green`, `Blocked`, or approved `N/A` and perform the final traceability review.

## Mandatory Task Labels
Use this extended format for all test and gate tasks:

```text
- [ ] T### [P?] [US#?] [TDD|BDD|ATDD|GATE] Description with exact file path
```

`[GATE]` is allowed only for non-product validation tasks and MUST state the protected suite or evidence destination.

The label identifies primary suite ownership. If an artifact supports multiple evidence roles, create one task under its owning-suite label and record the other mappings in the description and traceability matrix. Do not generate equivalent tasks or artifacts solely to satisfy multiple labels.

## Required Per-Story Minimum
Each user story MUST include at least:
- one `[ATDD]` Gherkin feature task when ATDD is `Required`;
- one `[BDD]` Gherkin feature task when BDD is `Required`;
- one `[TDD]` happy-path test task;
- one `[TDD]` edge/error/boundary test task;
- red-state run tasks before implementation, with evidence retained in task/PR/CI output or an audit-required report;
- green-state run tasks after implementation;
- a `[GATE]` task updating `specs/<feature>/test-traceability.md` before implementation and after execution.

{CORE_TEMPLATE}

## Additional Completion Report Fields
Include in the task generation completion report:
- Count of `[TDD]`, `[BDD]`, `[ATDD]`, and `[GATE]` tasks
- Confirmation that no implementation task precedes its required tests
- List of Gherkin feature files planned for BDD and ATDD
- List of BDD/ATDD `N/A` decisions with rationale and alternative evidence
- List of gate applicability decisions, commands, thresholds, and evidence destinations
- Confirmation that traceability creation and update tasks use `specs/<feature>/test-traceability.md`
