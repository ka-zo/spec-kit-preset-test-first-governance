# Test-First Checklist Wrapper

When generating any checklist, include test-first readiness checks unless the checklist topic is completely unrelated to implementation quality.

{CORE_TEMPLATE}

## Mandatory Test-First Checklist Categories
Include these categories when applicable:
- TDD readiness and negative-path coverage
- BDD Gherkin scenario completeness and step-binding mirroring
- ATDD acceptance scenario completeness and executable mirroring
- Coverage, linting, static analysis, and runtime smoke gates
- Requirement-to-test traceability
- Directory ownership: `tests/tdd/`, `tests/bdd/`, `tests/atdd/`, `tests/reports/`
