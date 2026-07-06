# Test-First Specification Wrapper

Apply these requirements in addition to the core specification workflow.

## Critical Overrides
- Treat TDD evidence as mandatory for production logic.
- Every user story MUST mark BDD and ATDD as `Required` or `N/A`.
- Mark BDD `Required` for user-visible behavior, business rules, alternate flows, and observable errors.
- Mark ATDD `Required` for stakeholder-facing acceptance criteria and release boundaries.
- Every user-visible behavior, alternate flow, business rule, and error flow MUST map to Gherkin scenario evidence carrying the BDD role.
- Permit `N/A` only for technical-only work with no corresponding observable behavior or stakeholder acceptance boundary. Record a concrete rationale and alternative TDD or quality-gate evidence.
- Every functional requirement and edge/error condition MUST be testable and mapped to TDD, BDD, or ATDD evidence in the Test Classification Matrix.
- Assign one owning suite to each planned executable artifact. An artifact MAY support multiple evidence roles or source IDs.
- Treat `Required` as an evidence obligation, not a requirement for a separately owned artifact. One scenario MAY satisfy both BDD and ATDD when it fully covers both intents and traceability records both roles.
- Do not duplicate equivalent artifacts merely to satisfy multiple practice labels.

## Scenario ID Rules
Use stable IDs and Gherkin tags:
- Reuse core identifiers: `US1`, `FR-001`, and `SC-001`.
- Add `EC-001` only for edge-case traceability because core has no edge-case ID.
- ATDD: `@ATDD @US1 @FR-001 @SC-001 @ATDD-US1-001`
- BDD: `@BDD @US1 @FR-001 @BDD-US1-001`
- Edge/error scenarios: include the applicable `@EC-001`.
- IDs are stable after publication and MUST NOT be shortened, renumbered, or reused.

{CORE_TEMPLATE}

## Additional Specification Validation
After the core specification quality validation, perform this blocking test-first validation:
- [ ] Every user story records BDD and ATDD as `Required` or justified `N/A`
- [ ] Every `Required` decision maps to at least one planned Gherkin scenario carrying that evidence role, regardless of owning suite
- [ ] Every `N/A` decision identifies alternative TDD or quality-gate evidence
- [ ] Every FR/SC/EC has a mapped test suite and test intent
- [ ] Every expected error source has a negative-path test plan
- [ ] Every planned executable artifact has one owning suite
- [ ] Multi-role evidence is mapped without duplicate artifacts
- [ ] Core identifiers are reused wherever available
- [ ] New identifiers are introduced only where necessary and remain consistent across tests, scenarios, tags, bindings, and traceability

If any item fails, update `spec.md` before reporting completion.
