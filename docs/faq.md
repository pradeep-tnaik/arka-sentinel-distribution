# ❓ Frequently Asked Questions

## Q1. How is Arka Sentinel different from ESLint, Semgrep, or traditional static analysis tools?

Traditional tools focus on syntax, patterns, and predefined rules. They are excellent at detecting formatting issues, code smells, and common implementation mistakes, but they do not understand the architectural intent of your repository.

Arka Sentinel evaluates code changes within the context of your repository's historical evolution and structural patterns. Rather than looking only for predefined signatures, it helps identify architectural drift, repository-specific violations, and implementation changes that may conflict with established engineering conventions.

In short:

| Traditional Tools     | Arka Sentinel                  |
| --------------------- | ------------------------------ |
| Syntax-focused        | Context-focused                |
| Rule-driven           | Repository-aware               |
| Generic checks        | Repository-specific validation |
| Detects coding issues | Detects architectural drift    |

---

## Q2. Do I need to write and maintain rule files?

No.

Most rule-based tools require engineering teams to continuously author, tune, and maintain custom rules.

Arka Sentinel is designed to minimize manual configuration by learning repository patterns during initialization. It analyzes your local Git history and repository structure to establish a contextual baseline that can be used during future validations.

This significantly reduces operational overhead while allowing the system to adapt to the repository it protects.

---

## Q3. Why use Arka Sentinel if we already have SonarQube or enterprise security scanners?

Enterprise scanners remain valuable and complementary.

However, most of these systems operate after code has already been pushed to a shared repository or entered the CI/CD pipeline.

Arka Sentinel operates much earlier in the software delivery lifecycle by validating changes directly inside the local Git pre-commit workflow.

Benefits include:

* Earlier detection of repository-specific violations
* Faster feedback for developers
* Reduced CI/CD noise
* Preservation of team-specific architectural conventions
* Prevention of issues before code leaves the workstation

---

## Q4. Why not rely solely on GitHub Copilot or cloud-based AI coding assistants?

AI coding assistants are designed to generate code.

Arka Sentinel is designed to validate code.

These are fundamentally different responsibilities.

Code assistants can accelerate implementation, but they do not enforce repository architecture, organizational policies, or engineering governance requirements.

Additionally, Arka Sentinel operates entirely offline:

* No cloud processing
* No external inference services
* No source code transmission
* No telemetry requirements
* No recurring AI API costs

This makes it suitable for teams with strict privacy, compliance, or intellectual property requirements.

---

## Q5. What happens when a validation fails?

When a repository boundary or policy is violated, Arka Sentinel blocks the commit and generates a detailed Root Cause Analysis (RCA) report.

The report explains:

* What failed
* Why it failed
* Which files were affected
* Potential impact
* Recommended remediation steps

Generated reports are stored locally:

```text
.arkasentinel/context_state.md
```

This allows developers to resolve issues quickly without manually investigating validation failures.

---

## Q6. Will Arka Sentinel slow down my development workflow?

No.

Arka Sentinel is designed to operate as a lightweight local validation layer optimized for developer workstations.

Typical validation times range between:

```text
0.2s – 0.4s
```

For most repositories, validation completes fast enough to remain effectively invisible within the normal commit workflow.

---

## Q7. Why is the software distributed as a ZIP package instead of a raw executable?

Release packages are distributed as compressed archives to simplify cross-platform delivery and reduce distribution overhead.

Benefits include:

* Smaller download sizes
* Easier release management
* Cleaner GitHub distribution workflows
* Reduced repository clutter
* Improved compatibility across operating systems

After extraction, the executable can be placed directly inside the target repository.

---

## Q8. How do I resolve the "Developer Cannot Be Verified" warning on macOS?

Because Arka Sentinel is distributed directly through GitHub Releases rather than the Apple App Store, macOS Gatekeeper may initially mark the binary as an unverified application.

To authorize the executable, run:

```bash
xattr -d com.apple.quarantine ./arka-sentinel
```

This removes the Gatekeeper quarantine attribute and allows the binary to execute normally.

Afterward, proceed with installation:

```bash
./arka-sentinel --install
```

---

## Q9. Does Arka Sentinel send repository data anywhere?

No.

Arka Sentinel follows a local-first architecture.

Repository analysis, validation, and context generation occur entirely on the developer workstation.

Your source code is never:

* Uploaded
* Shared
* Indexed remotely
* Sent to cloud AI providers
* Processed by external services

All repository intelligence remains local to your environment.

---

## Q10. Is Arka Sentinel a replacement for existing security, quality, and compliance tools?

No.

Arka Sentinel is intended to complement existing tooling.

A typical engineering stack may include:

* ESLint
* Semgrep
* SonarQube
* SAST platforms
* Dependency scanners
* CI/CD quality gates

Arka Sentinel adds a missing layer:

> Repository Context Validation

Its role is to help preserve architectural integrity and repository-specific knowledge before code reaches downstream systems.
