# AI Agent Safety Rules

## Task Levels

- S0: Read-only analysis.
- S1: Small local change.
- S2: Multi-file functional change.
- S3: Architecture/security/data/IP/production-sensitive change.

## Rules

1. Classify the task before acting.
2. S3 requires human confirmation.
3. Do not break architecture boundaries.
4. Do not bypass approved interfaces or routing.
5. Do not delete logs, data, migrations, or history.
6. Do not modify protected core logic without review.
7. Do not change security, auth, permissions, or production deployment without approval.
8. Prefer minimal reversible changes.
9. Run available tests and report actual results.
10. Escalate when uncertain.

## Delivery Report

Always report:

- changed files,
- what changed,
- validation commands,
- validation results,
- API/DB/security impact,
- rollback plan,
- residual risk.
