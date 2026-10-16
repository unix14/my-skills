# Grill Me

> A relentless interview that maps your plan as a design tree and works it round by round until nothing is left silently assumed.

| | |
|---|---|
| **Slug** | `grill-me` |
| **Category** | Thinking & Critique |
| **Author** | **[Matt Pocock](https://github.com/mattpocock)** — this skill is his, copied verbatim |
| **Upstream** | [mattpocock/skills](https://github.com/mattpocock/skills) · MIT · Copyright (c) 2026 Matt Pocock |
| **Prompt files** | [`skill.md`](./skill.md) (trigger) + [`grilling.md`](./grilling.md) (implementation) |
| **License** | [MIT — his notice](./LICENSE-mattpocock), included as the license requires |

> **This is not a re-implementation.** Both files in this folder are byte-for-byte
> copies of Matt Pocock's originals, redistributed under the MIT license he
> published them under. The wording is entirely his. Nothing here is ours except
> this README.

---

## Overview

Most "interview me" prompts ask a scattershot list of questions and stop when
they run out. This one has a mechanism.

It maps the problem as a **design tree**, where every decision branches into the
decisions hanging off it. It then works that tree in **rounds**. The *frontier*
is every decision whose prerequisites are already settled — the questions that
can be asked now without guessing at answers not yet heard. It asks the whole
frontier in one numbered round, giving its recommended answer to each question,
worded so "yes" accepts the recommendation. Then it waits.

Your answers reshape the tree: settled decisions push the frontier outward and
unblock questions that depended on them. It recomputes and asks the next round.
A question whose answer depends on another question still open belongs to a
later round, not this one. The session ends when the frontier is empty — every
branch visited, nothing silently assumed — and it will not act until you confirm
you have reached shared understanding.

One detail worth noticing: finding **facts** is the agent's job, never yours.
When a question needs something from the filesystem or a tool, it dispatches a
sub-agent to go and look rather than asking you for what it could discover
itself. It doesn't block on that either — only the questions downstream of the
exploration wait.

### Use it when

- You are about to start building and want the design settled first.
- You have a plan you believe in and need every assumption in it surfaced.
- A decision has branches you can feel but haven't enumerated.
- You want an agent to reach shared understanding with you *before* it writes code.

### Don't use it when

- You want to be quizzed on whether you *understand* a topic — this converges on a plan, it doesn't test knowledge.
- You want your plan attacked rather than mapped — use [`devils-advocate`](../devils-advocate/).
- You need a quick answer. This is a multi-round conversation by design.

### A note on portability

Unlike the other skills in this collection, this one assumes an agent with tools
— it dispatches sub-agents to find facts. It works best in Claude Code or a
similar agentic harness. In a plain chat interface the rounds still work; the
agent will simply ask you for facts it cannot go and fetch.

---

## Raw links

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/grill-me/skill.md
https://raw.githubusercontent.com/unix14/my-skills/main/skills/grill-me/grilling.md
```

Or take them from the source, which is the better habit:

```
https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/grill-me/SKILL.md
https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/grilling/SKILL.md
```

---

## Install via AI

This skill is two files: `grill-me` is a user-invocable trigger that calls
`grilling`, which holds the actual instructions. **Both must be installed.**

```text
Install a skill for me from public URLs. It comes in two parts.

1. Fetch these two raw Markdown files:
   https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/grill-me/SKILL.md
   https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/grilling/SKILL.md

2. Save them verbatim as:
   .claude/skills/grill-me/SKILL.md
   .claude/skills/grilling/SKILL.md
   (Use ~/.claude/skills/ instead if I want them available globally.)

3. Do not rewrite, summarise, or "improve" either file, and keep the YAML
   frontmatter exactly as-is — `grill-me` delegates to `grilling` by name,
   so renaming either one breaks it.

4. Confirm both are registered, then tell me the phrase that triggers it.
```

### Install manually

```bash
for part in grill-me grilling; do
  mkdir -p ".claude/skills/$part"
  curl -fsSL "https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/$part/SKILL.md" \
    -o ".claude/skills/$part/SKILL.md"
done
```

### Install by copy-paste

In a plain chat interface, the trigger file is pointless — paste the contents of
[`grilling.md`](./grilling.md) below its frontmatter as your system prompt or
custom instruction, then describe the plan you want grilled.

---

## Credits & Origin

**This skill is the work of [Matt Pocock](https://github.com/mattpocock)**, from
[mattpocock/skills](https://github.com/mattpocock/skills) — "Skills for Real
Engineers. Straight from my .agents directory."

- [`skills/productivity/grill-me/SKILL.md`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) → copied here as [`skill.md`](./skill.md)
- [`skills/productivity/grilling/SKILL.md`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md) → copied here as [`grilling.md`](./grilling.md)

Both are **byte-for-byte identical** to the originals, verified by checksum, and
redistributed under the MIT license he released them under. His copyright and
permission notice is included in this folder as
[`LICENSE-mattpocock`](./LICENSE-mattpocock), which is what the license requires
of anyone redistributing it — including you, if you copy it onward.

The design-tree-and-frontier mechanism, the round format, the "word each question
so yes accepts your recommendation" instruction, and the rule that finding facts
is the agent's job and not the user's are all his ideas and his wording. The repo
you are reading contributes nothing to this skill but a directory to put it in.

**Go read his repo.** It has around thirty more skills, several of them better
than anything here.

If Matt Pocock would prefer this not be redistributed, or wants the framing
changed, open an issue and it will be removed the same day — license or no
license.
