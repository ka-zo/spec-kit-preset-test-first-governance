# Test-First Governance Preset for GitHub Spec Kit

## Motivation

Spec-Driven Development makes intent explicit before implementation, but a well-written specification alone does not prove that the resulting software is correct, resilient, or complete. This preset strengthens the path from specification to implementation by requiring test-first executable evidence, behavior and acceptance coverage where applicable, requirement-to-test traceability, and risk-based quality gates.

The goal is to make SDD delivery more robust and repeatable: requirements remain connected to tests, expected failures are observed before production code is written, and implementation is considered complete only when the declared evidence and quality checks support that conclusion.

## Approach

The preset strengthens the existing Spec Kit workflow rather than replacing it. It combines several complementary techniques:

- **Test-Driven Development (TDD)** uses the Red-Green-Refactor cycle: write a failing test, implement the smallest change that makes it pass, then improve the design while tests remain green. This provides rapid feedback and keeps production logic testable.
- **Behavior-Driven Development (BDD)** describes user-visible behavior and business rules through concrete Gherkin examples. These shared examples reduce ambiguity and connect expected behavior to executable tests.
- **Acceptance Test-Driven Development (ATDD)** defines stakeholder-facing acceptance evidence before implementation. It helps ensure that delivered functionality satisfies the intended business outcome, not merely its internal design.
- **Requirement-to-test traceability** connects stories, requirements, edge cases, scenarios, tests, and execution evidence. It exposes missing or stale coverage across the development lifecycle.
- **Risk-based quality gates** apply coverage, linting, formatting, static analysis, security, and runtime checks according to the project’s technology and risk surface. They provide broader safeguards without imposing irrelevant ceremony.

These techniques are carried through specification, planning, task generation, implementation, and analysis. Tests precede production code, expected failures are observed, required evidence remains traceable, and completion is blocked when declared tests or quality gates do not support it.

## Governance Scope

This preset governs a strict test-first delivery workflow for Spec Kit features:

- **TDD**: failing implementation-level tests before production code, including happy paths, boundaries, edge cases, and expected error sources.
- **BDD**: Gherkin behavior scenarios with executable mirrored step bindings when the feature has user-visible behavior or business rules.
- **ATDD**: Gherkin acceptance scenarios with executable mirrored acceptance tests when the feature has a stakeholder-facing acceptance boundary.
- **Quality gates**: risk-based coverage, linting, formatting, static analysis/type checking, applicable runtime smoke checks, and traceability.

TDD, BDD, and ATDD are complementary development practices, not mutually exclusive test types. Every executable test artifact has one **owning suite** for directory, task, command, and report routing, but it MAY provide evidence for multiple practices or requirements. Equivalent tests MUST NOT be copied between suites merely to satisfy labels.

TDD remains mandatory for production logic. Each user story MUST explicitly mark BDD and ATDD as `Required` or `N/A`. `N/A` is permitted only for technical-only work with no corresponding observable behavior or stakeholder acceptance boundary; it requires a concrete rationale and alternative TDD or quality-gate evidence.

## Identifier Contract

- Reuse core Spec Kit identifiers: `User Story 1`, `US1`, `[US1]`, `FR-001`, `SC-001`, and `T###`.
- Add `EC-001` only because core Edge Cases have no identifier and traceability needs a stable reference.
- Test and scenario IDs add only an owning-suite prefix and sequence: `TDD-US1-001`, `BDD-US1-001`, and `ATDD-US1-001`.
- Gherkin tags reuse source and scenario IDs verbatim, for example `@BDD @US1 @FR-001 @BDD-US1-001`.

Identifiers are stable once published. Never renumber or reuse them when artifacts move or requirements change.

## Installation

This preset requires GitHub Spec Kit `>=0.8.0`.

After the preset is published to an install-enabled catalog:

```bash
specify preset add test-first-governance --priority 5
```

To install a tagged release directly:

```bash
specify preset add --from "https://github.com/ka-zo/spec-kit-preset-test-first-governance/archive/refs/tags/v1.0.0.zip" --priority 5
```

For local development, run the following commands from this repository root:

```bash
specify preset add --dev . --priority 5
specify preset resolve spec-template
specify preset resolve tasks-template
specify preset info test-first-governance
```

## Recommended Workflow

```text
/speckit.constitution
/speckit.specify
/speckit.clarify
/speckit.plan
/speckit.checklist
/speckit.tasks
/speckit.analyze
/speckit.implement
/speckit.converge
```

## Governance and Enforcement Boundary

The preset uses append and wrap composition so it can coexist with other presets. It adds mandatory sections to core templates and wraps core commands with stronger test-first instructions.

Within the Spec Kit workflow, if a lower-priority/core template says tests are optional, this preset supersedes that wording. Tests are mandatory for all buildable behavior.

A preset governs generated artifacts and agent instructions; it does not install test tools, configure CI, or prevent contributors from bypassing the workflow. For mechanical enforcement, projects using this preset MUST configure the test and quality-gate commands selected during planning as required CI checks and, where available, protect the target branch against failing or missing checks.

## Required Directory Semantics

```text
tests/
├── tdd/
├── bdd/
├── atdd/
├── support/
└── [reports/]  # only when versioned report retention is required
```

Platform-specific conventions are allowed only when suite ownership remains visible. A BDD or ATDD directory is required when that practice has executable artifacts; an entirely non-applicable suite need not create an empty directory. Shared fixtures, helpers, and runner adapters belong under `tests/support/` (or an equivalent shared path) instead of being duplicated across suites. A local reports directory is optional because CI is the default evidence-retention mechanism.

## Traceability Lifecycle

Each feature uses one canonical traceability artifact:

```text
specs/<feature>/test-traceability.md
```

`/speckit.plan` resolves the preset's `test-traceability-template` and creates the file. `/speckit.tasks` adds explicit update tasks, `/speckit.implement` records Red/Green and gate evidence, and `/speckit.analyze` treats a missing or stale matrix as a blocking issue.

## Quality-Gate Policy

Every project declares its gate commands, applicability, thresholds, and evidence retention during planning. Coverage is mandatory for changed production code; 90% line and 85% branch coverage are recommended starting guardrails rather than universal constants. Lower thresholds require a documented, approved exception and compensating evidence.

Runtime smoke, security, and tool-specific static-analysis gates are required when applicable to the stack and risk surface. A gate may be `N/A` only with a concrete technical rationale. Red-state and final results should normally be retained as reproducible CI output or CI artifacts, not committed per-story report files.

## License

This preset is available under the [MIT License](LICENSE).
