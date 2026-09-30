# ARCHITECTURE — Cloudflare, GitHub, deploy

How every Procure property is shaped. Architecture and conventions only — no code, no inventory, no configuration.

## 1. Property types

Every property is exactly one of two things. Decide this **before** anything is built, because it determines the whole path.

**Static property** — a marketing site or landing page. Content and presentation only: no server-side logic, no database, no authentication, no webhooks.

**Application property** — anything with request routing, a database, key-value state, authentication, scheduled work, webhooks, or an API.

If a property starts static and later needs logic, it is **promoted** to an application property deliberately — not by bolting a script onto a static page.

## 2. Cloudflare

**Static properties run on Cloudflare Pages.** A Pages project is connected to that property's generated output repository and builds from it. Custom domain attached at the Pages project.

**Application properties run on Cloudflare Workers.** A Worker owns its routes and binds only the resources it actually needs (database, key-value, queues). Bindings are declared in the property's configuration file in the private factory — never added by hand in the dashboard.

**The dashboard is read-only in practice.** It is for looking at logs, metrics, and settings. It is never used to change code, content, or bindings. A dashboard change is invisible to every check and is the single hardest class of drift to detect (see `LAWS.md` L5).

**Secrets** are set through the platform's secret mechanism, per environment. They are never in any repository (L11).

## 3. GitHub

Three distinct roles. Confusing them is the most common mistake.

**The private factory repository** is the source of truth for everything Procure builds: application source, site sources, build tooling, gates, and per-property configuration. Nothing is authored anywhere else.

**A property's output repository** holds *generated* static output and exists so Cloudflare Pages has something to build. It is **output, never source** (L12). Editing it directly is an out-of-band change that the next build will erase.

**This public standard repository** holds the rules, architecture, and procedure. No code, no config, no secrets — so it can be read by any tool or person without exposing anything operational.

**Branching.** Work happens on a branch and reaches `main` through a pull request. `main` is the deployable state. Changes to the laws or to the gate require a reviewed PR — that is what makes them governance rather than convention.

## 4. Deploy — one pipeline

Every property, regardless of type, follows the same shape:

> **source in the factory → branch → pull request → automated gate → merge to `main` → deploy → receipt recorded**

Only the final publish step differs by property type: a Pages publish for static properties, a Worker deploy for application properties. That difference is an adapter at the end of the pipeline, **not a different process**.

### What the gate checks before anything ships
A deploy is refused unless every applicable check passes. The gate **fails closed** — a check that cannot run is a refusal, not a pass.

- The change came through the factory path, not an out-of-band edit.
- The code compiles.
- Any required database migration is already applied (L7).
- Live state matches the last recorded deploy — no drift from an out-of-band change.
- Backups exist for every file that changed (L6).
- No unresolved hard-stop applies to this property (L14).
- The property has a declared owner and the deployer matches it (L13).
- Post-deploy health checks pass.

### The receipt
Every successful deploy appends a machine-written record: what deployed, when, by whom, each check's result, and the version of this standard that was in force. Receipts are the audit trail — they answer "what was live on that date, and which rules governed it" without anyone having to remember.

## 5. Current state vs. target state

**Target:** the gate runs in CI on every pull request; merging to `main` deploys automatically; the production credential exists only in CI, so no human can deploy around the gate.

**Today:** the gate runs locally at deploy time and the owner gives an explicit OK. This is a real gate and it refuses real deploys, but it is a **convention backed by a check**, not a wall — a determined person can still take another path.

The standard becomes genuinely enforced only when the alternative paths are closed: dashboard editing disabled at the account level, direct CLI deploys removed, and any content currently mastered outside the repository moved into it. Until then, treat this document as the agreed way of working, not as something that physically cannot be bypassed.
