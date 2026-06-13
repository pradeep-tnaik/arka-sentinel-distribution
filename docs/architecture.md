# 🏗️ Arka Sentinel Architecture Specification

This document details the low-level component execution flow, core technical specifications, and system boundaries of Arka Sentinel's local-first validation engine.

---

## 🧭 System Component Topology

Arka Sentinel is composed of three decoupled core layers that execute synchronously inside a native runtime container loop:

### A. The Symbolic Abstract Syntax Tree (AST) Compiler Layer
* **Responsibility:** Structural, rule-based static pattern tracking.
* **Mechanics:** Leverages deterministic tree-parsing runtimes to convert modified Python source code files into a localized syntactic flow tree. It checks explicit constraints (e.g., verifying import origins, restricted class initializations, and mandatory interface implementations) before execution compiles.

### B. The Neuro Semantic Context Model Layer
* **Responsibility:** Intent validation and contextual drift mapping.
* **Mechanics:** Orchestrates a lightweight, frozen, offline vector embedding engine (sub-100MB footprint running directly on host CPU matrix math runtimes). It translates newly modified functions and code blocks into geometric vectors to analyze semantic proximity against project standards.

### C. The Lifecycle Execution Manager (Pre-Commit Hook)
* **Responsibility:** Runtime gatekeeping and telemetry capture.
* **Mechanics:** Binds to the project's `.git/hooks/pre-commit` boundary. It intercepts commit sequences, feeds changed diffs into the evaluation layers, and determines the structural PASS/FAIL execution branch within a sub-0.4s runtime window.

---

## 🔄 Synchronous Execution Flow Matrix

```text
[Terminal Window] ──► git commit -m "..."
                           │
                           ▼
┌────────────────────────────────────────────────────────┐
│ 1. Git Pre-Commit Intercept Loop (<0.05s)              │
└──────────────────────────┬─────────────────────────────┘
                           │
                           ▼
┌────────────────────────────────────────────────────────┐
│ 2. Isolated Source Extraction & Delta Chunk Parsing    │
└──────────────────────────┬─────────────────────────────┘
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
┌──────────────────────────┐┌──────────────────────────┐
│ 3A. Deterministic AST    ││ 3B. Offline Vector Map   │
│ Structural Scan (Rules)  ││ Similarity Matching      │
└─────────────┬────────────┘└───────────┬──────────────┘
              │                         │
              └────────────┬────────────┘
                           │
                           ▼
┌────────────────────────────────────────────────────────┐
│ 4. Neuro-Symbolic Evaluator Convergence Check          │
└──────────────────────────┬─────────────────────────────┘
                           │
            ┌──────────────┴──────────────┐
            ▼                             ▼
   [PASS: Margin > 0.85]         [FAIL: Margin < 0.85]
            │                             │
            ▼                             ▼
    (Commit Validated)           (Commit Aborted)
                                          │
                                          ▼
                                 ┌─────────────────┐
                                 │ 5. Compile RCA  │ ──► .arkasentinel/context_state.md
                                 └─────────────────┘