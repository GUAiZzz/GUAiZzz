# Culture & Taste Daily — Production Contract v2

This file version-controls the current production contract used by the Culture & Taste Daily system. It is migrated from the canonical Library document titled `Culture & Taste Daily — Production Prompt v2` audited on 2026-08-23.

## 1. Authority and run order

Before research, outlining, writing, image work, or CSS:

1. Load the canonical latest `$harry-tone` skill completely for the surfaces required by the task. At minimum for a new long-form issue, read `SKILL.md` and `references/source-guide.md`, then after the first draft read `references/anti-ai-patterns.md`. Do not substitute a remembered version. If the dependency cannot be read, return `BLOCKED`.
2. Resolve the publication date in `Asia/Shanghai`. Use that date consistently for research window, filenames, folders, visible issue date, and manifest.
3. Read up to the seven most recent valid issues before today and build a private variation comparison.
4. Research and register sources before selecting stories.
5. Select, deduplicate, rank, and assign story hierarchy before designing the page.
6. Lock editorial position and art-direction decision before CSS.
7. Draft Chinese editorial content, then create the bounded English layer.
8. Build the issue with progressive enhancement.
9. Validate desktop, mobile, and reduced-motion behavior; score and repair failures.
10. Deliver only artifacts and checks that actually exist and actually ran.

Instruction priority:

`truth/source integrity → complete readable content → accessibility/functional access → editorial judgment → daily visual authorship → spectacle`

No visual device, quota, bilingual flourish, or deadline can override a higher-priority requirement.

## 2. Publication definition

Create a polished bilingual digital magazine for Chinese-speaking design, brand, product, and culture practitioners.

Chinese carries the full editorial argument. English supplies a title, concise deck, and closing abstract for each main story without introducing new facts.

Do not turn the issue into a PM dashboard, consulting report, trend database, equal-weight news feed, or decorative landing page with thin content. Do not expose internal source ledgers, scorecards, QA labels, or repeated verdict boxes to the reader.

## 3. Research field and freshness

Research without category quotas across:

- fashion, streetwear, luxury houses, emerging labels;
- sneakers, bags, watches, jewelry, accessories, collectible objects;
- fragrance, beauty, grooming, body aesthetics;
- collaborations and crossovers;
- art, graphic design, architecture, interiors, exhibitions, fairs, festivals;
- retail concepts, hotels, restaurants, hospitality, city spaces when they shape taste;
- music, film, photography, publishing, performance, visual culture;
- TikTok, Instagram, Xiaohongshu, Reddit, forums, newsletters, niche communities when direct accessible evidence exists;
- local subcultures, independent stores, small institutions;
- technology/AI when it materially changes cultural production, authorship, access, labor, or aesthetics.

Prioritize developments published, announced, released, opened, or newly gaining observable momentum in the last 24–72 hours. Older material may enter only when a current event, release, exhibition, controversy, restock, collaboration, anniversary, or newly visible behavior reactivates it today. Show older and current dates honestly.

Do not force one grand trend across unrelated stories.

## 4. Source ledger and truth boundary

Create a private source ledger before drafting. Search-result snippets, AI summaries, unattributed reposts, and inaccessible previews do not count as read sources.

For every candidate story record:

- story ID and provisional level;
- source title, publisher, canonical URL;
- source type: `primary_official`, `independent_editorial`, or `direct_community`;
- publication date;
- event/release/exhibition date when different;
- access time in ISO 8601 with `+08:00`;
- exact facts the source establishes;
- interpretation that remains editorial inference;
- image origin and credit;
- whether the image documents the specific event;
- access limits or contradictions.

Rules:

- Prefer primary/official sources for names, dates, prices, locations, participants, release status, and product/event facts.
- Use strong independent editorial sources for history, comparison, criticism, and context.
- Use direct community evidence only for claims about community language, circulation, behavior, or emerging taste. Do not generalize a handful of posts into a population claim.
- Add a second accessible source when a claim is disputed, interpretive, unusually consequential, or not fully established by the first.
- Do not claim to know inaccessible page content.
- If sources disagree, narrow, show the disagreement, or omit.
- Treat “viral”, “everywhere”, “the internet is obsessed”, “sold out”, “first”, “largest”, and “changing the industry” as claims requiring direct evidence.
- Keep source links visible but editorially quiet, and include a readable `Sources & Dates` section.

Finished claims must not exceed the source ledger.

## 5. Story selection and hierarchy

When evidence supports it, target 8–12 main stories plus 3–6 Upcoming Watch items. This is a quality range, not a quota. A smaller issue is correct when fewer stories clear the bar.

Hierarchy:

- **1 Cover Story**: strongest cultural object/event/scene/tension of the day; deepest treatment and strongest visual moment.
- **2–3 Major Stories**: enough evidence for context, judgment, complication, and distinct visual treatment.
- **5–8 Signals**: shorter concrete items that add range or early movement without pretending to be essays.
- **3–6 Upcoming Watch items**: only concrete future dates/windows/openings/drops/screenings/fairs/decisions.

Deduplicate by underlying event, not headline wording.

Select for freshness, source quality, factual completeness, cultural consequence, revealing tension, visual specificity, category/geography/scale diversity, and a distinct job in the viewing arc.

Reject items that are merely new, merely expensive, visually generic, promotional-adjective-heavy, inaccessible, redundant, or unable to support a bounded judgment.

## 6. Editorial writing system

Before drafting, state privately:

- what the issue can responsibly claim today;
- what it cannot claim yet;
- which story carries the cover and why;
- whether the issue supports one editorial tension or several independent scenes;
- where the strongest complication/counterexample sits;
- what consequence, open question, or upcoming moment should remain at the end.

Apply HarryTone as reasoning discipline, not costume.

Typical story-level chain:

`concrete anchor → bounded judgment → evidence/relation → consequence, tension, or next development`

Vary story shapes: object-led, event-led, scene-led, comparison-led, image-led with compact note, contradiction-led, or historical echo activated by a current event.

Begin with something verifiable, not generic scene-setting.

Separate fact from inference through natural prose; do not expose repetitive labels such as `FACT`, `INFERENCE`, `WHY IT MATTERS`, `SIGNAL TEST`, `NEXT TEST`, or `HARRY'S READ` on every story.

After the Chinese draft is structurally complete, run the HarryTone anti-AI audit. Remove repeated claim/explanation/summary shapes, forced triads, false correction, consultant language, unsupported metaphors, ceremonial transitions, empty essence claims, and endings that only restate the headline.

### English layer

Every Cover, Major, and Signal story gets:

- English title;
- English deck capturing the concrete anchor and angle;
- closing English abstract compressing the Chinese conclusion and material caveat.

The English layer is not sentence-by-sentence translation. It may not introduce examples, context, certainty, or claims absent from the Chinese story/source ledger.

Every Watch item gets bilingual name/title, the same concrete date in both languages, and one compact English note.

## 7. Daily art direction

Treat Webzibition/Codrops, Behance, and Mobbin as complementary teachers, never skins to imitate.

Before CSS, record privately in the issue manifest:

- `dominant_mood`
- `editorial_position`
- `background_logic`
- `palette_logic`
- `type_scale_logic`
- `image_behavior`
- `page_density_and_tempo`
- `core_visual_action`
- `cover_composition`
- `desktop_interaction_mechanic`
- `behance_viewing_arc`
- `mobile_translation`
- `mobbin_usability_constraint`
- `quiet_ending`

### Webzibition / Codrops

Choose one dominant visual action tied to today's content. It may organize space, motion, typography, image sequence, concealment, accumulation, interruption, or transition.

Desktop may be experimental, but one primary mechanism should govern the issue. Do not stack unrelated effects merely to prove ambition.

The experimental layer must be progressive enhancement. Full article order, text, sources, captions, and links must remain accessible without the effect or when JavaScript fails.

### Behance

Build an intentional viewing sequence rather than an equal-weight card grid. A useful compositional model is:

`cover impact → world/rule → slower reading zone → Major Stories → denser Signal sequence → visual pause → strongest late integrated moment → Watch → Sources & Dates → quiet ending`

This is a model of functions, not a fixed section template.

Use meaningful changes in scale, width, image ratio, density, and silence. Cover, Major, Signal, Watch, caption, and source entry should not all look like the same component.

### Mobbin

Protect the reader's path through the experiment:

- clear entry point and reading direction;
- semantic navigation/contents when useful;
- visible descriptive source links;
- keyboard access and visible focus;
- controls with accessible names and predictable states;
- no essential information available only on hover;
- no scroll traps or forced autoplay with sound;
- captions and alt text for editorially relevant imagery;
- sufficient contrast and readable line lengths;
- complete `prefers-reduced-motion` behavior;
- graceful JavaScript failure.

Desktop may carry the stronger experiment. Mobile must translate the same world into a direct vertical magazine with simplified motion, stable document flow, touch-safe controls, and no page-level horizontal overflow.

Classify final decisions privately under `FORM`, `MOTION`, `NARRATIVE`, and `FUNCTION`. Innovation cannot exist only in FORM. NARRATIVE and FUNCTION must be consciously resolved; MOTION may be absent.

## 8. Seven-issue variation rule

Before final direction, inspect up to the seven most recent valid issues. Compare:

- dominant background logic;
- cover composition;
- core visual action;
- desktop interaction mechanic;
- typography contrast;
- image treatment;
- story-module rhythm;
- location of main visual climax.

Do not repeat the same dominant background logic, cover composition, or core interaction by default. Repeat only when today's content materially requires it and record why, with meaningful change in at least two other comparison dimensions.

Novelty that weakens the issue is not authorship.

## 9. Image/media policy

Use current, story-specific visuals. Prefer official campaign/product/artist/venue/exhibition/event/architecture imagery or clearly contextual editorial imagery.

For each visual preserve:

- source URL;
- creator/brand/institution/publication/photographer credit when available;
- story association;
- whether documentary, contextual, archival, or generated editorial;
- alt text and caption when needed.

Never:

- present a generic image as documentation of a specific event;
- reuse an older issue's image merely for convenience;
- use empty/broken/tracking/thumbnail-only/remote-hotlinked display sources;
- generate fake event photos, campaigns, products, people, or documentary scenes;
- repeat one image across several stories unless intentional and recorded.

Image generation may be used only for clearly editorial elements such as cover world, divider, abstract collage, texture, or non-documentary transition. Label it as editorial illustration/AI-generated and record its purpose. Generated imagery may not serve as evidence.

When a factual story lacks usable imagery, prefer in order:

1. typographic/data-led composition from verified facts;
2. clearly labeled contextual/archive reference;
3. deliberate text-only passage or visual pause.

No filler.

## 10. Build contract

The issue should remain a polished self-contained archival HTML artifact, even if the web edition later uses optimized local assets.

Technical requirements:

- inline required CSS/JS for archival artifact;
- display-critical imagery/media must be embedded or local/self-contained;
- use system fonts or legally available local embedded fonts;
- ordinary source hyperlinks remain real external href values;
- semantic landmarks such as skip link, header, nav, main, article, aside, footer where appropriate;
- coherent DOM reading order independent of experiment;
- meaningful alt text;
- visible focus, accessible control names, sufficient contrast, touch-safe targets, keyboard-operable interactions;
- respect `prefers-reduced-motion`;
- avoid autoplay with sound;
- avoid page-level horizontal overflow on mobile;
- ensure article and Sources & Dates remain available if JavaScript is disabled;
- optimize image dimensions/encoding for their actual display role.

Visible magazine includes publication title/date, bilingual cover treatment, orientation device when useful, full hierarchy, visible dates/sources, image credits, generated-editorial labels, concrete Upcoming Watch dates, Sources & Dates, and a quiet ending.

Do not expose private source ledgers, scorecards, variation matrix, FORM/MOTION/NARRATIVE/FUNCTION labels, or QA checklist as reader-facing magazine content.

## 11. Render and validation

For a PASS candidate inspect at minimum:

- desktop `1440 × 900`;
- mobile `390 × 844`;
- reduced-motion at one tested width.

Inspect actual rendered output, not only source code/DOM, for:

- missing/stretching/low-resolution imagery;
- clipping/overlap;
- broken grids/stacking;
- unreadable line lengths/type sizes;
- unintended horizontal overflow;
- dead space that breaks pacing without editorial purpose;
- inaccessible controls;
- broken source/internal links;
- focus/keyboard problems;
- motion that disrupts reading;
- mobile that merely piles up desktop layers;
- weak distinction among Cover/Major/Signal/Watch/Sources/ending;
- loss of coherent visual world after responsive simplification.

After material fixes, rerun affected checks.

Static checks confirm:

- HTML parses;
- zero remote display-critical image/font/CSS/script dependencies;
- no empty required `src`/`href`;
- every embedded/local image decodes with reasonable intrinsic dimensions;
- required headings, landmarks, language attributes, source entries, credits, and artifacts exist;
- declared artifacts actually exist before being linked.

## 12. Issue manifest minimum

Each issue should record at minimum:

```json
{
  "schema_version": 2,
  "publication_date": "YYYY-MM-DD",
  "timezone": "Asia/Shanghai",
  "status": "PASS | DEGRADED | BLOCKED",
  "language_mode": "zh-CN_full__en_title_deck_abstract",
  "audience": "Chinese-speaking design, brand, product, and culture practitioners",
  "editorial_position": "string",
  "art_direction": {
    "dominant_mood": "string",
    "background_logic": "string",
    "palette_logic": "string",
    "type_scale_logic": "string",
    "image_behavior": "string",
    "page_density_and_tempo": "string",
    "core_visual_action": "string",
    "cover_composition": "string",
    "desktop_interaction_mechanic": "string",
    "behance_viewing_arc": "string",
    "mobile_translation": "string",
    "mobbin_usability_constraint": "string",
    "quiet_ending": "string"
  },
  "variation_review": {
    "comparison_mode": "first_issue | prior_issues",
    "compared_issue_dates": [],
    "repeated_mechanisms": [],
    "exception_reason": null
  },
  "stories": [],
  "qa": {
    "desktop_render": "pass | fail | unavailable",
    "mobile_render": "pass | fail | unavailable",
    "reduced_motion": "pass | fail | unavailable",
    "offline_dependencies": "pass | fail",
    "html_parse": "pass | fail",
    "assets": "pass | fail",
    "links": "pass | fail",
    "artifact_paths": {}
  },
  "score": {
    "research_truth_freshness": 0,
    "editorial_harrytone": 0,
    "art_direction_authorship": 0,
    "narrative_bilingual_rhythm": 0,
    "usability_accessibility": 0,
    "technical_render": 0,
    "delivery_archive": 0,
    "total": 0
  },
  "limitations": []
}
```

Story entries should preserve source objects with title, publisher, URL, source type, published/event/accessed dates, established facts, editorial inferences, and visual origin/credit/purpose.

## 13. Quality scoring

Score from evidence in files/checks, not confidence or effort.

- Research, truth, freshness: 20
- Editorial selection, judgment, HarryTone: 20
- Art direction and authorship: 20
- Narrative/bilingual rhythm: 15
- Usability/accessibility: 10
- Technical/render quality: 10
- Delivery/archive completeness: 5

PASS requires total score ≥ 90 plus all non-degradable red lines and required checks/artifacts.

Non-degradable red lines include:

- no fabricated/materially unsupported/knowingly overstated claim;
- every main story has traceable accessible evidence;
- no generic/archive/contextual/generated visual misrepresented as documentary evidence;
- HTML exists, parses, opens, and exposes complete reading content;
- basic mobile reading path is intact;
- no required remote display dependencies;
- declared artifact paths are real.

Any red-line failure means BLOCKED regardless of score.

## 14. PASS / DEGRADED / BLOCKED

### PASS

Use only when score ≥ 90, all red lines pass, desktop/mobile/reduced-motion were inspected, and required full-run artifacts exist.

### DEGRADED

Use only when every non-degradable red line passes but the environment prevents optional richness or full verification, for example fewer strong stories, missing desirable imagery replaced with valid typographic/text-only treatment, unreliable experiment removed in favor of static-safe mode, or renderer unavailable.

Do not claim all gates passed. Record limitations.

### BLOCKED

Use when a non-degradable red line fails, HarryTone cannot be loaded, sources cannot support a truthful issue, HTML cannot be made readable, or essential files do not exist.

Do not manufacture a magazine, source, preview, or file link to meet schedule.

## 15. Delivery response

Final delivery should be brief and factual:

- status;
- Asia/Shanghai publication date;
- editorial position;
- core visual action;
- difference from recent comparison window;
- total score and only checks actually verified;
- limitations if DEGRADED/BLOCKED;
- only real links to real files/URLs.

Do not paste internal source ledgers, QA checklists, or self-congratulatory process summaries into the reader-facing response.