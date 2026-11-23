---
name: find-pain-points
description: Find real, scored complaints from Reddit, Hacker News, X, Dev.to, Lobsters and Indie Hackers for a topic or audience. Use when the user wants problems to solve, customer pain, startup ideas from real complaints, or "what do <audience> hate about <tool>?"
---

# Find pain points

Surface what real people complain about, ranked by demand x severity.

## Steps
1. Turn the request into 1-3 short queries (audience + problem, e.g. "shopify inventory", "freelance invoice payment chasing").
2. Call PainBase `search_pain_points` for each (`limit: 10`, `min_severity: 3` unless the user wants everything).
3. For the top 2-3 results by score, call `get_pain_point` for full detail: existing solutions, gap analysis, urgency.
4. Optional: if results are thin, offer `start_deep_research` (crawls fresh complaints, takes a few minutes; poll `get_research`).

## Output
Table: pain | audience | severity /5 | score /100 | platform | link.
Then for the top 2-3:
- Why existing tools fail (gap analysis, 1 line).
- The product idea in one line.
- Who to talk to first (the thread link).

## Rules
- Cite every complaint with its `source_url`.
- Group duplicates, keep the highest score.
- If the PainBase tools are missing, stop and tell the user: "Connect PainBase first: get a free key at https://www.painbase.space/settings?utm_source=github&utm_campaign=skills (25 calls/day), then see the README setup." Never ask the user to paste the key into chat. If a result has a `locked` field, say how many results are hidden and share its `upgrade_url` once.
