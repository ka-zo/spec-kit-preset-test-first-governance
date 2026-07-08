# Test-First Planning Wrapper

Apply these requirements in addition to the core planning workflow.

## Mandatory Planning Outputs
The implementation plan MUST include:
- test directory structure with visible ownership for every applicable suite;
- selected tools and commands for TDD, BDD, ATDD, coverage, linting, formatting, static analysis/type checking, security, and runtime smoke validation;
- gate applicability, blocking behavior, risk-based thresholds, and exception policy;
- CI output or artifact locations and any explicit versioned-report retention requirement;
- red-green-refactor execution model for every user story;
- a materialized `specs/<feature>/test-traceability.md` with an evidence artifact registry, source-to-artifact coverage map, scenario coverage matrix, applicability decisions, and quality-gate results;
- BDD and ATDD applicability decisions, including rationale and alternative evidence for every `N/A`.
- coverage-complete, non-duplicative scenario mappings showing how every `Required` BDD/ATDD role is satisfied, which suite owns each artifact, and which scenario/example rows cover each source.

## Mandatory Traceability Creation
Before reporting planning complete:
1. Resolve `test-traceability-template` through Spec Kit's template resolver (for example, `specify preset resolve test-traceability-template`).
2. Materialize the resolved template at `specs/<feature>/test-traceability.md`.
3. Populate the Evidence Artifact Registry with planned artifact IDs, owning suites, evidence roles, paths, and commands.
4. Populate the Source Coverage Map with all known source IDs and their artifact IDs.
5. Populate the Scenario Coverage Matrix with scenario/example rows, primary source IDs, input classes, interfaces, and sampling or shared-evidence rationales.
6. Populate applicability decisions and Quality Gate Results without duplicating mutable artifact execution fields in source mappings.
7. Set unexecuted required evidence to `Planned`; do not claim Red or Green results during planning.

If the traceability artifact already exists, update it in place and preserve valid registry and gate execution history.

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
- [ ] Every required BDD and ATDD evidence role maps to an executable binding and owning-suite command
- [ ] The Scenario Coverage Matrix covers every required BDD/ATDD behavior, acceptance boundary, edge/error condition, and required example class
- [ ] Every scenario outline enumerates required examples or records an approved sampling strategy
- [ ] Shared BDD/ATDD evidence has one owning suite and one execution path, with both roles recorded in traceability
- [ ] Shared BDD/ATDD evidence records why behavior and acceptance intent are equivalent
- [ ] Every BDD/ATDD `N/A` remains justified and is not contradicted by the planned behavior
- [ ] Coverage thresholds protect changed code and the accepted project baseline
- [ ] Every gate has a command or a justified `N/A`, plus blocking behavior and evidence retention
- [ ] Lower threshold exceptions identify scope, rationale, compensating evidence, approver, and expiry/follow-up
- [ ] `specs/<feature>/test-traceability.md` contains complete registry, coverage-map, scenario-matrix, applicability, and gate sections with no duplicated execution state
