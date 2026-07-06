# Test-First Analysis Wrapper

Apply these checks in addition to the core cross-artifact analysis.

## Additional Critical Findings
Report a CRITICAL issue if any of the following are true:
- `specs/<feature>/test-traceability.md` is missing, still contains unresolved required placeholders, or is stale relative to spec.md, plan.md, tasks.md, or execution evidence.
- Any story heading, source reference, or task label violates Spec Kit's `User Story 1` / `US1` / `[US1]` convention.
- A parallel alias such as `US-001` is introduced for a core `US1` story.
- Any necessary preset-specific test, scenario, Gherkin tag, or binding ID is inconsistent with its core source ID.
- Any published identifier is renumbered or reused for a different artifact.
- Any executable product-test artifact does not have exactly one owning suite (`TDD`, `BDD`, or `ATDD`).
- Equivalent tests, scenarios, bindings, or fixtures are duplicated solely to satisfy multiple practice labels.
- Any user story lacks an explicit `Required` or `N/A` decision for BDD or ATDD.
- Any `Required` BDD or ATDD decision lacks Gherkin scenario evidence mapped to that role, regardless of owning suite.
- Separate scenarios, bindings, tasks, commands, or reports exist only because both BDD and ATDD are `Required`, although one artifact fully covers both intents.
- Any BDD or ATDD `N/A` lacks a concrete rationale and alternative evidence, or conflicts with observable behavior or a stakeholder acceptance boundary.
- Any BDD or ATDD Gherkin scenario lacks stable tags for suite, user story, and requirement/success/edge-case ID.
- Any Gherkin scenario lacks an executable test binding or planned binding task.
- Any implementation task appears before required test tasks for the same story.
- Any FR/SC/EC has zero mapped test artifacts.
- Coverage lacks approved thresholds or permits regression below the accepted baseline.
- Any quality gate lacks a command or a justified `N/A`, blocking behavior, or an evidence-retention destination.
- Any threshold exception lacks scope, rationale, compensating evidence, approval, or expiry/follow-up.
- Per-story generated reports are required without an audit or regulatory retention rationale.
- Test directories do not make TDD/BDD/ATDD ownership clear.

{CORE_TEMPLATE}

## Additional Output Tables
Add these tables to the report:

### Test Evidence Coverage Summary
| Practice | Applicability | Mapped Artifact IDs | Owning Suites | Execution Commands | Blocking Gaps |
|----------|---------------|---------------------|---------------|--------------------|---------------|
| TDD | Required | [ids] | [owners] | [commands] | [gaps] |
| BDD | [Required/N/A] | [ids] | [owners] | [commands] | [gaps] |
| ATDD | [Required/N/A] | [ids] | [owners] | [commands] | [gaps] |

### Quality Gate Decisions
| Gate | Applicability | Threshold/Policy | Evidence Destination | Exception | Gap? |
|------|---------------|------------------|----------------------|-----------|------|
| Coverage | Required | [line/branch + baseline] | [location] | [none/details] | [yes/no] |
| Static Analysis | [Required/N/A] | [severity policy] | [location] | [none/details] | [yes/no] |
| Security | [Required/N/A] | [severity policy] | [location] | [none/details] | [yes/no] |
| Runtime Smoke | [Required/N/A] | [pass policy] | [location] | [none/details] | [yes/no] |

### Requirement-to-Test Traceability
| Source ID | TDD | BDD | ATDD | Matrix Status | Evidence | Gap? |
|-----------|-----|-----|------|---------------|----------|------|
| FR-001 | [ids] | [ids] | [ids] | [status] | [paths] | [yes/no] |
