---
name: daily-tech-brief
description: 'Fetches and summarizes the top 10 tech news stories of the day, curated for software developers. Use when asked for a "daily tech brief", "tech news", "what happened in tech today", "top tech stories", "morning tech roundup", or any request for current technology headlines, developer news, or software industry updates. Covers AI/ML, security, open source, cloud, programming languages, developer tools, and industry news from sources like Hacker News, Techmeme, Lobste.rs, The Verge, Ars Technica, Wired, The New Stack, GitHub Blog, MIT Technology Review, TechCrunch, and more. Outputs an HTML page opened in Chrome.'
---

# Daily Tech Brief

Fetches the top 10 technology news stories of the day from across the web, curated specifically for software developers, and presents them as a clean, readable HTML page opened directly in the user's browser.

## When to Use This Skill

- User says "daily tech brief", "tech brief", or "morning roundup"
- User asks "what happened in tech today?" or "what's the top tech news?"
- User wants a developer-focused news digest
- User asks for top stories from Hacker News, The Verge, Ars Technica, Wired, etc.
- User wants tech news as an HTML page or in the browser

## Sources to Fetch From

Start with aggregators, then fill gaps with primary sources. Full priority guide in `references/sources.md`.

| Source | URL | Best For |
|--------|-----|----------|
| Hacker News | https://news.ycombinator.com/ | Developer community picks, open source, security |
| Techmeme | https://www.techmeme.com/ | Most-linked tech stories of the day |
| Lobste.rs | https://lobste.rs/ | Developer-focused: languages, open source, security |
| The New Stack | https://thenewstack.io/ | Cloud-native, Kubernetes, DevOps |
| GitHub Blog | https://github.blog/ | GitHub, Actions, Copilot, open-source news |
| Ars Technica | https://feeds.arstechnica.com/arstechnica/index (RSS) | Deep technical coverage, science, policy |
| The Verge | https://www.theverge.com/tech | Consumer tech, industry news, product launches |
| Wired | https://www.wired.com/ | Security, culture, policy, in-depth features |
| MIT Technology Review | https://www.technologyreview.com/ | Research, emerging tech, energy, AI |
| TechCrunch | https://techcrunch.com/ | Startups, funding, industry moves |
| The Register | https://www.theregister.com/ | Enterprise tech, security, UK/EU policy |
| Krebs on Security | https://krebsonsecurity.com/ | Security and cybercrime |

## Step-by-Step Workflow

### Step 1: Fetch Aggregators First

Start with the aggregators — they surface what's actually trending **today**, not just what sources you already know about. Fetch all three simultaneously:

- **Hacker News** (`https://news.ycombinator.com/`) — community-ranked; reflects what developers care about right now
- **Techmeme** (`https://www.techmeme.com/`) — algorithm + human editors; shows the most-linked stories of the day
- **Lobste.rs** (`https://lobste.rs/`) — developer-focused aggregator with topic tags; great for open source, languages, and security

From these, identify ~15 strong candidate stories. Note which primary sources the aggregators are linking to — these are your high-signal targets for Step 2.

Then, to fill any coverage gaps, fetch primary sources in parallel using RSS feeds where available (Ars Technica, TechCrunch, The Register) since they return clean structured content. See `references/sources.md` for the full list.

### Step 2: Fetch Article Detail for Top Candidates

From the headlines gathered, identify ~15 strong candidates. For the most promising stories, fetch the article page for additional detail. **Note:** if the headline and visible lead paragraph on the index page give you enough to write a good summary, you do not need to fetch the full article — this keeps execution fast.

If `web_fetch` fails for a source (4xx, timeout, paywall), skip it and note it in the footer. Prioritize:

- **Developer relevance**: tools, languages, frameworks, APIs, open source
- **Security**: vulnerabilities, supply chain attacks, surveillance policy
- **AI/ML**: model releases, research, product launches, policy
- **Industry**: layoffs, acquisitions, regulatory actions, major product changes
- **Freshness**: prefer stories from the current day or previous 24 hours

Avoid:
- Deals/sales roundups unless the product is developer-relevant
- Celebrity or non-tech news
- Opinion pieces without a newsworthy hook

### Step 3: Select the Top 10

Choose 10 stories that collectively span multiple categories. Aim for variety:
- At least 2 AI/ML stories
- At least 1 security or privacy story
- At least 1 developer tools / open source story
- Remaining from industry, hardware, policy, or research

### Step 4: Write Summaries

For each story write **1–2 short paragraphs** (~3–5 sentences each):
- **Paragraph 1**: What happened and why it matters
- **Paragraph 2**: Context, implications, or developer-relevant detail

### Step 5: Generate and Open HTML

Create the HTML file at `/tmp/daily-tech-brief-YYYY-MM-DD.html` using the template in `references/html-template.md`. Then open it in Chrome:

```bash
open -a "Google Chrome" /tmp/daily-tech-brief-YYYY-MM-DD.html
```

## Output Requirements

- Barebones, readable HTML — minimal CSS, no heavy frameworks
- Each story must include: headline, source name, direct article link, 1–2 paragraph summary
- Stories numbered 1–10
- Header shows today's date
- Footer lists all sources consulted

## Story Selection Criteria (Ranked)

1. **Developer impact** — directly affects how developers work, build, or deploy
2. **Security** — threats, breaches, or policy affecting software supply chains
3. **AI tooling** — new models, coding assistants, agent frameworks
4. **Industry signal** — major layoffs, acquisitions, or pivots at large tech companies
5. **Open source / standards** — notable releases, RFCs, language changes
6. **Policy / regulation** — laws or rulings that affect software, privacy, or the internet

## References

- HTML output template: `references/html-template.md`
- Source priority guide: `references/sources.md`
