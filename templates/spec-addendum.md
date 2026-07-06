
---

## Test-First Specification Addendum *(mandatory)*

### Test Classification and Applicability Matrix
For every User Story, Functional Requirement, Success Criterion requiring buildable work, Edge Case, and Error Condition, define the required test coverage before planning.

| Source ID | Source Type | Description | TDD | BDD | ATDD | Test Intent / N/A Rationale |
|-----------|-------------|-------------|-----|-----|------|-----------------------------|
| US1 | User Story | [story summary] | Required | [Required/N/A] | [Required/N/A] | [evidence intent or concrete N/A rationale] |
| FR-001 | Functional Requirement | [requirement summary] | Required | [Required/N/A] | [Required/N/A] | [what proves it works or why a practice does not apply] |
| EC-001 | Edge Case | [edge/error condition] | Required | [Required/N/A] | [Required/N/A] | [what proves safe handling or why a practice does not apply] |

Rules:
- Reuse core story identifiers such as `US1`; do not introduce a parallel alias.
- Each executable test artifact MUST declare exactly one owning suite: `TDD`, `BDD`, or `ATDD`.
- Required evidence MAY name multiple practices, and one artifact MAY support multiple evidence roles or source IDs.
- A `Required` BDD or ATDD decision MUST map to scenario evidence for that role, but it does not require a separately owned artifact.
- One scenario MAY satisfy both BDD and ATDD when it fully covers both intents; record both roles and one owning suite in traceability.
- Do not create equivalent copies of an artifact solely to place it in more than one suite.
- TDD is required for production logic.
- BDD is required for user-visible behavior, business rules, alternate flows, and observable error behavior.
- ATDD is required for stakeholder-facing acceptance criteria and release boundaries.
- BDD or ATDD MAY be `N/A` only for technical-only work lacking the corresponding behavior or acceptance boundary. Every `N/A` MUST state a concrete rationale and alternative TDD or quality-gate evidence.
- Required BDD and ATDD entries MUST use Gherkin syntax and MUST have stable scenario IDs.
- TDD entries MUST cover happy paths, boundary values, invalid inputs, state transitions, integration contracts, and expected error sources.
- At least one negative-path test MUST exist for every requirement with validation, permissions, input parsing, persistence, external I/O, concurrency, or failure modes.

### ATDD Acceptance Evidence *(Gherkin, mandatory when ATDD is Required)*
Create an ATDD-owned stakeholder-facing scenario under `tests/atdd/features/` when distinct acceptance evidence is needed. A scenario owned by BDD MAY instead satisfy the ATDD role when it fully proves the same stakeholder-facing outcome and traceability records both roles.

```gherkin
@ATDD @US1 @FR-001 @SC-001
Feature: [Feature capability]
  @ATDD-US1-001
  Scenario: [Stakeholder-visible acceptance outcome]
    Given [initial business state]
    When [stakeholder action or system trigger]
    Then [observable acceptance result]
    And [measurable success or invariant]
```

### BDD Behavior Evidence *(Gherkin, mandatory when BDD is Required)*
Create a BDD-owned behavior example under `tests/bdd/features/` when distinct behavior evidence is needed. A scenario owned by ATDD MAY instead satisfy the BDD role when it fully proves the same user-visible behavior or business rule and traceability records both roles.

```gherkin
@BDD @US1 @FR-001
Feature: [User behavior or business rule]
  @BDD-US1-001
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

### Specification Traceability Inputs
Before specification is considered complete:
- Every `FR-###` MUST have at least one `TDD`, `BDD`, or `ATDD` test mapping.
- Every user story MUST record a `Required` or justified `N/A` decision for BDD and ATDD.
- Every `Required` decision MUST map to at least one scenario carrying the corresponding evidence role; the scenario MAY be owned by another suite.
- Every Gherkin scenario MUST have suite, user story, and requirement tags directly or by feature-level inheritance.
- Every scenario-specific ID tag MUST appear immediately above exactly one `Scenario` or `Scenario Outline`, never at feature level.
- All expected error sources, edge cases, and boundary conditions MUST have planned evidence.
- Every executable artifact MUST have one owning suite, with all additional evidence roles represented through traceability rather than duplicated tests.
