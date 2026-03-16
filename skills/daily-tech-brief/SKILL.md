---
name: daily-tech-brief
description: 'Fetches and summarizes the top 10 tech news stories of the day, curated for software developers. Use when asked for a "daily tech brief", "tech news", "what happened in tech today", "top tech stories", "morning tech roundup", or any request for current technology headlines, developer news, or software industry updates. Covers AI/ML, security, open source, cloud, DevOps, programming languages, and developer tools. Sources aggregators first (Hacker News, Techmeme, lobste.rs) then primary outlets (Ars Technica, The Register, The New Stack, GitHub Blog) for deep developer coverage. Outputs formatted text directly in the conversation.'
---

# Daily Tech Brief

Fetches the top 10 technology news stories of the day from across the web, curated specifically for software developers, and outputs them as formatted text directly in the conversation.

## When to Use This Skill

- User says "daily tech brief", "tech brief", or "morning roundup"
- User asks "what happened in tech today?" or "what's the top tech news?"
- User wants a developer-focused news digest
- User asks for top stories from Hacker News, Techmeme, Ars Technica, The Register, etc.

## Sources to Fetch From

Fetch in passes — **aggregators first**, then primary outlets. This surfaces what's actually trending today rather than defaulting to the same homepages every run.

### Pass 1 — Aggregators (Always Fetch First)

| Source | URL | Best For |
|--------|-----|----------|
| Hacker News | https://news.ycombinator.com/ | Community-ranked developer picks; open source, tools, security. **Fetch as HTML** — RSS omits vote counts needed for trending filter. |
| Techmeme | https://www.techmeme.com/feed.xml | Algorithm + human editors; most-linked tech stories of the day. **Filter out any item that appears to be a paid placement** (sponsor entries appear inline in the RSS feed). |
| lobste.rs | https://lobste.rs/rss | Developer-curated; programming languages, tools, open source |

### Pass 2 — Primary Outlets (Deep Developer Coverage)

| Source | URL | Best For |
|--------|-----|----------|
| Ars Technica | https://feeds.arstechnica.com/arstechnica/technology-lab | Deep technical coverage — AI, security, software, science |
| The Register | https://www.theregister.com/headlines.atom | Enterprise tech, security, infrastructure, UK/EU policy |
| The New Stack | https://thenewstack.io/feed/ | DevOps, Kubernetes, cloud-native, microservices |
| GitHub Blog | https://github.blog/feed/ | Platform updates, open source releases, security advisories |

### Pass 3 — Secondary Sources (Fetch When Needed for Breadth)

| Source | URL | Best For |
|--------|-----|----------|
| Krebs on Security | https://krebsonsecurity.com/feed/ | Cybersecurity and cybercrime |
| InfoQ | https://feed.infoq.com/ | Software architecture, AI tooling, enterprise dev |
| Stack Overflow Blog | https://stackoverflow.blog/feed/ | Developer community insights, AI/ML tools, engineering practices |
| TechCrunch | https://techcrunch.com/feed/ | Startups, funding, industry moves |
| MIT Technology Review | https://www.technologyreview.com/feed/ | AI/ML research, emerging tech (often paywalled — use headlines only) |

## Step-by-Step Workflow

### Step 1: Fetch Aggregators First

Use the `web_fetch` tool to load **all three aggregators simultaneously**. These surface what's actually trending *today* without guessing which outlets are hot:

| Aggregator | URL |
|------------|-----|
| Hacker News | https://news.ycombinator.com/ |
| Techmeme | https://www.techmeme.com/feed.xml |
| lobste.rs | https://lobste.rs/rss |

From these results, collect headlines and links generating the most attention — this is your initial candidate pool. For Techmeme, filter out any items that appear to be paid placements (sponsor entries appear as regular items in the RSS feed — skip anything that reads as an advertisement rather than editorial coverage).

### Step 2: Broaden with Primary Outlets

Fetch **primary outlets in parallel** to catch important developer stories aggregators may have missed. All primary outlets now have RSS/Atom feeds for clean structured data:

- Ars Technica Technology Lab RSS: `https://feeds.arstechnica.com/arstechnica/technology-lab`
- The Register Atom: `https://www.theregister.com/headlines.atom`
- The New Stack RSS: `https://thenewstack.io/feed/`
- GitHub Blog RSS: `https://github.blog/feed/`

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

### Step 6: Output as Formatted Text

Write the brief directly in your response using this structure:

```
## Daily Tech Brief — {DATE}
*Curated for software developers*

---

**1. {HEADLINE}**
*{SOURCE_NAME}* — {ARTICLE_URL}

{PARAGRAPH_1}

{PARAGRAPH_2}

---

**2. {HEADLINE}**
...
```

Continue for all 10 stories. End with a one-line footer listing the sources consulted.

## Output Requirements

- Plain text using markdown formatting — no HTML, no files, no browser
- Each story must include: headline (bold), source name (italic), direct article link, 2-paragraph summary
- Stories numbered 1–10, separated by `---`
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

- Source priority guide: `references/sources.md`
