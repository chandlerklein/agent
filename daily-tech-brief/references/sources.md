# Source Priority Guide

Reference for which sources to fetch and how to prioritize their content.

## Source Discovery (Preventing Stale Coverage)

**Do not rely solely on the static source list below.** Publication schedules vary — some sources may have few fresh articles on a given day. Use the following discovery approach on every run:

### Step 1: Check News Aggregators First

Start with aggregators that surface what's actually trending *today*, rather than always hitting the same homepages:

| Aggregator | URL | Notes |
|------------|-----|-------|
| Hacker News front page | https://news.ycombinator.com/ | Community-ranked; reflects what developers care about right now |
| Google News – Technology | https://news.google.com/topics/CAAqJggKIiBDQkFTRWdvSUwyMHZNRGRqTVhZU0FtVnVHZ0pWVXlBQVAB | Broad real-time index across hundreds of outlets |
| Techmeme | https://www.techmeme.com/ | Algorithm + human editors; shows the most-linked tech stories of the day |

Pull these **first**. They will point you to specific outlets and articles that are actually hot today, not just outlets you've hardcoded.

### Step 2: Follow the Links

From aggregator results, follow the links to the actual source articles. This means you'll naturally end up reading from whatever outlets published the most relevant stories today — which changes daily.

### Step 3: Validate Freshness

Before including a story, check its publication date. Only include stories published within the **last 48 hours**. If an article has no visible date, skip it.

For RSS feeds (e.g., Ars Technica), use the `<pubDate>` field to filter. Discard items older than 48 hours.

---

## Primary Sources (Reliable Daily Coverage)

These sources publish tech news every day and are worth checking directly if the aggregators miss something:

| Source | URL | Format | Notes |
|--------|-----|--------|-------|
| Hacker News | https://news.ycombinator.com/ | HTML | Sort by points. Stories with 100+ points are strong candidates. |
| Ars Technica | https://feeds.arstechnica.com/arstechnica/index | RSS/XML | Use RSS for clean structured data. Filter to `AI`, `Tech`, `Security`, `Science` categories. |
| The Verge | https://www.theverge.com/tech | HTML | Tech section landing page. |
| Engadget | https://www.engadget.com/ | HTML | Good for consumer tech, AI product news, streaming. |

## Secondary Sources (Fetch When Possible)

Fetch these to broaden coverage, especially if primary sources are thin:

| Source | URL | Format | Notes |
|--------|-----|--------|-------|
| Wired | https://www.wired.com/ | HTML | Best for security, policy, and in-depth features. |
| MIT Technology Review | https://www.technologyreview.com/ | HTML | Research, AI, energy, and emerging tech. |
| TechCrunch | https://techcrunch.com/ | HTML | Startups, funding rounds, industry moves. |
| The Register | https://www.theregister.com/ | HTML | Enterprise, security, UK/EU policy. |
| 9to5Mac | https://9to5mac.com/ | HTML | Apple platform and developer news. |
| Krebs on Security | https://krebsonsecurity.com/ | HTML | Cybersecurity and cybercrime. |

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
