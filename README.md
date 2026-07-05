# Test-First Governance Preset for GitHub Spec Kit

This preset governs a strict test-first delivery workflow for Spec Kit features:

- **TDD**: failing implementation-level tests before production code, including happy paths, boundaries, edge cases, and expected error sources.
- **BDD**: Gherkin behavior scenarios with executable mirrored step bindings when the feature has user-visible behavior or business rules.
- **ATDD**: Gherkin acceptance scenarios with executable mirrored acceptance tests when the feature has a stakeholder-facing acceptance boundary.
- **Quality gates**: coverage, linting, formatting, static analysis/type checking, runtime smoke checks, and traceability.

TDD, BDD, and ATDD are complementary development practices, not mutually exclusive test types. Every executable test artifact has one **owning suite** for directory, task, command, and report routing, but it MAY provide evidence for multiple practices or requirements. Equivalent tests MUST NOT be copied between suites merely to satisfy labels.

TDD remains mandatory for production logic. Each user story MUST explicitly mark BDD and ATDD as `Required` or `N/A`. `N/A` is permitted only for technical-only work with no corresponding observable behavior or stakeholder acceptance boundary; it requires a concrete rationale and alternative TDD or quality-gate evidence.

## Install Locally During Development

```bash
specify preset add --dev ./test-first-governance --priority 5
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
└── reports/
```

Platform-specific conventions are allowed only when suite ownership remains visible. A BDD or ATDD directory is required when that practice has executable artifacts; an entirely non-applicable suite need not create an empty directory. Shared fixtures, helpers, and runner adapters belong under `tests/support/` (or an equivalent shared path) instead of being duplicated across suites.

## Community Catalog Entry Example

```json
"test-first-governance": {
  "name": "Test-First Governance",
  "id": "test-first-governance",
  "version": "1.0.0",
  "description": "Governs TDD with applicable BDD and ATDD Gherkin scenarios, explicit suite ownership, traceability, coverage, linting, static analysis, and runtime validation gates.",
  "author": "Your Name or Organization",
  "repository": "https://github.com/your-org/spec-kit-preset-test-first-governance",
  "download_url": "https://github.com/your-org/spec-kit-preset-test-first-governance/archive/refs/tags/v1.0.0.zip",
  "homepage": "https://github.com/your-org/spec-kit-preset-test-first-governance",
  "documentation": "https://github.com/your-org/spec-kit-preset-test-first-governance/blob/main/README.md",
  "license": "MIT",
  "requires": { "speckit_version": ">=0.8.0" },
  "provides": { "templates": 7, "commands": 7 },
  "tags": ["tdd", "bdd", "atdd", "gherkin", "quality-gates", "traceability", "test-first"],
  "created_at": "2026-07-05T00:00:00Z",
  "updated_at": "2026-07-05T00:00:00Z"
}
```

## Release Checklist

- [ ] Update `preset.yml` version
- [ ] Update `CHANGELOG.md`
- [ ] Create a GitHub release/tag
- [ ] Test with `specify preset add --dev ./test-first-governance`
- [ ] Verify `specify preset resolve` for all overridden templates/commands
- [ ] Submit catalog entry and docs row if publishing to the community catalog
