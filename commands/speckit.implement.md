# Test-First Implementation Wrapper

Apply these execution rules in addition to the core implementation workflow.

## Critical Execution Rules
- Do not write production code for a behavior slice until its required TDD and applicable ATDD/BDD executable evidence exists.
- Run the new evidence for the current slice before its production change and confirm it fails for the expected missing behavior. Record red-state evidence in task, PR, or CI output; write a persistent report only when the plan requires versioned retention.
- After the expected failure, update the matching row in `specs/<feature>/test-traceability.md` to `Red` with its evidence path.
- Implement the smallest production change needed to pass the current slice's failing evidence.
- Rerun the slice evidence, update it to `Green`, and refactor while keeping the relevant suites green.
- Complete one Red-Green-Refactor cycle before adding executable evidence for the next slice; do not batch every failing test for the story before implementation.
- Run full TDD, all executable evidence mapped to required BDD/ATDD roles, coverage, linting, formatting, and every quality gate marked `Required` before marking the story complete.
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
- [ ] Reproducible red-state evidence exists in the retention location declared by the plan
- [ ] All TDD tests pass and approved coverage thresholds are met without baseline regression
- [ ] All scenarios mapped to required BDD roles pass and have executable bindings
- [ ] All scenarios mapped to required ATDD roles pass and have executable bindings
- [ ] Shared BDD/ATDD evidence uses one owning-suite execution route and provides both mapped roles
- [ ] Every BDD/ATDD `N/A` remains justified and has alternative evidence
- [ ] Linting/formatting has zero blocking findings
- [ ] Every required static-analysis, security, and runtime-smoke gate passes
- [ ] Every gate `N/A` and threshold exception remains justified and approved
- [ ] `specs/<feature>/test-traceability.md` has no missing FR/SC/US/EC coverage or stale statuses
