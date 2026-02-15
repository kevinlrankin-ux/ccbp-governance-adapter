# CLP (Constitutional Language Protocol) – Compliance Definition

CLP exists to keep governance automation safe, auditable, and consistent across repos.

## Minimum CLP requirements for this repo
1) PowerShell compatibility
- Scripts must run in Windows PowerShell 5.1 (no PS7-only syntax like `??`, `?:`, etc.)

2) StrictMode safety
- Repos may use `Set-StrictMode -Version Latest`
- Missing JSON properties must not cause crashes: use PSObject property checks (e.g., `.PSObject.Properties["name"]`)

3) Governance integrity
- Do not remove, bypass, or silently disable governance controls intended to preserve:
  - append-only event logging
  - SIM vs REAL separation gates
  - deterministic structure hashing

4) No secret storage
- Do not store credentials, tokens, or secrets in the repo.
- Enterprise sinks must be safe-by-default and offline unless explicitly enabled.

## What “CLP-Compliant Use” means
Using or distributing this Software while meeting the requirements above.
