# Codebase Analysis Reports Skill

<p align="center">
  <a href="README.md">한국어</a> •
  <a href="README.en.md">English</a> •
  <a href="README.ja.md">日本語</a> •
  <a href="README.zh.md">中文</a> •
  <a href="README.es.md">Español</a>
</p>

这是一个用于 Hermes Agent 的代码库分析报告技能，强调简洁、可读和基于证据。

它会引导 Hermes 分析代码库、插件、库、框架或仓库，并生成两个产物。

1. `CODEBASE_ANALYSIS_HUMAN.md` — 以用户主要语言为中心、适合人阅读的分析报告
2. `CODEBASE_ANALYSIS_AGENT.md` — 供后续 AI Agent 直接接手的执行型 handoff(交接) 报告

## 核心规则

- 先理解 repo(仓库)整体结构和 `entrypoint`(执行最先进入的位置)。
- 再绘制 component map(组件地图)。
- 最后根据用户目的深入分析。
- 关键结论必须附带 file path(文件路径)和 line anchor(行号依据)。
- 人类报告/Agent 报告各自按 `wc -c` 控制在 7KB 以下。
- 没有证据的问题或风险不要写。
- 无法确认的部分写入 `Analysis Limits / Uncertainty`(分析限制/不确定性)，不要猜。
- 像 `manifest`(告诉宿主程序/插件的名称、入口、权限和 hook 的配置文件) 这类术语，首次出现时要简短解释。
- 函数名、字段名、命令等英文标识符保持原文，必要时在括号里解释。

## 安装

公开仓库安装:

```bash
hermes skills install https://raw.githubusercontent.com/withqua/codebase-analysis-reports-skill/main/SKILL.md
```

手动安装:

```bash
git clone https://github.com/withqua/codebase-analysis-reports-skill.git
mkdir -p ~/.hermes/skills/software-development/codebase-analysis-reports
cp codebase-analysis-reports-skill/SKILL.md ~/.hermes/skills/software-development/codebase-analysis-reports/SKILL.md
```

如果 Hermes 已在运行，请执行 `/reload-skills` 或重启 CLI。

## 使用方式

```bash
hermes -s codebase-analysis-reports
```

在聊天中:

```text
/skill codebase-analysis-reports
```

请求示例:

```text
请分析 /path/to/repo。生成一份人类阅读报告和一份 AI Agent 交接报告。
```

## 文件

- `SKILL.md` — 实际 Hermes Agent 技能
- `README.md` — 韩语指南
- `README.en.md` — English guide
- `README.ja.md` — 日本語ガイド
- `README.zh.md` — 中文指南
- `README.es.md` — guía en español
- `LICENSE` — MIT License
