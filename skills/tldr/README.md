# TLDR

> Ruthless compression: one sentence you could act on, the few points that matter, and what to do about it.

| | |
|---|---|
| **Slug** | `tldr` |
| **Category** | Communication & Tone |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

Ask a model to summarise and you usually get a shorter version of the same
sprawl, opening with "This article discusses…" — a description of the source's
structure rather than its content.

This skill enforces a fixed shape and a hard 150-word ceiling: a **TL;DR** of
30 words maximum that stands alone, **3–5 key points** in priority order, and a
**So what** section naming what someone now has to do. Conclusion first, never
a recap of the source's structure. Numbers, names, dates, and decisions survive;
background and hedging don't. It preserves uncertainty rather than promoting
"we think" into fact, adds nothing the source didn't say, and scales *down* for
short inputs instead of padding them into the template.

For threads and meeting notes it separates what was **decided** from what was
merely **discussed**, and attributes commitments to the person who made them.

### Use it when

- A long thread, doc, or transcript landed on you and you need the gist plus the actions.
- You are forwarding something to someone busier than you and need the top of the email.
- You need meeting notes turned into decisions and owners.
- You are triaging a backlog of reading and need to know what deserves the full read.

### Don't use it when

- Nuance is the point — a legal clause, a medical finding, or a contract needs reading in full.
- You need the source's reasoning preserved, not just its conclusions.
- You are summarising something you intend to quote from; go to the original.

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/tldr/skill.md
```

---

## Install via AI

Paste this into your local AI agent (Claude Code, Cursor, Copilot CLI, Gemini CLI, or any agent that can fetch a URL and write a file):

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/tldr/skill.md

2. Create the directory `.claude/skills/tldr/` in my current project.
   (Use `~/.claude/skills/tldr/` instead if I want it available globally.)

3. Save the fetched content verbatim as `SKILL.md` inside that directory.
   Do not rewrite, summarise, or "improve" the instructions, and keep the
   YAML frontmatter exactly as-is.

4. Confirm the skill is registered, then tell me the phrase that triggers it.
```

### Install manually

```bash
mkdir -p .claude/skills/tldr
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/tldr/skill.md \
  -o .claude/skills/tldr/SKILL.md
```

### Install by copy-paste

Open [`skill.md`](./skill.md), copy everything below the YAML frontmatter, and paste
it as a system prompt, custom instruction, or Project / Custom GPT / Gem instruction
in whichever LLM interface you use.

---

## Credits & Origin

This skill packages standard editorial and professional-writing conventions.
Specific lineage:

- **The TL;DR convention itself** — internet forum and Usenet culture;
  see [TL;DR](https://en.wikipedia.org/wiki/TL;DR) for the origin of the term.
- **Conclusion-first structure** — [BLUF (Bottom Line Up Front)](https://en.wikipedia.org/wiki/BLUF_(communication)),
  the US military and government standard for professional writing.
- **Most important information first, detail descending** — the
  [inverted pyramid](https://en.wikipedia.org/wiki/Inverted_pyramid_(journalism)) from journalism.
- **Plain, compressed phrasing** — the [federal plain language guidelines](https://www.plainlanguage.gov/guidelines/).

All credit for these ideas belongs to their respective authors, who retain all
rights to their own work and wording. `skill.md` contains no copied text from
the sources above — it is an independent prompt that operationalises publicly
documented patterns. If you are one of these authors and would like the
attribution changed or this skill removed, open an issue and it will be handled.
