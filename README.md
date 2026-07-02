# AI Agent Collaboration Protocol

**An open template for defining how AI coding agents should read, modify, validate, and report changes in a software repository.**

---

### The Gap

In the vibe coding workflow popularized by Karpathy, you describe your intent and AI helps generate or modify the code. It unlocked enormous productivity.

But when AI shifts from "writing a snippet" to "working inside your real project", a new set of problems emerges:

- AI can cross architecture boundaries.
- AI can modify files it should not touch.
- AI can claim tests passed without running them.
- AI can leave you unsure what it actually changed.

Vibe coding optimizes for speed of generation. It does not define the boundaries of execution.

---

### What This Protocol Does

This protocol gives AI coding agents a **project-level collaboration contract** — not a prompt, but a governance layer:

- **S0–S3 task classification** — every task gets a risk level before execution
- **Boundary review** — identify affected modules, APIs, data, security, and audit surfaces
- **Lite / Full review** — review depth scales with task risk
- **Human confirmation gates** — S3-level tasks require explicit approval before proceeding
- **Delivery checklist** — report changed files, validation results, residual risk, and rollback plan
- **Audit and traceability** — record what changed, why it changed, and how it was validated

> **Vibe coding teaches AI to go full speed. AGENTS.md teaches AI when to pause and ask.** A mature team member needs both.

---

### Before / After

**Without a protocol:**

```
User: Refactor the auth module.
AI:  *changes auth logic*
     *edits database migration without asking*
     *updates production config*
     *claims tests passed*
     *provides no rollback plan*
```

**With AGENTS.md:**

```
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

Copy `AGENTS.public.md` into your repository as `AGENTS.md`:

```bash
curl -L https://raw.githubusercontent.com/lawrencezeng818/ai-agent-collaboration-protocol/main/AGENTS.public.md -o AGENTS.md
```

Then customize:

- architecture boundaries
- test commands
- protected files
- review rules
- deployment rules

For private rules, create `AGENTS.private.md` and keep it out of public repositories.

---

### Documentation

Full documentation site:

https://lawrencezeng818.github.io/ai-agent-collaboration-protocol/

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

[CC BY-NC 4.0](LICENSE) — free for non-commercial use. Commercial use requires separate written permission.

---

*This is a public template. It intentionally excludes proprietary algorithms, internal architecture, deployment secrets, private decision memory, and patent-sensitive implementation details.*
