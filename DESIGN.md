---
name: glanceable
description: Answer-first research view. Clean layout, warm colors, one highlighter.
colors:
  ground:  "#fffaf5"   # page, warm white
  surface: "#ffffff"   # reading pane, chips
  tint:    "#fff3e8"   # passage panel, selected and hovered rows, mode pill
  ink:     "#2b2320"   # text
  muted:   "#6f625b"   # all secondary text (4.5:1 or better)
  faint:   "#cdbdb2"   # non-text only: bar segment
  rule:    "#f0e4da"   # hairlines, chip borders
  accent:  "#c4432b"   # coral: links, focus, the open button, wordmark
  marker:  "#ffd6a3"   # peach highlighter, quoted evidence only
  ok:      "#2e7d50"
  warn:    "#a95c00"
  bad:     "#c83a26"
  na:      "#8f8178"
dark:
  ground: "#1a1512"
  surface: "#221c18"
  tint: "#2e2621"
  ink: "#f5ece4"
  muted: "#bcada3"
  rule: "#372d27"
  accent: "#ff8a6b"
  accent-ink: "#1a1512"
  marker: "#f5b97a"
  marker-ink: "#1a1512"
typography:
  answer:       { family: Fraunces, axes: "SOFT 100, WONK 0, opsz 96", size: "clamp(28px,3.6vw,40px)", weight: 600, line-height: 1.14, tracking: -0.02em }
  answer-long:  { size: "clamp(24px,2.8vw,30px)", line-height: 1.22 }   # over 120 characters
  section:      { family: Fraunces, axes: "SOFT 100", size: 19px, weight: 600 }
  source-title: { family: Fraunces, axes: "SOFT 100", size: 21px, weight: 600, line-height: 1.25 }
  wordmark:     { family: Fraunces, axes: "SOFT 100", size: 19px, weight: 600 }
  claim:        { family: Geist, size: 16px, weight: 400, line-height: 1.5, measure: 68ch }
  passage:      { family: Geist, size: 16px, weight: 400, line-height: 1.7 }
  body:         { family: Geist, size: 15px, weight: 400, line-height: 1.6 }
  meta:         { family: Geist, size: 13px, weight: 500 }
  data:         { family: Geist Mono, size: 12px, weight: 400, numerals: tabular }  # [n], domains, counts
spacing: [4, 8, 12, 16, 24, 32, 48]
rounded: { sm: 8px, md: 12px, lg: 20px, full: 9999px }
shadow: "0 1px 2px rgba(110,60,30,.05), 0 12px 32px rgba(110,60,30,.08)"   # reading pane only
motion: { fast: 150ms, sheet: 240ms, ease: "cubic-bezier(.16,1,.3,1)" }
---

## Atmosphere

Clean layout, warm feeling. The structure is a calm list with lots of space, like a good product tool. The warmth comes from the cream ground, a soft rounded serif for headings, coral for actions and a peach highlighter for evidence.

## Rules

- Order never changes: question, answer (h1), confidence and answer sources, verification bar, then Why, Watch out, Didn't hold up, Next step.
- Fraunces (soft) is for headings only: answer, section titles, source title, wordmark. Everything else is Geist.
- Mono is for data only: source keys, domains, counts.
- The peach marker appears only on quoted source text and under the selected claim.
- Coral is for interaction: links, focus, the open button. Never use it for status.
- Status is shown three ways at once: glyph shape, color and a word. Status colors are never used for selection or decoration.
- Rows are a flat list separated by hairlines. Hover and selection fill the row with the tint, with rounded corners. No cards around rows.
- The reading pane is the one raised object: white, 20px radius, soft warm shadow, no border.
- One motion moment: the highlighter sweeps across the quote when a passage opens. Reduced motion shows it at once.

## Components

- **Row:** 24px glyph disc, then the claim. 12px padding. The whole row is clickable; source chips sit above that click area.
- **Source chip:** pill, white, 1px rule border, mono 12px, 28px tall with a 44px hit area.
- **Passage:** tint panel, 12px radius, 16px/18px padding. The quote is marked, with one sentence of context either side.
- **Verdict:** glyph, status word in the status color at 600, note in muted. No box.
- **Open button:** solid coral pill, 44px tall.
- **Mobile sheet (under 960px):** 80vh, 20px top radius, 30% ink scrim, 36x4 handle. Focus moves to the sheet heading on open and returns to the opener on close. A "Sources" pill in the top bar opens the source list.

## Responsive

- 960px and up: two columns (answer 1fr, pane 420px), 48px gap.
- Under 960px: one column; the pane becomes a bottom sheet.
- 16px side gutter at every width. No horizontal scroll at 390px.

## Don't

- Don't recolor large text on hover. Use a marker underline.
- Don't put text below 4.5:1 contrast. Coral text uses the darker #c4432b, never a lighter coral.
- Don't add a second accent color.
- Don't put rows in cards or add more shadows.
- Don't use em-dashes in interface copy.
- Don't make external requests beyond Google Fonts, and always keep system fallbacks.
