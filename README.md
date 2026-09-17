# learn-by-doing

A [Claude Code](https://claude.com/claude-code) skill that turns Claude into a mentor instead of an implementer.

Normally Claude edits your files and runs your commands. With this skill active, it doesn't — it tells you what to do, why, and what to expect, then waits while you do it yourself. Every change Claude makes for you is a rep you didn't get.

## Install

Clone into your personal skills directory:

```bash
git clone https://github.com/LeonardoM011/learn-by-doing-skill.git \
  ~/.claude/skills/learn-by-doing
```

Or, to scope it to a single project, clone into `.claude/skills/learn-by-doing` inside that repo.

Claude picks up the skill on the next session — no restart of anything else needed.

## Usage

Invoke it explicitly:

```
/learn-by-doing
```

Or just say what you want in plain language — the skill triggers on phrases like *"teach me"*, *"guide me"*, *"learning mode"*, *"don't do it for me"*, *"I want to do it myself"*.

Once active it stays active for the rest of the session, until you explicitly turn it off:

```
stop learning mode
```

## What changes

**Claude still will:** read files, search the codebase, run read-only inspection (`git status`, `git diff`, `cat`, `grep`, log reads) — and often hand those commands to you instead, when the inspection itself is the lesson.

**Claude won't:** create, edit, or delete files; run anything that changes state (installs, builds, migrations, commits, pushes, restarts, config edits, deploys); or paste a finished solution you can copy without thinking.

Instead you get one step at a time, each with:

1. **What** — the exact command, or which file and roughly where to change it
2. **Why** — the concept behind it, in a sentence or two
3. **What to expect** — so you can tell whether it worked
4. **How to verify**, when relevant

For code, Claude starts at the top of a ladder and only descends if you're stuck: describe the goal → name the concept or API → pseudocode skeleton with gaps → exact code as a last resort.

When a step fails, you don't get handed the fix. You get pointed at the line of the error that matters and nudged toward the cause.

## Escape hatches

- **One-off override** — *"just do this one for me"*: Claude does that single thing, explains it, then returns to mentor mode.
- **Boilerplate** — for tedium with no learning value (200 lines of test fixtures, a rename across 40 files), Claude offers to do it but asks first.
- **Off for the session** — *"stop learning mode"* / *"just do it"*.

## Safety

Before anything destructive or hard to undo — `rm -rf`, dropping tables, `git reset --hard`, force pushes, firewall rules on a remote box, editing `sshd_config` — Claude warns first and tells you how to back up or roll back. On remote machines it flags steps that could lock you out.

## Repo layout

```
SKILL.md    the skill itself (frontmatter + instructions)
LICENSE     MIT
```

## License

MIT — see [LICENSE](LICENSE).
