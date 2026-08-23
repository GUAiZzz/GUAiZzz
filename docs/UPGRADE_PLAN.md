# Culture & Taste Daily — Upgrade Plan

## Goal

Turn the current migration prototype into a reliable, version-controlled publishing system that preserves HarryTone, daily visual authorship, historical archive integrity, and fail-closed deployment.

This plan is the strongest current proposal, not permanent doctrine. A materially better architecture is welcome if it preserves or improves truth, editorial authorship, accessibility, archive integrity, reliability, and maintainability.

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
  PRODUCTION_CONTRACT_V2.md
  ARCHITECTURE.md
  DECISION_LOG.md

skill/
  HARRYTONE_VERSION.json

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

The missing original `references/social-content.md` should also be restored/resolved so the skill mirror is complete.

Do not claim “latest HarryTone” unless the actual commit/version can be identified.

## Production contract

Move the canonical `Culture & Taste Daily — Production Prompt v2` into version control. Do not leave the production system dependent on chat memory or a file-library-only artifact.

Future changes should be versioned and logged instead of silently overwriting the contract.

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
- manifest;
- QA report;
- desktop/mobile previews.

### Web edition

- optimized local assets;
- smaller pages suitable for GitHub Pages;
- same editorial world;
- no remote display-critical dependencies;
- no JavaScript requirement for reading.

Before adopting this split, calculate current and projected storage cost and document the tradeoff.

## Manifest-driven archive

Do not manually hardcode new issues into the homepage.

Every issue should own `issue-manifest.json` with the publication date, editorial position, art direction, source ledger, visual metadata, HarryTone version, variation review, QA results, status, and limitations.

Generate from manifests where appropriate:

- homepage latest issue;
- archive;
- RSS;
- sitemap;
- OpenGraph/social metadata.

The homepage can be relatively stable. Individual issue art direction must remain independent.

## Responsibility split

### AI/editorial layer

Responsible for:

- research;
- source ledger;
- selection and deduplication;
- bounded editorial judgment;
- HarryTone writing;
- art direction;
- issue generation;
- repair after failed deterministic checks.

### Deterministic engineering layer

Responsible for:

- parsing;
- schema validation;
- asset validation;
- link validation;
- accessibility checks;
- rendering/screenshots;
- archive/RSS/sitemap build;
- deployment;
- post-deploy smoke tests.

The same AI that created the issue must not be the only authority certifying technical validity.

## Fail-closed publishing

Desired pipeline:

```text
scheduled editorial generation
→ candidate committed to source branch
→ deterministic GitHub Actions validation
→ build
→ PASS?
    no  → previous production remains live
    yes → deploy GitHub Pages
→ post-deploy smoke test
```

A broken daily issue must not corrupt or replace yesterday's good site.

Use concurrency protection so overlapping jobs cannot race or partially update production.

## Minimum deterministic validation

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

- keyboard access;
- visible focus;
- meaningful alt text;
- sufficient contrast;
- useful landmarks;
- axe or equivalent automated checks where practical.

### Render

At minimum:

- 1440 × 900 desktop;
- 390 × 844 mobile;
- reduced-motion variant.

Inspect for overflow, clipping, overlap, blank media, unreadable type, broken stacking, touch issues, and whether mobile is an intentional translation rather than desktop collapse.

### Publication integrity

- manifest schema valid;
- directory/date match;
- HarryTone version recorded;
- issue does not overwrite another date;
- archive generation deterministic.

## Status semantics

Keep exactly:

- PASS
- DEGRADED
- BLOCKED

PASS means required checks actually ran and passed.

DEGRADED means the publication remains truthful and readable but optional richness or full verification was unavailable.

BLOCKED means a non-degradable red line failed.

Do not convert BLOCKED into PASS because of schedule pressure.

## Implementation order

### Phase 0 — Audit

Map every current file, dependency, historical artifact, automation, and deployment path. Produce an updated `CURRENT_STATE.md`.

### Phase 1 — Source of truth

- Create/verify `AGENTS.md`.
- Version the production contract.
- Version the North Star/design-teacher brief.
- Restore/resolve missing HarryTone `social-content.md`.
- Record HarryTone commit dependency.

### Phase 2 — Repository architecture

Create or prepare a dedicated Culture & Taste source repository. Separate source from deployed output.

### Phase 3 — Historical migration

Restore 8/20 and 8/21 accurately. Investigate 8/22 original source before reconstruction. Eliminate JS-required article loading.

### Phase 4 — Manifest-driven publication

Add issue manifests. Generate homepage/archive automatically. Add RSS/sitemap where useful.

### Phase 5 — Deterministic QA

Implement HTML, assets, links, accessibility, render, and manifest validation.

### Phase 6 — Deployment

GitHub Actions deploys only validated builds. Add concurrency protection and rollback-safe behavior.

### Phase 7 — Post-deploy verification

Smoke-test the actual public URL and critical assets/internal links.

### Phase 8 — Daily automation cutover

Only after multiple dry runs pass should the daily editorial automation publish through the new pipeline.

Until then, preserve the currently working production branch.

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
- QA/DEPLOYMENT IMPACT

Then recommend adoption or rejection.