# TASKS.md
## *Revelations of Divine Love* — Illustrated Translation
### A Modular Build Plan for Claude Code

This document carries the project from raw Middle English to a finished, sellable
Kindle ebook. It is **modular**: each module has a goal, a set of tasks, and a
definition of done. Work them in order, but each is self-contained enough to pause
and resume.

The companion files are `STYLEGUIDE.md` (the controlling intelligence),
`SOURCE.md` (Middle English, the only text translated from), `REFERENCE.md`
(Warrack 1901, comparison only), `GLOSSARY.md` and `NOTES.md` (both grow as you go).

---

## Conventions for Claude Code

Before any translation work, read `STYLEGUIDE.md` and `GLOSSARY.md` into context.
These govern every decision. A few standing rules:

- **Translate only from `SOURCE.md`.** Never from `REFERENCE.md`, never from memory.
- **Surface, don't bury.** When a translation choice is non-obvious (an ambiguous
  *kinde* / *homely*, a syntactic clarification, a textual variant), flag it to Mark
  rather than deciding silently.
- **The styleguide is living.** If a ruling changes mid-project, say so explicitly so
  earlier chapters can be revisited.
- **Commit per chapter.** One chapter, one commit (`feat: translate ch. NN`). This
  makes the project's history legible and reversible.
- **Base text is Sloane 2499; the Long Text has 86 chapters.**

---

## Module 0 — Repository Setup

**Goal:** A clean, well-structured repo ready to work in.

- [ ] Confirm the existing files are in place: `STYLEGUIDE.md`, `SOURCE.md`,
      `REFERENCE.md`
- [ ] Create `GLOSSARY.md` (seed it from the term table in STYLEGUIDE §6)
- [ ] Create `NOTES.md` (empty; for textual decisions and variant logging)
- [ ] Create `translations/` directory
- [ ] Create `images/` directory (for illustration assets)
- [ ] Create `build/` directory (gitignored; build artefacts)
- [ ] Create `book/` directory (front matter, back matter, metadata, stylesheet)
- [ ] Write a short `README.md` orienting any future collaborator (or future Mark)
- [ ] Add a `.gitignore` (ignore `build/`, OS cruft, editor files)
- [ ] `git init` and initial commit

**Done when:** the structure below exists and is committed.

```
/
├── STYLEGUIDE.md
├── SOURCE.md
├── REFERENCE.md
├── GLOSSARY.md
├── NOTES.md
├── README.md
├── translations/
├── images/
├── book/
│   ├── 00_titlepage.md
│   ├── 01_copyright.md
│   ├── 02_introduction.md
│   ├── 03_note_on_the_text.md
│   ├── metadata.yaml
│   └── style.css
└── build/            (gitignored)
```

---

## Module 1 — Source Import

**Goal:** All 86 chapters of the Middle English Long Text, faithfully captured in
`SOURCE.md`.

This is deliberately unhurried. Import is not mechanical copying; it is the first act
of editorial care.

- [ ] Settle the **scribal-headings decision** (STYLEGUIDE §2 / NOTES): translate the
      chapter summaries, set them apart as a historical layer, or omit. Record the
      ruling in `NOTES.md` before importing, since it shapes how you capture them.
- [ ] Source each chapter's Middle English from the TEAMS Middle English Texts (METS)
      edition. Import chapter by chapter, not in one bulk paste.
- [ ] Preserve original spelling and scribal inconsistency. Do **not** silently
      modernise (no expanding *þe* to *the*, no regularising *kinde*/*kynde*).
- [ ] Normalise only whitespace and obvious OCR artefacts; log anything ambiguous.
- [ ] Use a consistent chapter delimiter so later scripts can split reliably
      (e.g. `## Chapter N`).
- [ ] Note any special characters present: thorn (þ), eth (ð), yogh (ȝ), ash (æ).
      Ensure the file is saved UTF-8. These matter again at build/QA time.

**Done when:** `SOURCE.md` contains all 86 chapters, UTF-8, spelling intact, with a
recorded ruling on the scribal headings.

---

## Module 2 — Translation Loop (the core)

**Goal:** A faithful, literary translation of every chapter, produced by the
iterative ritual below.

**Per-chapter ritual.** For each chapter N:

1. Load `STYLEGUIDE.md` and current `GLOSSARY.md` into context.
2. Read chapter N's Middle English from `SOURCE.md`.
3. Draft the translation, observing register, rhythm (§4), vocabulary (§5), and the
   term rulings (§6).
4. Self-check against the §8 "must not do" list — no propositional flattening, no
   resolving paradox, no invented connective tissue, *alle shalle be wele* preserved.
5. Write to `translations/NN_short-title.md` in the format prescribed in STYLEGUIDE §9.
6. **Surface to Mark:** new term decisions, ambiguous *kinde*/*homely*/*sensualite*
   cases, any syntactic clarification made, any textual variant chosen (Sloane vs
   Paris).
7. Mark reviews against source and styleguide.
8. Amendments go either to the translation or to `STYLEGUIDE.md` / `GLOSSARY.md`.
9. If a styleguide or glossary ruling changed, **flag earlier chapters for
   re-review.**
10. Commit (`feat: translate ch. NN`).

**Tasks:**

- [ ] Establish the ritual on Chapter 1 as a test case; confirm the loop and the
      output format feel right before scaling.
- [ ] Work through chapters in order, in sustainable batches (2–3 per session).
- [ ] Keep `GLOSSARY.md` updated the moment a new term ruling is set.
- [ ] Keep `NOTES.md` updated with every variant and clarification.

**Done when:** all 86 chapters exist in `translations/`, each reviewed, with glossary
and notes current.

---

## Module 3 — Consistency Pass

**Goal:** The whole translation speaks with one voice and honours every glossary
ruling.

Claude Code is well suited to this sweep.

- [ ] For each load-bearing term in `GLOSSARY.md`, search the Middle English in
      `SOURCE.md` for its occurrences, then check the corresponding translated
      passages render it per the ruling. Flag divergences.
- [ ] Write a small consistency script (grep-based is fine) that reports, per glossary
      term, every rendering used across `translations/`. Review the report for drift.
- [ ] Check `oneing`, *homely* → intimacy, *goostly* → spiritual, and the motherhood
      vocabulary specifically; these are the highest-risk for inconsistency.
- [ ] Re-read the transitions between revelations for tonal continuity.
- [ ] Resolve every flag, amending translation or glossary as needed.

**Done when:** the consistency report is clean and every flag is resolved.

---

## Module 4 — Front & Back Matter

**Goal:** The editorial apparatus that turns a translation into an *edition*.

- [ ] **Title page** (`book/00_titlepage.md`): title, the word **"Illustrated"** in
      the title or subtitle (KDP requirement for illustrated public-domain editions),
      "Julian of Norwich", "Translated and illustrated by [your name / pen name]".
      Decide here whether to publish under your own name or **Mark Oriel** — a
      devotional translation may want either, and your established author identity is
      a consideration.
- [ ] **Copyright page** (`book/01_copyright.md`) with the public-domain disclaimer:
      *"This translation, together with all introductions, notes, and illustrations,
      is © [Your name] [Year]. Julian of Norwich's original text is in the public
      domain."*
- [ ] **Translator's introduction** (`book/02_introduction.md`): who Julian was, the
      manuscript tradition, your translation philosophy in brief. This is genuine
      value-add and part of what differentiates the edition for KDP.
- [ ] **Note on the text** (`book/03_note_on_the_text.md`): Sloane 2499 as base,
      Paris as variant, your handling of the scribal headings.
- [ ] **Table of contents**: generated at build time (Module 6), but decide depth now
      (chapter level is right for 86 chapters).
- [ ] Optional back matter: a short afterword, a note on the illustrations, a
      bibliography for further reading.

**Done when:** all front/back matter drafted, reviewed, and saved in `book/`.

---

## Module 5 — Illustration Integration

**Goal:** Original Art Nouveau devotional illustrations, properly placed and
prepared, meeting KDP's illustrated-edition bar.

- [ ] Confirm the count: **at least 10 original illustrations** (KDP's threshold for
      an illustrated edition). Plan more if the design calls for it.
- [ ] Decide the illustration scheme: illuminated initial capitals at chapter openings,
      full-page plates at the major revelations, decorative borders, or a combination.
      The scribal-heading layer (Module 1) can be designed as illuminated incipits.
- [ ] Establish a naming convention (`images/ch07_plate.png`,
      `images/initial_A.png`).
- [ ] Place illustration markers in the relevant chapter files using standard image
      syntax, so the build picks them up in order.
- [ ] Write **meaningful alt text** for every image (accessibility, and KDP expects
      it).
- [ ] Prepare images at Kindle-appropriate resolution and format (high-resolution
      PNG/JPEG; check current KDP image guidelines at build time). Keep masters in a
      separate high-res store; the repo holds the export-ready versions.
- [ ] Decide cover art separately — the cover is uploaded to KDP independently of the
      interior and has its own spec.

**Done when:** ≥10 original illustrations are placed with alt text, plus a cover
plan.

---

## Module 6 — Ebook Build (Markdown → EPUB)

**Goal:** A clean, validating EPUB3 — the format to take into Kindle. Minimal
toolchain, in keeping with a no-build sensibility: essentially one tool (Pandoc) plus
a stylesheet.

- [ ] Install Pandoc (single dependency for the conversion).
- [ ] Write `book/metadata.yaml` (title, language `en`, rights, publisher, date,
      cover image reference). Handle author/translator attribution on the title page
      and again in the KDP listing (Module 8).
- [ ] Write `book/style.css` for the typography:
  - Body: a readable serif licensed for embedding.
  - Display/initials: an Art Nouveau face for titles and drop capitals — **only a
    font licensed for embedding.** Verify the licence before embedding.
  - Use the Kindle-supported CSS subset; avoid layout that won't reflow.
- [ ] Write a `build.sh` that assembles front matter, all chapters in order, and back
      matter into one EPUB. A working starting point:

```bash
#!/usr/bin/env bash
set -euo pipefail
mkdir -p build

pandoc \
  book/metadata.yaml \
  book/00_titlepage.md \
  book/01_copyright.md \
  book/02_introduction.md \
  book/03_note_on_the_text.md \
  translations/*.md \
  --toc --toc-depth=1 \
  --css=book/style.css \
  --epub-embed-font='fonts/*.otf' \
  --resource-path=.:images \
  -o build/revelations.epub

echo "Built build/revelations.epub"
```

- [ ] Confirm chapter files sort correctly (zero-padded `NN_` prefixes).
- [ ] Run the build; produce `build/revelations.epub`.

**Done when:** `build.sh` produces an EPUB containing all matter, in order, styled.

---

## Module 7 — Validation & QA

**Goal:** An EPUB that is technically valid and renders correctly on Kindle devices.

- [ ] Run **epubcheck** (open-source EPUB validator) against the build; fix every
      error.
- [ ] Open the EPUB in **Kindle Previewer** (Amazon's free desktop QA app; note it is
      a GUI tool, not Linux-CLI-friendly). Check across phone, tablet, and e-ink
      renderings.
- [ ] Verify: table of contents navigates correctly; chapter breaks land cleanly;
      illustrations display at the right size and position; drop capitals render;
      embedded fonts are honoured (with graceful fallback).
- [ ] **Special-character check:** if any Middle English is retained in the final
      edition (epigraphs, the scribal headings, a decorative *alle shalle be wele*),
      confirm thorn (þ), yogh (ȝ), eth (ð), and ash (æ) render in the chosen fonts and
      survive the build. Substitute or embed a covering font if not.
- [ ] Proofread the rendered text end to end — rendering can surface errors the source
      view hides.

**Done when:** epubcheck passes and the book reads correctly across Previewer's
device profiles.

---

## Module 8 — KDP Publishing Preparation

**Goal:** Everything assembled and verified so the listing can be created. 

> **Note:** the steps that touch your KDP account — creating the listing, accepting
> terms, uploading, setting price, and publishing — are yours to perform directly.
> This module prepares the materials and gives you the checklist; it does not perform
> the account, upload, or payment actions.

- [ ] **Verify current KDP requirements** at the point of publishing. KDP's accepted
      formats, illustrated-edition rules, public-domain policy, and UI change over
      time; confirm the specifics rather than relying on this plan.
- [ ] Confirm the **differentiation** case is strong: original translation, original
      introduction and notes, ≥10 original illustrations. This is what justifies a
      paid listing alongside any free Julian texts.
- [ ] Confirm **"Illustrated"** appears in the title/subtitle.
- [ ] Prepare the **cover** to KDP's current cover spec (separate from the interior
      EPUB).
- [ ] Draft the **book description** (the sales copy), **categories**, and
      **keywords**.
- [ ] Prepare author/translator attribution for the listing (Julian of Norwich as
      author; you as translator/contributor).
- [ ] Have the **public-domain declaration** ready for KDP's content form.
- [ ] **UK note:** the original Middle English is safely public domain everywhere; the
      value you are selling is your new translation and illustrations, which are your
      copyright. No third-party-rights issue arises from the source text itself.
- [ ] Final pre-flight: re-run `build.sh`, re-run epubcheck, one last Previewer pass.

**Done when:** the validated EPUB, cover, metadata, and copy are all prepared and the
checklist above is complete — ready for you to create and publish the listing.

---

## Suggested Order & Pacing

Modules 0–1 are setup and import (careful but finite). Module 2 is the long heart of
the work — at 2–3 chapters per session with review between, the 86 chapters are a
season's project, not a sprint. Modules 3–8 are consolidation and production, and move
quickly once the translation is sound. Illustration (Module 5) can proceed in parallel
with later translation if you prefer.

## Environment & Dependencies

- **Pandoc** — Markdown → EPUB conversion (the one real build dependency)
- **epubcheck** — EPUB validation
- **Kindle Previewer** — Amazon's QA app (desktop GUI; Mac/Windows)
- **git** — version control, one commit per chapter
- **Fonts licensed for embedding** — body serif + an Art Nouveau display face

---

*This plan is modular and living. Revise it as the work teaches you what it needs.*
