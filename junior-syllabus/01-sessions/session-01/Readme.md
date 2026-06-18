# Session 01 - Week 1

## Topic
Linux Fundamentals: Boot Process, systemd Targets, Resource Baseline

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/related-certificates.md

## Session Summary

This session provides a comprehensive introduction to Linux fundamentals, essential for any aspiring DevOps professional. Students will explore the complete boot process, from firmware (BIOS/UEFI) to the initialization of the system via `systemd`. The session delves into core concepts such as processes, threads, CPU, and memory management. A significant focus is placed on practical, hands-on skills, including resource usage analysis (CPU, RAM, system load), and understanding file permissions and ownership. By the end of this session, students will be proficient in using basic command-line tools for system inspection and troubleshooting, enabling them to establish an operational baseline of a Linux system. This foundational knowledge is critical for system analysis and diagnostics from an operator's perspective.

## Technical Topics to be Covered

- Linux Structure and Boot Process
- The role of the bootloader and systemd
- Process and Thread concepts
- Memory and CPU concepts
- Basic commands for inspection and troubleshooting
- Resource usage analysis (CPU, RAM, load)
- Permission and Ownership concepts
- Common systemd targets like multi-user.target and graphical.target

## Key Commands

- **System & Boot Info**: `uname -r`, `hostnamectl`, `uptime`, `dmesg`
- **systemd**: `systemctl get-default`, `systemctl set-default <target>`, `systemctl list-units --type=target`, `systemctl isolate <target>`, `systemctl status <service>`, `systemctl start|stop|restart|enable|disable <service>`
- **Journaling**: `journalctl -b`, `journalctl -u <service>`, `journalctl -f`
- **Process Management**: `ps aux`, `ps aux --sort=-%cpu`, `ps aux --sort=-%mem`, `top`, `htop`
- **Memory/CPU Usage**: `free -h`, `vmstat 1`, `lscpu`
- **File System & Permissions**: `ls -l`, `ls -la`, `find . -name "<file>"`, `grep "<pattern>" <file>`, `less <file>`, `tail -f <file>`, `chmod`, `chown`

## Practical Scenario

The student must create a baseline report that includes the kernel version, load average, memory status, top processes, and a brief interpretation of any bottlenecks. This output should be saved as a deliverable artifact in Git.

## LPIC-like Mapping

- **101.1**: Determine and configure hardware settings.
- **101.2**: Boot the system.
- **101.3**: Change runlevels / boot targets and shut down or reboot the system.
- **103.1**: Work on the command line.
- **103.5**: Create, monitor, and kill processes.
- **103.7**: Search for files and text in files.
- **104.2**: Manage file permissions and ownership.
- **108.1**: Manage user and group accounts and related system files.

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
- Introduce a quicarticulate the sequence of events in the Linux boot process, from power-on to a usable user-space.
- The student can differentiate between a process and a thread, and describe their lifecycle.
- The student can use `systemctl` to inspect and manage systemd targets and services.
- The student can analyze CPU and memory usage using `top`, `free`, and `vmstat` to identify potential performance bottlenecks.
- The student can interpret file permissions (read, write, execute) and change ownership using `chmod` and `chown`.
- The student can create a script to automate the collection of system baseline metric
##**00:00 - 00:20 (20 min)**: Introduction: Course goals, structure, and the importance of an operational baseline.
- **00:20 - 00:50 (30 min)**: Theory: The Linux Boot Process (BIOS/UEFI, Bootloader, Kernel, Init/systemd).
- **00:50 - 01:20 (30 min)**: Theory & Demo: Understanding `systemd` (Targets, Services, Dependencies, `systemctl` basics).
- **01:20 - 01:30 (10 min)**: Break
- **01:30 - 02:00 (30 min)**: Practical Lab 1: System Inspection (`uname`, `hostnamectl`, `uptime`, `lscpu`).
- **02:00 - 02:30 (30 min)**: Practical Lab 2: Resource Analysis (`top`, `free`, `vmstat`, `ps`).
- **02:30 - 02:50 (20 min)**: Theory & Demo: Permissions and Ownership (`ls -l`, `chmod`, `chown`).
- **02:50 - 03:00 (10 min)**: Wrap-up: Assignment overview and Q&A.es)

- 00:00 to 00:20: Course overview and defining an operational baseline
- 00**Start with a healthy VM**: Demonstrate how to establish a baseline using `uptime`, `free -h`, and `top`. Capture this initial state.
2.  **Introduce a problem**: Intentionally start a CPU-intensive process (e.g., a `while true` loop) or a memory-consuming script.
3.  **Diagnose the issue**: Use `top` or `ps` to identify the problematic process. Show how `systemctl status` and `journalctl -u` can be used if it were a failing service.
4.  **Correlate findings**: Compare the output of `top`, `free`, `vmstat`, and `ps` side-by-side to build a complete picture of the system's state under load.
5.  **File Permissions Demo**: Create a file, show its default permissions with `ls -l`. Use `chmod` to make it executable and `chown` to change its owner.
6.  **Final Report**: Guide students to script the collection of these metrics into a single, readable report as their assignmend
- 02:10 to 02:40: Command drill on file/process inspection
- **Confusing Load Average with CPU Utilization**: Explain that load average includes processes in the run queue (waiting for CPU) and in uninterruptible sleep, not just active CPU usage.
- **Misinterpreting `free` command output**: Clarify the difference between `used` memory and `available` memory, highlighting the role of buffers and cache.
- **Permission Denied**: Troubleshoot `EACCES` errors by checking file/directory permissions (`ls -l`) and ownership (`chown`/`chmod`).
- **Command Not Found**: Explain the role of the `$PATH` environment variable and how the shell locates executables.
- **Over-reliance on a single tool**: Emphasize the need to use multiple commands (`top`, `vmstat`, `ps`) to get a holistic view of system performance.

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
