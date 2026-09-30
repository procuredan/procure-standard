# Procure Build & Deploy Standard

The single source of truth for **how Procure Media properties are built and deployed** — on Cloudflare, in GitHub, through one deploy path.

This repo is **public on purpose**. Any assistant working on a Procure property — Claude, ChatGPT, Grok, Codex, or a human — reads the same rules from here, so there is one rulebook instead of one per tool.

**Agents start at [`AGENTS.md`](./AGENTS.md).**

| File | What it is |
|---|---|
| `AGENTS.md` | Entry point for any AI assistant. Read first. |
| `LAWS.md` | The non-negotiables. Breaking one is a stop-work condition. |
| `ARCHITECTURE.md` | How Cloudflare, GitHub and deploy are shaped. |
| `PLAYBOOK.md` | The steps a change follows to reach production. |

## What is deliberately NOT in this repo
No source code. No scripts or build tooling. No credentials or secrets. No property-specific configuration, inventory, or ownership data. Those live in the private factory repository. **This repo is architecture and procedure only.**

## Status
v1, in force from 2026-09-29 for every new property. Changes require a reviewed pull request.
