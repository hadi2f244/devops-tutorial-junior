# 05 — Basic Commands for Inspection and Troubleshooting

## Overview

The command line is the primary interface for operating and diagnosing Linux systems. This file is a **practical reference** for the core commands used in system inspection, log reading, and file system navigation. Each command includes annotated example output so you know exactly what you are reading.

---

## System Identity Commands

### `uname` — Kernel and System Information

```bash
uname -a
# Linux myserver 5.15.0-89-generic #99-Ubuntu SMP Mon Oct  9 18:37:45 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
# │     │        │                  │                                           │
# │     │        │                  └─ Build timestamp                          └─ Architecture
# │     │        └─ Kernel release version
# │     └─ Hostname
# └─ Kernel name
```

| Flag | Output |
|------|--------|
| `uname -s` | Kernel name: `Linux` |
| `uname -r` | Release: `5.15.0-89-generic` |
| `uname -m` | Machine hardware: `x86_64` |
| `uname -n` | Hostname |
| `uname -a` | All of the above |

---

### `hostnamectl` — System Identity and OS Info

```bash
hostnamectl
#  Static hostname: myserver
#        Icon name: computer-vm
#          Chassis: vm
#       Machine ID: a1b2c3d4e5f6...
#          Boot ID: 9f8e7d6c5b4a...
#   Virtualization: vmware
# Operating System: Ubuntu 22.04.2 LTS
#           Kernel: Linux 5.15.0-89-generic
#     Architecture: x86-64
```

```bash
# Change hostname (persistent across reboots)
sudo hostnamectl set-hostname new-hostname
```

---

### `uptime` — Runtime and Load Average

```bash
uptime
# 14:32:16 up 45 days, 3:22,  2 users,  load average: 0.42, 0.38, 0.35
# │         │           │      │          │             │     │     │
# │         │           │      │          │             │     │     └─ 15-min avg
# │         │           │      │          │             │     └─ 5-min avg
# │         │           │      │          │             └─ 1-min avg
# │         │           │      └─ logged in user sessions
# │         │           └─ time up (days, hours:minutes)
# │         └─ system uptime
# └─ current time
```

---

### `dmesg` — Kernel Ring Buffer

The kernel writes all boot messages, hardware events, and driver output to an in-memory ring buffer. `dmesg` reads it.

```bash
dmesg                       # Full buffer (can be thousands of lines)
dmesg | head -30            # First 30 lines — early boot messages
dmesg | tail -20            # Recent events (hardware plug/unplug, errors)
sudo dmesg -T               # With human-readable timestamps
dmesg | grep -i "error\|fail\|warn"   # Scan for problems
dmesg | grep -i "oom"       # OOM kill events
dmesg | grep -i "usb"       # USB device events
```

**Example annotated output**:
```
[    0.000000] Linux version 5.15.0-89-generic ...
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz root=/dev/sda1 ro quiet
[    1.234567] ACPI: BIOS _OSI(Linux) query honored
[    5.678901] EXT4-fs (sda1): mounted filesystem with ordered data mode
[  123.456789] usb 1-2: new high-speed USB device number 3
```

Numbers in brackets are **seconds since boot**.

---

## File System Navigation Commands

### `ls` — List Directory Contents

```bash
ls -lh /var/log
# total 148M
# drwxr-xr-x 2 root   root   4.0K Jun 15 09:00 apt/
# -rw-r--r-- 1 syslog adm    50M  Jun 18 10:22 syslog
# -rw-r----- 1 root   adm    2.1M Jun 18 10:21 auth.log
# │           │ │      │      │    │             │
# │           │ │      │      │    │             └─ filename
# │           │ │      │      │    └─ last modification time
# │           │ │      │      └─ size (human-readable with -h)
# │           │ │      └─ group owner
# │           │ └─ user owner
# │           └─ hard link count
# └─ type + permissions (d=directory, -=file, l=symlink)
```

| Flag | Effect |
|------|--------|
| `-l` | Long format (permissions, owner, size, date) |
| `-h` | Human-readable sizes (K, M, G) |
| `-a` | Show hidden files (starting with `.`) |
| `-t` | Sort by modification time (newest first) |
| `-S` | Sort by file size (largest first) |
| `-R` | Recursive listing |
| `-d` | Show directory itself, not its contents |

---

### `find` — Search for Files

```bash
# Find all .log files under /var/log
find /var/log -name "*.log"

# Find files larger than 100 MB
find / -type f -size +100M 2>/dev/null

# Find files modified in the last 24 hours
find /etc -type f -mtime -1

# Find files owned by a specific user
find /home -user alice

# Find SUID binaries (security audit)
find / -perm /4000 -type f 2>/dev/null

# Find and delete files older than 30 days (careful!)
find /tmp -type f -mtime +30 -delete

# Find and execute a command on results
find /var/log -name "*.log" -exec ls -lh {} \;
```

| Option | Meaning |
|--------|---------|
| `-type f` | Files only |
| `-type d` | Directories only |
| `-name "*.ext"` | Filename pattern (case-sensitive) |
| `-iname "*.ext"` | Filename pattern (case-insensitive) |
| `-mtime -N` | Modified less than N days ago |
| `-mtime +N` | Modified more than N days ago |
| `-size +NM` | Larger than N megabytes |
| `-user USERNAME` | Owned by user |
| `2>/dev/null` | Suppress permission denied errors |

---

### `grep` — Search Text in Files

```bash
# Find lines containing "ERROR" in a file
grep "ERROR" /var/log/syslog

# Case-insensitive search
grep -i "failed" /var/log/auth.log

# Show line numbers with matches
grep -n "CRITICAL" app.log

# Count matching lines
grep -c "ERROR" /var/log/syslog

# Search recursively through all files in a directory
grep -r "TODO" /home/alice/project/

# Invert: show lines that do NOT match
grep -v "INFO" app.log

# Multiple patterns (OR)
grep -E "ERROR|WARN|CRITICAL" /var/log/syslog

# Show N lines of context around each match
grep -A 3 -B 1 "ERROR" app.log   # 3 lines After, 1 line Before

# Search only filenames (list files that match)
grep -l "error" /var/log/*.log
```

| Flag | Effect |
|------|--------|
| `-i` | Case-insensitive |
| `-n` | Show line numbers |
| `-c` | Count matches |
| `-v` | Invert match |
| `-r` | Recursive |
| `-l` | List matching filenames only |
| `-E` | Extended regex (allows `\|`, `+`, `?`) |
| `-A N` | N lines after match |
| `-B N` | N lines before match |
| `-C N` | N lines around match |

---

### `less` — Page Through Large Files

`less` is the standard pager for reading large files without loading the entire file into memory.

```bash
less /var/log/syslog
less +G /var/log/syslog    # Open at end of file
```

**Navigation inside `less`**:

| Key | Action |
|-----|--------|
| `Space` / `f` | Next page |
| `b` | Previous page |
| `g` | Go to beginning |
| `G` | Go to end |
| `/pattern` | Search forward |
| `?pattern` | Search backward |
| `n` | Next match |
| `N` | Previous match |
| `q` | Quit |

---

### `tail` — View End of File / Follow Logs

```bash
tail /var/log/syslog            # Last 10 lines (default)
tail -n 50 /var/log/syslog      # Last 50 lines
tail -f /var/log/syslog         # Follow: print new lines as they are appended
tail -f /var/log/syslog | grep -i "error"   # Live log filtering
```

> `tail -f` is the most common command for **real-time log monitoring**. Press `Ctrl+C` to exit.

---

## Quick Reference Table

| Command | Use Case |
|---------|----------|
| `uname -r` | What kernel version is running? |
| `hostnamectl` | What OS and hostname is this system? |
| `uptime` | How long has it been running and what is the load? |
| `sudo dmesg -T \| tail -30` | What hardware/kernel events happened recently? |
| `ls -lh /path/` | What files are in this directory and how big are they? |
| `find /path -name "*.conf"` | Where are all the config files for X? |
| `grep -r "error" /var/log/` | Is there an error pattern in the logs? |
| `tail -f /var/log/syslog` | Watch the system log in real time |
| `less /var/log/auth.log` | Read through the auth log interactively |

---

## Practical Workflow: First 5 Minutes on a New System

```bash
# 1. Who am I and what system is this?
whoami && hostnamectl

# 2. How long has it been up and what is the load?
uptime

# 3. What kernel?
uname -r

# 4. Any hardware/kernel errors since boot?
sudo dmesg -T | grep -iE "error|fail|warn" | tail -20

# 5. What's running?
ps aux | head -20

# 6. How's memory?
free -h

# 7. Any failed services?
systemctl --failed
```
