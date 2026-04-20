# outline-content

> Build comprehensive SEO content outlines from a target keyword.

Part of [SEO Toolkit for Claude](../../README.md).

## What it does

Analyzes SERP Top 10, extracts competitor heading structures, identifies search intent, maps keywords, and generates a ready-to-use Writer Briefing in 8–15 minutes.

## Features

- ✅ SERP Analysis for Top 10 results
- ✅ Heading Frequency Matrix from top competitors
- ✅ Entity enrichment via Knowledge Graph
- ✅ Keyword expansion with volume/KD/intent metrics
- ✅ Full H1/H2/H3 outline with MACRO/MICRO classification
- ✅ Meta Title/Description (multiple options)
- ✅ Schema JSON-LD skeleton
- ✅ Writer Briefing in ready-to-paste markdown

## MCP Requirements

| Server | Role | Required? |
|---|---|---|
| SerpAPI MCP | SERP analysis + keyword suggestions | Recommended |
| Ahrefs MCP | Volume / KD / Intent enrichment | Optional |
| Google Keyword Planner MCP | Volume alternative to Ahrefs | Optional |
| Knowledge Graph MCP | Entity + Schema @type | Optional |

Falls back to `web_search` + `web_fetch` when no MCPs are available.

## Installation

From the repo root:

```bash
# macOS
cp -r skills/outline-content ~/Library/Application\ Support/Claude/skills/

# Windows (PowerShell)
Copy-Item -Recurse skills\outline-content $env:APPDATA\Claude\skills\

# Linux
cp -r skills/outline-content ~/.config/Claude/skills/
```

Restart Claude Desktop.

## Usage

Trigger the skill with any of these phrases in a Claude Desktop conversation:

**English**
```
"create an outline for the keyword [X]"
"generate SEO outline for [X]"
"build a content brief for [X]"
"outline an article about [X] for [domain]"
```

**Vietnamese**
```
"lên outline cho từ khóa [X]"
"tạo outline SEO cho [X]"
"làm content brief cho [X]"
"xây dựng outline cho [X]"
```

The skill will ask 3–5 clarifying questions (language, page type, tone, domain) before running the workflow.

## Workflow

```
Input keyword
    ↓
Step 1: SERP Analysis (SerpAPI)
Step 2: Competitor Heading Extraction
Step 3: Entity Enrichment (Knowledge Graph)
Step 4: Keyword Expansion (SerpAPI + Ahrefs)
Step 5: Outline Construction (H1/H2/H3 + MACRO/MICRO)
Step 6: Meta + Schema Skeleton
Step 7: Writer Briefing (markdown)
```

**Execution time:** 8–15 minutes per outline.

## Output

The skill returns 7 artifacts:

1. SERP Analysis Summary
2. Heading Frequency Matrix
3. Entity Map
4. Keyword Map (volume/KD/intent)
5. Full Outline
6. Meta options + Schema JSON-LD
7. Complete Writer Briefing (ready to paste into Google Docs)

## Example trigger

```
You: "Create an SEO outline for 'remote work productivity tips'
      for a blog audience, tone is friendly"

Claude: [triggers outline-content skill]
         [runs Steps 1-7 with clarifying questions]
         [outputs 7 artifacts]
```

## Philosophy

This skill deliberately does NOT:
- Write the full article (that's a separate content-writing skill)
- Skip SERP analysis (data-driven is non-negotiable)
- Auto-select keywords when you've provided one
- Generate outlines without real SERP data

If you need any of those behaviors, this isn't the skill for you — use a generic LLM prompt instead.

## Feedback

- 🐛 [Report a bug](../../../issues)
- 💡 [Request a feature](../../../discussions)
- ⭐ Star the [parent repo](../../) if this helps you
