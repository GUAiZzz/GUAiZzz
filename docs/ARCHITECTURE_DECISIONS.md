# Culture & Taste Daily — Audit Baseline Decisions v1

Status: **proposed baseline for review**  
Date: 2026-08-23  
Scope: documentation/schema only. No production code, workflow, or `gh-pages` change is authorized by this document.

## Decision 0 — Production-contract authority

### Problem

Two representations of Production Contract v2 exist: the legacy Library document and `docs/PRODUCTION_CONTRACT_V2.md`. Leaving both independently "canonical" creates silent drift.

### Decision

Use a one-way cutover:

1. The Library document is the **historical source snapshot** from which the repository copy was migrated.
2. During this audit-baseline PR, compare the repository copy against the Library source and record any material differences. No silent merge of conflicting rules is allowed.
3. Once this baseline is approved, `docs/PRODUCTION_CONTRACT_V2.md` becomes the **canonical version-controlled Culture & Taste production contract for migration and future production**.
4. After cutover, future contract changes happen by versioned Git commit/PR with a decision note. The Library copy may remain as an archive/reference but may not override the repository contract by timestamp alone.
5. HarryTone remains separately canonical in `GUAiZzz/harry-tone`; the production contract must never impersonate or fork HarryTone.

Until step 3 is approved, any material conflict between the two contract copies is **BLOCKED** and must be surfaced explicitly.

## Decision 1 — Repository boundary

### Decision

The preferred production architecture remains a **dedicated Culture & Taste source repository**, rather than continuing to develop inside the legacy personal blog repository.

Why:

- isolates publication code/history from the old blog;
- makes Codex/CI permissions easier to reason about;
- allows source and generated Pages output to be separated cleanly;
- reduces the blast radius of automation mistakes.

This audit PR does **not** create or cut over that repository. Until a dedicated repository is available, `codex/culture-taste-system-v3` remains the migration workspace and `gh-pages` remains untouched production.

A materially better repository arrangement may replace this decision only through an explicit ADR comparing risk, Pages constraints, migration cost, privacy, and rollback.

## Decision 2 — GitHub Pages artifact model

### Decision

Keep **GitHub Pages as the static hosting target**, but stop treating the deployed branch as the authoring/source-of-truth surface.

Target publication path:

`source candidate → deterministic validation/build → immutable Pages artifact → deploy → smoke test`

The future deployment workflow should use the supported GitHub Pages build-artifact model (or an equivalently isolated artifact deployment) rather than an editorial agent directly editing production files.

Required properties:

- source and deployed output are separable;
- deployment only occurs after required validation passes;
- overlapping runs cannot race;
- a failed candidate leaves the previous good Pages release live;
- rollback points to a known previously validated artifact/commit;
- the basic article remains readable without JavaScript.

No deployment workflow is added in this baseline PR.

## Decision 3 — Source-ledger privacy

### Problem

The production contract requires a private research/source ledger. A public GitHub repository is itself public even when a file is not linked from the website.

### Decision

Separate **private editorial evidence** from **public publication provenance**.

Private source-ledger instances may contain:

- research notes;
- rejected candidates;
- internal fact/inference distinctions;
- contradictions and uncertainty notes;
- internal QA/scoring/workflow metadata;
- unpublished editorial reasoning.

These instances **must not be committed to a public Culture & Taste repository or Pages artifact**.

Public issue metadata may contain only publishable fields needed for transparency and site generation, such as source title/publisher/URL/dates, image credit, public limitations, issue art direction, HarryTone commit, and public QA status.

The repository may contain schemas describing both artifacts, because schemas contain structure rather than private run data.

For the first implementation, private ledger data should remain in the trusted generation workspace and be excluded from the public build. A durable private storage/retention mechanism must be chosen before full automation cutover; do not invent one silently.

## Decision 4 — Daily automation gate

### Decision

The current direct-publish daily automation is not an approved production path and is paused.

It may be re-enabled only when all of the following are true:

1. canonical HarryTone can be resolved and its commit recorded at runtime;
2. the canonical version-controlled production contract is resolved unambiguously;
3. candidate generation writes to a non-production source/workspace;
4. private ledger data is excluded from public source/build artifacts;
5. deterministic validation exists for manifest, HTML, assets, internal links, accessibility, desktop/mobile/reduced-motion rendering, and no-JS reading;
6. deployment is fail-closed and cannot overwrite the previous good release on validation failure;
7. concurrency/race protection exists;
8. post-deploy smoke testing exists;
9. rollback is documented and tested;
10. multiple dry runs have completed without production writes.

The editorial automation and deployment automation should remain separate responsibilities. The editorial agent may generate and repair a candidate; deterministic CI decides whether it is deployable.

## Non-decision / room to improve

These are the strongest decisions supported by the current audit, not permanent doctrine. Codex should propose a better approach when it can demonstrate lower risk or better maintainability without weakening HarryTone, editorial authorship, daily visual variation, accessibility, archive integrity, privacy, deterministic QA, or rollback safety.