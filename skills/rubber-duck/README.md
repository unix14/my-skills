# Rubber Duck

> A Socratic debugging partner that refuses to give you the answer, so you find it yourself.

| | |
|---|---|
| **Slug** | `rubber-duck` |
| **Category** | Code & Debugging |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

The reason rubber duck debugging works is that explaining a problem out loud
forces you to make your assumptions explicit, and most bugs are a wrong
assumption rather than a wrong line. An AI that immediately offers a fix skips
that entirely — and hands you a guess, since it can't see your environment.

This skill makes the model hold its tongue. Its only tools are questions and
reflections. It starts by making you narrate expected-vs-actual (where a
surprising number of bugs die), then works the gap: what's the last line you're
*certain* ran, and how do you know? What are you taking for granted there? What
changed since it worked? What's the smallest input that still reproduces it?
Before you run it — what do you expect to see if your theory is right?

It mirrors your own words back so you hear the contradiction, follows your
theory rather than steering you onto its own, and calls it out when you circle
the same spot three times. It breaks character on three conditions only: you say
"just tell me", you ask for a plain fact it has and you don't, or you're about
to do something destructive.

### Use it when

- You have been stuck for twenty minutes and have stopped forming new theories.
- The behaviour makes no sense and you suspect your mental model, not the code.
- You are about to ask a colleague and want to get past the obvious first.
- You are breaking down a problem that is too big to hold in your head.

### Don't use it when

- You need a fact, an API signature, or syntax — just ask for it directly.
- The clock is against you (production is down). Ask for the answer.
- You already know the fix and just want it written — this will be pure friction.

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/rubber-duck/skill.md
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
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/rubber-duck/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/rubber-duck/SKILL.md  (the file must be SKILL.md)
   - Cursor          .cursor/rules/rubber-duck.mdc  (.md is ignored there; replace the
                     frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/rubber-duck.instructions.md  (frontmatter
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
mkdir -p .claude/skills/rubber-duck
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/rubber-duck/skill.md \
  -o .claude/skills/rubber-duck/SKILL.md
```

---

## Credits & Origin

This skill is a Markdown re-implementation of a technique that predates LLMs
entirely. Specific lineage:

- **Rubber duck debugging** — named and popularised by Andrew Hunt and David Thomas in
  [*The Pragmatic Programmer*](https://pragprog.com/titles/tpp20/the-pragmatic-programmer-20th-anniversary-edition/);
  background at [Rubber duck debugging](https://en.wikipedia.org/wiki/Rubber_duck_debugging).
- **Questioning rather than telling, to surface the answerer's own assumptions** — the
  [Socratic method](https://en.wikipedia.org/wiki/Socratic_method).
- **Hypothesis → prediction → test as a debugging loop** — the
  [scientific method](https://en.wikipedia.org/wiki/Scientific_method) applied to debugging,
  as taught in David Agans' *Debugging* and standard engineering practice.

All credit for these ideas belongs to their respective authors, who retain all
rights to their own work and wording. `skill.md` contains no copied text from
the sources above — it is an independent prompt that operationalises publicly
documented patterns. If you are one of these authors and would like the
attribution changed or this skill removed, open an issue and it will be handled.

### See also, and not a source

Matt Pocock's
[`diagnosing-bugs`](https://github.com/mattpocock/skills/blob/main/skills/engineering/diagnosing-bugs/SKILL.md)
([mattpocock/skills](https://github.com/mattpocock/skills), MIT) works the same
ground from the opposite end. Its first and largest phase refuses to let the
agent theorise at all until it has one fast, deterministic command that goes red
on your actual bug; then it ranks three to five falsifiable hypotheses and
instruments one variable at a time.

Nothing here came from it. This skill withholds the answer on purpose and his is
built to produce one, which is a real difference and not a framing of the same
thing. But the honest advice is: if you want the bug found rather than the
practice of finding it, use his.
