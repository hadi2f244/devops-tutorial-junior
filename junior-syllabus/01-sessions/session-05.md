# Session 05 - Week 3

## Topic
Networking for DevOps: L4/L7, DNS, Firewall, SSH Hardening

Course specification, editorial standard, and format reference:
- ../00-governance/course-metadata.md
- ../00-governance/editorial-standard.md
- ../00-governance/session-template.md

## Session Summary

This session examines networking from a DevOps perspective: identifying the problem layer, analyzing DNS, checking socket state, and applying firewall and SSH hardening. The goal is for the student to be able to root-cause simple network outages with standard Linux tools.

## Technical Topics to be Covered

- Difference between L4 and L7 load balancing
- DNS resolution path and service discovery
- Identifying socket and route state
- Firewall policy and SSH hardening

## Key Commands

- ip addr, ip route, ss -tulpen, ping, traceroute
- dig, nslookup, host, curl -v, nc -zv
- ssh-keygen, ssh-copy-id, ssh -i, ssh -o
- ufw status/allow/deny, iptables -S/-L, nft list ruleset
- tcpdump -i

## Practical Scenario

Two microservices are connected via DNS-based discovery, then a minimal firewall policy is applied, and SSH is kept active only with key-based authentication and a limited source.

## LPIC-like Mapping

- 109.x: networking fundamentals
- 110.x: security

## References for this Session

- Official: https://man7.org/linux/man-pages/man8/ip.8.html
- Official: https://man7.org/linux/man-pages/man8/ss.8.html
- Official: https://man7.org/linux/man-pages/man8/iptables.8.html
- Blog: https://www.cloudflare.com/learning/dns/what-is-dns/
- Blog: https://www.cloudflare.com/learning/dns/dns-server-types/
- Blog: https://www.digitalocean.com/community/tags/networking
- LPIC-like: https://learning.lpi.org/en/learning-materials/102-500/

## Assignment and Rubric

- Assignment: network troubleshooting runbook
- Artifact: homework/session-05/network-runbook.md + commands.log
- Rubric: 35% network accuracy, 30% security controls, 20% troubleshooting path, 15% clarity

## Suggested Supplementary Content

- Introduce the TCP handshake and its effect on timeout analysis
- Practice short packet captures with tcpdump and initial interpretation
- Out-of-scope (Junior): advanced routing/BGP

## Detailed Learning Objectives

- The student can stage the network troubleshooting path from L3 to L7.
- Be able to isolate DNS, route, and firewall problems.
- Apply basic SSH hardening for dev/prod environments.

## Detailed Agenda (180 minutes)

- 00:00 to 00:25: L4/L7 and service path
- 00:25 to 01:05: DNS resolution and service discovery
- 01:05 to 01:20: Socket/network inspection tools
- 01:20 to 01:30: Break
- 01:30 to 02:10: Firewall baseline (ufw/iptables/nft)
- 02:10 to 02:40: SSH hardening
- 02:40 to 03:00: Lab outage simulation

## Step-by-step Teaching Path

1. Reproduce a failed request with curl.
2. Check the DNS chain with dig/nslookup.
3. Analyze the network path with ss/ip route/socket state.
4. Secure the service with a minimal firewall policy.

## Common Errors to Cover

- Using hostnames in firewall rules without fixing the IP
- Leaving SSH open to password authentication
- Not having a rollback plan for firewall changes

## Expanded Web References

### Official

- https://man7.org/linux/man-pages/man8/ip.8.html
- https://man7.org/linux/man-pages/man8/ss.8.html
- https://man7.org/linux/man-pages/man8/iptables.8.html
- https://man7.org/linux/man-pages/man1/dig.1.html
- https://man7.org/linux/man-pages/man8/ssh.8.html

### Practical / Blogs

- https://www.cloudflare.com/learning/dns/what-is-dns/
- https://www.cloudflare.com/learning/dns/dns-server-types/
- https://www.digitalocean.com/community/tags/networking

### LPIC-like / Exam-style

- https://learning.lpi.org/en/learning-materials/102-500/
