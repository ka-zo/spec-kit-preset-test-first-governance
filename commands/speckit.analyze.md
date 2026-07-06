# Test-First Analysis Wrapper

Apply these checks in addition to the core cross-artifact analysis.

## Additional Critical Findings
Report a CRITICAL issue if any of the following are true:
- `specs/<feature>/test-traceability.md` is missing, lacks any required normalized section, still contains unresolved required placeholders, or is stale relative to spec.md, plan.md, tasks.md, or execution evidence.
- Within the traceability artifact, artifact commands, statuses, or evidence paths are copied into Source Coverage Map rows instead of being stored once in the Evidence Artifact Registry.
- A source or applicability row references an artifact ID missing from the registry, or an executable artifact has more than one registry entry.
- A required quality gate lacks exactly one current entry in Quality Gate Results.
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
- Any scenario-specific ID tag is placed at feature level, inherited by multiple scenarios, or attached to more than one `Scenario` or `Scenario Outline`.
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
| Artifact ID | Owning Suite | Evidence Roles | Status | Evidence | Blocking Gaps |
|-------------|--------------|----------------|--------|----------|---------------|
| TDD-US1-001 | TDD | TDD | [status] | [path] | [gaps] |
| ATDD-US1-001 | ATDD | ATDD, BDD | [status] | [path] | [gaps] |

### Quality Gate Decisions
| Gate | Applicability | Threshold/Policy | Evidence Destination | Exception | Gap? |
|------|---------------|------------------|----------------------|-----------|------|
| Coverage | Required | [line/branch + baseline] | [location] | [none/details] | [yes/no] |
| Static Analysis | [Required/N/A] | [severity policy] | [location] | [none/details] | [yes/no] |
| Security | [Required/N/A] | [severity policy] | [location] | [none/details] | [yes/no] |
| Runtime Smoke | [Required/N/A] | [pass policy] | [location] | [none/details] | [yes/no] |

### Source Coverage Summary
| Source ID | Source Type | Artifact IDs | Coverage Intent | Gap? |
|-----------|-------------|--------------|-----------------|------|
| FR-001 | Functional Requirement | [ids] | [intent] | [yes/no] |
