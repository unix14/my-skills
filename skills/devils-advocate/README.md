# Devil's Advocate

> Attacks your plan properly — strongest objection first, with the evidence that would refute it.

| | |
|---|---|
| **Slug** | `devils-advocate` |
| **Category** | Thinking & Critique |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

Models are agreeable by default. Ask one whether your plan is good and you will
usually be told it is, with three supporting bullets.

This skill makes the model argue the other side as well as it can be argued.
It **steel-mans your proposal first** — restating its strongest version, so the
criticism lands on what you actually believe rather than a straw man — then works
nine lines of attack: the load-bearing assumption, whether the problem is real
or an artefact of framing, the case for doing nothing, the strongest alternative,
second-order effects, failure modes ranked by probability rather than drama,
where a number is doing work it can't support, the cost nobody budgeted for, and
whose incentives are served by approval regardless of outcome.

Two rules keep it honest. Every objection comes with **what would change my
mind** — the specific evidence or test that would kill it, so nothing is
unfalsifiable. And it ends with **what survives**, because a critic who finds
nothing good is a broken instrument. It concedes immediately when you rebut it
well, and it will not invent a statistic to strengthen an attack.

### Use it when

- You have made a decision and want it attacked before the room does it for you.
- A plan feels right and you cannot articulate why, which is usually a warning.
- You are writing a proposal, RFC, or ADR and need the counter-arguments section to be real.
- The team agreed too quickly.

### Don't use it when

- You need encouragement or momentum; this will take both.
- The decision is already made and irreversible — criticism you cannot act on is just morale cost.
- You want your plan *mapped and settled* rather than attacked — use [`grill-me`](../grill-me/), which converges where this one pulls apart.
- You want your *knowledge* tested rather than your plan — use [`quiz-me`](../quiz-me/).

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/devils-advocate/skill.md
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
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/devils-advocate/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/devils-advocate/SKILL.md  (the file must be SKILL.md)
   - Cursor          .cursor/rules/devils-advocate.mdc  (.md is ignored there; replace the
                     frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/devils-advocate.instructions.md  (frontmatter
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
mkdir -p .claude/skills/devils-advocate
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/devils-advocate/skill.md \
  -o .claude/skills/devils-advocate/SKILL.md
```

---

## Credits & Origin

This skill packages a set of well-documented critical-thinking practices.
Specific lineage:

- **The role itself** — the *advocatus diaboli*, the official appointed to argue against
  canonisation; see [Devil's advocate](https://en.wikipedia.org/wiki/Devil%27s_advocate).
- **Structured adversarial review of your own plan** — [red teaming](https://en.wikipedia.org/wiki/Red_team),
  as practised in military, security, and intelligence analysis.
- **Imagining the failure before it happens** — Gary Klein's
  [*Performing a Project Premortem*](https://hbr.org/2007/09/performing-a-project-premortem), Harvard Business Review, 2007.
- **Steel-manning before attacking** — the [principle of charity](https://en.wikipedia.org/wiki/Principle_of_charity)
  in argumentation.
- **"What would change my mind" as a requirement** — Karl Popper's
  [falsifiability](https://en.wikipedia.org/wiki/Falsifiability).

All credit for these ideas belongs to their respective authors, who retain all
rights to their own work and wording. `skill.md` contains no copied text from
the sources above — it is an independent prompt that operationalises publicly
documented patterns. If you are one of these authors and would like the
attribution changed or this skill removed, open an issue and it will be handled.
