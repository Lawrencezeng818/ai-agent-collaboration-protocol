# AI Agent Collaboration Protocol

> An open template for defining how AI coding agents should read, modify, validate, and report changes in a software repository.

---

### The Gap

Karpathy coined "**vibe coding**" — describe your intent, and AI writes the code. It unlocked enormous productivity.

But when AI shifts from "writing a snippet" to "working inside your real project", a new set of problems emerges. AI can cross architecture boundaries, modify files it shouldn't touch, claim tests passed without running them, and leave you unsure what it actually changed.

Vibe coding solves **how fast** AI can produce. It doesn't solve **where it should stop**.

---

### What This Protocol Does

- **S0–S3 task classification** — every task gets a risk level before execution
- **Boundary review** — what modules, APIs, and data are affected
- **Lite / Full review** — depth proportional to risk
- **Human confirmation gates** — S3 requires explicit approval
- **Delivery checklist** — changed files, validation results, rollback plan
- **Audit and traceability** — record what changed and why

> **Vibe coding teaches AI to go full speed. AGENTS.md teaches AI when to pause and ask.** A mature team member needs both.

---

### Quick Start

Copy [`AGENTS.public.md`](protocol.md) into your repo as `AGENTS.md`.

Then customize:

- architecture boundaries
- test commands
- protected files
- review rules
- deployment rules

For private rules, create `AGENTS.private.md` and keep it out of version control.

> **License:** [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)
> 
> **Disclaimer:** This is a public template. It intentionally excludes proprietary algorithms, internal architecture, deployment secrets, and patent-sensitive implementation details.
