# SA1 — Security surfaces and selector

**Date:** 2026-11-21  
**Repo:** ALPHA-LOOP  
**Scope:** SA1 only (surfaces + selector). SA2–SA5 not started in this change set.

## Delivered

- `src/lib/security-surfaces.ts` — application surfaces from `.alpha-loop/context.md` and file signals; agent `mcp` surface only when the selected agent's MCP config names a server; optional model JSON accepted only for the closed application-surface set.
- `src/commands/security.ts` — step 1 surface report; step 2 oracle-backed technique checkbox; `Show surfaces that were not detected` defaults unchecked; confirm creates milestones/issues with `security-check` (not `ready`); dry run writes `.alpha-loop/security-plan.json` only.
- `src/lib/config.ts` — `writeSecurityChecks()` sets `security_checks: true`.
- Unit tests: `tests/lib/security-surfaces.test.ts`, `tests/commands/security.test.ts`, `writeSecurityChecks` in `tests/lib/config.test.ts`.

## Test evidence

```text
pnpm test -- tests/lib/security-surfaces.test.ts tests/commands/security.test.ts \
  tests/lib/security-catalog.test.ts tests/lib/security-plan.test.ts
# 4 suites, 19 passed
```

## Done-when check

- Fixture with `.mcp.json` and no cloud SDK: offers `mcp`, omits `cloud-control-plane`.
- Dry run writes `.alpha-loop/security-plan.json` only (no GitHub, no config writer).
