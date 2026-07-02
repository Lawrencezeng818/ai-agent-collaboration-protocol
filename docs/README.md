# AI Agent Collaboration Protocol

> An open template for defining how AI coding agents should read, modify, validate, and report changes in a software repository.

---

### The Gap

In the vibe coding workflow popularized by Karpathy, you describe your intent and AI helps generate or modify the code. It unlocked enormous productivity.

But when AI shifts from "writing a snippet" to "working inside your real project", problems emerge:

- AI can cross architecture boundaries.
- AI can modify files it should not touch.
- AI can claim tests passed without running them.
- AI can leave you unsure what it actually changed.

Vibe coding optimizes for speed of generation. It does not define the boundaries of execution.

---

### What This Protocol Does

- **S0–S3 task classification** — every task gets a risk level before execution
- **Boundary review** — identify affected modules, APIs, data, security, and audit surfaces
- **Lite / Full review** — review depth scales with task risk
- **Human confirmation gates** — S3 requires explicit approval
- **Delivery checklist** — report changed files, validation results, residual risk, and rollback plan
- **Audit and traceability** — record what changed, why it changed, and how it was validated

> **Vibe coding teaches AI to go full speed. AGENTS.md teaches AI when to pause and ask.** A mature team member needs both.

---

### Before / After

**Without a protocol:**

```text
User: Refactor the auth module.
AI:  *changes auth logic*
     *edits database migration without asking*
     *updates production config*
     *claims tests passed*
     *provides no rollback plan*
```

**With AGENTS.md:**

```text
Task Level: S3
Reason: auth/security boundary affected
Status: Human confirmation required

Proposed Plan:
  - inspect auth module
  - identify affected files
  - propose minimal change
  - define validation and rollback plan

No file changes will be made before approval.
```

---

### Quick Start

Copy `AGENTS.public.md` into your repo as `AGENTS.md`:

```bash
curl -L https://raw.githubusercontent.com/lawrencezeng818/ai-agent-collaboration-protocol/main/AGENTS.public.md -o AGENTS.md
```

Then customize: architecture boundaries, test commands, protected files, review rules, deployment rules.

For private rules, create `AGENTS.private.md` and keep it out of public repositories.

> **License:** [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) — free for non-commercial use.
> 
> **Disclaimer:** This is a public template. It intentionally excludes proprietary algorithms, internal architecture, deployment secrets, private decision memory, and patent-sensitive implementation details.
