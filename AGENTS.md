# Culture & Taste Daily — Codex Instructions

This branch is a safe migration workspace. Do not treat it as the live production branch.

## Mandatory reading order

Before changing Culture & Taste Daily code or editorial behavior:

1. Read `docs/NORTH_STAR.md`.
2. Read `docs/CURRENT_STATE.md`.
3. Read `docs/UPGRADE_PLAN.md`.
4. Read `docs/PRODUCTION_CONTRACT_V2.md` when present; until then, do not weaken any production rules summarized in the docs above.
5. Read the canonical private repository `GUAiZzz/harry-tone`, especially `SKILL.md`, `references/source-guide.md`, and for post-draft review `references/anti-ai-patterns.md`.

## Source-of-truth rules

- `GUAiZzz/harry-tone` is the canonical HarryTone repository. Do not create an independent drifting copy of the skill.
- HarryTone governs judgment, reasoning, truth boundaries, speaking position, voice, and anti-AI revision.
- Culture & Taste visual/editorial publication behavior is an additional system layered on HarryTone. Do not pretend the writing skill alone contains the visual system.
- Historical issues are evidence and archive objects. Do not normalize them into one fixed visual template.

## Production safety

- Do not write directly to the live `gh-pages` branch while working on the migration.
- Prefer source → deterministic validation → build → deploy.
- A failed validation must leave the previous production site untouched.
- Never require JavaScript merely to expose the article text, sources, or basic reading path.
- Mobile is a deliberate translation, not mechanical stacking of desktop layers.
- Do not deploy an issue just because the schedule says it is time.
- PASS / DEGRADED / BLOCKED labels must reflect checks that actually ran.

## Design behavior

- Do not make tomorrow by cloning yesterday and recoloring it.
- Read up to the previous seven valid issues before choosing art direction.
- Webzibition/Codrops teaches authorship and world-building.
- Behance UI/UX teaches viewing sequence and dramatic presentation.
- Mobbin teaches product grammar and usability constraints.
- These are teachers, not visual templates.

## Permission to improve the system

The documented architecture is the strongest current proposal, not permanent doctrine. If you find a materially better architecture, do not silently replace the system. First document:

- current assumption;
- proposed alternative;
- why it is better;
- tradeoffs and migration cost;
- risks;
- how it preserves HarryTone, editorial authorship, daily variation, accessibility, archive integrity, deterministic QA, and fail-closed deployment.

Then recommend whether to adopt it.

## First-task behavior

Before a large implementation, return a compact audit with:

- CURRENT STATE
- CONFIRMED FACTS
- MISSING INPUTS
- ARCHITECTURE RISKS
- PROPOSED TARGET
- MIGRATION PLAN
- FILES TO CREATE/MODIFY
- TEST PLAN
- ROLLBACK PLAN
- BETTER ALTERNATIVES / OPEN QUESTIONS

Prefer incremental, reversible changes over a single rewrite.