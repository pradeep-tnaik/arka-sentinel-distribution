# 🛡️ Arka Sentinel Pre-Commit Guardrail Engine

> **Protect architectural integrity before code leaves the workstation.**

Arka Sentinel is a local-first repository guardrail that validates code changes directly within the developer workflow. It helps engineering teams identify security risks, compliance violations, architectural drift, and unsafe implementation patterns before code reaches shared repositories or CI/CD pipelines.

---

# Why Arka Sentinel?

Modern software systems accumulate risk through small, incremental changes:

* Security controls are bypassed
* Repository conventions drift
* Sensitive data leaks into code
* Architectural boundaries erode over time
* Institutional knowledge disappears as teams evolve

Arka Sentinel helps prevent these issues by evaluating changes at commit time, when feedback is fastest and remediation is cheapest.

---

# Key Capabilities

## 🔒 Local-First Security

All validation runs locally.

* No source code uploads
* No cloud dependencies
* No telemetry collection
* No external AI APIs
* No internet connectivity required

Your code never leaves your workstation.

---

## 🧠 Multi-Layer Validation

Arka Sentinel combines:

* Structural code analysis
* Repository context validation
* Security policy enforcement
* Compliance rule evaluation

This enables detection of both syntax-level violations and higher-level implementation risks.

---

## 📋 Automated Remediation Guidance

When a validation fails, Arka Sentinel generates a detailed report explaining:

* What failed
* Why it failed
* Which files were affected
* Recommended remediation steps

This helps developers resolve issues quickly without lengthy investigation cycles.

---

# Compliance & Governance Coverage

The engine includes validation coverage across multiple security and compliance domains.

| Rule Identifier              | Validation Category               | Framework / Domain      |
| ---------------------------- | --------------------------------- | ----------------------- |
| `DATABASE_INJECTION_01`      | Raw SQL Injection Detection       | OWASP Top 10            |
| `HEALTH_GDPR_HIPAA_01`       | Sensitive Data Exposure           | GDPR / HIPAA            |
| `PCI_DSS_CREDENTIALS_01`     | Secrets & Credential Detection    | PCI-DSS                 |
| `FINANCIAL_COMPLIANCE_01`    | Unauthorized Financial Operations | Internal Controls       |
| `MULTI_TENANCY_ISOLATION_01` | Tenant Isolation Validation       | Multi-Tenant Platforms  |
| `SRE_RESOURCE_LIMITS_01`     | Resource Safety Controls          | Reliability Engineering |

---

# 🚀 Installation Guide

Ensure you are operating inside the target repository root and have activated your local development environment.

---

## 🪟 Windows

### Step 1: Activate Virtual Environment

```powershell
.\venv\Scripts\activate
```

### Step 2: Initialize Arka Sentinel

```powershell
python engine_v2.py --init
```

---

## 🍎 macOS & 🐧 Linux

### Step 1: Activate Virtual Environment

```bash
source venv/bin/activate
```

### Step 2: Initialize Arka Sentinel

```bash
python3 engine_v2.py --init
```

### Step 3: Configure Git Hook Permissions

```bash
chmod +x .git/hooks/pre-commit
```

---

# Verification Workflow

Once initialized, Arka Sentinel automatically intercepts standard Git commit operations through the local pre-commit hook.

To manually verify the current staged changes:

```bash
python engine_v2.py --verify
```

A successful verification confirms:

* ✅ Repository hooks are active
* ✅ Validation rules are loaded
* ✅ Local policy enforcement is operational
* ✅ Runtime dependencies are healthy

---

# Evaluation Mode

## Default Trial

```text
5-Day Local Evaluation License
```

Evaluation licenses are hardware-bound and validated locally.

---

# Generated Artifacts

## Repository Context Report

```text
generated_artifacts/context_state.md
```

Contains:

* Validation summaries
* Violation reports
* Root Cause Analysis (RCA)
* Recommended remediation guidance

---

# Dashboard & Diagnostics

Launch the local dashboard:

```bash
python dashboard_view.py
```

The dashboard provides visibility into:

* Active validations
* Rule execution results
* Repository compliance posture
* Historical validation reports
* Similarity score metrics

---

# Example Validation Failure

```text
🛡️ Validation Fault Detected

Rule:
DATABASE_INJECTION_01

Category:
Unsanitized SQL Construction

Status:
COMMIT BLOCKED
```

Generated report:

```text
generated_artifacts/context_state.md
```

---

# Security & Operational Model

## Source Code Protection

* No source code transmission
* No remote processing
* No cloud inference services
* No external telemetry

## Operational Model

* Fully local execution
* Lightweight runtime footprint
* Native Git workflow integration
* Offline operation

## Performance

Typical validation completes in **sub-second execution time** after the local runtime is initialized.

---

# Vision

Software systems accumulate knowledge faster than teams can document it.

Arka Sentinel exists to help engineering organizations preserve architectural intent, maintain repository governance, strengthen compliance posture, and reduce delivery risk directly within the developer workflow.

---

# Copyright

**© 2026 Arka Pvt. Ltd. All Rights Reserved.**
