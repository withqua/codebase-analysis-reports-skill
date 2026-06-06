# Codebase Analysis Reports Skill

<p align="center">
  <a href="README.md">한국어</a> •
  <a href="README.en.md">English</a> •
  <a href="README.ja.md">日本語</a> •
  <a href="README.zh.md">中文</a> •
  <a href="README.es.md">Español</a>
</p>

Hermes Agent용 코드베이스 분석 보고서 스킬입니다.

코드베이스, 플러그인, 라이브러리, 프레임워크, 저장소를 분석한 뒤 두 산출물을 만들게 합니다.

1. `CODEBASE_ANALYSIS_HUMAN.md` — 사용자의 주 언어 중심, 사람이 읽기 좋은 분석 보고서
2. `CODEBASE_ANALYSIS_AGENT.md` — 후속 AI 에이전트가 바로 이어받는 실행 중심 handoff(인수인계) 보고서

## 핵심 원칙

- 먼저 repo(저장소) 전체 구조와 `entrypoint`(실행이 처음 들어오는 지점)를 파악합니다.
- 그다음 component map(구성요소 지도)을 만듭니다.
- 마지막에 사용자의 목적에 맞춰 깊게 분석합니다.
- 주요 주장에는 file path(파일 경로)와 line anchor(라인 근거)를 붙입니다.
- 인간용/에이전트용 보고서는 각각 `wc -c` 기준 7KB 이하입니다.
- 근거 없는 문제/리스크는 쓰지 않습니다.
- 분석하지 못한 부분은 추측하지 않고 `Analysis Limits / Uncertainty`(분석 한계/불확실성)에 씁니다.
- `manifest`(프로그램/플러그인이 이름, 진입점, 권한, hook을 호스트에 알려주는 설정 파일)처럼 낯선 용어는 첫 등장 때 짧게 설명합니다.
- 함수명/필드명/명령어 같은 영어 식별자는 원문 유지 + 괄호 설명을 붙입니다.

## 설치

공개 저장소이므로 HTTP(S) URL로 설치할 수 있습니다.

```bash
hermes skills install https://raw.githubusercontent.com/withqua/codebase-analysis-reports-skill/main/SKILL.md
```

수동 설치가 필요하면:

```bash
git clone https://github.com/withqua/codebase-analysis-reports-skill.git
mkdir -p ~/.hermes/skills/software-development/codebase-analysis-reports
cp codebase-analysis-reports-skill/SKILL.md ~/.hermes/skills/software-development/codebase-analysis-reports/SKILL.md
```

이미 Hermes 세션이 떠 있으면 `/reload-skills`를 실행하거나 CLI를 다시 시작하세요.

## 사용 예시

```bash
hermes -s codebase-analysis-reports
```

대화 중에는:

```text
/skill codebase-analysis-reports
```

예시 요청:

```text
/path/to/repo 를 분석해줘. 인간용 분석 파일과 AI 에이전트용 분석 파일을 만들어줘.
```

## 파일

- `SKILL.md` — 실제 Hermes Agent 스킬 정의
- `README.md` — 한국어 안내
- `README.en.md` — English guide
- `README.ja.md` — 日本語ガイド
- `README.zh.md` — 中文指南
- `README.es.md` — guía en español
- `LICENSE` — MIT License
