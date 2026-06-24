# 🛡️ Arka Sentinel

## Universal Architectural Context Memory Engine

Prevent structural drift, implementation decay, and critical design boundary violations before code ever leaves a developer workstation.

**Local-first. Offline by default. Repository-aware.**

---

# Why Arka Sentinel?

Software systems often outlive the teams that originally designed them.

Over time:

* Engineers move on
* Documentation becomes outdated
* Architectural decisions lose context
* Shortcuts become permanent patterns
* Repository conventions drift

The result is often not a coding problem—it is a context problem.

Teams gradually lose the knowledge that explains **why** certain design decisions were made, leading to architectural drift, compliance violations, fragile implementations, and production incidents that are discovered far too late in the delivery lifecycle.

Arka Sentinel helps preserve that context by validating changes before they are committed.

---

# Core Principles

## 🔒 Privacy First

Your source code remains on your machine.

* No cloud services
* No source code uploads
* No external AI APIs
* No telemetry collection
* No internet connectivity required

Everything runs locally.

---

## 🌍 Language Agnostic by Design

Arka Sentinel evaluates repository changes using a language-independent approach rather than relying exclusively on language-specific parsers.

This enables a consistent validation model across:

* Python
* TypeScript
* JavaScript
* Go
* Terraform (HCL)
* SQL
* Shell scripts
* Mixed-language repositories

---

## ⚡ Validate Earlier

Most quality and security checks happen after code reaches shared infrastructure.

Arka Sentinel operates directly inside the developer workflow, providing feedback before changes leave the workstation.

---

## 🧠 Preserve Architectural Knowledge

Repositories often contain critical assumptions that are never fully captured in documentation.

Arka Sentinel helps maintain:

* Architectural boundaries
* Repository conventions
* Security controls
* Compliance constraints
* Institutional engineering knowledge

---

# What Arka Sentinel Detects

### Architectural Drift

* Layer violations
* Repository boundary bypasses
* Missing dependency controls
* Unexpected implementation patterns

### Security Risks

* Unsafe code paths
* Sensitive data exposure
* Configuration misuse
* Policy violations

### Compliance Violations

* Repository-specific controls
* Regulatory guardrails
* Organization-defined rules
* Workflow enforcement boundaries

---

# High-Level Architecture

```text
Developer Changes
        │
        ▼
Git Staging Area
(git add)
        │
        ▼
Git Pre-Commit Hook
        │
        ▼
Repository Analysis Engine
(engine_v2.py)
        │
        ├── Context Evaluation
        ├── Rule Validation
        ├── Security Analysis
        └── Compliance Checks
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
Commit        Commit Blocked
Allowed       RCA Generated
```

---

# Quick Start

## 🪟 Windows Installation

### Step 1: Download

Download the latest release package:

```text
arka-sentinel-windows-x64.zip
```

### Step 2: Extract

Extract the archive into your repository root.

```text
my-project/
├── dist_launcher_windows.bat
├── engine_v2.py
├── dashboard_view.py
├── release_memory.bin
└── logo.png
```

### Step 3: Install

```powershell
.\dist_launcher_windows.bat --install
```

Arka Sentinel will initialize repository context and install the required Git hooks.

---

## 🍎 macOS / 🐧 Linux Installation

### Step 1: Download

Download the latest release package:

```text
arka-sentinel-macos-universal.zip
```

### Step 2: Extract

Extract the archive into your repository root.

### Step 3: Authorize the Launcher

```bash
chmod +x ./dist_launcher_unix.sh
```

### Step 4: Install

```bash
./dist_launcher_unix.sh --install
```

Arka Sentinel will initialize repository context and install the required Git hooks.

---

# Commercial Licensing

Every installation automatically starts with a fully functional evaluation period.

## Purchase a License

Acquire a permanent workstation license:

👉 https://rzp.io/rzp/arkasentinel

---

## Activate

Place the issued license file in the repository root:

```text
my-project/
├── .arkasentinel.key
├── engine_v2.py
└── .git/
```

---

## Protect Your License

Add the following entry to your `.gitignore` file:

```gitignore
.arkasentinel.key
```

This prevents license credentials from being committed to shared repositories.

---

# Management & Diagnostics

## Dashboard

Review validation activity, repository health, and historical events:

```bash
python dashboard_view.py
```

---

## Manual Verification

Run a direct validation pass:

```bash
python engine_v2.py --verify "intent: manual verification check"
```

---

# Security Model

## Source Code Protection

* No source code transmission
* No cloud processing
* No external inference services
* No telemetry collection

## Runtime Model

* Local execution
* CPU-based processing
* Offline operation
* Repository-native integration

All repository analysis remains entirely within the developer workstation.

---

# Roadmap

* Repository Context Analytics
* Team Policy Packs
* Organizational Governance Controls
* Architectural Drift Reporting
* Release Assurance Integrations
* Enterprise Compliance Packs
* Enhanced Developer Experience

---

# Vision

Software systems accumulate knowledge faster than teams can document it.

Arka Sentinel exists to make repository context visible, enforceable, and actionable directly inside the development workflow.

The goal is simple:

> Preserve architectural intent before it becomes operational risk.

---

# Copyright

**© 2026 Arka Sentinel. All Rights Reserved.**

Protecting engineering knowledge, one commit at a time.
