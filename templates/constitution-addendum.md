
---

## Test-First Governance Principles *(mandatory)*

### Principle TF-1: Tests Are Executable Requirements
All implementation work MUST be preceded by executable tests. TDD, BDD, and ATDD are complementary development practices, not mutually exclusive test types. Every executable product-test artifact MUST have exactly one owning suite (`TDD`, `BDD`, or `ATDD`) for directory, task, command, and report routing. An artifact MAY provide evidence for multiple practices, requirements, or acceptance criteria, and the traceability matrix MUST record those relationships. Equivalent tests MUST NOT be duplicated across suites merely to satisfy labels.

### Principle TF-2: ATDD Acceptance Before Implementation
Every stakeholder-facing acceptance criterion, release boundary, and externally observable success criterion MUST have ATDD scenarios written in Gherkin syntax before implementation starts. Each user story MUST mark ATDD as `Required` or `N/A`. `N/A` is allowed only for technical-only work with no stakeholder-facing acceptance boundary and MUST include a concrete rationale plus alternative TDD or quality-gate evidence.

### Principle TF-3: BDD Behavior Before Implementation
Every user-visible behavior, business rule, alternate flow, and observable error flow MUST have BDD Gherkin scenarios before implementation starts. Each user story MUST mark BDD as `Required` or `N/A`. `N/A` is allowed only for technical-only work with no observable behavior or business rule and MUST include a concrete rationale plus alternative TDD or quality-gate evidence. BDD scenarios MUST be mirrored by executable step definitions or equivalent test bindings.

### Principle TF-4: TDD Red-Green-Refactor Discipline
Unit, component, integration, contract, property-based, and negative-path tests MUST be created before the corresponding production code. Each implementation task MUST follow Red → Green → Refactor: write failing tests, implement the smallest change that passes, then refactor while keeping the full suite green.

### Principle TF-5: Gherkin-to-Test Mirroring
Identifiers defined by core Spec Kit MUST be reused: `User Story 1` / `US1` / `[US1]`, `FR-001`, `SC-001`, and `T###`. This preset adds `EC-001` because core Edge Cases have no stable identifier, and adds suite-owned executable IDs such as `TDD-US1-001`, `BDD-US1-001`, and `ATDD-US1-001`. Identifiers are stable and MUST NOT be renumbered or reused after publication.

Every BDD and ATDD Gherkin scenario MUST have a stable scenario ID tag and an implemented executable test or step binding using the same ID. The suite tag (`@BDD` or `@ATDD`) identifies the scenario's owning suite; it does not prohibit the scenario from supporting additional evidence roles. Scenario tags MUST also include the core user-story tag (`@US1`) and relevant requirement or success-criterion tags (`@FR-001`, `@SC-001`, or `@EC-001`).

### Principle TF-6: Quality Gates Are Mandatory
The plan MUST declare applicability, commands, thresholds, blocking behavior, and evidence retention for coverage, linting, formatting, static analysis/type checking, security validation, and runtime smoke checks. Coverage is mandatory for changed production code. Other gates are mandatory when applicable to the selected stack or risk surface; `N/A` requires a concrete technical rationale. Threshold exceptions MUST be scoped, approved, and backed by compensating evidence.

Quality gates are guards around TDD and every required BDD/ATDD suite, not substitutes for product tests. Reproducible command output and CI artifacts are preferred over committed per-story reports unless audit or regulatory requirements demand versioned evidence.

### Principle TF-7: Traceability Is Non-Negotiable
Every feature MUST maintain `specs/<feature>/test-traceability.md` as its canonical requirement-to-test matrix. Every Functional Requirement, Success Criterion requiring buildable work, User Story, Edge Case, and externally visible error condition MUST map to planned evidence before implementation and to execution evidence before completion. Planning creates the matrix from the resolved `test-traceability-template`; task generation and implementation keep it current. A missing or stale matrix is a blocking issue.
