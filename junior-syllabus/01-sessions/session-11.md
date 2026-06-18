# Session 11 - Week 6

## Topic
Sample Project Pipeline: Build/Test with Git + Bash + Docker

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session takes the sample final project into the CI stage. The student must build a pipeline that separates build and test, runs unit and integration tests in the flow, and has reportable output.

## Technical Topics to be Covered

- Designing build and test stages
- Unit tests and integration tests
- Fail-fast behavior
- Reproducible pipeline

## Key Commands

- git rebase, bash strict mode
- docker build/run
- docker compose -f compose.test.yaml up --abort-on-container-exit
- make test, pytest -q
- coverage tooling

## Practical Scenario

For a data service, a local pipeline is designed that separates build and test and clearly reports failure stages.

## LPIC-like Mapping

- This session only overlaps with LPIC-like in terms of shell discipline.

## References for this Session

- Official: https://docs.github.com/en/actions
- Official: https://docs.github.com/actions/get-started/quickstart
- Official: https://docs.github.com/actions/get-started/understand-github-actions
- Official: https://docs.gitlab.com/ee/ci/
- Blog: https://martinfowler.com/articles/continuousIntegration.html
- Blog: https://github.blog/category/engineering/

## Assignment and Rubric

- Assignment: local + CI pipeline with a minimum of 2 stages
- Artifact: homework/session-11/ci-pipeline.yml + compose.test.yaml + test-report.md
- Rubric: 40% pipeline correctness, 25% test quality, 20% reproducibility, 15% reporting

## Suggested Supplementary Content

- Add a caching strategy for dependency installation
- Add a basic pipeline badge and quality gate
- Out-of-scope (Junior): matrix builds and progressive delivery

## Detailed Learning Objectives

- The student will implement a minimal end-to-end build/test pipeline.
- Operationalize the difference between unit and integration tests in a CI flow.
- Enforce fail-fast and reproducible builds in the pipeline.

## Detailed Agenda (180 minutes)

- 00:00 to 00:20: Anatomy of a CI pipeline
- 00:20 to 01:00: Build stage design
- 01:00 to 01:20: Test strategy (unit/integration)
- 01:20 to 01:30: Break
- 01:30 to 02:10: Local CI with compose.test
- 02:10 to 02:40: Workflow on GitHub Actions or GitLab CI
- 02:40 to 03:00: Failure analysis

## Step-by-step Teaching Path

1. Define a deterministic build command.
2. Run the test stage with clear pass/fail output.
3. Inject an intentional failure and practice the debug path.
4. Deliver the final report with a coverage summary.

## Common Errors to Cover

- Dependency on the local environment without version pinning
- Running integration tests without an isolated service
- Slow pipeline due to incorrect caching

## Expanded Web References

### Official

- https://docs.github.com/en/actions
- https://docs.github.com/actions/get-started/quickstart
- https://docs.github.com/actions/get-started/understand-github-actions
- https://docs.gitlab.com/ee/ci/
- https://docs.docker.com/guides/

### Practical / Blogs

- https://martinfowler.com/articles/continuousIntegration.html
- https://github.blog/category/engineering/

### Extension

- https://docs.github.com/en/actions/how-tos/monitor-workflows/add-a-status-badge
