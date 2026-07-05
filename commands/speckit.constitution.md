# Test-First Governance Wrapper

Before and after executing the core constitution workflow, ensure the project constitution contains non-negotiable principles for:
- test-first implementation;
- explicit suite ownership while treating TDD, BDD, and ATDD as complementary practices;
- mandatory Gherkin for BDD and ATDD;
- Gherkin scenario ID to executable test mirroring;
- coverage, linting, static analysis, runtime smoke, and traceability gates.

If the constitution omits these principles, add them or report a blocking governance gap.

{CORE_TEMPLATE}

## Additional Done Criteria
- [ ] Constitution includes TDD, BDD, and ATDD as mandatory development disciplines
- [ ] Constitution requires one owning suite per executable artifact and prohibits label-driven duplication
- [ ] Constitution states that quality gates are mandatory and blocking
