# Security profile report

- Template image: `newsletter-signup:template`
- Template image ID: `sha256:b052904fa538580241563c1ed350515e5ca3b864e7b30dd8cf4a9f7aa140b50f`
- Demo repo: `soltrinox/newsletter-signup-demo`
- Branch: `security-run/20261122-062940`
- Base URL: `http://127.0.0.1:3100`
- Generated: 2026-11-22T06:30:16.109Z

## Application profile

- Source: https://github.com/mitre/cti
- Section result: **PASS**

| Technique | Milestone | Status | Reason |
|-----------|-----------|--------|--------|
| T1078 | Security: T1078 (public-http) | PASS | Exit code 0 matched passExit 0. |
| T1133 | Security: T1133 (public-http) | PASS | Exit code 0 matched passExit 0. |
| T1190 | Security: T1190 (public-http) | PASS | Exit code 0 matched passExit 0. |
| T1552 | Security: T1552 (credentials-at-rest) | PASS | Exit code 0 matched passExit 0. |

## Agent profile

- Source: https://github.com/secure-agentic-framework/saf-mcp
- Section result: **NOT_APPLICABLE**
- Reason: no MCP server configured for the selected agent
- Milestone count: 0

## Overall

**PASS** (application PASS + agent NOT_APPLICABLE)

