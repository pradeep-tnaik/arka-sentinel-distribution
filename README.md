# 🛡️ Arka Sentinel

> **Repository Context Guardrails for Engineering Teams**
>
> Prevent architectural drift, unsafe code paths, and compliance violations before code ever leaves a developer workstation.

---

## Why Arka Sentinel?

Modern software systems accumulate technical debt not because engineers lack skill, but because critical architectural context gets lost over time.

* Teams change.
* Repositories evolve.
* Documentation becomes stale.
* Deadlines compress decision-making.

The result is architectural drift, compliance risks, fragile implementations, and expensive defects discovered too late in the delivery pipeline.

Arka Sentinel addresses this problem by acting as a **local-first repository context guardian**, validating changes against repository knowledge before commits are accepted.

---

# Core Principles

## 🔒 Privacy First

Your source code remains on your machine.

* No cloud services
* No source code uploads
* No external LLM calls
* No telemetry requirements
* No recurring AI API costs

---

## ⚡ Shift Validation Left

Most tooling identifies issues after code reaches CI/CD pipelines.

Arka Sentinel evaluates changes during the local commit workflow, helping engineers catch problems before they propagate downstream.

---

## 🧠 Preserve Architectural Knowledge

Repositories often outlive the engineers who originally designed them.

Arka Sentinel helps preserve and enforce repository conventions, architectural boundaries, and implementation patterns across the software lifecycle.

---

# Core Capabilities

## Repository Context Awareness

Builds an understanding of repository structure, implementation relationships, and historical engineering patterns.

---

## Architectural Guardrails

Detects:

* Layer violations
* Unsafe implementation shortcuts
* Repository policy violations
* Missing dependency flows
* Architectural bypasses
* Context inconsistencies

---

## Root Cause Analysis

When a validation fails, Arka Sentinel generates actionable remediation guidance explaining:

* What failed
* Why it failed
* Impact assessment
* Recommended fixes

---

## Local Audit Trail

Maintains a historical ledger of:

* Validation failures
* Warning events
* Emergency bypass activity
* Repository compliance signals

---

# High-Level Architecture

```text
Developer Changes
        │
        ▼
 Git Pre-Commit Hook
        │
        ▼
 Repository Analysis Engine (engine_v2.py)
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

# How It Works

## 1. Repository Initialization

During installation, Arka Sentinel analyzes the local repository and historical Git activity.

This process creates a compressed local context model (`release_memory.bin`) that serves as the repository's architectural memory.

---

## 2. Commit Interception

Whenever a developer runs:

```bash
git commit -m "feature update"
```

Arka Sentinel evaluates staged changes against:

* Repository structure
* Historical implementation patterns
* Configured policies
* Architectural constraints

---

## 3. Validation Decision

The engine determines whether the proposed changes align with repository expectations.

### Validation Pass

```text
✓ Commit Approved
```

### Validation Failure

```text
🛡️ Validation Fault Detected

Commit Blocked

Review local engine alerts or dashboard.
```

---

# Example

## Problem

A developer bypasses an approved repository abstraction layer.

```python
from database import direct_db_client

def update_user_balance(user_id, amount):
    return direct_db_client.execute(...)
```

---

## Commit Attempt

```bash
git commit -m "update balance workflow"
```

---

## Result

```text
[🛡️ Arka Sentinel]

Rule: ARCH-402
Category: Data Layer Isolation Bypass

Commit Blocked
```

---

## Generated RCA

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

# 🚀 Quick Start

## 🪟 Windows Installation

### Step 1: Download the Release Package

Download the latest release package:

```text
arka-sentinel-windows-x64.zip
```

Extract the archive directly into your repository root directory.

```text
my-project/
├── dist_launcher_windows.bat
├── engine_v2.py
├── dashboard_view.py
├── release_memory.bin
├── logo.png
├── .git/
└── src/
```

---

### Step 2: Initialize the Context Guardian

Build the repository memory model and install the Git pre-commit hook.

```powershell
.\dist_launcher_windows.bat --install
```

---

### Step 3: Continue Working Normally

```bash
git add .
git commit -m "feat: regular development workflow"
```

Arka Sentinel automatically performs validation inside your native shell during commit operations.

---

## 🍎 macOS Installation

### Step 1: Download the Distribution Package

Download the latest release package:

```text
arka-sentinel-macos-universal.zip
```

Extract the archive directly into your repository root directory.

```text
my-project/
├── dist_launcher_unix.sh
├── engine_v2.py
├── dashboard_view.py
├── release_memory.bin
├── logo.png
├── .git/
└── src/
```

---

### Step 2: Authorize the Launcher Script

Grant execution permissions:

```bash
chmod +x ./dist_launcher_unix.sh
```

---

### Step 3: Initialize the Context Guardian

Build the local repository memory model and install the Git pre-commit hook.

```bash
./dist_launcher_unix.sh --install
```

---

### What Happens During Initialization?

Arka Sentinel performs a completely local repository analysis process:

* Mines historical Git activity
* Builds repository relationship maps
* Establishes repository context baselines
* References the local memory layer (`release_memory.bin`)

No source code leaves the workstation during this process.

---

### Step 4: Continue Working Normally

```bash
git add .
git commit -m "feat: regular development workflow"
```

Typical validation execution time is measured in sub-seconds and runs entirely on your local machine before the commit is finalized.

---

# Local Validation Engine Commands

You can interface directly with the main analysis engine (`engine_v2.py`) from your virtual environment.

## Verify Repository Status

```bash
python engine_v2.py --verify
```

---

## Re-Evaluate Repository Boundaries

```bash
python engine_v2.py
```

---

# Security Model

## Source Code Protection

* Source code never leaves the workstation
* No external transmission
* No cloud dependency
* No remote inference

---

## Operational Footprint

* Local execution
* CPU-based processing
* Lightweight runtime
* No heavy infrastructure requirements

---

# Licensing

Arka Sentinel includes a cryptographic activation layer for operational environments.

## Activation Flow

Place your issued license file directly inside the repository root directory.

```text
my-project/
├── .arkasentinel.key
├── engine_v2.py
└── .git/
```

### Important

Add the following entry to your `.gitignore` file:

```gitignore
.arkasentinel.key
```

This prevents personal license files from being accidentally committed to shared repositories.

---

# Roadmap

* Team Policy Packs
* Organization-Wide Governance
* Architectural Drift Analytics
* Compliance Automation
* Release Assurance Integrations
* Knowledge Graph Expansion
* Enterprise Controls
* Developer Experience Enhancements

---

# Vision

Software systems accumulate knowledge faster than teams can document it.

Arka Sentinel exists to make repository context visible, enforceable, and actionable directly within the developer workflow—helping engineering organizations maintain architectural integrity as systems and teams scale.

---

# Copyright

**© 2026 Arka Sentinel. All Rights Reserved.**
