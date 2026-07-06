# Test-First Planning Wrapper

Apply these requirements in addition to the core planning workflow.

## Mandatory Planning Outputs
The implementation plan MUST include:
- test directory structure with visible `tests/tdd/`, `tests/bdd/`, `tests/atdd/`, and `tests/reports/` ownership;
- selected tools and commands for TDD, BDD, ATDD, coverage, linting, static analysis/type checking, and runtime smoke validation;
- minimum quality thresholds;
- expected report paths;
- red-green-refactor execution model for every user story;
- a materialized `specs/<feature>/test-traceability.md` mapping FR/SC/US/EC IDs to test and scenario IDs;
- BDD and ATDD applicability decisions, including rationale and alternative evidence for every `N/A`.

## Mandatory Traceability Creation
Before reporting planning complete:
1. Resolve `test-traceability-template` through Spec Kit's template resolver (for example, `specify preset resolve test-traceability-template`).
2. Materialize the resolved template at `specs/<feature>/test-traceability.md`.
3. Populate all known source IDs, applicability decisions, planned artifact IDs, owning suites, paths, and commands.
4. Set unexecuted evidence to `Planned`; do not claim Red or Green results during planning.

If the matrix already exists, update it in place and preserve valid execution history.

## Tool Selection Guidance
Choose stack-native tools. Examples:
- Python: pytest, pytest-bdd/behave, coverage.py, ruff, mypy/pyright, bandit where applicable.
- TypeScript/JavaScript: Vitest/Jest, Cucumber.js/Playwright, c8/nyc, ESLint, TypeScript compiler, dependency audit where applicable.
- Java: JUnit, Cucumber JVM, JaCoCo, Checkstyle/SpotBugs/Error Prone where applicable.
- .NET: xUnit/NUnit/MSTest, SpecFlow/Reqnroll, Coverlet, dotnet format, analyzers.
- Go: go test, godog, coverage, go vet, staticcheck.

{CORE_TEMPLATE}

## Additional Planning Gate
Before completing the plan, verify:
- [ ] The plan makes tests mandatory, not optional
- [ ] Required BDD and ATDD practices have Gherkin runners or equivalent bindings
- [ ] Every BDD/ATDD `N/A` remains justified and is not contradicted by the planned behavior
- [ ] Coverage/lint/static/runtime gate commands are declared
- [ ] Test reports are stored by suite under `tests/reports/`
- [ ] `specs/<feature>/test-traceability.md` exists and contains all known planned mappings
