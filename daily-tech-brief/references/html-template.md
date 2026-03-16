# HTML Output Template

Use this structure for the daily tech brief HTML output. Keep styling minimal and readable.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Daily Tech Brief — {DATE}</title>
  <style>
    body { font-family: Georgia, serif; max-width: 750px; margin: 40px auto; padding: 0 20px; line-height: 1.7; color: #222; }
    h1 { font-size: 1.5rem; border-bottom: 2px solid #222; padding-bottom: 8px; }
    .meta { color: #666; font-size: 0.85rem; margin-bottom: 30px; }
    h2 { font-size: 1.1rem; margin-top: 2em; margin-bottom: 4px; }
    .source { font-size: 0.8rem; color: #888; text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 6px; }
    p { margin: 0.5em 0 1em; }
    a { color: #1a0dab; }
    hr { border: none; border-top: 1px solid #ddd; margin: 2em 0; }
  </style>
</head>
<body>

<h1>Daily Tech Brief — {DATE}</h1>
<p class="meta">Curated for software developers &mdash; {SOURCE_LIST}</p>

<hr>

<!-- Repeat this block for each story -->
<h2>{N}. {HEADLINE}</h2>
<p class="source">{SOURCE_NAME} &mdash; <a href="{ARTICLE_URL}">Read full article</a></p>
<p>{PARAGRAPH_1}</p>
<p>{PARAGRAPH_2}</p>
<hr>
<!-- End story block -->

<p class="meta">Sources consulted: {SOURCE_LINKS}</p>

</body>
</html>
```

## Variables

| Variable | Description |
|----------|-------------|
| `{DATE}` | Full date, e.g. "March 16, 2026" |
| `{SOURCE_LIST}` | Comma-separated plain-text source names |
| `{N}` | Story number (1–10) |
| `{HEADLINE}` | Article headline, kept concise |
| `{SOURCE_NAME}` | Publication name, e.g. "Ars Technica" |
| `{ARTICLE_URL}` | Direct link to the article |
| `{PARAGRAPH_1}` | What happened and why it matters |
| `{PARAGRAPH_2}` | Context, implications, or developer-relevant detail |
| `{SOURCE_LINKS}` | Anchor tags for each source consulted |

## Output File Naming

Save to: `/tmp/daily-tech-brief-YYYY-MM-DD.html`

Example: `/tmp/daily-tech-brief-2026-03-16.html`
