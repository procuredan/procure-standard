# LAWS

Non-negotiable. Breaking one of these is a **stop-work condition**, not a judgment call. If a task appears to require breaking a law, stop and raise it.

**L1 — Everything goes through the factory path.** Every change, no matter how small, is made in the source of truth and deployed by the documented path so it is recorded. No out-of-band edits.

**L2 — Never guess.** Read the actual file, config, or data and verify before claiming or acting. State what you read. If you cannot verify, say so and stop.

**L3 — The decision gate is human.** Deploy, migration, push, enabling ads, and real outreach sends each require an explicit OK from the owner. Everything up to that point may proceed freely.

**L4 — One deploy path per target type, and only that path.** Never a bare CLI deploy that bypasses the gate. The documented command is the only way.

**L5 — No console or dashboard edits.** Production is never changed by clicking in a cloud provider's dashboard, and pages are never hand-built there. Such a change is invisible to every check and will be treated as drift.

**L6 — Back up before you edit.** Any file being changed is first copied to `<name>.PRE-<reason>-BAK-<YYYYMMDD>`. No backup, no edit.

**L7 — Migrations land first.** A database migration is applied and verified *before* the code that depends on it deploys. Deploying code first fails silently and is worse than failing loudly.

**L8 — Reconcile against live before uploading (SYNC-FIRST).** Local source may be stale. Diff against what is actually live before publishing, or you will overwrite work that isn't in your copy.

**L9 — The repository is the master copy.** Content is never mastered in a key-value store, a dashboard, or a CMS field. Those are *publish targets*. If it isn't in the repo, it isn't real and it cannot be reviewed or rolled back.

**L10 — Every deploy writes a receipt.** A machine-written record of what deployed, when, by whom, which checks passed, and which version of this standard was in force.

**L11 — Secrets are never committed.** Credentials, tokens, and keys are set through the platform's own secret mechanism and never appear in any repository, public or private.

**L12 — A generated output repository is output, never source.** Editing a build artifact directly is an out-of-band change and will be overwritten by the next build.

**L13 — Every property has a declared owner.** Work on an unowned property does not deploy. (The ownership map itself is private operational state, not part of this public standard.)

**L14 — A declared HARD-STOP blocks deployment until cleared.** Hard-stops mark work that must not reach production yet. (The active list is private operational state.)

**L15 — New properties adopt this standard from day one.** Exemptions exist only where they are explicitly named in `AGENTS.md`. Convenience is not an exemption.
