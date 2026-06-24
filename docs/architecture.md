# 🏗️ Arka Sentinel Architecture Specification

This document describes the core execution model, runtime architecture, and system boundaries of the Arka Sentinel local-first validation platform.

---

# 🧭 System Overview

Arka Sentinel operates entirely on the developer workstation and performs repository validation before code is committed.

The platform is composed of three primary execution layers:

1. Universal Git Diff Intake Layer
2. Semantic Evaluation Layer
3. Lifecycle Execution Manager

All components execute locally without cloud connectivity, remote inference, or external API dependencies.

---

# A. Universal Git Diff Intake Layer

## Responsibility

Language-agnostic repository change ingestion.

## Execution Model

During validation, Arka Sentinel invokes:

```bash
git diff --cached --unified=3
```

The engine processes raw staged additions and deletions directly from Git.

Rather than depending on language-specific parsers, compiler toolchains, or repository-specific configuration, Arka Sentinel evaluates changes as normalized code modification streams.

Supported repositories may contain:

* Python
* Go
* Java
* TypeScript
* JavaScript
* Terraform (HCL)
* SQL
* Shell scripts
* Mixed-language implementations

The intake layer provides a unified representation of repository modifications for downstream analysis.

---

# B. Semantic Evaluation Layer

## Responsibility

Context validation and architectural intent analysis.

## Execution Model

The semantic evaluation layer utilizes a local embedding model to transform code modifications into vector representations suitable for similarity analysis.

Local model:

```text
sentence-transformers/all-MiniLM-L6-v2
```

The engine:

1. Extracts staged modifications
2. Generates local vector embeddings
3. Evaluates semantic proximity against signed validation rules
4. Calculates rule activation scores
5. Triggers policy enforcement when configured thresholds are exceeded

All processing occurs locally on the developer workstation.

No repository data leaves the execution environment.

---

# C. Lifecycle Execution Manager

## Responsibility

Validation orchestration, policy enforcement, and audit generation.

## Execution Model

The Lifecycle Execution Manager integrates with:

```text
.git/hooks/pre-commit
```

When a commit is initiated:

1. Repository changes are collected
2. Validation rules are evaluated
3. Threshold scores are calculated
4. Policy decisions are generated
5. Audit artifacts are produced when required

The manager also performs:

* Commit interception
* Rule orchestration
* Validation reporting
* Local telemetry generation
* RCA generation

---

# 🔄 Validation Execution Flow

```text
Developer Workstation
        │
        ▼
git commit -m "..."
        │
        ▼
┌────────────────────────────────────────────┐
│ 1. Git Pre-Commit Intercept                │
└──────────────────┬─────────────────────────┘
                   │
                   ▼
┌────────────────────────────────────────────┐
│ 2. Staged Change Extraction                │
│    git diff --cached --unified=3           │
└──────────────────┬─────────────────────────┘
                   │
                   ▼
┌────────────────────────────────────────────┐
│ 3. Local Semantic Evaluation               │
│    Vector Embedding Generation             │
└──────────────────┬─────────────────────────┘
                   │
                   ▼
┌────────────────────────────────────────────┐
│ 4. Rule Threshold Evaluation               │
│    Similarity Scoring                      │
└──────────────────┬─────────────────────────┘
                   │
        ┌──────────┴──────────┐
        ▼                     ▼

     PASS                   FAIL

        │                     │
        ▼                     ▼

Commit Allowed      Commit Blocked
                          │
                          ▼
                Root Cause Analysis
                          │
                          ▼
generated_artifacts/context_state.md
```

---

# Rule Evaluation Model

Arka Sentinel evaluates repository changes against signed rule definitions contained within the local rule store.

Primary evaluation stages:

1. Diff Extraction
2. Vector Generation
3. Similarity Scoring
4. Threshold Comparison
5. Enforcement Decision

Example:

```text
Rule Score:          0.58
Activation Threshold: 0.35

Result: BLOCK
```

Each rule maintains its own activation threshold, allowing different governance controls to operate at different sensitivity levels.

---

# Generated Artifacts

## Root Cause Analysis Report

```text
generated_artifacts/context_state.md
```

Contains:

* Validation summary
* Triggered rule information
* Risk assessment
* Remediation guidance

---

## Validation History

```text
violation_history.jsonl
```

Contains:

* Recent validation events
* Rule activations
* Enforcement outcomes
* Execution timestamps

---

# Security Model

## Local-First Execution

All repository analysis occurs locally.

* No cloud services
* No source code uploads
* No external API calls
* No telemetry transmission

## Repository Protection

Validation executes before code leaves the workstation, helping preserve architectural integrity and repository governance standards.

---

# Design Philosophy

Arka Sentinel is designed around a simple principle:

> Architectural intent should be preserved with the same rigor as source code.

By validating repository changes against contextual governance rules during development, Arka Sentinel helps engineering teams reduce architectural drift, maintain compliance boundaries, and preserve institutional knowledge as systems evolve.
