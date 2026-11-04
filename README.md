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

