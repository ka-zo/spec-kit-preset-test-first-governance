# Test-First Governance Wrapper

Before and after executing the core constitution workflow, ensure the project constitution contains non-negotiable principles for:
- test-first implementation;
- explicit suite ownership while treating TDD, BDD, and ATDD as complementary practices;
- mandatory Gherkin when BDD or ATDD applies, with governed `N/A` decisions for technical-only work;
- Gherkin scenario ID to executable test mirroring;
- risk-based coverage, linting, formatting, applicable static-analysis/security/runtime gates, and lifecycle-managed traceability.

If the constitution omits these principles, add them or report a blocking governance gap.

{CORE_TEMPLATE}

## Additional Done Criteria
- [ ] Constitution makes TDD mandatory for production logic and defines BDD/ATDD applicability
- [ ] Constitution requires concrete rationale and alternative evidence for BDD/ATDD `N/A`
- [ ] Constitution requires one owning suite per executable artifact and prohibits label-driven duplication
- [ ] Constitution states that quality gates are mandatory and blocking
- [ ] Constitution requires explicit gate applicability, threshold exceptions, and evidence-retention policy
- [ ] Constitution defines `specs/<feature>/test-traceability.md` as the canonical feature matrix
