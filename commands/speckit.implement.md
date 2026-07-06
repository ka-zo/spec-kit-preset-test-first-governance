# Test-First Implementation Wrapper

Apply these execution rules in addition to the core implementation workflow.

## Critical Execution Rules
- Do not write production code for a user story until its TDD and all `Required` ATDD/BDD test tasks exist.
- Run the new TDD and all `Required` ATDD/BDD tests before implementation and confirm they fail for the expected reason. Record red-state evidence under `tests/reports/{suite}/`.
- After each expected failure, update the matching row in `specs/<feature>/test-traceability.md` to `Red` with its evidence path.
- Implement the smallest production change needed to pass the failing tests.
- Refactor only after tests pass, and rerun the relevant suites after refactoring.
- Run full TDD, all required BDD/ATDD suites, coverage, linting, static analysis, and runtime smoke gates before marking the story complete.
- Update each executed artifact or gate to `Green` or `Blocked`; retain `N/A` only with its approved rationale and alternative evidence.
- Mark tasks `[X]` only after the relevant tests/gates have been executed and evidence paths exist.

## Failure Handling
If a test fails for an unexpected reason, stop the current story implementation and report:
- failing command;
- failing suite (`TDD`, `BDD`, `ATDD`, or gate);
- expected failure reason vs actual failure reason;
- file path and scenario/test ID;
- proposed fix.

{CORE_TEMPLATE}

## Additional Done Criteria
- [ ] All required red-state reports exist
- [ ] All TDD tests pass and coverage thresholds are met
- [ ] All required BDD scenarios pass and each scenario has an executable binding
- [ ] All required ATDD scenarios pass and each scenario has an executable binding
- [ ] Every BDD/ATDD `N/A` remains justified and has alternative evidence
- [ ] Linting/formatting has zero blocking findings
- [ ] Static analysis/type checking has zero blocking findings
- [ ] Runtime smoke checks pass
- [ ] `specs/<feature>/test-traceability.md` has no missing FR/SC/US/EC coverage or stale statuses
