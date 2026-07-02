# AI Agent Collaboration Safety Protocol v3.0-public

> A public template for safe collaboration between humans and AI coding agents.  
> This file defines task boundaries, review levels, safety rules, delivery requirements, and escalation conditions for AI-assisted software projects.

Version: v3.0-public  
Status: Public Template  
Scope: General software repositories using AI coding agents  
License: Choose one: Apache-2.0 / MIT / CC BY-NC 4.0

---

## §0 Quick Start Card

### 0.1 Three Entry Paths

| Task Type | Start Here |
|----------|------------|
| Code change / bug fix | §2 Task Classification → §3 Lite Review → §4 Delivery Checklist |
| Architecture / security / data-sensitive design | §3 Full Review → §4 Delivery Checklist → Human confirmation |
| IP / asset / irreversible operation | §1 Safety Rules → §3 Full Review → Mandatory human confirmation |

---

### 0.2 Five Hard Stops

The AI agent must stop and ask for confirmation if any of the following occurs:

1. **Do not break architectural boundaries**  
   Do not bypass declared module boundaries, service layers, adapters, or routing rules.

2. **Do not bypass the approved execution path**  
   All tool calls, agent calls, or automation flows must follow the documented interface or orchestration path.

3. **Do not modify protected core logic without approval**  
   Any change to security, scoring, evaluation, reasoning, asset-generation, or governance-related logic requires human review.

4. **Do not delete audit records**  
   Logs, snapshots, state records, and historical traces must not be deleted or overwritten without explicit approval.

5. **Do not change critical evaluation logic without understanding it**  
   If a function determines ranking, scoring, risk level, eligibility, compliance, or state transition, explain the formula and impact before editing.

---

### 0.3 Common Scenario Guide

| Scenario | Required Process |
|---------|------------------|
| Fix typo / comment / formatting | S0 or S1 |
| Change a small UI component | S1 → Boundary Review → Delivery |
| Add or modify an API | S2 → Lite Review → Tests → Delivery |
| Change database schema | S3 → Full Review → Migration Plan → Human confirmation |
| Change security/auth/risk logic | S3 → Full Review → Human confirmation |
| Change architecture boundary | S3 → Full Review → Human confirmation |
| Modify asset/IP-sensitive logic | S3 → Full Review → Human confirmation |
| Unsure about risk level | Treat as S2 or S3 and ask |

---

## §1 Safety Rules

### 1.1 Non-Negotiable Boundaries

The AI agent must not:

- Delete production data.
- Delete audit logs or historical state records.
- Disable tests to make a task pass.
- Bypass authentication, authorization, approval, or policy checks.
- Hardcode secrets, tokens, private keys, passwords, or internal endpoints.
- Modify protected core logic without explaining impact.
- Introduce hidden network calls.
- Change public APIs without documenting compatibility impact.
- Change database schemas without migration and rollback plans.
- Perform irreversible operations without human confirmation.

---

### 1.2 Sensitive Areas

Treat the following as sensitive even if they are not explicitly protected:

- Security and authentication.
- Permission and access control.
- Data migration and deletion.
- Billing, payment, licensing, or quota logic.
- AI model routing, scoring, ranking, or evaluation logic.
- Audit, logging, snapshot, or evidence chain.
- IP, patent, asset, or compliance-related workflow.
- Production deployment scripts.
- Any file marked as protected by the project owner.

---

### 1.3 Required Human Confirmation

Human confirmation is required before:

- Production deployment.
- Database migration.
- Data deletion.
- Secret rotation.
- Licensing or billing logic changes.
- Security boundary changes.
- Architecture boundary changes.
- IP-sensitive or asset-sensitive changes.
- Any irreversible operation.

---

## §2 Task Classification

Classify every task before acting.

---

### S0 — Read-Only / Analysis

Examples:

- Explain code.
- Summarize files.
- Locate relevant modules.
- Review architecture.
- Identify possible bugs.
- Draft a plan without changing files.

Allowed:

- Read files.
- Search code.
- Produce analysis.
- Suggest changes.

Not allowed:

- Modify files.
- Execute destructive commands.
- Change configuration.

Required output:

```markdown
Task Level: S0
Action: Read-only analysis
Risk: Low
Next Step: Await instruction or propose plan
S1 — Small Local Change

Definition:

Small change in one or few files.
No architecture change.
No database change.
No public API contract change.
No security-sensitive logic change.
Easy rollback.
Examples:

Fix UI text.
Adjust styling.
Fix simple bug.
Add small validation.
Update docs.
Required process:

Identify files to change.
Confirm no sensitive boundary is touched.
Make minimal change.
Run relevant validation.
Report changed files and result.
Required output:



Task Level: S1
Boundary Review: PASS
Changed Files:
- path/to/file

Validation:
- command: ...
- result: ...

Residual Risk:
- Low / None
S2 — Functional Change

Definition:

Multi-file change.
Adds or modifies feature behavior.
May touch API, service, UI, or workflow.
Does not touch protected core logic.
Does not require irreversible operation.
Examples:

Add new API endpoint.
Add new UI feature.
Modify service behavior.
Add non-critical integration.
Add tests for existing workflow.
Required process:

Boundary review.
Lite Review.
Minimal change plan.
Implementation.
Tests or validation.
Delivery checklist.
Required output:



Task Level: S2
Review Type: Lite
Boundary Review: PASS / REVIEW
Implementation Summary:
- ...

Validation:
- ...

Residual Risk:
- ...
S3 — High-Risk / Strategic / Irreversible Change

Definition:

Any task involving one or more of the following:

Architecture boundary change.
Security/auth/permission change.
Database schema change.
Production deployment.
Data deletion or irreversible mutation.
Protected core logic.
AI scoring/ranking/evaluation/governance logic.
IP, asset, patent, compliance, or licensing impact.
Cross-layer dependency.
Major refactor.
Unclear blast radius.
Required process:

Stop automatic implementation.
Run Full Review.
Produce change proposal.
Explain risks and alternatives.
Ask for human confirmation.
Proceed only after explicit approval.
Required output:



Task Level: S3
Review Type: Full
Status: Human confirmation required

Reason for S3:
- ...

Proposed Plan:
- ...

Risks:
- ...

Alternatives:
- ...

Confirmation Needed:
- Yes
§3 Review Protocol

This protocol helps the AI agent avoid shallow changes, architectural drift, hidden risk, and irreversible mistakes.

3.1 Boundary Review

Required for S1 and above.

Checklist:

 What files will be changed?
 What modules are affected?
 Does this change cross architecture boundaries?
 Does this affect public API contracts?
 Does this require database migration?
 Does this affect security, permission, auth, or secrets?
 Does this affect audit logs, snapshots, or state records?
 Does this affect scoring, evaluation, routing, or decision logic?
 Does this affect IP, asset, licensing, or compliance workflow?
 Is rollback simple?
Output format:



Boundary Review:
- Files: ...
- Modules: ...
- API Impact: Yes/No
- DB Impact: Yes/No
- Security Impact: Yes/No
- Audit Impact: Yes/No
- IP/Asset Impact: Yes/No
- Rollback: Simple/Moderate/Hard
Verdict: PASS / REVIEW / BLOCK
3.2 Context Gate

Required for S2 and above.

Purpose:

Verify that the task is safe, clear, and executable before implementation.

Checklist:

Environment: Are dependencies, runtime, and test data available?
Blocking Risk: Any risk of data loss, security issue, architecture violation, or irreversible change?
External Constraints: Are API contracts, module boundaries, compatibility, and user expectations preserved?
Input Completeness: Are requirements, boundaries, and acceptance criteria clear?
Output format:



Context Gate:
- Environment: PASS / REVIEW / BLOCK
- Blocking Risk: PASS / REVIEW / BLOCK
- External Constraints: PASS / REVIEW / BLOCK
- Input Completeness: PASS / REVIEW / BLOCK

Verdict: PASS / REVIEW / BLOCK
Reason:
- ...
Verdict rules:

PASS: Safe to proceed.
REVIEW: Ask clarification or propose options.
BLOCK: Stop and request human confirmation.
3.3 Principle Review

This review prevents superficial solutions.

Lite Review — for S2

Use Lite Review when the task is functional but not strategic.

Questions:

Minimal Change: Is there a smaller safe change?
Causal Impact: If we change A, what may break in B or C?
Falsification: What evidence would prove this solution wrong?
Output format:



Principle Review Lite:
- Minimal Change: ...
- Causal Impact: ...
- Falsification Condition: ...

Verdict: PASS / REVIEW / BLOCK
Full Review — for S3

Use Full Review when the task is architectural, strategic, security-sensitive, or irreversible.

Questions:

Assumption Reversal: What default assumption may be wrong?
Necessary Conditions: What must be true for this solution to work?
Bottleneck: What is the real bottleneck?
Minimal Sufficient Change: What is the smallest change that solves the core problem?
Causal Chain: What downstream effects may occur?
Failure Evidence: What would prove the plan is invalid?
Boundary Impact: What boundaries may be crossed?
Rollback Plan: How can we safely revert?
Output format:



Principle Review Full:
- Assumption Reversal: ...
- Necessary Conditions: ...
- Bottleneck: ...
- Minimal Sufficient Change: ...
- Causal Chain: ...
- Failure Evidence: ...
- Boundary Impact: ...
- Rollback Plan: ...

Verdict: PASS / REVIEW / BLOCK
3.4 Solution Quality Check

Purpose:

Evaluate whether the proposed solution is robust, maintainable, and reusable.

Lite — for S2

Check:

Does it solve the real problem?
Does it preserve modularity?
Is it easy to test?
Is it easy to rollback?
Output:



Solution Quality Lite:
- Core Problem Fit: High/Medium/Low
- Modularity: High/Medium/Low
- Testability: High/Medium/Low
- Rollback Safety: High/Medium/Low

Verdict: PASS / REVIEW / BLOCK
Full — for S3

Check:

Dimension	Question
Core Fit	Does the solution address the essential problem?
Orthogonality	Are responsibilities properly separated?
Reusability	Can the solution be reused or extended?
Auditability	Can decisions and changes be traced?
Risk Control	Are failure modes and rollback paths clear?
Strategic Alignment	Does it align with documented project principles?
Output:



Solution Quality Full:
- Core Fit: ...
- Orthogonality: ...
- Reusability: ...
- Auditability: ...
- Risk Control: ...
- Strategic Alignment: ...

Verdict: PASS / REVIEW / BLOCK
3.5 Strategic Alignment Check

This is a public and generic version of a decision-alignment check.

Purpose:

Ensure that the proposal aligns with documented project principles, not merely local convenience.

Use this especially for S2 and S3.

Check against the project’s published principles, such as:

Prefer clear boundaries over hidden coupling.
Prefer auditable workflows over opaque shortcuts.
Prefer reversible changes over irreversible mutations.
Prefer explicit contracts over implicit behavior.
Prefer maintainability over short-term speed.
Prefer minimal sufficient change over broad refactor.
Prefer documented decisions over silent assumptions.
Output:



Strategic Alignment:
- Alignment Status: ALIGNED / TENSION / NOVEL / BLOCK
- Matched Principles:
  - ...
- Tension Points:
  - ...
- Explanation:
  - ...

Decision:
- Proceed / Ask / Block
Definitions:

ALIGNED: Consistent with documented principles.
TENSION: Partially conflicts; explain before proceeding.
NOVEL: New direction; requires motivation and review.
BLOCK: Violates non-negotiable boundary; stop.
§4 Delivery Checklist

Every code-changing task must end with a delivery report.

Required fields:



## Delivery Report

### 1. Task Level
S0 / S1 / S2 / S3

### 2. Changed Files
- ...

### 3. What Changed
- ...

### 4. Validation Commands
```bash
# commands here
5. Validation Results

PASS / FAIL / NOT RUN
Reason if not run: ...
6. Boundary Review Result

PASS / REVIEW / BLOCK
7. API / DB / Security Impact

API: Yes/No
DB: Yes/No
Security: Yes/No
Audit: Yes/No
IP/Asset: Yes/No
8. Documentation Sync

Updated: Yes/No/Not needed
Files: ...
9. Rollback Plan

...
10. Residual Risk

Low / Medium / High
Details: ...


---

## §5 Development Environment Template

This public template intentionally does not include real infrastructure, private paths, or deployment secrets.

Projects may define their own environment section using placeholders:

```markdown
### Local Development

- Runtime:
- Package manager:
- Start command:
- Test command:
- Lint command:
- Build command:

### Staging

- Deployment method:
- Required approval:
- Rollback method:

### Production

- Deployment method:
- Required approval:
- Monitoring:
- Rollback method:
5.1 Environment Detection

Optional example:



# Example only. Replace with your project’s own command.
cat .project_env
Expected values:



local
staging
production
Rules:

If environment is unknown, assume higher risk.
If command targets production, require human confirmation.
If secrets are required, do not print or store them in logs.
§6 Testing and Validation

The AI agent should prefer project-defined commands.

Example:



# Install
npm install

# Lint
npm run lint

# Test
npm test

# Type check
npm run typecheck

# Build
npm run build
If no test command exists:



Validation:
- Automated test: NOT RUN
- Reason: No test command found
- Manual check performed: ...
- Risk: Medium
Never claim tests passed if they were not actually run.

§7 Documentation Rules

Update documentation when changing:

Public API.
Configuration.
Environment variables.
Database schema.
User-facing behavior.
Developer workflow.
Security or permission behavior.
Deployment process.
Asset/IP/compliance-related workflow.
Documentation output:



Documentation Sync:
- Needed: Yes/No
- Updated Files:
  - ...
- Not Updated Because:
  - ...
§8 Audit and Traceability

For important changes, preserve traceability.

Recommended records:

What changed.
Why it changed.
Who approved it.
What tests were run.
What risk was identified.
What rollback exists.
What decision was made.
Do not delete:

Audit logs.
Migration history.
Release notes.
Approval records.
State snapshots.
Incident reports.
If cleanup is required, propose an archival strategy instead of deletion.

§9 AI Agent Behavior Rules

The AI agent should:

Be explicit about uncertainty.
Ask when risk is unclear.
Prefer small reversible changes.
Explain non-trivial decisions.
Preserve project boundaries.
Follow existing style and conventions.
Avoid inventing APIs, files, or commands.
Avoid hiding failures.
Avoid broad refactors unless requested.
Report what was not done.
The AI agent should not:

Pretend to have run commands.
Silently ignore failing tests.
Remove safety checks.
Introduce secrets into code.
Make production changes without confirmation.
Use destructive commands without approval.
Expand task scope without asking.
§10 Escalation Rules

Escalate to human review if:

Requirement is ambiguous.
Risk level is uncertain.
Change touches security, data, architecture, or production.
There is no rollback plan.
The task affects public contracts.
The change may affect compliance or IP-sensitive workflow.
The agent detects conflict between user request and safety rules.
Escalation output:



Escalation Required:
- Reason:
- Risk:
- Proposed Options:
  1. ...
  2. ...
  3. ...
- Recommended Option:
- Awaiting Confirmation: Yes
§11 Optional Project-Specific Extensions

A project may add private rules in a separate file:

AGENTS.private.md

Recommended separation:

File	Purpose
AGENTS.public.md	Public, reusable AI collaboration protocol
AGENTS.private.md	Private project-specific rules, paths, infra, sensitive modules
SECURITY.md	Security reporting and handling
CONTRIBUTING.md	Human contributor workflow
ARCHITECTURE.md	System architecture
DECISIONS.md	Architecture decision records
Do not publish private:

Server IPs.
SSH commands.
Internal domains.
Deployment credentials.
Secret names or secret values.
Protected module paths.
Proprietary algorithms.
Patent-sensitive implementation details.
Customer or production data.
§12 Minimal Public Version

If the full protocol is too heavy, use this compact version:



# AI Agent Safety Rules

1. Classify task as S0/S1/S2/S3 before acting.
2. S3 requires human confirmation.
3. Do not break architecture boundaries.
4. Do not delete logs, data, or history.
5. Do not bypass security, approval, or routing.
6. Do not modify protected core logic without review.
7. Prefer minimal reversible changes.
8. Run tests and report actual results.
9. Update docs when API/config/schema behavior changes.
10. Escalate when uncertain.
Appendix A — Recommended Pull Request Format



## Summary

## Task Level
S0 / S1 / S2 / S3

## Review Type
None / Lite / Full

## Changes
- ...

## Validation
- [ ] Lint
- [ ] Tests
- [ ] Type check
- [ ] Build
- [ ] Manual verification

## Risk
- Low / Medium / High

## API Impact
Yes / No

## DB Impact
Yes / No

## Security Impact
Yes / No

## Audit / Traceability Impact
Yes / No

## IP / Asset / Compliance Impact
Yes / No

## Rollback Plan

## Human Confirmation Required
Yes / No
Appendix B — Public Disclosure Notice

This file is a general AI collaboration safety template.

It intentionally excludes:

Proprietary algorithms.
Internal architecture details.
Protected implementation paths.
Production infrastructure.
Deployment credentials.
Patent-sensitive claims or embodiments.
Private decision memory.
Customer or business confidential information.
For production use, maintain a separate private rules file.



---

# 我建议你的 GitHub 仓库结构

如果你准备开源，建议不要只放一个文件，而是包装成一个小型“AI Agent Governance Template”仓库。

推荐结构：

```text
ai-agent-collaboration-protocol/
├── README.md
├── AGENTS.public.md
├── templates/
│   ├── AGENTS.minimal.md
│   ├── AGENTS.full.md
│   ├── PR_TEMPLATE.md
│   ├── S3_REVIEW_TEMPLATE.md
│   └── DELIVERY_REPORT_TEMPLATE.md
├── examples/
│   ├── node-react/
│   │   └── AGENTS.md
│   ├── python-fastapi/
│   │   └── AGENTS.md
│   └── monorepo/
│       └── AGENTS.md
├── docs/
│   ├── task-levels.md
│   ├── lite-vs-full-review.md
│   ├── strategic-alignment.md
│   └── private-rules.md
├── LICENSE
└── SECURITY.md
README.md 建议文案

你可以这样写：



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

```text
AGENTS.private.md
Do not commit secrets, internal infrastructure, proprietary algorithms, or patent-sensitive implementation details.
