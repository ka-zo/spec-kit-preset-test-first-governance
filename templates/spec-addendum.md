
---

## Test-First Specification Addendum *(mandatory)*

### Test Classification Matrix
For every User Story, Functional Requirement, Success Criterion requiring buildable work, Edge Case, and Error Condition, define the required test coverage before planning.

| Source ID | Source Type | Description | Required Suite | Test Intent | Gherkin Required? | Notes |
|-----------|-------------|-------------|----------------|-------------|-------------------|-------|
| US-001 | User Story | [story summary] | ATDD, BDD, TDD | [acceptance + behavior + implementation verification] | Yes for ATDD/BDD | [notes] |
| FR-001 | Functional Requirement | [requirement summary] | [TDD/BDD/ATDD] | [what proves it works] | [Yes/No] | [notes] |
| EC-001 | Edge Case | [edge/error condition] | [TDD/BDD/ATDD] | [what proves safe handling] | [Yes/No] | [notes] |

Rules:
- Product tests MUST be explicitly classified as `TDD`, `BDD`, or `ATDD`.
- BDD and ATDD entries MUST use Gherkin syntax and MUST have stable scenario IDs.
- TDD entries MUST cover happy paths, boundary values, invalid inputs, state transitions, integration contracts, and expected error sources.
- At least one negative-path test MUST exist for every requirement with validation, permissions, input parsing, persistence, external I/O, concurrency, or failure modes.

### ATDD Acceptance Scenarios *(Gherkin, mandatory)*
Create stakeholder-facing acceptance scenarios under `tests/atdd/features/`.

```gherkin
@ATDD @US1 @FR-001 @SC-001 @ATDD-US1-001
Feature: [Feature capability]
  Scenario: [Stakeholder-visible acceptance outcome]
    Given [initial business state]
    When [stakeholder action or system trigger]
    Then [observable acceptance result]
    And [measurable success or invariant]
```

### BDD Behavior Scenarios *(Gherkin, mandatory)*
Create behavior examples under `tests/bdd/features/`.

```gherkin
@BDD @US1 @FR-001 @BDD-US1-001
Feature: [User behavior or business rule]
  Scenario: [Concrete behavior example]
    Given [context]
    When [behavior occurs]
    Then [expected behavior]
```

### TDD Test Inventory *(mandatory)*
Define the implementation-level tests required before code is written.

| Test ID | Source ID(s) | Test Level | Path | Intent | Expected Initial Failure |
|---------|--------------|------------|------|--------|--------------------------|
| TDD-US1-001 | FR-001, US1 | Unit | tests/tdd/unit/test_[name].[ext] | [what it verifies] | [missing implementation / failing assertion] |
| TDD-US1-002 | EC-001 | Negative/Boundary | tests/tdd/unit/test_[name].[ext] | [edge/error handling] | [missing validation / wrong error] |

### Test Traceability Requirements
Before `/speckit.plan` is considered complete:
- Every `FR-###` MUST have at least one `TDD`, `BDD`, or `ATDD` test mapping.
- Every user story MUST have at least one ATDD scenario and one BDD scenario.
- Every Gherkin scenario MUST include suite, user story, and requirement tags.
- All expected error sources, edge cases, and boundary conditions MUST be represented in the matrix.
