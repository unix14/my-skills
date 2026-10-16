# Humanizer

> Strips the AI tells out of copy and rewrites it the way a competent human would, without changing what it says.

| | |
|---|---|
| **Slug** | `humanizer` |
| **Category** | Communication & Tone |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

AI prose has a recognisable signature: "In today's fast-paced world", three
adjectives where one would do, *leverage* and *utilise* and *streamline*,
"Moreover" welding together sentences that didn't need welding, the
not-just-X-but-Y construction twice in one paragraph, and a closing paragraph
summarising the three paragraphs above it.

This skill is an editor, not a co-author. It has an explicit **delete-on-sight
list** of those tells, a set of rewrite moves (verbs over nouns, active over
passive, deliberate variation in sentence length — which is most of what "human"
means on the page), and a target of 20–40% shorter, on the principle that a
sentence which survives deletion unchanged in meaning was padding.

The constraints are the important part. **Meaning does not change** — not the
claims, the numbers, the names, the caveats, or the degree of certainty; a hedge
in the original stays a hedge. It adds no facts or examples that weren't there,
keeps the register (a legal notice stays a legal notice), and keeps jargon that
carries precise meaning. Where the original was vague, it flags that only you
can supply the specific rather than inventing one. If the text is already clean,
it says so and changes nothing.

### Use it when

- You drafted with AI and it reads like it.
- Your own copy has gone corporate and you've lost the ear to hear it.
- You need a landing page, email, or README to sound like a person wrote it.
- A document is 40% longer than it needs to be and you know it.

### Don't use it when

- The text must be reproduced exactly — legal, regulated, or quoted material.
- You want the content improved rather than the prose; this deliberately won't add ideas.
- You are trying to defeat an AI-detection tool. That isn't what this does, and the output is honest editing, not evasion.

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/humanizer/skill.md
```

---

## Install via AI

Paste this into your local AI agent (Claude Code, Cursor, Copilot CLI, Gemini CLI, or any agent that can fetch a URL and write a file):

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/humanizer/skill.md

2. Create the directory `.claude/skills/humanizer/` in my current project.
   (Use `~/.claude/skills/humanizer/` instead if I want it available globally.)

3. Save the fetched content verbatim as `SKILL.md` inside that directory.
   Do not rewrite, summarise, or "improve" the instructions, and keep the
   YAML frontmatter exactly as-is.

4. Confirm the skill is registered, then tell me the phrase that triggers it.
```

### Install manually

```bash
mkdir -p .claude/skills/humanizer
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/humanizer/skill.md \
  -o .claude/skills/humanizer/SKILL.md
```

### Install by copy-paste

Open [`skill.md`](./skill.md), copy everything below the YAML frontmatter, and paste
it as a system prompt, custom instruction, or Project / Custom GPT / Gem instruction
in whichever LLM interface you use.

---

## Credits & Origin

This skill packages advice from the plain-English tradition, applied to the
specific failure modes of AI-generated prose. Specific lineage:

- **Cut every word that earns nothing; prefer the short, concrete, active word** — George Orwell,
  [*Politics and the English Language*](https://www.orwellfoundation.com/the-orwell-foundation/orwell/essays-and-other-works/politics-and-the-english-language/), 1946.
- **Omit needless words; verbs over noun phrases** — Strunk's
  [*The Elements of Style*](https://www.gutenberg.org/ebooks/37134).
- **Write the way you would say it out loud** — Paul Graham,
  [*Write Like You Talk*](https://paulgraham.com/talk.html).
- **Plain, jargon-free professional register** — the
  [Plain English Campaign](https://www.plainenglish.co.uk/) and the
  [federal plain language guidelines](https://www.plainlanguage.gov/guidelines/).

The specific list of AI tells (opening throat-clearing, the adjective triad,
"Moreover", not-just-X-but-Y, em-dash sprawl, the redundant closing summary) is
drawn from widely shared community observation across writing and editing
communities rather than from any single author.

All credit for these ideas belongs to their respective authors, who retain all
rights to their own work and wording. `skill.md` contains no copied text from
the sources above — it is an independent prompt that operationalises publicly
documented patterns. If you are one of these authors and would like the
attribution changed or this skill removed, open an issue and it will be handled.
