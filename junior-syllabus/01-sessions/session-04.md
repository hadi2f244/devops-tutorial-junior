# Session 04 - Week 2

## Topic
Production-Ready Bash Scripting, Regex, awk/sed, Error Handling

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session takes Bash from the command line level to the operational script level. The focus is on error handling, parsing, quoting, and creating a script that is reliable in a production environment.

## Technical Topics to be Covered

- Strict mode and trap patterns
- Parsing with awk/sed/grep
- Quoting, globbing, and preventing word splitting
- Designing appropriate exit codes for CI and operations

## Key Commands

- bash -n, shellcheck, set -euo pipefail, trap '...' ERR EXIT
- grep -E, awk, sed -E, cut, tr, xargs, tee
- sort, uniq, getopts, [[ ]], case, for/while

## Practical Scenario

A script is written to validate backups. It parses logs, categorizes errors, returns an appropriate exit code, and generates a report.

## LPIC-like Mapping

- 103.x: text processing tools
- 105.x: shell scripting fundamentals

## References for this Session

- Official: https://www.gnu.org/software/bash/manual/bash.html
- Official: https://www.gnu.org/software/gawk/manual/gawk.html
- Official: https://www.gnu.org/software/sed/manual/sed.html
- Blog: https://www.digitalocean.com/community/tutorials/how-to-use-bash-scripting-in-linux
- Blog: https://mywiki.wooledge.org/BashGuide
- LPIC-like: https://learning.lpi.org/en/learning-materials/101-500/

## Assignment and Rubric

- Assignment: production-ready script with test cases
- Artifact: homework/session-04/backup-validator.sh + test-cases.txt + sample-logs/
- Rubric: 35% robustness, 25% readability, 25% parsing correctness, 15% tests

## Suggested Supplementary Content

- Add bats-core for unit testing shell scripts
- Add a standard logging format (timestamp + severity)
- Out-of-scope (Junior): developing a reusable shell library at a team scale

## Detailed Learning Objectives

- The student will write a reliable script with real error handling.
- Become familiar with quoting/globbing pitfalls and prevent common errors.
- Use awk/sed/grep correctly in a pipeline for log parsing.

## Detailed Agenda (180 minutes)

- 00:00 to 00:25: Principles of a production-ready script
- 00:25 to 01:05: set -euo pipefail + trap patterns
- 01:05 to 01:20: Regex and quoting pitfalls
- 01:20 to 01:30: Break
- 01:30 to 02:15: Parsing pipeline with awk/sed/grep
- 02:15 to 02:45: Implementing backup-validator.sh
- 02:45 to 03:00: Collective code review

## Step-by-step Teaching Path

1. Show a fragile version of the script.
2. Refactor the same script with strict mode and traps.
3. Add a few sample logs with edge cases and make the parser robust.
4. Define an exit code contract for CI.

## Common Errors to Cover

- Unwanted word splitting due to not quoting
- Relying on grep-only for structured parsing
- Ignoring shellcheck warnings

## Expanded Web References

### Official

- https://www.gnu.org/software/bash/manual/bash.html
- https://www.gnu.org/software/gawk/manual/gawk.html
- https://www.gnu.org/software/sed/manual/sed.html
- https://mywiki.wooledge.org/BashGuide
- https://man7.org/linux/man-pages/man1/grep.1.html

### Practical / Blogs

- https://www.digitalocean.com/community/tutorials/how-to-use-bash-scripting-in-linux
- https://www.digitalocean.com/community/tutorials/how-to-use-find-and-locate-to-search-for-files-on-linux

### LPIC-like / Exam-style

- https://learning.lpi.org/en/learning-materials/101-500/
