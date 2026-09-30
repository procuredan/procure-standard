# AGENTS.md — read this before you do anything

You are working on a **Procure Media** property. Whatever tool you are (Claude, ChatGPT, Grok, Codex, or a human), this is the same rulebook. Read it before you build, change, or deploy.

## Order of reading
1. **`LAWS.md`** — the non-negotiables. If an action would break a law, **stop and say so** rather than proceeding.
2. **`ARCHITECTURE.md`** — how Cloudflare, GitHub and deploy are shaped here, and which shape this property uses.
3. **`PLAYBOOK.md`** — the steps a change follows to reach production.

## Three rules that override everything else

**Never guess.** Before any command, claim, or instruction that depends on how a tool, script, config, or file behaves, **read the actual source and verify it**, and state what you read. If you cannot verify something, say "I cannot verify X" and stop. Do not infer or assume.

**Nothing reaches production except through the documented path.** No cloud-console edits, no pages hand-built in a dashboard, no bare CLI deploys, no editing content that lives in a key-value store as if it were the master copy. If the documented path is blocked, stop — do not route around it.

**The decision gate is the owner (Dan).** Deploying, running a migration, pushing, enabling ads, or sending real outreach all require an explicit human OK. Build and test freely; stop before anything goes live.

## If a gate or check refuses you
That is the system working. **Do not work around it, disable it, or retry with the check skipped.** Report what refused, quote the exact message, and wait for a decision.

## Scope
Applies to **every new property from 2026-09-29 forward**, and to existing properties as they migrate.

**Explicitly exempt — do not change how these are built or deployed:** `snapndone`, `snapndish`, `hankhere`. If you are working on one of those, this standard does not apply and you should leave their process alone.

## What you will not find here
No source code, scripts, credentials, inventory, or per-property configuration — those are private. If a task requires them, you need access to the private factory, not this repo.
