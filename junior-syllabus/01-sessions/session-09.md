# Session 09 - Week 5

## Topic
Docker Fundamentals, Multi-Stage Builds, Cache Optimization, Container Security

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه Docker را از نگاه image design و runtime security بررسی می‌کند. دانشجو باید بتواند Dockerfile بهینه بنویسد، cache را بهتر کند و برنامه را به‌صورت non-root اجرا کند.

## موضوعات فنی که باید پوشش داده شود

- image layers و build cache
- multi-stage build
- کاهش اندازه image
- اجرای container با user غیر root

## دستورات کلیدی

- docker version, docker info, docker build
- docker build --target, docker image ls, docker history
- docker run, docker exec, docker logs, docker inspect, docker stats
- docker system df/prune

## سناریوی عملی

یک Dockerfile قدیمی بازنویسی می‌شود، build چندمرحله‌ای می‌گیرد، و تفاوت size و زمان build قبل و بعد از optimization ثبت می‌شود.

## نگاشت LPIC-like

- این جلسه LPIC مستقیم ندارد و در حوزه containers baseline قرار می‌گیرد.

## رفرنس‌های این جلسه

- Official: https://docs.docker.com/get-started/
- Official: https://docs.docker.com/build/building/multi-stage/
- Official: https://docs.docker.com/build/cache/
- Official: https://docs.docker.com/engine/security/
- Blog: https://www.docker.com/blog/
- Blog: https://www.digitalocean.com/community/tags/docker

## Assignment and Rubric

- Assignment: rewrite Dockerfile with multi-stage and non-root execution
- Artifact: homework/session-09/Dockerfile + benchmark.md + security-notes.md
- Rubric: 35% build correctness، 25% optimization، 25% security، 15% explanation

## محتوای تکمیلی پیشنهادی

- معرفی image scanning baseline (trivy/grype)
- معرفی policy ساده برای base image update cadence
- Out-of-scope (Junior): hardened distroless pipelines در scale بالا

## اهداف یادگیری تفصیلی

- دانشجو Dockerfile بهینه و قابل نگهداری بنویسد.
- تاثیر build cache و layer ordering را اندازه گیری کند.
- امنیت پایه container runtime را با non-root و کمینه سازی image اعمال کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:25: container model و image layering
- 00:25 تا 01:00: Dockerfile anti-patterns
- 01:00 تا 01:20: multi-stage design
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: cache optimization lab
- 02:10 تا 02:40: security hardening baseline
- 02:40 تا 03:00: benchmark discussion

## مسیر تدریس مرحله ای

1. Dockerfile اولیه با ضعف های متداول اجرا شود.
2. نسخه multi-stage جایگزین و اندازه image مقایسه شود.
3. user غیر root و minimum package set اعمال شود.
4. build time و image size به صورت عددی ثبت شود.

## خطاهای رایج که باید حتما پوشش داده شود

- کپی کردن کل source قبل از dependency install
- نداشتن .dockerignore
- اجرای app با root

## رفرنس های تکمیلی وب (Expanded)

### Official

- https://docs.docker.com/get-started/
- https://docs.docker.com/build/building/multi-stage/
- https://docs.docker.com/build/cache/
- https://docs.docker.com/engine/security/
- https://docs.docker.com/reference/cli/docker/buildx/build/

### Practical / Blogs

- https://www.docker.com/blog/
- https://www.digitalocean.com/community/tags/docker

### Extension

- https://docs.docker.com/scout/
