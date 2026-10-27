# socratic-tutor

A skill that makes an AI assistant tutor you through a problem instead of solving it for you. One sitting, no files, no tracking.

You write the code. The tutor asks the questions, points at the docs, reviews what you wrote, and tells you plainly where your understanding stands.

---

## Why a separate skill

[guided-learning](https://github.com/jmstudyacc/guided-learning-skill) runs multi-session learning: topic packs, homework, spaced retrieval, checkpoints. That's the right tool for learning a subject over weeks, and too much machinery for "help me work this one out myself".

This is the tutoring core on its own. Nothing is written to disk and nothing carries forward — what you keep is what you now understand.

## What it does

- **Doesn't write the code you're learning.** Failing tests, interface specs, out-of-scope scaffolding, analogies from a different domain, and a reference implementation *after* your attempt are fine. Filled-in method bodies are not.
- **Predict before you run.** You state what you expect before executing. The gap between prediction and reality is where the learning lands.
- **A stuck ladder.** Five rungs, from "what did you try, and what did you expect?" up to "here's the answer, now solve this variant". Fifteen minutes on the same wall climbs a rung.
- **Honest assessment.** Concepts are named *can use* / *can explain* / *can design with*. No praise without evidence, and "I get it" doesn't count.
- **A close, in chat.** What's solid, what's shaky, one question to answer from memory in a few days, and optionally one small exercise.

## Modes

Tutor is the default. The skill drops into Lookup on its own when you ask a factual question, then returns to Tutor.

| You say | What happens |
| --- | --- |
| A conceptual or build question | Tutor — Socratic, you do the work |
| A factual question (API name, flag syntax, "does X support Y") | Lookup — one-line answer, no follow-up |
| `lookup: …` / `tutor mode` | Forces that mode |
| `just tell me` | Direct answer, no negotiation, flagged at the close to revisit |

## Install

**Terminal-based coding assistants** (Claude Code, OpenCode, Codex)

```bash
git clone https://github.com/jmstudyacc/socratic-tutor-skill.git
cp -r socratic-tutor-skill/socratic-tutor <your-skills-dir>/
```

| Tool | Skills directory |
| --- | --- |
| Claude Code | `~/.claude/skills/` (personal) or `.claude/skills/` inside a repo |
| OpenCode | `~/.config/opencode/skills/` or `.opencode/skills/` inside a repo |
| Codex | `~/.codex/skills/` or `.codex/skills/` inside a repo |

The path must be `<skills-dir>/socratic-tutor/SKILL.md` — one level too deep is the most common install error. Start a new session to pick it up.

**Chat apps that take a skill ZIP** (Claude.ai, Claude Desktop)

```bash
git clone https://github.com/jmstudyacc/socratic-tutor-skill.git
cd socratic-tutor-skill && zip -r socratic-tutor.zip socratic-tutor
```

Upload `socratic-tutor.zip` via the app's skills area. Don't use GitHub's "Download ZIP" button — it nests everything one level too deep.

## Quick start

> Tutor me through writing a SQLite migration runner in Go. Don't give me the answer.

Or invoke it directly with `/socratic-tutor`.

## Using it alongside guided-learning

Both skills respond to phrases like "don't write it for me". If you install both, this one is scoped to single-sitting requests and hands multi-session ones to guided-learning — but narrowing guided-learning's own trigger list makes the split more reliable.

## Licence

MIT — see [license](license).
