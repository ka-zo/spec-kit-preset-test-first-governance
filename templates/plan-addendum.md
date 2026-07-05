
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
└── reports/
    ├── tdd/
    ├── bdd/
    └── atdd/
```

If the repository uses a platform-specific convention, keep the platform convention but preserve the same semantic split: `tdd`, `bdd`, `atdd`, and `reports` MUST be visible in directory names.

### Test Tooling Decisions
| Suite/Gate | Tool | Scope | Required Command | Output Path | Blocking? |
|------------|------|-------|------------------|-------------|-----------|
| TDD | [unit test runner] | unit/component/integration/contract/property/negative | `[command]` | tests/reports/tdd/ | Yes |
| BDD | [Gherkin/Cucumber-compatible runner] | behavior scenarios and step bindings | `[command]` | tests/reports/bdd/ | Yes |
| ATDD | [acceptance/e2e runner] | stakeholder acceptance scenarios | `[command]` | tests/reports/atdd/ | Yes |
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
1. Write ATDD Gherkin scenarios and expected failing bindings.
2. Write BDD Gherkin scenarios and expected failing bindings.
3. Write TDD tests covering units, boundaries, error paths, contracts, and integration seams.
4. Run the relevant suites and record expected failures.
5. Implement the smallest production code needed to pass.
6. Refactor with all TDD, BDD, and ATDD suites still green.
7. Run coverage, linting, static analysis, and runtime smoke gates.
