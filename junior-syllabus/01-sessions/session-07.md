# Session 07 - Week 4

## Topic
Ansible Project Structure, Inventory, Jinja2, Playbook Testing

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session introduces Ansible as a configuration management tool. The focus is on project structure, inventory, role design, and templating with Jinja2, so that the student can design a clean and scalable automation project.

## Technical Topics to be Covered

- Control node, inventory, managed node
- Project structure for multi-env
- Role-based design
- Jinja2 and precedence rules
- Linting and initial testing

## Key Commands

- ansible --version, ansible all -m ping
- ansible-inventory --list, ansible-playbook
- ansible-config dump, ansible-doc, ansible-galaxy
- ansible-lint, molecule test

## Practical Scenario

An Ansible project is created with dev/stage/prod environments, roles are separated, and a Jinja2-based template is rendered for a web service.

## LPIC-like Mapping

- This session does not have a direct LPIC equivalent and falls more into the Associate-level automation domain.

## References for this Session

- Official: https://docs.ansible.com/ansible/latest/getting_started/index.html
- Official: https://docs.ansible.com/ansible/latest/playbook_guide/index.html
- Official: https://docs.ansible.com/ansible/latest/inventory_guide/index.html
- Official: https://docs.ansible.com/ansible/latest/reference_appendices/general_precedence.html
- Blog: https://www.ansible.com/blog
- Blog: https://www.redhat.com/en/blog/channel/management-and-automation

## Assignment and Rubric

- Assignment: role-based ansible project tree + executable site.yml
- Artifact: homework/session-07/site.yml + roles/ + group_vars/
- Rubric: 35% architecture, 30% playbook correctness, 20% readability, 15% testability

## Suggested Supplementary Content

- Add host pattern design for partial deploys
- Examine practical idempotency by running a playbook repeatedly
- Out-of-scope (Junior): custom module development

## Detailed Learning Objectives

- The student can design an Ansible project architecture for multiple environments.
- Manage idempotency and precedence in a real playbook.
- Control automation quality with initial linting/testing.

## Detailed Agenda (180 minutes)

- 00:00 to 00:20: Ansible mental model (control/inventory/managed)
- 00:20 to 01:00: Project structure at small to medium scale
- 01:00 to 01:20: Jinja2 and variable precedence
- 01:20 to 01:30: Break
- 01:30 to 02:10: Modules, roles, tags, limits
- 02:10 to 02:40: Lint + molecule test intro
- 02:40 to 03:00: Review and refactor

## Step-by-step Teaching Path

1. Create a project skeleton with roles and inventory.
2. Render a Jinja template with environment variables.
3. Run the playbook twice and confirm idempotency.
4. Convert lint warnings into a team policy.

## Common Errors to Cover

- Hardcoding variables inside tasks
- Ignoring precedence rules
- Running a playbook without check/diff in a sensitive environment

## Expanded Web References

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
