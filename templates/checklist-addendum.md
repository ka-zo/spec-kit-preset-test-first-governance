
---

## Test-First Quality Checklist Addendum *(mandatory)*

### TDD Completeness
- [ ] Every implementation unit has a failing test before production code is written
- [ ] Happy paths, edge cases, invalid inputs, boundary values, and expected error sources are covered
- [ ] Contract/integration seams have tests before dependent implementation is added
- [ ] TDD tests are stored under a clearly visible `tests/tdd/` directory or equivalent platform-specific path

### BDD Completeness
- [ ] Every user-visible behavior and business rule has Gherkin scenarios
- [ ] Every BDD scenario has tags for suite, user story, and requirement IDs
- [ ] Every BDD scenario has an implemented step binding or equivalent executable mapping
- [ ] BDD feature files and step definitions are stored under `tests/bdd/` or equivalent platform-specific path

### ATDD Completeness
- [ ] Every user story has stakeholder-facing acceptance scenarios in Gherkin syntax
- [ ] Every buildable success criterion maps to at least one ATDD scenario
- [ ] Every ATDD scenario has an implemented acceptance binding or equivalent executable mapping
- [ ] ATDD feature files and step definitions are stored under `tests/atdd/` or equivalent platform-specific path

### Quality Gates
- [ ] Coverage thresholds are declared and enforced
- [ ] Linting/formatting is configured and blocking
- [ ] Static analysis/type checking is configured and blocking
- [ ] Runtime smoke checks are configured and blocking
- [ ] Reports are stored in `tests/reports/` by suite

### Traceability
- [ ] Every FR/SC/US/EC maps to one or more TDD, BDD, or ATDD artifacts
- [ ] Every Gherkin scenario ID maps to an executable test or step binding
- [ ] Every executable product-test artifact has exactly one owning suite
- [ ] Additional evidence roles are represented in traceability rather than duplicate tests
- [ ] Shared fixtures, helpers, and runner adapters are not duplicated across suites
