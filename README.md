# my-skills

**A curated, open collection of practical AI skills — in plain Markdown.**

[![Skills](https://img.shields.io/badge/skills-7-blue)](#the-catalog)
[![Format](https://img.shields.io/badge/format-pure%20markdown-lightgrey)](#how-it-works)
[![Dependencies](https://img.shields.io/badge/dependencies-none-success)](#how-it-works)
[![Works with](https://img.shields.io/badge/works%20with-any%20LLM-8A2BE2)](#quick-start)
[![License](https://img.shields.io/badge/license-MIT-green)](./LICENSE)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-orange)](#contributing)

No MCP servers. No build step. No CI. No install script. No API keys.
Every skill is one `.md` file you can read in two minutes, paste anywhere, and
fully understand before you run it.

---

## Disclaimer — read this first

This repository is a **curated collection of tools, not a claim of ownership.**

The patterns here — Socratic questioning, rubber duck debugging, red teaming,
plain-language explanation, problem-first product specs — were invented by
other people, most of them long before LLMs existed. This repo contributes the
packaging: turning those public, well-documented ideas into tight, modular
prompts that behave consistently.

- **Every skill credits its source.** No exceptions. If a skill has no
  `Credits & Origin` section with a working link, it does not belong here.
- **Original authors retain all rights** to their own work, wording, and
  concepts. No text is copied from the sources credited; each `skill.md` is an
  independent prompt that operationalises a publicly documented pattern.
- **The MIT license covers this repository's own prompt text only** — the
  curation and wording in these files. It makes no claim over the underlying
  ideas or anyone else's writing.
- If you are an author credited here and want the attribution corrected,
  expanded, or the skill removed entirely —
  [open an issue](../../issues) and it will be handled.

**Safety:** zero secrets, zero PII, zero telemetry, zero network calls. These
are text files. Read them before you use them, the same way you would read a
shell script before you pipe it to your shell.

---

## The catalog

| Skill | What it does | Category | Credit / origin |
|---|---|---|---|
| [**grill-me**](./skills/grill-me/) | A demanding interviewer that escalates one layer per answer until your understanding breaks, then debriefs you on exactly what cracked. | Thinking & Critique | [Socratic method](https://en.wikipedia.org/wiki/Socratic_method) · [testing effect](https://en.wikipedia.org/wiki/Testing_effect) |
| [**tldr**](./skills/tldr/) | Compresses any text, thread, or transcript to a 30-word takeaway, 3–5 key points, and the actions it implies. 150-word hard ceiling. | Communication & Tone | [BLUF](https://en.wikipedia.org/wiki/BLUF_(communication)) · [inverted pyramid](https://en.wikipedia.org/wiki/Inverted_pyramid_(journalism)) |
| [**rubber-duck**](./skills/rubber-duck/) | A Socratic debugging partner that refuses to give you the answer and asks the questions that make you find it. | Code & Debugging | [*The Pragmatic Programmer*](https://pragprog.com/titles/tpp20/the-pragmatic-programmer-20th-anniversary-edition/), Hunt & Thomas |
| [**devils-advocate**](./skills/devils-advocate/) | Steel-mans your plan, then attacks it across nine fronts — strongest objection first, each with the evidence that would refute it. | Thinking & Critique | [Red teaming](https://en.wikipedia.org/wiki/Red_team) · [pre-mortem](https://hbr.org/2007/09/performing-a-project-premortem), Gary Klein |
| [**eli5**](./skills/eli5/) | Explains hard things to a curious adult: a mapped analogy, where that analogy breaks, and the real term only at the end. | Learning & Explanation | [r/explainlikeimfive](https://www.reddit.com/r/explainlikeimfive/) · [Feynman technique](https://fs.blog/feynman-technique/) |
| [**prd-generator**](./skills/prd-generator/) | Interrogates a raw idea in batches of 5–8 questions, then writes a 14-section PRD. Flags every inference as `[ASSUMPTION]`. | Product & Ideation | [Marty Cagan / SVPG](https://www.svpg.com/articles/) · [Working Backwards](https://www.workingbackwards.com/), Bryar & Carr |
| [**humanizer**](./skills/humanizer/) | Deletes the AI tells and rewrites copy 20–40% shorter, without changing a single claim, number, or hedge. | Communication & Tone | [Orwell, *Politics and the English Language*](https://www.orwellfoundation.com/the-orwell-foundation/orwell/essays-and-other-works/politics-and-the-english-language/) · [Paul Graham](https://paulgraham.com/talk.html) |

### By category

- **Code & Debugging** — [rubber-duck](./skills/rubber-duck/)
- **Product & Ideation** — [prd-generator](./skills/prd-generator/)
- **Communication & Tone** — [tldr](./skills/tldr/), [humanizer](./skills/humanizer/)
- **Thinking & Critique** — [grill-me](./skills/grill-me/), [devils-advocate](./skills/devils-advocate/)
- **Learning & Explanation** — [eli5](./skills/eli5/)

---

## Quick start

There are two ways to use any skill here. Both take under a minute.

### Method A — copy-paste (works in every LLM interface)

1. Open the skill's folder and click [`skill.md`](./skills/prd-generator/skill.md).
2. Copy everything **below the YAML frontmatter** (the part after the closing `---`).
3. Paste it wherever your tool keeps standing instructions:
   - **ChatGPT** → Custom GPT instructions, or a Project's instructions
   - **Claude** → a Project's custom instructions, or the top of a new chat
   - **Gemini** → a Gem's instructions
   - **Cursor / Copilot / Windsurf** → a rules or instructions file
   - **Anything else** → the system prompt field, or just the first message
4. Describe your task. The skill takes over from there.

The frontmatter is harmless if you paste it too — it just helps agent
frameworks register the skill by name.

### Method B — let your AI agent install it

Every skill is served over the GitHub raw URL, so any agent that can fetch a URL
and write a file can install it for you. Paste this, with the skill name
substituted:

```text
Install a new skill for me from a public URL.

1. Fetch the raw Markdown at:
   https://raw.githubusercontent.com/unix14/my-skills/main/skills/<skill-name>/skill.md

2. Create the directory `.claude/skills/<skill-name>/` in my current project.
   (Use `~/.claude/skills/<skill-name>/` instead if I want it available globally.)

3. Save the fetched content verbatim as `SKILL.md` inside that directory.
   Do not rewrite, summarise, or "improve" the instructions, and keep the
   YAML frontmatter exactly as-is.

4. Confirm the skill is registered, then tell me the phrase that triggers it.
```

Each skill's own README carries this prompt with the URL already filled in.

### Method C — `curl`, for people who prefer the shell

```bash
SKILL=prd-generator
mkdir -p ".claude/skills/$SKILL"
curl -fsSL "https://raw.githubusercontent.com/unix14/my-skills/main/skills/$SKILL/skill.md" \
  -o ".claude/skills/$SKILL/SKILL.md"
```

Install all seven at once:

```bash
for SKILL in grill-me tldr rubber-duck devils-advocate eli5 prd-generator humanizer; do
  mkdir -p ".claude/skills/$SKILL"
  curl -fsSL "https://raw.githubusercontent.com/unix14/my-skills/main/skills/$SKILL/skill.md" \
    -o ".claude/skills/$SKILL/SKILL.md"
done
```

---

## How it works

Each skill is a self-contained folder:

```
my-skills/
├── README.md                              <- you are here
├── LICENSE
├── skills/
│   ├── devils-advocate/
│   │   ├── README.md                      <- purpose, usage, install, credits
│   │   └── skill.md                       <- the raw prompt. this is the product.
│   ├── eli5/
│   │   ├── README.md
│   │   └── skill.md
│   ├── grill-me/
│   │   ├── README.md
│   │   └── skill.md
│   ├── humanizer/
│   │   ├── README.md
│   │   └── skill.md
│   ├── prd-generator/
│   │   ├── README.md
│   │   └── skill.md
│   ├── rubber-duck/
│   │   ├── README.md
│   │   └── skill.md
│   └── tldr/
│       ├── README.md
│       └── skill.md
└── templates/
    └── skill-readme-template.md           <- copy this to add a skill
```

- **`skill.md`** is the whole skill: minimal YAML frontmatter (`name`,
  `description`) followed by plain Markdown instructions. Model-agnostic. No
  tool calls, no MCP, no shell, no hidden state.
- **`README.md`** is for humans deciding whether to use it: what it does, when
  *not* to use it, the raw link, the install prompt, and the credits.
- **Modular by design.** Skills never reference each other at runtime. Install
  one or install all seven; nothing breaks either way.

### Design rules every skill follows

1. **One job.** A skill that does two things does neither reliably.
2. **Behavioural, not topical.** These change *how* the model works, not what
   it knows.
3. **Tells the model what to refuse.** The constraints are usually more valuable
   than the instructions.
4. **No fabrication.** Every skill that could invent a fact is explicitly told
   not to, and told to mark gaps instead.
5. **Readable in two minutes.** If you cannot audit it quickly, you should not
   run it.
6. **Credited.** See the disclaimer above.

---

## Contributing

New skills are welcome. The bar is attribution and discipline, not volume.

1. Copy [`templates/skill-readme-template.md`](./templates/skill-readme-template.md)
   to `skills/<your-skill>/README.md` and fill in every `{{PLACEHOLDER}}`.
2. Write `skills/<your-skill>/skill.md` — frontmatter plus plain Markdown.
3. Add a row to the catalog table above, with a category and a real credit link.
4. Open a PR.

**A PR will be rejected if:** the skill has no source attribution or the link is
dead; it requires MCP, tooling, or a build step; it contains secrets, API keys,
PII, or real client names; it duplicates an existing skill without being clearly
better; or it is a topical knowledge dump rather than a behavioural instruction set.

Rewording someone else's published prompt and crediting them properly is fine
and welcome. Rewording it and claiming it is not.

---

## License

[MIT](./LICENSE) — covering this repository's own prompt text and documentation.
The ideas and patterns these prompts implement belong to the authors credited in
each skill's `Credits & Origin` section, and this license makes no claim over
their work.
