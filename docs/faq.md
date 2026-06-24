# ❓ Frequently Asked Questions

---

## Q1. How is Arka Sentinel different from ESLint, Semgrep, or traditional static analysis tools?

Traditional static analysis tools focus primarily on syntax, predefined patterns, and language-specific rules.

Arka Sentinel focuses on repository context and architectural intent.

Rather than evaluating only code structure, Arka Sentinel analyzes staged repository modifications against locally enforced governance rules and context-aware validation policies.

| Traditional Static Analysis | Arka Sentinel                |
| --------------------------- | ---------------------------- |
| Syntax-focused              | Context-focused              |
| Language-specific rule sets | Language-agnostic validation |
| Pattern matching            | Semantic evaluation          |
| Typically runs in CI/CD     | Runs before commit           |
| Generic rule libraries      | Repository-aware governance  |

---

## Q2. Do I need to create or maintain custom rule files?

No.

Arka Sentinel is designed to minimize operational overhead.

During initialization, the engine loads signed validation definitions from the local rule store:

```text
release_memory.bin
```

This allows the platform to enforce governance policies without requiring teams to continuously manage custom regex patterns, rule files, or parser configurations.

---

## Q3. Why use Arka Sentinel if we already have SonarQube or enterprise security scanners?

Arka Sentinel is complementary to existing security and quality tooling.

Most enterprise scanners operate after code has already been pushed to a shared repository or CI/CD pipeline.

Arka Sentinel shifts validation earlier in the software delivery lifecycle by operating directly within the local Git workflow.

Benefits include:

* Earlier feedback
* Reduced CI/CD noise
* Faster remediation
* Repository-specific enforcement
* Preservation of architectural boundaries

---

## Q4. Why not rely solely on GitHub Copilot or cloud-based AI coding assistants?

AI coding assistants are designed to generate code.

Arka Sentinel is designed to validate code.

These tools solve different problems.

Arka Sentinel operates entirely offline:

* No cloud databases
* No external AI APIs
* No source code uploads
* No telemetry collection
* No network dependency

This makes it suitable for teams with strict privacy, compliance, and intellectual property requirements.

---

## Q5. What happens when a validation fails?

When a staged modification violates an active governance rule, Arka Sentinel blocks the commit and generates a Root Cause Analysis (RCA) report.

The report explains:

* What failed
* Why it failed
* Which rule was triggered
* Recommended remediation steps

Generated reports are stored locally:

```text
generated_artifacts/context_state.md
```

---

## Q6. Will Arka Sentinel slow down my development workflow?

No.

Arka Sentinel is designed to operate as a lightweight local validation layer.

Typical execution times are measured in milliseconds and occur entirely on the developer workstation.

For most repositories, validation completes fast enough to remain effectively invisible within the normal commit workflow.

---

## Q7. How do I receive my production license after purchase?

After a successful purchase, a signed activation package is delivered to the email address associated with the transaction.

The package contains:

```text
.arkasentinel.key
```

Activation instructions are included with the license delivery.

To activate:

```text
my-project/
├── .arkasentinel.key
├── engine_v2.py
└── .git/
```

Place the license file in the repository root and continue using Git normally.

---

## Q8. Does Arka Sentinel send repository data anywhere?

No.

Arka Sentinel follows a strict local-first execution model.

All repository analysis occurs directly on the developer workstation.

Your source code is never:

* Uploaded
* Shared externally
* Indexed remotely
* Processed by cloud AI services
* Sent to third-party platforms

Repository context remains entirely within your local environment.

---

## Q9. Can Arka Sentinel replace existing security and compliance tools?

No.

Arka Sentinel is intended to complement existing tooling rather than replace it.

A typical engineering stack may still include:

* ESLint
* Semgrep
* SonarQube
* SAST platforms
* Dependency scanners
* CI/CD quality gates

Arka Sentinel adds an additional layer focused on:

> Repository Context Validation

Its purpose is to help preserve architectural intent and enforce repository-specific governance before code leaves the workstation.

---

## Q10. What problem is Arka Sentinel ultimately solving?

Software systems accumulate knowledge faster than teams can document it.

As teams change and repositories evolve, critical architectural assumptions can disappear.

Arka Sentinel helps organizations preserve that context by making repository governance visible, enforceable, and actionable directly within the developer workflow.
