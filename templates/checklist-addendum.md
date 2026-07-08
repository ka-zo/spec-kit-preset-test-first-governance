
---

## Test-First Quality Checklist Addendum *(mandatory)*

### TDD Completeness
- [ ] Every implementation unit has a failing test before production code is written
- [ ] Happy paths, edge cases, invalid inputs, boundary values, and expected error sources are covered
- [ ] The TDD inventory has enough distinct test cases for complete implementation-level coverage, not just a happy-path/error-path minimum
- [ ] Contract/integration seams have tests before dependent implementation is added
- [ ] TDD tests are stored under a clearly visible `tests/tdd/` directory or equivalent platform-specific path

### BDD Completeness
- [ ] Every user story marks BDD as `Required` or provides a concrete `N/A` rationale and alternative evidence
- [ ] Every user-visible behavior and business rule maps to Gherkin scenario evidence carrying the BDD role
- [ ] BDD scenarios cover each supported user-facing option or equivalence class
- [ ] Each observable edge/error condition has a dedicated negative or boundary BDD scenario or scenario-outline example
- [ ] Every BDD scenario has tags for suite, user story, and requirement IDs
- [ ] Every BDD scenario has an implemented step binding or equivalent executable mapping
- [ ] BDD feature files and step definitions are stored under `tests/bdd/` or equivalent platform-specific path

### ATDD Completeness
- [ ] Every user story marks ATDD as `Required` or provides a concrete `N/A` rationale and alternative evidence
- [ ] Every stakeholder-facing acceptance criterion maps to Gherkin scenario evidence carrying the ATDD role
- [ ] Each buildable success criterion has ATDD scenario evidence or an approved `N/A`
- [ ] Required externally visible option combinations have full coverage or justified pairwise/risk-based sampling
- [ ] Every ATDD scenario has an implemented acceptance binding or equivalent executable mapping
- [ ] ATDD feature files and step definitions are stored under `tests/atdd/` or equivalent platform-specific path

### Quality Gates
- [ ] Coverage thresholds are risk-based, approved, enforced, and prevent baseline regression
- [ ] Linting/formatting is configured and blocking
- [ ] Static analysis, security validation, and runtime smoke are `Required` or have a concrete `N/A` rationale
- [ ] Every required gate is blocking and has reproducible commands
- [ ] Threshold exceptions are scoped, approved, compensated, and time-bounded or tracked
- [ ] Evidence retention uses CI output/artifacts by default; committed reports have an explicit audit rationale

### Traceability
- [ ] `specs/<feature>/test-traceability.md` exists and was created from `test-traceability-template`
- [ ] Core identifiers are reused: `User Story 1` / `US1` / `[US1]`, `FR-001`, `SC-001`, and `T###`
- [ ] `EC-001` is introduced only where an edge case needs traceability
- [ ] Test/scenario IDs use minimal `<SUITE>-US1-001` forms
- [ ] Gherkin tags, executable bindings, and traceability rows reuse identifiers verbatim
- [ ] Every scenario-specific ID tag appears immediately above exactly one `Scenario` or `Scenario Outline`, not above `Feature`
- [ ] Published IDs have not been shortened, renumbered, or reused
- [ ] Every FR/SC/US/EC maps to one or more TDD, BDD, or ATDD artifacts
- [ ] The Scenario Coverage Matrix contains scenario/example rows for every required BDD/ATDD behavior, acceptance boundary, edge/error condition, and required example class
- [ ] Scenario outlines enumerate required examples or record an approved sampling strategy
- [ ] Broad umbrella scenarios are not the only evidence for unrelated FRs, SCs, ECs, inputs, interfaces, outcomes, or error messages
- [ ] Every Gherkin scenario ID maps to an executable test or step binding
- [ ] Every executable product-test artifact has exactly one owning suite
- [ ] Additional evidence roles are represented in traceability rather than duplicate tests
- [ ] A scenario shared by BDD and ATDD has one owning suite, both evidence roles, and no label-driven duplicate
- [ ] A scenario shared by BDD and ATDD records an explicit equivalence rationale
- [ ] Artifact definitions and execution results appear once in the Evidence Artifact Registry
- [ ] FR/SC/US/EC relationships appear in the Source Coverage Map without copied status or evidence fields
- [ ] Every mapped artifact ID resolves to exactly one registry entry
- [ ] Quality-gate commands, policies, statuses, and evidence appear once in Quality Gate Results
- [ ] Shared fixtures, helpers, and runner adapters are not duplicated across suites
- [ ] Planned, Red, Green, Blocked, and N/A statuses agree with current task and execution evidence
