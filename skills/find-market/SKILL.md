---
name: find-market
description: Find a startup niche worth entering using verified startup revenue. Use when the user asks "what should I build?", "which niche?", "where is there money?", or wants winnable, growing or big markets.
---

# Find market

Rank niches by real revenue so the user picks a market, not a guess.

## Steps
1. Ask (max 2 questions, skip if known): target size (`side` $1-20k/mo, `solo` $20-250k, `funded` $250k+) and any topic keyword.
2. Call PainBase `find_markets` with `view: "winnable"` (default), plus `scale` and `query` if given.
3. Also call `view: "growing"` and compare. Markets in both lists = strongest picks.
4. For the top 2 markets: `find_startups` with a keyword from the market name to show real players + their channels.
5. For the #1 pick: `search_pain_points` with the market keyword to show what users still complain about.

## Output
Table: market | competitors | 30d verified revenue | median growth | leader share | leader status.
Then for the top pick:
- Who earns there (2-3 startups, MRR, marketing channels).
- 2-3 open complaints with links = where a new product can win.
- One-line recommendation.

## Rules
- "Wide open" (low leader share) beats "biggest" for a solo founder. Say so.
- Revenue numbers come only from tool output. Round them.
- If the PainBase tools are missing, stop and tell the user: "Connect PainBase first: get a free key at https://www.painbase.space/settings?utm_source=github&utm_campaign=skills (25 calls/day), then see the README setup." Never ask the user to paste the key into chat. If a result has a `locked` field, say how many results are hidden and share its `upgrade_url` once.
