# Codebase Analysis Reports Skill

Hermes Agent용 코드베이스 분석 보고서 스킬입니다.

이 스킬은 코드베이스, 플러그인, 라이브러리, 프레임워크, 저장소를 분석할 때 다음 두 산출물을 만들도록 안내합니다.

1. `CODEBASE_ANALYSIS_HUMAN.md` — 사람이 읽기 좋은 한국어 중심 분석 보고서
2. `CODEBASE_ANALYSIS_AGENT.md` — 후속 AI 에이전트가 바로 이어받을 수 있는 실행 중심 handoff 보고서

## 핵심 원칙

- 먼저 저장소 전체 구조와 entrypoint(진입점)를 파악합니다.
- 그다음 component map(구성요소 지도)을 만듭니다.
- 마지막에 사용자의 목적에 맞춰 깊게 분석합니다.
- 모든 주요 주장에는 파일 경로와 line anchor(라인 근거)를 붙입니다.
- 근거 없는 문제/리스크는 쓰지 않습니다.
- 분석하지 못한 부분은 추측하지 않고 `Analysis Limits / Uncertainty`에 명시합니다.
- 사용자가 한국어를 쓰면 인간용 보고서의 제목, 표 헤더, 다이어그램 라벨, 구성요소명까지 한국어로 씁니다.
- 함수명/필드명/명령어 같은 영어 식별자는 원문을 유지하고 괄호 안에 한국어 설명을 붙입니다.

## 설치

### 로컬 파일로 설치

```bash
hermes skills install ./SKILL.md
```

### GitHub URL로 설치

프라이빗 저장소라면 GitHub 인증이 된 환경에서 raw URL 또는 clone 후 설치하세요.

```bash
git clone https://github.com/withqua/codebase-analysis-reports-skill.git
cd codebase-analysis-reports-skill
hermes skills install ./SKILL.md
```

## 사용 예시

```bash
hermes -s codebase-analysis-reports
```

또는 대화 중에:

```text
/skill codebase-analysis-reports
```

그다음 예시 요청:

```text
/Users/qwer/path/to/repo 를 분석해줘. 인간용 분석 파일과 AI 에이전트용 분석 파일을 만들어줘.
```

## 파일

- `SKILL.md` — 실제 Hermes Agent 스킬 정의
- `README.md` — 공유/설치 안내
- `LICENSE` — MIT License
