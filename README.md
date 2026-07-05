# Test-First Governance Preset for GitHub Spec Kit

This preset enforces a strict test-first delivery workflow for Spec Kit features:

- **TDD**: failing implementation-level tests before production code, including happy paths, boundaries, edge cases, and expected error sources.
- **BDD**: Gherkin behavior scenarios with executable mirrored step bindings.
- **ATDD**: Gherkin acceptance scenarios with executable mirrored acceptance tests.
- **Quality gates**: coverage, linting, formatting, static analysis/type checking, runtime smoke checks, and traceability.

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

## Enforcement Model

The preset uses append and wrap composition so it can coexist with other presets. It adds mandatory sections to core templates and wraps core commands with stronger test-first instructions.

Important override: if a lower-priority/core Spec Kit template says tests are optional, this preset supersedes that wording. Tests are mandatory for all buildable behavior.

## Required Directory Semantics

```text
tests/
├── tdd/
├── bdd/
├── atdd/
└── reports/
```

Platform-specific conventions are allowed only when the suite ownership remains visible in the path names.

## Community Catalog Entry Example

```json
"test-first-governance": {
  "name": "Test-First Governance",
  "id": "test-first-governance",
  "version": "1.0.0",
  "description": "Enforces TDD, BDD, and ATDD with mandatory Gherkin scenarios, explicit suite ownership, traceability, coverage, linting, static analysis, and runtime validation gates.",
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
