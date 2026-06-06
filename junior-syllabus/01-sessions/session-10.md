# Session 10 - Week 5

## Topic
Docker Compose, Volumes/Networks, Swarm Intro

مرجع مشخصات دوره، استاندارد نگارشی و قالب:

## خلاصه جلسه

این جلسه به Docker Compose و Swarm می‌پردازد. دانشجو یاد می‌گیرد چگونه یک stack چندسرویسه را برای local dev و E2E مدیریت کند و سپس همان الگو را در Swarm به‌صورت ساده deploy کند.

## موضوعات فنی که باید پوشش داده شود

- تعریف multi-container application با Compose
- network و volume در Compose
- healthcheck و restart policy
- معرفی Swarm و service model

## دستورات کلیدی

- docker compose up/down/ps/logs/exec/build
- docker network ls/create/inspect
- docker volume ls/create/inspect
- docker swarm init
- docker service create/ls/scale/update
- docker stack deploy

## سناریوی عملی

یک stack شامل app + db + redis با Compose بالا می‌آید، smoke test اجرا می‌شود و سپس نسخه ساده همان workload روی Swarm deploy می‌شود تا تفاوت orchestration دیده شود.

## نگاشت LPIC-like

- این جلسه LPIC مستقیم ندارد و در سطح orchestration intro قرار می‌گیرد.

## رفرنس‌های این جلسه

- Official: https://docs.docker.com/compose/
- Official: https://docs.docker.com/engine/network/
- Official: https://docs.docker.com/engine/storage/volumes/
- Official: https://docs.docker.com/engine/swarm/
- Blog: https://www.docker.com/blog/
- Blog: https://www.digitalocean.com/community/tags/docker

## Assignment and Rubric

- Assignment: compose stack with healthcheck + simple swarm stack
- Artifact: homework/session-10/compose.yaml + stack.yaml + e2e-checklist.md
- Rubric: 35% service wiring، 25% persistence، 25% orchestration understanding، 15% clarity

## محتوای تکمیلی پیشنهادی

- اضافه کردن restart policy و healthcheck tuning
- تمرین fault injection با قطع یکی از سرویس ها
- Out-of-scope (Junior): multi-node overlay network troubleshooting عمیق

## اهداف یادگیری تفصیلی

- دانشجو بتواند یک محیط چندسرویسه local را با Compose پایدار اجرا کند.
- شبکه و volume را برای محیط توسعه/تست درست طراحی کند.
- تفاوت runtime بین Compose و Swarm را در عمل ببیند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:20: compose model و فایل compose.yaml
- 00:20 تا 01:00: services, networks, volumes عمیق
- 01:00 تا 01:20: healthcheck و startup order
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: E2E local lab
- 02:10 تا 02:40: swarm intro و service deploy
- 02:40 تا 03:00: مقایسه و جمع بندی

## مسیر تدریس مرحله ای

1. stack محلی app+db+cache با Compose بالا بیاید.
2. healthcheck و restart policy تنظیم شود.
3. smoke test اجرا و failure شبیه سازی شود.
4. نسخه ساده همان stack روی swarm deploy شود.

## خطاهای رایج که باید حتما پوشش داده شود

- استفاده از depends_on به عنوان تضمین readiness
- نداشتن volume برای stateful service
- expose کردن همه پورت ها بدون نیاز

## رفرنس های تکمیلی وب (Expanded)

### Official

- https://docs.docker.com/compose/
- https://docs.docker.com/reference/compose-file/
- https://docs.docker.com/engine/network/
- https://docs.docker.com/engine/storage/volumes/
- https://docs.docker.com/engine/swarm/

### Practical / Blogs

- https://www.docker.com/blog/
- https://www.digitalocean.com/community/tags/docker

### Extension

- https://docs.docker.com/compose/faq/
- https://docs.docker.com/engine/swarm/key-concepts/
