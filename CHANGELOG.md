# Changelog

## Unreleased

- Clarify that the preset governs Spec Kit artifacts and agent instructions, while mechanical enforcement requires project CI checks and branch protection.
- Replace overstated "enforces" wording with "governs" in preset metadata and documentation.
- Distinguish complementary TDD, BDD, and ATDD practices from primary suite ownership.
- Allow one artifact to support multiple evidence roles while prohibiting label-driven duplication of tests, scenarios, bindings, and shared support code.
- Make BDD and ATDD applicability explicit instead of requiring both indiscriminately for every story.
- Permit governed `N/A` decisions for technical-only work when backed by a concrete rationale and alternative TDD or quality-gate evidence.

## 1.0.0 - 2026-07-05

- Initial Test-First Governance preset.
- Adds mandatory TDD, BDD, ATDD, Gherkin, traceability, coverage, linting, static analysis, and runtime smoke gates.
