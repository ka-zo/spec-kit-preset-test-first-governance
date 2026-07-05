
---

## Test-First Governance Principles *(mandatory)*

### Principle TF-1: Tests Are Executable Requirements
All implementation work MUST be preceded by executable tests. TDD, BDD, and ATDD are complementary development practices, not mutually exclusive test types. Every executable product-test artifact MUST have exactly one owning suite (`TDD`, `BDD`, or `ATDD`) for directory, task, command, and report routing. An artifact MAY provide evidence for multiple practices, requirements, or acceptance criteria, and the traceability matrix MUST record those relationships. Equivalent tests MUST NOT be duplicated across suites merely to satisfy labels.

### Principle TF-2: ATDD Acceptance Before Implementation
Every user story, acceptance criterion, success criterion that requires buildable behavior, and externally observable edge case MUST have at least one ATDD scenario written in Gherkin syntax before implementation starts. ATDD scenarios define stakeholder-facing acceptance at the feature or release boundary.

### Principle TF-3: BDD Behavior Before Implementation
Every user-visible behavior, business rule, alternate flow, and error flow MUST have at least one BDD Gherkin scenario before implementation starts. BDD scenarios express behavior examples and MUST be mirrored by executable step definitions or equivalent test bindings.

### Principle TF-4: TDD Red-Green-Refactor Discipline
Unit, component, integration, contract, property-based, and negative-path tests MUST be created before the corresponding production code. Each implementation task MUST follow Red → Green → Refactor: write failing tests, implement the smallest change that passes, then refactor while keeping the full suite green.

### Principle TF-5: Gherkin-to-Test Mirroring
Every BDD and ATDD Gherkin scenario MUST have a stable scenario ID tag and an implemented executable test or step binding using the same ID. The suite tag (`@BDD` or `@ATDD`) identifies the scenario's owning suite; it does not prohibit the scenario from supporting additional evidence roles. Scenario tags MUST also include the user story (`@US#`) and relevant requirement or success criterion (`@FR-###`, `@SC-###`, or `@EC-###`).

### Principle TF-6: Quality Gates Are Mandatory
Linting, formatting, static analysis, runtime smoke checks, coverage reporting, and security-sensitive validation MUST be included in the implementation plan and task list. These gates are not a substitute for product tests; they are mandatory guards around the TDD, BDD, and ATDD suites.

### Principle TF-7: Traceability Is Non-Negotiable
Every Functional Requirement, Success Criterion requiring buildable work, User Story, Edge Case, and externally visible error condition MUST map to at least one test artifact. Missing traceability is a blocking issue and MUST be resolved before implementation proceeds.
