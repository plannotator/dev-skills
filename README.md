## A growing list of simple skills to enhance development with agents

#### Categories

- **general**: non-opinionated daily essentials
- **code-review**: varied and curated industry code review skills

#### Most useful

90% of the time, these two skills provide the most utility without disrupting workflows:

- **bro**: explain the last message more simply, no jargon
- **self-review**: have the agent conduct a self-review of its last effort

*these skills have nothing to do with the install of [Plannotator](https://github.com/backnotprop/plannotator)*

## Install

```bash
npx skills add plannotator/dev-skills
```

List all first:

```bash
npx skills add /Users/ramos/review-skills --list
```

Install a specific skill:

```bash
npx skills add plannotator/dev-skills --skill bro
npx skills add plannotator/dev-skills --skill simplify
```

## Skills

### General

- `bro` - Restate the last message in plain human language, no jargon.

### Code Review

- `claude-review`: Combined Claude's oss skill and derived more capable review. [Source: [Claude Code](https://www.anthropic.com/product/claude-code)]
- `codex-review`: The actual codex-rs source review prompt. [Source: [Codex](https://github.com/openai/codex)]
- `simplify`: Review changed code for reuse, quality, and efficiency. [Source: [Claude Code](https://www.anthropic.com/product/claude-code)]
- `self-review`: Self-review the code you just wrote for bugs, duplication, and reusability.
- `thermo-nuclear-code-quality-review`: Strict maintainability review for abstraction quality, giant files, and spaghetti growth. [Source: [Cursor](https://cursor.com/)]

## Repository Shape

Skills live under `skills/<category>/<skill-name>/SKILL.md`. The `.claude-plugin/plugin.json` manifest curates which skills are exposed by default, and `skills.sh.json` groups the public skills.sh page.
