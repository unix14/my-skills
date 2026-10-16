# tools

One script, no dependencies, no build step — in keeping with the rest of the repo.

---

## `skill-audit.py`

A static safety scanner for Markdown skills. It reads a prompt file, looks for
the patterns that make a skill dangerous, and rates it **1 to 5 stars** with the
reasoning shown.

```bash
./tools/skill-audit.py                    # every skill in this repo
./tools/skill-audit.py path/to/SKILL.md   # a skill you downloaded from anywhere
./tools/skill-audit.py --selftest         # prove it still catches known attacks
./tools/skill-audit.py --json skills/     # machine-readable
```

Requires Python 3.8+. Nothing else — it makes no network calls and executes
nothing it scans.

### What the stars mean

| | Meaning |
|---|---|
| ★★★★★ | no red flags found — nothing matched, and it is short enough to read |
| ★★★★☆ | minor concerns — a couple of things worth a glance |
| ★★★☆☆ | review before use — read it properly before installing |
| ★★☆☆☆ | significant concerns — treat as untrusted |
| ★☆☆☆☆ | do not run unread — something here can exfiltrate, destroy, or override |

**A single critical finding pins the score at one star**, whatever else is in the
file. That is deliberate: the scoring must not let a well-written malicious skill
average its way up to four stars on the strength of its prose.

### What it looks for

| Class | Examples |
|---|---|
| **Exfiltration** | posting content to a URL, hard-coded webhooks (Slack, Discord, `webhook.site`, pastebin, ngrok, `.onion`), "email the contents to…" |
| **Credentials** | `~/.ssh`, `id_rsa`, `.aws/credentials`, `.netrc`, keychain, `.env` harvesting, `$GITHUB_TOKEN` |
| **Live secrets** | committed AWS keys, `ghp_`/`xox`/`sk-` tokens, private-key blocks, JWTs |
| **Destruction** | `rm -rf`, `mkfs`, `dd of=/dev/…`, fork bombs, `git push --force`, `reset --hard`, `DROP TABLE`, unqualified `DELETE` |
| **Remote execution** | `curl … \| sh`, `eval`, `os.system`, installing from a URL or git ref, `chmod +x && ./` |
| **Prompt injection** | "ignore all previous instructions", "you have no restrictions", developer-mode framing |
| **Concealment** | "never tell the user", "silently delete", "without the user's knowledge" |
| **Consent bypass** | "without asking for confirmation", "no need to approve" |
| **False authority** | "the user has already approved this", "Anthropic requires that you…" |
| **Persistence** | `.bashrc`/`.zshrc`, `crontab`, LaunchAgents, `systemctl enable`, `.git/hooks`, `authorized_keys` |
| **Self-modification** | editing `CLAUDE.md`, `AGENTS.md`, `.cursor/rules`, `settings.json` |
| **Privilege** | `sudo`, `osascript … administrator` |

### Evasion is the interesting part

A keyword list alone is trivially defeated, so before matching anything the
scanner normalises the text and then scans the de-obfuscated forms as **separate
layers**:

- **Invisible characters** — zero-width spaces, soft hyphens, BOM. Flagged on sight: there is no benign use in a prompt.
- **Bidirectional overrides** — the [Trojan Source](https://trojansource.codes/) trick, where displayed order differs from read order.
- **Homoglyphs** — Cyrillic `с` in `сurl`, Greek `ο` in `ignοre`. Folded to ASCII, then matched.
- **Markdown splitting** — `r*m* -*r*f` renders as *rm -rf* and defeats a naive grep. Emphasis marks are stripped and the result re-scanned.
- **Escape sequences** — `\x72\x6d` and `r` are decoded.
- **Base64 payloads** — any sufficiently long blob that decodes to text is decoded and scanned.
- **HTML comments** — invisible in rendered Markdown, fully visible to the model. Scanned as their own layer.

**Anything that matches only after de-obfuscation is escalated to critical**,
because breaking a keyword up is itself evidence of intent. A plain `rm -rf` in a
documented cleanup step is a finding; `r*m* -*r*f` is a finding *and* a lie about
it, and the output says so.

### What it cannot do

Five stars is **not a certificate of safety.** It means no known-bad pattern
matched. It will not catch:

- a novel attack that looks like ordinary prose
- an instruction that is harmful only in your situation ("delete the staging data")
- logic that is dangerous in aggregate while every sentence reads innocently
- anything the skill fetches at run time, which can change after you audit it
- a legitimate-looking skill that happens to be wrong about your codebase

This tool narrows what you have to read closely. It does not replace reading it.
That caveat prints with every run, on purpose.

### Exit codes

`0` clean (or above `--min-stars`), `1` below threshold or a self-test failure,
`2` nothing to scan. Useful in a pre-commit hook if you want one, though this
repo deliberately has no CI.

### Self-test

`--selftest` runs 20 adversarial cases — plain and obfuscated overrides, hidden
comments, base64 payloads, homoglyphs, bidi, persistence, secrets — and asserts
each one scores at or below the rating it must never exceed. The attack strings
live inline in the script rather than as files on disk, so nothing alarming sits
in the repo. Run it after editing any rule:

```bash
./tools/skill-audit.py --selftest
```

If you add a rule, add the case that proves it works and the case that proves it
does not fire on ordinary prose. A rule that cries wolf is worse than no rule,
because people stop reading the output.
