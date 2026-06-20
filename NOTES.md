# NOTES.md
## Textual Decisions, Variant Log & Open Questions

The running record of editorial decisions for the translation. Every textual variant
chosen (Sloane vs Paris), every syntactic clarification, every ambiguous-term ruling,
and every unresolved question lands here. Glossary rulings live in `GLOSSARY.md`; this
file holds the *reasoning* and the *instances*.

Dates are absolute. New entries go at the top of each section.

---

## Standing Rulings

### Project sequencing: Long Text first — *ruled 2026-06-20*
- The project produces the **Long Text first** (Sloane 2499). An earlier 2026-06-20
  decision to do the **Short Text first** was **reverted** the same day: no clean,
  freely available Middle English Short Text could be found (Crampton/METS carries only
  excerpts of it; Holloway's Amherst page is a diplomatic transcription embedded in an
  essay), whereas the **Long Text is cleanly obtainable** from Crampton (see sourcing
  below). The Short Text is **shelved indefinitely** pending a sourceable clean text; if
  revived it becomes a later phase. The `SOURCE-short.md` stub and `translations/short/`
  were removed (recoverable from git history).

### Base text
- **Sloane 2499** (British Library) is the base text. The Paris manuscript
  (BnF fonds anglais 40) is consulted only where readings meaningfully diverge; any
  such divergence chosen is logged under *Textual Variants* below.
- Working Middle English source: **TEAMS Middle English Texts Series (METS)** edition —
  **Georgia Ronan Crampton, *The Shewings of Julian of Norwich* (1994)**, Sloane 2499
  base, hosted at metseditions.org. Imported chapter by chapter into `SOURCE.md` with
  spelling preserved. Print line-wraps are reflowed to running paragraphs; words and
  spelling are not altered.

### Letter-forms — *ruled 2026-06-16*
- **Ruling:** *Accept the Crampton edition as-is.* It uses **modern letter-forms** —
  thorn (þ), yogh (ȝ), and eth (ð) are already transcribed into modern letters (e.g.
  *thornys*, *ghostly*, *trowthe*). We do not attempt to restore manuscript
  orthography. Spelling is otherwise preserved exactly.
- **Consequence:** TASKS Module 1's thorn/yogh-preservation wording and STYLEGUIDE §2's
  "Glasscoe lineage" reference were corrected to match (both edited 2026-06-16). The
  Module 7 special-character check largely falls away unless such characters are
  reintroduced decoratively.

### Scribal chapter-summaries — *ruled 2026-06-16*
- **Ruling:** *Set apart as a historical layer.* The chapter-summaries in Sloane 2499
  are most likely an early scribe's work, not Julian's. They will be **translated but
  typographically distinguished** from Julian's own text — presented as a later
  editorial layer (candidate treatment: illuminated incipits, dovetailing with the
  Art Nouveau illustration scheme in Module 5).
- **Capture rule for import (Module 1):** in `SOURCE.md`, keep each scribal summary
  clearly marked as distinct from the chapter's running text (e.g. a blockquote or a
  labelled sub-heading) so the build can style it as a separate layer.

### Import workflow — *ruled 2026-06-20 (supersedes 2026-06-16)*
- **Mark copy-pastes the Crampton text, part by part, from metseditions.org.** The METS
  reader is a JavaScript app that does not yield reliable bulk text by page-fetching, so
  the earlier "per-chapter just-in-time fetch" approach is dropped. Instead Mark pastes
  whole parts (Part 1 = chs I–XXXIII, etc.); Claude files the **public-domain Middle
  English + scribal rubrics** into `SOURCE.md` (reflowing print line-wraps only).
- **Crampton's glosses and notes are a private aid, not repo content.** They are her
  1994 copyrighted scholarship; Claude *consults* them while drafting (they flag textual
  variants and difficult words) but does **not** commit them verbatim or republish them
  in the edition. Only Claude's own derived decisions are logged here.

### The Sloane incipit — *ruled 2026-06-16*
- The edition's opening — *"Revelations to one who could not read a letter. Anno Domini
  1373."* and *"A Particular of the Chapters."* — is **front matter, not part of
  Chapter 1.** Captured in `SOURCE.md` under *Front Matter — Incipit*; its translation
  will be placed in the book's front matter (candidate: an epigraph facing the title
  page).

### Chapter 1 as apparatus — *ruled 2026-06-16*
- Chapter 1 (the enumeration of the sixteen revelations) is a **scribal table of
  contents, not Julian's running prose.** It is treated as part of the historical /
  apparatus layer: set apart typographically (candidate: an illuminated opening list)
  and translated as apparatus rather than as devotional prose. Marked *Apparatus layer*
  in `SOURCE.md`.

### Attribution — *ruled 2026-06-16*
- Translation and edition published under the pen name **Mark Oriel**. Julian's
  original text is public domain; the translation, introduction, notes, and
  illustrations are © Mark Oriel.

---

## Textual Variants (Sloane vs Paris)

> Log each chosen variant: chapter, the Sloane reading, the Paris reading, which was
> taken, and why.

- **Ch. 1, "the Trinite":** Sloane reads *thee*; the edition reads *the Trinite* (Paris
  *precious* etc. nearby). We follow the edition's *Trinite* — the enumeration plainly
  intends the Trinity. (Surfaced by Crampton's note; logged, not copied.)

---

## Syntactic Clarifications

> Per STYLEGUIDE §4.1: where a genuinely confusing original structure was lightly
> clarified, record it here — chapter, the original, the rendering, the reason.

*(none yet)*

---

## Ambiguous-Term Instances

> Per-instance log for the context-dependent terms: *kinde/kindly*, *homely*,
> *failing*, *privy*, and any other case where the glossary ruling required a judgement
> call. Chapter, the source word, the rendering chosen, the rationale.

**Chapter 1 (apparatus list):**
- ***geveand* → "giving"** — *"reuland and geveand all things"* = "ruling and giving."
  Resolved: my earlier tentative "governing" was wrong; corrected to **"giving"**.
- ***privityes* → "secrets"** — *"wete His privityes"* = "know His secrets" (the *privy*
  ruling in its hidden sense).

**Proposed new glossary terms — awaiting Mark's ratification (not yet in `GLOSSARY.md`):**
- ***asseth* → "amends"** (Julian's satisfaction/reparation for sin; chosen over
  "satisfaction"/"reparation"). Supported as a load-bearing legal-ecclesiastical term.
- ***wele / wo* → "weal / woe"** (kept as the alliterative pair, over "well-being/woe").
- ***likeing* → "delight"** (over "pleasure"/"liking").

---

## Open Questions for Mark

> Anything surfaced during drafting that needs a ruling. Resolve and move to the
> appropriate section above once decided.

*(none yet — the Sloane incipit and Chapter-1-as-apparatus questions were resolved
2026-06-16; see Standing Rulings above.)*
