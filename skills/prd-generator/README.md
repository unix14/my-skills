# PRD Generator

> Turns a raw product idea into a decision-ready PRD — by interrogating the idea first, then writing the document.

| | |
|---|---|
| **Slug** | `prd-generator` |
| **Category** | Product & Ideation |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

Most AI-generated PRDs fail the same way: you give the model a one-line idea, it
gives you twelve confident sections built entirely out of invented users,
invented metrics, and invented market research. The document looks finished and
is worthless.

This skill inverts that. It makes the model act as a Principal PM who
**interrogates the idea before writing anything** — problem, user, outcome,
success metric, scope, constraints, risk — in focused batches of 5–8 questions.
Only then does it draft, using a 14-section structure where non-goals,
counter-metrics, failure modes, and a rollback plan are first-class sections
rather than afterthoughts. Anything it had to infer is tagged `[ASSUMPTION]`
inline and collected at the end, so you can correct the whole set in one pass.
It finishes by stress-testing its own draft: weakest assumption, most likely
scope balloon, and the one fact worth going to find.

### Use it when

- You have an idea in your head (or a Slack thread) and need something a team can actually build from.
- A stakeholder asked for "a quick spec" and you want it to survive engineering review.
- You are scoping an MVP and keep losing the argument about what is out of scope.
- You inherited a vague feature request and need to surface what nobody has decided yet.

### Don't use it when

- You already have a written spec and just want it edited — the interrogation phase will feel like friction.
- You need a technical design doc (API contracts, data models, system diagrams) rather than a product requirements doc.
- You want a document to rubber-stamp a decision already made; this skill is built to find the holes in it.

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/prd-generator/skill.md
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
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/prd-generator/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/prd-generator/SKILL.md  (the file must be SKILL.md)
   - Cursor          .cursor/rules/prd-generator.mdc  (.md is ignored there; replace the
                     frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/prd-generator.instructions.md  (frontmatter
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
mkdir -p .claude/skills/prd-generator
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/prd-generator/skill.md \
  -o .claude/skills/prd-generator/SKILL.md
```

---

## Example

**You:**
> We should let users export their dashboard to PDF.

**The skill:** does *not* write a PRD. It asks, among others: who asked for this
and how often; what they do today instead; whether the real need is sharing
rather than exporting; what breaks if the dashboard is interactive; which single
number tells you it worked. Three of those usually change the feature.

---

## Credits & Origin

This skill is a Markdown re-implementation of well-established product
management practice. It is not an original invention, and the structure is
deliberately recognisable. Specific lineage:

- **Problem-first framing, non-goals, and "opportunity before solution"** —
  [Marty Cagan / Silicon Valley Product Group](https://www.svpg.com/articles/),
  whose writing on product discovery and *Inspired* established the
  problem-before-solution discipline this skill enforces.
- **Working backwards from the customer, written narrative over slides** —
  Amazon's PR/FAQ process, documented by Colin Bryar and Bill Carr in
  [*Working Backwards*](https://www.workingbackwards.com/) — the origin of the
  "write the document first, build second" norm.
- **Counter-metrics and the single primary metric** — the
  [HEART framework, Rodden, Hutchinson & Fu, Google](https://research.google/pubs/measuring-the-user-experience-on-a-large-scale-user-centered-metrics-for-web-applications/),
  and Amplitude/Mixpanel-era analytics practice around guardrail metrics.
- **PRD section inventory and "what a good spec contains"** —
  [Lenny Rachitsky's product templates and essays](https://www.lennysnewsletter.com/),
  a widely used public reference for modern PRD structure.
- **Interrogate-before-answering prompt pattern** —
  [Anthropic's prompt engineering guidance](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
  on role prompting and explicit step-by-step process instructions.

All credit for these concepts belongs to their respective authors; they retain
all rights to their own work and wording. Nothing in `skill.md` is copied text
from the sources above — it is an independent prompt that operationalises their
publicly documented ideas. If you are one of these authors and want the
attribution changed or this skill removed, open an issue and it will be handled.

### On the batched questions, which is a fair thing to ask about

Phase 1 here asks 5 to 8 numbered questions at a time and waits. Matt Pocock's
[`grilling`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md)
also batches: it asks every question on the *frontier* of a design tree in one
numbered round, each with his recommended answer attached, then recomputes the
frontier from what you said and asks the next round.

The two were written independently and the resemblance stops at the first step.
Batching numbered questions is the obvious correction to asking fifty questions
one at a time; what makes his version work is absent here. There is no design
tree, so no dependency ordering and no frontier. No question carries a
recommended answer. There is one batch, not rounds that continue until nothing
is left unasked. Convergence on an obvious idea, not a debt — recorded here
rather than left for someone else to wonder about.

What is true is that his interrogation is better than this one, and it is
already in this repo: [`grill-me`](../grill-me/) is his skill, copied verbatim.
Running that first and bringing the answers here for the document is a better
sequence than using Phase 1 alone.

Two more of his are adjacent without being sources
([mattpocock/skills](https://github.com/mattpocock/skills), MIT):
[`to-spec`](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-spec/SKILL.md)
deliberately does not interview — it synthesises a spec out of a conversation
you have already had and publishes it to your issue tracker — and
[`to-questionnaire`](https://github.com/mattpocock/skills/blob/main/skills/productivity/to-questionnaire/SKILL.md)
turns the questions you cannot answer yourself into a document for the person
who can.
