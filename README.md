# Review Skills

Agent skills for general and code review workflows.

## Install

List available skills:

```bash
npx skills add ramos/review-skills --list
```

Install interactively:

```bash
npx skills add ramos/review-skills
```

Install a specific skill:

```bash
npx skills add ramos/review-skills --skill bro
npx skills add ramos/review-skills --skill simplify
```

## Skills

### General

- `bro` - Restate the last message in plain human language, no jargon.

### Code Review

- `crusty-old-engineer` - Grounded skeptical engineering advice for architecture, legacy refactors, tooling, and broad planning questions.
- `simplify` - Review changed code for reuse, quality, and efficiency, then fix issues found.
- `self-review` - Self-review the code you just wrote for bugs, duplication, and reusability.
- `thermo-nuclear-code-quality-review` - Extremely strict maintainability review for abstraction quality, giant files, and spaghetti-condition growth.

## Repository Shape

Skills live under `skills/<category>/<skill-name>/SKILL.md`. The `.claude-plugin/plugin.json` manifest curates which skills are exposed by default, and `skills.sh.json` groups the public skills.sh page.
