# Tahles

> The answer in the first line. Then only the result, the risks, and what is needed from you. Your decision goes last.

| | |
|---|---|
| **Slug** | `tahles` |
| **Category** | Communication & Tone |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

"Tahles" (תכל'ס) is Hebrew slang for "the bottom line". This skill makes the
model answer that way in every reply: the answer first, risks before actions,
one action per sentence, active voice, no idioms or jargon, and no detail until
you ask for it. If you must decide something, that decision is the last line.

Unlike [`tldr`](../tldr/), which compresses a document you hand it, `tahles`
changes how the model writes its own answers for the rest of the conversation.

### Use it when

- You want short, direct answers you can act on immediately.
- You are on a phone or between meetings and will not read a long reply.
- You need risks and decisions surfaced, not buried in explanation.

### Don't use it when

- You are learning a topic and want the reasoning — use [`eli5`](../eli5/) instead.
- You need to summarise a long text someone else wrote — use [`tldr`](../tldr/) instead.

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/tahles/skill.md
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
instructions, a Gemini Gem, or just your first message.

### 2. Let your agent install it

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/tahles/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/tahles/SKILL.md  (must be SKILL.md)
   - Cursor          .cursor/rules/tahles.mdc  (.md is ignored there;
                     replace the frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/tahles.instructions.md
                     (frontmatter `applyTo: "**"`), or append to
                     .github/copilot-instructions.md
   - Codex, Zed, Aider, Warp, Windsurf, Jules, goose, opencode, Gemini CLI and
     the other AGENTS.md readers: append it to AGENTS.md under its own heading
   - anything else   your own equivalent — and tell me where you put it

3. Keep the instructions verbatim. Do not summarise or "improve" them, and do
   not drop the `description` — that is how most tools decide when to load it.

4. Confirm it is registered, then tell me the phrase that triggers it.
```

### 3. Shell

```bash
mkdir -p .claude/skills/tahles
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/tahles/skill.md \
  -o .claude/skills/tahles/SKILL.md
```

---

## Credits & Origin

The eight rules come from the repository owner's own working style. The ideas
behind them are well documented:

- **Answer first** — [BLUF (Bottom Line Up Front)](https://en.wikipedia.org/wiki/BLUF_(communication)),
  the US military and government standard for professional writing.
- **Active voice, short sentences, plain words** — the
  [federal plain language guidelines](https://www.plainlanguage.gov/guidelines/)
  and [Orwell, *Politics and the English Language*](https://www.orwellfoundation.com/the-orwell-foundation/orwell/essays-and-other-works/politics-and-the-english-language/).

All credit for these ideas belongs to their respective authors, who retain all
rights to their own work and wording. `skill.md` contains no copied text from
the sources above. If you are one of these authors and would like the
attribution changed or this skill removed, open an issue and it will be handled.
