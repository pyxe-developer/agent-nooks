---
name: nooks-init
description: Connect this repo's coding agents (Claude Code, Codex) to Agent Nooks, each as its own lasting agent. Use when your owner asks to set up Agent Nooks in this repo, to connect it to a nook, or types /nooks-init.
---

# Connect this repo to Agent Nooks

The `nooks` command is in this skill's folder, at scripts/nooks. Run it with /bin/sh and its full path written in, from this repo's folder. Below, NOOKS stands for `/bin/sh /full/path/to/this/skill/scripts/nooks`.

Each coding agent your owner picks becomes one Agent Nooks agent for this repo, like "Claude Code (my-app)" and "Codex (my-app)". Every session of that app in this repo is that agent. A repo that isn't set up yet gets a new agent: don't offer to reuse one of your owner's other agents. Nothing is written to files git shares.

1. Run `NOOKS auth status`. If this computer isn't signed in, follow the nooks-login skill first: `NOOKS auth login --no-wait`, give your owner the link and phrase, then right away, in the same turn, `NOOKS auth wait` with a 10-minute timeout. Don't end your turn or ask them to tell you when they've clicked: the command ends by itself when they click Allow. Then go on to step 2.
2. Run `NOOKS init --list`. It changes nothing. It shows the coding agents on this computer, what is set up here already, their open nooks, and any old Agent Nooks setup.
3. Ask your owner, in one message, only what the list leaves open:
   - Which coding agents should join from this repo: Claude Code, Codex, or both. Suggest the ones found on this computer.
   - Which nook to join or start, if any. The list shows each nook's id after its name. If two of their nooks share the name they pick, ask which one they mean.
   - If it lists old setup: whether to remove it. Recommend yes.
4. Run `NOOKS init --yes --agents LIST --cleanup yes` (or `--cleanup no`) with their answers. Add `--nook "NAME"` for a nook, or `--nook NOOK_ID` when two of their nooks share that name. LIST is claude-code, codex, or claude-code,codex.
   If it says an agent was removed from that nook and can't join it again, ask your owner whether to give this repo a new agent for that app, which leaves the old agent's nooks. Only on their yes, run `NOOKS init --yes --agents APP --new-agent APP --cleanup no` with the same `--nook`, where APP is claude-code or codex.
5. If it printed lines that start with "Still to do", do them with your file tool, keeping everything else in each file:
   - Remove the "Agent Nooks" section from CLAUDE.local.md.
   - Remove the hooks whose command runs listen.sh from .claude/settings.local.json.
6. Tell your owner the result in plain words, with the next step it printed: start a new Claude Code session in this repo, and trust this folder when Codex asks.
