# Session 04 - Week 2

## Topic
Production-Ready Bash Scripting, Regex, awk/sed, Error Handling

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه Bash را از سطح command line به سطح script عملیاتی می‌برد. تمرکز روی error handling، parsing، quoting و ساخت اسکریپتی است که در محیط production قابل اعتماد باشد.

## موضوعات فنی که باید پوشش داده شود

- strict mode و trap pattern
- parsing با awk/sed/grep
- quoting، globbing و جلوگیری از word splitting
- طراحی exit code مناسب برای CI و عملیات

## دستورات کلیدی

- bash -n, shellcheck, set -euo pipefail, trap '...' ERR EXIT
- grep -E, awk, sed -E, cut, tr, xargs, tee
- sort, uniq, getopts, [[ ]], case, for/while

## سناریوی عملی

یک script برای اعتبارسنجی backup نوشته می‌شود که log را parse کند، خطاها را دسته‌بندی کند، exit code مناسب برگرداند و report تولید کند.

## نگاشت LPIC-like

- 103.x: text processing tools
- 105.x: shell scripting fundamentals

## رفرنس‌های این جلسه

- Official: https://www.gnu.org/software/bash/manual/bash.html
- Official: https://www.gnu.org/software/gawk/manual/gawk.html
- Official: https://www.gnu.org/software/sed/manual/sed.html
- Blog: https://www.digitalocean.com/community/tutorials/how-to-use-bash-scripting-in-linux
- Blog: https://mywiki.wooledge.org/BashGuide
- LPIC-like: https://learning.lpi.org/en/learning-materials/101-500/

## Assignment and Rubric

- Assignment: script production-ready با test cases
- Artifact: homework/session-04/backup-validator.sh + test-cases.txt + sample-logs/
- Rubric: 35% robustness، 25% readability، 25% parsing correctness، 15% tests

## محتوای تکمیلی پیشنهادی

- افزودن bats-core برای unit test اسکریپت shell
- اضافه کردن قالب استاندارد logging (timestamp + severity)
- Out-of-scope (Junior): توسعه library shell قابل reuse در مقیاس تیمی

## اهداف یادگیری تفصیلی

- دانشجو script قابل اتکا با error handling واقعی بنویسد.
- با quoting/globbing pitfalls آشنا شود و خطاهای رایج را پیشگیری کند.
- برای parsing لاگ از awk/sed/grep در pipeline درست استفاده کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:25: اصول script production-ready
- 00:25 تا 01:05: set -euo pipefail + trap patterns
- 01:05 تا 01:20: regex and quoting pitfalls
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:15: parsing pipeline با awk/sed/grep
- 02:15 تا 02:45: پیاده سازی backup-validator.sh
- 02:45 تا 03:00: code review جمعی

## مسیر تدریس مرحله ای

1. نسخه شکننده script را نشان دهید.
2. همان script با strict mode و trap refactor شود.
3. چند sample log با edge case اضافه و parser robust شود.
4. Exit code contract برای CI تعریف شود.

## خطاهای رایج که باید حتما پوشش داده شود

- word splitting ناخواسته به علت quote نکردن
- اتکا به grep-only برای parsing ساختارمند
- نادیده گرفتن shellcheck warningها

## رفرنس های تکمیلی وب (Expanded)

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
