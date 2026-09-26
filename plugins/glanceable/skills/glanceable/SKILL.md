---
name: glanceable
description: Turns research into an answer-first view you can read at a glance - answer, reasons, risks, next step - where every line opens the exact passage from its source and is marked supported, partly supported, not supported or unchecked. Use when the user asks a research question and wants the answer, or pastes/uploads a long research report (ChatGPT, Gemini, Perplexity, Claude deep research) and wants it made glanceable, summarised or checked.
---

# Glanceable

Turn research into a one-screen answer. Each line links to the exact passage it came from, so the user can check it in one click.

You are a formatting and checking layer. The research comes from this platform's own search or from a report the user supplies. Never invent sources, quotes or facts.

## Pick the mode

- **Research mode:** the user asks a question and there is no report. Research it with your normal web search/browse tools, then build the view.
- **Verify mode:** the user pastes or uploads a report. Don't research the topic again. Restructure the report and check its citations.

If you can't tell what decision or question the answer should serve, ask one short plain-text question first. Otherwise start.

## Steps

1. **Find the answer.** State it in one or two sentences, and make it a direct recommendation or finding, not a topic summary. In verify mode, take it from the report. If the report doesn't reach one, give the best-supported answer and say the report was inconclusive.
2. **Pick the claims that matter.** Choose 3-5 reasons behind the answer and 1-3 risks: what could make it wrong, or when it wouldn't apply. Leave out background and filler.
3. **Get the evidence.** For each claim, open its source (in verify mode, the URL the report cites) and copy:
   - `quote`: the exact sentence that bears on the claim, character for character.
   - `context`: that sentence plus about one sentence either side, character for character. The quote must appear exactly inside the context.
4. **Check each claim separately.** Re-read the quote against the claim as a skeptic, not as the claim's author:
   - `supported`: the quote clearly says it.
   - `partial`: the quote says something weaker, narrower or older, and a `note` explains the gap.
   - `unsupported`: the source doesn't say it or says the opposite, and a `note` explains.
   - `unverified`: the source couldn't be opened (paywall, block, dead link). Leave `quote` and `context` empty and say why in `note`.
   Never mark a claim `supported` from memory or from the report's own wording.
5. **Re-check the answer.** Base the answer only on `supported` and `partial` claims. If dropping the `unsupported` ones changes the answer, change it and say so in a risk. Set `confidence` to `high`, `medium` or `low`.
6. **Write one next step.** Make it concrete and doable today.
7. **Render** (see Output).

## Output

1. Read `template.html` from this skill's folder.
2. Replace only the JSON inside `<script type="application/json" id="glance-data">` with your data. Keep everything else byte for byte.
3. Show the result:
   - **Claude:** publish it as an HTML artifact.
   - **ChatGPT / Gemini:** open it in Canvas as HTML and preview it.
   - **CLI tools:** save it as `glance.html` and tell the user to open it.
4. If you can't render HTML, or can't read the template, output the text version below instead.

Keep the reply around the view to one line. Don't repeat the card in chat.

### Data format

```json
{
  "question": "The user's question, in one line",
  "answer": { "text": "1-2 sentence answer", "confidence": "high|medium|low",
              "cites": [{ "source": "s1", "quote": "exact sentence" }] },
  "reasons":    [{ "text": "claim", "status": "supported|partial|unsupported|unverified",
                   "note": "only when not supported", "cites": [{ "source": "s1", "quote": "exact sentence" }] }],
  "risks":      [ same shape as reasons ],
  "next_steps": [{ "text": "one concrete action" }],
  "sources": { "s1": { "title": "Page title", "site": "domain.com", "url": "https://...",
                       "context": "exact passage containing every quote cited from this source" } },
  "report": "verify mode only: the original report text, optional"
}
```

JSON rules:
- Only `http`/`https` URLs.
- Put the source's most relevant sentences in `context`. If several claims cite the same source from different places, join those passages with " … ".
- Escape quotes and newlines properly, and write every `</` as `<\/` so no text can close the script tag.

### Text version (fallback)

```
**Answer:** <answer> (confidence: <level>)

**Why**
✅ <claim> — [1]
⚠️ <claim> — [2] (<note>)
❌ <claim> — [2] (<note>)

**Watch out**
❔ <claim> — [3] (couldn't check: <reason>)

**Next step:** <action>

[1] <title> — <url>
    > "<quote>"
```

## Rules

- Quote exactly, never paraphrase inside `quote` or `context`.
- Never mark `supported` without a quote you actually read in the source.
- Never hide an `unsupported` claim. It stays visible, crossed out, so the user sees what the report got wrong.
- Keep each line to one sentence where possible. The user should get the answer in under 30 seconds.
- Stay neutral on disputed topics: if good sources disagree, say so in a risk and cite both sides.
