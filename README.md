# Revelations of Divine Love — An Illustrated Translation

A fresh translation of Julian of Norwich's *Revelations of Divine Love* (Long Text)
from the Middle English, set in Art Nouveau styling and built to a Kindle EPUB.
Styleguide-driven, Markdown → EPUB, made slowly and with care.

Translated and illustrated by **Mark Oriel**. Julian's original text is public domain;
the translation, introduction, notes, and illustrations are © Mark Oriel.

---

## How this repository works

The work is **styleguide-driven** and proceeds chapter by chapter, one commit per
chapter. A few standing rules govern everything:

- **Translate only from `SOURCE.md`** (Middle English). Never from `REFERENCE.md`
  (Warrack 1901) and never from memory.
- **`STYLEGUIDE.md` is the controlling intelligence** — tone, rhythm, register, the
  load-bearing term glossary, and a hard "must not do" list.
- **Surface non-obvious choices** rather than deciding silently — ambiguous terms,
  syntactic clarifications, textual variants all get logged.
- **The styleguide and glossary are living.** When a ruling changes, earlier chapters
  are flagged for re-review.

## The files

| File / dir | Role |
|---|---|
| `STYLEGUIDE.md` | The controlling intelligence — read first, every session. |
| `SOURCE-short.md` | **Short Text** Middle English (Amherst MS / Holloway). **Current focus.** |
| `SOURCE.md` | **Long Text** Middle English (Sloane 2499 / Crampton). Deferred to phase 2. |
| `REFERENCE.md` | Grace Warrack (1901), Long Text. Comparison only — never translated from. |
| `GLOSSARY.md` | Ruling translations for load-bearing terms. Living. |
| `NOTES.md` | Textual decisions, variant log, ambiguous-term instances, open questions. |
| `TASKS.md` | The modular build plan (Modules 0–8). |
| `translations/` | One file per chapter: `NN_short-title.md`. |
| `images/` | Export-ready illustration assets (high-res masters kept elsewhere). |
| `book/` | Front/back matter, `metadata.yaml`, `style.css`. |
| `fonts/` | Fonts licensed for embedding (body serif + Art Nouveau display). |
| `build/` | EPUB build artefacts (gitignored). |

## Building the ebook

The build is a single Pandoc invocation (see `TASKS.md` Module 6). In outline:

```bash
./build.sh        # assembles front matter + chapters + back matter → build/revelations.epub
```

Then validate with **epubcheck** and review in **Kindle Previewer** (Module 7).

## Current state

Module 0 (repository setup) is complete. The project is now producing the **Short Text
first** — Julian's earlier (c. 1373) account — from the Amherst manuscript via Holloway's
transcription, captured into `SOURCE-short.md` and translated under `translations/short/`.
The Long Text (Sloane 2499) is deferred to a second phase; its imported Chapter 1 stands.
See `TASKS.md` for the full plan and `NOTES.md` for standing editorial rulings.
