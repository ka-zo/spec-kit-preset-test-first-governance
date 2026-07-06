
---

## Test-First Architecture & Quality Plan *(mandatory)*

### Test Suite Directory Structure
The selected project structure MUST expose clear ownership for all test artifacts.

```text
tests/
├── tdd/
│   ├── unit/
│   ├── component/
│   ├── integration/
│   ├── contract/
│   ├── property/
│   ├── negative/
│   └── fixtures/
├── bdd/
│   ├── features/
│   │   ├── user-stories/
│   │   ├── business-rules/
│   │   └── edge-cases/
│   ├── steps/
│   └── support/
├── atdd/
│   ├── features/
│   │   ├── acceptance/
│   │   └── regression/
│   ├── steps/
│   └── support/
├── support/
│   ├── fixtures/
│   ├── helpers/
│   └── runner-adapters/
└── reports/
    ├── tdd/
    ├── bdd/
    └── atdd/
```

If the repository uses a platform-specific convention, keep the platform convention but preserve the same semantic split: `tdd`, `bdd`, `atdd`, and `reports` MUST be visible when those suites produce artifacts. Do not create empty BDD or ATDD directories when the practice is entirely `N/A`.

Suite directories identify primary ownership, not mutually exclusive test types. Shared fixtures, helpers, environment setup, and runner adapters MUST live under `tests/support/` or an equivalent shared path unless they are genuinely suite-specific. The plan MUST identify and remove equivalent scenarios or tests duplicated only to satisfy multiple practice labels.

### BDD and ATDD Applicability
For every user story, carry forward the specification's BDD and ATDD decisions:

| User Story | BDD | ATDD | N/A Rationale | Alternative Evidence |
|------------|-----|------|---------------|----------------------|
| US-001 | [Required/N/A] | [Required/N/A] | [concrete rationale when applicable] | [TDD/gate artifact IDs] |

The plan MUST NOT turn an approved `N/A` into ceremonial scenarios. If planning reveals observable behavior or a stakeholder acceptance boundary, change the decision to `Required` and update the specification.

### Traceability Materialization
Before planning completes:
1. Resolve the template named `test-traceability-template` through Spec Kit's template resolver.
2. Create `specs/<feature>/test-traceability.md` from the resolved content.
3. Populate every known FR/SC/US/EC, BDD/ATDD applicability decision, planned artifact ID, owning suite, path, and execution command.
4. Use `Planned` for evidence not yet executed; do not invent Red/Green results during planning.

If the file already exists, update it in place and preserve valid execution history.

### Test Tooling Decisions
| Suite/Gate | Tool | Scope | Required Command | Output Path | Blocking? |
|------------|------|-------|------------------|-------------|-----------|
| TDD | [unit test runner] | unit/component/integration/contract/property/negative | `[command]` | tests/reports/tdd/ | Yes |
| BDD | [Gherkin/Cucumber-compatible runner] | required behavior scenarios and step bindings | `[command or N/A]` | tests/reports/bdd/ | When required |
| ATDD | [acceptance/e2e runner] | required stakeholder acceptance scenarios | `[command or N/A]` | tests/reports/atdd/ | When required |
| Coverage | [coverage tool] | suite coverage | `[command]` | tests/reports/tdd/coverage/ | Yes |
| Lint/Format | [linter/formatter] | source + tests | `[command]` | tests/reports/tdd/lint/ | Yes |
| Static Analysis | [type checker/SAST/static analyzer] | source + tests | `[command]` | tests/reports/tdd/static/ | Yes |
| Runtime Smoke | [smoke runner] | deployed/runnable artifact | `[command]` | tests/reports/atdd/runtime/ | Yes |

### Minimum Quality Thresholds
Unless the project constitution or user specifies stricter values, use these minimum gates:
- TDD line coverage: **90%** for changed production code.
- TDD branch coverage: **85%** for changed production code.
- BDD scenario execution: **100% of planned BDD scenarios pass**.
- ATDD scenario execution: **100% of planned ATDD scenarios pass**.
- Lint/format: **0 blocking findings**.
- Static analysis/type checking: **0 blocking findings**.
- Runtime smoke: **all declared smoke checks pass**.
- Security-sensitive code paths: include negative tests for authentication, authorization, validation, injection, path traversal, secrets handling, and persistence failures where applicable.

### Red-Green-Refactor Execution Model
For each user story:
1. Write required ATDD Gherkin scenarios and expected failing bindings.
2. Write required BDD Gherkin scenarios and expected failing bindings.
3. Write TDD tests covering units, boundaries, error paths, contracts, and integration seams.
4. Run the relevant suites and record expected failures.
5. Implement the smallest production code needed to pass.
6. Refactor with TDD and all required BDD and ATDD suites still green.
7. Run coverage, linting, static analysis, and runtime smoke gates.
