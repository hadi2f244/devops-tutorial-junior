# Session 03 - Week 2

## Topic
systemd, journald, Unit Override, Cron vs Timer vs at

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session covers the practical behavior of systemd, journald, and task scheduling. The student should be able to manage services, query logs, and decide between cron, timer, and at based on real-world needs.

## Technical Topics to be Covered

- Service lifecycle in systemd
- Querying logs with journalctl
- Overriding a unit file
- The difference between cron, timer, and at

## Key Commands

- systemctl status/start/stop/restart/reload/enable/disable
- systemctl edit, systemctl daemon-reload, systemctl list-timers
- journalctl -u, journalctl -b, journalctl --since, journalctl -f
- crontab -e/-l, at, atq, atrm

## Practical Scenario

A custom health-check service is created, run every few minutes with a timer, its output is logged in the journal, and then the same task is implemented and compared with cron.

## LPIC-like Mapping

- 101.x: boot/service behavior
- 107.x: scheduled jobs, log inspection

## References for this Session

- Official: https://www.freedesktop.org/software/systemd/man/latest/systemd.service.html
- Official: https://www.freedesktop.org/software/systemd/man/latest/systemd.timer.html
- Official: https://www.freedesktop.org/software/systemd/man/latest/journalctl.html
- Blog: https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs
- Blog: https://www.redhat.com/en/blog/systemd-timers
- LPIC-like: https://learning.lpi.org/en/learning-materials/102-500/

## Assignment and Rubric

- Assignment: backup-check.service + backup-check.timer
- Artifact: homework/session-03/backup-check.service + backup-check.timer + README
- Rubric: 40% unit correctness, 30% log inspection, 20% cron-vs-timer reasoning, 10% clarity

## Suggested Supplementary Content

- Add journald retention policy and log rotation rationale
- Practice failure injection with an intentionally faulty ExecStart
- Out-of-scope (Junior): custom target design at the multi-service orchestration level

## Detailed Learning Objectives

- The student will practically understand the difference between a service unit and a timer unit.
- Be able to analyze systemd logs with time and service unit queries.
- Make the correct choice between cron and timer based on operational needs.

## Detailed Agenda (180 minutes)

- 00:00 to 00:20: Overview of init/systemd architecture
- 00:20 to 01:00: Service unit deep dive
- 01:00 to 01:20: journald query patterns
- 01:20 to 01:30: Break
- 01:30 to 02:15: Designing a timer and comparing it with cron/at
- 02:15 to 02:45: Practical backup-check lab
- 02:45 to 03:00: Lightweight postmortem

## Step-by-step Teaching Path

1. Create a simple unit.
2. Run the unit with an intentional error and analyze the log path.
3. Implement the same task with cron and a timer and compare observability.
4. Convert the output into a usable runbook for incidents.

## Common Errors to Cover

- Forgetting to run daemon-reload
- Using a timer without checking timezone and persistent behavior
- Lack of a health signal in the task's log output

## Expanded Web References

### Official

- https://www.freedesktop.org/software/systemd/man/latest/systemd.service.html
- https://www.freedesktop.org/software/systemd/man/latest/systemd.timer.html
- https://www.freedesktop.org/software/systemd/man/latest/journalctl.html
- https://man7.org/linux/man-pages/man5/crontab.5.html
- https://man7.org/linux/man-pages/man1/at.1p.html

### Practical / Blogs

- https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs
- https://www.redhat.com/en/blog/systemd-timers

### LPIC-like / Exam-style

- https://learning.lpi.org/en/learning-materials/102-500/
