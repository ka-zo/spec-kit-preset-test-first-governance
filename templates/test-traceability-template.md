# Test Traceability Matrix: [FEATURE NAME]

**Feature**: [link to spec.md]  
**Plan**: [link to plan.md]  
**Created**: [DATE]

**Last Updated**: [DATE]

## Coverage Matrix

| Source ID | Source Type | Owning Suite | Evidence Role(s) | Test/Scenario ID | Artifact Path | Execution Command | Status | Evidence Path | Notes |
|-----------|-------------|--------------|------------------|------------------|---------------|-------------------|--------|---------------|-------|
| FR-001 | Functional Requirement | TDD | TDD | TDD-US1-001 | tests/tdd/unit/test_[name].[ext] | [command] | Planned | [task/PR/CI/report link] | [notes] |
| US1 | User Story | ATDD | ATDD, BDD | ATDD-US1-001 | tests/atdd/features/acceptance/[feature].feature | [command] | Planned | [task/PR/CI/report link] | [shared acceptance/behavior evidence] |

## BDD and ATDD Applicability

| User Story | Practice | Decision | Scenario Evidence ID(s) | N/A Rationale | Alternative Evidence |
|------------|----------|----------|-------------------------|---------------|----------------------|
| US1 | BDD | Required | ATDD-US1-001 |  |  |
| US1 | ATDD | Required | ATDD-US1-001 |  |  |

## Status Vocabulary

- `Planned`: artifact and command are defined but not yet executed.
- `Red`: the test failed for the intended missing behavior before implementation.
- `Green`: the test or gate passed against the current implementation.
- `Blocked`: execution cannot proceed; explain the blocker in Notes.
- `N/A`: an approved applicability decision with rationale and alternative evidence.

## Required Checks

- [ ] Core identifiers are reused wherever available (`US1`, `FR-001`, `SC-001`, and `T###`)
- [ ] New identifiers exist only where core has no equivalent (`EC-001` and suite-owned executable IDs)
- [ ] Test, scenario, binding, task, and Gherkin IDs match verbatim across artifacts
- [ ] Every FR has at least one mapped test artifact
- [ ] Every user story records BDD and ATDD as `Required` or justified `N/A`
- [ ] Every `Required` BDD/ATDD decision maps to scenario evidence carrying that role, regardless of owning suite
- [ ] Every `N/A` decision has a concrete rationale and alternative evidence
- [ ] Every edge/error case has a mapped negative, BDD, or ATDD test
- [ ] Every Gherkin scenario has an executable binding
- [ ] Every executable artifact has exactly one owning suite
- [ ] Multi-role evidence is mapped without duplicating equivalent artifacts
- [ ] Status and evidence fields match the latest task and execution results
