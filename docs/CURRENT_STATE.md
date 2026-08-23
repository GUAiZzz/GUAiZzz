# Culture & Taste Daily — Current State

Last audited: 2026-08-23 22:51 Asia/Shanghai.

## Audit verdict

- GitHub Pages as a static publication target: **GO**.
- Direct daily writes into the deployed `gh-pages` branch: **BLOCKED**.
- Migration project: **REVISE**, then continue incrementally.

## Repositories

### `GUAiZzz/GUAiZzz`

This is an older public GitHub Pages/blog repository. The current Culture & Taste experiment lives on the production `gh-pages` branch under `culture-taste-daily/`.

Known production structure includes:

- `culture-taste-daily/index.html`
- `culture-taste-daily/2026-08-20/`
- `culture-taste-daily/2026-08-21/`

The live archive migration is provisional, not production-complete.

Known migration defect: 8/20 and 8/21 use a small loader `index.html` that fetches `.txt` fragments with JavaScript and reconstructs archived HTML at runtime. If JavaScript fails, the article is not exposed. This violates the production contract's progressive-enhancement requirement.

The archive homepage is manually hardcoded rather than generated from issue manifests.

`codex/culture-taste-system-v3` is the safe migration workspace. `audit-baseline-v1` is a documentation/schema-only child branch used to resolve audit blockers. Neither branch is production.

### `GUAiZzz/harry-tone`

Private repository. This is the canonical HarryTone source of truth.

The previously reported missing `references/social-content.md` has been restored. The current latest verified `main` commit at this audit is:

`13cd6b7046bd81be396810d2923f3a5dc818e93f` — `Restore missing HarryTone social content guide`.

The current canonical set includes `SKILL.md`, `agents/openai.yaml`, and all eight recovered reference files. Do not describe a pinned snapshot as "latest" without checking the canonical repository at runtime.

## Historical publication artifacts known outside production GitHub

At minimum:

- 2026-08-20: original full HarryTone HTML exists.
- 2026-08-21: original `HARRYTONE_LATEST` full HTML exists, plus ZIP and desktop/mobile preview artifacts.
- 2026-08-22: a PDF exists; original HTML/source must be searched for before reconstruction.

Migration must preserve editorial text, art direction, color world, typography behavior, image behavior, pacing, and source links. Do not normalize historical issues into one template.

## Current automation

The ChatGPT automation `Culture & Taste GitHub Daily` previously targeted direct writes to `GUAiZzz/GUAiZzz:gh-pages/culture-taste-daily/`.

Because the audit classifies direct daily auto-publish as BLOCKED, that automation was **paused on 2026-08-23 before the next scheduled run**. It must remain paused until the automation gate in `docs/ARCHITECTURE_DECISIONS.md` is satisfied.

The old prompt remains useful as editorial-generation input, but its direct-publish instructions are not an approved deployment path.

## Production-contract authority

Two representations currently exist:

1. the Library document `Culture & Taste Daily — Production Prompt v2` / `Pasted markdown.md`;
2. the repository migration document `docs/PRODUCTION_CONTRACT_V2.md`.

They are not a byte-for-byte mirror. The Library v2 remains the canonical historical v2 for the existing system. The repository document is a migration adaptation/draft successor and must not silently override it. Before production cutover, the two must be deliberately reconciled into a new version-controlled successor (recommended `PRODUCTION_CONTRACT_V3.md`). After v3 approval, the repository version becomes canonical and the Library v2 becomes a frozen historical reference. See `docs/ARCHITECTURE_DECISIONS.md`.

## Three design teachers

1. Codrops / Webzibition — authorship, world-building, concept concentration.
2. Behance UI/UX — dramatic presentation and intentional viewing sequence.
3. Mobbin — real product grammar, usability, and interaction clarity.

They are complementary teachers, not templates.

## Privacy boundary

The production contract requires a private source ledger and also requires visible reader-facing Sources & Dates. These are not the same artifact.

A public GitHub Pages/source repository must never contain private research notes, internal QA scaffolding, internal scoring, or unpublished editorial inference. Public issue manifests contain only publishable provenance/metadata. The private source ledger stays outside the public repository. Schemas for both sides may be version-controlled publicly; private ledger instances may not.

## Explicitly not verified / not complete

- 8/20 and 8/21 are not PASS-grade historical web issues yet.
- Original visual assets are not fully restored in migrated web versions.
- 8/22 has not been migrated into a verified web issue.
- No independent deterministic CI currently enforces the production contract.
- No dedicated `culture-taste-daily` source repository has been cut over.
- No approved Pages build-artifact workflow exists yet.
- Daily production automation is paused pending the new gate.

## Safety rule

Do not modify `culture-taste-daily/`, add deployment workflows, merge to `gh-pages`, or alter the live site from the audit-baseline PR. The next change must remain documentation/schema-only and reversible.