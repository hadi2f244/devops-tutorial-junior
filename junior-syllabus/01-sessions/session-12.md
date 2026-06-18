# Session 12 - Week 6

## Topic
Final Swarm Orchestration, Basic Monitoring, End-to-End Demo, Next Steps

Course specification, editorial standard, and format reference:


## Session Summary

This session marks the end of the Junior path: a final deployment, health check, rollback practice, and a minimal review of observability. The goal is for the student to be able to explain and execute an end-to-end operational path.

## Technical Topics to be Covered

- Final deployment with Swarm
- Rollback and recovery
- Health verification and smoke tests
- Basic introduction to metrics/logs/signals

## Key Commands

- docker swarm init/join
- docker node ls, docker service ls/ps/logs/update/rollback
- docker stack deploy/rm
- curl for smoke tests

## Practical Scenario

The process from commit to deployment on Swarm is executed, the app's connection to the DB is checked, the health endpoint and logs are reviewed, and finally, the rollback runbook is completed.

## LPIC-like Mapping

- This session does not have a direct LPIC equivalent and is seen as transition planning.

## References for this Session

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
- Rubric: 35% end-to-end correctness, 25% operability, 20% monitoring clarity, 20% presentation

## Suggested Supplementary Content

- Add a simple SLI/SLO for a key endpoint
- Introduce a minimum incident timeline template
- Out-of-scope (Junior): production-grade multi-cluster observability

## Detailed Learning Objectives

- The student can execute the final demo from commit to deployment.
- Document the operational rollback and recovery path.
- Understand the basic concepts of observability for the next stage (K8s).

## Detailed Agenda (180 minutes)

- 00:00 to 00:25: Recap of the final project architecture
- 00:25 to 01:00: Deployment on Swarm and health verification
- 01:00 to 01:20: Rollback strategy and practice
- 01:20 to 01:30: Break
- 01:30 to 02:10: Observability basics (metrics/logs/signals)
- 02:10 to 02:45: Team demo
- 02:45 to 03:00: Retrospective + next step roadmap

## Step-by-step Teaching Path

1. Perform a standard deployment with a stack.
2. Create a controlled failure and test the rollback.
3. Review the health endpoint and logs to confirm service status.
4. Define the next migration path to Kubernetes.

## Common Errors to Cover

- Not having acceptance criteria before deployment
- Rolling back without real testing
- Observability with only raw logs and no metrics

## Expanded Web References

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
