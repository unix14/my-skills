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
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/tldr/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/tldr/SKILL.md  (the file must be SKILL.md)
   - Cursor          .cursor/rules/tldr.mdc  (.md is ignored there; replace the
                     frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/tldr.instructions.md  (frontmatter
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
mkdir -p .claude/skills/tldr
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/tldr/skill.md \
  -o .claude/skills/tldr/SKILL.md
```

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
