# agent

A collection of resources for the [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli) agent — including skills, prompt templates, and reference materials.

## Contents

| Resource Type | Location | Description |
|---------------|----------|-------------|
| Skills | [`skills/`](skills/) | Custom behaviors that extend what the Copilot CLI agent can do |

## Skills

Skills are markdown prompt files that extend the Copilot CLI agent with specialized behaviors. Each skill lives in its own directory under `skills/` and includes a `SKILL.md` that tells the agent when and how to use it.

| Skill | Description |
|-------|-------------|
| [daily-tech-brief](skills/daily-tech-brief/) | Fetches and summarizes the top 10 tech news stories of the day, curated for software developers. Outputs a clean HTML page opened in the browser. |

### Using Skills

To load skills into the Copilot CLI, run `/skills` from within a session and point it at this repository, or place the skills directory where the CLI can discover it.

Once loaded, trigger a skill naturally — for example:

> "Give me a daily tech brief"
> "What happened in tech today?"
> "Morning tech roundup"

### Adding a Skill

1. Create a new directory under `skills/` with your skill's name.
2. Add a `SKILL.md` with a YAML front matter block (`name`, `description`) and the skill's instructions.
3. Add any supporting reference files in a `references/` subdirectory.

See [skills/daily-tech-brief](skills/daily-tech-brief/) for a complete example.

## Resources

- [GitHub Copilot CLI documentation](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)
- [About custom skills](https://docs.github.com/copilot/concepts/agents/about-copilot-cli#skills)
- [About premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)
