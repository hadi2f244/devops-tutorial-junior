# Session 07 - Week 4

## Topic
Ansible Project Structure, Inventory, Jinja2, Playbook Testing

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه وارد Ansible به‌عنوان ابزار configuration management می‌شود. تمرکز روی ساختار پروژه، inventory، role design، و templating با Jinja2 است تا دانشجو بتواند یک automation project تمیز و قابل گسترش طراحی کند.

## موضوعات فنی که باید پوشش داده شود

- control node, inventory, managed node
- project structure برای multi-env
- role-based design
- jinja2 و precedence rules
- lint و test اولیه

## دستورات کلیدی

- ansible --version, ansible all -m ping
- ansible-inventory --list, ansible-playbook
- ansible-config dump, ansible-doc, ansible-galaxy
- ansible-lint, molecule test

## سناریوی عملی

یک پروژه Ansible با dev/stage/prod ساخته می‌شود، roleها جدا می‌شوند، و یک template مبتنی بر Jinja2 برای سرویس web رندر می‌گردد.

## نگاشت LPIC-like

- این جلسه LPIC مستقیم ندارد و بیشتر در حوزه automation دوره Associate قرار می‌گیرد.

## رفرنس‌های این جلسه

- Official: https://docs.ansible.com/ansible/latest/getting_started/index.html
- Official: https://docs.ansible.com/ansible/latest/playbook_guide/index.html
- Official: https://docs.ansible.com/ansible/latest/inventory_guide/index.html
- Official: https://docs.ansible.com/ansible/latest/reference_appendices/general_precedence.html
- Blog: https://www.ansible.com/blog
- Blog: https://www.redhat.com/en/blog/channel/management-and-automation

## Assignment and Rubric

- Assignment: role-based ansible project tree + executable site.yml
- Artifact: homework/session-07/site.yml + roles/ + group_vars/
- Rubric: 35% architecture، 30% playbook correctness، 20% readability، 15% testability

## محتوای تکمیلی پیشنهادی

- اضافه کردن host pattern design برای partial deploy
- بررسی idempotency عملی با اجرای تکراری playbook
- Out-of-scope (Junior): custom module development

## اهداف یادگیری تفصیلی

- دانشجو معماری پروژه Ansible را برای چند محیط طراحی کند.
- idempotency و precedence را در playbook واقعی مدیریت کند.
- با lint/test اولیه کیفیت اتوماسیون را کنترل کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:20: model ذهنی Ansible (control/inventory/managed)
- 00:20 تا 01:00: project structure در مقیاس کوچک تا متوسط
- 01:00 تا 01:20: jinja2 و variable precedence
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: modules, roles, tags, limits
- 02:10 تا 02:40: lint + molecule test intro
- 02:40 تا 03:00: review و refactor

## مسیر تدریس مرحله ای

1. skeleton پروژه با role و inventory بسازید.
2. یک template جینجا با variableهای محیطی رندر کنید.
3. playbook را دوبار اجرا و idempotency تایید کنید.
4. lint warningها را به policy تیمی تبدیل کنید.

## خطاهای رایج که باید حتما پوشش داده شود

- hardcode کردن variableها داخل task
- نادیده گرفتن precedence rules
- اجرای playbook بدون check/diff در محیط حساس

## رفرنس های تکمیلی وب (Expanded)

### Official

- https://docs.ansible.com/ansible/latest/getting_started/index.html
- https://docs.ansible.com/ansible/latest/playbook_guide/index.html
- https://docs.ansible.com/ansible/latest/inventory_guide/index.html
- https://docs.ansible.com/ansible/latest/reference_appendices/general_precedence.html
- https://docs.ansible.com/ansible/latest/command_guide/index.html

### Practical / Blogs

- https://www.ansible.com/blog
- https://www.redhat.com/en/blog/channel/management-and-automation

### Extension

- https://docs.ansible.com/ansible/latest/reference_appendices/test_strategies.html
