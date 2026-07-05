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

## Required Checks

- [ ] Every FR has at least one mapped test artifact
- [ ] Every user story has BDD and ATDD scenario coverage
- [ ] Every edge/error case has a mapped negative, BDD, or ATDD test
- [ ] Every Gherkin scenario has an executable binding
- [ ] Every executable artifact has exactly one owning suite
- [ ] Multi-role evidence is mapped without duplicating equivalent artifacts
