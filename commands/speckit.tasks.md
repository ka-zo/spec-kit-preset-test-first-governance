# Test-First Tasks Wrapper

Apply these requirements in addition to the core task-generation workflow.

## Critical Override: Tests Are Not Optional
If the core command or template says tests are optional, replace that rule with this preset rule: tests are mandatory. Generate ATDD, BDD, and TDD tasks whenever the feature has stakeholder acceptance, user-visible behavior, implementation logic, edge cases, or expected error sources.

## Mandatory Task Ordering
For each user story, create tasks in this exact sequence:
1. `[ATDD]` Gherkin acceptance scenarios.
2. `[BDD]` Gherkin behavior scenarios.
3. `[ATDD]` and `[BDD]` executable step bindings/support fixtures.
4. `[TDD]` failing unit/component/integration/contract/property/negative tests.
5. `[TDD]`, `[BDD]`, `[ATDD]` red-state execution/report tasks proving tests fail for expected reasons.
6. Production implementation tasks.
7. Refactor tasks.
8. `[GATE]` validation tasks for full test suite, coverage, linting, static analysis, runtime smoke, and traceability.

## Mandatory Task Labels
Use this extended format for all test and gate tasks:

```text
- [ ] T### [P?] [US#?] [TDD|BDD|ATDD|GATE] Description with exact file path
```

`[GATE]` is allowed only for non-product validation tasks and MUST state the protected suite or report path.

The label identifies primary suite ownership. If an artifact supports multiple evidence roles, create one task under its owning-suite label and record the other mappings in the description and traceability matrix. Do not generate equivalent tasks or artifacts solely to satisfy multiple labels.

## Required Per-Story Minimum
Each user story MUST include at least:
- one `[ATDD]` Gherkin feature task;
- one `[BDD]` Gherkin feature task;
- one `[TDD]` happy-path test task;
- one `[TDD]` edge/error/boundary test task;
- red-state run tasks before implementation;
- green-state run tasks after implementation;
- traceability update task.

{CORE_TEMPLATE}

## Additional Completion Report Fields
Include in the task generation completion report:
- Count of `[TDD]`, `[BDD]`, `[ATDD]`, and `[GATE]` tasks
- Confirmation that no implementation task precedes its required tests
- List of Gherkin feature files planned for BDD and ATDD
- List of coverage/lint/static/runtime commands and report paths
