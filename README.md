# AI Agent Collaboration Protocol

**An open template for defining how AI coding agents should read, modify, validate, and report changes in a software repository.**

---

### The Gap

Karpathy coined "**vibe coding**" — describe your intent, and AI writes the code. It unlocked enormous productivity.

But when AI shifts from "writing a snippet" to "working inside your real project", a new set of problems emerges. AI can cross architecture boundaries, modify files it shouldn't touch, claim tests passed without running them, and leave you unsure what it actually changed.

Vibe coding solves **how fast** AI can produce. It doesn't solve **where it should stop**.

---

### What This Protocol Does

AGENTS.public.md defines a **project-level AI collaboration protocol** — not a prompt, but a governance layer:

- **S0–S3 task classification** — every task gets a risk level before execution
- **Boundary review** — the agent must check what modules, APIs, and data it touches
- **Lite / Full review** — simple logic check for functional changes; deep review for architecture, security, and data changes
- **Human confirmation gates** — S3-level tasks require explicit approval before proceeding
- **Delivery checklist** — changed files, validation commands, actual results, rollback plan
- **Audit and traceability** — leave a record of what was changed and why

> **Vibe coding teaches AI to go full speed. AGENTS.md teaches AI when to pause and ask.** A mature team member needs both.

---

### The S0–S3 System at a Glance

| Level | Scope | AI Behavior |
|-------|-------|------------|
| S0 | Read-only / analysis | Read, search, suggest. No modifications. |
| S1 | Small local change | Single-file, no architecture impact, easy rollback. |
| S2 | Functional change | Multi-file, may touch API/service. Lite review required. |
| S3 | High-risk / strategic | Architecture, security, data, IP. Stop and ask for human confirmation. |

S3 is where the protocol adds the most value — it's the formal "pause button" that turns AI from a black-box tool into a governable team member.

---

### Supported AI Coding Agents

Cursor, Claude Code, OpenAI Codex-style agents, GitHub Copilot coding agent, and other autonomous or semi-autonomous development tools that read `AGENTS.md` from the repository root.

---

### Quick Start

1. Copy [`AGENTS.public.md`](AGENTS.public.md) into your repository as `AGENTS.md`.
2. Customize: architecture boundaries, test commands, protected files, review rules.
3. For private rules, create `AGENTS.private.md` and keep it out of version control.

---

### Repository Structure

```
├── AGENTS.public.md                   # Main protocol (v3.0-public)
├── LICENSE                            # CC BY-NC 4.0
├── templates/
│   ├── AGENTS.minimal.md              # Compact one-page version
│   ├── S3_REVIEW_TEMPLATE.md          # S3 review worksheet
│   └── DELIVERY_REPORT_TEMPLATE.md    # Task delivery report
└── docs/                              # Documentation site (docsify)
```

### License

[CC BY-NC 4.0](LICENSE) — free for non-commercial use.

---

*This is a public template. It intentionally excludes proprietary algorithms, internal architecture, deployment secrets, and patent-sensitive implementation details. For production teams, maintain a separate private rules file.*
