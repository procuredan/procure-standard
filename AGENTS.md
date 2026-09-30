# AGENTS.md — read this before you do anything

You are working on a **Procure Media** property. Whatever tool you are (Claude, ChatGPT, Grok, Codex, or a human), this is the same rulebook. Read it before you build, change, or deploy.

## This file is the entry point, not the whole standard
If you were handed only this URL, fetch the other three now. Full URLs, so they resolve from anywhere — a chat window, a browser, a script.

1. **`LAWS.md`** — the non-negotiables. If an action would break a law, **stop and say so** rather than proceeding.
   `https://raw.githubusercontent.com/procuredan/procure-standard/main/LAWS.md`
2. **`ARCHITECTURE.md`** — how Cloudflare, GitHub and deploy are shaped here, and which shape this property uses.
   `https://raw.githubusercontent.com/procuredan/procure-standard/main/ARCHITECTURE.md`
3. **`PLAYBOOK.md`** — the steps a change follows to reach production.
   `https://raw.githubusercontent.com/procuredan/procure-standard/main/PLAYBOOK.md`

Read them in that order before you build, change, or deploy anything.

## Three rules that override everything else

**Never guess.** Before any command, claim, or instruction that depends on how a tool, script, config, or file behaves, **read the actual source and verify it**, and state what you read. If you cannot verify something, say "I cannot verify X" and stop. Do not infer or assume.

**Nothing reaches production except through the documented path.** No cloud-console edits, no pages hand-built in a dashboard, no bare CLI deploys, no editing content that lives in a key-value store as if it were the master copy. If the documented path is blocked, stop — do not route around it.

**The decision gate is the owner (Dan).** Deploying, running a migration, pushing, enabling ads, or sending real outreach all require an explicit human OK. Build and test freely; stop before anything goes live.

## If a gate or check refuses you
That is the system working. **Do not work around it, disable it, or retry with the check skipped.** Report what refused, quote the exact message, and wait for a decision.

## Scope
Applies to **every new property from 2026-09-29 forward**, and to existing properties as they migrate.

**Explicitly exempt — do not change how these are built or deployed:** `snapndone`, `snapndish`, `hankhere`. If you are working on one of those, this standard does not apply and you should leave their process alone.

## What you will not find here — and what that means for you
No source code, scripts, credentials, inventory, owner map, active hard-stop list, or per-property configuration. All of that is private operational state and it is excluded on purpose.

**So these rules are the foundation, not the build instructions.** They tell you how work is shaped, what is forbidden, and where the stop conditions are. They do not tell you where a property's source lives, which command deploys it, who owns it, or whether it is currently under a hard-stop.

If you are reasoning, reviewing, or planning, this repo is enough. **If you are about to build or deploy, it is not** — you also need access to the private factory. Having the rules without the factory does not mean you can ship. Say so rather than improvising a path.
