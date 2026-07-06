# Test-First Checklist Wrapper

When generating any checklist, include test-first readiness checks unless the checklist topic is completely unrelated to implementation quality.

{CORE_TEMPLATE}

## Mandatory Test-First Checklist Categories
Include these categories when applicable:
- TDD readiness and negative-path coverage
- BDD applicability, Gherkin completeness, and step-binding mirroring
- ATDD applicability, acceptance completeness, and executable mirroring
- rationale and alternative evidence for BDD/ATDD `N/A` decisions
- non-duplicative BDD/ATDD evidence-role mappings and one owning suite per shared scenario
- reuse of core story, requirement, success-criterion, and task identifiers
- minimal, stable edge-case, scenario, test, and binding identifiers where core has no equivalent
- risk-based coverage, linting, formatting, and applicable static-analysis/security/runtime gates
- gate applicability, threshold exceptions, blocking behavior, and evidence retention
- lifecycle completeness of `specs/<feature>/test-traceability.md`
- directory ownership for applicable `tests/tdd/`, `tests/bdd/`, and `tests/atdd/` suites
