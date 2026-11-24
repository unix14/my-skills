# WIP

> A short bullet-point TL;DR of everything uncommitted in your repo — staged, unstaged, and untracked.

| | |
|---|---|
| **Slug** | `wip` |
| **Category** | Code & Debugging |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

Run it in a git repository and it reads your working tree with read-only git
commands, then reports what you have changed and not yet committed: one
sentence on what the work is doing as a whole, then bullets grouped as
**Staged**, **Unstaged**, and **Untracked**, each describing a logical change
rather than a line count. A **Watch out** section flags leftover debug code,
conflict markers, half-finished edits, and secrets — naming the file without
repeating the value. Hard ceiling of 150 words. It never stages, commits,
stashes, or discards anything.

> **Needs an agent that can run shell commands** — Claude Code, Cursor, Copilot
> CLI, Codex, Gemini CLI and similar. In a plain chat interface, paste your
> `git status` and `git diff` output after the prompt instead.

### Use it when

- You come back to a repo after a break and need to remember where you were.
- You are about to commit and want to check nothing unexpected is staged.
- You need a starting point for a commit message or a standup update.

### Don't use it when

- You want a summary of committed history — read `git log` instead.
- You need a line-by-line code review — use a review tool; this skill only summarises.

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/wip/skill.md
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
instructions, a Gemini Gem, or just your first message.

### 2. Let your agent install it

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/wip/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/wip/SKILL.md  (must be SKILL.md)
   - Cursor          .cursor/rules/wip.mdc  (.md is ignored there;
                     replace the frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/wip.instructions.md
                     (frontmatter `applyTo: "**"`), or append to
                     .github/copilot-instructions.md
   - Codex, Zed, Aider, Warp, Windsurf, Jules, goose, opencode, Gemini CLI and
     the other AGENTS.md readers: append it to AGENTS.md under its own heading
   - anything else   your own equivalent — and tell me where you put it

3. Keep the instructions verbatim. Do not summarise or "improve" them, and do
   not drop the `description` — that is how most tools decide when to load it.

4. Confirm it is registered, then tell me the phrase that triggers it.
```

### 3. Shell

```bash
mkdir -p .claude/skills/wip
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/wip/skill.md \
  -o .claude/skills/wip/SKILL.md
```

---

## Credits & Origin

**Pattern:** the [`git status`](https://git-scm.com/docs/git-status) and
[`git diff`](https://git-scm.com/docs/git-diff) workflow — the Git project.
The output shape follows [`tldr`](../tldr/) and
[BLUF (Bottom Line Up Front)](https://en.wikipedia.org/wiki/BLUF_(communication)).

This skill wraps standard read-only git commands in a summary format. The
authors of these tools and conventions retain all rights to their own work and
wording, and `skill.md` contains no copied text from them. If you are one of
these authors and would like the attribution changed or this skill removed,
open an issue and it will be handled.
