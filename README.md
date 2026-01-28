# Multi-container Sandbox Demo

This repo contains a single Crafting sandbox definition that demonstrates:
- A blank workspace plus two container workloads (MySQL and MinIO)
- Inter-workload networking by service name (e.g. `mysql:3306`, `minio:9000`)
- A simple proof script that writes logs visible in the Crafting UI

## Files
- `demo-multi-container.yaml` — the sandbox definition to use with `cs sandbox create --from def:...`

## What the demo does
When the sandbox starts, it runs a one-time `demo-proof` process that:
1. Connects to MySQL and writes a proof row
2. Connects to MinIO and uploads a proof file
3. Writes logs to `/home/owner/demo-logs/demo.log`

The script includes a guard file (`/home/owner/demo-logs/.demo_done`) so it only runs once per sandbox.

## Quick start
```bash
cs sandbox create demo-mc --from def:demo-multi-container.yaml
```

In the UI, open sandbox `demo-mc`, then:
**Workloads → dev → System process `demo-proof` → Logs**

