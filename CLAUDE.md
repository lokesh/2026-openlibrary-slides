# CLAUDE.md

Slide deck for the Open Library 2026 talk, "Tools for Participation". A single
self-contained reveal.js deck in `index.html`. Nothing to build or install.

## Layout

- `index.html` — the whole deck: CSS theme in `<head>`, one `<section>` per slide, `Reveal.initialize` at the bottom.
- `reveal.min.js`, `reveal.min.css`, `notes.min.js` — vendored reveal.js and its speaker-notes plugin. Do not edit.
- `img/` — media used by slides (`catboy.mp4` + poster; `covers/` holds the 90 vendored Open Library cover JPEGs for the opener).
- `README.md` — just the repo name.

## Viewing

Open `index.html` directly in a browser, or serve the folder:

```bash
python3 -m http.server 8000
```

Press `S` in the deck for the speaker-notes window. Slides use `hash:true`, so `#/3` jumps to slide 3.

## Source material

The site this deck describes lives in the sibling repo `../openlibrary`
(openlibrary.org, Python/web.py + Jinja, Vue/Lit frontend). When a slide needs
a fact about a feature, route, or component, look it up there rather than
guessing. Its own `CLAUDE.md` and `docs/ai-coding-guide.md` explain the layout.
Do not modify that repo from this project.

## Deck conventions

- Deck is 1280x720, `transition:'fade'`, slide numbers shown as `c/t`.
- Each slide is a `<section>` with a numbered HTML comment (`<!-- 3 · MOBILE UX & DESIGN -->`). Keep comments in sync when adding or reordering slides.
- Every slide uses `data-background-color="#f1ede0"` (the lighter cream). No alternation; new slides use the same value.
- Every slide has an `<aside class="notes">` with the spoken script. Write notes in the presenter's voice (Mek), conversational, a short paragraph.
- Colors come from the CSS variables in `:root` (Open Library cream/ink/blue palette sampled from the brand banner). Use the variables, don't add new hex colors.
- Type: Literata (weight 700, `font-optical-sizing:none` so it stays the text cut at display sizes) for headings, Schibsted Grotesk for body, JetBrains Mono for kickers, tags, and paths. All loaded from Google Fonts. Cards have no colored top border.
- Reusable blocks already defined: `.principles`/`.principle` (3-up pillars), `.units`/`.unit` (3-up cards), `.feats`/`.feat` (wrapping feature cards), `.two` (two-column demo/detail), `.kicker`, `.step` (chapter pill like "1 / 3 · Better UX"), `.sub`, `.path`. Reuse these before adding new CSS.
- Section headings, pillars, and feature cards carry an inline Lucide icon (`<svg class="ic ic-<name>">`), not an emoji. Use the same icon openlibrary.org uses for that feature where one exists (its set is `../openlibrary/static/icons/src/lucide/`; gallery at openlibrary.org/developers/design/icons); otherwise pick a plain Lucide glyph. Paste the 24-grid path geometry inline; `.ic` handles size, stroke, and color.
- Chapter structure: opener (floating cover field, `section.every`) → title → What's New (3 pillars) → chapter slides tagged `1 / 3`, `2 / 3`, `3 / 3` → closing slide. New feature slides belong under the matching chapter and its `.step` pill.
