
---

## Test-First Governance Principles *(mandatory)*

### Principle TF-1: Tests Are Executable Requirements
All implementation work MUST be preceded by executable tests. Product test cases MUST be explicitly classified as exactly one of: `TDD`, `BDD`, or `ATDD`. No product test case may be unclassified, ambiguously classified, or stored outside the declared suite directory.

### Principle TF-2: ATDD Acceptance Before Implementation
Every user story, acceptance criterion, success criterion that requires buildable behavior, and externally observable edge case MUST have at least one ATDD scenario written in Gherkin syntax before implementation starts. ATDD scenarios define stakeholder-facing acceptance at the feature or release boundary.

### Principle TF-3: BDD Behavior Before Implementation
Every user-visible behavior, business rule, alternate flow, and error flow MUST have at least one BDD Gherkin scenario before implementation starts. BDD scenarios express behavior examples and MUST be mirrored by executable step definitions or equivalent test bindings.

### Principle TF-4: TDD Red-Green-Refactor Discipline
Unit, component, integration, contract, property-based, and negative-path tests MUST be created before the corresponding production code. Each implementation task MUST follow Red → Green → Refactor: write failing tests, implement the smallest change that passes, then refactor while keeping the full suite green.

### Principle TF-5: Gherkin-to-Test Mirroring
Every BDD and ATDD Gherkin scenario MUST have a stable scenario ID tag and an implemented executable test or step binding using the same ID. Scenario tags MUST include the suite (`@BDD` or `@ATDD`), user story (`@US#`), and relevant requirement or success criterion (`@FR-###`, `@SC-###`, or `@EC-###`).

### Principle TF-6: Quality Gates Are Mandatory
Linting, formatting, static analysis, runtime smoke checks, coverage reporting, and security-sensitive validation MUST be included in the implementation plan and task list. These gates are not a substitute for product tests; they are mandatory guards around the TDD, BDD, and ATDD suites.

### Principle TF-7: Traceability Is Non-Negotiable
Every Functional Requirement, Success Criterion requiring buildable work, User Story, Edge Case, and externally visible error condition MUST map to at least one test artifact. Missing traceability is a blocking issue and MUST be resolved before implementation proceeds.
