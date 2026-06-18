# 01 — Linux Structure and Boot Process

## Overview

Linux is a **monolithic kernel** operating system. It manages hardware resources directly from a single kernel binary. Unlike microkernels, most OS functionality (memory management, device drivers, filesystem support) runs in **kernel space** (ring 0), while user applications run in **user space** (ring 3).

The kernel is modular: core functionality is compiled in, while optional features (drivers, filesystems) are loaded at runtime as **kernel modules** (`.ko` files), keeping the base image small.

```
┌──────────────────────────────────────┐
│            User Space                │   Applications, shells, daemons
├──────────────────────────────────────┤
│  System Call Interface (glibc/syscall)│   Bridge between user and kernel
├──────────────────────────────────────┤
│           Kernel Space               │
│   Memory Mgmt │ Process Scheduler    │
│   VFS         │ Device Drivers       │
│   Network     │ Security (SELinux)   │
├──────────────────────────────────────┤
│           Hardware (CPU, RAM, Disk)  │
└──────────────────────────────────────┘
```

---

## Boot Sequence — Full Flowchart

```mermaid
flowchart TD
    A([Power On]) --> B[Firmware\nBIOS / UEFI]
    B --> C{Firmware\nType?}
    C -->|BIOS| D[Read MBR\nSector 0, 446 bytes]
    C -->|UEFI| E[Read EFI System\nPartition /boot/efi]
    D --> F[GRUB2 Stage 1]
    E --> F
    F --> G[GRUB2 Stage 1.5\nFilesystem drivers]
    G --> H[GRUB2 Stage 2\n/boot/grub2/grub.cfg]
    H --> I[Load Kernel Image\n/boot/vmlinuz-*]
    H --> J[Load initramfs\n/boot/initramfs-*.img]
    I --> K[Kernel Decompresses\nand Self-initializes]
    J --> K
    K --> L[Kernel mounts\ninitramfs as tmp root]
    L --> M[/init loads modules\nfor real root fs]
    M --> N[Pivot root to\nreal filesystem]
    N --> O[Kernel exec\n/sbin/init = PID 1]
    O --> P[systemd starts\nand resolves targets]
    P --> Q([User Space Ready])

    style A fill:#2d6a4f,color:#fff
    style Q fill:#2d6a4f,color:#fff
    style O fill:#e76f51,color:#fff
    style P fill:#e76f51,color:#fff
```

---

## Stage 1: Firmware (BIOS / UEFI)

The **firmware** is the first code that runs after power-on. It performs **POST** (Power-On Self-Test) to validate hardware (CPU, RAM, storage), then hands control to the bootloader.

### BIOS vs UEFI

| Aspect | BIOS | UEFI |
|--------|------|------|
| Age | 1980s | 2007+ (standard) |
| Execution mode | 16-bit real mode | 32/64-bit protected mode |
| Max addressable disk | 2.2 TB (MBR/CHS) | 9.4 ZB (GPT) |
| Max partitions | 4 primary (MBR) | 128 (GPT) |
| Security | None | Secure Boot (cryptographic) |
| Config storage | CMOS battery | NVRAM on motherboard |
| Boot partition | First 512 bytes (MBR) | EFI System Partition (ESP) |
| Speed | Slow (sequential probe) | Faster (parallel init) |

**UEFI ESP** (EFI System Partition): A FAT32 partition mounted at `/boot/efi` containing signed bootloader binaries (e.g., `shimx64.efi`, `grubx64.efi`).

```bash
# Inspect UEFI boot entries
sudo efibootmgr -v

# View contents of the ESP
ls -la /boot/efi/EFI/
```

---

## Stage 2: Partition Schemes (MBR vs GPT)

### MBR (Master Boot Record)

Located at **sector 0** of the disk:

```
┌──────────────────────────────────────┐ ← Byte 0
│  Bootstrap Code (446 bytes)          │  Stage 1 bootloader
├──────────────────────────────────────┤ ← Byte 446
│  Partition Table (64 bytes)          │  Max 4 primary partitions
├──────────────────────────────────────┤ ← Byte 510
│  Magic Signature (2 bytes: 0x55AA)   │
└──────────────────────────────────────┘ ← Byte 512
```

**Limitation**: No redundancy. If sector 0 is corrupted, the disk is unbootable.

### GPT (GUID Partition Table)

```
┌───────────────────────┐
│  Protective MBR       │  Sector 0 — legacy compatibility
├───────────────────────┤
│  Primary GPT Header   │  Sector 1 — metadata + CRC32 checksum
├───────────────────────┤
│  Partition Entries    │  Sectors 2–33 — up to 128 partitions
├───────────────────────┤
│  Data Partitions...   │
├───────────────────────┤
│  Secondary GPT Header │  Last sector — backup of primary header
└───────────────────────┘
```

**Advantage**: Self-healing via backup header; CRC32 validates all metadata.

```bash
# Inspect partition table (MBR or GPT)
sudo fdisk -l /dev/sda

# GPT-specific inspection
sudo gdisk -l /dev/sda

# View UUIDs of all partitions
blkid
```

---

## Stage 3: Bootloader (GRUB2)

Covered in detail in `02-bootloader-and-systemd.md`.

---

## Stage 4: Kernel Initialization

Once GRUB2 loads the kernel binary (`vmlinuz`) into RAM and passes control, the kernel:

1. **Decompresses itself** (it is a self-extracting gzip/bzip2 archive)
2. **Switches to protected mode** (64-bit long mode on modern x86)
3. **Initializes the MMU** (Memory Management Unit) — sets up page tables
4. **Detects hardware** via CPUID and ACPI tables
5. **Initializes early console** (VGA / serial) for kernel messages
6. **Mounts initramfs** as the initial root filesystem

**Kernel parameters** are passed from GRUB via the kernel command line:

```bash
# View parameters the running kernel received
cat /proc/cmdline
# Example: BOOT_IMAGE=/vmlinuz-5.15.0 root=/dev/sda1 ro quiet splash

# View early boot kernel messages
dmesg | head -40
sudo dmesg -T | grep -i error
```

---

## Stage 5: initramfs

The **initramfs** (Initial RAM Filesystem) is a compressed CPIO archive loaded alongside the kernel. It contains a minimal Linux environment sufficient to mount the real root filesystem.

**Why it is needed**: The real root filesystem (on `/dev/sda1`, an LVM volume, or an encrypted LUKS device) may require kernel modules (drivers) that are not compiled into the kernel itself. The initramfs bootstraps this process.

```
initramfs contents:
/bin/          — minimal utilities (sh, mount, modprobe)
/lib/modules/  — kernel modules (storage, filesystem drivers)
/etc/          — critical configs (fstab, mdadm.conf)
/init          — the main init script (PID 1 inside initramfs)
```

```bash
# List contents of the initramfs (RHEL/CentOS)
lsinitrd /boot/initramfs-$(uname -r).img

# Rebuild initramfs (RHEL/Fedora)
sudo dracut -f

# Rebuild initramfs (Debian/Ubuntu)
sudo update-initramfs -u
```

---

## Stage 6: PID 1 and User Space

After the kernel pivots to the real root filesystem, it executes `/sbin/init` — the **first user-space process**, always assigned **PID 1**.

- PID 1 is the **ancestor** of all other processes.
- It handles **orphaned processes** (re-parents them when their parent dies).
- It receives `SIGTERM` on graceful shutdown.
- **It cannot be killed** by a regular user — only a reboot terminates it.

On all modern Linux distributions, `/sbin/init` is a symlink to `systemd`.

```bash
# Confirm PID 1
ls -la /proc/1/exe
# lrwxrwxrwx ... /proc/1/exe -> /lib/systemd/systemd

# Confirm /sbin/init symlink
ls -la /sbin/init
# lrwxrwxrwx ... /sbin/init -> /lib/systemd/systemd
```

---

## Key Commands Reference

| Command | Purpose |
|---------|---------|
| `uname -a` | All kernel info: name, hostname, release, version, architecture |
| `uname -r` | Kernel release version only |
| `hostnamectl` | Hostname, OS, kernel version, machine ID |
| `uptime` | System runtime and load average |
| `dmesg` | Kernel ring buffer (boot messages, hardware events) |
| `sudo dmesg -T` | Kernel messages with human-readable timestamps |
| `cat /proc/cmdline` | Kernel boot parameters passed by GRUB |
| `cat /proc/version` | Kernel version and compiler info |
| `efibootmgr -v` | UEFI boot entries (UEFI systems only) |
| `blkid` | UUIDs and filesystem types of all partitions |
| `sudo fdisk -l` | List all disk partition tables |
| `lsinitrd` | List contents of the initramfs image |

### Example: Quick System Identity Check

```bash
uname -r            # 5.15.0-89-generic
hostnamectl         # OS, kernel, architecture
cat /proc/cmdline   # How this kernel was booted
dmesg | grep -i "error\|fail\|warn" | head -20
```

---

## Common Pitfalls

| Mistake | Clarification |
|---------|--------------|
| Editing `/boot/grub2/grub.cfg` directly | This file is auto-generated. Edit `/etc/default/grub` then run `grub2-mkconfig`. |
| Assuming BIOS on all hardware | Check with `ls /sys/firmware/efi` — if the directory exists, the system booted via UEFI. |
| Thinking kernel loads all drivers at boot | Most drivers are modules in initramfs or loaded by systemd-modules-load later. |
| Confusing initrd with initramfs | `initrd` is legacy (loop-mounted disk image). Modern systems use `initramfs` (CPIO archive). |
