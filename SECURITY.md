# Security Policy

Thanks for helping keep SEO Toolkit and its users safe.

## Reporting a Vulnerability

If you discover a security issue with any skill in this toolkit — for example, a prompt injection vector, a way to leak API credentials, or any other security concern — please do **NOT** open a public issue.

Instead, contact privately via one of these channels:

- **GitHub**: DM [@ibangtam](https://github.com/ibangtam) through profile
- **Website**: Contact form at [seobangtam.com](https://seobangtam.com/)

### What to include

To help me investigate efficiently, please include:

- Which skill is affected (e.g., `outline-content`)
- A clear description of the issue
- Steps to reproduce
- Potential impact (what could an attacker do?)
- Any suggested mitigation (optional)

### Response timeline

- **Within 72 hours**: Initial acknowledgement
- **Within 7 days**: Assessment and confirmation
- **Coordinated disclosure**: We'll agree on a timeline before any public discussion

## Scope

This policy covers:

- Skill definitions in `skills/` — prompt injection, unsafe tool chaining, credential exposure
- Documentation in `docs/` and root files — misleading install instructions that could expose user data
- Example code snippets — anything that could compromise user systems if copied

This policy does NOT cover:

- Third-party MCP servers referenced in docs — report those to their respective maintainers
- Claude Desktop itself — report to Anthropic via their security channels
- User-provided API keys — these are your responsibility to secure

## Safe Harbor

If you make a good-faith effort to follow this policy when reporting an issue, I won't pursue legal action against you. Research responsibly, don't exploit issues in the wild, and we're on the same team.

## Credit

With your permission, I'll credit you in the changelog and release notes when the fix ships. If you prefer to remain anonymous, that's fine too.
