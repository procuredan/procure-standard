# PLAYBOOK — how a change reaches production

Follow every step. Skipping one is how the failures in `LAWS.md` happened in the first place.

## Before you touch anything
1. **Confirm the property type** — static or application (`ARCHITECTURE.md` §1). It determines the whole path.
2. **Confirm the property is not exempt.** See the exemption list in `AGENTS.md`. If it is, stop — leave its process alone.
3. **Confirm ownership.** Unowned work does not deploy (L13).
4. **Check for an active hard-stop** on this property (L14). If one applies, stop.
5. **Read the actual current state** — the live file, the live config, the live data. Do not work from memory or from a summary. (L2)
6. **Reconcile local against live** before editing (L8). Local copies go stale; a stale upload overwrites real work.

## Making the change
7. **Back up every file you are about to edit** → `<name>.PRE-<reason>-BAK-<YYYYMMDD>` (L6).
8. **Edit the source in the factory.** Never the generated output repository (L12), never a dashboard, never a key-value entry (L5, L9).
9. **Work on a branch**, not directly on `main`.
10. **If the change needs a database migration, apply and verify the migration first** (L7). Never deploy the code that depends on it beforehand.

## Getting it reviewed and shipped
11. **Open a pull request.** Describe what changed and what you verified — not what you intended.
12. **Let the gate run.** If it refuses, **stop**. Report the exact refusal message. Do not disable the check, do not retry with it skipped, do not find another route.
13. **Get the explicit human OK** before anything goes live (L3). This is the decision gate and it is never assumed from silence.
14. **Merge and deploy through the documented path only** — never a bare CLI deploy (L4).

## After it ships
15. **Verify on the real thing.** Load the live page, place the real call, submit the real form. A green deploy is not proof the change works.
16. **Confirm the receipt was written** (L10).
17. **Record the decision** in the decision log so every other person and tool inherits it.

## If something goes wrong
- **The gate refused:** that is the system working. Report it; do not route around it.
- **Drift was detected** (live doesn't match the last recorded deploy): someone changed production out of band. Do **not** overwrite it blindly. Prove the local copy contains everything live has before adopting it as the new baseline, then reconcile.
- **You broke something live:** say so immediately and plainly. Restore from the backup taken in step 7 — which is why step 7 is not optional.

## The standing reminder
Being fast is not a reason to skip a step. Every rule in `LAWS.md` exists because skipping it already cost something real.
