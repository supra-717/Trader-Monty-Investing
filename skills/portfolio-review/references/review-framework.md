# Portfolio Review Framework

Full 7-step review structure with output templates.

## Step 0 — Load Portfolio Data

Accepted input formats:
- **Screenshot** — read positions, prices, quantities visually
- **CSV paste** — parse columns for symbol, qty, entry price, current price
- **Manual table** — user-provided data in any tabular format
- **Baseline fallback** — only if user explicitly requests it; use Section 5 of `TRADING_SYSTEM_MASTER.md`

First line of output: `Using: [screenshot / CSV / baseline — dated YYYY-MM-DD]`

## Step 0.5 — Continuity Check (R13)

State for each position whether anything material has changed since last advice. Format:

```
Continuity check:
- ASML: No change — thesis intact
- TTE: Earnings beat reported — update required
- [NEW]: GEV added to portfolio since last review
```

Default to HOLD for positions with no new catalysts.

## Step 1 — Market Regime

Header: `## Market Regime — [DATE]`

```
| Index      | Price | 1D Chg | Signal                              |
|------------|-------|--------|-------------------------------------|
| S&P 500    |       |        |                                     |
| NASDAQ 100 |       |        |                                     |
| DAX        |       |        |                                     |
| VIX        |       |        | LOW <15 / ELEVATED 15-25 / HIGH >25 |
| EUR/USD    |       |        |                                     |
| US 10Y     |       |        |                                     |
| Gold (USD) |       |        |                                     |
| Oil (WTI)  |       |        |                                     |

Environment: RISK-ON 🟢 / NEUTRAL 🟡 / RISK-OFF 🔴
Reason: [one sentence]
```

VIX thresholds gate:
- R3 (leveraged ETF): VIX must be < 18
- R7 (cash mandate): only applies in RISK-ON regime

## Step 2 — Catalysts This Week

Header: `## Catalysts — Week of [DATE]`

```
| Date | Event               | Positions Affected | Binary? |
|------|---------------------|--------------------|---------|
|      | [earnings/macro/CB] |                    | ⚠️ YES / No |
```

Binary event = earnings or FDA decision within 5 days on position >1.5% portfolio risk.
Binary events trigger R12 consideration (may recommend REDUCE before event if exposure is high).

## Step 3 — Position Dashboard

Header: `## Position Dashboard`

```
| # | Symbol | Qty | Entry € | Now € | P&L € | P&L % | Action    | Conf | Stop € | Target € | Reason         |
|---|--------|-----|---------|-------|-------|-------|-----------|------|--------|----------|----------------|
| 1 |        |     |         |       |       |       | HOLD/ADD… | H/M/L|       |          |                |
```

Followed by footnotes:
```
⚠️ Overlooked — [Symbol]: [Non-consensus angle with factual basis] (R14)
```

Action codes:
- `HOLD` — thesis intact, no change
- `ADD` — increase position (only if rules permit)
- `REDUCE` — trim position size
- `EXIT` — close position
- `STOP-HIT` — stop loss triggered, exit immediately
- `WATCH` — monitor closely, no action yet

## Step 4 — EUR Opportunity Scan

Header: `## EUR Opportunity Scan`

Scan sequence: European large caps → Tradegate Core ETFs → Asia via EUR ETFs.
All entries EUR-denominated (R11). Size at 1% account risk.

```
| Symbol | Exchange    | Entry € | Stop € | Target € | Size € | R/R | Catalyst        |
|--------|-------------|---------|--------|----------|--------|-----|-----------------|
|        | Tradegate   |         |        |          |        |     |                 |
```

Skip any row with R/R < 2:1.
Always include ASML check (R10).
Flag leveraged ETFs with ⚠️ and confirm R3 + R9 clear before including.

## Step 5 — Priority Actions

Header: `## Priority Actions`

```
1. [IMMEDIATE] — [Exact instruction, e.g., "Set GTC stop on TTE at €70.00"]
2. [TODAY] — ...
3. [TODAY] — ...
4. [THIS WEEK] — ...
5. [THIS WEEK] — ...
```

R7 check: if cash + margin > 40% portfolio AND RISK-ON → actions 1–2 must be new BUY entries.

## Step 6 — Portfolio Health

Header: `## Portfolio Health`

```
| Metric                | Value   | Status                        |
|-----------------------|---------|-------------------------------|
| Diversification       | X stocks / Y ETFs | Good / Concentrated |
| Cash ratio            | X%      | OK (<40%) / High (>40%)       |
| USD exposure          | €X (X%) | Grandfathered / Expanding ⚠️  |
| Active rule violations| [list]  | None / R3: leveraged… / etc.  |
| Positions without stop| X       | OK / Fix: [symbols]           |
| Overall score         | X/10    |                               |
```

Scoring:
- Start at 10
- -1 per active rule violation
- -1 if cash ratio > 40% in RISK-ON
- -1 per position missing a hard stop
- -1 if any position down >7% with no stop and no EXIT recommended

## Output Standards

- Header: `# Portfolio Review — YYYY-MM-DD`
- Tables only — no prose paragraphs between sections
- EUR values for all positions; USD only for legacy grandfathered holdings (label clearly)
- Write `[check manually]` if a price cannot be fetched — never guess
- Maximum 2% portfolio risk on any single trade
