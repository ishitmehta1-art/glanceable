---
name: glanceable
description: Answer-first research view. Cool sage paper, a serif answer, one highlighter.
colors:
  ground:  "#eef1ee"   # page
  surface: "#fbfcfa"   # reading pane
  raised:  "#ffffff"   # chips, selected row
  ink:     "#15201b"   # text
  muted:   "#5a665f"   # all secondary text (4.5:1 or better)
  faint:   "#8a958f"   # non-text only: bar segment, disabled
  rule:    "#d9dfdb"   # hairlines
  accent:  "#0b6b5e"   # links, focus ring, "Open at this passage"
  marker:  "#e4f36b"   # quoted evidence only
  ok:      "#1c7a45"
  warn:    "#a35b00"
  bad:     "#b42318"
  na:      "#6b7570"
dark:
  ground: "#0e1311"
  surface: "#151b18"
  raised: "#1b221f"
  ink: "#e5ece8"
  muted: "#a3aea8"
  rule: "#29332e"
  accent: "#5cc8b4"
  marker: "#c3d64a"
  marker-ink: "#10170c"
typography:
  answer:      { family: Newsreader, size: "clamp(26px,3.6vw,36px)", weight: 500, line-height: 1.18, tracking: -0.015em }
  answer-long: { size: "clamp(22px,2.6vw,28px)", line-height: 1.25 }   # over 120 characters
  passage:     { family: Newsreader, size: 18px, weight: 400, line-height: 1.62 }
  source-title: { family: Newsreader, size: 21px, weight: 500, line-height: 1.25 }
  claim:       { family: Geist, size: 16px, weight: 400, line-height: 1.5, measure: 68ch }
  body:        { family: Geist, size: 15px, weight: 400, line-height: 1.55 }
  meta:        { family: Geist, size: 13px, weight: 500 }
  data:        { family: Geist Mono, size: 12px, weight: 400, numerals: tabular }  # [n], domains, counts
spacing: [4, 8, 12, 16, 24, 32, 48]
rounded: { sm: 4px, md: 8px, lg: 12px, full: 9999px }
motion: { fast: 150ms, sheet: 240ms, ease: "cubic-bezier(.16,1,.3,1)" }
---

## Atmosphere

A reading desk, not a dashboard. The answer is the headline and the evidence is one click away. The highlighter is the only saturated color on the page.

## Rules

- Order never changes: question, answer (h1), confidence and answer sources, verification bar, then Why, Watch out, Didn't hold up, Next step.
- The marker appears only on quoted source text and on the selected claim's underline.
- The accent is for interaction (links, focus, the open action). Never use it for status.
- Status is shown three ways at once: glyph shape, color and a word. Status colors are never used for selection or decoration.
- No eyebrow labels and no uppercase tracking. Mono is for data only: source keys, domains, counts.
- Depth comes from surface color. There is one shadow, on the mobile sheet only, tinted with ink.
- Glyphs are inline SVG, 14px, stroke 2, currentColor, in a 20px tinted disc.
- One motion moment: the highlighter sweeps across the quote when a passage opens. Reduced motion shows it at once.

## Components

- **Row:** 20px glyph column, then the claim. 12px padding, hairline below. The whole row is clickable; source chips sit above that click area. Selected row: raised background, 1px rule inset, marker underline on the claim.
- **Source chip:** data type, raised background, 1px rule, small radius, 28px tall with a 44px hit area.
- **Reading pane:** surface color, large radius, 24px padding, sticky 24px from the top on desktop. Order: source title and site, claim, passage, verdict, open link.
- **Verdict:** glyph, status word in the status color at 600, note in muted. No tinted box.
- **Mobile sheet (under 960px):** 78vh, large top radius, 28% ink scrim, 36x4 handle. Focus moves to the sheet heading on open and returns to the opener on close. A "Sources" button in the top bar opens the source list.

## Responsive

- 960px and up: two columns (answer 1fr, pane 420px), 40px gap.
- Under 960px: one column; the pane becomes a bottom sheet.
- 16px side gutter at every width. No horizontal scroll at 390px.

## Don't

- Don't recolor large text on hover. Use an underline.
- Don't put text below 4.5:1 contrast.
- Don't add a second accent color.
- Don't use em-dashes in interface copy.
- Don't make external requests beyond Google Fonts, and always keep system fallbacks.
