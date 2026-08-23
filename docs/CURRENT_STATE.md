# Culture & Taste Daily — Current State

Last audited: 2026-08-23.

## Repositories

### `GUAiZzz/GUAiZzz`

This is an older GitHub Pages / blog repository. The current Culture & Taste experiment lives on the `gh-pages` branch under:

`culture-taste-daily/`

Known current structure:

- `culture-taste-daily/index.html`
- `culture-taste-daily/2026-08-20/`
- `culture-taste-daily/2026-08-21/`

The live archive migration should be considered provisional, not production-complete.

Known migration defect: 8/20 and 8/21 currently expose a small loader `index.html` that fetches several `.txt` fragments with JavaScript and reconstructs the archived HTML at runtime. If JavaScript fails, the article is not exposed. This conflicts with the publication requirement that the full reading path, sources, and article order remain accessible without JavaScript.

The current archive homepage is also manually hardcoded rather than generated from issue manifests.

### `GUAiZzz/harry-tone`

Private repository. This is the canonical HarryTone source of truth.

Known current contents:

- `SKILL.md`
- `agents/openai.yaml`
- `references/source-guide.md`
- `references/anti-ai-patterns.md`
- `references/chat-writing.md`
- `references/portable-prompt.md`
- `references/product-rules.md`
- `references/rewriting.md`
- `references/work-writing.md`

Known mismatch: the recovered original HarryTone archive also contained `references/social-content.md`. That file is currently missing from the GitHub mirror. Do not call the mirror complete until this mismatch is resolved.

## Historical publication artifacts known to exist outside this branch

At minimum:

- 2026-08-20: original full HarryTone HTML exists in the user's file library.
- 2026-08-21: original `HARRYTONE_LATEST` full HTML exists, plus ZIP and desktop/mobile preview artifacts.
- 2026-08-22: a 4.37 MB PDF is known to exist; do not assume the original HTML is unavailable until searched for explicitly.

Do not redesign these old issues during migration. Preserve their editorial text, art direction, color world, typography behavior, image behavior, visual pacing, and source links. Fix only reliability/accessibility/migration defects unless a redesign is explicitly requested.

## Current automation

A daily ChatGPT automation exists for Culture & Taste Daily. It has been updated to require the latest HarryTone repository files before publishing and to publish to GitHub Pages rather than `chatgpt.site`.

However, the automation currently still writes toward the deployed `gh-pages` model. The target architecture should separate generation from deterministic validation and deployment.

## Current production-contract location

The canonical current contract is `Culture & Taste Daily — Production Prompt v2`, currently stored in the user's file library as a Markdown file rather than version-controlled alongside the website.

This is a source-of-truth risk. The full contract should be copied into version control before production cutover.

## Three design teachers

The established references are:

1. Codrops / Webzibition — authorship, world-building, concept concentration.
   - https://tympanus.net/codrops/webzibition/page/2/
2. Behance UI/UX — dramatic presentation and intentional viewing sequence.
   - https://www.behance.net/galleries/ui-ux/ui-ux
3. Mobbin — real product grammar, usability, and interaction clarity.
   - https://mobbin.com/discover/apps/web/latest

They are complementary teachers, not templates to imitate.

## What is explicitly NOT verified yet

- The existing migrated 8/20 and 8/21 pages do not qualify as PASS-grade historical web issues yet.
- Embedded original image assets are not fully restored in the migrated web versions.
- 8/22 has not yet been migrated into a verified web issue.
- The current deployed Culture & Taste setup does not yet have independent deterministic CI enforcing the production contract.
- A dedicated `culture-taste-daily` repository has not yet been created from this environment.

## Safety rule for this branch

`codex/culture-taste-system-v3` is a planning and migration workspace. Do not merge it into `gh-pages` or use it to change the live site until the migration has a test plan, rollback plan, and verified deployment path.