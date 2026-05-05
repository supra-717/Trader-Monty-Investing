---
name: portfolio-review
description: Run a full DeGiro swing-trader portfolio review using the 14-rule trading system. Use when the user provides a portfolio screenshot, CSV, or data paste and asks for a review, position analysis, EUR opportunity scan, or priority actions. Also triggers for "review my portfolio", "morning brief", "run portfolio review", or the /portfolio-review command.
---

# Portfolio Review

## Overview

Execute a structured 7-step portfolio review for a DeGiro EUR-based swing trader, applying the 14 hard rules on every position. Accept portfolio data from screenshots, CSV paste, or manual input — no broker API required. Output in tables only; no prose paragraphs.

## When to Use

- User provides a portfolio screenshot or data and says "review", "portfolio review", or similar
- User types `/portfolio-review`
- User asks for a morning brief
- User asks whether to hold, add, reduce, or exit a specific position
- User asks for EUR new-entry ideas

## Prerequisites

No API key required. Uses WebSearch to fetch current market prices and news.

## Workflow

### Step 0 — Load Portfolio Data

Accept data in any of these forms:
- Screenshot image (read visible positions, prices, quantities)
- CSV paste
- Manual table from user
- Fall back to the baseline in `TRADING_SYSTEM_MASTER.md` Section 5 only if user explicitly says to use the baseline

State which input was used: `Using: [screenshot / CSV / baseline]`

### Step 0.5 — Continuity Check (Rule R13)

Read `references/trading-rules.md` for all 14 rules before proceeding.

State which positions have changed since last session advice. If nothing materially new has happened → output:
`No change from yesterday — thesis intact` for each unchanged position before proceeding.

### Step 1 — Market Regime

Fetch current data via WebSearch for: S&P 500, NASDAQ 100, DAX, VIX, EUR/USD, US 10Y yield, Gold (USD), Oil (WTI).

Output:
```
| Index      | Price | 1D Chg | Signal |
|------------|-------|--------|--------|
| S&P 500    |       |        |        |
| NASDAQ 100 |       |        |        |
| DAX        |       |        |        |
| VIX        |       |        | LOW <15 / ELEVATED 15-25 / HIGH >25 |
| EUR/USD    |       |        |        |
| US 10Y     |       |        |        |
| Gold (USD) |       |        |        |
| Oil (WTI)  |       |        |        |
```

Classify environment: **RISK-ON 🟢 / NEUTRAL 🟡 / RISK-OFF 🔴** — one sentence why.

Note: VIX level gates Rule R3 (leveraged ETF) and Rule R7 (cash deployment mandate).

### Step 2 — Catalysts This Week

Search for earnings, central bank events, and macro data releases affecting held positions within the next 5 trading days.

Output:
```
| Date | Event | Positions Affected | Binary? |
|------|-------|--------------------|---------|
```

Flag any event as `⚠️ BINARY` if it is an earnings release or FDA decision within 5 days on a position >1.5% portfolio risk (Rule R12 trigger).

### Step 3 — Position Dashboard

For each held position, apply all 14 rules before assigning an action. Read `references/trading-rules.md` to check each rule.

Output:
```
| # | Symbol | Qty | Entry | Now | P&L€ | P&L% | Action | Conf | Stop | Target | Reason |
|---|--------|-----|-------|-----|------|------|--------|------|------|--------|--------|
```

**Action codes:** `HOLD` / `ADD` / `REDUCE` / `EXIT` / `STOP-HIT` / `WATCH`
**Confidence:** H (>70%) / M (50–70%) / L (<50%)

After the table, add a `⚠️ Overlooked:` footnote for each major position with a non-consensus angle (Rule R14). Only include if factual basis exists — label clearly.

**Rule checks to run on each row:**
- R1: Is the stock in a downtrend >3 months? → block BUY unless base confirmed
- R2: Is this a macro/structural theme? → do not suggest EXIT within 5 days of entry if thesis intact
- R4: Is this the 3rd entry in same stock with 2nd trade underperforming? → flag COOLING PERIOD
- R5: P/E >40x and extended? → only ADD on 20-week MA pullback or post-earnings beat
- R6: Position down >7% with no stop? → recommend EXIT, not HOLD
- R9: Was a leveraged ETF sold within 30 days? → flag lockout if re-entry attempted
- R12: Losing position — only EXIT if stop hit, binary catalyst imminent, or thesis reversed

### Step 4 — EUR Opportunity Scan

EUR-denominated instruments only (Rule R11). Size all entries at 1% account risk (~€400 risk per trade).

Read `references/degiro-reference.md` for the standard watchlist and preferred ETFs.

Scan order:
1. European large caps (Xetra / Euronext Paris / Amsterdam)
2. Core Selection ETFs on Tradegate (€1 flat fee)
3. Asia exposure via EUR ETFs on Tradegate

Apply Rule R1 (no falling knives), Rule R3 (leveraged ETF gating), Rule R5 (high-PE entry), Rule R11 (EUR-only).

Output:
```
| Symbol | Exchange | Entry | Stop | Target | Size EUR | R/R | Catalyst |
|--------|----------|-------|------|--------|----------|-----|---------|
```

Minimum R/R: 2:1. Skip any setup with R/R < 2:1.

### Step 5 — Priority Actions

List the top 5 actions numbered by urgency. Give exact instructions (e.g., "Sell 4 of 10 MSFT at market open on Tradegate").

Apply Rule R7: if cash + margin > 40% of portfolio AND regime is RISK-ON → must include 2+ new BUY entries in this list.

```
1. [URGENCY: IMMEDIATE / TODAY / THIS WEEK] — [Exact action]
2. ...
```

### Step 6 — Portfolio Health

Output:
```
| Metric              | Value | Status        |
|---------------------|-------|---------------|
| Diversification     |       | Good / Concern |
| Cash ratio          |       | OK / Too High / Too Low |
| USD exposure        |       | Grandfathered / Expanding |
| Active rule violations |    | [list or None] |
| Overall score       | x/10  |               |
```

Score deductions: -1 per active rule violation, -1 if cash >40% in RISK-ON, -1 if any position has no stop.

### Output Rules

- **Tables only — no prose paragraphs**
- All values in EUR (USD-priced legacy holdings shown in USD with EUR equivalent)
- Header: `# Portfolio Review — YYYY-MM-DD`
- If current price unavailable: write `[check manually]` — never guess
- Max 2% portfolio risk per single trade
- Never recommend adding USD-denominated new positions (Rule R11)

## Resources

- `references/trading-rules.md` — All 14 hard rules with trigger conditions
- `references/review-framework.md` — Full review structure with output templates
- `references/degiro-reference.md` — Exchanges, watchlist, EUR ETF list, stop-loss setup
- `TRADING_SYSTEM_MASTER.md` (repo root) — Complete system with portfolio baseline and behavioral patterns
