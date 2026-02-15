# CCBP Governance Ledger Adapter

A PowerShell 5.1–compatible adapter that emits **append-only compliance events** to a local ledger (JSONL + optional CSV),
with an **Enterprise dial** that can route events to external sinks via a router stub.

## What this repo contains
- \governance/adapter/Ledger-Adapter.ps1\ — core event writer (LIGHT + ENTERPRISE modes)
- \governance/adapter/Invoke-EnterpriseSinks.ps1\ — enterprise router (safe-by-default outbox stub)
- \schemas/ledger_event.schema.json\ — event schema
- \governance/docs/SETTINGS_SCHEMA.md\ — settings schema used by the adapter

## Quick start (LIGHT)
1) Copy \examples/light/governance.settings.json\ into your target repo at:
   - \governance/governance.settings.json\
2) Run:
\\\powershell
.\governance\adapter\Ledger-Adapter.ps1 -Scope SIM -EventType CUSTOM -CrPath "changes/CR-0001" -StructureHashSha256 "TEST"
\\\

## Enterprise dial
Set \governance_mode\ to \ENTERPRISE\. The adapter will call:
- \governance/adapter/Invoke-EnterpriseSinks.ps1\
By default it writes a local outbox file (offline-safe).

## Versioning
See \VERSION.txt\.
