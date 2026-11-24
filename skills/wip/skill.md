---
name: wip
description: Summarises all uncommitted work in the current git repository — staged, unstaged, and untracked — as a short bullet-point TL;DR. Use when asked for "/wip", "what's uncommitted", "what have I changed", "what's in my working tree", "summarise my local changes", or before writing a commit message.
---

# WIP

You report what is uncommitted in the current git repository. Nothing else.
The reader wants to know, in ten seconds, what they have changed and not yet
committed.

## Gather (read-only)

Run only commands that read. These are enough:

- `git status --short --branch` — branch, and every changed file
- `git diff --cached` — staged changes
- `git diff` — unstaged changes
- for each untracked file: read it, or its first lines if it is large

Never stage, commit, stash, discard, check out, or change anything. If the
folder is not a git repository, say so in one line and stop.

## Output format

Always this shape, nothing before or after it:

**WIP on `<branch>`** — one sentence, maximum 25 words: what this work is doing,
as a whole.

**Staged**
- one bullet per logical change, not per file: what changed and why it matters
- name the files in `code` at the end of the bullet

**Unstaged**
- same rules

**Untracked**
- same rules: what each new file is for

**Watch out**
- only real problems: leftover debug code, a secret or credential, conflict
  markers, a half-finished edit, a large or generated file, the same file both
  staged and unstaged with different content

Omit any section that is empty. If nothing is uncommitted, answer with one
line: "Working tree is clean on `<branch>`."

## Rules

- **Hard ceiling: 150 words**, file names not counted. Group related files into
  one bullet before you cut detail.
- **Describe meaning, not mechanics.** "Adds retry to the upload client", not
  "Modified 14 lines in upload.ts".
- **Never invent intent.** If you cannot tell why a change was made, describe
  what it does and stop.
- **Never print a secret.** If a diff contains one, name the file under
  **Watch out** and do not repeat the value.
- **Skip noise.** Lockfiles, build output, and formatting-only changes get one
  short bullet at most.
