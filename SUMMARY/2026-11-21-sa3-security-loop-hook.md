# SA3 — Security milestone loop hook

**Date:** 2026-11-21  
**Workspace:** `/Users/rosario/work/ALPHA-LOOP`  
**Scope:** Wire `--sec-mile` / `--skip-sec` into `init` and `run`; hide security-check-only milestones from `pickTarget`; run the session security executor once after the product-test gate.

## Changes

- `src/cli.ts`: `--sec-mile` on `init` and `run`; `--skip-sec` and `-y/--yes` on `run`
- `src/commands/init.ts`: after scan (step 7), call `securityCommand` when `--sec-mile`
- `src/commands/run.ts`: selector before `pickTarget`; `--yes --sec-mile` without a plan file exits; filter security-only milestones; session gate after `runFullSuiteGate` (non-quick)
- `src/lib/pipeline.ts`: session gate inside `finalizeQuickRun` after the quick product-test gate
- `src/lib/security-gate.ts`: filter helpers, proof table, session gate orchestration
- `src/lib/security-executor.ts`: `skipReason` for `--skip-sec` NOT_RUN path
- `src/lib/session.ts`: append `securityProofMarkdown` to the session PR body

## Anti-scope honored

- Did not change `buildPlanPrompt`, `buildRoadmapPrompt`, pipeline step 5, `run --verify-only`, or `evolve`
- Did not start SA4–SA5

## Tests

```bash
npm test -- tests/lib/security-gate.test.ts tests/lib/security-executor.test.ts \
  tests/cli.test.ts tests/commands/init.test.ts tests/commands/run.test.ts \
  tests/commands/security.test.ts
```

Evidence: all listed suites PASS.
