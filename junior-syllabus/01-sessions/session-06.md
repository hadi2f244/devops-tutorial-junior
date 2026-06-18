# Session 06 - Week 3

## Topic
Git and Gitflow: Branching, Rebase/Merge, Recovery

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session examines Git from the perspective of team workflows and error recovery. The student must practically understand a suitable branch strategy, the difference between merge and rebase, and the recovery path with reflog and reset.

## Technical Topics to be Covered

- Commit graph and branch design
- Merge vs. rebase
- Conflict resolution
- Recovery with reflog, reset, restore

## Key Commands

- git init, git clone, git status, git add, git commit
- git log --oneline --graph, git branch, git switch, git merge, git rebase
- git cherry-pick, git stash, git fetch, git pull --rebase, git push
- git reflog, git reset --soft/mixed, git restore

## Practical Scenario

A team repo is created with feature, release, and hotfix branches, a real conflict is created and resolved, and finally, a destructive mistake is recovered with reflog.

## LPIC-like Mapping

- This session does not have a direct LPIC equivalent, but it is an important prerequisite for CI/CD workflows.

## References for this Session

- Official: https://git-scm.com/docs
- Official: https://git-scm.com/book/en/v2
- Official: https://git-scm.com/docs/git-rebase
- Blog: https://www.atlassian.com/git/tutorials
- Blog: https://github.blog/
- Workflow: https://git-scm.com/docs/gitworkflows

## Assignment and Rubric

- Assignment: complete workflow from feature to release + PR template
- Artifact: homework/session-06/gitflow-demo.md + conflict-resolution.md
- Rubric: 40% workflow correctness, 25% conflict handling, 20% commit history quality, 15% docs

## Suggested Supplementary Content

- Add Conventional Commits for history readability
- Add a protected branch policy on the remote
- Out-of-scope (Junior): mono-repo scale workflows

## Detailed Learning Objectives

- The student can design a simple but maintainable branch strategy.
- Analyze the difference between merge and rebase based on traceability and readability.
- Recover from common errors with reflog/reset/restore.

## Detailed Agenda (180 minutes)

- 00:00 to 00:20: Why Git is important in DevOps
- 00:20 to 01:00: Object model and commit graph
- 01:00 to 01:20: Merge vs. rebase in a real scenario
- 01:20 to 01:30: Break
- 01:30 to 02:10: Conflict resolution lab
- 02:10 to 02:40: Recovery with reflog/reset/restore
- 02:40 to 03:00: Final flow: feature -> release

## Step-by-step Teaching Path

1. Create a shared repo with a few branches.
2. Intentionally create a conflict and practice the correct resolution path.
3. Recover a destructive mistake with reflog.
4. Define a minimal commit/branch policy for the team.

## Common Errors to Cover

- Force pushing without team coordination
- Rebasing a shared branch without notification
- Large commits without meaningful messages

## Expanded Web References

### Official

- https://git-scm.com/docs
- https://git-scm.com/book/en/v2
- https://git-scm.com/docs/git-rebase
- https://git-scm.com/docs/git-merge
- https://git-scm.com/docs/git-reflog

### Practical / Blogs

- https://www.atlassian.com/git/tutorials
- https://github.blog/

### Workflow / Exam-style

- https://git-scm.com/docs/gitworkflows
