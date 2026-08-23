# Culture & Taste Daily — Upgrade Plan

## Goal

Turn the current migration prototype into a reliable, version-controlled publishing system that preserves HarryTone, daily visual authorship, historical archive integrity, privacy, and fail-closed deployment.

This plan is the strongest current proposal, not permanent doctrine. A materially better architecture is welcome if it preserves or improves truth, editorial authorship, accessibility, archive integrity, privacy, reliability, and maintainability.

## Target architecture

Preferred long-term repository:

`GUAiZzz/culture-taste-daily`

Suggested structure:

```text
AGENTS.md
README.md

docs/
  NORTH_STAR.md
  CURRENT_STATE.md
  PRODUCTION_CONTRACT_V3.md
  ARCHITECTURE.md
  DECISION_LOG.md

skill/
  HARRYTONE_VERSION.json

schemas/
  issue-manifest.public.schema.json
  source-ledger.private.schema.json

issues/
  2026-08-20/
  2026-08-21/
  2026-08-22/
  YYYY-MM-DD/

src/
  homepage/
  archive/
  shared/

scripts/
  validate-html
  validate-manifest
  validate-assets
  validate-links
  generate-archive
  generate-rss
  generate-sitemap
  render-screenshots
  smoke-test

tests/

.github/workflows/
  validate.yml
  deploy.yml
  post-deploy-check.yml
```

If a dedicated repository cannot be created in the current environment, prepare the migration on an isolated branch and do not silently collapse the architecture into the old live branch.

## HarryTone dependency

`GUAiZzz/harry-tone` remains canonical.

Every issue/build should record at least:

- source repository;
- source branch;
- source commit;
- loaded-at timestamp;
- required files.

Minimum required files for Culture & Taste long-form publication:

- `SKILL.md`
- `references/source-guide.md`
- `references/anti-ai-patterns.md`

The previously missing recovered reference `references/social-content.md` has been restored to the canonical HarryTone repository. Do not describe a pinned snapshot as “latest” unless the canonical repository is checked at runtime.

## Production-contract authority and V3 path

The Library document `Culture & Taste Daily — Production Prompt v2` remains the **canonical historical v2** until a version-controlled successor is explicitly approved.

`docs/PRODUCTION_CONTRACT_V2.md` in this migration branch is a **non-canonical migration adaptation / draft successor**. It must not silently override the Library v2.

Before production cutover:

1. compare Library v2 and the migration adaptation line by line at the level of requirements and intent;
2. preserve stricter truth, accessibility, privacy, archive, and delivery requirements unless an intentional change is approved;
3. document intentional changes;
4. create `docs/PRODUCTION_CONTRACT_V3.md`;
5. review and approve v3 explicitly;
6. only then make the repository v3 the canonical production contract and freeze Library v2 as historical reference.

A material unresolved conflict between Library v2 and the migration adaptation is BLOCKED.

## Historical migration

Investigate and restore historical sources before reconstructing anything.

Known minimum set:

- 2026-08-20 original full HTML;
- 2026-08-21 original HARRYTONE_LATEST full HTML + ZIP + desktop/mobile previews;
- 2026-08-22 PDF, plus search for original HTML/source before conversion.

Migration rule: preserve original text, sources, composition, palette, typography behavior, image behavior, and pacing. Do not normalize history into one template.

Remove the current JavaScript-required `.txt` reconstruction. The basic article must exist in the served HTML/DOM even when JavaScript fails.

## Web edition vs archival edition

Evaluate two representations rather than assuming one artifact must serve every purpose.

### Archival edition

- self-contained HTML;
- offline-safe display-critical assets;
- ZIP;
- manifest/reporting metadata;
- QA evidence;
- desktop/mobile previews.

### Web edition

- optimized local assets;
- smaller pages suitable for GitHub Pages;
- same editorial world;
- no remote display-critical dependencies;
- no JavaScript requirement for reading.

Before adopting this split, calculate current and projected storage cost and document the tradeoff.

## Private ledger vs public manifest

Do not put the private source ledger inside a public issue manifest.

### Private source ledger

Private ledger instances may contain research notes, rejected candidates, fact/inference distinctions, contradictions, uncertainty, image-rights evidence, unpublished reasoning, and internal workflow metadata.

Private ledger instances must never be committed to a public repository or included in a Pages artifact. The public repository may contain only the schema describing the private ledger.

A durable private retention/storage mechanism must be explicitly chosen before full automation cutover.

### Public issue manifest

Every issue may own a public `issue-manifest.json` containing publishable metadata only, such as publication date, public source provenance, art-direction metadata, HarryTone commit, public limitations, and reporting fields derived from completed checks/reviews.

Generate from publishable manifests where appropriate:

- homepage latest issue;
- archive;
- RSS;
- sitemap;
- OpenGraph/social metadata.

The homepage can be relatively stable. Individual issue art direction must remain independent.

## Responsibility and authority split

### AI/editorial generator

Responsible for:

- research;
- private source ledger creation;
- selection and deduplication;
- bounded editorial judgment;
- HarryTone writing;
- art direction;
- candidate issue generation;
- repair after failed checks/review.

The generator may report its own checks and proposed status, but **generator self-report is never deployment authority**.

### Deterministic CI

Responsible for independently producing technical evidence for:

- parsing;
- schema validation;
- asset validation;
- internal-link validation;
- automated accessibility checks;
- deterministic render capture at required viewports;
- no-JavaScript reading checks;
- archive/RSS/sitemap build integrity;
- build artifact creation;
- deployment mechanics;
- post-deploy smoke tests.

Screenshot/render creation can be deterministic; interpretation of visual quality is not assumed to be deterministic.

### Editorial / visual review

Editorial truth/judgment, HarryTone quality, historical fidelity, and visual authorship/usability require **separate review evidence** from the generation step. This may be a human review or a deliberately separate reviewer process, but it must be recorded distinctly from generator self-scoring.

### Deployment authority

Deployment is authorized only when the required technical CI evidence and required editorial/visual review evidence both satisfy the approved production contract.

Public manifest `status`, `qa`, and score fields are reporting data after the fact; they do not authorize deployment by themselves.

## Fail-closed publishing

Desired pipeline:

```text
scheduled editorial generation
→ candidate committed/staged in non-production source workspace
→ deterministic CI evidence
→ separate editorial/visual review evidence
→ deployment gate
→ approved?
    no  → previous production remains live
    yes → build immutable Pages artifact → deploy
→ post-deploy smoke test
```

A broken or unapproved daily issue must not corrupt or replace yesterday's good site.

Use concurrency protection so overlapping jobs cannot race or partially update production.

## Minimum deterministic technical evidence

### HTML

- parses cleanly;
- correct language metadata;
- semantic landmarks;
- complete basic article without JavaScript;
- Sources & Dates available;
- no empty required href/src.

### Assets

- local/embedded display-critical assets resolve;
- images decode and dimensions are sane;
- no required remote CSS/font/script dependencies;
- no broken local paths.

### Links

- internal navigation resolves;
- archive links resolve;
- local assets resolve;
- external source checking may run separately so temporary publisher downtime does not unnecessarily destroy a valid deployment.

### Accessibility

- keyboard-operable structure where automatable;
- visible-focus and landmark checks where automatable;
- meaningful alt-text presence;
- automated contrast/a11y checks where practical;
- axe or equivalent tooling where practical.

Automated checks do not replace editorial accessibility review where judgment is required.

### Render capture

At minimum capture:

- 1440 × 900 desktop;
- 390 × 844 mobile;
- reduced-motion variant.

Automated checks may detect overflow, clipping signals, missing assets, and page-level horizontal overflow. Visual pacing, hierarchy, historical fidelity, and authored quality remain part of separate visual review.

### Publication integrity

- public manifest schema valid;
- directory/date match;
- HarryTone version recorded;
- issue does not overwrite another date;
- archive generation deterministic;
- private ledger instances absent from public repository/build artifact.

## Status semantics

Keep exactly:

- PASS
- DEGRADED
- BLOCKED

The candidate/public manifest may report a status, but the deploy gate must derive authority from independently produced evidence rather than trusting that field.

PASS means the required technical evidence and required editorial/visual review actually exist and pass.

DEGRADED means the publication remains truthful and readable but an explicitly degradable capability is unavailable and the canonical contract permits publication under that limitation.

BLOCKED means a non-degradable red line or required approval/evidence is missing or failed.

Do not convert BLOCKED into PASS because of schedule pressure.

## Implementation order

### Phase 0 — Audit reconciliation

- Keep `CURRENT_STATE.md` factual and evidence-qualified.
- Record architectural decisions and unresolved choices.
- Keep production content/workflows untouched.

### Phase 1 — Source of truth

- Verify `AGENTS.md` and North Star.
- Reconcile Library historical v2 with the migration adaptation.
- Create and explicitly approve `PRODUCTION_CONTRACT_V3.md`.
- Verify current canonical HarryTone and record the resolved commit.
- Keep private/public schema boundaries explicit.

### Phase 2 — Repository architecture

Create or prepare a dedicated Culture & Taste source repository. Separate source from deployed output.

### Phase 3 — Historical migration

Restore 8/20 and 8/21 accurately. Investigate 8/22 original source before reconstruction. Eliminate JS-required article loading.

### Phase 4 — Manifest-driven publication

Add public issue manifests and generation from publishable metadata. Add RSS/sitemap where useful. Do not expose private ledger instances.

### Phase 5 — Independent QA/review evidence

Implement deterministic CI evidence for HTML/assets/links/accessibility/render capture/manifest validation, plus a separately recorded editorial/visual review step.

### Phase 6 — Deployment

GitHub Actions deploys only when the approved evidence gate passes. Add concurrency protection and rollback-safe behavior.

### Phase 7 — Post-deploy verification

Smoke-test the actual public URL and critical assets/internal links.

### Phase 8 — Daily automation cutover

Only after multiple dry runs pass should the daily editorial automation be re-enabled through the new pipeline.

Until then, preserve the currently working production branch and keep the direct-publish task disabled.

## How to propose a better architecture

Before replacing this plan, document:

- CURRENT ASSUMPTION
- PROPOSED ALTERNATIVE
- WHY BETTER
- TRADEOFF
- MIGRATION COST
- RISK
- HARRYTONE PRESERVATION
- EDITORIAL AUTHORSHIP PRESERVATION
- DAILY VARIATION PRESERVATION
- ACCESSIBILITY IMPACT
- ARCHIVE INTEGRITY IMPACT
- PRIVACY IMPACT
- QA/DEPLOYMENT IMPACT

Then recommend adoption or rejection.