# Session 09 - Week 5

## Topic
Docker Fundamentals, Multi-Stage Builds, Cache Optimization, Container Security

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session examines Docker from the perspective of image design and runtime security. The student should be able to write an optimized Dockerfile, improve the cache, and run the application as a non-root user.

## Technical Topics to be Covered

- Image layers and build cache
- Multi-stage build
- Reducing image size
- Running a container with a non-root user

## Key Commands

- docker version, docker info, docker build
- docker build --target, docker image ls, docker history
- docker run, docker exec, docker logs, docker inspect, docker stats
- docker system df/prune

## Practical Scenario

An old Dockerfile is rewritten, a multi-stage build is implemented, and the difference in size and build time before and after optimization is recorded.

## LPIC-like Mapping

- This session does not have a direct LPIC equivalent and falls into the containers baseline area.

## References for this Session

- Official: https://docs.docker.com/get-started/
- Official: https://docs.docker.com/build/building/multi-stage/
- Official: https://docs.docker.com/build/cache/
- Official: https://docs.docker.com/engine/security/
- Blog: https://www.docker.com/blog/
- Blog: https://www.digitalocean.com/community/tags/docker

## Assignment and Rubric

- Assignment: rewrite Dockerfile with multi-stage and non-root execution
- Artifact: homework/session-09/Dockerfile + benchmark.md + security-notes.md
- Rubric: 35% build correctness, 25% optimization, 25% security, 15% explanation

## Suggested Supplementary Content

- Introduce a baseline image scanning (trivy/grype)
- Introduce a simple policy for base image update cadence
- Out-of-scope (Junior): hardened distroless pipelines at high scale

## Detailed Learning Objectives

- The student will write an optimized and maintainable Dockerfile.
- Measure the impact of build cache and layer ordering.
- Apply basic container runtime security with non-root and image minimization.

## Detailed Agenda (180 minutes)

- 00:00 to 00:25: Container model and image layering
- 00:25 to 01:00: Dockerfile anti-patterns
- 01:00 to 01:20: Multi-stage design
- 01:20 to 01:30: Break
- 01:30 to 02:10: Cache optimization lab
- 02:10 to 02:40: Security hardening baseline
- 02:40 to 03:00: Benchmark discussion

## Step-by-step Teaching Path

1. Run the initial Dockerfile with common weaknesses.
2. Replace it with a multi-stage version and compare image sizes.
3. Apply a non-root user and a minimal package set.
4. Record build time and image size numerically.

## Common Errors to Cover

- Copying the entire source before dependency installation
- Not having a .dockerignore file
- Running the app as root

## Expanded Web References

### Official

- https://docs.docker.com/get-started/
- https://docs.docker.com/build/building/multi-stage/
- https://docs.docker.com/build/cache/
- https://docs.docker.com/engine/security/
- https://docs.docker.com/reference/cli/docker/buildx/build/

### Practical / Blogs

- https://www.docker.com/blog/
- https://www.digitalocean.com/community/tags/docker

### Extension

- https://docs.docker.com/scout/
