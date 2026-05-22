# Repo Setup Notes

## Short Answer

Put general and code-review skills in the same repo, as separate skill folders. Users can choose individual skills during install, install specific ones with `--skill`, or install all. The best pattern is one public skills repo with a curated manifest and root README, not a README inside every skill.

## What I Found

The standard unit is:

```text
skill-name/
  SKILL.md
  scripts/      optional
  references/   optional
  assets/       optional
```

`SKILL.md` is the required per-skill doc. It has YAML frontmatter with at least `name` and `description`; the description is what agents use to decide whether to load the skill. The spec recommends keeping `SKILL.md` lean and moving deeper material into `references/`, `scripts/`, or `assets/`.

Source: [Agent Skills spec](https://agentskills.io/specification)

Vercel's `skills` CLI supports multi-skill repos, direct paths, listing, interactive selection, specific skill install, and all-skill install:

```bash
npx skills add owner/repo --list
npx skills add owner/repo
npx skills add owner/repo --skill code-review
npx skills add owner/repo --skill '*'
npx skills add owner/repo --all
```

Source: [vercel-labs/skills README](https://github.com/vercel-labs/skills)

I also verified locally that `mattpocock/skills` exposes only 13 curated skills by default via `.claude-plugin/plugin.json`, but `--full-depth` finds 27 including deprecated/in-progress ones. That means the manifest is useful as your public catalog.

## Recommended Structure

```text
agent-skills/
  README.md
  LICENSE
  skills.sh.json
  .claude-plugin/
    plugin.json              # simple single collection
    # or marketplace.json     # if you want general/review as separate plugin groups
  skills/
    general/
      bro/
        SKILL.md
    code-review/
      crusty-old-engineer/
        SKILL.md
      simplify/
        SKILL.md
      self-review/
        SKILL.md
      thermo-nuclear-code-quality-review/
        SKILL.md
```

Use `plugin.json` for one collection:

```json
{
  "name": "ramos-agent-skills",
  "skills": [
    "./skills/general/bro",
    "./skills/code-review/crusty-old-engineer",
    "./skills/code-review/simplify",
    "./skills/code-review/self-review",
    "./skills/code-review/thermo-nuclear-code-quality-review"
  ]
}
```

Use `.claude-plugin/marketplace.json` if you want installable groups like `general-agent-skills` and `code-review-agent-skills`. Anthropic's public skills repo uses this pattern to expose grouped plugins such as document skills and example skills.

Sources:

- [anthropics/skills](https://github.com/anthropics/skills)
- [raw marketplace.json](https://raw.githubusercontent.com/anthropics/skills/main/.claude-plugin/marketplace.json)

## README / Metadata

Use:

- Root `README.md`: human-facing overview, install commands, skill index, examples.
- `SKILL.md`: agent-facing instructions for each skill.
- `references/*.md`: deeper agent-facing docs loaded only when needed.
- Category `README.md`: optional, human-only; fine for browsing.
- Per-skill `README.md`: usually skip. It is not a discovery surface; it will drift from `SKILL.md`.

Add `skills.sh.json` at repo root if your repo appears on skills.sh and you want public page grouping. It only affects skills.sh display, not CLI install behavior.

Source: [skills.sh customize docs](https://www.skills.sh/docs/customize)

For Codex/OpenAI-facing UI metadata, you can optionally add `agents/openai.yaml` inside each skill, but treat that as product-specific metadata, not the cross-agent standard.

## For This Repo

Use one repo with two categories:

- `skills/general/*`
- `skills/code-review/*`

Keep each skill narrow by trigger. Do not make one giant general skill if there are separate workflows like "turn goal into plan," "critique a plan," and "extract risks." Same for review: `simplify`, `self-review`, and `thermo-nuclear-code-quality-review` are separate skills with different review scopes.

Use a manifest to curate what installs by default, keep drafts out of it, and let users choose individual skills:

```bash
npx skills add ramos/review-skills --skill simplify
```
