# Session 03 - Week 2

## Topic
systemd, journald, Unit Override, Cron vs Timer vs at

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه رفتار عملی systemd، journald و زمان‌بندی taskها را پوشش می‌دهد. دانشجو باید بتواند سرویس‌ها را مدیریت کند، لاگ‌ها را query کند و بین cron، timer و at بر اساس نیاز واقعی تصمیم بگیرد.

## موضوعات فنی که باید پوشش داده شود

- lifecycle سرویس در systemd
- query کردن log با journalctl
- override کردن unit file
- تفاوت cron، timer و at

## دستورات کلیدی

- systemctl status/start/stop/restart/reload/enable/disable
- systemctl edit, systemctl daemon-reload, systemctl list-timers
- journalctl -u, journalctl -b, journalctl --since, journalctl -f
- crontab -e/-l, at, atq, atrm

## سناریوی عملی

یک service سفارشی برای health-check ساخته می‌شود، با timer هر چند دقیقه اجرا می‌شود، خروجی آن در journal ثبت می‌گردد و سپس همان کار با cron هم پیاده‌سازی و مقایسه می‌شود.

## نگاشت LPIC-like

- 101.x: boot/service behavior
- 107.x: scheduled jobs, log inspection

## رفرنس‌های این جلسه

- Official: https://www.freedesktop.org/software/systemd/man/latest/systemd.service.html
- Official: https://www.freedesktop.org/software/systemd/man/latest/systemd.timer.html
- Official: https://www.freedesktop.org/software/systemd/man/latest/journalctl.html
- Blog: https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs
- Blog: https://www.redhat.com/en/blog/systemd-timers
- LPIC-like: https://learning.lpi.org/en/learning-materials/102-500/

## Assignment and Rubric

- Assignment: backup-check.service + backup-check.timer
- Artifact: homework/session-03/backup-check.service + backup-check.timer + README
- Rubric: 40% unit correctness، 30% log inspection، 20% cron-vs-timer reasoning، 10% clarity

## محتوای تکمیلی پیشنهادی

- اضافه کردن journald retention policy و log rotation rationale
- تمرین failure injection با ExecStart عمدی خطادار
- Out-of-scope (Junior): custom target design در سطح multi-service orchestration

## اهداف یادگیری تفصیلی

- دانشجو تفاوت service unit و timer unit را عملی بفهمد.
- بتواند لاگ های systemd را با query زمانی و واحد سرویس تحلیل کند.
- بین cron و timer بر اساس نیاز عملیاتی انتخاب صحیح انجام دهد.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:20: مروری بر init/systemd architecture
- 00:20 تا 01:00: service unit deep dive
- 01:00 تا 01:20: journald query patterns
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:15: طراحی timer و مقایسه با cron/at
- 02:15 تا 02:45: lab عملی backup-check
- 02:45 تا 03:00: postmortem سبک

## مسیر تدریس مرحله ای

1. یک unit ساده ایجاد شود.
2. unit با خطای عمدی اجرا و log path تحلیل شود.
3. همان task با cron و timer پیاده و مقایسه observability انجام شود.
4. خروجی به runbook قابل استفاده در incident تبدیل شود.

## خطاهای رایج که باید حتما پوشش داده شود

- فراموش کردن daemon-reload
- استفاده از timer بدون بررسی timezone و persistent behavior
- نبود health signal در لاگ خروجی task

## رفرنس های تکمیلی وب (Expanded)

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
