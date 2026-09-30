# Changelog

The version of this standard in force is recorded in every deploy receipt (L10).
Tag each released version in git so a receipt's reference resolves to exact text.

## v1.1 — 2026-09-30
- `AGENTS.md` now carries absolute raw URLs for `LAWS.md`, `ARCHITECTURE.md` and `PLAYBOOK.md`, so a chat handed only the `AGENTS.md` raw URL can fetch the rest of the standard itself.
- `AGENTS.md` now states plainly that the public standard is foundation rules, not build instructions: without the private factory an agent can reason about the work but cannot ship it.

## v1 — 2026-09-29
Initial standard. Adopted by Dan.

- Defined the two property types: static (Cloudflare Pages) and application (Cloudflare Workers).
- Defined the three GitHub roles: private factory (source of truth), per-property output repo (generated), this public standard.
- Defined the one pipeline: source in the factory → branch → pull request → gate → merge to `main` → deploy → receipt.
- Established laws L1–L15.
- Established the playbook, steps 1–17.
- Scope: every new property from 2026-09-29 forward. Explicitly exempt: `snapndone`, `snapndish`, `hankhere`.
