# ❓ Arka Sentinel Frequently Asked Questions (FAQ)

---

### Q1: Why should I use Arka Sentinel instead of SonarQube?
**A:** SonarQube is a static code analysis platform that executes checks *after* code is pushed to a remote branch or central CI/CD pipeline. By the time SonarQube flags an issue, your code has already left the machine, triggered a build, and broken team coordination trees. 

Arka Sentinel operates **entirely left of the pipeline**. It intercepts dangerous code intent natively inside the pre-commit loop in **under 0.4 seconds**. Developers fix problems locally before an broken build ever ruins collective tracking. Additionally, SonarQube requires massive server overhead and database maintenance; Arka Sentinel runs cleanly on your machine's CPU.

---

### Q2: Why not just use GitHub Copilot or an LLM chatbot?
**A:** AI assistants like GitHub Copilot are designed to *generate* lines of code based on immediate prompts. They do not understand overall architectural context, nor do they prevent you from making compliance mistakes or bypassing internal code guidelines. They are also completely cloud-dependent.

Arka Sentinel is an active, offline **Context Holder and Guardrail**. It does not generate code; it protects your codebase from structural malpractices. Because it runs 100% offline via local matrix math runtimes, **your proprietary source code never leaves the workstation**, eliminating cloud security vulnerabilities and high API platform fees.

---

### Q3: What exactly does the local "Semantic Neuro-Map" store?
**A:** The local model extracts vector embeddings representing function structures, implementation paths, and dependency hierarchies across your repository. It maps structural context over time. If a new module attempts to interact with resources in a pattern that violates structural expectations, the engine identifies the conflict based on semantic intent rather than simple keyword matches.

---

### Q4: Does running Arka Sentinel affect system processing speeds?
**A:** No. The engine relies on lightweight, frozen matrix compilation frameworks optimized explicitly for workstation CPUs. Total validation execution clocks out between **0.2s to 0.4s**, meaning your git workflow remains completely seamless with zero lagging interruptions.