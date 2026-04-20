# MCP Server Setup

This guide covers setting up MCP (Model Context Protocol) servers commonly used by SEO Toolkit skills.

## What is MCP?

MCP is a protocol that lets Claude Desktop connect to external tools and data sources. Skills in this toolkit leverage MCP servers to access SERP data, keyword metrics, backlink analysis, and more.

Official docs: [modelcontextprotocol.io](https://modelcontextprotocol.io)

## Recommended MCP Servers for SEO

### 🔍 SerpAPI MCP

**Used by:** `outline-content`, `keyword-research` (upcoming), `qc-content` (upcoming)

**Purpose:** Fetch real-time SERP data, keyword suggestions, PAA, related searches.

**Get an API key:** [serpapi.com](https://serpapi.com/) (free tier: 100 searches/month)

**Setup:** Search GitHub for `serpapi-mcp` or build your own wrapper using the SerpAPI REST API.

### 📊 Ahrefs MCP

**Used by:** `outline-content`, `keyword-research` (upcoming), `seo-drift` (upcoming)

**Purpose:** Volume, KD, backlinks, organic keywords, domain metrics.

**Requirements:** Ahrefs subscription with API access.

**Setup:** See [Ahrefs API docs](https://docs.ahrefs.com/) for official MCP integration.

### 🎯 Google Keyword Planner MCP

**Used by:** `outline-content`, `keyword-research` (upcoming)

**Purpose:** Free alternative for search volume when Ahrefs isn't available.

**Requirements:** Google Ads account with API access.

**Setup:** Search GitHub for community-built `google-keyword-planner-mcp` implementations.

### 🧠 Knowledge Graph MCP

**Used by:** `outline-content`

**Purpose:** Entity lookup, Schema @type suggestion, topical authority signals.

**Requirements:** Google Cloud API key with Knowledge Graph Search API enabled.

**Setup:** Search GitHub for `google-knowledge-graph-mcp`.

### 📈 Google Search Console MCP

**Used by:** `qc-content` (upcoming), `seo-drift` (upcoming)

**Purpose:** Real query/page performance, striking distance keywords, cannibalization detection.

**Requirements:** Google Search Console account access.

**Setup:** Search GitHub for `gsc-mcp` community implementations.

## Configuring MCP Servers in Claude Desktop

MCP servers are configured in Claude Desktop's config file:

### macOS
```
~/Library/Application Support/Claude/claude_desktop_config.json
```

### Windows
```
%APPDATA%\Claude\claude_desktop_config.json
```

Example config structure:

```json
{
  "mcpServers": {
    "serpapi": {
      "command": "node",
      "args": ["/path/to/serpapi-mcp/server.js"],
      "env": {
        "SERPAPI_API_KEY": "your_key_here"
      }
    },
    "ahrefs": {
      "command": "python",
      "args": ["/path/to/ahrefs-mcp/server.py"],
      "env": {
        "AHREFS_API_KEY": "your_key_here"
      }
    }
  }
}
```

Restart Claude Desktop after editing the config.

## No MCP? No problem.

Every skill in this toolkit is designed to **gracefully degrade** when MCP servers aren't available:

- SerpAPI unavailable → falls back to Claude's built-in `web_search`
- Ahrefs unavailable → uses Google Keyword Planner or `web_search`
- Knowledge Graph unavailable → skips entity enrichment step

You can use these skills with zero MCP setup — just with reduced data quality.

## Recommended Starter Stack

If you're new to MCP and SEO tooling, start here:

1. **SerpAPI** (free tier) — covers SERP analysis for most skills
2. **Google Knowledge Graph** (free tier) — entity enrichment
3. **Ahrefs** (paid) — add when you need keyword volume/KD at scale

This gets you 80% of the toolkit's value for ~$0/month.

## Questions?

Open a [Discussion](../../discussions) with the skill name and the MCP error you're hitting.
