# Session 06 - Week 3

## Topic
Git and Gitflow: Branching, Rebase/Merge, Recovery

مرجع مشخصات دوره، استاندارد نگارشی و قالب:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## خلاصه جلسه

این جلسه Git را از زاویه workflow تیمی و بازیابی خطاها بررسی می‌کند. دانشجو باید branch strategy مناسب، تفاوت merge و rebase، و مسیر recovery با reflog و reset را به‌صورت عملی بفهمد.

## موضوعات فنی که باید پوشش داده شود

- commit graph و branch design
- merge vs rebase
- conflict resolution
- recovery با reflog, reset, restore

## دستورات کلیدی

- git init, git clone, git status, git add, git commit
- git log --oneline --graph, git branch, git switch, git merge, git rebase
- git cherry-pick, git stash, git fetch, git pull --rebase, git push
- git reflog, git reset --soft/mixed, git restore

## سناریوی عملی

یک repo تیمی با feature، release و hotfix branch ساخته می‌شود، conflict واقعی ایجاد و حل می‌گردد، و در نهایت یک اشتباه destructive با reflog recover می‌شود.

## نگاشت LPIC-like

- این جلسه LPIC مستقیم ندارد، اما prerequisite مهم برای workflowهای CI/CD است.

## رفرنس‌های این جلسه

- Official: https://git-scm.com/docs
- Official: https://git-scm.com/book/en/v2
- Official: https://git-scm.com/docs/git-rebase
- Blog: https://www.atlassian.com/git/tutorials
- Blog: https://github.blog/
- Workflow: https://git-scm.com/docs/gitworkflows

## Assignment and Rubric

- Assignment: complete workflow from feature to release + PR template
- Artifact: homework/session-06/gitflow-demo.md + conflict-resolution.md
- Rubric: 40% workflow correctness، 25% conflict handling، 20% commit history quality، 15% docs

## محتوای تکمیلی پیشنهادی

- اضافه کردن Conventional Commits برای خوانایی تاریخچه
- افزودن protected branch policy در remote
- Out-of-scope (Junior): mono-repo scale workflows

## اهداف یادگیری تفصیلی

- دانشجو بتواند branch strategy ساده اما قابل نگهداری طراحی کند.
- تفاوت merge و rebase را بر اساس traceability و readability تحلیل کند.
- با reflog/reset/restore خطاهای رایج را recover کند.

## Agenda تفصیلی (180 دقیقه)

- 00:00 تا 00:20: چرا Git در DevOps مهم است
- 00:20 تا 01:00: object model و commit graph
- 01:00 تا 01:20: merge vs rebase در سناریوی واقعی
- 01:20 تا 01:30: استراحت
- 01:30 تا 02:10: conflict resolution lab
- 02:10 تا 02:40: recovery با reflog/reset/restore
- 02:40 تا 03:00: flow نهایی feature -> release

## مسیر تدریس مرحله ای

1. یک repo مشترک با چند branch بسازید.
2. conflict عمدی ایجاد و مسیر حل صحیح تمرین شود.
3. یک اشتباه destructive را با reflog recover کنید.
4. policy حداقلی commit/branch برای تیم تعریف کنید.

## خطاهای رایج که باید حتما پوشش داده شود

- force push بدون هماهنگی تیمی
- rebase روی branch shared بدون اعلان
- commit های بزرگ و بدون پیام معنادار

## رفرنس های تکمیلی وب (Expanded)

### Official

- https://git-scm.com/docs
- https://git-scm.com/book/en/v2
- https://git-scm.com/docs/git-rebase
- https://git-scm.com/docs/git-merge
- https://git-scm.com/docs/git-reflog

### Practical / Blogs

- https://www.atlassian.com/git/tutorials
- https://github.blog/

### Workflow / Exam-style

- https://git-scm.com/docs/gitworkflows
