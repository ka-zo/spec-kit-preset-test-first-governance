# Test-First Analysis Wrapper

Apply these checks in addition to the core cross-artifact analysis.

## Additional Critical Findings
Report a CRITICAL issue if any of the following are true:
- Any executable product-test artifact does not have exactly one owning suite (`TDD`, `BDD`, or `ATDD`).
- Equivalent tests, scenarios, bindings, or fixtures are duplicated solely to satisfy multiple practice labels.
- Any user story lacks ATDD Gherkin scenario coverage.
- Any user story lacks BDD Gherkin scenario coverage.
- Any BDD or ATDD Gherkin scenario lacks stable tags for suite, user story, and requirement/success/edge-case ID.
- Any Gherkin scenario lacks an executable test binding or planned binding task.
- Any implementation task appears before required test tasks for the same story.
- Any FR/SC/EC has zero mapped test artifacts.
- Coverage, linting, static analysis, or runtime smoke gates are missing.
- Test directories do not make TDD/BDD/ATDD ownership clear.

{CORE_TEMPLATE}

## Additional Output Tables
Add these tables to the report:

### Test Suite Coverage Summary
| Suite | Planned Artifacts | Executable Bindings | Report Path | Blocking Gaps |
|-------|-------------------|---------------------|-------------|---------------|
| TDD | [count] | [count] | tests/reports/tdd/ | [gaps] |
| BDD | [count] | [count] | tests/reports/bdd/ | [gaps] |
| ATDD | [count] | [count] | tests/reports/atdd/ | [gaps] |

### Requirement-to-Test Traceability
| Source ID | TDD | BDD | ATDD | Gap? |
|-----------|-----|-----|------|------|
| FR-001 | [ids] | [ids] | [ids] | [yes/no] |
