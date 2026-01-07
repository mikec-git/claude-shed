# Claude Code Asset Marketplace - Design Document

**Version:** 1.0
**Date:** January 6, 2026
**Status:** Draft

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Project Vision](#2-project-vision)
3. [Market Research](#3-market-research)
4. [Target Audience](#4-target-audience)
5. [Core Features](#5-core-features)
6. [Asset Types](#6-asset-types)
7. [User Flows](#7-user-flows)
8. [Discovery & Search](#8-discovery--search)
9. [Handling Duplicates & Similar Assets](#9-handling-duplicates--similar-assets)
10. [UI/UX Design](#10-uiux-design)
11. [Technical Architecture](#11-technical-architecture)
12. [Security Considerations](#12-security-considerations)
13. [MVP Scope](#13-mvp-scope)
14. [Future Monetization](#14-future-monetization)
15. [Success Metrics](#15-success-metrics)
16. [Open Questions](#16-open-questions)

---

## 1. Executive Summary

### What We're Building

A **unified marketplace for Claude Code assets** - the first platform to support all asset types (skills, hooks, sub-agents, commands, and CLAUDE.md snippets) in one place, with intelligent duplicate handling and quality-first curation.

### Key Differentiators

| Existing Platforms | Our Approach |
|-------------------|--------------|
| Skills only | Full asset suite from day one |
| Quantity over quality (60k+ unvetted) | Automated quality scoring |
| Overwhelming search results | Primary + alternatives pattern |
| No author tools | Analytics dashboard, future monetization |
| Basic discovery | Trending, categories, staff picks |

### Constraints

- **Solo developer, side project**
- **Free tier initially** - monetization after user growth
- **Fully automated curation** - no manual review for MVP

---

## 2. Project Vision

### Mission Statement

> Make it effortless for developers to discover, share, and install high-quality Claude Code assets - while handling the complexity of duplicates and similar tools intelligently.

### Core Principles

1. **Developer-Native** - Feels like a tool built by developers, for developers
2. **Quality Over Quantity** - Better to surface the best than list everything
3. **Non-Overwhelming** - Smart defaults, progressive disclosure
4. **Author-Friendly** - Easy to submit, transparent metrics, future monetization path
5. **Open Ecosystem** - Works with GitHub, supports the open SKILL.md standard

### Long-Term Vision

Become the **npm/PyPI of Claude Code** - the default place developers go to find and share Claude Code assets, with a sustainable author monetization model.

---

## 3. Market Research

### Existing Platforms Analysis

| Platform | Size | Strengths | Weaknesses |
|----------|------|-----------|------------|
| **SkillsMP** | 32,000+ | Largest catalog, semantic search | Low quality bar (2-star minimum) |
| **claude-plugins.dev** | Medium | CLI-first, 8+ IDE support | No GUI browsing |
| **claudecodeplugins.io** | 739 | Curated, excellent docs | Small catalog |
| **claudecodemarketplace.net** | 1,325 | User accounts, upvoting | Skills collection is small (64) |
| **Anthropic Official** | 29 | Pre-installed, trusted | Tiny, slow to add new plugins |

### Gaps Identified (Our Opportunities)

| Gap | Opportunity |
|-----|-------------|
| Skills-only focus | Support all asset types |
| No duplicate handling | Smart grouping algorithm |
| No author analytics | Basic metrics → paid detailed analytics |
| No monetization for authors | Future paid tiers |
| No security scanning | Automated safety checks (phase 2) |
| No verified publishers | Trust badges and verification |

### SKILL.md Standard

The marketplace will follow the **open SKILL.md specification** at [agentskills.io/specification](https://agentskills.io/specification), ensuring compatibility with:
- Claude Code
- OpenAI Codex CLI
- GitHub Copilot
- Cursor, Amp, Zed

**Required Fields:**
```yaml
---
name: my-skill              # Max 64 chars, lowercase, hyphens only
description: Does X when Y  # Max 1024 chars, triggers activation
---
```

**Optional Fields:** `allowed-tools`, `model`, `license`, `metadata`

---

## 4. Target Audience

### Primary Users

**Developers using Claude Code** who want to:
- Find skills/tools to enhance their workflow
- Discover what's popular and trending
- Compare similar tools before installing
- Share their own creations

### User Segments

| Segment | Needs | Features |
|---------|-------|----------|
| **Browsers** | Quick discovery, easy install | Search, categories, trending |
| **Power Users** | Filtering, comparison, saved collections | Advanced filters, favorites, history |
| **Authors** | Easy submission, visibility, metrics | GitHub integration, analytics |

### User Personas

**1. Alex - The Explorer**
- New to Claude Code
- Wants to see what's possible
- Browses categories, installs popular tools
- Needs: Clear categories, "best of" lists, easy install

**2. Sam - The Power User**
- Uses Claude Code daily
- Knows what they want, searches by keyword
- Compares alternatives before choosing
- Needs: Fast search, comparison features, detailed info

**3. Jordan - The Creator**
- Built useful skills/hooks
- Wants to share with community
- Cares about visibility and feedback
- Needs: Easy submission, install metrics, ratings

---

## 5. Core Features

### MVP Features (Phase 1)

| Feature | Description | Priority |
|---------|-------------|----------|
| **Browse by Category** | Skills, Hooks, Agents, Commands, Snippets | Must Have |
| **Keyword Search** | Fast, relevant results | Must Have |
| **Trending Section** | Assets growing in popularity | Must Have |
| **Popular Section** | Top K by installs | Must Have |
| **New Arrivals** | Recently added assets | Must Have |
| **Asset Detail Page** | Description, install command, author, stats | Must Have |
| **Copy Install Command** | One-click copy | Must Have |
| **GitHub OAuth** | For authors to submit | Must Have |
| **GitHub Auto-Discovery** | Index public repos with SKILL.md | Must Have |
| **Basic Ratings** | 5-star rating system | Must Have |
| **Save to Favorites** | Bookmark assets (requires account) | Should Have |
| **Share Button** | Share asset link | Should Have |
| **Author Dashboard** | View count, install count | Should Have |

### Phase 2 Features

| Feature | Description |
|---------|-------------|
| **Security Scanning** | Automated checks for hooks/commands |
| **Verified Authors** | Badge for trusted publishers |
| **Reviews with Text** | Written reviews, not just stars |
| **Collections/Bundles** | Group related assets |
| **Claude Code Plugin** | Browse from within Claude Code |
| **CLI Tool** | `npx marketplace install <asset>` |

### Phase 3 Features (Post-Monetization)

| Feature | Description |
|---------|-------------|
| **Detailed Analytics** | Time series, geography, referrers |
| **Promoted Listings** | Authors pay for visibility |
| **Premium Assets** | Paid skills/hooks |
| **Enterprise Features** | Private registries, SSO |

---

## 6. Asset Types

### Supported Asset Types

| Type | Icon | Color | Description |
|------|------|-------|-------------|
| **Skills** | ⚡ | Amber (#f5a623) | SKILL.md files that extend Claude's capabilities |
| **Hooks** | 🪝 | Purple (#a855f7) | Shell scripts that run before/after events |
| **Sub-Agents** | 🤖 | Cyan (#22d3ee) | Specialized agent definitions |
| **Commands** | 📜 | Green (#22c55e) | Slash commands for quick actions |
| **Snippets** | 📄 | Gray (#71717a) | CLAUDE.md partials for reuse |
| **Bundles** | 📦 | Gradient | Collections of related assets |

### Asset Schema

```typescript
interface Asset {
  // Identity
  id: string;                    // UUID
  name: string;                  // Unique within type
  slug: string;                  // URL-friendly identifier
  type: AssetType;               // skill | hook | agent | command | snippet | bundle

  // Content
  description: string;           // Short description (max 1024 chars)
  readme: string;                // Full markdown documentation
  installCommand: string;        // Copy-paste install command

  // Source
  sourceType: 'github' | 'upload' | 'discovered';
  sourceUrl?: string;            // GitHub repo URL
  version: string;               // Latest version

  // Author
  authorId: string;              // Reference to User
  authorName: string;            // Display name
  authorVerified: boolean;       // Verified badge

  // Metadata
  tags: string[];                // Searchable tags
  category: string;              // Primary category
  license?: string;              // Apache-2.0, MIT, etc.

  // Stats
  installCount: number;
  viewCount: number;
  rating: number;                // 1-5 average
  ratingCount: number;

  // Grouping
  similarTo?: string[];          // IDs of similar assets
  primaryInGroup: boolean;       // Is this the "best" in its group?

  // Timestamps
  createdAt: Date;
  updatedAt: Date;

  // Trends
  installsThisWeek: number;
  installsTrend: number;         // % change week over week
}
```

---

## 7. User Flows

### Flow 1: Browse and Install (Anonymous User)

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Homepage   │────▶│  Category   │────▶│Asset Detail │────▶│Copy Command │
│             │     │  or Search  │     │    Page     │     │  & Install  │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
                           │
                           ▼
                    ┌─────────────┐
                    │  Expand     │
                    │ Alternatives│
                    └─────────────┘
```

### Flow 2: Submit Asset (Author)

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Submit    │────▶│GitHub OAuth │────▶│ Enter Repo  │────▶│  Preview &  │
│   Button    │     │   Login     │     │  URL/Upload │     │   Confirm   │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
                                                                   │
                                                                   ▼
                                                            ┌─────────────┐
                                                            │  Published  │
                                                            │  (indexed)  │
                                                            └─────────────┘
```

### Flow 3: Save to Favorites

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│ Click Save  │────▶│ Prompt for  │────▶│   Saved!    │
│   Button    │     │GitHub Login │     │ (if logged) │
└─────────────┘     └─────────────┘     └─────────────┘
```

---

## 8. Discovery & Search

### Homepage Discovery Sections

| Section | Algorithm | Display |
|---------|-----------|---------|
| **Trending** | Highest % increase in installs (7 days) | Top 6, horizontal scroll |
| **Popular** | Highest total installs | Top 10, grid |
| **New Arrivals** | Most recent `createdAt` | Top 8, horizontal scroll |
| **Staff Picks** | Manually curated (future) | 1 featured + 3 secondary |
| **By Category** | Category landing pages | 6 category cards |

### Search Algorithm

**Query Processing:**
1. Tokenize search query
2. Match against: `name`, `description`, `tags`, `readme`
3. Weight: name (3x) > tags (2x) > description (1.5x) > readme (1x)

**Ranking Formula:**
```
score = (relevance × 0.4) + (installs_normalized × 0.3) +
        (rating × 0.2) + (recency × 0.1)
```

**Filters Available:**
- Asset type (multi-select)
- Minimum rating
- Minimum installs
- Author verified only
- Time range (last week, month, year, all time)

### Search Results Display

```
┌─────────────────────────────────────────────────────────────────┐
│  Results for "git commit" (47 matches)                          │
├─────────────────────────────────────────────────────────────────┤
│  Sort: [Relevance] [Most Installed] [Highest Rated] [Newest]    │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─ BEST MATCH ───────────────────────────────────────────────┐ │
│  │  smart-commit  ⚡                                           │ │
│  │  ★★★★★ (847) • 12.4k installs • Updated 2 days ago        │ │
│  │  "Analyzes git diffs and generates semantic commits..."    │ │
│  │  [Install] [Save] [Share]                                  │ │
│  │                                                            │ │
│  │  ┌─ 4 similar alternatives ─────────────────────────── ▾ ┐ │ │
│  │  └───────────────────────────────────────────────────────┘ │ │
│  └────────────────────────────────────────────────────────────┘ │
│                                                                  │
│  ┌─ OTHER RESULTS ────────────────────────────────────────────┐ │
│  │  pr-reviewer  ⚡  (different functionality)                │ │
│  │  ...                                                       │ │
│  └────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────┘
```

---

## 9. Handling Duplicates & Similar Assets

### The Problem

Multiple assets often solve the same problem (e.g., 5 different "git commit message generators"). Showing all equally:
- Overwhelms users with choice
- Makes it hard to pick the "best"
- Buries quality under quantity

### Our Solution: "Primary + Alternatives"

**Concept:** Algorithmically select the "best" asset as **primary**, group similar ones as **alternatives** that are collapsed but accessible.

### Similarity Detection Algorithm

**Step 1: Text Similarity**
```python
def compute_similarity(asset_a, asset_b):
    # Combine searchable text
    text_a = f"{asset_a.name} {asset_a.description} {' '.join(asset_a.tags)}"
    text_b = f"{asset_b.name} {asset_b.description} {' '.join(asset_b.tags)}"

    # TF-IDF + Cosine similarity
    similarity = cosine_similarity(tfidf(text_a), tfidf(text_b))

    return similarity  # 0.0 to 1.0
```

**Step 2: Grouping**
```python
SIMILARITY_THRESHOLD = 0.65  # Tunable

def group_similar_assets(assets):
    groups = []
    for asset in assets:
        matched = False
        for group in groups:
            if compute_similarity(asset, group[0]) > SIMILARITY_THRESHOLD:
                group.append(asset)
                matched = True
                break
        if not matched:
            groups.append([asset])
    return groups
```

**Step 3: Select Primary**
```python
def select_primary(group):
    # Score each asset
    for asset in group:
        asset.score = (
            normalize(asset.installCount) * 0.4 +
            asset.rating * 0.3 +
            recency_score(asset.updatedAt) * 0.2 +
            (1 if asset.authorVerified else 0) * 0.1
        )

    # Highest score becomes primary
    group.sort(key=lambda a: a.score, reverse=True)
    group[0].primaryInGroup = True

    return group
```

### UI Pattern

**Collapsed State (Default):**
```
┌─────────────────────────────────────────────────────────────┐
│  🏆 smart-commit  ⚡                        PRIMARY         │
│  ★★★★★ (847) • 12.4k installs                              │
│  "Analyzes git diffs and generates semantic commits..."    │
│                                                            │
│  ┌─ See 4 alternatives ─────────────────────────────── ▾ ┐ │
└─────────────────────────────────────────────────────────────┘
```

**Expanded State (On Click):**
```
┌─────────────────────────────────────────────────────────────┐
│  🏆 smart-commit  ⚡                        PRIMARY         │
│  ★★★★★ (847) • 12.4k installs                              │
│  "Analyzes git diffs and generates semantic commits..."    │
│                                                            │
│  ┌─ 4 alternatives ─────────────────────────────────── ▴ ┐ │
│  │                                                        │ │
│  │  Why grouped: All generate commit messages from diffs  │ │
│  │                                                        │ │
│  │  ┌────────────┐ ┌────────────┐ ┌────────────┐         │ │
│  │  │commit-gen  │ │git-commit  │ │auto-commit │         │ │
│  │  │★4.0 • 1.8k │ │★4.2 • 3.2k │ │★3.9 • 982  │         │ │
│  │  │"Simpler,   │ │"AI-powered │ │"Minimal,   │         │ │
│  │  │opinionated"│ │with GPT"   │ │fast"       │         │ │
│  │  └────────────┘ └────────────┘ └────────────┘         │ │
│  └────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

### Edge Cases

| Scenario | Handling |
|----------|----------|
| New asset similar to popular one | Add to group as alternative |
| New asset becomes more popular | Re-run algorithm weekly, swap primary |
| Asset has no similar matches | Show standalone (no alternatives section) |
| Two assets tied in score | Prefer more recent `updatedAt` |

---

## 10. UI/UX Design

### Design Direction: "Terminal Editorial"

A sophisticated fusion of **developer-native terminal aesthetics** with **editorial magazine layouts**.

**Why This Works:**
- Dark mode = developers' natural habitat
- Command bar hero = feels native
- Magazine layout = prevents overwhelming
- Serif + mono typography = intellectual, refined

### Color Palette

```css
:root {
  /* Base - Deep charcoal */
  --bg-primary: #0d0d0f;
  --bg-secondary: #161618;
  --bg-elevated: #1c1c1f;

  /* Text */
  --text-primary: #fafafa;
  --text-secondary: #a0a0a0;
  --text-muted: #666666;

  /* Accent - Warm amber */
  --accent-primary: #f5a623;
  --accent-hover: #ffb84d;

  /* Asset type colors */
  --color-skill: #f5a623;
  --color-hook: #a855f7;
  --color-agent: #22d3ee;
  --color-command: #22c55e;
  --color-snippet: #71717a;

  /* Semantic */
  --success: #22c55e;
  --warning: #f59e0b;
  --error: #ef4444;

  /* Borders */
  --border: #2a2a2d;
  --border-hover: #3a3a3d;
}
```

### Typography

```css
/* Headlines - Distinctive serif */
--font-display: 'Playfair Display', serif;

/* Body - Clean, readable */
--font-body: 'DM Sans', sans-serif;

/* Code - Developer-native */
--font-mono: 'JetBrains Mono', monospace;
```

### Page Layouts

#### Homepage

```
┌─────────────────────────────────────────────────────────────────────┐
│  HEADER                                                             │
│  [Logo]              [Categories ▾]  [Submit]  [★ Saved]  [Login]  │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  HERO - Command Bar                                                  │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  ⌘  Search skills, hooks, agents...                    ⏎    │    │
│  └─────────────────────────────────────────────────────────────┘    │
│  Quick tags: git • testing • devops • ai/ml • docs • security       │
│                                                                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  TRENDING THIS WEEK                                      → See all  │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐       │
│  │ #1 ↑234%│ │ #2 ↑89% │ │ #3 ↑67% │ │ #4 ↑52% │ │ #5 ↑41% │       │
│  │ Card    │ │ Card    │ │ Card    │ │ Card    │ │ Card    │       │
│  └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘       │
│                                                                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  BROWSE BY CATEGORY                                                  │
│  ┌───────────────────┐ ┌───────────────────┐ ┌───────────────────┐  │
│  │ ⚡ SKILLS         │ │ 🪝 HOOKS          │ │ 🤖 SUB-AGENTS     │  │
│  │ 2,847 assets      │ │ 892 assets        │ │ 341 assets        │  │
│  └───────────────────┘ └───────────────────┘ └───────────────────┘  │
│  ┌───────────────────┐ ┌───────────────────┐ ┌───────────────────┐  │
│  │ 📜 COMMANDS       │ │ 📄 SNIPPETS       │ │ 📦 BUNDLES        │  │
│  │ 156 assets        │ │ 1,204 assets      │ │ 89 bundles        │  │
│  └───────────────────┘ └───────────────────┘ └───────────────────┘  │
│                                                                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  JUST ADDED                                              → See all  │
│  [Horizontal scroll of recent assets with timestamps]               │
│                                                                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  MOST POPULAR                                            → See all  │
│  [Grid of top 6 assets by install count]                           │
│                                                                      │
├─────────────────────────────────────────────────────────────────────┤
│  FOOTER                                                             │
│  About • GitHub • Submit • API • Terms                              │
└─────────────────────────────────────────────────────────────────────┘
```

#### Search Results Page

```
┌─────────────────────────────────────────────────────────────────────┐
│  HEADER with search bar pre-filled                                  │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─ FILTERS ────┐  ┌─ RESULTS ─────────────────────────────────────┐│
│  │              │  │                                                ││
│  │ Type         │  │  47 results for "git commit"                  ││
│  │ ☑ Skills     │  │  Sort: [Relevance ▾] [Installs] [Rating]      ││
│  │ ☑ Hooks      │  │                                                ││
│  │ ☐ Agents     │  │  ┌─ BEST MATCH ──────────────────────────────┐││
│  │ ☐ Commands   │  │  │ smart-commit ⚡  ★★★★★  12.4k installs    │││
│  │ ☐ Snippets   │  │  │ "Analyzes git diffs..."                   │││
│  │              │  │  │ [Install] [Save] [Share]                  │││
│  │ Rating       │  │  │ ┌─ 4 alternatives ─────────────────── ▾ ┐ │││
│  │ ○ Any        │  │  └──────────────────────────────────────────┘││
│  │ ○ 4+ stars   │  │                                                ││
│  │ ○ 3+ stars   │  │  ┌─────────────────────────────────────────┐  ││
│  │              │  │  │ pr-reviewer ⚡  ★★★★☆  5.6k installs     │  ││
│  │ Installs     │  │  │ "Reviews PRs for code quality..."        │  ││
│  │ ○ Any        │  │  └─────────────────────────────────────────┘  ││
│  │ ○ 1k+        │  │                                                ││
│  │ ○ 10k+       │  │  [Load more...]                               ││
│  │              │  │                                                ││
│  └──────────────┘  └────────────────────────────────────────────────┘│
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

#### Asset Detail Page

```
┌─────────────────────────────────────────────────────────────────────┐
│  ← Back to results                               [♡ Save] [↗ Share] │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─ HERO ───────────────────────────────────────────────────────────┐
│  │                                                                   │
│  │  ⚡ SKILL                                                         │
│  │                                                                   │
│  │  smart-commit                                                     │
│  │  ════════════════                                                 │
│  │                                                                   │
│  │  ★★★★★ 4.9 (847 ratings)                                         │
│  │                                                                   │
│  │  ↓ 12,487 installs  •  👁 34,221 views  •  📅 Updated 2 days ago │
│  │                                                                   │
│  │  ┌───────────────────────────────────────────────────────────┐   │
│  │  │  claude plugin install @semantic/smart-commit        [📋] │   │
│  │  └───────────────────────────────────────────────────────────┘   │
│  │                                                                   │
│  └───────────────────────────────────────────────────────────────────┘
│                                                                      │
│  ┌─ TABS ───────────────────────────────────────────────────────────┐
│  │  [Overview]  [Documentation]  [Reviews (847)]  [Versions]        │
│  └───────────────────────────────────────────────────────────────────┘
│                                                                      │
│  ┌─ ABOUT ──────────────────────────────────────────────────────────┐
│  │  Analyzes your staged git changes and generates meaningful,      │
│  │  semantic commit messages following conventional commit          │
│  │  standards. Supports custom templates and team conventions.      │
│  │                                                                   │
│  │  Tags: #git #commit #automation #conventional-commits            │
│  └───────────────────────────────────────────────────────────────────┘
│                                                                      │
│  ┌─ AUTHOR ─────────────────────────────────────────────────────────┐
│  │  [avatar]  @semanticdev  ✓ Verified                              │
│  │            12 assets published • 45k total installs              │
│  └───────────────────────────────────────────────────────────────────┘
│                                                                      │
│  ┌─ ALTERNATIVES ───────────────────────────────────────────────────┐
│  │  Similar assets that solve the same problem:                     │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐            │
│  │  │git-commit│ │commit-gen│ │auto-msg  │ │msg-writer│            │
│  │  │★4.2 3.2k │ │★4.0 1.8k │ │★3.9 982  │ │★3.7 456  │            │
│  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘            │
│  └───────────────────────────────────────────────────────────────────┘
│                                                                      │
│  ┌─ REVIEWS ────────────────────────────────────────────────────────┐
│  │  [Review cards]                                                   │
│  └───────────────────────────────────────────────────────────────────┘
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Mobile Responsive

**Breakpoints:**
- Mobile: < 768px
- Tablet: 768px - 1024px
- Desktop: > 1024px

**Mobile Adaptations:**
- Single column layout
- Bottom sheet for filters
- Hamburger menu for navigation
- Swipe between category tabs
- Sticky search bar
- Full-width cards

### Unique Design Elements

1. **Command Bar Hero** - Terminal-style search (⌘K to focus)
2. **Asset Type Badges** - Color-coded by type
3. **Trend Sparklines** - Mini charts showing popularity trajectory
4. **Primary + Alternatives** - Smart grouping UI
5. **Quick Install Toast** - Copy confirmation with usage hint

---

## 11. Technical Architecture

### Stack

| Layer | Technology | Rationale |
|-------|------------|-----------|
| **Frontend** | Next.js 14 (App Router) | React + SSR, great DX |
| **Hosting** | Vercel | Free tier, easy deployment |
| **Database** | Supabase (Postgres) | Free tier, auth included |
| **Auth** | Supabase Auth (GitHub OAuth) | Built-in, simple |
| **Storage** | Supabase Storage | Asset screenshots, avatars |
| **Search** | Postgres full-text | Free, good enough for MVP |
| **Caching** | Vercel Edge Cache | Performance |

### Database Schema

```sql
-- Users (authors)
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  github_id TEXT UNIQUE NOT NULL,
  username TEXT NOT NULL,
  display_name TEXT,
  avatar_url TEXT,
  verified BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Assets
CREATE TABLE assets (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name TEXT NOT NULL,
  slug TEXT UNIQUE NOT NULL,
  type TEXT NOT NULL CHECK (type IN ('skill', 'hook', 'agent', 'command', 'snippet', 'bundle')),
  description TEXT NOT NULL,
  readme TEXT,
  install_command TEXT NOT NULL,

  -- Source
  source_type TEXT NOT NULL CHECK (source_type IN ('github', 'upload', 'discovered')),
  source_url TEXT,
  version TEXT DEFAULT '1.0.0',

  -- Author
  author_id UUID REFERENCES users(id),

  -- Metadata
  tags TEXT[],
  category TEXT,
  license TEXT,

  -- Stats
  install_count INTEGER DEFAULT 0,
  view_count INTEGER DEFAULT 0,
  rating DECIMAL(2,1) DEFAULT 0,
  rating_count INTEGER DEFAULT 0,

  -- Grouping
  similarity_group_id UUID,
  primary_in_group BOOLEAN DEFAULT FALSE,

  -- Trends
  installs_this_week INTEGER DEFAULT 0,
  installs_trend DECIMAL(5,2) DEFAULT 0,

  -- Timestamps
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW(),

  -- Search
  search_vector TSVECTOR GENERATED ALWAYS AS (
    setweight(to_tsvector('english', name), 'A') ||
    setweight(to_tsvector('english', COALESCE(description, '')), 'B') ||
    setweight(to_tsvector('english', COALESCE(array_to_string(tags, ' '), '')), 'B')
  ) STORED
);

CREATE INDEX idx_assets_search ON assets USING GIN(search_vector);
CREATE INDEX idx_assets_type ON assets(type);
CREATE INDEX idx_assets_category ON assets(category);
CREATE INDEX idx_assets_install_count ON assets(install_count DESC);
CREATE INDEX idx_assets_rating ON assets(rating DESC);
CREATE INDEX idx_assets_created_at ON assets(created_at DESC);

-- Ratings
CREATE TABLE ratings (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  asset_id UUID REFERENCES assets(id) ON DELETE CASCADE,
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  rating INTEGER NOT NULL CHECK (rating >= 1 AND rating <= 5),
  review TEXT,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  UNIQUE(asset_id, user_id)
);

-- Favorites
CREATE TABLE favorites (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  asset_id UUID REFERENCES assets(id) ON DELETE CASCADE,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  UNIQUE(user_id, asset_id)
);

-- Similarity Groups
CREATE TABLE similarity_groups (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  description TEXT,  -- Why these are grouped
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Install Events (for analytics)
CREATE TABLE install_events (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  asset_id UUID REFERENCES assets(id) ON DELETE CASCADE,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- View Events
CREATE TABLE view_events (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  asset_id UUID REFERENCES assets(id) ON DELETE CASCADE,
  created_at TIMESTAMPTZ DEFAULT NOW()
);
```

### API Routes

```
GET    /api/assets                    # List assets (with filters)
GET    /api/assets/:slug              # Get single asset
POST   /api/assets                    # Create asset (auth required)
PUT    /api/assets/:slug              # Update asset (author only)
DELETE /api/assets/:slug              # Delete asset (author only)

GET    /api/assets/:slug/alternatives # Get similar assets
POST   /api/assets/:slug/rate         # Rate asset (auth required)
POST   /api/assets/:slug/install      # Track install event
POST   /api/assets/:slug/view         # Track view event

GET    /api/search?q=...              # Search assets
GET    /api/trending                  # Trending assets
GET    /api/popular                   # Most installed
GET    /api/recent                    # Recently added

GET    /api/categories                # List categories
GET    /api/categories/:slug          # Assets in category

GET    /api/users/:username           # Author profile
GET    /api/users/:username/assets    # Author's assets

POST   /api/favorites                 # Add favorite (auth required)
DELETE /api/favorites/:assetId        # Remove favorite
GET    /api/favorites                 # List favorites (auth required)

POST   /api/auth/github               # GitHub OAuth callback
GET    /api/auth/me                   # Current user
POST   /api/auth/logout               # Logout
```

### GitHub Auto-Discovery

**Cron Job (Daily):**
```typescript
async function discoverSkills() {
  // Search GitHub for SKILL.md files
  const results = await github.search.code({
    q: 'filename:SKILL.md path:.claude/skills',
    per_page: 100
  });

  for (const file of results.items) {
    // Check if already indexed
    const existing = await db.assets.findBySourceUrl(file.repository.html_url);
    if (existing) continue;

    // Fetch and parse SKILL.md
    const content = await github.repos.getContent({
      owner: file.repository.owner.login,
      repo: file.repository.name,
      path: file.path
    });

    const parsed = parseSkillMd(content);

    // Create asset
    await db.assets.create({
      name: parsed.name,
      description: parsed.description,
      sourceType: 'discovered',
      sourceUrl: file.repository.html_url,
      // ... other fields
    });
  }
}
```

---

## 12. Security Considerations

### MVP Security (Automated)

For MVP, security is **automated but not blocking**:

| Check | Implementation | Action |
|-------|----------------|--------|
| **SKILL.md Validation** | YAML schema validation | Reject invalid |
| **Basic Pattern Scan** | Regex for obvious dangers | Flag for review |
| **Rate Limiting** | Per-IP and per-user limits | Prevent abuse |
| **Auth** | GitHub OAuth only | Verified identity |

### Future Security (Phase 2)

| Feature | Description |
|---------|-------------|
| **ShellCheck Integration** | Static analysis for hooks |
| **Dangerous Pattern Detection** | `curl\|sh`, `eval`, `rm -rf` |
| **Sandbox Testing** | Run hooks in isolated container |
| **Verified Authors** | Manual verification for trusted badge |
| **Community Reporting** | Flag suspicious assets |

### Trust Indicators (Displayed to Users)

```
┌─────────────────────────────────────────────┐
│  Trust Signals                              │
│                                             │
│  ✓ Author verified via GitHub              │
│  ✓ Source code available                   │
│  ⚠ Contains shell commands (hooks only)    │
│  ○ Not yet security scanned                │
└─────────────────────────────────────────────┘
```

---

## 13. MVP Scope

### Phase 1: MVP (4-6 weeks)

**Goal:** Launchable product with core discovery and browsing.

| Feature | Status | Notes |
|---------|--------|-------|
| Homepage with sections | Required | Trending, popular, categories, new |
| Keyword search | Required | Postgres full-text |
| Asset detail pages | Required | Install command, stats, author |
| Browse by category | Required | 6 asset types |
| Browse by type | Required | Skills, hooks, etc. |
| GitHub OAuth | Required | For authors |
| Submit via GitHub URL | Required | Parse SKILL.md from repo |
| View/install tracking | Required | Basic counters |
| 5-star ratings | Required | No text reviews yet |
| Save to favorites | Should have | Requires login |
| Share button | Should have | Copy link |
| Author dashboard | Should have | View count, install count |
| Mobile responsive | Required | Works on all devices |

**Not in MVP:**
- Security scanning
- Text reviews
- CLI tool
- Claude Code plugin
- GitHub auto-discovery (manual submission only)
- Bundles
- Verified author badges

### Phase 2: Growth (Post-Launch)

| Feature | Timeline |
|---------|----------|
| GitHub auto-discovery | +2 weeks |
| Text reviews | +2 weeks |
| Security scanning (hooks) | +4 weeks |
| Verified author program | +4 weeks |
| CLI tool | +6 weeks |
| Claude Code plugin | +8 weeks |

### Phase 3: Monetization (After User Growth)

| Feature | Timeline |
|---------|----------|
| Detailed analytics (paid) | +3 months |
| Promoted listings | +4 months |
| Premium assets | +6 months |

---

## 14. Future Monetization

### Strategy: Free to Start, Monetize Later

**Phase 1 (MVP):** Completely free
- Build user base
- Establish trust
- Gather feedback

**Phase 2 (Growth):** Introduce optional paid features
- Don't paywall core functionality
- Premium = enhanced, not required

### Monetization Options

| Option | Model | Platform Cut | Notes |
|--------|-------|--------------|-------|
| **Detailed Analytics** | Subscription | 100% to platform | $5-10/month for authors |
| **Promoted Listings** | Pay-per-impression | 100% to platform | Boost visibility in search |
| **Premium Assets** | One-time or subscription | 15-20% to platform | Authors sell paid skills |
| **Tips/Sponsors** | One-time | 0% (pass-through) | Like GitHub Sponsors |
| **Verified Badge** | One-time fee | 100% to platform | $25-50 for verification |
| **Enterprise** | Subscription | 100% to platform | Private registries, SSO |

### Recommended Rollout

1. **Month 3-6:** Detailed analytics as paid feature ($9/month)
2. **Month 6-9:** Promoted listings (auction-based)
3. **Month 9-12:** Premium assets (15% platform fee)
4. **Year 2:** Enterprise tier

### Revenue Projections (Conservative)

| Milestone | Users | Paying Users | MRR |
|-----------|-------|--------------|-----|
| Month 6 | 1,000 | 20 (2%) | $180 |
| Month 12 | 5,000 | 150 (3%) | $1,350 |
| Month 18 | 15,000 | 600 (4%) | $5,400 |
| Month 24 | 30,000 | 1,500 (5%) | $13,500 |

---

## 15. Success Metrics

### North Star Metric

**Monthly Active Installers** - Users who install at least one asset per month.

### Key Metrics

| Metric | Definition | Target (Month 6) |
|--------|------------|------------------|
| **Total Assets** | Assets in database | 1,000+ |
| **Monthly Visits** | Unique visitors | 10,000 |
| **Monthly Installs** | Install button clicks | 5,000 |
| **Active Authors** | Authors with 1+ asset | 200 |
| **Avg Rating** | Mean star rating | 4.0+ |
| **Search Success** | Searches that lead to install | 30% |

### Tracking Implementation

```typescript
// Track key events
analytics.track('asset_viewed', { assetId, assetType });
analytics.track('install_clicked', { assetId, assetType });
analytics.track('search_performed', { query, resultCount });
analytics.track('search_result_clicked', { query, assetId, position });
analytics.track('asset_submitted', { assetType, sourceType });
analytics.track('rating_submitted', { assetId, rating });
analytics.track('favorite_added', { assetId });
```

---

## 16. Additional Decisions

### Seed Content Strategy

**Decision:** Import from existing platforms

- Scrape/index popular assets from SkillsMP, claude-plugins.dev, GitHub
- Respect licenses and attribution
- Run initial similarity grouping after import
- Target: 500-1000 assets at launch

### Automated Moderation System

**Decision:** Automated quality gates + community reporting

**Quality Score Algorithm:**
```python
quality_score = (
    description_length_score +     # 0-20 points (min 50 chars)
    has_readme_score +             # 0-20 points
    github_stars_score +           # 0-20 points (if from GitHub)
    author_history_score +         # 0-20 points
    no_spam_patterns_score         # 0-20 points
)

if quality_score < 40: reject
if quality_score < 60: flag_for_review
if quality_score >= 60: auto_publish
```

**Automated Gates:**
| Gate | Check | Action |
|------|-------|--------|
| Minimum description | >= 50 characters | Reject |
| Valid SKILL.md | YAML schema validation | Reject |
| Duplicate detection | > 95% similarity | Flag |
| Spam patterns | Excessive links, keyword stuffing | Reject |
| Rate limiting | Max 3 submissions/day for new authors | Throttle |

**Community Reporting:**
- Flag button on each asset
- After 3 flags, auto-hide pending review
- Reputation system for reporters (future)

### Analytics Architecture

**Decision:** Hybrid approach

| Layer | Tool | Data |
|-------|------|------|
| **Page Analytics** | Vercel Analytics (free) | Traffic, performance, bounce |
| **Product Events** | Supabase (database) | Installs, views, searches, ratings |
| **Error Monitoring** | Vercel built-in | Errors, exceptions |

### Legal

**Decision:** Use standard templates

- Terms of Service: Generate from Termly or similar
- Privacy Policy: GDPR-compliant template
- Add before public launch

### Community

**Decision:** None for MVP

- No Discord, forums, or built-in comments
- Revisit after launch based on user feedback

### Claude Code Plugin

**Decision:** Full terminal integration

- Browse and search from within Claude Code
- View asset details in terminal
- One-command install
- Phase 2 feature (post-MVP)

### Repository

**Decision:** New GitHub repo (public)

- Open source from day one
- Encourages contributions
- Builds trust with community

### SEO Strategy

**Decision:** Critical priority

**Implementation:**
- Server-side rendering (Next.js App Router)
- Dynamic meta tags per asset page
- Sitemap generation
- Schema.org structured data for assets
- Clean URLs (`/skills/smart-commit` not `/assets?id=123`)
- Category landing pages for keyword targeting

**Target Keywords:**
- "claude code skills"
- "claude code plugins"
- "claude code hooks"
- "[specific skill name]" (long-tail)

---

## 17. Open Questions

### Project Name

**Decision:** Use placeholder `claude-marketplace` for development, rename before public launch.

### Remaining Decisions

| Question | Options | Decision Needed By |
|----------|---------|-------------------|
| Final platform name? | TBD | Before public launch |
| Allow duplicate names across types? | Yes / No / Namespaced | Before schema finalization |
| Require license field? | Required / Optional / Default | Before launch |

### Technical Questions

| Question | Options | Decision Needed By |
|----------|---------|-------------------|
| Full-text search enough? | Postgres / Algolia / Typesense | Before launch |
| Background jobs for import? | Vercel Cron / Inngest / QStash | Before seed content import |

---

## Appendix A: Competitive Analysis Details

See [Section 3: Market Research](#3-market-research) for summary.

Full competitive analysis available in research notes.

## Appendix B: SKILL.md Specification

Full specification at [agentskills.io/specification](https://agentskills.io/specification).

## Appendix C: Security Scanning Details

Detailed security implementation plan available in research notes.

---

## Appendix D: Session Context for Future Development

> **Purpose:** This section preserves context from the initial design session to help future Claude instances continue work without losing important decisions, rationale, and discussion points.

### Session Summary

**Date:** January 6, 2026
**Scope:** Initial design and planning for a Claude Code asset marketplace

### How We Got Here

1. **Initial Question:** User asked about the Superpowers plugin for Claude Code, then about existing skill-sharing platforms.

2. **Opportunity Identified:** User wanted to build a marketplace that stands out from existing platforms (SkillsMP, claude-plugins.dev, claudecodeplugins.io, etc.).

3. **Differentiation Angles Selected:**
   - Unified asset hub (all asset types, not just skills)
   - Quality curation (automated, not manual for MVP)
   - Author platform (analytics, future monetization)

4. **Research Conducted:** Four parallel research agents gathered information on:
   - Existing platforms deep-dive (features, gaps, UX patterns)
   - Monetization models (JetBrains, GitHub Sponsors, Gumroad, etc.)
   - Security scanning (ShellCheck, sandboxing, trust models)
   - SKILL.md standard (specification, usage, extensions)

5. **Design Decisions:** Made through iterative Q&A with user, captured in this document.

### Key User Preferences Expressed

| Topic | User's Preference |
|-------|-------------------|
| **Duplicate handling** | Wanted recommendation - we chose "Primary + Alternatives" pattern |
| **Monetization** | Free first, monetize after user growth |
| **Curation** | Fully automated (no manual review) |
| **Asset types** | Full suite from day one |
| **Submission** | GitHub auto-discovery + manual submission + direct upload |
| **Auth** | GitHub OAuth for authors only, anonymous browsing allowed |
| **Security scanning** | Nice to have, not MVP blocker |
| **Community features** | None for MVP |
| **SEO** | Critical priority |
| **Analytics** | Vercel + database events (detailed analytics as future paid feature) |

### Research Findings Worth Remembering

**Existing Platform Weaknesses:**
- SkillsMP: 32k+ skills but low quality bar (2-star minimum)
- claude-plugins.dev: CLI-first, no GUI browsing
- claudecodeplugins.io: Good docs but small catalog (739)
- All platforms: No author analytics, no monetization, no security scanning, skills-only focus

**Monetization Benchmarks:**
- JetBrains: 75%+ to developers, handles taxes/payments
- GitHub Sponsors: 0% fee for personal sponsors
- Polar.sh: 4% + $0.40, merchant of record
- VS Code: No native monetization (major gap)

**SKILL.md Standard:**
- Spec at agentskills.io/specification
- Required: `name` (64 chars), `description` (1024 chars)
- Optional: `allowed-tools`, `model`, `license`, `metadata`
- Used by Claude Code, Codex CLI, Copilot, Cursor

### Decisions Made (With Rationale)

| Decision | Choice | Why |
|----------|--------|-----|
| Stack | Next.js + Vercel + Supabase | Free tiers, fast to ship, solo-friendly |
| Duplicate handling | Algorithm selects primary, shows alternatives collapsed | Less overwhelming than showing all equally |
| Quality scoring | 0-100 score, auto-publish at 60+ | Balances quality with low friction |
| Seed content | Import from existing platforms | Need content at launch for credibility |
| Name | Placeholder "claude-marketplace" | Avoid bikeshedding, rename before launch |
| Plugin | Full terminal integration | User specifically wanted browse-in-terminal |

### Things Explicitly Deferred

| Item | Deferred To | Notes |
|------|-------------|-------|
| Final platform name | Before public launch | Using placeholder for now |
| Security scanning | Phase 2 | User said "nice to have" |
| Text reviews | Phase 2 | MVP has star ratings only |
| CLI tool | Phase 2 | Web-first approach |
| Claude Code plugin | Phase 2 | User wants it but not blocking MVP |
| Detailed analytics | Monetization phase | First paid feature |
| Verified author badges | Phase 2 | Need manual verification process |
| Community (Discord, forums) | Post-launch | Based on user demand |

### Potential Future Directions Discussed

1. **Monetization rollout:**
   - Month 3-6: Detailed analytics ($9/month)
   - Month 6-9: Promoted listings
   - Month 9-12: Premium/paid assets (15% platform fee)
   - Year 2: Enterprise tier

2. **Security scanning implementation:**
   - ShellCheck for shell scripts
   - Semgrep for custom rules
   - Docker sandboxing for testing
   - Trust tiers (Official → Verified → Community → Unverified)

3. **Discovery enhancements:**
   - AI-powered recommendations
   - "Works well together" suggestions
   - Conflict detection between assets

4. **Author platform:**
   - Detailed analytics dashboard
   - Version management
   - Tip jar / GitHub Sponsors integration

### Design Patterns Established

**"Primary + Alternatives" for Duplicates:**
```
score = (installs × 0.4) + (rating × 0.3) + (recency × 0.2) + (author_trust × 0.1)
```
Highest score becomes primary. Others shown collapsed but accessible.

**Quality Score for Submissions:**
```
quality_score = description_length + has_readme + github_stars + author_history + no_spam
```
- < 40: Reject
- 40-59: Flag for review
- 60+: Auto-publish

**Asset Type Color Coding:**
- Skills: Amber (#f5a623)
- Hooks: Purple (#a855f7)
- Agents: Cyan (#22d3ee)
- Commands: Green (#22c55e)
- Snippets: Gray (#71717a)

### Technical Decisions Locked In

- **Database:** Supabase Postgres with full-text search
- **Auth:** Supabase Auth with GitHub OAuth only
- **Hosting:** Vercel (free tier)
- **Analytics:** Vercel Analytics + custom DB events
- **Search:** Postgres full-text (upgrade to Algolia/Typesense if needed)
- **Background jobs:** TBD (Vercel Cron vs Inngest vs QStash)

### Open Technical Questions

1. **Full-text search scaling:** Postgres should handle MVP, but may need dedicated search if catalog grows large
2. **Background job provider:** Need to decide before implementing auto-discovery crawler
3. **Image/asset storage:** Supabase Storage should work, but monitor costs

### User's Communication Style

- Prefers being given options with explanations
- Wants recommendations when unsure ("What do you think would be best?")
- Values automation over manual processes
- Focused on user experience (not overwhelming)
- Pragmatic about MVP scope (willing to defer features)
- Interested in long-term monetization but patient about it

### Files Created This Session

| File | Purpose |
|------|---------|
| `/Users/mchoi/claude-asset-marketplace-design.md` | This design document |

### Recommended Next Steps

When resuming development:

1. **Create GitHub repo** (`claude-marketplace`)
2. **Initialize Next.js 14** with App Router
3. **Set up Supabase** project and run schema migrations
4. **Build core pages:** Homepage, search, asset detail
5. **Implement GitHub OAuth** for author submissions
6. **Build submission flow** (GitHub URL → parse SKILL.md → create asset)
7. **Add trending/popular algorithms**
8. **Implement similarity detection** for duplicate grouping
9. **Seed initial content** from existing platforms
10. **SEO optimization** (meta tags, sitemap, structured data)
11. **Deploy to Vercel**
12. **Generate legal pages** (ToS, Privacy Policy)

### Questions to Ask User When Resuming

If picking up this project later, consider asking:
- "Have you thought more about the platform name?"
- "Should we allow the same asset name across different types (e.g., 'smart-commit' as both a skill and a hook)?"
- "Do you want license to be a required field?"
- "Ready to start building, or need to refine anything first?"

---

**Document Status:** Draft - Ready for Development
**Last Updated:** January 6, 2026
**Session Context Added:** January 6, 2026
**Next Review:** Before development begins
