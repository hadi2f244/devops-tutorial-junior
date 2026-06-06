# Session 12 - Week 6

## Topic
Final Swarm Orchestration, Basic Monitoring, End-to-End Demo, Next Steps

مرجع مشخصات دوره، استاندارد نگارشی و قالب:

 
## خلاصه جلسه

این جلسه پایان مسیر Junior است: یک deploy نهایی، بررسی health، تمرین rollback و مرور حداقلی observability. هدف این است که دانشجو بتواند یک مسیر end-to-end عملیاتی را توضیح و اجرا کند.

## موضوعات فنی که باید پوشش داده شود

- deploy نهایی با Swarm
- rollback و recovery
- health verification و smoke test
- آشنایی اولیه با metrics/logs/signals

## دستورات کلیدی

- docker swarm init/join
- docker node ls, docker service ls/ps/logs/update/rollback
- docker stack deploy/rm
- curl برای smoke test

## سناریوی عملی

از commit تا deploy روی swarm اجرا می‌شود، اتصال app به DB بررسی می‌شود، health endpoint و log مرور می‌شود و در پایان runbook rollback تکمیل می‌گردد.

## نگاشت LPIC-like

- این جلسه LPIC مستقیم ندارد و به‌عنوان transition planning دیده می‌شود.

## رفرنس‌های این جلسه

- Official: https://docs.docker.com/engine/swarm/
- Official: https://docs.docker.com/engine/swarm/services/
- Official: https://docs.docker.com/engine/swarm/stack-deploy/
- Official: https://prometheus.io/docs/introduction/overview/
- Official: https://12factor.net/
- Blog: https://www.cncf.io/blog/
- Blog: https://www.redhat.com/en/blog/channel/management-and-automation
- Blog: https://prometheus.io/blog/

## Assignment and Rubric

- Assignment: team final demo + rollback runbook
- Artifact: homework/session-12/final-demo.md + rollback-runbook.md + architecture-diagram.png
- Rubric: 35% end-to-end correctness، 25% operability، 20% monitoring clarity، 20% presentation

## محتوای تکمیلی پیشنهادی

- اضافه کردن SLI/SLO ساده برای یک endpoint کلیدی
- معرفی minimum incident timeline template
- Out-of-scope (Junior): production-grade multi-cluster observability

## اهداف یادگیری تفصیلی

- دانشجو بتواند demo نهایی را از commit تا deploy اجرا کند.
- rollback عملیاتی و مسیر recovery را مستندسازی کند.
- مفاهیم پایه observability را برای مرحله بعدی (K8s) درک کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:25: recap معماری نهایی پروژه
- 00:25 تا 01:00: deploy روی swarm و health verification
- 01:00 تا 01:20: rollback strategy و تمرین
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: observability basics (metrics/logs/signals)
- 02:10 تا 02:45: team demo
- 02:45 تا 03:00: retrospective + next step roadmap

## مسیر تدریس مرحله ای

1. deploy استاندارد با stack انجام شود.
2. failure کنترل شده ایجاد و rollback تست شود.
3. health endpoint و log review برای تایید سرویس انجام شود.
4. مسیر migration بعدی به Kubernetes تعریف شود.

## خطاهای رایج که باید حتما پوشش داده شود

- نداشتن معیار پذیرش قبل از deploy
- rollback بدون تست واقعی
- observability فقط با log خام و بدون metric

## رفرنس های تکمیلی وب (Expanded)

### Official

- https://docs.docker.com/engine/swarm/
- https://docs.docker.com/engine/swarm/services/
- https://docs.docker.com/engine/swarm/stack-deploy/
- https://prometheus.io/docs/introduction/overview/
- https://12factor.net/

### Practical / Blogs

- https://www.cncf.io/blog/
- https://www.redhat.com/en/blog/channel/management-and-automation
- https://prometheus.io/blog/

### Extension

- https://prometheus.io/docs/introduction/first_steps/
- https://grafana.com/docs/
