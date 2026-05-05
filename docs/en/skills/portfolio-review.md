---
layout: default
title: "Portfolio Review"
grand_parent: English
parent: Skill Guides
nav_order: 36
lang_peer: /ja/skills/portfolio-review/
permalink: /en/skills/portfolio-review/
---

# Portfolio Review
{: .no_toc }

Run a full DeGiro swing-trader portfolio review using the 14-rule trading system. Use when the user provides a portfolio screenshot, CSV, or data paste and asks for a review, position analysis, EUR opportunity scan, or priority actions.
{: .fs-6 .fw-300 }

<span class="badge badge-free">No API</span>

[Download Skill Package (.skill)](https://github.com/tradermonty/claude-trading-skills/raw/main/skill-packages/portfolio-review.skill){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View Source on GitHub](https://github.com/tradermonty/claude-trading-skills/tree/main/skills/portfolio-review){: .btn .fs-5 .mb-4 .mb-md-0 }

<details open markdown="block">
  <summary>Table of Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 1. Overview

Execute a structured 7-step portfolio review for a DeGiro EUR-based swing trader, enforcing 14 hard rules on every position. Works from screenshots, CSV pastes, or manual input — no broker API or external account connection required. Output is tables only with exact action instructions.

This skill is the counterpart to **Portfolio Manager** (which requires Alpaca MCP). Portfolio Review works with any broker as long as the user provides position data.

---

## 2. When to Use

- User provides a portfolio screenshot or data and says "review", "portfolio review", or `/portfolio-review`
- User asks for a morning brief
- User asks whether to hold, add, reduce, or exit a specific position
- User asks for EUR-denominated new entry ideas
- User wants to check which of the 14 rules are currently being violated

---

## 3. Prerequisites

**No API key required.** Uses WebSearch to fetch current market prices and news.

The skill expects:
- Portfolio data (screenshot, CSV paste, or manual table)
- Access to `TRADING_SYSTEM_MASTER.md` at the repo root for baseline fallback

---

## 4. How It Works

### Step 0 — Portfolio Data Input
Accepts screenshots (reads positions visually), CSV paste, or manual table. Falls back to the baseline in `TRADING_SYSTEM_MASTER.md` only if the user explicitly requests it.

### Step 0.5 — Continuity Check (Rule R13)
States which positions changed since last advice. Unchanged positions default to HOLD — no action without new catalyst.

### Step 1 — Market Regime
Fetches S&P 500, NASDAQ 100, DAX, VIX, EUR/USD, US 10Y, Gold, Oil via WebSearch and classifies the environment as RISK-ON / NEUTRAL / RISK-OFF.

### Step 2 — Catalysts This Week
Identifies earnings, central bank events, and macro releases affecting held positions within the next 5 trading days. Binary events (earnings/FDA) trigger Rule R12 review.

### Step 3 — Position Dashboard
For each held position: applies all 14 rules, assigns an action (HOLD/ADD/REDUCE/EXIT/STOP-HIT/WATCH), confidence level, stop, and target. Adds a non-consensus `⚠️ Overlooked:` footnote per Rule R14.

### Step 4 — EUR Opportunity Scan
Scans European large caps → Tradegate Core ETFs → Asia EUR ETFs for new entries. All new entries must be EUR-denominated (Rule R11). Minimum R/R 2:1.

### Step 5 — Priority Actions
Top 5 actions numbered by urgency with exact trade instructions. Enforces Rule R7 (cash deployment mandate in RISK-ON).

### Step 6 — Portfolio Health
Summary table with diversification, cash ratio, USD exposure, rule violations, and overall score out of 10.

---

## 5. The 14 Hard Rules (Summary)

| # | Rule | Key Condition |
|---|------|---------------|
| R1 | No falling knives | No BUY in 3-month downtrend without base or earnings beat |
| R2 | Macro theme patience | No EXIT on structural theme within 5 days unless stop hit |
| R3 | Leveraged ETF filter | VIX < 18 + index above 50-day MA + no macro event within 10 days |
| R4 | Same-stock cooling | 3rd entry blocked if 2nd trade made <50% of 1st |
| R5 | High-valuation entry | P/E >40x: only BUY at 20-week MA or post-earnings beat |
| R6 | Stop discipline | Every BUY needs a hard stop; no stop + down >7% → EXIT |
| R7 | Cash deployment | Cash + margin >40% in RISK-ON → must recommend 2+ new entries |
| R8 | Single entry | One order per position per day, correctly sized from the start |
| R9 | Leveraged lockout | 30-day lockout after selling any 2X/3X ETF |
| R10 | ASML pattern | Always check ASML in every European scan |
| R11 | EUR-only entries | All new buys must be EUR-denominated; US/Asia via Tradegate ETFs |
| R12 | No forced loss exits | EXIT only on stop hit, binary catalyst, or thesis reversal |
| R13 | Continuity | Default HOLD if no new catalyst since last advice |
| R14 | Overlooked factor | Include one non-consensus angle per major position |

---

## 6. Output Format

All output is **tables only** — no prose paragraphs. Header: `# Portfolio Review — YYYY-MM-DD`.

Example position dashboard row:
```
| 1 | ASML | 4 | €1,212 | €1,243 | +€124 | +2.6% | HOLD | H | €1,180 | €1,350 | At mid-range; thesis intact |
```

Example opportunity scan row:
```
| RHM | Xetra | €185 | €178 | €210 | €3,200 | 3.6:1 | European rearmament — defence budget acceleration |
```

---

## 7. Combining with Other Skills

| Workflow | Sequence |
|----------|----------|
| Full morning routine | **Portfolio Review** → Market regime + position dashboard |
| New entry research | **Portfolio Review** (EUR scan) → **Technical Analyst** (chart confirmation) |
| Position sizing | **Portfolio Review** (identify entry) → **Position Sizer** (exact units) |
| Earnings risk check | **Earnings Calendar** (upcoming dates) → **Portfolio Review** (R12 check) |
| Thesis tracking | **Portfolio Review** (HOLD/EXIT) → **Trader Memory Core** (update thesis state) |

---

## 8. Resources

| File | Purpose |
|------|---------|
| `references/trading-rules.md` | All 14 hard rules with violation checklist |
| `references/review-framework.md` | Step-by-step review structure with output templates |
| `references/degiro-reference.md` | Exchanges, EUR ETF list, watchlist, stop-loss setup |
| `TRADING_SYSTEM_MASTER.md` (root) | Complete trading system with portfolio baseline and behavioral patterns |
