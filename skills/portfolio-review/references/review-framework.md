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

**Pricing:** Use the price from the user's screenshot as the current price (R15). Do not substitute another source for held positions.

```
| # | Symbol | Qty | Entry € | Now € | P&L € | P&L % | Action    | Conf  | Stop € | Target € | Thesis Status | Reason         |
|---|--------|-----|---------|-------|-------|-------|-----------|-------|--------|----------|---------------|----------------|
| 1 |        |     |         |       |       |       | HOLD/ADD… | H/M/L |        |          | INTACT        |                |
```

Followed by footnotes:
```
⚠️ Overlooked — [Symbol]: [Non-consensus angle with factual basis] (R14)
```

Action codes:
- `HOLD` — thesis intact, no change
- `ADD` — increase position (only if rules permit and R16 real-money check passes)
- `REDUCE` — trim position size
- `EXIT` — close position (only if R17 conditions met: stop hit, thesis broken, or binary event risk)
- `STOP-HIT` — stop loss triggered, exit immediately
- `WATCH` — monitor closely, no action yet

Thesis Status codes (replaces "Days Left" — there is no time-based exit):
- `INTACT` — original thesis still valid, catalyst not yet played out
- `WEAKENING` — one or more thesis conditions deteriorating but not yet broken
- `BROKEN` — the reason for holding no longer exists → EXIT justified
- `BINARY EVENT` — earnings/FDA/macro event within 5 days → assess risk per R12

## Step 4 — EUR Opportunity Scan

Header: `## EUR Opportunity Scan`

Scan sequence: European large caps → Tradegate Core ETFs → Asia via EUR ETFs.
All entries EUR-denominated (R11). Size at 1% account risk.

**Pricing requirement (R15):** Before writing any row, WebSearch the current EUR price for that instrument on the stated exchange. Include the verification inline: `(verified €X.XX, [source])`. If the price cannot be confirmed, write `[verify price]` — do not populate entry/stop/target.

**Real money check (R16):** Only include setups you would personally enter with your own savings at the current price and size. Remove or downgrade to WATCH any setup where conviction is not genuinely high.

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

## Step 7 — Proactive Intelligence

Header: `## Proactive Intelligence`

Apply genuine judgment beyond rules. Flag anything important the user has not explicitly asked about.

**Blind spots:**
```
| Issue | Position(s) | Severity | Suggested action |
|-------|-------------|----------|-----------------|
```
Look for: oversized positions, sector overconcentration (>40% in one sector), a thesis catalyst that has already passed with no reassessment, positions where the original entry reason is no longer valid.

**Macro risks (up to 3):**
List specific macro factors that could hurt this portfolio over the next 2–4 weeks. State factual basis. Skip if nothing material.

**Ideas radar (up to 2):**
```
| Symbol | Exchange | Why interesting | Status |
|--------|----------|-----------------|--------|
```
These are not BUY recommendations. They are setups worth monitoring based on current conditions.

If nothing to flag: `No additional flags — portfolio appears aligned with current conditions.`

---

## Output Standards

- Header: `# Portfolio Review — YYYY-MM-DD`
- Tables only — no prose paragraphs between sections
- EUR values for all positions; USD only for legacy grandfathered holdings (label clearly)
- Write `[verify price]` if a price cannot be confirmed — never guess
- Maximum 2% portfolio risk on any single trade
