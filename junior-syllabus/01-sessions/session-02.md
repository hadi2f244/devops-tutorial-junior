# Session 02 - Week 1

## Topic
Linux Storage, Filesystems, LVM, Inode, Users and Least Privilege

مرجع مشخصات دوره، استاندارد نگارشی و قالب:

## خلاصه جلسه

این جلسه روی storage lifecycle در Linux تمرکز دارد: از شناسایی block device تا ساخت filesystem، مدیریت LVM، بررسی inode و اعمال least privilege. هدف فقط آشنایی با فرمان‌ها نیست؛ دانشجو باید بفهمد در چه موقعیتی Ext4 بهتر است و چه زمانی XFS یا LVM به کار می‌آید.

## موضوعات فنی که باید پوشش داده شود

- partitioning و تشخیص دیسک با lsblk و blkid
- تفاوت Ext4 و XFS برای data volume
- ساخت PV/VG/LV و resize کردن آن
- inode behavior و نشانه‌های exhaustion
- user, sudoers و ACL برای least privilege

## دستورات کلیدی

- lsblk, blkid, fdisk -l, parted -l
- mkfs.ext4, mkfs.xfs, mount, umount, findmnt
- df -hT, pvs, vgs, lvs, pvcreate, vgcreate, lvcreate, lvextend
- xfs_growfs, resize2fs, ls -i, stat
- useradd, usermod, visudo, sudo -l, getfacl, setfacl

## سناریوی عملی

یک disk جدید به VM اضافه می‌شود، روی آن LVM ساخته می‌شود، filesystem مناسب انتخاب می‌شود، mount دائمی از طریق fstab اعمال می‌شود و در نهایت با ACL دسترسی یک گروه محدود می‌گردد. این سناریو باید همراه با توضیح علت انتخاب‌ها اجرا شود.

## نگاشت LPIC-like

- 104.x: partitions, filesystems, mounting, permissions
- 102.x: user administration
- 107.x: security basics

## رفرنس‌های این جلسه

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
- Rubric: 35% storage correctness، 25% security، 25% troubleshooting، 15% documentation

## محتوای تکمیلی پیشنهادی

- افزودن سناریوی inode exhaustion با فایل کوچک زیاد
- بررسی خطرات NOPASSWD و pattern امن برای sudoers.d
- Out-of-scope (Junior): RAID tuning و advanced filesystem benchmark

## اهداف یادگیری تفصیلی

- دانشجو بتواند lifecycle کامل PV -> VG -> LV را اجرا و troubleshoot کند.
- برای workloadهای متفاوت انتخاب Ext4 یا XFS را توجیه کند.
- سیاست least privilege را با sudoers و ACL پیاده کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:25: storage map و block device شناخت
- 00:25 تا 01:05: partitioning و filesystem creation
- 01:05 تا 01:20: inode behavior و failure modes
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: LVM عملی از صفر
- 02:10 تا 02:40: sudoers + ACL policy lab
- 02:40 تا 03:00: جمع بندی و ارزیابی سناریو محور

## مسیر تدریس مرحله ای

1. دیسک خام اضافه شود و با lsblk/blkid وضعیت اولیه ثبت شود.
2. یک LV ساخته و mount دائمی از طریق fstab اعمال شود.
3. با ایجاد فایل های کوچک زیاد، inode pressure شبیه سازی شود.
4. دسترسی یک تیم فرضی با ACL و sudo policy محدود شود.

## خطاهای رایج که باید حتما پوشش داده شود

- ادیت مستقیم sudoers بدون visudo
- mount شدن دستی بدون persist در fstab
- عدم تست rollback بعد از تغییرات storage

## رفرنس های تکمیلی وب (Expanded)

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
