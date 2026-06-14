# 🛡️ Arka Sentinel

> **Repository Context Guardrails for Engineering Teams**
>
> Prevent architectural drift, unsafe code paths, and compliance violations before code ever leaves a developer workstation.

---

## Why Arka Sentinel?

Modern software systems accumulate technical debt not because engineers lack skill, but because critical architectural context gets lost over time.

Teams change.

Repositories evolve.

Documentation becomes stale.

Deadlines compress decision-making.

The result is architectural drift, compliance risks, fragile implementations, and expensive defects discovered too late in the delivery pipeline.

Arka Sentinel addresses this problem by acting as a **local-first repository context guardian**, validating changes against repository knowledge before commits are accepted.

---

## Key Principles

### 🔒 Privacy First

Your source code remains on your machine.

- No cloud services
- No source code uploads
- No external LLM calls
- No telemetry requirements
- No recurring AI API costs

### ⚡ Shift Validation Left

Most tooling identifies issues after code reaches CI/CD.

Arka Sentinel evaluates changes during the local commit workflow, helping engineers catch problems before they propagate downstream.

### 🧠 Preserve Architectural Knowledge

Repositories often outlive the engineers who originally designed them.

Arka Sentinel helps preserve and enforce repository conventions, architectural boundaries, and implementation patterns across the software lifecycle.

---

## Core Capabilities

### Repository Context Awareness

Builds an understanding of repository structure, implementation relationships, and historical engineering patterns.

### Architectural Guardrails

Detects:

- Layer violations
- Unsafe implementation shortcuts
- Repository policy violations
- Missing dependency flows
- Architectural bypasses
- Context inconsistencies

### Root Cause Analysis

When a validation fails, Arka Sentinel generates actionable remediation guidance explaining:

- What failed
- Why it failed
- Impact assessment
- Recommended fixes

### Local Audit Trail

Maintains a historical ledger of:

- Validation failures
- Warning events
- Emergency bypass activity
- Repository compliance signals

---

## High-Level Architecture

```text
Developer Changes
        │
        ▼
 Git Pre-Commit Hook
        │
        ▼
 Repository Analysis Engine
        │
        ├── Structural Analysis
        ├── Context Evaluation
        └── Policy Validation
        │
        ▼
 Guardrail Decision Engine
        │
 ┌──────┴────────┐
 │               │
 ▼               ▼
PASS            FAIL
 │               │
 ▼               ▼
Commit        RCA Generated
Allowed       Commit Blocked
```

---

## How It Works

### 1. Repository Initialization

During installation, Arka Sentinel analyzes the local repository and historical Git activity.

This process creates a compressed local context model that serves as the repository's architectural memory.

```bash
./arka-sentinel.exe --install
```

---

### 2. Commit Interception

Whenever a developer runs:

```bash
git commit -m "feature update"
```

Arka Sentinel evaluates staged changes against:

- Repository structure
- Historical implementation patterns
- Configured policies
- Architectural constraints

---

### 3. Validation Decision

The engine determines whether the proposed changes align with repository expectations.

If validation passes:

```text
✓ Commit Approved
```

If validation fails:

```text
🛡️ Validation Fault Detected

Commit Blocked

Review:
.arkasentinel/context_state.md
```

---

## Example

### Problem

A developer bypasses an approved repository abstraction layer.

```python
from database import direct_db_client

def update_user_balance(user_id, amount):
    return direct_db_client.execute(...)
```

### Commit Attempt

```bash
git commit -m "update balance workflow"
```

### Result

```text
[🛡️ Arka Sentinel]

Rule: ARCH-402
Category: Data Layer Isolation Bypass

Commit Blocked
```

### Generated RCA

```markdown
Issue:
Data Layer Isolation Bypass

Affected File:
src/controllers/user_controller.py

Reason:
Repository standards require all persistence
operations to use approved repository interfaces.

Recommended Action:
Use UserRepository abstraction layer.
```

---

## Installation

### Step 1

Download the latest release package.

### Step 2

Extract the binary into your repository root.

```text
arka-sentinel.exe
```

### Step 3

Initialize the repository context model.

```bash
./arka-sentinel.exe --install
```

### Step 4

Continue using Git normally.

```bash
git add .
git commit -m "new feature"
```

Arka Sentinel automatically performs validation during commit operations.

---

## Generated Files

### Repository Context

```text
.arkasentinel/context_cache.bin
```

Local repository memory model.

### Root Cause Analysis

```text
.arkasentinel/context_state.md
```

Generated remediation guidance.

### Incident Ledger

```text
.arkasentinel/incident_history.log
```

Historical validation and bypass tracking.

---

## Emergency Override

For critical production situations:

```bash
git commit --no-verify
```

Override events are logged for future review and audit visibility.

---

## Security Model

### Source Code Protection

- Source code never leaves the workstation
- No external transmission
- No cloud dependency
- No remote inference

### Operational Footprint

- Local execution
- CPU-based processing
- Lightweight runtime
- No infrastructure requirements

---

## Licensing

Arka Sentinel includes a limited evaluation period.

### Activation Flow

Generate a machine fingerprint:

```bash
./arka-sentinel.exe --fingerprint
```

Submit:

- Fingerprint ID
- Purchase reference

Receive:

```text
.arkasentinel.key
```

Place the license file in the repository root to activate.

---

## Roadmap

- Team Policy Packs
- Organization-Wide Governance
- Architectural Drift Analytics
- Compliance Automation
- Release Assurance Integrations
- Knowledge Graph Expansion
- Enterprise Controls
- Developer Experience Enhancements

---

## Vision

Software systems accumulate knowledge faster than teams can document it.

Arka Sentinel exists to make repository context visible, enforceable, and actionable directly within the developer workflow—helping engineering organizations maintain architectural integrity as systems and teams scale.

---

## Copyright

**© 2026 Arka Sentinel. All Rights Reserved.**

Built for teams that believe architectural knowledge should be preserved—not rediscovered.