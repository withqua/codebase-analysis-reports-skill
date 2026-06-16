# HTML Template for Human-Facing Reports

The template at `references/html-template.html` is the canonical starting point for all human-facing codebase analysis reports.

## Key design decisions (v1.3.0)

- **Self-contained:** No external CSS dependencies. Only Mermaid loads from CDN (removable if no diagrams).
- **Dark/light mode:** Automatic via `prefers-color-scheme` media query. All colors are CSS custom properties.
- **Responsive:** Single-column, max-width 900px. Mobile breakpoint at 640px.
- **Certainty labels:** Four-tier color-coded badges — 확인됨(green), 추정(yellow), 불확실(orange), 분석불가(red).
- **Print-optimized:** Separate `@media print` stylesheet strips backgrounds, forces black text, avoids page breaks inside code blocks and diagrams.
- **Sections:** 13 standard sections in fixed order (Header → TOC → TL;DR → ... → Footer).

## Placeholder System

The template uses `{{PLACEHOLDER}}` syntax. Replace each with actual content. Delete any section block (including its HTML comment wrapper) that is not applicable.

## Size Budget

Template boilerplate (CSS + structure): ~14 KB. Content budget: ~16 KB. Total cap: 30 KB (`wc -c`).

## Dual-Sync Pitfall

When updating this skill, changes must be applied to **both** locations:
1. Git repository (`/home/jetson/codebase-analysis-reports-skill/`) — for version control
2. Local Hermes skill directory (`~/.hermes/skills/software-development/codebase-analysis-reports/`) — for active use

Syncing only one causes drift. After editing the repo, run:
```bash
cp /path/to/repo/SKILL.md ~/.hermes/skills/software-development/codebase-analysis-reports/SKILL.md
cp -r /path/to/repo/references/ ~/.hermes/skills/software-development/codebase-analysis-reports/references/
```
