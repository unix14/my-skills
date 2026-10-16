# ELI5

> Explains hard things in plain language — real analogies, no jargon, and no talking down.

| | |
|---|---|
| **Slug** | `eli5` |
| **Category** | Learning & Explanation |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

"Explain it simply" usually produces one of two failures: an explanation that is
still full of jargon, or a cutesy one that is simple because it is wrong.

This skill targets a curious adult with no background — not a literal
five-year-old — and builds the explanation in a fixed order. One sentence under
20 words that stands alone. Then an analogy that maps the actual **mechanism**
rather than the vibe, *and* a note on where that analogy breaks, because a
borrowed intuition that's wrong is worse than none. Then why anyone cares, then
how it actually works in 3–5 plain steps, and only at the very end the proper
jargon — once you already understand the idea and can recognise the term in the
wild.

It simplifies by **leaving things out, never by making things up**, and says
which important thing it left out and when that omission will matter. It bans
"simply", "just", and "obviously", which tell a confused reader the confusion is
their fault. Under 250 words by default, then it offers the next layer down
rather than lecturing.

### Use it when

- You hit a concept in a doc, paper, or code review that everyone else seems to already know.
- You need to explain your work to someone outside your field — a client, an exec, a relative.
- A textbook or man page explanation is technically complete and completely unhelpful.
- You are writing onboarding docs and need the intuition before the detail.

### Don't use it when

- You need precision for implementation — a simplified model will mislead you at the edges.
- You need the rigorous version: the proof, the spec, the RFC. Read the source.
- You already understand it and want to be tested rather than taught — use [`quiz-me`](../quiz-me/).

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/eli5/skill.md
```

---

## Install

Pure Markdown with no dependencies, so this runs in any assistant that lets you
set standing instructions — only the destination changes. Exact paths for Claude
Code, Cursor, Copilot, Codex, Gemini and the rest are in
[**docs/COMPATIBILITY.md**](../../docs/COMPATIBILITY.md). The three common routes:

### 1. Paste it (any chat interface)

Open [`skill.md`](./skill.md), copy everything below the YAML frontmatter, and
paste it into ChatGPT's Custom GPT instructions, a Claude Project's custom
instructions, a Gemini Gem, or just your first message. The frontmatter is
harmless if you paste it too.

### 2. Let your agent install it

Paste this into Claude Code, Cursor, Copilot CLI, Gemini CLI, Codex, or any
agent that can fetch a URL and write a file:

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/eli5/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/eli5/SKILL.md  (the file must be SKILL.md)
   - Cursor          .cursor/rules/eli5.mdc  (.md is ignored there; replace the
                     frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/eli5.instructions.md  (frontmatter
                     `applyTo: "**"`), or append to .github/copilot-instructions.md
   - Codex, Zed, Aider, Warp, Windsurf, Jules, goose, opencode, Gemini CLI and
     the other AGENTS.md readers: append it to AGENTS.md under its own heading
   - anything else   your own equivalent — and tell me where you put it

3. Keep the instructions verbatim. Do not summarise or "improve" them, and do
   not drop the `description` — that is how most tools decide when to load it.

4. Confirm it is registered, then tell me the phrase that triggers it.
```

Use `~/.claude/skills/` rather than `.claude/skills/` to install it globally.

### 3. Shell

```bash
mkdir -p .claude/skills/eli5
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/eli5/skill.md \
  -o .claude/skills/eli5/SKILL.md
```

---

## Credits & Origin

This skill packages public plain-language practice and a well-known teaching
technique. Specific lineage:

- **The "explain like I'm five" convention** — [r/explainlikeimfive](https://www.reddit.com/r/explainlikeimfive/),
  the community that established the format and its "layperson-friendly, not literally childish" norm.
- **Explain it plainly to find the gaps in your own understanding** — the
  [Feynman technique](https://fs.blog/feynman-technique/), after Richard Feynman's approach to teaching physics.
- **Constrained vocabulary as a forcing function for clarity** — Randall Munroe's
  [*Up Goer Five*](https://xkcd.com/1133/) and the book *Thing Explainer*.
- **Short sentences, active voice, defined terms, no undefined acronyms** — the
  [federal plain language guidelines](https://www.plainlanguage.gov/guidelines/).

All credit for these ideas belongs to their respective authors, who retain all
rights to their own work and wording. `skill.md` contains no copied text from
the sources above — it is an independent prompt that operationalises publicly
documented patterns. If you are one of these authors and would like the
attribution changed or this skill removed, open an issue and it will be handled.
