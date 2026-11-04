# Flisk Task Starter

A distributed microservice application configured for local landscape orchestration with Flisk.

## Quickstart

Run the single command below to launch the entire multi-service stack:

```bash
flisk up
Once running, access the vote client on http://vote.localhost and real-time tally on http://result.localhost.
What was hard
Migrating from the legacy docker-compose setup to individual Flisk service definitions introduced inter-service startup race conditions between the .NET worker, Redis queue, and Postgres backend.
Resolving these lifecycle dependencies required declaring explicit dependency mappings across services so workers wait until backend ports are healthy.
Additionally, running container landscapes on native Windows surfaces OS virtualization constraints that require WSL2 Ubuntu for container socket communication.
---

### Step 3: Create `ROADMAP.md` (40 Points)

The entire Product section (40 points) requires a file in the root directory named **`ROADMAP.md`**[cite: 1]. 
It has very strict automated rules:
* `## Vision` header with 20+ words[cite: 1]
* `## Next 6 months` header containing an ICE table[cite: 1]
* The table must have 3 rows scored with `Impact`, `Confidence`, `Ease`, and `ICE` (`Impact × Confidence × Ease`), sorted highest first[cite: 1]
* Every row must have a column with a real `Number to watch` (a measurable metric)[cite: 1]
* `## Not now` header with a clear reason of 8+ words[cite: 1]

Click **Add file > Create new file**, name it **`ROADMAP.md`**, paste this exact content, and commit:

```markdown
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