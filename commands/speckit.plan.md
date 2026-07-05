# Test-First Planning Wrapper

Apply these requirements in addition to the core planning workflow.

## Mandatory Planning Outputs
The implementation plan MUST include:
- test directory structure with visible `tests/tdd/`, `tests/bdd/`, `tests/atdd/`, and `tests/reports/` ownership;
- selected tools and commands for TDD, BDD, ATDD, coverage, linting, static analysis/type checking, and runtime smoke validation;
- minimum quality thresholds;
- expected report paths;
- red-green-refactor execution model for every user story;
- traceability mechanism from FR/SC/US/EC IDs to test and scenario IDs.

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
- [ ] BDD and ATDD Gherkin runners or equivalent bindings are selected
- [ ] Coverage/lint/static/runtime gate commands are declared
- [ ] Test reports are stored by suite under `tests/reports/`
- [ ] Traceability approach is explicit
