# Test-First Specification Wrapper

Apply these requirements in addition to the core specification workflow.

## Critical Overrides
- Treat TDD, BDD, and ATDD evidence as mandatory for all features.
- Every user story MUST include acceptance criteria that can be converted into ATDD Gherkin scenarios.
- Every user-visible behavior, alternate flow, business rule, and error flow MUST be expressed as BDD Gherkin scenarios.
- Every functional requirement and edge/error condition MUST be testable and mapped to TDD, BDD, or ATDD in the Test Classification Matrix.
- Do not leave product test cases unclassified.

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
- [ ] No test case is unclassified

If any item fails, update `spec.md` before reporting completion.
