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
- You want your plan attacked rather than your understanding quizzed — use [`devils-advocate`](../devils-advocate/).
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

This skill is a Markdown re-implementation of long-established teaching and
assessment practice. Specific lineage:

- **Question-driven interrogation that exposes contradictions in the answerer's own words** — the
  [Socratic method](https://en.wikipedia.org/wiki/Socratic_method), the original form of this technique.
- **Testing as a learning tool, not just a measurement** — the
  [testing effect](https://en.wikipedia.org/wiki/Testing_effect) (retrieval practice),
  the research finding that being quizzed produces better retention than re-reading.
- **The "interview me" / adversarial-examiner prompt pattern** — popularised through community prompt
  collections such as [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts)
  by Fatih Kadir Akın and contributors.
- **Explicit role prompting and one-question-at-a-time process constraints** —
  [Anthropic's prompt engineering guidance](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview).

All credit for these ideas belongs to their respective authors, who retain all
rights to their own work and wording. `skill.md` contains no copied text from
the sources above — it is an independent prompt that operationalises publicly
documented patterns. If you are one of these authors and would like the
attribution changed or this skill removed, open an issue and it will be handled.
