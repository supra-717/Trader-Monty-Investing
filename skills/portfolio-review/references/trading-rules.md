# Trading Rules — 14 Hard Rules

These rules override all general analysis. Check every rule before every recommendation.

## Rule Reference Table

| # | Rule Name | Rule | When to Apply |
|---|-----------|------|---------------|
| R1 | No falling knives | Never BUY a stock in lower-high/lower-low trend for >3 months unless: (a) earnings just beat, OR (b) technical base confirmed (3+ weeks consolidation above prior low) | Check 3-month chart before any new BUY |
| R2 | Macro theme patience | If thesis is geopolitical/structural (defence, energy, AI), flag EXIT only if: stop hit OR thesis reversed. Do NOT suggest exit within 5 days just because position is up | Check if theme is structural before REDUCE |
| R3 | Leveraged ETF filter | Only recommend 2X/3X leveraged ETFs when: VIX < 18 AND index above 50-day MA AND no earnings/macro event within 10 days | Always check VIX before suggesting leveraged |
| R4 | Same-stock cooling | If same stock traded twice and 2nd trade made <50% of 1st → flag "COOLING PERIOD — wait for >10% pullback before 3rd entry" | Track repeat names |
| R5 | High-valuation entry | For P/E > 40x stocks, only BUY on: pullback to 20-week MA OR post strong earnings beat. Never chase extended high-PE names | Apply to LLY, ADBE, MSFT, GOOGL situations |
| R6 | Stop discipline | Every new BUY must include a hard stop. If position has no stop AND is down >7% → recommend EXIT, not HOLD | Always populate Stop column |
| R7 | Cash deployment mandate | If cash + margin > 40% of portfolio AND regime is RISK-ON → must recommend 2+ new entries. No idle cash in bull markets | Check cash ratio before closing review |
| R8 | Single entry per trade | Do not recommend adding to a position in multiple tranches same day. Size correctly from start (1–2% risk max) | Flag if user averages intraday |
| R9 | Leveraged re-entry lockout | After selling 2X/3X ETF at profit → no re-entry for 30 days unless: index above 50-day MA + VIX below 18 + no pending macro shock | Track last leveraged exit date |
| R10 | ASML pattern | ASML is the trader's most consistent winner. Always check ASML in European scan. Entry at support, 5–10 day hold, exit at resistance. Size: 4–5 units (€4,500–€6,000) | Include in every European scan |
| R11 | EUR-only new entries | All new BUY recommendations must be EUR-denominated instruments. For US/Asia theses → use EUR ETFs on Tradegate. Existing USD holdings grandfathered — manage but don't add to | Apply to ALL new entry recommendations |
| R12 | No forced loss exits | Do NOT recommend selling at a loss unless: (a) hard stop explicitly hit, OR (b) binary catalyst (earnings/FDA) within 5 trading days AND position risk >1.5% portfolio, OR (c) thesis fundamentally reversed. Present risk as information, not instruction | Apply before any EXIT on losing position |
| R13 | Continuity check | Before generating recommendations, check previous advice. If no stop hit and no new contradicting catalyst → default to HOLD. State: "No change from yesterday — thesis intact" | Run as first step every session |
| R14 | Overlooked factor scan | For each major recommendation, include one non-consensus angle: cross-asset signals, rotation nuances, macro-micro disconnects, positioning extremes. Only include if factual basis exists. Label: `⚠️ Overlooked:` | Add to each position row |
| R15 | Pricing accuracy | For held positions: use the price from the user's screenshot — it is the authoritative current price. For any newly recommended stock: WebSearch the current EUR price on the target exchange before quoting it. Write `[verify price]` if it cannot be confirmed. Never guess a price. | Every new entry recommendation; never override screenshot prices for held positions |
| R16 | Real money standard | Before recommending any BUY or ADD, ask: would you personally put your own savings into this right now? If the honest answer is no — because the setup is weak, the timing is wrong, or conviction is low — do not recommend it. A loss is a real setback, not an abstraction. Flag low-conviction entries with Conf: L and a warning. | Every BUY / ADD recommendation |
| R17 | Thesis-driven exits only | There is no hard time limit on any trade. Do not suggest an exit because X days have passed or because the position is up. Exit only when: (a) the hard stop is hit, (b) the original thesis is fundamentally broken (catalyst passed, sector rotation reversed, fundamental deterioration), or (c) a binary event creates unacceptable risk. "Thesis Status" replaces "Days Left" in the dashboard. | Every HOLD / REDUCE / EXIT assignment |

## Quick Violation Checklist

Before finalising any recommendation, confirm none of these apply:

- [ ] R1: Recommending BUY on stock in 3-month downtrend without base/beat?
- [ ] R2: Recommending EXIT on structural macro theme within 5 days of entry?
- [ ] R3: Recommending leveraged ETF with VIX ≥ 18?
- [ ] R4: Recommending 3rd entry in same stock where 2nd underperformed by >50%?
- [ ] R5: Recommending ADD on P/E >40x stock at extended levels?
- [ ] R6: New BUY recommendation missing a hard stop price?
- [ ] R7: Cash + margin >40% of portfolio in RISK-ON and no new entries recommended?
- [ ] R8: Recommending multiple partial buys of same stock same day?
- [ ] R9: Recommending leveraged ETF re-entry within 30-day lockout window?
- [ ] R11: Recommending any new USD-denominated position?
- [ ] R12: Recommending EXIT on losing position without stop hit, binary event, or thesis reversal?
- [ ] R15: Quoting a price for a new recommendation that has not been verified via WebSearch?
- [ ] R15: Using a different price source for held positions instead of the user's screenshot?
- [ ] R16: Recommending a BUY/ADD where honest conviction is low — would you use your own money here?
- [ ] R17: Suggesting an exit purely because time has passed or position is up, without thesis breaking?

## Behavioral Patterns to Avoid (from historical trade analysis)

| Pattern | Example Outcome | Rule |
|---------|----------------|------|
| Sells macro themes too early | VanEck Defense sold after 3 days → +€241 instead of +€2,000+ | R2 |
| Catches falling knives | Adobe bought into 6-month downtrend → -€636 | R1 |
| Chases repeated names | Micron: 3rd entry → -€450 | R4 |
| Buys high-PE at peak | Eli Lilly at peak → -€575+ unrealised | R5 |
| Under-deploys cash in bull market | €35k+ margin idle during Jan–Mar rally → missed AMZN +6.6%, NVDA +6.8% | R7 |
| Re-enters leveraged ETF without signal | Amundi 2X LEV multiple re-entries → flat net | R9 |

## Best Patterns to Replicate

| Pattern | Result |
|---------|--------|
| ASML: 3 clean technical entries at support | +€879 total, consistent |
| Netflix: one entry, one exit | +€735 |
| Single correct-sized position from the start | Minimal friction |
