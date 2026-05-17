# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| Latest (`main`) | Yes |
| Older releases | No |

## Reporting a Vulnerability

If you find a security issue (e.g., prompt injection, unintended data exposure, configuration leakage), **do not open a public issue**.

Instead, use GitHub's [Private Vulnerability Reporting](https://github.com/Destined-at-Dawn/research-daily/security/advisories):

1. Go to the Security Advisories page.
2. Click "Report a vulnerability."
3. Describe what you found, how to reproduce it, and potential impact.

Response time: within 7 days.

## Scope

### In Scope

- **Prompt injection** — inputs that cause the skill to bypass grading criteria or output constraints
- **Configuration leakage** — skill behavior that exposes user-specific config (keywords, profiles, API endpoints)
- **Data exfiltration** — skill behavior that sends user research data to unintended external services
- **Path traversal** — inputs that cause the skill to read/write files outside the configured workspace

### Out of Scope

- AI output quality (hallucinations, incorrect paper analysis) — these are research limitations, not security vulnerabilities
- Feature requests — use [Issues](https://github.com/Destined-at-Dawn/research-daily/issues)
- Third-party API rate limits (arXiv, IEEE) — these are external service constraints

## Privacy Commitment

Research Daily processes all data locally within your Claude Code workspace. No research data, paper analysis, or user profiles are sent to external servers beyond the standard Claude API calls. Configuration files remain in your local workspace and are never uploaded unless you explicitly push them to your own repository.
