# Flisk Task Starter

A distributed microservice application configured for local landscape orchestration with Flisk.

## Quickstart

Run the single command below to launch the entire multi-service stack:

```bash
flisk up

---

Once running, access the vote client on http://vote.localhost and real-time tally on http://result.localhost.

---

## What was hard
Migrating from the legacy docker-compose setup to individual Flisk service definitions introduced inter-service startup race conditions between the .NET worker, Redis queue, and Postgres backend.
Resolving these lifecycle dependencies required declaring explicit dependency mappings across services so workers wait until backend ports are healthy.
Additionally, running container landscapes on native Windows surfaces OS virtualization constraints that require WSL2 Ubuntu for container socket communication.
---

# Product Roadmap

## Vision
Flisk empowers software engineering teams to define, run, and scale distributed local microservice environments instantaneously through a unified developer interface, eliminating environment drift and maximizing developer velocity alongside AI development workflows across modern container landscapes.

## Next 6 months

| Priority Item | Impact | Confidence | Ease | ICE | Number to watch |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Pre-flight Environment Diagnostic CLI for Windows and WSL2 | 8 | 9 | 8 | 576 | < 1 minute developer onboarding drop-off rate |
| Automated Health Check Probes and Service Dependency Wait Graphs | 8 | 8 | 7 | 448 | 0 container crash-loop restart incidents on boot |
| Zero-Config Local TLS and Custom Subdomain Routing via Traefik Proxy | 7 | 8 | 7 | 392 | 100% localhost SSL certificate validation rate |

## Not now
Native Windows kernel containerization without WSL2 because maintaining parity across divergent container engines introduces excessive maintenance overhead compared to standardized WSL2 runtimes.