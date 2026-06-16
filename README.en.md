# Codebase Analysis Reports Skill

<p align="center">
  <a href="README.md">한국어</a> •
  <a href="README.en.md">English</a> •
  <a href="README.ja.md">日本語</a> •
  <a href="README.zh.md">中文</a> •
  <a href="README.es.md">Español</a>
</p>

A Hermes Agent skill for concise, evidence-backed codebase analysis reports.

It guides Hermes to analyze a codebase, plugin, library, framework, or repository and produce two artifacts.

1. `CODEBASE_ANALYSIS_HUMAN.html` — self-contained HTML report with standardized design (dark/light mode, responsive, code highlighting, Mermaid diagrams, print-optimized)
2. `CODEBASE_ANALYSIS_AGENT.md` — operational markdown AI-agent handoff report for follow-up work

## Core rules

- Understand the repo structure and `entrypoint`(where execution first enters) first.
- Build a component map before drilling into details.
- Deep-dive according to the user's purpose.
- Back key claims with file paths and line anchors.
- Keep human report ≤ 30KB (HTML), agent report ≤ 7KB (MD) by `wc -c`.
- HTML reports use the `references/html-template.html` template.
- Do not invent problems or risks without evidence.
- Put unknowns in `Analysis Limits / Uncertainty`.
- Explain unfamiliar terms on first use, e.g. `manifest`(a config file that tells the host a program/plugin name, entrypoints, permissions, and hooks).
- Preserve exact code identifiers, then add short parenthesized explanations when helpful.

## Install

Public repo install:

```bash
hermes skills install https://raw.githubusercontent.com/withqua/codebase-analysis-reports-skill/main/SKILL.md
```

Manual install:

```bash
git clone https://github.com/withqua/codebase-analysis-reports-skill.git
mkdir -p ~/.hermes/skills/software-development/codebase-analysis-reports
cp codebase-analysis-reports-skill/SKILL.md ~/.hermes/skills/software-development/codebase-analysis-reports/SKILL.md
```

If Hermes is already running, use `/reload-skills` or restart the CLI.

## Usage

```bash
hermes -s codebase-analysis-reports
```

In chat:

```text
/skill codebase-analysis-reports
```

Example request:

```text
Analyze /path/to/repo. My goal is to understand the plugin architecture and reusable parts of this codebase. Create a human report and an AI-agent handoff report for that purpose.
```

## Files

- `SKILL.md` — actual Hermes Agent skill
- `references/html-template.html` — human-report HTML template (design spec)
- `README.md` — Korean guide
- `README.en.md` — English guide
- `README.ja.md` — Japanese guide
- `README.zh.md` — Chinese guide
- `README.es.md` — Spanish guide
- `LICENSE` — MIT License
