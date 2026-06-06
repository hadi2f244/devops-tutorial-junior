# Session 08 - Week 4

## Topic
Ansible Vault, Galaxy Dependencies, Multi-Environment Deployment

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه روی امنیت اتوماسیون تمرکز دارد: Vault، dependency pinning، و deployment چند محیطی. دانشجو باید بفهمد secret باید جدا از کد نگهداری شود و تغییرات محیطی باید قابل کنترل باشند.

## موضوعات فنی که باید پوشش داده شود

- ansible-vault و lifecycle secret
- Galaxy dependency management
- pinning نسخه‌ها برای کاهش drift
- deployment جداگانه برای dev و stage

## دستورات کلیدی

- ansible-vault create/edit/view/encrypt/decrypt/rekey
- ansible-galaxy init/install/list
- ansible-playbook -i inventory, --tags, --limit, --check, --diff

## سناریوی عملی

یک سرویس در dev و stage با secret جدا deploy می‌شود و dependencyهای roleها با requirements.yml نسخه‌بندی و تثبیت می‌گردد.

## نگاشت LPIC-like

- این جلسه LPIC مستقیم ندارد و به‌عنوان extension عملی automation + security دیده می‌شود.

## رفرنس‌های این جلسه

- Official: https://docs.ansible.com/ansible/latest/vault_guide/index.html
- Official: https://docs.ansible.com/ansible/latest/galaxy/user_guide.html
- Official: https://docs.ansible.com/ansible/latest/module_plugin_guide/index.html
- Blog: https://www.redhat.com/en/blog/build-security-itops-start-automation
- Blog: https://www.ansible.com/blog
- Extension: https://docs.ansible.com/projects/ansible/devel/porting_guides/porting_guide_12.html

## Assignment and Rubric

- Assignment: multi-env deployment with vault and pinned dependencies
- Artifact: homework/session-08/site.yml + group_vars/ + vault/ + requirements.yml
- Rubric: 35% secret hygiene، 30% env consistency، 20% automation quality، 15% docs

## محتوای تکمیلی پیشنهادی

- اضافه کردن secret rotation checklist
- مقایسه short-lived credential با static secret
- Out-of-scope (Junior): enterprise secrets backends integration

## اهداف یادگیری تفصیلی

- دانشجو secret را از code جدا و lifecycle آن را مدیریت کند.
- dependency pinning را برای کاهش drift پیاده کند.
- deployment چند محیطی را با کنترل تغییرات انجام دهد.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:25: threat model ساده برای secrets
- 00:25 تا 01:00: ansible-vault workflow کامل
- 01:00 تا 01:20: galaxy dependency management
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:15: multi-env deployment design
- 02:15 تا 02:45: drift detection mini-lab
- 02:45 تا 03:00: policy review

## مسیر تدریس مرحله ای

1. secret plain-text را به vault migration کنید.
2. requirements.yml را pin کرده و verify بگیرید.
3. deploy dev و stage با inventory جدا اجرا کنید.
4. یک drift عمدی ایجاد و بازیابی انجام دهید.

## خطاهای رایج که باید حتما پوشش داده شود

- commit شدن vault password یا secret فایل
- dependency بدون version pin
- نبود تفکیک متغیرهای محیطی

## رفرنس های تکمیلی وب (Expanded)

### Official

- https://docs.ansible.com/ansible/latest/vault_guide/index.html
- https://docs.ansible.com/ansible/latest/galaxy/user_guide.html
- https://docs.ansible.com/ansible/latest/module_plugin_guide/index.html
- https://docs.ansible.com/ansible/latest/reference_appendices/config.html

### Practical / Blogs

- https://www.redhat.com/en/blog/build-security-itops-start-automation
- https://www.ansible.com/blog

### Extension

- https://docs.ansible.com/projects/ansible/devel/porting_guides/porting_guide_12.html
