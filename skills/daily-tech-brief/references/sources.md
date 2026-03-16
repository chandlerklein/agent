# Source Priority Guide

Reference for which sources to fetch and how to prioritize their content.

## Aggregators (Fetch First)

Start with aggregators that surface what's actually trending *today*. These are the most important sources — they tell you what the developer community and broader tech industry are talking about right now, without you having to guess which outlets published something interesting.

| Aggregator | URL | Notes |
|------------|-----|-------|
| Hacker News | https://news.ycombinator.com/ | Community-ranked; best signal for what developers care about right now |
| Techmeme | https://www.techmeme.com/ | Algorithm + human editors; shows the most-linked tech stories of the day |
| lobste.rs | https://lobste.rs/ | Developer-curated community; heavier focus on programming, tools, and open source than HN |
| Google News – Technology | https://news.google.com/topics/CAAqJggKIiBDQkFTRWdvSUwyMHZNRGRqTVhZU0FtVnVHZ0pWVXlBQVAB | Broad real-time index across hundreds of outlets |

Pull these **before** hitting individual outlets. They will point you to specific articles that are actually hot today, which changes daily.

### Follow the Links

From aggregator results, follow links to the actual source articles. This means you'll naturally read from whatever outlets published the most relevant stories today.

### Validate Freshness

Before including a story, check its publication date. Only include stories published within the **last 48 hours**. If an article has no visible date, skip it.

For RSS feeds (e.g., Ars Technica), use the `<pubDate>` field to filter. Discard items older than 48 hours.

---

## Primary Sources (Deep Developer Coverage)

Fetch these **after aggregators** to broaden coverage and catch important developer stories the aggregators may have missed. These outlets publish high-quality technical content daily:

| Source | URL | Format | Notes |
|--------|-----|--------|-------|
| Ars Technica | https://feeds.arstechnica.com/arstechnica/index | RSS/XML | Use RSS for clean structured data. Deep technical coverage: AI, security, science, policy. |
| The Register | https://www.theregister.com/ | HTML | Enterprise tech, security, infrastructure, UK/EU policy. |
| The New Stack | https://thenewstack.io/ | HTML | DevOps, Kubernetes, cloud-native, microservices — excellent for infrastructure developers. |
| GitHub Blog | https://github.blog/ | HTML | Platform updates, open source releases, security advisories directly from GitHub. |

## Secondary Sources (Fetch When Primary Sources Are Thin)

Fetch these to broaden coverage, especially if primary sources are sparse on a given day:

| Source | URL | Format | Notes |
|--------|-----|--------|-------|
| Krebs on Security | https://krebsonsecurity.com/ | HTML | Cybersecurity and cybercrime — high signal for supply chain and threat news. |
| InfoQ | https://www.infoq.com/ | HTML | Software architecture, AI/ML tooling, enterprise development practices. |
| Wired | https://www.wired.com/ | HTML | Security policy and in-depth features with a tech/society angle. |
| TechCrunch | https://techcrunch.com/ | HTML | Startups, funding rounds, and industry moves. |
| MIT Technology Review | https://www.technologyreview.com/ | HTML | AI/ML research, emerging tech, energy. |

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

Pick the 10 highest-scoring stories. Break ties by favoring the story from the higher-priority source.

---

## Handling Paywalls and Errors

- If a source returns 401/403 or requires login, skip it and note in the footer.
- Bloomberg and Reuters frequently block scrapers — skip and substitute another source.
- If an article page is truncated, use what's available plus the headline to write the summary.
