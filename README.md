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
packaging, and in some cases nothing but a folder to keep someone else's file in.

Skills here come in two kinds, and each one says which it is at the top of its
`Credits & Origin` section:

1. **Redistributed verbatim.** The file is a byte-for-byte copy of a named
   author's published skill, kept under the license they released it under, with
   their copyright notice included in the folder. The wording is theirs, not
   ours. [`grill-me`](./skills/grill-me/) is Matt Pocock's, copied exactly.
2. **Independently written from a documented pattern.** The prompt is ours; the
   idea is not. These credit the technique and the people who established it.

- **Every skill credits its source.** No exceptions. If a skill has no
  `Credits & Origin` section with a working link, it does not belong here.
- **Original authors retain all rights** to their own work and wording. Where a
  skill is a verbatim copy, their license governs it and their notice ships with
  it — read that notice before you redistribute it further, because its terms
  bind you too.
- **The MIT license at the root covers only this repository's own text** — the
  prompts written here, plus the documentation. It makes no claim over anyone
  else's writing, and it does not override a license shipped inside a skill
  folder.
- If you are an author credited here and want the attribution corrected,
  expanded, or the skill removed entirely —
  [open an issue](../../issues) and it will be handled.

**Safety:** zero secrets, zero PII, zero telemetry, zero network calls. These
are text files. Read them before you use them, the same way you would read a
shell script before you pipe it to your shell.

### Prior art

- [**mattpocock/skills**](https://github.com/mattpocock/skills) — Matt Pocock's
  own `.agents` directory, MIT licensed. [`grill-me`](./skills/grill-me/) here
  **is his skill, copied verbatim** — both
  [`grill-me`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md)
  and the
  [`grilling`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md)
  implementation it delegates to, byte for byte, with his notice in the folder.
  His repo has around thirty more skills, several better than anything written
  here. Go there first.

---

## The catalog

| Skill | What it does | Category | Credit / origin |
|---|---|---|---|
| [**grill-me**](./skills/grill-me/) | Maps your plan as a design tree and interviews you in rounds — asking every question whose prerequisites are settled, each with a recommended answer — until nothing is left assumed. | Thinking & Critique | **Verbatim copy.** [`grill-me`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) + [`grilling`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md) by [Matt Pocock](https://github.com/mattpocock), MIT |
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
for SKILL in tldr rubber-duck devils-advocate eli5 prd-generator humanizer; do
  mkdir -p ".claude/skills/$SKILL"
  curl -fsSL "https://raw.githubusercontent.com/unix14/my-skills/main/skills/$SKILL/skill.md" \
    -o ".claude/skills/$SKILL/SKILL.md"
done

# grill-me is Matt Pocock's and ships as two files; take it from his repo.
for PART in grill-me grilling; do
  mkdir -p ".claude/skills/$PART"
  curl -fsSL "https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/$PART/SKILL.md" \
    -o ".claude/skills/$PART/SKILL.md"
done
```

`grill-me` is a trigger that delegates to `grilling`, so installing only one of
the two does nothing. See [its README](./skills/grill-me/) for why.

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
│   ├── grill-me/                      <- Matt Pocock's skill, copied verbatim
│   │   ├── LICENSE-mattpocock         <- his notice, as his license requires
│   │   ├── README.md
│   │   ├── grilling.md                <- the implementation skill.md delegates to
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

If your skill is a re-implementation of a **specific published skill** rather
than of a general technique, lead the `Credits & Origin` section with it: the
author, a link to the original file, its license, what your version does
differently, and when the reader should prefer the original.

If you are **redistributing someone's file verbatim**, the bar is higher and it
is not optional:

- Their license must actually permit redistribution. Check it. No license means
  no permission — link to it instead of copying it.
- Copy their notice into the skill folder (`LICENSE-<author>`), and say in the
  README that the wording is theirs and the copy is byte-exact.
- Do not edit the file, not even the frontmatter. If it needs changing, it is a
  re-implementation and is credited as one.
- Point readers at the upstream repo, not just the file.

[`grill-me`](./skills/grill-me/) is the worked example of a verbatim copy.

---

## License

[MIT](./LICENSE) — covering this repository's own prompt text and documentation.
The ideas and patterns these prompts implement belong to the authors credited in
each skill's `Credits & Origin` section, and this license makes no claim over
their work.
