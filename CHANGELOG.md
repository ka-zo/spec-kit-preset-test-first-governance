# Changelog

## 1.1.0 - 2026-07-06

- Clarify that the preset governs Spec Kit artifacts and agent instructions, while mechanical enforcement requires project CI checks and branch protection.
- Replace overstated "enforces" wording with "governs" in preset metadata and documentation.
- Distinguish complementary TDD, BDD, and ATDD practices from primary suite ownership.
- Allow one artifact to support multiple evidence roles while prohibiting label-driven duplication of tests, scenarios, bindings, and shared support code.
- Make BDD and ATDD applicability explicit instead of requiring both indiscriminately for every story.
- Permit governed `N/A` decisions for technical-only work when backed by a concrete rationale and alternative TDD or quality-gate evidence.
- Materialize the traceability template at `specs/<feature>/test-traceability.md` during planning.
- Require task-generation, implementation, and analysis workflows to maintain and validate traceability statuses and execution evidence.
- Replace universal coverage constants with risk-based approved thresholds, baseline protection, and governed exceptions.
- Make stack- and risk-dependent quality gates explicitly applicable or justified `N/A`.
- Prefer reproducible task, PR, and CI evidence over committed per-story generated reports unless audit retention requires them.
- Reuse core Spec Kit identifiers (`US1`, `FR-001`, `SC-001`, and `T###`) without parallel aliases.
- Introduce new identifiers only where necessary: `EC-001` for edge-case traceability and `<SUITE>-US1-001` for executable evidence.
- Keep test, scenario, Gherkin, binding, task, and traceability references consistent with their core source identifiers.
- Treat suite markers as task-description extensions without altering core `T###`, `[P]`, or `[US1]` identifiers.
- Prepare the README for release with Motivation and Approach sections, complete installation and licensing guidance, and removal of the Community Catalog Entry Example and Release Checklist sections.
- Add a branded header image to the README.

## 1.0.0 - 2026-07-05

- Initial Test-First Governance preset.
- Adds mandatory TDD, BDD, ATDD, Gherkin, traceability, coverage, linting, static analysis, and runtime smoke gates.
