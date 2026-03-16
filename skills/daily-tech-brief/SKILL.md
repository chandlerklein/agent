---
name: daily-tech-brief
description: 'Fetches and summarizes the top 10 tech news stories of the day, curated for software developers. Use when asked for a "daily tech brief", "tech news", "what happened in tech today", "top tech stories", "morning tech roundup", or any request for current technology headlines, developer news, or software industry updates. Covers AI/ML, security, open source, cloud, DevOps, programming languages, and developer tools. Sources aggregators first (Hacker News, Techmeme, lobste.rs, Google News) then primary outlets (Ars Technica, The Register, The New Stack, GitHub Blog) for deep developer coverage. Outputs an HTML page opened in the browser.'
---

# Daily Tech Brief

Fetches the top 10 technology news stories of the day from across the web, curated specifically for software developers, and presents them as a clean, readable HTML page opened directly in the user's browser.

## When to Use This Skill

- User says "daily tech brief", "tech brief", or "morning roundup"
- User asks "what happened in tech today?" or "what's the top tech news?"
- User wants a developer-focused news digest
- User asks for top stories from Hacker News, Techmeme, Ars Technica, The Register, etc.
- User wants tech news as an HTML page or in the browser

## Sources to Fetch From

Fetch in two passes. **Aggregators first**, then primary outlets. This ensures you surface what's actually trending today rather than defaulting to the same homepages every run.

### Pass 1 — Aggregators (Always Fetch First)

| Source | URL | Best For |
|--------|-----|----------|
| Hacker News | https://news.ycombinator.com/ | Community-ranked developer picks; open source, tools, security |
| Techmeme | https://www.techmeme.com/ | Algorithm + human editors; most-linked tech stories of the day |
| lobste.rs | https://lobste.rs/ | Developer-curated; programming languages, tools, open source |
| Google News – Technology | https://news.google.com/topics/CAAqJggKIiBDQkFTRWdvSUwyMHZNRGRqTVhZU0FtVnVHZ0pWVXlBQVAB | Broad real-time index across hundreds of outlets |

### Pass 2 — Primary Outlets (Deep Developer Coverage)

| Source | URL | Best For |
|--------|-----|----------|
| Ars Technica | https://feeds.arstechnica.com/arstechnica/index (RSS) | Deep technical coverage, science, security, policy |
| The Register | https://www.theregister.com/ | Enterprise tech, security, infrastructure |
| The New Stack | https://thenewstack.io/ | DevOps, Kubernetes, cloud-native, microservices |
| GitHub Blog | https://github.blog/ | Platform updates, open source releases, security advisories |

### Pass 3 — Secondary Sources (Fetch When Needed for Breadth)

| Source | URL | Best For |
|--------|-----|----------|
| Krebs on Security | https://krebsonsecurity.com/ | Cybersecurity and cybercrime |
| InfoQ | https://www.infoq.com/ | Software architecture, AI tooling, enterprise dev |
| Wired | https://www.wired.com/ | Security policy, in-depth features |
| TechCrunch | https://techcrunch.com/ | Startups, funding, industry moves |
| MIT Technology Review | https://www.technologyreview.com/ | AI/ML research, emerging tech |

## Step-by-Step Workflow

### Step 1: Fetch Aggregators First

Use the `web_fetch` tool to load **all four aggregators simultaneously** in a single response. These surface what's actually trending *today* without you having to guess which outlets published strong stories:

| Aggregator | URL |
|------------|-----|
| Hacker News | https://news.ycombinator.com/ |
| Techmeme | https://www.techmeme.com/ |
| lobste.rs | https://lobste.rs/ |
| Google News – Technology | https://news.google.com/topics/CAAqJggKIiBDQkFTRWdvSUwyMHZNRGRqTVhZU0FtVnVHZ0pWVXlBQVAB |

From these results, collect the headlines and links that are generating the most attention. This becomes your initial candidate pool.

### Step 2: Broaden with Primary Outlets

Fetch **primary outlets in parallel** to catch important developer stories that aggregators may have missed. Use RSS where available (e.g., Ars Technica) for clean structured data:

- Ars Technica RSS: `https://feeds.arstechnica.com/arstechnica/index`
- The Register: `https://www.theregister.com/`
- The New Stack: `https://thenewstack.io/`
- GitHub Blog: `https://github.blog/`

### Step 3: Fetch Article Detail for Top Candidates

From the headlines gathered, identify ~15 strong candidates. For the most promising stories, fetch the article page to get enough detail to write a 2-paragraph summary. Prioritize:

- **Developer relevance**: tools, languages, frameworks, APIs, open source
- **Security**: vulnerabilities, supply chain attacks, surveillance policy
- **AI/ML**: model releases, research, product launches, policy
- **Industry**: layoffs, acquisitions, regulatory actions, major product changes
- **Freshness**: prefer stories from the current day or previous 24 hours

Avoid:
- Deals/sales roundups unless the product is developer-relevant
- Celebrity or non-tech news
- Opinion pieces without a newsworthy hook

### Step 4: Select the Top 10

Choose 10 stories that collectively span multiple categories. Aim for variety:
- At least 2 AI/ML stories
- At least 1 security or privacy story
- At least 1 developer tools / open source story
- Remaining from industry, hardware, policy, or research

### Step 5: Write Summaries

For each story write **2 short paragraphs** (~3–5 sentences each):
- **Paragraph 1**: What happened and why it matters
- **Paragraph 2**: Context, implications, or developer-relevant detail

### Step 6: Generate and Open HTML

Create the HTML file at `/tmp/daily-tech-brief-YYYY-MM-DD.html` using the template in `references/html-template.md`. Then open it with:

```bash
open /tmp/daily-tech-brief-YYYY-MM-DD.html
```

## Output Requirements

- Barebones, readable HTML — minimal CSS, no heavy frameworks
- Each story must include: headline, source name, direct article link, 2-paragraph summary
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
