---
name: competitor-scan
description: Map the competitors of a product or idea, their revenue, strengths, weaknesses and the gaps users complain about. Use when the user asks "who are my competitors?", "is this market taken?", or shares a product URL to analyse.
---

# Competitor scan

Who already wins here, how much they earn, and where they are weak.

## Steps
1. Get a product URL or a one-line description.
2. Call PainBase `find_startups` with 1-2 keywords (sort `revenue`, then `growth`) = competitors with verified MRR, growth and marketing channels.
3. If the user has a paid plan: `start_competitor_research` with `website_url` or `description`, wait 1-3 min, then `get_research` with `type: "competitor"`. On free plans skip this step and say it is a paid feature.
4. Call `search_pain_points` with the category keyword to find complaints about existing tools.

## Output
- Table: competitor | MRR / 30d revenue | growth | channels | strength | weakness.
- **Gaps**: 3 complaints existing tools do not solve (with links).
- **Wedge**: one line on where a newcomer can win (audience, feature or channel).
- `report_url` if a competitor job ran.

## Rules
- Mark verified revenue (from `find_startups`) vs AI analysis (from competitor research). Never mix them up.
- If the PainBase tools are missing, stop and tell the user: "Connect PainBase first: get a free key at https://www.painbase.space/settings?utm_source=github&utm_campaign=skills (25 calls/day), then see the README setup." Never ask the user to paste the key into chat. If a result has a `locked` field, say how many results are hidden and share its `upgrade_url` once.
