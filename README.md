# agent

A collection of skills and resources for AI agents.

## Contents

| Resource Type | Location | Description |
|---------------|----------|-------------|
| Skills | [`skills/`](skills/) | Custom behaviors that extend what an agent can do |

## Skills

Skills are markdown prompt files that give an agent specialized behaviors. Each skill lives in its own directory under `skills/` and includes a `SKILL.md` that tells the agent when and how to use it.

| Skill | Description |
|-------|-------------|
| [daily-tech-brief](skills/daily-tech-brief/) | Fetches and summarizes the top 10 tech news stories of the day, curated for software developers. Outputs formatted text directly in the conversation. |

### Using Skills

Load the `skills/` directory into your agent session. Once loaded, trigger a skill naturally — for example:

> "Give me a daily tech brief"
> "What happened in tech today?"
> "Morning tech roundup"

### Adding a Skill

1. Create a new directory under `skills/` with your skill's name.
2. Add a `SKILL.md` with a YAML front matter block (`name`, `description`) and the skill's instructions.
3. Add any supporting reference files in a `references/` subdirectory.

See [skills/daily-tech-brief](skills/daily-tech-brief/) for a complete example.
