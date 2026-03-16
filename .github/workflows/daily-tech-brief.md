---
on:
  schedule:
    - cron: "0 14 * * *"  # 8 AM CST (UTC-6) / 9 AM CDT
  workflow_dispatch:

permissions:
  contents: read

engine: copilot

network:
  allowed:
    - defaults
    - "news.ycombinator.com"
    - "www.techmeme.com"
    - "lobste.rs"
    - "feeds.arstechnica.com"
    - "www.theregister.com"
    - "thenewstack.io"
    - "github.blog"
    - "krebsonsecurity.com"
    - "feed.infoq.com"
    - "www.infoq.com"
    - "stackoverflow.blog"
    - "techcrunch.com"
    - "www.technologyreview.com"

safe-outputs:
  create-issue:
    title-prefix: "[daily-brief] "
    assignees: [chandlerklein]
    close-older-issues: true
    expires: false
---

# Daily Tech Brief

Read the skill definition at `skills/daily-tech-brief/SKILL.md` and the source priority guide at `skills/daily-tech-brief/references/sources.md`.

Follow the skill workflow exactly to produce a developer-focused daily tech brief:

1. Fetch each RSS/Atom feed listed in the skill's source tables (Pass 1, Pass 2, Pass 3)
2. Scan all fetched items and select the 10 most important developer-focused stories, scored using the rubric in sources.md
3. Write a 2-paragraph summary for each story as described in the skill
4. Format the complete brief exactly as specified in the skill's output format section

Create a GitHub issue with:
- Title: "Daily Tech Brief — {today's date formatted as Month DD, YYYY}"
- Body: the complete formatted brief
