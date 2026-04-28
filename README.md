# Steelman

A Claude Code skill for pressure-testing decisions before you commit. For Claude Code users facing high-stakes, hard-to-reverse choices.

## What it does

When you invoke `/steelman`, Claude genuinely argues for the 2-3 strongest alternatives to whatever direction you've chosen. Not devil's advocate theater — real arguments, rooted in your specific context, presented at full strength. Then you decide whether to proceed, reconsider, or investigate further.

Full technique: see [SKILL.md](./SKILL.md).

## Install

**Prerequisites:** Claude Code installed. Skills load automatically from `~/.claude/skills/`; no restart needed.

Clone into your skills directory:

```bash
git clone https://github.com/techiejd/claude-skill-steelman.git ~/.claude/skills/steelman
```

Or grab just `SKILL.md` with curl:

```bash
mkdir -p ~/.claude/skills/steelman && \
  curl -fsSL https://raw.githubusercontent.com/techiejd/claude-skill-steelman/main/SKILL.md \
  -o ~/.claude/skills/steelman/SKILL.md
```

To update later: `cd ~/.claude/skills/steelman && git pull` (clone install only).

### Verify it works

In any Claude Code session, paste:

```
I'm going to use Postgres for this project.
/steelman
```

You should see:

1. **Blind spots** in choosing Postgres (2-4 bullets, specific to "this project")
2. **2-3 alternatives** (e.g., SQLite, DynamoDB) each argued at full strength
3. **An honest assessment** — did Postgres survive the scrutiny?
4. **A decision prompt** — proceed / reconsider / investigate

If you get a generic pros/cons list or a "your choice is still solid" closer, the skill didn't load — re-check the directory path.

## Usage

State your direction, then invoke the skill:

```
"We're going with GraphQL for our API layer."
/steelman
```

Claude may also **suggest** invoking it when it notices a high-stakes decision in context (architecture choice, technology selection, strategic pivot). It will ask before running — never auto-trigger.

## When to use it

- Architecture choices (monolith vs. microservices, database selection)
- Technology selections (frameworks, languages, platforms)
- Business decisions (pricing models, go-to-market strategy)
- Any high-stakes choice where momentum bias might be doing the thinking for you

## Limitations

- **Not for already-shipped decisions.** Steelmanning a choice you can't reverse adds friction without value.
- **Requires you to state a direction.** "Should I use X or Y?" isn't a steelman input — pick one and then invoke.
- **Anti-sycophancy quality varies by model.** Tested primarily on Claude Opus / Sonnet. Smaller or older models may revert to hedging.
- **Auto-suggest is probabilistic.** Claude won't always notice a high-stakes decision. Invoke explicitly when it matters.

## Star this project

Stars are the signal I use to decide whether to keep investing in a skill. If `steelman` caught a decision you would've shipped on autopilot, [star the repo](https://github.com/techiejd/claude-skill-steelman) — it's the difference between this getting more anti-sycophancy hardening and going stale.

## Contributing

Found a case where Claude broke the technique — sycophantic close, hedged alternative, generic argument from training data instead of your context? Open an issue with the transcript. PRs to [SKILL.md](./SKILL.md) welcome; please include the failure case the change addresses.

## License

[MIT](./LICENSE)
