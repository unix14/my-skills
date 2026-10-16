# Grill Me

> A demanding interviewer that escalates until your understanding breaks — then shows you exactly where.

| | |
|---|---|
| **Slug** | `grill-me` |
| **Category** | Thinking & Critique |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

Asking a model "do I understand Kubernetes?" gets you reassurance. This skill
gets you an interview.

It asks **one question at a time**, waits, and escalates one layer deeper with
each answer — definition, then mechanism, then trade-off, then failure mode,
then the edge case nobody considers, then "now design something with it under a
hard constraint". It gives no praise, follows vagueness instead of politely
moving on, and names it when you dodge. After 8–12 questions it debriefs you in
four parts: what held up, what cracked (quoted back to you), what would get you
rejected in a real interview, and what to study first.

It works in two modes: *knowledge* (do you actually understand this?) and *plan*
(will this hold up when someone senior pushes on it?).

### Use it when

- You have a technical interview, design review, or viva coming up.
- You are about to present a decision and want the hard questions in private first.
- You think you understand something and want that assumption tested rather than flattered.
- You are onboarding into an unfamiliar system and need to find your real gaps fast.

### Don't use it when

- You are trying to *learn* something new — get it explained first ([`eli5`](../eli5/)), then come here to test it.
- You want your plan attacked rather than your understanding quizzed — use [`devils-advocate`](../devils-advocate/),
  or [Matt Pocock's `grilling`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md), which is built for exactly that.
- You are low on patience or time; this is deliberately uncomfortable and is not a quick lookup.

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/grill-me/skill.md
```

---

## Install via AI

Paste this into your local AI agent (Claude Code, Cursor, Copilot CLI, Gemini CLI, or any agent that can fetch a URL and write a file):

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/grill-me/skill.md

2. Create the directory `.claude/skills/grill-me/` in my current project.
   (Use `~/.claude/skills/grill-me/` instead if I want it available globally.)

3. Save the fetched content verbatim as `SKILL.md` inside that directory.
   Do not rewrite, summarise, or "improve" the instructions, and keep the
   YAML frontmatter exactly as-is.

4. Confirm the skill is registered, then tell me the phrase that triggers it.
```

### Install manually

```bash
mkdir -p .claude/skills/grill-me
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/grill-me/skill.md \
  -o .claude/skills/grill-me/SKILL.md
```

### Install by copy-paste

Open [`skill.md`](./skill.md), copy everything below the YAML frontmatter, and paste
it as a system prompt, custom instruction, or Project / Custom GPT / Gem instruction
in whichever LLM interface you use.

---

## Credits & Origin

**Original skill:** [`grill-me`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md)
and its implementation [`grilling`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md),
by **[Matt Pocock](https://github.com/mattpocock)** — from
[mattpocock/skills](https://github.com/mattpocock/skills) ("Skills for Real
Engineers"), MIT licensed, Copyright (c) 2026 Matt Pocock.

The name `grill-me` and the idea of a skill whose entire job is to interview you
relentlessly until nothing is left silently assumed are his. This skill exists
because that one does. If you only install one, install his.

### What differs here, and which one you want

Matt's `grilling` works a **design tree**. It computes the *frontier* — every
decision whose prerequisites are already settled — asks that whole frontier in
one numbered round with a recommended answer for each question, and repeats as
your answers push the frontier outward, until it is empty and you have shared
understanding. It finds facts itself rather than asking you for anything it
could look up. It is built to **converge on a plan** before any work starts.

This version is narrower and deliberately adversarial: one question at a time,
escalating one layer per answer (definition → mechanism → trade-off → failure →
edge → design), no recommended answers offered, and a closing debrief naming
what cracked. It is built to **test whether you actually understand something** —
interview prep, a viva, a system you've just inherited.

So: stress-testing a plan or a design → use
[Matt's](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md).
Stress-testing your own knowledge → this one.

No text is copied from Matt's skills; `skill.md` here is an independently
written prompt with a different mechanism, and the debt is to the concept and
the name. Secondary lineage for the technique itself:

- **Question-driven interrogation that exposes contradictions in the answerer's own words** — the
  [Socratic method](https://en.wikipedia.org/wiki/Socratic_method).
- **Testing as a learning tool, not just a measurement** — the
  [testing effect](https://en.wikipedia.org/wiki/Testing_effect) (retrieval practice).
- **Explicit role prompting and one-question-at-a-time process constraints** —
  [Anthropic's prompt engineering guidance](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview).

Matt Pocock retains all rights to his own work and wording. If he would like the
attribution changed, expanded, or this skill removed, open an issue and it will
be handled the same day.
