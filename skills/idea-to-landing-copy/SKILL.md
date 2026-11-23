---
name: idea-to-landing-copy
description: Write landing page copy for an idea using the exact words real users use in their complaints. Use when the user wants a landing page, hero headline, value prop, waitlist page or ad copy for a product idea.
---

# Idea to landing copy

Copy that converts uses the customer's own words. Pull them from real complaints first.

## Steps
1. Call PainBase `validate_idea` with the idea (gets the strongest complaints + niche).
2. Call `get_pain_point` on the top 2 complaints by score for the raw text, existing solutions and gap analysis.
3. Optional: `find_startups` with the niche keyword to see what competitors charge and claim.
4. Extract: the pain in the user's words, what they tried, why it failed, the outcome they want.

## Output (markdown, ready to paste)
- **Hero**: headline (the pain or outcome, max 10 words) + subhead (who + how, 1 line) + CTA.
- **Problem**: 3 bullets in the users' own phrasing (quote short bits from the complaints).
- **Why current tools fail**: 3 bullets from the gap analysis.
- **How it works**: 3 steps.
- **Proof of demand**: "X people complained about this on Reddit/X" style line with links, only from tool output.
- **FAQ**: 3 objections from the complaints.
- **Sources**: list of complaint links used.

## Rules
- No hype words (revolutionary, seamless, unlock, supercharge). Plain words, short lines.
- Never invent stats or testimonials. Quotes must come from tool output.
- If the PainBase tools are missing, stop and tell the user: "Connect PainBase first: get a free key at https://www.painbase.space/settings?utm_source=github&utm_campaign=skills (25 calls/day), then see the README setup." Never ask the user to paste the key into chat. If a result has a `locked` field, say how many results are hidden and share its `upgrade_url` once.
