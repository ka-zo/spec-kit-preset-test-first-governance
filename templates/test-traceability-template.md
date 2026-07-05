# Test Traceability Matrix: [FEATURE NAME]

**Feature**: [link to spec.md]  
**Plan**: [link to plan.md]  
**Created**: [DATE]

## Coverage Matrix

| Source ID | Source Type | Owning Suite | Evidence Role(s) | Test/Scenario ID | Artifact Path | Execution Command | Status | Notes |
|-----------|-------------|--------------|------------------|------------------|---------------|-------------------|--------|-------|
| FR-001 | Functional Requirement | TDD | TDD | TDD-US1-001 | tests/tdd/unit/test_[name].[ext] | [command] | Planned | [notes] |
| US1 | User Story | BDD | BDD | BDD-US1-001 | tests/bdd/features/user-stories/[feature].feature | [command] | Planned | [notes] |
| US1 | User Story | ATDD | ATDD, BDD | ATDD-US1-001 | tests/atdd/features/acceptance/[feature].feature | [command] | Planned | [shared acceptance/behavior evidence] |

## BDD and ATDD Applicability

| User Story | Practice | Decision | N/A Rationale | Alternative Evidence |
|------------|----------|----------|---------------|----------------------|
| US1 | BDD | [Required/N/A] | [concrete rationale when N/A] | [TDD/gate artifact IDs] |
| US1 | ATDD | [Required/N/A] | [concrete rationale when N/A] | [TDD/gate artifact IDs] |

## Required Checks

- [ ] Every FR has at least one mapped test artifact
- [ ] Every user story records BDD and ATDD as `Required` or justified `N/A`
- [ ] Every `Required` BDD/ATDD decision has scenario coverage
- [ ] Every `N/A` decision has a concrete rationale and alternative evidence
- [ ] Every edge/error case has a mapped negative, BDD, or ATDD test
- [ ] Every Gherkin scenario has an executable binding
- [ ] Every executable artifact has exactly one owning suite
- [ ] Multi-role evidence is mapped without duplicating equivalent artifacts
