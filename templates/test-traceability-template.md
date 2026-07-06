# Test Traceability: [FEATURE NAME]

**Feature**: [link to spec.md]  
**Plan**: [link to plan.md]  
**Created**: [DATE]

**Last Updated**: [DATE]

## Evidence Artifact Registry

| Artifact ID | Owning Suite | Evidence Role(s) | Artifact Path | Execution Command | Status | Evidence Path | Notes |
|-------------|--------------|------------------|---------------|-------------------|--------|---------------|-------|
| TDD-US1-001 | TDD | TDD | tests/tdd/unit/test_[name].[ext] | [command] | Planned | [task/PR/CI/report link] | [notes] |
| ATDD-US1-001 | ATDD | ATDD, BDD | tests/atdd/features/acceptance/[feature].feature | [command] | Planned | [task/PR/CI/report link] | [shared acceptance/behavior evidence] |

## Source Coverage Map

| Source ID | Source Type | Artifact ID(s) | Coverage Intent | Notes |
|-----------|-------------|----------------|-----------------|-------|
| FR-001 | Functional Requirement | TDD-US1-001, ATDD-US1-001 | [implementation and acceptance behavior] | [notes] |
| US1 | User Story | ATDD-US1-001 | [stakeholder outcome and user-visible behavior] | [notes] |

## BDD and ATDD Applicability

| User Story | Practice | Decision | Scenario Evidence ID(s) | N/A Rationale | Alternative Evidence |
|------------|----------|----------|-------------------------|---------------|----------------------|
| US1 | BDD | Required | ATDD-US1-001 |  |  |
| US1 | ATDD | Required | ATDD-US1-001 |  |  |

## Quality Gate Results

| Gate | Applicability | Execution Command | Threshold / Policy | Status | Evidence Path | Notes |
|------|---------------|-------------------|--------------------|--------|---------------|-------|
| Coverage | Required | [command] | [line/branch thresholds and baseline] | Planned | [CI/report link] | [notes] |
| Runtime Smoke | [Required/N/A] | [command or N/A] | [pass policy or N/A rationale] | [Planned/N/A] | [CI/report link or N/A] | [notes] |

## Status Vocabulary

- `Planned`: an artifact or required gate and its command are defined but not yet executed.
- `Red`: the test failed for the intended missing behavior before implementation.
- `Green`: the artifact or gate passed against the current implementation.
- `Blocked`: execution cannot proceed; explain the blocker in Notes.
- `N/A`: an approved practice or gate applicability decision with its required rationale.

## Required Checks

- [ ] Core identifiers are reused wherever available (`US1`, `FR-001`, `SC-001`, and `T###`)
- [ ] New identifiers exist only where core has no equivalent (`EC-001` and suite-owned executable IDs)
- [ ] Test, scenario, binding, task, and Gherkin IDs match verbatim across artifacts
- [ ] Every executable artifact appears exactly once in the Evidence Artifact Registry
- [ ] Every source-to-artifact relationship appears in the Source Coverage Map
- [ ] Every artifact ID in the Source Coverage Map and every scenario evidence ID in the applicability table exists in the registry
- [ ] Every FR has at least one mapped test artifact
- [ ] Every user story records BDD and ATDD as `Required` or justified `N/A`
- [ ] Every `Required` BDD/ATDD decision maps to scenario evidence carrying that role, regardless of owning suite
- [ ] Every `N/A` decision has a concrete rationale and alternative evidence
- [ ] Every edge/error case has a mapped negative, BDD, or ATDD test
- [ ] Every Gherkin scenario has an executable binding
- [ ] Every executable artifact has exactly one owning suite
- [ ] Multi-role evidence is mapped without duplicating equivalent artifacts
- [ ] Within this traceability artifact, artifact commands, statuses, and evidence exist only in the registry and match the latest execution results
- [ ] Within this traceability artifact, gate commands, policies, statuses, and evidence exist only in Quality Gate Results and match the latest execution results
- [ ] Source Coverage Map rows do not duplicate mutable execution status or evidence
