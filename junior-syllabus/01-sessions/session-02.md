# Session 02 - Week 1

## Topic
Linux Storage, Filesystems, LVM, Inode, Users and Least Privilege

Course specification, editorial standard, and format reference:

## Session Summary

This session focuses on the storage lifecycle in Linux: from identifying block devices to creating filesystems, managing LVM, examining inodes, and applying the principle of least privilege. The goal is not just to become familiar with commands; the student must understand in which situations Ext4 is better and when XFS or LVM are applicable.

## Technical Topics to be Covered

- Partitioning and disk identification with lsblk and blkid
- Difference between Ext4 and XFS for data volumes
- Creating and resizing PV/VG/LV
- Inode behavior and signs of exhaustion
- User, sudoers, and ACL for least privilege

## Key Commands

- lsblk, blkid, fdisk -l, parted -l
- mkfs.ext4, mkfs.xfs, mount, umount, findmnt
- df -hT, pvs, vgs, lvs, pvcreate, vgcreate, lvcreate, lvextend
- xfs_growfs, resize2fs, ls -i, stat
- useradd, usermod, visudo, sudo -l, getfacl, setfacl

## Practical Scenario

A new disk is added to the VM, LVM is created on it, a suitable filesystem is chosen, it is permanently mounted via fstab, and finally, access for a specific group is restricted using ACLs. This scenario must be executed with an explanation for the choices made.

## LPIC-like Mapping

- 104.x: partitions, filesystems, mounting, permissions
- 102.x: user administration
- 107.x: security basics

## References for this Session

- Official: https://man7.org/linux/man-pages/man8/lsblk.8.html
- Official: https://man7.org/linux/man-pages/man8/lvm.8.html
- Official: https://man7.org/linux/man-pages/man5/fstab.5.html
- Blog: https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux
- Blog: https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-permissions
- LPIC-like: https://learning.lpi.org/en/learning-materials/101-500/
- LPIC-like: https://learning.lpi.org/en/learning-materials/102-500/

## Assignment and Rubric

- Assignment: storage provisioning runbook + least-privilege policy
- Artifact: homework/session-02/storage-lab.md + commands.sh + sudoers-policy.md
- Rubric: 35% storage correctness, 25% security, 25% troubleshooting, 15% documentation

## Suggested Supplementary Content

- Add a scenario for inode exhaustion with many small files
- Review the risks of NOPASSWD and secure patterns for sudoers.d
- Out-of-scope (Junior): RAID tuning and advanced filesystem benchmarking

## Detailed Learning Objectives

- The student can execute and troubleshoot the complete PV -> VG -> LV lifecycle.
- Justify the choice of Ext4 or XFS for different workloads.
- Implement a least privilege policy using sudoers and ACLs.

## Detailed Agenda (180 minutes)

- 00:00 to 00:25: Storage map and block device identification
- 00:25 to 01:05: Partitioning and filesystem creation
- 01:05 to 01:20: Inode behavior and failure modes
- 01:20 to 01:30: Break
- 01:30 to 02:10: Practical LVM from scratch
- 02:10 to 02:40: Sudoers + ACL policy lab
- 02:40 to 03:00: Summary and scenario-based evaluation

## Step-by-step Teaching Path

1. Add a raw disk and record the initial state with lsblk/blkid.
2. Create an LV and apply a permanent mount via fstab.
3. Simulate inode pressure by creating many small files.
4. Restrict access for a hypothetical team using ACLs and a sudo policy.

## Common Errors to Cover

- Editing sudoers directly without visudo
- Manual mounting without persisting in fstab
- Not testing rollback after storage changes

## Expanded Web References

### Official

- https://man7.org/linux/man-pages/man8/lsblk.8.html
- https://man7.org/linux/man-pages/man8/lvm.8.html
- https://man7.org/linux/man-pages/man5/fstab.5.html
- https://man7.org/linux/man-pages/man1/chmod.1.html
- https://man7.org/linux/man-pages/man1/chown.1.html

### Practical / Blogs

- https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux
- https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-permissions
- https://wiki.archlinux.org/title/LVM

### LPIC-like / Exam-style

- https://learning.lpi.org/en/learning-materials/101-500/
- https://learning.lpi.org/en/learning-materials/102-500/
