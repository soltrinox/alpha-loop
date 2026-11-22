# SA5 — Newsletter security profile demo

**Date:** 2026-11-21 (PT) / 2026-11-22 (UTC run)  
**Workspace:** `/Users/rosario/work/ALPHA-LOOP`  
**Plan:** `security_milestone_gate_bccbd649` SA5 only (plan file not edited)  
**Commit:** `177c266bf727370e0db363f75cf548ddf75cd096` (pushed to `origin/master`)
## Delivered

- `examples/newsletter-signup/` — Next.js signup form, `POST /api/signup`, `GET /api/health`, store under `data/` (not public)
- `Dockerfile` → image `newsletter-signup:template` (build only when tag missing)
- `docker-compose.yml` starts from that image (host port `3100` by default)
- `.alpha-loop.yaml` — `security_checks: true`; both profiles enabled at defaults; agent not forced off
- `templates/security-profiles/oracles.json` — application checks only (health, empty reject, valid accept, store not public)
- `test-security-e2e.sh` + `scripts/run-security-executor.mjs` + `scripts/oracle-checks.mjs`
- `DRY_RUN=1` path for report shape without live Docker/gh
- Docs: Newsletter demo section in `docs/security-profiles.md`

## Live run evidence

| Check | Result |
|-------|--------|
| First image build | Built once; tag `newsletter-signup:template` id `sha256:b052904fa538…` |
| Second script run | Logged `already present — skip build` |
| Health | `GET http://127.0.0.1:3100/api/health` → 200 |
| Demo repo | `soltrinox/newsletter-signup-demo` created; branches `security-run/<ts>` |
| Milestones / issues | `security-check` issues + milestones on demo repo only |
| Report | application **PASS** (T1190, T1133, T1078, T1552); agent **NOT_APPLICABLE**; overall **PASS** |
| Compose down | Ran; image retained |

Evidence under `test-results/newsletter-security-demo/` (`.log.txt` + `security-profile-report-*.md`).

## Re-run

```bash
pnpm build
./examples/newsletter-signup/test-security-e2e.sh
# DEMO_REPO=owner/name DEMO_FORK=1 DRY_RUN=1 also supported
```
