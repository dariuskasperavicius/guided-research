# Guided Research

A skill for AI agents (Claude Code, Kimi Code CLI, and others that support the `SKILL.md` format): in-depth research on any topic using a fixed process—first gathering input through a guided dialogue, then conducting the research, and finally producing a `.md` report.

## What It Does

It conducts in-depth research on a topic and produces a structured report covering areas such as:

- Competitive analysis
- Audience research and user pain points
- Market, niche, and technology analysis
- Gathering source material on a topic for content creation

**Core idea:** 80% of research quality depends on the quality of the input, yet users rarely know how to provide that input on their own. That is why the skill does not begin researching immediately. It first guides the user step by step through gathering the necessary input (goal → context → structure → style → sources), asking questions with suggested answers, and only then begins the research.

## How It Works

1. **Goal** — defined together with the user using the formula: “I want to [action] so that [outcome]; to do that, I need to understand [what].” A topic (“research competitors”) is not a goal; it is the subject of the research.
2. **Context** — 4–6 questions generated for the specific goal, rather than a fixed list.
3. **Report structure + sample section** — a report outline and one example section to validate the format before spending time on research.
4. **Style** — pyramid structure + tables + diagrams / concise summary / in-depth long-form report.
5. **Sources** — the voices of real people (forums, Reddit, review sites) / official data / content published by market participants themselves / all of the above.
6. **Research** — 10+ search steps, followed after each round by a brief assessment of what was found and what is still missing.
7. **Report** — a `.md` file in the project's `reports/` directory. Quotes are always verbatim and attributed to their sources; nothing is fabricated.

The user is interrupted only 3–4 times throughout the entire workflow: more interruptions become frustrating, while fewer lead to a generic report.

## Installation

### Option 1: Copy It to Your Skills Directory

Clone the repository and copy the skill into your agent's skills directory:

```bash
git clone https://github.com/abbnv/guided-research.git
mkdir -p ~/.agents/skills/guided-research
cp guided-research/SKILL.md ~/.agents/skills/guided-research/SKILL.md
```

Supported locations depend on your agent:

| Agent | Path |
|---|---|
| Kimi Code CLI / universal | `~/.agents/skills/guided-research/` |
| Claude Code (user level) | `~/.claude/skills/guided-research/` |
| Claude Code (project level) | `.claude/skills/guided-research/` in the project root |

### Option 2: Download the File Only

You only need one file: `SKILL.md`. Download it and place it in your skills directory:

```bash
mkdir -p ~/.agents/skills/guided-research
curl -o ~/.agents/skills/guided-research/SKILL.md \
  https://raw.githubusercontent.com/abbnv/guided-research/main/SKILL.md
```

## Usage

After installation, the skill responds to requests such as:

- “Research my competitors”
- “Conduct market research on X”
- “Identify the pain points of product Y's users”
- “Prepare a report on topic Z”

The agent will begin by asking questions to gather input. Answering them greatly improves the quality of the final report.

## When It Is NOT a Good Fit

- A one-off fact-check requiring only 1–2 sentences
- Writing code

## License

MIT
