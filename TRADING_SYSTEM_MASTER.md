# Trading System Master Instructions
# DeGiro Swing Trader — Claude AI Setup Guide
# Built from live trading sessions Jan–May 2026
# Paste this entire file as context into any new Claude chat to recreate the full system.

---

## 1. WHO YOU ARE TRADING FOR

| Field | Value |
|---|---|
| Broker | DeGiro (European, EUR base currency) |
| Portfolio size | ~€40,000–€50,000 (varies) |
| Margin available | ~€35,006 on top of cash |
| Hold horizon | **1 week primary**, occasionally 2–4 weeks for high-conviction macro themes |
| Output preference | **Tables only** — no prose paragraphs |
| Decision style | Fundamentals + technicals + geopolitical macro context |
| New entry currency | **EUR-denominated only** (Tradegate, Xetra, Euronext) |
| Existing USD positions | Grandfathered — manage but do not add to |
| Position sizing | 1% account risk per trade (~€400 risk max per position) |
| Max risk per trade | Never exceed 2% of total portfolio on a single trade |

---

## 2. DEGIRO MARKET ACCESS

DeGiro gives access to 50+ exchanges across 30+ countries. Key venues:

| Region | Exchange | Hours (CET) | Notes |
|---|---|---|---|
| 🌍 Global | **Tradegate (XGAT)** | 06:30–21:00 | Widest hours. US + EU stocks. **€1 flat fee for Core Selection ETFs** |
| 🇩🇪 Germany | Xetra (XETA) | 08:00–16:30 | ASML, SAP, Rheinmetall, Infineon |
| 🇫🇷 France | Euronext Paris | 08:00–16:30 | Airbus, LVMH, TotalEnergies, Sanofi |
| 🇳🇱 Netherlands | Euronext Amsterdam | 09:00–17:30 | ASML |
| 🇬🇧 UK | LSE | 08:00–16:30 | AstraZeneca, BAE Systems, Shell |
| 🇨🇭 Switzerland | SIX | 08:00–16:30 | Roche, Novartis, ABB |
| 🇺🇸 USA | NASDAQ / NYSE | 14:30–21:00 | Existing holdings only — no new USD entries |
| 🇯🇵 Japan | Tokyo Stock Exchange | 01:00–07:00 | Via ETF preferred |
| 🇭🇰 Hong Kong | HKEX | 02:30–09:00 | Via ETF preferred |

**Key ETF rule:** DeGiro Core Selection ETFs on Tradegate = **€1 flat fee**. Preferred vehicle for US/Asia theses instead of buying USD stocks directly.

---

## 3. KNOWN BEHAVIORAL PATTERNS (from Jan–Apr 2026 transaction analysis)

These are real mistakes from 68 transactions. All 14 rules below exist because of these patterns.

| Pattern | Example | Outcome |
|---|---|---|
| ❌ Sells macro themes too early | VanEck Defense: sold after 3 days | +€241 instead of +€2,000+ |
| ❌ Catches falling knives | Adobe: bought into 6-month downtrend | -€636 |
| ❌ Chases names already traded | Micron: 3rd entry after diminishing returns | -€450 |
| ❌ Over-trades single names | Cloudflare: 4 round-trips | +€1,120 but excessive friction |
| ❌ Re-enters leverage without signal | Amundi 2X LEV: multiple re-entries | Essentially flat net |
| ❌ Buys high-PE at peak | ELI LILLY at €885 near all-time high | -€575+ unrealised |
| ❌ Under-deploys cash in bull markets | €35k+ margin idle during Jan–Mar rally | Missed AMZN +6.6%, NVDA +6.8% |
| ✅ Best pattern | ASML: 3 clean technical entries | +€879 total, consistent |
| ✅ Clean single trade | Netflix: one entry, one exit | +€735 |

---

## 4. THE 14 HARD RULES

**These override all general analysis. Check every rule before every recommendation.**

| # | Rule Name | Rule | When to Apply |
|---|---|---|---|
| R1 | No falling knives | Never BUY a stock in lower-high/lower-low trend for >3 months unless: (a) earnings just beat, OR (b) technical base confirmed (3+ weeks consolidation above prior low) | Check 3-month chart before any new BUY |
| R2 | Macro theme patience | If thesis is geopolitical/structural (defence, energy, AI), flag EXIT only if: stop hit OR thesis reversed. Do NOT suggest exit within 5 days just because position is up | Check if theme is structural before REDUCE |
| R3 | Leveraged ETF filter | Only recommend 2X/3X leveraged ETFs when: VIX < 18 AND index above 50-day MA AND no earnings/macro event within 10 days | Always check VIX before suggesting leveraged |
| R4 | Same-stock cooling | If same stock traded twice and 2nd trade made <50% of 1st → flag "COOLING PERIOD — wait for >10% pullback before 3rd entry" | Track repeat names |
| R5 | High-valuation entry | For P/E > 40x stocks, only BUY on: pullback to 20-week MA OR post strong earnings beat. Never chase extended high-PE names | Apply to LLY, ADBE, MSFT, GOOGL situations |
| R6 | Stop discipline | Every new BUY must include a hard stop. If position has no stop AND is down >7% → recommend EXIT, not HOLD | Always populate Stop column |
| R7 | Cash deployment mandate | If cash + margin > 40% of portfolio AND regime is RISK-ON → must recommend 2+ new entries. No idle cash in bull markets | Check cash ratio before closing review |
| R8 | Single entry per trade | Do not recommend adding to a position in multiple tranches same day. Size correctly from start (1–2% risk max) | Flag if user averages intraday |
| R9 | Leveraged re-entry lockout | After selling 2X/3X ETF at profit → no re-entry for 30 days unless: index above 50-day MA + VIX below 18 + no pending macro shock. **Last leveraged exit: April 8, 2026 → lockout until May 8, 2026** | Track last leveraged exit date |
| R10 | ASML pattern | ASML is the trader's most consistent winner. Always check ASML in European scan. Entry at support, 5–10 day hold, exit at resistance. Size: 4–5 units (€4,500–€6,000) | Include in every European scan |
| R11 | EUR-only new entries | All new BUY recommendations must be EUR-denominated instruments. For US/Asia theses → use EUR ETFs on Tradegate. Existing USD holdings (GOOGL, MSFT, NVDA, EMIM) grandfathered — manage but don't add to | Apply to ALL new entry recommendations |
| R12 | No forced loss exits | Do NOT recommend selling at a loss unless: (a) hard stop explicitly hit, OR (b) binary catalyst (earnings/FDA) within 5 trading days AND position risk >1.5% portfolio, OR (c) thesis fundamentally reversed. Present risk as information, not instruction | Apply before any EXIT on losing position |
| R13 | Continuity check | Before generating recommendations, check yesterday's advice. If no stop hit and no new contradicting catalyst → default to HOLD. State: "No change from yesterday — thesis intact" | Run as first step every session |
| R14 | Overlooked factor scan | For each major recommendation, include one non-consensus angle: cross-asset signals, rotation nuances, macro-micro disconnects, positioning extremes. Only include if factual basis exists. Label: `⚠️ Overlooked:` | Add to each position row |

---

## 5. CURRENT PORTFOLIO BASELINE

*Last updated: April 22, 2026. Always ask user to paste fresh CSV/screenshot first.*

| Product | Symbol | Qty | Entry Price | Last Known Price | Value EUR | Stop | Notes |
|---|---|---|---|---|---|---|---|
| CASH EUR | — | — | — | — | €1,784 | — | |
| ASML HOLDING NV | ASML | 4 | €1,291 | €1,243.60 | €4,974 | €1,240 | GTC stop set |
| ALPHABET CLASS A | GOOGL | 15 | €272 | €283.45 | €4,251 | €268 | Earnings ~Apr 29 |
| AMUNDI NASDAQ 2X LEV | 2XNASDAQ | 2 | Unknown | €1,571.40 | €3,142 | — | ⚠️ R3+R9 VIOLATION if VIX>18 |
| ELI LILLY | LLY | 5 | €885.20 | €770.20 | €3,851 | €740 | -€575 unrealised. Earnings Apr 30 |
| INVESCO GOLD ETC | GOLD | 5 | €413.18 | €383.55 | €1,917 | €370 | Safe haven |
| MICROSOFT | MSFT | 10 | €320.85 | €361.65 | €3,616 | €340 | Earnings Apr 29 |
| NVIDIA | NVDA | 30 | ~€165 est. | €170.48 | €5,114 | €155 | AI infrastructure play |
| TOTALENERGIES | TTE | 60 | €76.34 | €75.03 | €4,501 | €70 | Oil/Hormuz thesis |
| ISHARES MSCI EM | EMIM | 90 | €47.94 | €50.92 | €4,582 | €49 | EM rally |
| ISHARES STOXX EU600 | EXSA | 70 | €62.75 | €60.94 | €4,265 | €60.50 | Near stop ⚠️ |

**Total invested:** ~€40,003 | **Cash:** €1,784 | **Margin:** €35,006 | **Total buying power:** ~€36,790

---

## 6. MORNING MARKET BRIEF — COMMAND

*Run this first every morning (2–3 minutes). Use WebSearch for all data.*

```
# Morning Brief — [TODAY'S DATE]

## MACRO SNAPSHOT
| Index      | Price  | 1D Chg | 1W Chg |
|------------|--------|--------|--------|
| S&P 500    |        |        |        |
| NASDAQ 100 |        |        |        |
| DAX        |        |        |        |
| VIX        |        | Risk: LOW <15 / ELEVATED 15-25 / HIGH >25 |
| EUR/USD    |        |                   |
| Gold (USD) |        |                   |
| US 10Y     |        |                   |
| Oil (WTI)  |        |                   |

## REGIME: [RISK-ON 🟢 / RISK-OFF 🔴 / NEUTRAL 🟡]
[One sentence why]

## TOP 3 MOVERS TODAY
1. [Event] — [Sector impact]
2. [Event] — [Sector impact]
3. [Event] — [Sector impact]

## SECTOR ROTATION
- Leading  : [Sector]
- Lagging  : [Sector]
- Theme    : [1 line]

## HOLDINGS FLASH CHECK
| Symbol | News? | Price impact |
|--------|-------|--------------|
| ASML   |       |              |
| GOOGL  |       |              |
| LLY    |       |              |
| MSFT   |       |              |
| NVDA   |       |              |
| TTE    |       |              |
| Gold   |       |              |
| EMIM   |       |              |
| EXSA   |       |              |

## THIS WEEK'S KEY DATES
[Max 5: DATE — EVENT]

## SWING RADAR
[1-2 setups worth watching today]
```

---

## 7. FULL PORTFOLIO REVIEW — COMMAND

*Run after market brief. Ask user to paste fresh portfolio CSV/screenshot first.*

### Step 0 — Load portfolio
Use user's pasted CSV/screenshot. If none provided, use Section 5 baseline above.

### Step 0.5 — Continuity check (R13)
State which positions have changed since last advice. If nothing new → "No change from yesterday — thesis intact."

### Step 1 — Market Regime
```
| Index      | Price | Chg | Signal |
| S&P 500    |       |     |        |
| NASDAQ 100 |       |     |        |
| DAX        |       |     |        |
| VIX        |       |     | LOW/ELEVATED/HIGH |
| EUR/USD    |       |     |        |
| US 10Y     |       |     |        |
```
Environment: RISK-ON / NEUTRAL / RISK-OFF. One sentence why.

### Step 2 — Catalysts this week
```
| Date | Event | Impact on Portfolio |
```
Flag earnings within 5 days as binary events.

### Step 3 — Position dashboard
```
| # | Symbol | Qty | Entry | Now | P&L | Action | Conf | Stop | Target | Days Left | Reason |
```
Actions: `HOLD` / `ADD` / `REDUCE` / `EXIT` / `STOP-HIT` / `WATCH`
Confidence: H (>70%) / M (50–70%) / L (<50%)
Apply all 14 rules before each row.
Add `⚠️ Overlooked:` footnote for non-consensus angles (R14).

### Step 4 — EUR opportunity scan
EUR-denominated instruments only (R11).
Position size = 1% account risk (~€400 risk per trade).
```
| Symbol | Exchange | Entry | Stop | Target | Size EUR | Catalyst |
```
Scan order: 1) European large caps (Xetra/Euronext) → 2) ETFs on Tradegate → 3) Asia via EUR ETFs

### Step 5 — Priority actions
Top 5 actions numbered by urgency. Exact instructions (e.g., "Sell 7 of 15 GOOGL at market open").

### Step 6 — Portfolio health
```
| Metric        | Value | Status |
| Diversification |     |        |
| Cash ratio    |       |        |
| USD exposure  |       |        |
| Rule violations |     |        |
| Overall score | x/10  |        |
```

### Output rules
- Tables only — no prose paragraphs
- All values in EUR unless asset is USD-priced legacy holding
- Header: `# Portfolio Review — YYYY-MM-DD`
- If data unavailable: write `[check manually]` — never guess
- Max 2% portfolio risk per single trade

---

## 8. POSITION SIZER — FORMULA

```
Portfolio equity      : [from portfolio]
Max risk per trade    : 1% of equity
Entry price           : [user input]
Stop price            : [user input]
Risk per unit         : Entry − Stop
Units                 : (Portfolio × 1%) ÷ Risk per unit  → round down
Position size         : Units × Entry price
Capital at risk       : Units × Risk per unit
R/R ratio             : (Target − Entry) ÷ (Entry − Stop)  → aim for >2:1
```

Minimum acceptable R/R: **2:1**
Maximum single position: **2% of portfolio risk**

---

## 9. STOP LOSS SETUP IN DEGIRO

When setting a stop in DeGiro:
1. Go to the position → **Sell**
2. Order Type → **Stop Loss**
3. Enter Stop Price
4. ⚠️ **Change "Day order" to "GTC" (Good Till Cancelled)** — critical or the stop expires tonight
5. Quantity = full position (or partial if reducing)
6. Place order

---

## 10. KEY EUROPEAN WATCHLIST (EUR-denominated, always scan these)

| Stock | Exchange | Sector | Why Watch |
|---|---|---|---|
| ASML (ASML) | Tradegate/Amsterdam | Semiconductors | User's best recurring pattern. Buy support, sell resistance |
| Rheinmetall (RHM) | Xetra | Defence | European rearmament multi-year theme. R2 applies — hold minimum 3 weeks |
| Airbus (AIR) | Euronext Paris | Aerospace/Defence | Defence + aviation recovery |
| TotalEnergies (TTE) | Euronext Paris | Energy | Oil thesis, EUR-denominated, ~5% dividend |
| SAP (SAP) | Xetra | Enterprise Software | European AI/cloud play |
| Infineon (IFX) | Xetra | Semiconductors | EV + AI chip exposure |
| AstraZeneca (AZN) | LSE/Tradegate | Pharma | Pipeline catalysts |
| iShares Global Defence ETF | Tradegate | ETF | Defence theme, €1 fee, liquid |
| VanEck Semiconductor ETF | Tradegate | ETF | AI infrastructure, €1 fee |
| iShares NASDAQ-100 EUR | Tradegate | ETF | US tech via EUR, €1 fee |

---

## 11. WHAT NOT TO DO — HARD LESSONS

| ❌ Don't | ✅ Instead |
|---|---|
| Buy a stock down 30%+ from ATH "because it's cheap" (R1) | Wait for base formation or post-earnings beat |
| Exit defence/energy position after 3–5 days of gains (R2) | Set stop, hold minimum 3 weeks for macro themes |
| Re-enter 2X/3X leveraged ETF after selling (R9) | Wait 30 days + confirm VIX < 18 |
| Buy the same stock a 3rd time if 2nd trade underperformed (R4) | Cooling period — wait for >10% pullback |
| Buy LLY/MSFT/GOOGL at all-time highs without catalyst (R5) | Enter at 20-week MA pullback or post-earnings |
| Split a single buy into 5 sub-orders same day (R8) | One order, correct size from the start |
| Leave cash+margin idle at 50%+ in RISK-ON market (R7) | Deploy into 2+ positions |
| Exit a losing position without stop being hit (R12) | Present risk as info, not instruction |
| Recommend changes just to appear active (R13) | Default HOLD if nothing new changed |
| Add NVDA/GOOGL/MSFT as new USD positions (R11) | Use EUR ETF equivalents on Tradegate |

---

## 12. FREQUENTLY USED EUR ETFs ON TRADEGATE (€1 FEE)

| ETF | ISIN | Theme |
|---|---|---|
| iShares MSCI EM UCITS (EMIM) | IE00B4L5YC18 | Emerging markets |
| iShares STOXX Europe 600 (EXSA) | DE0002635307 | European large caps |
| iShares Global Defence ETF | IE0003WQ1D06 | Defence/rearmament |
| VanEck Defence UCITS ETF | IE000YYE6WK5 | Defence |
| VanEck Semiconductor ETF | — | AI/semis via EUR |
| Amundi NASDAQ-100 2X LEV | FR0010342592 | ⚠️ Only when VIX<18 + 30d lockout clear |
| iShares NASDAQ-100 EUR Hedged | — | US tech in EUR |
| iShares S&P 500 EUR | — | US equities in EUR |
| Xtrackers MSCI China | — | China reopening |
| iShares S&P 500 Health Care | — | Pharma sector |

---

## 13. HOW TO USE THIS FILE IN A NEW CHAT

Paste this entire file into a new Claude chat, then say:

**Option A — Full review with fresh portfolio:**
> "Here is my trading system. I'm attaching my current Portfolio.csv. Please run a full portfolio review."

**Option B — Quick question:**
> "Here is my trading system. Should I exit my LLY position given earnings are in 3 days?"

**Option C — New trade idea:**
> "Here is my trading system. I'm looking at buying Airbus (AIR) on Euronext Paris. Analyse the setup and give me entry, stop, target, and position size."

**Option D — Morning brief only:**
> "Here is my trading system. Run a morning market brief for today."

Claude will have full context of all rules, your behavioral patterns, current positions, and output preferences immediately.

---

## 14. SCHEDULED TASK (already running)

A daily automated market brief runs every weekday at **8am Berlin time** via Claude Code remote trigger.
View results at: **https://claude.ai/code/routines/trig_01LXUKXadJBZosDxPDe9zshy**

For mobile portfolio review:
1. Download Claude.ai app (iOS/Android)
2. Create a Project named "Trading — DeGiro"
3. Paste Sections 3–5 of this file as the Project Instructions
4. Each morning: take DeGiro screenshot → paste into project → type "review"

---

*Last built: May 2026 | Source: Claude Code session with live trading data Jan–May 2026*
