# Newsletter Docker synth test — evidence check

**Date:** 2026-11-21 (PT)  
**Workspace:** `/Users/rosario/work/ALPHA-LOOP`  
**Question:** Was a synthetic test run on `newsletter-signup:template` with a temporary/demo repo so milestones insert correctly?

## Verdict

**Yes.** A prior live SA5 synthetic run already completed. No re-run was required.

## Verified evidence

| Item | Value |
|------|--------|
| Template image | `newsletter-signup:template` (`b052904fa538`, present locally) |
| Demo repo | `soltrinox/newsletter-signup-demo` (default branch `main` unchanged as template) |
| Run branch | `security-run/20261122-062940` (also `security-run/20261122-062833`) |
| Health | `GET http://127.0.0.1:3100/api/health` → 200 |
| Application | **PASS** (T1078, T1133, T1190, T1552) |
| Agent | **NOT_APPLICABLE** |
| Overall | **PASS** |

### Milestones on demo repo

1. `Security: T1078 (public-http)`
2. `Security: T1133 (public-http)`
3. `Security: T1190 (public-http)`
4. `Security: T1552 (credentials-at-rest)`

### `security-check` issues (open)

First run: #1–#4. Second run (reused milestones): #5–#8.

### Report path

`test-results/newsletter-security-demo/security-profile-report-20261122-062940.md`

Log: `test-results/newsletter-security-demo/e2e-20261122-062940.log.txt` (`overall=PASS`, image skip-build confirmed).

## Action taken this session

Inspect only. No new synth run. No image rebuild. No force-push. No commit.
