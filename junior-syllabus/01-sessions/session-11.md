# Session 11 - Week 6

## Topic
Sample Project Pipeline: Build/Test with Git + Bash + Docker

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه نمونه پروژه نهایی را وارد مرحله CI می‌کند. دانشجو باید pipeline‌ای بسازد که build و test را تفکیک کند، unit و integration test را در جریان اجرا قرار دهد و خروجی قابل گزارش داشته باشد.

## موضوعات فنی که باید پوشش داده شود

- طراحی stageهای build و test
- unit test و integration test
- fail-fast behavior
- reproducible pipeline

## دستورات کلیدی

- git rebase, bash strict mode
- docker build/run
- docker compose -f compose.test.yaml up --abort-on-container-exit
- make test, pytest -q
- coverage tooling

## سناریوی عملی

برای یک data service، pipeline محلی طراحی می‌شود که build و test را جدا کند و failure stageها را واضح گزارش دهد.

## نگاشت LPIC-like

- این جلسه فقط از نظر shell discipline با LPIC-like هم‌پوشانی دارد.

## رفرنس‌های این جلسه

- Official: https://docs.github.com/en/actions
- Official: https://docs.github.com/actions/get-started/quickstart
- Official: https://docs.github.com/actions/get-started/understand-github-actions
- Official: https://docs.gitlab.com/ee/ci/
- Blog: https://martinfowler.com/articles/continuousIntegration.html
- Blog: https://github.blog/category/engineering/

## Assignment and Rubric

- Assignment: local + CI pipeline with minimum 2 stages
- Artifact: homework/session-11/ci-pipeline.yml + compose.test.yaml + test-report.md
- Rubric: 40% pipeline correctness، 25% test quality، 20% reproducibility، 15% reporting

## محتوای تکمیلی پیشنهادی

- افزودن caching strategy برای dependency install
- اضافه کردن basic pipeline badge و quality gate
- Out-of-scope (Junior): matrix builds و progressive delivery

## اهداف یادگیری تفصیلی

- دانشجو pipeline حداقلی build/test را end-to-end پیاده کند.
- فرق unit و integration test را در جریان CI عملیاتی کند.
- fail-fast و reproducible build را در pipeline enforce کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:20: anatomy یک CI pipeline
- 00:20 تا 01:00: build stage design
- 01:00 تا 01:20: test strategy (unit/integration)
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: local CI با compose.test
- 02:10 تا 02:40: workflow روی GitHub Actions یا GitLab CI
- 02:40 تا 03:00: failure analysis

## مسیر تدریس مرحله ای

1. build command deterministic تعریف شود.
2. test stage با خروجی واضح پاس/فیل اجرا شود.
3. یک failure عمدی تزریق و مسیر debug تمرین شود.
4. report نهایی با coverage summary تحویل شود.

## خطاهای رایج که باید حتما پوشش داده شود

- وابستگی به محیط local بدون pin version
- اجرای integration test بدون isolated service
- pipeline کند به علت cache نادرست

## رفرنس های تکمیلی وب (Expanded)

### Official

- https://docs.github.com/en/actions
- https://docs.github.com/actions/get-started/quickstart
- https://docs.github.com/actions/get-started/understand-github-actions
- https://docs.gitlab.com/ee/ci/
- https://docs.docker.com/guides/

### Practical / Blogs

- https://martinfowler.com/articles/continuousIntegration.html
- https://github.blog/category/engineering/

### Extension

- https://docs.github.com/en/actions/how-tos/monitor-workflows/add-a-status-badge
