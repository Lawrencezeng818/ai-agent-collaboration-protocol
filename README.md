# AI Agent Collaboration Protocol

A public template for safer collaboration between humans and AI coding agents.

This protocol helps teams define:

- task risk levels,
- architecture boundaries,
- review requirements,
- human confirmation rules,
- delivery checklists,
- audit and traceability expectations,
- safe escalation behavior.

It is designed for projects using AI coding agents such as Claude Code, Cursor, OpenAI Codex-style agents, GitHub Copilot coding agent, and other autonomous or semi-autonomous development tools.

## Why this exists

AI agents are powerful, but they can also:

- change too much,
- bypass architecture boundaries,
- hide failing tests,
- delete important records,
- modify sensitive logic without understanding it,
- make irreversible changes without approval.

This template gives AI agents a clear operating protocol.

## Quick Start

Copy `AGENTS.public.md` into your repository as `AGENTS.md`.

Then customize:

- architecture boundaries,
- test commands,
- protected files,
- review rules,
- deployment rules.

For private rules, create:

AGENTS.private.md
Do not commit secrets, internal infrastructure, proprietary algorithms, or patent-sensitive implementation details.
