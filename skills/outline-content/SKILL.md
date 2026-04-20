---
name: outline-content
description: >
  Build a comprehensive SEO content outline from a target keyword. Automatically analyzes SERP Top 10, extracts competitor heading structures, identifies search intent, maps keywords, and outputs a detailed outline with H1/H2/H3 hierarchy, Meta Title, Meta Description, keyword mapping, Schema JSON-LD skeleton, and a ready-to-use Writer Briefing. Trigger when user mentions: "create outline", "generate outline", "SEO outline", "content brief", "article outline", "build outline", "outline for keyword", or Vietnamese equivalents: "lên outline", "outline content", "tạo outline", "dàn ý bài viết", "outline SEO", "brief content", "content brief", "lên dàn ý", "outline bài", "xây dựng outline". Also triggers when user provides a single keyword with a request to write an SEO article. Tools: SerpAPI MCP (priority) + Ahrefs MCP + Google Keyword Planner MCP + Knowledge Graph MCP. Output: H1/H2/H3 outline + Meta + Keyword Map + Schema JSON-LD skeleton + Writer Briefing.
---

# SEO Content Outline — 7-Step Workflow

**Tools:** SerpAPI MCP (priority) · Ahrefs MCP · Google Keyword Planner MCP · Knowledge Graph MCP
**Output:** H1/H2/H3 outline + Meta + Keyword Map + Schema skeleton + Writer Briefing
**Estimated time:** 8–15 minutes

---

## INPUT DETECTION

```
Single keyword                      →  SINGLE MODE  (full 7 steps)
Keyword + URL                       →  SITE MODE    (+ Step 0: analyze existing page)
Keyword + niche/industry            →  NICHE MODE   (Step 2 expands with English SERP)
```

**Confirm with user before Step 1:**
- What is the focus keyword?
- Domain/website (for internal link suggestions)? *(optional)*
- Article language: English / Vietnamese / other?
- Page type: Blog informational / Category / Product / Landing page?
- Specific tone of voice? *(professional / friendly / authoritative / casual)*

---

## STEP 1 — SERP ANALYSIS (SerpAPI priority)

### 1.1. Fetch SERP Top 10

```
Tool: serpapi:google_search
Params:
  query: {focus_keyword}
  location: target country (e.g., "United States", "Vietnam")
  hl: language code (e.g., "en", "vi")
  num: 10
```

Extract:
- Top 10 organic results (URL, title, snippet)
- People Also Ask (PAA) — all questions
- Related Searches
- Featured Snippet (if present)
- Knowledge Panel (if present)
- SERP Features: Video, Image Pack, Local Pack, Shopping, News

### 1.2. Classify SERP Format

Count page types appearing in Top 10:
- Blog/Article: how many URLs?
- Product/Category: how many URLs?
- Landing page: how many URLs?
- Video/Forum/Other: how many URLs?

→ **SERP Dominant Format** = the type accounting for ≥6/10 results.

### 1.3. Determine Search Intent

Based on SERP Format + keyword semantics:
- **Informational**: SERP dominated by blogs, how-tos, guides → explanatory article
- **Commercial Investigation**: SERP contains reviews, comparisons, "best X" → comparison article
- **Transactional**: SERP contains product pages, "buy", "price" → landing/product page
- **Navigational**: SERP is brand-specific → not suitable for new content

### 1.4. Step 1 Output

```
SERP Analysis Summary:
- Dominant Format: [Blog Article / Product / Landing / Mixed]
- Search Intent: [Informational / Commercial / Transactional]
- SERP Features: [list]
- Top 3 Competitors: [URL 1, URL 2, URL 3]
- PAA Questions: [all, max 10]
- Related Searches: [list]
```

---

## STEP 2 — COMPETITOR HEADING EXTRACTION

### 2.1. Fetch Top 3-5 Competitor Content

```
Tool: web_fetch
URLs: Top 3-5 from SERP in Step 1
```

Extract heading structure per page:
- H1 (1 per page)
- All H2s
- H3s nested under each H2

### 2.2. Heading Frequency Matrix

Build a frequency table of H2s shared across competitors:

```
H2 Topic                          | URL 1 | URL 2 | URL 3 | Frequency
----------------------------------|-------|-------|-------|----------
Definition / Concept              |   ✓   |   ✓   |   ✓   |   3/3
Benefits                          |   ✓   |   ✓   |       |   2/3
How to implement                  |   ✓   |       |   ✓   |   2/3
...                               |       |       |       |
```

### 2.3. Classify H2s

- **MUST HAVE**: Frequency ≥2/3 → mandatory in outline
- **SHOULD HAVE**: Frequency 1/3 + intent match → recommended
- **COULD HAVE**: Frequency 0/3 but hinted by PAA/related searches → differentiator

---

## STEP 3 — ENTITY & TOPIC ENRICHMENT

### 3.1. Knowledge Graph lookup

```
Tool: knowledge-graph:search_knowledge_graph
Query: {focus_keyword}
```

Extract:
- Entity type (@type for Schema)
- Related entities
- Authoritative description

### 3.2. Map entities to outline

Each entity should be mapped to a specific H2/H3 to increase topical depth. Record:

```
Entity: [name]
Type: [Person / Organization / Place / Thing / ...]
Relevance: [High / Medium / Low]
Suggested placement: H2 "[H2 name]"
```

---

## STEP 4 — KEYWORD EXPANSION & VOLUME

### 4.1. Keyword suggestions (SerpAPI priority)

```
Tool: serpapi:keyword_suggestions
Query: {focus_keyword}
```

Returns: autocomplete + related searches + PAA (1 call covers all).

### 4.2. Enrich with volume/KD/Intent (Ahrefs secondary)

```
Tool: ahrefs:keywords-explorer-matching-terms
Params:
  keyword: {focus_keyword}
  country: en (or target country code)
  limit: 50
```

Gets: Volume, KD, CPC, Intent for each keyword variant.

### 4.3. Keyword Grouping

```
PRIMARY KEYWORD      → H1 + Title + opening sentence
SECONDARY KEYWORDS   → main H2s (3-5 keywords)
LSI/SEMANTIC         → H3 + body text
LONG-TAIL            → FAQ section + internal anchor text
```

---

## STEP 5 — OUTLINE CONSTRUCTION

### 5.1. Standard Layout

```
H1: {Main title — contains PRIMARY keyword naturally}

Intro paragraph (50-80 words):
- Opening hook
- Mention PRIMARY keyword in first sentence
- Promise to the reader

H2 (1): {MUST HAVE from Frequency Matrix}
  H3 (1.1): ...
  H3 (1.2): ...

H2 (2): {MUST HAVE from Frequency Matrix}
  H3 (2.1): ...

H2 (3): {SHOULD HAVE}
  H3 (3.1): ...

H2 (4): {COULD HAVE — differentiator}

H2 (5): FAQ
  H3: [PAA Question 1]
  H3: [PAA Question 2]
  H3: [PAA Question 3]

Conclusion (CTA):
- Summary
- Internal link suggestions
- Call-to-action
```

### 5.2. Classify MACRO vs MICRO

Mark each H2 as:
- **MACRO**: Long section, multiple H3s, >300 words — provides depth
- **MICRO**: Short section, 1-2 paragraphs, <200 words — quick supporting facts

Recommended ratios:
- Informational: ≥60% MACRO
- Commercial: ≥50% MACRO
- Landing page: ≥40% MACRO

### 5.3. Word Count Estimate

```
Estimate = (number of H2s × 200) + (number of H3s × 100) + (intro 80 + conclusion 100)
```

Compare to Top 3 SERP: target ≥80% of the top-ranking page's word count.

---

## STEP 6 — META & SCHEMA

### 6.1. Meta Title

```
Rules:
- Max 60 characters
- PRIMARY keyword within the first 30 characters
- Add a compelling modifier: number, year, "best", "complete", "2026"
- Format: {Keyword} {Modifier} | {Brand if applicable}
```

Suggest 3 options for user to choose.

### 6.2. Meta Description

```
Rules:
- 140-160 characters
- PRIMARY keyword within the first 120 characters
- Benefit + CTA
- Avoid duplication with other pages on the site
```

Suggest 2 options.

### 6.3. Schema JSON-LD Skeleton

Choose @type based on page type + entity from Step 3:

```json
// Blog/Article
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "",
  "author": { "@type": "Person", "name": "" },
  "datePublished": "",
  "dateModified": "",
  "mainEntityOfPage": ""
}

// FAQ
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "",
      "acceptedAnswer": { "@type": "Answer", "text": "" }
    }
  ]
}

// Product / Service — depending on page type
```

---

## STEP 7 — WRITER BRIEFING

The briefing handed to the writer must include:

```markdown
# BRIEF: {Focus Keyword}

## 1. Basic Info
- Focus Keyword:
- Search Volume:
- KD:
- Search Intent:
- Target Word Count:
- Deadline:

## 2. SERP Context
- Top 3 competitors (URL)
- Dominant format
- SERP Features to target: Featured Snippet / PAA / ...

## 3. Tone of Voice
- Target persona
- Tone: [professional / friendly / authoritative / casual]
- POV: first person / second person / third person
- Good sample sentence / bad sample sentence

## 4. Complete Outline
[paste outline from Step 5]

## 5. Keyword Map
| Section | Primary KW | Secondary | LSI |
|---------|-----------|-----------|-----|
| H1      |           |           |     |
| Intro   |           |           |     |
| H2 (1)  |           |           |     |
...

## 6. Meta
- Title (3 options):
- Description (2 options):
- Schema @type:

## 7. Internal Link Suggestions
- Link to: [URL 1] — suggested anchor: "..."
- Link to: [URL 2] — suggested anchor: "..."

## 8. External Sources (citations)
- Which statistics need a source
- Which entities need a Wikipedia/official site reference

## 9. Must-Have Elements
- [ ] Primary keyword in H1
- [ ] Primary keyword in opening sentence
- [ ] FAQ section with 5-7 questions from PAA
- [ ] CTA at the end
- [ ] Schema markup with correct @type
```

---

## FINAL OUTPUT

The skill returns to the user:

1. **SERP Analysis Summary** (Step 1)
2. **Heading Frequency Matrix** (Step 2)
3. **Entity Map** (Step 3)
4. **Keyword Map with volume/KD** (Step 4)
5. **Full Outline** (Step 5)
6. **Meta Title/Description options + Schema skeleton** (Step 6)
7. **Writer Briefing** (Step 7) — markdown format ready to paste into a doc

---

## PROHIBITED

This skill does NOT:
- Write the full article content (that's the job of the `content-writing` skill)
- Skip SERP analysis steps (Steps 1-2 are mandatory)
- Auto-select a keyword when the user has already provided one
- Generate an outline without actual SERP data

---

## NOTES

- If SerpAPI quota is exhausted → fall back to manual `web_search` + `web_fetch`
- If Ahrefs is unavailable → use Google Keyword Planner MCP as a volume source
- If Knowledge Graph doesn't match an entity → skip Step 3, it's not mandatory
- For Vietnamese articles, set `hl: "vi"` and `location: "Vietnam"`
- For English articles, set `hl: "en"` and `location: "United States"` (or target country)
