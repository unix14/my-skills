# Quiz Me

> A demanding examiner that escalates one layer per answer until your understanding breaks, then tells you exactly what cracked.

| | |
|---|---|
| **Slug** | `quiz-me` |
| **Category** | Thinking & Critique |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

Ask a model "do I understand Kubernetes?" and you get reassurance. This gets you
an examination.

It asks **one question at a time**, waits, and escalates one layer deeper with
each answer: definition, then mechanism, then trade-off, then failure mode, then
the edge case nobody considers, then "now design something with it under a hard
constraint". It gives no praise, follows vagueness instead of politely moving on,
and names it when you dodge or answer a question you weren't asked. After 8–12
questions it debriefs in four parts: what held up, what cracked (quoted back to
you), what would get you rejected in a real interview, and what to study first.

Two modes: *knowledge* (do you actually understand this?) and *plan* (will this
hold up when someone senior pushes on it?). For plan work,
[`grill-me`](../grill-me/) is the better tool — see below.

### Use it when

- You have a technical interview, design review, or viva coming up.
- You think you understand something and want that assumption tested rather than flattered.
- You are onboarding into an unfamiliar system and need to find your real gaps fast.
- You are about to teach or present something and want the holes found in private.

### Don't use it when

- You are trying to *learn* something new — get it explained first ([`eli5`](../eli5/)), then come here to test it.
- You want your *plan* settled rather than your knowledge tested — use [`grill-me`](../grill-me/).
- You want your plan attacked — use [`devils-advocate`](../devils-advocate/).
- You are low on patience or time. This is deliberately uncomfortable.

### How it differs from `grill-me`

Both interview you. They are built for different jobs, and installing both is
reasonable:

| | `quiz-me` (this one) | [`grill-me`](../grill-me/) (Matt Pocock's) |
|---|---|---|
| **Goal** | find out whether you understand it | reach shared understanding about a plan |
| **Shape** | one question at a time, escalating | numbered rounds of the whole settled frontier |
| **Recommends answers?** | never — that would hand you the answer | yes, worded so "yes" accepts it |
| **Ends with** | a debrief of what cracked | an empty frontier and your confirmation |
| **Needs tools?** | no, works in any chat | prefers an agent that can dispatch sub-agents |

The trigger words are kept apart on purpose — "grill me" goes to his, "quiz me"
comes here — so you can have both installed without them fighting.

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/quiz-me/skill.md
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
instructions, a Gemini Gem, or just your first message. Then tell it the topic
and the level you want to be held to.

### 2. Let your agent install it

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/quiz-me/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/quiz-me/SKILL.md  (the file must be SKILL.md)
   - Cursor          .cursor/rules/quiz-me.mdc  (.md is ignored there; replace the
                     frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/quiz-me.instructions.md  (frontmatter
                     `applyTo: "**"`), or append to .github/copilot-instructions.md
   - Codex, Zed, Aider, Warp, Windsurf, Jules, goose, opencode, Gemini CLI and
     the other AGENTS.md readers: append it to AGENTS.md under its own heading
   - anything else   your own equivalent — and tell me where you put it

3. Keep the instructions verbatim. Do not summarise or "improve" them, and do
   not drop the `description` — that is how most tools decide when to load it.

4. Confirm it is registered, then tell me the phrase that triggers it.
```

### 3. Shell

```bash
mkdir -p .claude/skills/quiz-me
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/quiz-me/skill.md \
  -o .claude/skills/quiz-me/SKILL.md
```

---

## Credits & Origin

**Independently written for this repo** — the prompt is ours, the techniques are
not. Its own history is worth stating plainly, because it explains the name:

This file sat in this repo as `grill-me` until Matt Pocock was identified as the
author of the skill that name belongs to. `skills/grill-me/` now holds
[his files, copied verbatim](../grill-me/), and this one was renamed to `quiz-me`
— both so it stops trading on his name, and because the two do different jobs
and should not fight over the same trigger phrase. Nothing in it is derived from
his wording; only the name ever overlapped.

Lineage of the technique itself:

- **Question-driven interrogation that exposes contradictions in the answerer's own words** — the
  [Socratic method](https://en.wikipedia.org/wiki/Socratic_method), the original form of this.
- **Testing as a learning tool rather than only a measurement** — the
  [testing effect](https://en.wikipedia.org/wiki/Testing_effect), the finding that
  being quizzed produces better retention than re-reading.
- **The "interview me" / adversarial-examiner prompt pattern** — popularised through
  community prompt collections such as
  [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) by
  Fatih Kadir Akın and contributors.
- **Explicit role prompting and one-question-at-a-time process constraints** —
  [Anthropic's prompt engineering guidance](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview).

All credit for these ideas belongs to their respective authors, who retain all
rights to their own work and wording. `skill.md` contains no copied text from
the sources above. If you are one of these authors and would like the
attribution changed or this skill removed, open an issue and it will be handled.
