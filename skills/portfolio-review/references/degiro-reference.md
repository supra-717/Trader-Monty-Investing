# DeGiro Reference — Exchanges, Watchlist, ETFs

## DeGiro Market Access

| Region | Exchange | Hours (CET) | Notes |
|--------|----------|-------------|-------|
| Global | Tradegate (XGAT) | 06:30–21:00 | Widest hours. US + EU stocks. €1 flat fee for Core Selection ETFs |
| Germany | Xetra (XETA) | 08:00–16:30 | ASML, SAP, Rheinmetall, Infineon |
| France | Euronext Paris | 08:00–16:30 | Airbus, LVMH, TotalEnergies, Sanofi |
| Netherlands | Euronext Amsterdam | 09:00–17:30 | ASML |
| UK | LSE | 08:00–16:30 | AstraZeneca, BAE Systems, Shell |
| Switzerland | SIX | 08:00–16:30 | Roche, Novartis, ABB |
| USA | NASDAQ / NYSE | 14:30–21:00 | Existing holdings only — no new USD entries (R11) |

**Core ETF rule:** DeGiro Core Selection ETFs on Tradegate = €1 flat fee. Preferred vehicle for US/Asia theses instead of buying USD stocks directly.

## Stop Loss Setup in DeGiro

1. Go to the position → **Sell**
2. Order Type → **Stop Loss**
3. Enter Stop Price
4. ⚠️ **Change "Day order" to "GTC" (Good Till Cancelled)** — critical or the stop expires at end of session
5. Quantity = full position (or partial if reducing)
6. Place order

Always set GTC stops on every new position (Rule R6).

## European Watchlist (always scan these)

| Stock | Exchange | Sector | Why Watch |
|-------|----------|--------|-----------|
| ASML (ASML) | Tradegate / Amsterdam | Semiconductors | User's best recurring pattern. Buy support, sell resistance. Size 4–5 units (R10) |
| Rheinmetall (RHM) | Xetra | Defence | European rearmament multi-year theme. R2 applies — hold minimum 3 weeks |
| Airbus (AIR) | Euronext Paris | Aerospace / Defence | Defence + aviation recovery |
| TotalEnergies (TTE) | Euronext Paris | Energy | Oil thesis, EUR-denominated, ~5% dividend |
| SAP (SAP) | Xetra | Enterprise Software | European AI / cloud play |
| Infineon (IFX) | Xetra | Semiconductors | EV + AI chip exposure |
| AstraZeneca (AZN) | LSE / Tradegate | Pharma | Pipeline catalysts |

## Core Selection ETFs on Tradegate (€1 flat fee)

| ETF | ISIN | Theme | Leveraged? |
|-----|------|-------|------------|
| iShares MSCI EM UCITS (EMIM) | IE00B4L5YC18 | Emerging markets | No |
| iShares STOXX Europe 600 (EXSA) | DE0002635307 | European large caps | No |
| iShares Global Defence ETF | IE0003WQ1D06 | Defence / rearmament | No |
| VanEck Defence UCITS ETF | IE000YYE6WK5 | Defence | No |
| VanEck Semiconductor ETF | — | AI / semis via EUR | No |
| iShares NASDAQ-100 EUR Hedged | — | US tech in EUR | No |
| iShares S&P 500 EUR | — | US equities in EUR | No |
| Xtrackers MSCI China | — | China reopening | No |
| iShares S&P 500 Health Care | — | Pharma sector | No |
| Amundi NASDAQ-100 2X LEV | FR0010342592 | US tech 2x leverage | ⚠️ YES — R3 + R9 apply |

**Leveraged ETF gate (R3):** Only use 2X/3X when VIX < 18 AND index above 50-day MA AND no macro event within 10 days.
**Leveraged re-entry lockout (R9):** 30-day lockout after any leveraged ETF sale.

## Position Sizing Formula

```
Portfolio equity      : [from portfolio]
Max risk per trade    : 1% of equity (~€400 on €40k account)
Entry price           : [user input]
Stop price            : [user input]
Risk per unit         : Entry − Stop
Units                 : (Portfolio × 1%) ÷ Risk per unit  → round down
Position size         : Units × Entry price
Capital at risk       : Units × Risk per unit
R/R ratio             : (Target − Entry) ÷ (Entry − Stop)  → aim ≥ 2:1
```

Minimum acceptable R/R: **2:1**
Maximum single position: **2% of portfolio risk**

## What NOT to Do

| Avoid | Do Instead |
|-------|-----------|
| Buy a stock down 30%+ from ATH "because it's cheap" | Wait for base formation or post-earnings beat (R1) |
| Exit defence/energy position after 3–5 days of gains | Set stop, hold minimum 3 weeks for macro themes (R2) |
| Re-enter 2X/3X leveraged ETF after selling | Wait 30 days + confirm VIX < 18 (R9) |
| Buy the same stock a 3rd time if 2nd trade underperformed | Cooling period — wait for >10% pullback (R4) |
| Buy LLY/MSFT/GOOGL at all-time highs without catalyst | Enter at 20-week MA pullback or post-earnings (R5) |
| Split a single buy into 5 sub-orders same day | One order, correct size from the start (R8) |
| Leave cash+margin idle at 50%+ in RISK-ON market | Deploy into 2+ positions (R7) |
| Exit a losing position without stop being hit | Present risk as information, not instruction (R12) |
| Add NVDA/GOOGL/MSFT as new USD positions | Use EUR ETF equivalents on Tradegate (R11) |
