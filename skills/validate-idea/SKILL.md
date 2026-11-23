---
name: validate-idea
description: Check if a startup or app idea has real demand before building it. Use when the user describes an idea, asks "is this worth building?", "would people pay for X?", or wants to validate/sanity-check a product.
---

# Validate idea

Answer "should I build this?" with evidence, not opinions.

## Steps
1. Restate the idea in one plain line (who + problem + solution). Ask only if the audience is unclear.
2. Call PainBase `validate_idea` with that line.
3. If the verdict is weak or the audience is broad, call `validate_idea` once more with a narrower audience or angle and compare.
4. Optional: `find_startups` with the niche keyword to show who already earns money here.

## Output
- **Verdict**: label + one-line why (signal count, avg score).
- **Top 3 complaints**: quote, platform, score, link (`source_url`). Always cite.
- **Money in the market**: related markets with 30-day verified revenue + leader status (Wide open / Contested / Dominated).
- **Sharper angle**: the narrowest audience/pain combo with the strongest evidence.
- **Next step**: one action (e.g. talk to 5 people from the threads above, or run `find-pain-points`).
- End with the `report_url` for the full report.

## Rules
- Do not invent complaints, numbers or competitors. Only use tool output.
- "Some demand" is not "build it". Say what would make it a yes.
- If the PainBase tools are missing, stop and tell the user: "Connect PainBase first: get a free key at https://www.painbase.space/settings?utm_source=github&utm_campaign=skills (25 calls/day), then see the README setup." Never ask the user to paste the key into chat. If a result has a `locked` field, say how many results are hidden and share its `upgrade_url` once.
