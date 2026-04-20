# Contributing to SEO Toolkit

Thanks for your interest in contributing! This project is open to contributions from the SEO and Claude community.

## Ways to Contribute

### 🐛 Report Bugs
Found something broken? [Open an issue](../../issues/new) with:
- Which skill is affected
- What you expected vs what happened
- Steps to reproduce
- Your environment (macOS / Windows, Claude Desktop version)

### 💡 Suggest Features
Have an idea for a new skill or improvement? [Start a discussion](../../discussions/new) before opening a PR — this saves everyone time if the idea isn't a fit.

### 🔧 Submit Pull Requests

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Test the skill in Claude Desktop
5. Commit with a clear message
6. Push and open a PR

### 🌍 Translate
Skills currently support English and Vietnamese trigger phrases. PRs adding other language triggers (Spanish, Portuguese, Indonesian, etc.) are welcome.

## Skill Contribution Guidelines

If you want to add a new skill to this toolkit:

### Structure
```
skills/your-skill-name/
├── SKILL.md          # Required — the skill definition
├── README.md         # Required — usage documentation
└── references/       # Optional — additional reference docs
    └── *.md
```

### SKILL.md Requirements

- YAML frontmatter with `name` and `description`
- Clear trigger phrases (English at minimum, bilingual preferred)
- Step-by-step workflow
- Tool/MCP requirements explicitly listed
- Fallback behavior when MCPs unavailable
- Output format specification
- "PROHIBITED" section listing what the skill does NOT do

### Quality Bar

- **Production-tested**: the skill should have been used on real projects
- **Self-contained**: minimize dependencies on private infrastructure
- **No secrets**: no API keys, tokens, personal paths, or client names
- **Clear scope**: one skill = one well-defined job

### What doesn't fit here

- Generic Claude skills unrelated to SEO
- Skills that require proprietary APIs with no free/trial tier
- Skills that duplicate existing ones without meaningful differences
- Skills requiring infrastructure beyond Claude Desktop + MCP servers

## Code of Conduct

Be respectful, constructive, and professional. We're here to build useful tools together.

## Questions?

Open a [Discussion](../../discussions) — I'm happy to chat about ideas before you invest time in a PR.
