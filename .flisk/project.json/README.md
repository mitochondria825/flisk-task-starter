# Flisk Task Starter: Distributed Voting App

A multi-service distributed voting application ported from a legacy Docker Compose setup to modern local orchestration using **Flisk** (`flisk up`).

---

## Architecture Overview

The application consists of 5 microservices communicating across local boundaries:

* **Voting Frontend (`vote/`):** Python / Flask client allowing users to cast votes.
* **In-Memory Message Broker (`redis/`):** Transient queue holding votes for asynchronous processing.
* **Processing Worker (`worker/`):** .NET background service consuming queued votes from Redis and persisting aggregated results to PostgreSQL.
* **Persistent Storage (`db/`):** PostgreSQL database storing normalized vote tallies.
* **Results Frontend (`result/`):** Node.js / Express application rendering real-time results via WebSockets.

[ User Browser ]
│
▼
[ vote (Python) ] ──► [ redis ] ──► [ worker (.NET) ] ──► [ db (Postgres) ]
▲
│
[ User Browser ] ◄────────────────────────────── [ result (Node.js) ]


---

## Quickstart: How to Run with `flisk up`

### Prerequisites
* Docker Desktop or compatible container runtime
* Node.js (v18+)

### 1. Clone the Fork
```bash
git clone [https://github.com/flisk-candidate/flisk-task-starter.git](https://github.com/flisk-candidate/flisk-task-starter.git)
cd flisk-task-starter


### 4. Cross-Platform Runtime Constraints (Windows vs. WSL2)
* **Challenge:** Running `flisk up` directly in a native Windows Command Prompt fails with:
  `❌ Landscape startup needs Ubuntu on WSL2. Native Windows runs only services that declare a command, as local processes.`
  Native Windows shells lack direct socket integration for the Linux container landscape that Tilt and Flisk orchestrate.
* **Resolution:** Documented the developer runtime requirement clearly: Windows engineers must execute Flisk workflows inside a WSL2 Ubuntu distribution rather than standard CMD/PowerShell, ensuring consistent container networking across developer machines.