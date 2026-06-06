# Codebase Analysis Reports Skill

<p align="center">
  <a href="README.md">한국어</a> •
  <a href="README.en.md">English</a> •
  <a href="README.ja.md">日本語</a> •
  <a href="README.zh.md">中文</a> •
  <a href="README.es.md">Español</a>
</p>

Hermes Agent 用の、簡潔で根拠付きのコードベース分析レポート用スキルです。

コードベース、プラグイン、ライブラリ、フレームワーク、リポジトリを分析し、次の2つの成果物を作るように案内します。

1. `CODEBASE_ANALYSIS_HUMAN.md` — ユーザーの主言語を中心にした、人間が読みやすい分析レポート
2. `CODEBASE_ANALYSIS_AGENT.md` — 後続のAIエージェントが引き継げる実行中心の handoff(引き継ぎ) レポート

## 基本ルール

- まず repo(リポジトリ)全体の構造と `entrypoint`(実行が最初に入る場所)を把握します。
- 次に component map(構成要素の地図)を作ります。
- 最後にユーザーの目的に合わせて深掘りします。
- 主要な主張には file path(ファイルパス)と line anchor(行番号の根拠)を付けます。
- 人間用/エージェント用レポートは、それぞれ `wc -c` 基準で7KB以下にします。
- 根拠のない問題やリスクは書きません。
- 分からない部分は推測せず、`Analysis Limits / Uncertainty`(分析上の限界/不確実性)に書きます。
- `manifest`(プログラム/プラグインの名前、入口、権限、hookをホストに伝える設定ファイル)のような用語は、初出時に短く説明します。
- 関数名、フィールド名、コマンドなどの英語識別子は原文を残し、必要なら括弧で説明します。

## インストール

公開リポジトリからインストール:

```bash
hermes skills install https://raw.githubusercontent.com/withqua/codebase-analysis-reports-skill/main/SKILL.md
```

手動インストール:

```bash
git clone https://github.com/withqua/codebase-analysis-reports-skill.git
mkdir -p ~/.hermes/skills/software-development/codebase-analysis-reports
cp codebase-analysis-reports-skill/SKILL.md ~/.hermes/skills/software-development/codebase-analysis-reports/SKILL.md
```

Hermes がすでに起動している場合は、`/reload-skills` を実行するか CLI を再起動してください。

## 使い方

```bash
hermes -s codebase-analysis-reports
```

チャット内では:

```text
/skill codebase-analysis-reports
```

依頼例:

```text
/path/to/repo を分析してください。人間用レポートとAIエージェント用引き継ぎレポートを作ってください。
```

## ファイル

- `SKILL.md` — 実際の Hermes Agent スキル
- `README.md` — 韓国語ガイド
- `README.en.md` — English guide
- `README.ja.md` — 日本語ガイド
- `README.zh.md` — 中文指南
- `README.es.md` — guía en español
- `LICENSE` — MIT License
