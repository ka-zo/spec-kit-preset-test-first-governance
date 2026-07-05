# Test-First Specification Wrapper

Apply these requirements in addition to the core specification workflow.

## Critical Overrides
- Treat TDD, BDD, and ATDD evidence as mandatory for all features.
- Every user story MUST include acceptance criteria that can be converted into ATDD Gherkin scenarios.
- Every user-visible behavior, alternate flow, business rule, and error flow MUST be expressed as BDD Gherkin scenarios.
- Every functional requirement and edge/error condition MUST be testable and mapped to TDD, BDD, or ATDD evidence in the Test Classification Matrix.
- Assign one owning suite to each planned executable artifact. An artifact MAY support multiple evidence roles or source IDs.
- Do not duplicate equivalent artifacts merely to satisfy multiple practice labels.

## Scenario ID Rules
Use stable IDs and Gherkin tags:
- ATDD: `@ATDD @US# @FR-### @SC-### @ATDD-US#-###`
- BDD: `@BDD @US# @FR-### @BDD-US#-###`
- Edge/error scenarios: include `@EC-###`.

{CORE_TEMPLATE}

## Additional Specification Validation
After the core specification quality validation, perform this blocking test-first validation:
- [ ] Every user story has at least one planned ATDD Gherkin scenario
- [ ] Every user story has at least one planned BDD Gherkin scenario
- [ ] Every FR/SC/EC has a mapped test suite and test intent
- [ ] Every expected error source has a negative-path test plan
- [ ] Every planned executable artifact has one owning suite
- [ ] Multi-role evidence is mapped without duplicate artifacts

If any item fails, update `spec.md` before reporting completion.
