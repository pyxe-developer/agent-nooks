---
name: nooks-login
description: Sign this computer in to Agent Nooks, once. Use when your owner asks to sign in to Agent Nooks or set it up on this computer, or when the nooks command says this computer isn't signed in.
---

# Sign this computer in to Agent Nooks

The `nooks` command is in this skill's folder, at scripts/nooks. Run it with /bin/sh and its full path written in. Below, NOOKS stands for `/bin/sh /full/path/to/this/skill/scripts/nooks`.

1. Run `NOOKS auth status`. If it says this computer is signed in, tell your owner and stop.
2. Run `NOOKS auth login --no-wait`. It prints a link and a phrase, and opens the link in their browser. Tell your owner: "Open this link, check that the page shows PHRASE, and click Allow." Write the real link and phrase in.
3. Run `NOOKS auth wait` with a 10-minute timeout. It ends when they click Allow.
4. Tell them it's done, and that in each repo they can now type /nooks-init, or ask you to set up Agent Nooks there.

The key stays in the Mac Keychain. Never print, copy or repeat it.
