# Session 08 - Week 4

## Topic
Ansible Vault, Galaxy Dependencies, Multi-Environment Deployment

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session focuses on automation security: Vault, dependency pinning, and multi-environment deployment. The student must understand that secrets should be kept separate from code and that environmental changes must be controllable.

## Technical Topics to be Covered

- ansible-vault and the secret lifecycle
- Galaxy dependency management
- Pinning versions to reduce drift
- Separate deployment for dev and stage

## Key Commands

- ansible-vault create/edit/view/encrypt/decrypt/rekey
- ansible-galaxy init/install/list
- ansible-playbook -i inventory, --tags, --limit, --check, --diff

## Practical Scenario

A service is deployed in dev and stage with separate secrets, and role dependencies are versioned and pinned with requirements.yml.

## LPIC-like Mapping

- This session does not have a direct LPIC equivalent and is seen as a practical extension of automation + security.

## References for this Session

- Official: https://docs.ansible.com/ansible/latest/vault_guide/index.html
- Official: https://docs.ansible.com/ansible/latest/galaxy/user_guide.html
- Official: https://docs.ansible.com/ansible/latest/module_plugin_guide/index.html
- Blog: https://www.redhat.com/en/blog/build-security-itops-start-automation
- Blog: https://www.ansible.com/blog
- Extension: https://docs.ansible.com/projects/ansible/devel/porting_guides/porting_guide_12.html

## Assignment and Rubric

- Assignment: multi-env deployment with vault and pinned dependencies
- Artifact: homework/session-08/site.yml + group_vars/ + vault/ + requirements.yml
- Rubric: 35% secret hygiene, 30% env consistency, 20% automation quality, 15% docs

## Suggested Supplementary Content

- Add a secret rotation checklist
- Compare short-lived credentials with static secrets
- Out-of-scope (Junior): enterprise secrets backends integration

## Detailed Learning Objectives

- The student will separate secrets from code and manage their lifecycle.
- Implement dependency pinning to reduce drift.
- Perform multi-environment deployments with change control.

## Detailed Agenda (180 minutes)

- 00:00 to 00:25: Simple threat model for secrets
- 00:25 to 01:00: Complete ansible-vault workflow
- 01:00 to 01:20: Galaxy dependency management
- 01:20 to 01:30: Break
- 01:30 to 02:15: Multi-env deployment design
- 02:15 to 02:45: Drift detection mini-lab
- 02:45 to 03:00: Policy review

## Step-by-step Teaching Path

1. Migrate a plain-text secret to a vault.
2. Pin requirements.yml and verify.
3. Run dev and stage deployments with separate inventories.
4. Intentionally create a drift and perform recovery.

## Common Errors to Cover

- Committing vault passwords or secret files
- Dependencies without version pins
- Lack of separation for environment variables

## Expanded Web References

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
