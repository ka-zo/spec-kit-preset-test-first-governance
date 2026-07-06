
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
└── [reports/]  # only when versioned report retention is required
    ├── tdd/
    ├── bdd/
    └── atdd/
```

If the repository uses a platform-specific convention, keep the platform convention but preserve visible `tdd`, `bdd`, and `atdd` ownership when those suites produce artifacts. Do not create empty BDD or ATDD directories when the practice is entirely `N/A`. Create a reports directory only when the evidence-retention policy requires versioned local reports.

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

### Test Tooling and Gate Decisions
| Suite/Gate | Applicability | Tool and Required Command | Threshold | Evidence Retention | Rationale |
|------------|---------------|---------------------------|-----------|--------------------|-----------|
| TDD | Required | [runner + command] | all planned tests pass | [CI output/artifact] | production logic |
| BDD | [Required/N/A] | [runner + command or N/A] | all planned scenarios pass | [CI output/artifact] | [decision] |
| ATDD | [Required/N/A] | [runner + command or N/A] | all planned scenarios pass | [CI output/artifact] | [decision] |
| Coverage | Required | [tool + command] | [line/branch thresholds] | [CI artifact] | changed production code |
| Lint/Format | Required | [tools + commands] | zero blocking findings | [CI output] | source consistency |
| Static Analysis | [Required/N/A] | [tool + command or N/A] | [severity policy] | [CI output/artifact] | [stack/risk rationale] |
| Security | [Required/N/A] | [tool + command or N/A] | [severity policy] | [CI artifact] | [threat-surface rationale] |
| Runtime Smoke | [Required/N/A] | [runner + command or N/A] | all declared checks pass | [CI artifact] | [runnable-artifact rationale] |

### Risk-Based Threshold Policy
The plan MUST declare coverage thresholds based on change scope, risk, and the existing project baseline:
- Recommended starting guardrails for changed production code are **90% line** and **85% branch** coverage; they are not universal constants.
- Coverage MUST NOT regress below the accepted project baseline.
- Lower thresholds require a scoped exception with rationale, compensating evidence, approver, and expiry or follow-up task.
- BDD scenario execution: **100% of planned BDD scenarios pass**.
- ATDD scenario execution: **100% of planned ATDD scenarios pass**.
- Lint/format: **0 blocking findings**.
- Required static analysis/type checking: **0 blocking findings** under the declared severity policy.
- Required runtime smoke: **all declared smoke checks pass**.
- Security-sensitive code paths: include negative tests for authentication, authorization, validation, injection, path traversal, secrets handling, and persistence failures where applicable.

### Evidence Retention
The authoritative evidence is the exact command, exit status, and reproducible output referenced by `specs/<feature>/test-traceability.md`. Store machine-readable reports as CI artifacts by default. Commit generated reports only when an explicit audit or regulatory retention policy requires versioned evidence.

### Red-Green-Refactor Execution Model
For each user story:
1. Write required ATDD Gherkin scenarios and expected failing bindings.
2. Write required BDD Gherkin scenarios and expected failing bindings.
3. Write TDD tests covering units, boundaries, error paths, contracts, and integration seams.
4. Run the relevant suites and record expected failures.
5. Implement the smallest production code needed to pass.
6. Refactor with TDD and all required BDD and ATDD suites still green.
7. Run coverage, linting, formatting, and every gate marked `Required`.
