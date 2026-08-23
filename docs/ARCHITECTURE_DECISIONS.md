# Culture & Taste Daily — Audit Baseline Decisions v1

Status: **proposed baseline for review**  
Date: 2026-08-23  
Scope: documentation/schema only. No production code, workflow, or `gh-pages` change is authorized by this document.

## Decision 0 — Production-contract authority

### Problem

Two different representations currently carry the label Production Contract v2: the legacy Library document `Culture & Taste Daily — Production Prompt v2` / `Pasted markdown.md`, and the migration document `docs/PRODUCTION_CONTRACT_V2.md`. They are not a byte-for-byte mirror: the Library v2 includes local archive-path and artifact-delivery requirements, while the repository document adapts parts of the contract toward the GitHub migration. Calling both canonical would create silent drift.

### Decision

1. The Library document remains the **canonical historical Production Contract v2** for the existing system until an explicit version-controlled successor is approved.
2. `docs/PRODUCTION_CONTRACT_V2.md` is a **migration adaptation / draft successor**, not an independent canonical v2. It must not silently override the Library v2.
3. Before production cutover, reconcile the two deliberately and create a new versioned repository contract (recommended name: `PRODUCTION_CONTRACT_V3.md`) with a short migration note listing intentional changes. Do not pretend an adapted contract is an exact v2 mirror.
4. Once v3 is approved, the repository contract becomes canonical for Culture & Taste production. Future changes happen by Git commit/PR and version/decision log; the Library v2 becomes a frozen historical reference.
5. Until v3 approval, a material conflict between Library v2 and the migration adaptation is **BLOCKED**. Preserve the stricter truth/accessibility/privacy requirement rather than weakening a rule by accident.
6. HarryTone remains separately canonical in `GUAiZzz/harry-tone`; the production contract must never impersonate or fork HarryTone.

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