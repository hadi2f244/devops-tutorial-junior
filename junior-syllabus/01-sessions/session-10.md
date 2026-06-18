# Session 10 - Week 5

## Topic
Docker Compose, Volumes/Networks, Swarm Intro

Course specification, editorial standard, and format reference:

## Session Summary

This session covers Docker Compose and Swarm. The student will learn how to manage a multi-service stack for local development and E2E testing, and then deploy the same pattern simply in Swarm.

## Technical Topics to be Covered

- Defining a multi-container application with Compose
- Networks and volumes in Compose
- Health checks and restart policies
- Introduction to Swarm and the service model

## Key Commands

- docker compose up/down/ps/logs/exec/build
- docker network ls/create/inspect
- docker volume ls/create/inspect
- docker swarm init
- docker service create/ls/scale/update
- docker stack deploy

## Practical Scenario

A stack including an app, a database, and Redis is brought up with Compose, a smoke test is run, and then a simple version of the same workload is deployed on Swarm to see the difference in orchestration.

## LPIC-like Mapping

- This session does not have a direct LPIC equivalent and is at the orchestration intro level.

## References for this Session

- Official: https://docs.docker.com/compose/
- Official: https://docs.docker.com/engine/network/
- Official: https://docs.docker.com/engine/storage/volumes/
- Official: https://docs.docker.com/engine/swarm/
- Blog: https://www.docker.com/blog/
- Blog: https://www.digitalocean.com/community/tags/docker

## Assignment and Rubric

- Assignment: compose stack with healthcheck + simple swarm stack
- Artifact: homework/session-10/compose.yaml + stack.yaml + e2e-checklist.md
- Rubric: 35% service wiring, 25% persistence, 25% orchestration understanding, 15% clarity

## Suggested Supplementary Content

- Add restart policy and healthcheck tuning
- Practice fault injection by stopping one of the services
- Out-of-scope (Junior): deep multi-node overlay network troubleshooting

## Detailed Learning Objectives

- The student can run a stable multi-service local environment with Compose.
- Design networks and volumes correctly for dev/test environments.
- See the runtime difference between Compose and Swarm in practice.

## Detailed Agenda (180 minutes)

- 00:00 to 00:20: Compose model and the compose.yaml file
- 00:20 to 01:00: Deep dive into services, networks, volumes
- 01:00 to 01:20: Health checks and startup order
- 01:20 to 01:30: Break
- 01:30 to 02:10: E2E local lab
- 02:10 to 02:40: Swarm intro and service deployment
- 02:40 to 03:00: Comparison and summary

## Step-by-step Teaching Path

1. Bring up a local app+db+cache stack with Compose.
2. Configure health checks and restart policies.
3. Run a smoke test and simulate a failure.
4. Deploy a simple version of the same stack on Swarm.

## Common Errors to Cover

- Using depends_on as a guarantee of readiness
- Not having a volume for a stateful service
- Exposing all ports unnecessarily

## Expanded Web References

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
