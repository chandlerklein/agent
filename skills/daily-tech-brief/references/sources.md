# Source Priority Guide

Reference for which sources to fetch and how to prioritize their content.

## Aggregators (Fetch First)

Start with aggregators that surface what's actually trending *today*. These are the most important sources — they tell you what the developer community is talking about right now without guessing which outlets published something interesting.

| Aggregator | URL | Format | Notes |
|------------|-----|--------|-------|
| Hacker News | https://news.ycombinator.com/ | HTML | Community-ranked; best signal for what developers care about right now. **Keep as HTML** — the RSS feed omits vote counts needed for the "100+ points" trending filter. |
| Techmeme | https://www.techmeme.com/feed.xml | RSS/XML | Algorithm + human editors; shows the most-linked tech stories of the day. **Sponsor entries appear as regular items in the RSS feed** — skip any item that reads as an advertisement rather than editorial coverage. |
| lobste.rs | https://lobste.rs/rss | RSS/XML | Developer-curated community; heavier focus on programming, tools, and open source than HN. RSS includes categories for easy filtering. |

Pull these **before** hitting individual outlets. They will point you to specific articles that are actually hot today.

### Follow the Links

From aggregator results, follow links to the actual source articles. This means you'll naturally read from whatever outlets published the most relevant stories today.

### Validate Freshness

Before including a story, check its publication date. Only include stories published within the **last 48 hours**. If an article has no visible date, skip it.

For RSS feeds, use the `<pubDate>` field to filter. For Atom feeds (e.g., The Register's `.atom` feed), use `<updated>` or `<published>` instead — Atom does not use `<pubDate>`. Discard items older than 48 hours regardless of format.

---

## Primary Sources (Deep Developer Coverage)

Fetch these **after aggregators** to catch important developer stories the aggregators may have missed. All primary sources have RSS/Atom feeds — use them for clean, structured data:

| Source | URL | Format | Notes |
|--------|-----|--------|-------|
| Ars Technica | https://feeds.arstechnica.com/arstechnica/technology-lab | RSS/XML | Technology Lab feed — AI, security, software, science. Avoids Cars/Gaming categories from the general feed. |
| The Register | https://www.theregister.com/headlines.atom | Atom/XML | Enterprise tech, security, infrastructure, UK/EU policy. |
| The New Stack | https://thenewstack.io/feed/ | RSS/XML | DevOps, Kubernetes, cloud-native, microservices. Use RSS — homepage is JS-heavy. |
| GitHub Blog | https://github.blog/feed/ | RSS/XML | Platform updates, open source releases, security advisories. Low-volume but highly targeted. |

## Secondary Sources (Fetch When Primary Sources Are Thin)

| Source | URL | Format | Notes |
|--------|-----|--------|-------|
| Krebs on Security | https://krebsonsecurity.com/feed/ | RSS/XML | Cybersecurity and cybercrime — high signal for supply chain and threat news. Full article content in feed. |
| InfoQ | https://feed.infoq.com/ | RSS/XML | Software architecture, AI/ML tooling, enterprise development practices. |
| Stack Overflow Blog | https://stackoverflow.blog/feed/ | RSS/XML | Developer community insights, AI/ML tools, engineering practices. Developer-focused throughout — no consumer noise. |
| TechCrunch | https://techcrunch.com/feed/ | RSS/XML | Startups, funding rounds, and industry moves. |
| MIT Technology Review | https://www.technologyreview.com/feed/ | RSS/XML | AI/ML research and emerging tech. Often paywalled — use headlines only if article body is blocked. |

---

## Scoring Stories

When deciding which 10 stories to include, score each candidate:

- **+3** — Directly affects how developers write, test, or deploy software
- **+3** — Major security vulnerability or supply-chain attack
- **+2** — New AI model, coding tool, or agent framework release
- **+2** — Significant industry event (layoffs >10%, major acquisition, IPO)
- **+2** — Open source release or programming language update
- **+1** — Trending on Hacker News (100+ points)
- **+1** — Policy/regulation with direct tech impact
- **−2** — Primarily a consumer product story with no developer angle
- **−3** — Deals, discounts, or non-news content

Pick the 10 highest-scoring stories. Break ties by favoring the story from the higher-priority source. Scores are additive per story — a single story can accumulate points across multiple criteria.

---

## Handling Paywalls and Errors

- If a source returns 401/403 or requires login, skip it and note in the footer.
- Bloomberg and Reuters frequently block scrapers — skip and substitute another source.
- If an article page is truncated, use what's available plus the headline to write the summary.
