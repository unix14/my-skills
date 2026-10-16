# Agent compatibility

Every skill in this repo is a plain Markdown prompt with no dependencies, so it
runs anywhere you can set standing instructions. What changes between tools is
only **where the file goes**.

This page is the single source of truth for that. Each skill's README links here
rather than repeating it.

Everything below was checked against first-party documentation on
**2026-10-16**. These conventions move quickly — if something here is stale,
[open an issue](https://github.com/unix14/my-skills/issues).

---

## The short version

| Your tool | Where a skill goes | Notes |
|---|---|---|
| **Claude Code** | `.claude/skills/<name>/SKILL.md` (project)<br>`~/.claude/skills/<name>/SKILL.md` (personal) | File **must** be named `SKILL.md`, one directory per skill. The directory name becomes the command, unless frontmatter `name` overrides it. |
| **Claude apps** (claude.ai, desktop) | a Project's *custom instructions* | Paste the body. No file paths involved. |
| **ChatGPT** | Custom GPT → *Instructions*, or a Project's instructions | Paste the body. |
| **Gemini app** | a Gem's *instructions* | Paste the body. |
| **Gemini CLI** | `GEMINI.md` — `~/.gemini/GEMINI.md` globally, or in your workspace and its parents | Set `context.fileName` in `settings.json` to use another name; it takes a list, e.g. `["AGENTS.md", "GEMINI.md"]`. |
| **Cursor** | `.cursor/rules/<name>.mdc` | Must be `.mdc` — plain `.md` in that directory is **ignored**. Frontmatter fields: `description`, `globs`, `alwaysApply`. Cursor also reads `AGENTS.md`. |
| **GitHub Copilot** | `.github/copilot-instructions.md` (repo-wide)<br>`.github/instructions/<name>.instructions.md` (path-scoped, needs an `applyTo` glob) | Also reads `AGENTS.md` anywhere in the repo, nearest file winning, or a single root `CLAUDE.md` / `GEMINI.md`. |
| **Codex, Zed, Aider, Warp, Windsurf, Jules, goose, opencode, Devin, Junie, Amp, RooCode, Kilo Code, VS Code, Factory, Ona, Augment Code, UiPath** | `AGENTS.md` at the repo root | See below. |
| **Anything else** | its system-prompt or custom-instruction field | If it takes text, it takes these skills. |

---

## AGENTS.md — the portable route

[AGENTS.md](https://agents.md) is an open format: a "README for agents", plain
Markdown at the repository root, with no required fields or schema. Nested files
are allowed in monorepos and the **nearest file wins**.

It is the widest-reach option by a distance. The tools named on agents.md as
reading it: Codex, Jules, Factory, Aider, goose, opencode, Zed, Warp, VS Code,
Devin, UiPath Autopilot & Coded Agents, Junie, Amp, Cursor, RooCode, Gemini CLI,
Kilo Code, Phoenix, Semgrep, GitHub Copilot's coding agent, Ona, Windsurf, and
Augment Code.

To use a skill this way, append it under a clear heading:

```markdown
## Skill: tldr

<!-- from https://github.com/unix14/my-skills/tree/main/skills/tldr -->
<!-- paste everything below skill.md's frontmatter here -->

Use this when I ask for a TL;DR, a summary, or key takeaways.
...
```

One caveat worth knowing: `AGENTS.md` is **always-on context**, not an
on-demand skill. Everything in it is sent with every prompt. One or two skills
is fine; pasting all eight will bloat every request and the instructions will
start competing with each other. For more than a couple, prefer a tool with real
skill or rule files — Claude Code, Cursor, or Copilot — where each one loads only
when it is relevant.

**Claude Code does not read `AGENTS.md`.** It auto-loads `CLAUDE.md` and
`.claude/skills/`. Use the paths in the table above for it.

---

## Per-tool recipes

### Claude Code

```bash
SKILL=tldr
mkdir -p ".claude/skills/$SKILL"
curl -fsSL "https://raw.githubusercontent.com/unix14/my-skills/main/skills/$SKILL/skill.md" \
  -o ".claude/skills/$SKILL/SKILL.md"
```

Swap `.claude` for `~/.claude` to make it available in every project. Our
frontmatter already carries `name` and `description`, which is what Claude Code
uses to decide when to load a skill, so nothing needs editing.

### Cursor

The extension matters and the frontmatter is different, so this one needs a
small edit rather than a straight copy:

```bash
SKILL=tldr
mkdir -p .cursor/rules
curl -fsSL "https://raw.githubusercontent.com/unix14/my-skills/main/skills/$SKILL/skill.md" \
  -o ".cursor/rules/$SKILL.mdc"
```

Then replace our frontmatter with Cursor's:

```yaml
---
description: Compress text to a TL;DR, key points, and the actions implied
alwaysApply: false
---
```

Leave `alwaysApply: false` and keep the `description` sharp — that is how Cursor
decides to pull the rule in. Add `globs` only if the skill should attach to
particular file types, which for these behavioural skills it usually shouldn't.

### GitHub Copilot

For one skill repo-wide, append it to `.github/copilot-instructions.md`.

For several, keep them separate and scoped:

```bash
SKILL=tldr
mkdir -p .github/instructions
curl -fsSL "https://raw.githubusercontent.com/unix14/my-skills/main/skills/$SKILL/skill.md" \
  -o ".github/instructions/$SKILL.instructions.md"
```

Then swap our frontmatter for an `applyTo` glob — `applyTo: "**"` for a
behavioural skill that isn't tied to a file type:

```yaml
---
applyTo: "**"
---
```

Path-specific instructions are, per GitHub's docs, supported on GitHub.com only
for the Copilot coding agent and Copilot code review. For Copilot Chat in your
editor, `.github/copilot-instructions.md` is the reliable one.

### ChatGPT, Claude, Gemini, and other chat interfaces

No files. Open the skill's `skill.md`, copy everything **below** the YAML
frontmatter, and paste it into:

- **ChatGPT** — Custom GPT → *Instructions*, or a Project's instructions
- **Claude** — a Project's *custom instructions*
- **Gemini** — a Gem's *instructions*
- anything else — the system prompt field, or simply your first message

The frontmatter is harmless if you paste it too; it is only metadata for agent
frameworks.

### Gemini CLI

```bash
# append a skill to your global context file
curl -fsSL "https://raw.githubusercontent.com/unix14/my-skills/main/skills/tldr/skill.md" \
  >> ~/.gemini/GEMINI.md
```

Gemini CLI concatenates every context file it finds and sends them with each
prompt, so the always-on caveat above applies — keep it to a skill or two. If
you would rather keep one portable file, point it at `AGENTS.md` via
`context.fileName` in `settings.json`.

---

## Skill-specific notes

- **[`grill-me`](../skills/grill-me/)** is the one exception to "works
  anywhere". It is Matt Pocock's skill, redistributed verbatim, and it expects an
  agent with tools — it dispatches sub-agents to find facts rather than asking
  you. It also ships as **two files** (`skill.md` triggers, `grilling.md`
  implements), and installing one without the other does nothing. In a plain chat
  interface, paste `grilling.md` and ignore the trigger.
- Every other skill is self-contained in a single file and assumes nothing about
  the host.

---

## Sources

- [AGENTS.md](https://agents.md) — format, placement, and the list of supporting tools
- [Claude Code — Skills](https://code.claude.com/docs/en/skills) — `SKILL.md` naming and the two skill directories
- [Cursor — Rules](https://cursor.com/docs/context/rules) — `.cursor/rules/*.mdc`, frontmatter fields, AGENTS.md support
- [GitHub Copilot — Adding repository custom instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions) — the three instruction file types
- [Gemini CLI — Context files](https://geminicli.com/docs/cli/gemini-md.md) — `GEMINI.md` paths and `context.fileName`
