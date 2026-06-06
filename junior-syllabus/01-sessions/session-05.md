# Session 05 - Week 3

## Topic
Networking for DevOps: L4/L7, DNS, Firewall, SSH Hardening

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه شبکه را از دید DevOps بررسی می‌کند: تشخیص لایه مشکل، تحلیل DNS، بررسی socket state و اعمال firewall و SSH hardening. هدف این است که دانشجو بتواند outageهای ساده شبکه را با ابزارهای استاندارد Linux ریشه‌یابی کند.

## موضوعات فنی که باید پوشش داده شود

- تفاوت L4 و L7 load balancing
- مسیر DNS resolution و service discovery
- تشخیص socket و route state
- firewall policy و SSH hardening

## دستورات کلیدی

- ip addr, ip route, ss -tulpen, ping, traceroute
- dig, nslookup, host, curl -v, nc -zv
- ssh-keygen, ssh-copy-id, ssh -i, ssh -o
- ufw status/allow/deny, iptables -S/-L, nft list ruleset
- tcpdump -i

## سناریوی عملی

دو microservice با DNS-based discovery به هم وصل می‌شوند، سپس policy firewall حداقلی اعمال می‌شود و SSH فقط با key-based auth و source محدود فعال می‌ماند.

## نگاشت LPIC-like

- 109.x: networking fundamentals
- 110.x: security

## رفرنس‌های این جلسه

- Official: https://man7.org/linux/man-pages/man8/ip.8.html
- Official: https://man7.org/linux/man-pages/man8/ss.8.html
- Official: https://man7.org/linux/man-pages/man8/iptables.8.html
- Blog: https://www.cloudflare.com/learning/dns/what-is-dns/
- Blog: https://www.cloudflare.com/learning/dns/dns-server-types/
- Blog: https://www.digitalocean.com/community/tags/networking
- LPIC-like: https://learning.lpi.org/en/learning-materials/102-500/

## Assignment and Rubric

- Assignment: network troubleshooting runbook
- Artifact: homework/session-05/network-runbook.md + commands.log
- Rubric: 35% network accuracy، 30% security controls، 20% troubleshooting path، 15% clarity

## محتوای تکمیلی پیشنهادی

- معرفی TCP handshake و اثر آن روی timeout analysis
- تمرین packet capture کوتاه با tcpdump و تفسیر اولیه
- Out-of-scope (Junior): advanced routing/BGP

## اهداف یادگیری تفصیلی

- دانشجو مسیر عیب یابی شبکه را از L3 تا L7 مرحله بندی کند.
- بتواند مشکلات DNS، route و firewall را تفکیک کند.
- hardening پایه SSH را برای محیط dev/prod اعمال کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:25: L4/L7 و service path
- 00:25 تا 01:05: DNS resolution و service discovery
- 01:05 تا 01:20: ابزار socket/network inspection
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: firewall baseline (ufw/iptables/nft)
- 02:10 تا 02:40: SSH hardening
- 02:40 تا 03:00: lab outage simulation

## مسیر تدریس مرحله ای

1. درخواست failed را با curl بازتولید کنید.
2. با dig/nslookup chain DNS را بررسی کنید.
3. با ss/ip route/socket state مسیر شبکه را تحلیل کنید.
4. با policy firewall حداقلی سرویس را secure کنید.

## خطاهای رایج که باید حتما پوشش داده شود

- استفاده از hostname در ruleهای firewall بدون تثبیت IP
- باز گذاشتن SSH روی password auth
- نداشتن rollback plan برای firewall changes

## رفرنس های تکمیلی وب (Expanded)

### Official

- https://man7.org/linux/man-pages/man8/ip.8.html
- https://man7.org/linux/man-pages/man8/ss.8.html
- https://man7.org/linux/man-pages/man8/iptables.8.html
- https://man7.org/linux/man-pages/man1/dig.1.html
- https://man7.org/linux/man-pages/man8/ssh.8.html

### Practical / Blogs

- https://www.cloudflare.com/learning/dns/what-is-dns/
- https://www.cloudflare.com/learning/dns/dns-server-types/
- https://www.digitalocean.com/community/tags/networking

### LPIC-like / Exam-style

- https://learning.lpi.org/en/learning-materials/102-500/
