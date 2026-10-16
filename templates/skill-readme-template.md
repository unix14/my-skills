<!--
  TEMPLATE: skills/<skill-name>/README.md
  --------------------------------------------------
  Copy this file to `skills/<skill-name>/README.md` and replace every
  {{PLACEHOLDER}}. Delete this comment block when you are done.

  Placeholders:
    {{SKILL_TITLE}}      Human-readable name, e.g. "PRD Generator"
    {{SKILL_SLUG}}       Folder name, kebab-case, e.g. "prd-generator"
    {{CATEGORY}}         One of: Code & Debugging | Product & Ideation |
                         Communication & Tone | Thinking & Critique |
                         Learning & Explanation
    {{ONE_LINER}}        One sentence, no marketing fluff
    {{OVERVIEW}}         2-4 sentences: what it does and how it behaves
    {{USE_CASE_N}}       Concrete situations where you would reach for it
    {{NOT_FOR_N}}        Situations where it is the wrong tool
    {{SOURCE_TITLE}}     Name of the prior art / original pattern
    {{SOURCE_URL}}       Direct, working link to that source
    {{SOURCE_AUTHOR}}    Author, community, or organisation behind it
    {{CREDIT_NOTE}}      One sentence on what exactly was borrowed

  Rules (non-negotiable for this repo):
    - Every skill MUST credit its source or inspiration. No exceptions.
    - If you are re-implementing a SPECIFIC published skill or prompt rather
      than a general technique, say so in the FIRST line of Credits & Origin:
      name the author, link the original file, note its license, and state
      plainly what your version does differently and when to prefer theirs.
    - No secrets, no API keys, no PII, no client names in examples.
    - `skill.md` stays model-agnostic plain Markdown. No tool calls,
      no MCP, no shell commands, no build step. If your skill needs an agent
      with tools, say so in the README and add a note to docs/COMPATIBILITY.md.
    - Leave the Install section as it is. It is deliberately agent-neutral and
      the per-tool paths live in docs/COMPATIBILITY.md, so they are maintained
      in one place rather than eight.
-->

# {{SKILL_TITLE}}

> {{ONE_LINER}}

| | |
|---|---|
| **Slug** | `{{SKILL_SLUG}}` |
| **Category** | {{CATEGORY}} |
| **Prompt file** | [`skill.md`](./skill.md) |
| **Dependencies** | None — pure Markdown |

---

## Overview

{{OVERVIEW}}

### Use it when

- {{USE_CASE_1}}
- {{USE_CASE_2}}
- {{USE_CASE_3}}

### Don't use it when

- {{NOT_FOR_1}}
- {{NOT_FOR_2}}

---

## Raw link

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/{{SKILL_SLUG}}/skill.md
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
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/{{SKILL_SLUG}}/skill.md

2. Work out where standing instructions belong for whichever assistant you are,
   and save it there verbatim:
   - Claude Code     .claude/skills/{{SKILL_SLUG}}/SKILL.md  (must be SKILL.md)
   - Cursor          .cursor/rules/{{SKILL_SLUG}}.mdc  (.md is ignored there;
                     replace the frontmatter with `description` + `alwaysApply: false`)
   - GitHub Copilot  .github/instructions/{{SKILL_SLUG}}.instructions.md
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
mkdir -p .claude/skills/{{SKILL_SLUG}}
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/{{SKILL_SLUG}}/skill.md \
  -o .claude/skills/{{SKILL_SLUG}}/SKILL.md
```

---

## Credits & Origin

<!-- Re-implementing a specific published skill? Lead with this, then the pattern:
**Original skill:** [`{{ORIGINAL_SKILL}}`]({{ORIGINAL_URL}}) by
[{{ORIGINAL_AUTHOR}}]({{ORIGINAL_AUTHOR_URL}}) — {{ORIGINAL_LICENSE}}.
What differs here: {{WHAT_DIFFERS}}. Prefer theirs when {{PREFER_THEIRS}}.
-->

**Pattern:** [{{SOURCE_TITLE}}]({{SOURCE_URL}}) — {{SOURCE_AUTHOR}}

{{CREDIT_NOTE}}

This file is a Markdown re-implementation of a publicly known pattern. The
original author retains all rights to their work and wording. Nothing here is
claimed as original intellectual property. If you are the author and want the
attribution changed or the skill removed, open an issue and it will be handled.
