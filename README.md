<div align="center">

# 🔍 SEO Toolkit for Claude

**A curated collection of production-grade Claude Skills for SEO workflows.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Claude](https://img.shields.io/badge/Claude-Skills-8B5CF6)](https://claude.ai)
[![MCP](https://img.shields.io/badge/MCP-Compatible-00A67E)](https://modelcontextprotocol.io)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

Battle-tested skills from real SEO agency work — distilled, cleaned, and shared back with the community.

[Skills](#-available-skills) · [Installation](#-installation) · [MCP Setup](docs/MCP-SETUP.md) · [Contributing](CONTRIBUTING.md) · [Roadmap](#-roadmap)

</div>

---

## 🎯 What is this?

**SEO Toolkit** is a monorepo of [Claude Skills](https://docs.claude.com) purpose-built for SEO professionals. Each skill is a self-contained workflow that extends Claude Desktop with domain-specific expertise — from keyword research to content production to technical audits.

These skills have been refined across hundreds of real client projects spanning finance, healthcare, e-commerce, and B2B industries in Vietnamese, US, and UK markets.

### Why use these skills?

- ⚡ **Production-ready** — not toy examples; battle-tested in real agency work
- 🔌 **MCP-native** — deeply integrated with SerpAPI, Ahrefs, Google Keyword Planner, Knowledge Graph
- 🌏 **Bilingual** — triggers in both English and Vietnamese
- 📦 **Modular** — install only the skills you need
- 🆓 **MIT licensed** — free for commercial use

---

## 📦 Available Skills

### ✅ Released

| Skill | Description | Status |
|---|---|---|
| [**outline-content**](skills/outline-content/) | Build comprehensive SEO content outlines from a target keyword. SERP Top 10 analysis, competitor heading extraction, search intent mapping, and Writer Briefing generation. | `v1.0` |

---

## 🗺️ Roadmap

Skills in active development, coming to this toolkit:

| Skill | Description | ETA |
|---|---|---|
| **qc-content** | 11-dimension quality control scorecard for SEO content. Anti-AI-pattern detection, GEO/AEO readiness checks, and Pass/Fix/Fail verdicts. | Q2 2026 |
| **seo-drift** | "Git for SEO" — baseline snapshot of on-page SEO fields, detect regressions after deployment, compare before/after. | Q2 2026 |
| **data-cache** | Local cache wrapper for MCP SEO tools (Ahrefs, GSC, SerpAPI) to save API credits on repeated queries. | Q3 2026 |
| **keyword-research** | Multi-mode keyword research (seed expansion, URL analysis, list enrichment) with silo grouping. | Q3 2026 |

Have a skill idea? [Open a discussion](../../discussions).

---

## 🚀 Installation

### Install a single skill (recommended)

```bash
# Clone the repo
git clone https://github.com/ibangtam/seo-toolkit.git
cd seo-toolkit

# Copy the skill you want into Claude Desktop's skills directory
# macOS
cp -r skills/outline-content ~/Library/Application\ Support/Claude/skills/

# Windows (PowerShell)
Copy-Item -Recurse skills\outline-content $env:APPDATA\Claude\skills\
```

Restart Claude Desktop.

### Install all skills at once

```bash
# macOS
cp -r skills/* ~/Library/Application\ Support/Claude/skills/

# Windows (PowerShell)
Copy-Item -Recurse skills\* $env:APPDATA\Claude\skills\
```

Full installation guide: [docs/INSTALL.md](docs/INSTALL.md)

---

## 🔌 MCP Servers

These skills are designed to work with MCP (Model Context Protocol) servers for SEO tooling. Each skill declares its preferred MCP servers and gracefully falls back to built-in `web_search` and `web_fetch` when MCPs aren't available.

Commonly required servers:
- **SerpAPI MCP** — SERP data, keyword suggestions, PAA
- **Ahrefs MCP** — volume, KD, backlinks, organic keywords
- **Google Keyword Planner MCP** — volume alternative
- **Knowledge Graph MCP** — entity enrichment, Schema @type

Full MCP setup guide: [docs/MCP-SETUP.md](docs/MCP-SETUP.md)

---

## 💡 How these skills work together

Each skill is self-contained but designed to chain with others in a full SEO workflow:

```
┌─────────────────────────┐
│  1. Keyword Research    │  (coming soon)
│  keyword-research       │
└────────────┬────────────┘
             ▼
┌─────────────────────────┐
│  2. Content Outline     │  ✅ available now
│  outline-content        │
└────────────┬────────────┘
             ▼
┌─────────────────────────┐
│  3. Content Writing     │  (private, agency-only)
└────────────┬────────────┘
             ▼
┌─────────────────────────┐
│  4. Quality Control     │  (coming soon)
│  qc-content             │
└────────────┬────────────┘
             ▼
┌─────────────────────────┐
│  5. Deployment Check    │  (coming soon)
│  seo-drift              │
└─────────────────────────┘
```

---

## 🤝 Contributing

Contributions are warmly welcome — bug fixes, new skills, documentation improvements, translations.

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## 👤 Author

**Nguyễn Sĩ Nguyên** — Founder, [SEO Bang Tam Agency](https://seobangtam.com/)

10+ years in SEO. Building content workflows and automation for clients in Vietnam, US, and UK markets across finance, banking, healthcare, furniture, and real estate industries.

- GitHub: [@ibangtam](https://github.com/ibangtam)
- Website: [seobangtam.com](https://seobangtam.com/)

---

## ⭐ Star History

If these skills save you time, a star helps others discover them.

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

Free for commercial use. Attribution appreciated but not required.

---

<div align="center">

**Built with ❤️ for the SEO community**

</div>
