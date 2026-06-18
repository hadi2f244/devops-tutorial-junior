# Session 01 - Week 1

## Topic
Linux Fundamentals: Boot Process, systemd Targets, Resource Baseline

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session is the foundation for entering the Linux world in the DevOps path. The student will become familiar with the boot flow from BIOS/UEFI to PID1, understand the difference between runlevels and systemd targets, and learn how to get an operational baseline of the system using the command line. The focus of the session is on analyzing the system's status from an operator's perspective, not just memorizing a few commands.

## Technical Topics to be Covered

- Linux boot path and the role of the bootloader and systemd
- Common targets like multi-user.target and graphical.target
- Initial analysis of CPU, RAM, load, and processes
- Basic commands for inspection and troubleshooting

## Key Commands

- uname, hostnamectl, uptime
- systemctl get-default, systemctl list-units --type=target, systemctl isolate
- journalctl -b
- top, free -h, vmstat
- ps aux --sort=-%cpu, ps aux --sort=-%mem
- ls, find, grep, less, tail

## Practical Scenario

The student must create a baseline report that includes the kernel version, load average, memory status, top processes, and a brief interpretation of any bottlenecks. This output should be saved as a deliverable artifact in Git.

## LPIC-like Mapping

- 101.x: system architecture + boot process
- 103.x: GNU/Linux commands
- 108.x: process basics

## References for this Session

- Official: https://www.freedesktop.org/software/systemd/man/latest/systemctl.html
- Official: https://www.freedesktop.org/software/systemd/man/latest/journalctl.html
- Official: https://www.gnu.org/software/coreutils/manual/coreutils.html
- Blog: https://www.digitalocean.com/community/tags/linux
- Blog: https://www.redhat.com/en/blog/channel/infrastructure
- LPIC-like: https://www.lpi.org/our-certifications/lpic-1-overview/
- LPIC-like: https://learning.lpi.org/en/learning-materials/101-500/

## Assignment and Rubric

- Assignment: system-report.sh script for a system snapshot
- Artifact: homework/session-01/system-report.sh + README + sample-output.txt
- Rubric: 30% conceptual, 30% output analysis, 25% lab, 15% assignment

## Suggested Supplementary Content

- Add sar/iostat for trend-based baselining
- Introduce a quick triage checklist for first-minute incidents
- Out-of-scope (Junior): deep kernel scheduler tuning

## Detailed Learning Objectives

- The student can explain the boot chain from firmware to user space.
- Analyze the difference between system state and service state in systemd.
- Convert the output of resource monitoring tools into operational decisions.

## Detailed Agenda (180 minutes)

- 00:00 to 00:20: Course overview and defining an operational baseline
- 00:20 to 00:55: Linux boot process and the role of systemd in startup
- 00:55 to 01:20: Targets, dependencies, and rescue mode
- 01:20 to 01:30: Break
- 01:30 to 02:10: Practical analysis of CPU/RAM/Load
- 02:10 to 02:40: Command drill on file/process inspection
- 02:40 to 03:00: Lab and Q&A

## Step-by-step Teaching Path

1.  Take a baseline of a healthy VM.
2.  Intentionally fail a service and show the diagnosis path using journalctl.
3.  Compare the output of top/free/ps side-by-side to show correlation.
4.  Receive the final output in the form of a report.

## Common Errors to Cover

- Confusing load average with CPU percentage
- Over-reliance on a single monitoring tool
- Lack of timestamps in operational reports

## Expanded Web References

### Official

- https://www.freedesktop.org/software/systemd/man/latest/systemd.html
- https://www.freedesktop.org/software/systemd/man/latest/systemctl.html
- https://www.freedesktop.org/software/systemd/man/latest/journalctl.html
- https://man7.org/linux/man-pages/man1/ps.1.html
- https://www.gnu.org/software/coreutils/manual/coreutils.html

### Practical / Blogs

- https://www.digitalocean.com/community/tags/linux
- https://www.redhat.com/en/blog/channel/infrastructure
- https://www.redhat.com/en/blog/systemd-timers

### LPIC-like / Exam-style

- https://www.lpi.org/our-certifications/lpic-1-overview/
- https://learning.lpi.org/en/learning-materials/101-500/
