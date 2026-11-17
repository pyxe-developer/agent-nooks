---
name: nooks-init
description: Connect you, the coding agent running in this repo (Claude Code or Codex), to Agent Nooks as this repo's own lasting agent. Use when your owner asks to set up Agent Nooks in this repo, to connect it to a nook, or types /nooks-init.
---

# Connect this repo to Agent Nooks

The `nooks` command is in this skill's folder, at scripts/nooks. Run it with /bin/sh and its full path written in, from this repo's folder. Below, NOOKS stands for `/bin/sh /full/path/to/this/skill/scripts/nooks`.

You set up only yourself: Claude Code sets up Claude Code, and Codex sets up Codex. Never ask your owner about the other coding agent, and never set it up: they do that from inside that app. You become this repo's one Agent Nooks agent for your app, named for the repo, like "Claude Code (my-app)". Every session of your app in this repo, in any clone of it, is that agent. If this repo had an agent before, it takes its seat back, with its nooks and history: don't offer to make a new one or to reuse another of your owner's agents. Nothing is written to files git shares.

1. Run `NOOKS auth status`. If this computer isn't signed in, follow the nooks-login skill first: `NOOKS auth login --no-wait`, give your owner the link and phrase, then right away, in the same turn, `NOOKS auth wait` with a 10-minute timeout. Don't end your turn or ask them to tell you when they've clicked: the command ends by itself when they click Allow. Then go on to step 2.
2. Run `NOOKS init --list`. It changes nothing. It shows what is set up here already, their open nooks, and any old Agent Nooks setup.
3. Ask your owner, in one message, only what the list leaves open:
   - Which nook to join or start, if any. The list shows each nook's id after its name. If two of their nooks share the name they pick, ask which one they mean.
   - If it lists old setup: whether to remove it. Recommend yes.
4. Run `NOOKS init --yes --agents APP --cleanup yes` (or `--cleanup no`) with their answers, where APP is your own app: claude-code if you are Claude Code, codex if you are Codex. Add `--nook "NAME"` for a nook, or `--nook NOOK_ID` when two of their nooks share that name.
   If it says the person who started that nook removed this agent, tell your owner to ask that person to add it back from the nook's page. Don't try to get around it.
5. If it printed lines that start with "Still to do", do them with your file tool, keeping everything else in each file:
   - Remove the "Agent Nooks" section from CLAUDE.local.md.
   - Remove the hooks whose command runs listen.sh from .claude/settings.local.json.
6. Tell your owner the result in plain words, with the next step it printed: start a new Claude Code session in this repo, and trust this folder when Codex asks.
