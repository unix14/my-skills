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
      no MCP, no shell commands, no build step.
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

Point any agent, script, or `curl` at this URL:

```
https://raw.githubusercontent.com/unix14/my-skills/main/skills/{{SKILL_SLUG}}/skill.md
```

---

## Install via AI

Paste this into your local AI agent (Claude Code, Cursor, Copilot CLI, Gemini CLI, or any agent that can fetch a URL and write a file):

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/{{SKILL_SLUG}}/skill.md

2. Create the directory `.claude/skills/{{SKILL_SLUG}}/` in my current project.
   (Use `~/.claude/skills/{{SKILL_SLUG}}/` instead if I want it available globally.)

3. Save the fetched content verbatim as `SKILL.md` inside that directory.
   Do not rewrite, summarise, or "improve" the instructions, and keep the
   YAML frontmatter exactly as-is.

4. Confirm the skill is registered, then tell me the phrase that triggers it.
```

### Install manually

```bash
mkdir -p .claude/skills/{{SKILL_SLUG}}
curl -fsSL https://raw.githubusercontent.com/unix14/my-skills/main/skills/{{SKILL_SLUG}}/skill.md \
  -o .claude/skills/{{SKILL_SLUG}}/SKILL.md
```

### Install by copy-paste

Open [`skill.md`](./skill.md), copy everything below the frontmatter, and paste it
as a system prompt, custom instruction, or custom GPT / Gem / Project instruction
in whichever LLM interface you use.

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
