# PainBase Skills

**Validate startup ideas inside Claude Code and Cursor, with real complaints and verified revenue instead of vibes.**

5 agent skills that call the [PainBase](https://www.painbase.space/?utm_source=github&utm_campaign=skills) MCP:
AI-scored complaints from Reddit, Hacker News, X, Dev.to, Lobsters, Indie Hackers + verified 30-day revenue for 2,500+ startups.

Free key = 25 calls/day. No credit card.

| Skill | Ask your agent | Uses |
|---|---|---|
| `validate-idea` | "Is an invoicing app for freelance designers worth building?" | `validate_idea`, `find_startups` |
| `find-market` | "What niche should I build in? Solo-founder size." | `find_markets`, `find_startups`, `search_pain_points` |
| `find-pain-points` | "What do Shopify sellers hate about inventory tools?" | `search_pain_points`, `get_pain_point` |
| `competitor-scan` | "Who are the competitors of ezybills.app?" | `find_startups`, `start_competitor_research`*, `search_pain_points` |
| `idea-to-landing-copy` | "Write a landing page for a payment-chasing tool for freelancers" | `validate_idea`, `get_pain_point` |

\* paid plans only; the skill falls back to free tools.

## 1. Get a key (1 min)

[painbase.space/settings](https://www.painbase.space/settings?utm_source=github&utm_campaign=skills) → **Create API key** (`pb_live_...`). Keep it private, never commit it.

## 2. Install

### Claude Code (plugin: skills + MCP in one go)

```bash
export PAINBASE_API_KEY=pb_live_YOUR_KEY   # add to ~/.zshrc or ~/.bashrc
```
Then inside Claude Code:
```
/plugin marketplace add P-Tung/painbase-skills
/plugin install painbase-skills@painbase-skills
```
The plugin reads `PAINBASE_API_KEY` from your environment. Restart Claude Code after setting it.

### Claude Code (skills only, MCP by hand)

```bash
git clone https://github.com/P-Tung/painbase-skills && cp -r painbase-skills/skills/* ~/.claude/skills/
claude mcp add --transport http painbase https://www.painbase.space/api/mcp \
  --header "Authorization: Bearer pb_live_YOUR_KEY"
```

### Cursor

```bash
git clone https://github.com/P-Tung/painbase-skills && mkdir -p ~/.cursor/skills && cp -r painbase-skills/skills/* ~/.cursor/skills/
```
MCP in `~/.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "painbase": {
      "url": "https://www.painbase.space/api/mcp",
      "headers": { "Authorization": "Bearer pb_live_YOUR_KEY" }
    }
  }
}
```

### Any other agent (Codex, Gemini CLI, Windsurf...)

```bash
npx skills add P-Tung/painbase-skills
```
Then add the MCP with an `Authorization: Bearer pb_live_YOUR_KEY` header to `https://www.painbase.space/api/mcp`.

## 3. Example outputs (real, from the MCP, 2026-11-23)

### `validate-idea`: "invoicing app for freelance designers"
- **Verdict: Some demand.** 7 complaints, 7 threads, avg score 39/100. Real pain, not loud. Narrow it.
- Top complaints:
  - "No response to invoice causes severe cash flow anxiety" (X, severity 5, score 66)
  - "Both parties forgetting invoices leads to long delays" (X, severity 4, score 54)
  - "Wasting too much time manually tracking hours across tools and writing invoices" (X, severity 4)
- **Sharper angle** (from `find-pain-points`): payment *chasing*, not invoice *creation*:
  - "Chasing up money is the worst part of freelance" (r/freelanceWriters, **score 84/100**, severity 5)
  - "The real pain isn't creating invoices, it's following up on unpaid invoices" (X, score 68)

### `find-market`: winnable markets, side-project size ($1-20k/mo)
| Market | Competitors | 30d verified revenue | Median growth | Leader share |
|---|---|---|---|---|
| AI for Business Operations & Productivity | 15 | $16.2k | +5.0% | 18% (wide open) |
| AI Image & Graphic Generation | 11 | $6.7k | -15.3% | 20% (wide open) |
| AI Tool Aggregators & General Platforms | 11 | $3.8k | 0% | 19% (wide open) |
| AI Developer Tools & Agent Infrastructure | 12 | $1.4k | 0% | 13% (wide open) |

### `find-pain-points`: "shopify inventory"
- "Medium Shopify businesses struggle to find integrated inventory + CRM that handles POs, stock and orders with reliable support" (r/smallbusinessuk, score 55)
- Gap: tools either lack features or have poor support.

### `competitor-scan`: ezybills.app (AI invoice generator)
| Competitor | Verified revenue | Weakness users hit |
|---|---|---|
| ezybills | $959 last 30d | new (Sep 2026), no channels listed |
| pdfs.build | $205 MRR, +3,286% 30d growth | dev-focused (PDF pipelines), SEO + blog |
| FreshBooks | (AI analysis) | overkill + pricey for "just send an invoice" |
| Invoice Simple | (AI analysis) | no AI parsing from text/photos |
- **Wedge:** nobody owns *getting paid* (follow-ups, escalation). Complaints score 68-84 on chasing vs ~30 on invoice design.

### `idea-to-landing-copy`: payment-chasing tool for freelancers
> **Stop chasing clients for money.**
> Automatic, polite follow-ups that get freelancers paid, without the awkward emails.
> - "Chasing up money is the worst part of freelance."
> - "It takes so much time and energy to keep following up."
> - Reminder tools exist, but they don't reduce the time or the awkwardness.

## Why skills + MCP?

The MCP gives your agent the data. The skills give it the method: which tools to call, in what order, how to cite evidence, and what to say when the signal is weak. Fork them and make your own.

## More

- Full web app, deep research reports, market feed: **[painbase.space](https://www.painbase.space/?utm_source=github&utm_campaign=skills)**
- MCP docs: [painbase.space/mcp](https://www.painbase.space/mcp?utm_source=github&utm_campaign=skills)

MIT licensed. PRs welcome: new skills, better prompts, more agents.
