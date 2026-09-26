# glanceable

Deep research gives you a 20-page report. You wanted the answer.

**glanceable** turns AI research into a single screen: the answer, the reasons behind it, the risks, and one next step. Click any line and the exact passage from its source opens beside it, highlighted. Every claim is marked:

| | Meaning |
|---|---|
| ✓ | Supported: the source says it |
| ! | Partly supported: the source says something weaker or narrower |
| ✕ | Not supported: the source doesn't say it (shown crossed out, never hidden) |
| ? | Couldn't check: the source wouldn't open |

## Why

- Deep research reports often run 10–45 pages, and the answer is buried somewhere inside.
- Studies of AI research tools in 2025–26 found that a large share of cited claims aren't actually backed by the source they cite. The link works; the claim doesn't match.

glanceable doesn't do the research. Your AI platform does. glanceable reshapes the result and shows you whether each claim holds up.

## Two ways to use it

**Ask a question** (research mode)
> "Should we use PostgreSQL or MongoDB for our order-tracking app?"

The AI researches it with its normal web search, then builds the glanceable view.

**Paste a report** (verify mode)
> "Make this glanceable:" + a deep research report from ChatGPT, Gemini, Perplexity or Claude

The AI pulls out the answer, checks each claim against the source it cites, and builds the view.

## See it

[`examples/verify-demo.html`](examples/verify-demo.html) is a real test result. A report with three planted mistakes went in; glanceable caught all three and flagged the source it couldn't open. Download the file and open it in a browser, or see [`examples/`](examples/) for details.

## Where it works

| Platform | How it shows |
|---|---|
| Claude (claude.ai, Claude Code) | Interactive view as an artifact |
| ChatGPT (plans with Skills) | Interactive view in Canvas |
| Gemini (app with Skills, Gemini CLI) | Interactive view in Canvas, or a saved HTML file in the CLI |
| Codex and other CLI tools | Saved `glance.html` file |
| Anywhere else | Text version with ✅ ⚠️ ❌ markers |

Canvas support in ChatGPT and Gemini hasn't been fully tested yet. Reports welcome.

## Install

**Claude Code**
```
/plugin marketplace add ishitmehta1-art/glanceable
/plugin install glanceable@glanceable
```

**Claude.ai, ChatGPT, Gemini, Perplexity:** download `glanceable.zip` from the [latest release](https://github.com/ishitmehta1-art/glanceable/releases/latest) and upload it as a skill in your platform's settings.

**Codex / Gemini CLI (manual):**
```bash
git clone https://github.com/ishitmehta1-art/glanceable.git
cp -r glanceable/plugins/glanceable/skills/glanceable ~/.agents/skills/
```

## How it's built

```
plugins/glanceable/skills/glanceable/
├── SKILL.md        instructions: the two modes, how to check claims, output format
└── template.html   the answer view; the AI fills in one JSON block
```

The visual rules (colors, type, spacing, components) live in [`DESIGN.md`](DESIGN.md). They're informed by [impeccable](https://github.com/pbakaus/impeccable), [taste-skill](https://github.com/leonxlnx/taste-skill) and [awesome-design-md](https://github.com/voltagent/awesome-design-md).

`template.html` has no external scripts and makes no network calls, so it runs inside sandboxed canvases. Its only outside request is Google Fonts (Newsreader, Geist, Geist Mono); where a platform blocks that, it falls back to system fonts. Open it directly in a browser to see a demo with example data.

## Status

Early version (0.3.0). Known limits:
- Paywalled or bot-blocked sources can't be checked; they're marked "Couldn't check".
- Checking quality depends on the AI model doing the checking.
- "View original" jumps to the highlighted sentence in Chrome and Edge. Other browsers open the page top.

## Credits

The exact-quote checking approach is inspired by [receipts](https://github.com/JamesWeatherhead/receipts) (MIT), which checks citations in academic manuscripts.

## License

MIT, see [LICENSE](LICENSE).
