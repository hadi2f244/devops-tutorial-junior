# Session 01 - Week 1

## Topic
Linux Fundamentals: Boot Process, systemd Targets, Resource Baseline

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه پایه ورود به Linux در مسیر DevOps است. دانشجو با boot flow از BIOS/UEFI تا PID1 آشنا می‌شود، فرق runlevel و systemd target را می‌فهمد، و یاد می‌گیرد چگونه با command line یک baseline عملیاتی از سیستم بگیرد. تمرکز جلسه روی تحلیل وضعیت سیستم از نگاه یک operator است، نه صرفا حفظ چند command.

## موضوعات فنی که باید پوشش داده شود

- مسیر بوت Linux و نقش bootloader و systemd
- targetهای رایج مثل multi-user.target و graphical.target
- تحلیل اولیه CPU، RAM، load و processها
- commandهای پایه برای inspection و troubleshooting

## دستورات کلیدی

- uname, hostnamectl, uptime
- systemctl get-default, systemctl list-units --type=target, systemctl isolate
- journalctl -b
- top, free -h, vmstat
- ps aux --sort=-%cpu, ps aux --sort=-%mem
- ls, find, grep, less, tail

## سناریوی عملی

دانشجو باید یک baseline report بسازد که شامل kernel version، load average، وضعیت حافظه، top processها و یک تفسیر کوتاه از bottleneck باشد. این خروجی باید به شکل artifact قابل تحویل در Git ذخیره شود.

## نگاشت LPIC-like

- 101.x: system architecture + boot process
- 103.x: GNU/Linux commands
- 108.x: process basics

## رفرنس‌های این جلسه

- Official: https://www.freedesktop.org/software/systemd/man/latest/systemctl.html
- Official: https://www.freedesktop.org/software/systemd/man/latest/journalctl.html
- Official: https://www.gnu.org/software/coreutils/manual/coreutils.html
- Blog: https://www.digitalocean.com/community/tags/linux
- Blog: https://www.redhat.com/en/blog/channel/infrastructure
- LPIC-like: https://www.lpi.org/our-certifications/lpic-1-overview/
- LPIC-like: https://learning.lpi.org/en/learning-materials/101-500/

## Assignment and Rubric

- Assignment: اسکریپت system-report.sh برای snapshot سیستم
- Artifact: homework/session-01/system-report.sh + README + sample-output.txt
- Rubric: 30% مفهومی، 30% تحلیل خروجی، 25% lab، 15% تکلیف

## محتوای تکمیلی پیشنهادی

- اضافه کردن sar/iostat برای baseline روندی
- معرفی quick triage checklist برای incident دقیقه اول
- Out-of-scope (Junior): tuning عمیق kernel scheduler

## اهداف یادگیری تفصیلی

- دانشجو بتواند زنجیره بوت را از firmware تا رسیدن به user space توضیح دهد.
- فرق system state و service state را در systemd تحلیل کند.
- خروجی ابزارهای resource monitoring را به تصمیم عملیاتی تبدیل کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:20: مرور مسیر دوره و تعریف operational baseline
- 00:20 تا 00:55: بوت لینوکس و نقش systemd در startup
- 00:55 تا 01:20: targetها، dependencyها، و حالت rescue
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: CPU/RAM/Load تحلیل عملی
- 02:10 تا 02:40: command drill روی file/process inspection
- 02:40 تا 03:00: lab و پرسش/پاسخ

## مسیر تدریس مرحله ای

1. یک VM سالم را baseline بگیرید.
2. یک سرویس را عمدا fail کنید و از journalctl مسیر تشخیص را نشان دهید.
3. خروجی top/free/ps را کنار هم مقایسه کنید تا correlation دیده شود.
4. خروجی نهایی را در قالب report تحویل بگیرید.

## خطاهای رایج که باید حتما پوشش داده شود

- یکی گرفتن load average با CPU درصدی
- reliance بیش از حد به یک ابزار مانیتورینگ
- نبود timestamp در گزارش های عملیاتی

## رفرنس های تکمیلی وب (Expanded)

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
