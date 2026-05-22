A growing list of simple skills to enhance development with agents.

**general:** non-opionated daily essentials.
**code-review:** varying & curated industry code review skills

90% of the time these two skills provide the most utility without disrupting workflows:

**bro** - explain the last message more simply, no jargon
**self-review** - have the agent conduct a self review of last effort of work.

## Install

```bash
npx skills add plannotator/dev-skills
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

- `claude-review` - Exact Plannotator Claude Code review prompt as a skill.
- `codex-review` - Exact Plannotator Codex review prompt as a skill.
- `crusty-old-engineer` - Grounded skeptical engineering advice for architecture, legacy refactors, tooling, and broad planning questions.
- `simplify` - Review changed code for reuse, quality, and efficiency, then fix issues found.
- `self-review` - Self-review the code you just wrote for bugs, duplication, and reusability.
- `thermo-nuclear-code-quality-review` - Extremely strict maintainability review for abstraction quality, giant files, and spaghetti-condition growth.

## Repository Shape

Skills live under `skills/<category>/<skill-name>/SKILL.md`. The `.claude-plugin/plugin.json` manifest curates which skills are exposed by default, and `skills.sh.json` groups the public skills.sh page.
