# Test-First Tasks Wrapper

Apply these requirements in addition to the core task-generation workflow.

## Critical Override: Tests Are Not Optional
If the core command or template says tests are optional, replace that rule with this preset rule: tests are mandatory. Generate TDD tasks for production logic. Generate the minimum non-duplicative scenario tasks needed to cover all `Required` ATDD and BDD evidence roles; preserve justified `N/A` decisions and report missing or contradictory rationales as blocking gaps.

## Mandatory Incremental Task Ordering
For each user story:
1. Create the minimum non-duplicative set of scenario specifications covering all required ATDD acceptance and BDD behavior evidence roles before production implementation begins.
2. Add a `[GATE]` task that records planned artifact IDs, paths, commands, and behavior slices in `specs/<feature>/test-traceability.md`.
3. Divide implementation into the smallest meaningful behavior slices that can be independently verified.
4. For each slice, generate one ordered Red-Green-Refactor cycle:
   1. `[ATDD]`, `[BDD]`, and/or `[TDD]` tasks add only the executable bindings and tests needed for that slice.
   2. Suite execution tasks prove the new evidence fails for the intended missing behavior and update its matrix status to `Red`.
   3. Production implementation tasks make the smallest change needed to pass that evidence.
   4. Suite execution tasks confirm the slice is `Green` and update its matrix evidence.
   5. Refactor tasks improve the design and rerun the relevant evidence while it remains green.
5. Repeat the cycle for the next slice. Do not accumulate every failing test for the story before beginning production implementation.
6. After all slices are green, add `[GATE]` validation tasks for the full test suite, coverage, linting, formatting, and every gate marked `Required`.
7. Finish with a `[GATE]` task that records final `Green`, `Blocked`, or approved `N/A` results and performs the story-level traceability review.

## Core-Compatible Suite Markers
Preserve the core task format and place the suite marker as the first token of the description for test and gate tasks:

```text
- [ ] T### [P?] [US#?] [TDD|BDD|ATDD|GATE] Description with exact file path
```

`[TDD]`, `[BDD]`, `[ATDD]`, and `[GATE]` do not replace or alter core `T###`, `[P]`, or `[US1]` identifiers. `[GATE]` is allowed only for non-product validation tasks and MUST state the protected suite or evidence destination.

The label identifies primary suite ownership. If an artifact supports multiple evidence roles, create one task under its owning-suite label and record the other mappings in the description and traceability matrix. Do not generate equivalent tasks or artifacts solely to satisfy multiple labels.

Preserve core Spec Kit story labels such as `[US1]`, `[US2]`, and `[US3]`. Use the same story identifier in suite-owned artifact IDs such as `TDD-US1-001`, `BDD-US1-001`, and `ATDD-US1-001`. Do not introduce a parallel `US-001` alias.

## Required Per-Story Minimum
Each user story MUST include at least:
- scenario tasks covering every `Required` BDD and ATDD evidence role; one owning-suite task MAY cover both roles;
- one `[TDD]` happy-path test task;
- one `[TDD]` edge/error/boundary test task;
- a red-state run before the production change for each behavior slice, with evidence retained in task/PR/CI output or an audit-required report;
- a green-state run immediately after the corresponding minimal production change;
- a `[GATE]` task updating `specs/<feature>/test-traceability.md` before implementation and after execution.

{CORE_TEMPLATE}

## Additional Completion Report Fields
Include in the task generation completion report:
- Count of `[TDD]`, `[BDD]`, `[ATDD]`, and `[GATE]` tasks
- Confirmation that no implementation task precedes its required tests
- List of Gherkin feature files, their owning suites, and their BDD/ATDD evidence roles
- List of BDD/ATDD `N/A` decisions with rationale and alternative evidence
- List of gate applicability decisions, commands, thresholds, and evidence destinations
- Confirmation that traceability creation and update tasks use `specs/<feature>/test-traceability.md`
- Confirmation that task-story labels and suite-owned artifact IDs reuse the same core story identifier
