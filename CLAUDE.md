# CLAUDE.md — IGRUS-Web-Design

## 레포지토리 목적

IGRUS 웹사이트의 HTML/CSS 디자인 시안을 생성하기 위한 디자인 에이전트 레포지토리이다.
메인 IGRUS-Web 프로젝트와 분리되어 있으며, 생성된 시안은 개발자가 React 컴포넌트를 구현할 때 시각적 참고 자료로 사용한다.

## 핵심 파일

- `guidelines/DESIGN_GUIDE.md` — 모든 시안 생성 시 반드시 따라야 할 디자인 가이드라인
- `prompts/system-prompt.md` — 에이전트 동작을 정의하는 시스템 프롬프트
- `reference/tokens.css` — 모든 시안이 공유하는 CSS 토큰 파일 (색상, 간격, 라운딩, 다크모드)
- `reference/` — 메인 IGRUS-Web 프로젝트의 디자인 시스템 원본 파일
- `archive/` — 생성된 시안과 평가 결과 저장소

## 디자인 시안 생성 시

1. 생성 전 `guidelines/DESIGN_GUIDE.md`를 반드시 숙지할 것
2. `prompts/system-prompt.md`에서 출력 포맷 요구사항 확인
3. `archive/`의 최근 평가 기록을 확인하여 프론트엔드 리드의 취향 파악
4. 2개 옵션(A, B)을 병렬 서브에이전트로 생성 (아래 "병렬 생성 워크플로우" 참조)
5. `reference/tokens.css`를 `<link>`로 참조 (토큰을 HTML에 직접 정의하지 말 것)
6. 디자인 시스템의 CSS custom properties 사용 (색상 하드코딩 금지)
7. 라이트/다크 모드 모두 지원
8. Inter 폰트를 Google Fonts에서 로드
9. 8px 기반 간격 스케일과 정의된 border-radius 토큰 사용

## 병렬 생성 워크플로우

시안 생성 시 Task 도구로 `general-purpose` 서브에이전트 2개를 **하나의 메시지에서 동시에** 실행한다.

### 사전 준비 (오케스트레이터가 수행)
1. `guidelines/DESIGN_GUIDE.md` 읽기
2. `prompts/system-prompt.md` 읽기
3. `reference/tokens.css` 읽기
4. 해당 페이지의 최근 `evaluation.json` 읽기 (있으면)
5. 출력 디렉토리 생성: `archive/NNN-page-name/round-N/`

### 병렬 실행
하나의 메시지에서 Task 도구를 2번 호출하여 병렬 실행:

**서브에이전트 A** (`subagent_type: general-purpose`):
- 프롬프트에 아래 내용을 **전문 포함**:
  - `prompts/system-prompt.md` 내용
  - `guidelines/DESIGN_GUIDE.md` 내용
  - 과거 평가 피드백 (evaluation.json 요약)
  - 페이지 요구사항
- 지시: "**Option A(안전한 접근)만** 생성하여 `archive/NNN-page-name/round-N/a.html`에 Write 도구로 저장하라"

**서브에이전트 B** (`subagent_type: general-purpose`):
- 프롬프트에 동일한 컨텍스트 전문 포함
- 지시: "**Option B(창의적 접근)만** 생성하여 `archive/NNN-page-name/round-N/b.html`에 Write 도구로 저장하라"

### 프롬프트 템플릿

각 서브에이전트 프롬프트는 다음 구조를 따른다:
```
너는 IGRUS 웹사이트 디자인 에이전트이다.

## 시스템 프롬프트
{system-prompt.md 전문}

## 디자인 가이드라인
{DESIGN_GUIDE.md 전문}

## 과거 평가 피드백
{evaluation.json 요약 또는 "첫 라운드이므로 없음"}

## 요청
{페이지 요구사항}

## 지시
Option {A 또는 B}만 생성하라.
- Option A: 기존 패턴을 충실히 따르는 안전한 접근
- Option B: 디자인 시스템 내에서 창의적/차별화된 접근
결과를 `{출력 경로}`에 Write 도구로 저장하라.
tokens.css 경로: `{상대경로}/reference/tokens.css`
```

### 완료 후
두 에이전트 모두 완료되면 사용자에게 결과 경로를 보고한다.

## 결과 저장 시

- `archive/` 하위에 `NNN-page-name/` 형식으로 새 디렉토리 생성
  - NNN = 0으로 패딩된 순번 (기존 디렉토리 확인 후 다음 번호 사용)
  - page-name = 소문자 kebab-case 설명
- 각 페이지 디렉토리 내에 `round-N/` 하위 폴더로 평가 라운드 관리
  - `round-1/`, `round-2/`, `round-3/` ...
  - 피드백을 반영한 새 시안은 다음 round 폴더에 저장
- 각 round 폴더에 `a.html`, `b.html`로 저장
- 평가 후 `evaluation.json` 저장 (아래 스키마 참조)

### evaluation.json 스키마

```json
{
  "winner": "a"|"b",
  "scores": {
    "visual_appeal": 1-10,
    "layout": 1-10,
    "dark_mode": 1-10,
    "mobile": 1-10,
    "consistency": 1-10
  },
  "liked": ["좋았던 구체적 요소들"],
  "disliked": ["아쉬웠던 구체적 요소들"],
  "next_round": ["다음 라운드에서 개선할 사항"]
}
```

### 평가 완료 후 체크리스트

1. **`evaluation.json` 생성** — 현재 `round-N/` 폴더에 평가 결과 저장 (위 스키마 준수)
2. **`guidelines/DESIGN_GUIDE.md` 업데이트** — 평가에서 새로운 선호 패턴이 발견되면 섹션 9 "프론트엔드 리드 선호 패턴"에 반영
3. **다음 라운드 시안 생성** — `next_round`에 개선 사항이 있으면 `round-N+1/` 폴더를 만들고 피드백을 반영한 `a.html`, `b.html` 생성
4. **최종 라운드인 경우** — `next_round`가 빈 배열이면 해당 페이지 작업 완료

## 가이드라인 업데이트 시

- 평가에서 패턴이 발견되면 `guidelines/DESIGN_GUIDE.md`에 반영
- 가이드는 생성 컨텍스트에 주입되므로 간결하게 유지
- 메인 프로젝트의 디자인 시스템 변경 시 `reference/`에도 반영

## 파일 네이밍 규칙

- 디렉토리: `NNN-descriptive-name` (kebab-case)
- HTML 파일: `a.html`, `b.html`
- 평가 파일: `evaluation.json`
- 모두 소문자, 공백 없음

## 언어

- 코드 주석 및 HTML 콘텐츠: 한국어
- 파일명 및 기술 식별자: 영어

## 디자인 시스템 Quick Reference

- 브랜드 Primary: `#03A69E` (light) / `#66CBC5` (dark)
- 폰트: Inter
- 간격: s1(4px), s2(8px), s3(12px), s4(16px), s5(24px), s6(32px), s7(48px), s8(56px)
- 라운딩: r1(4px), r2(8px), r3(12px), r4(16px), full(100px)
- 레이아웃: Sidebar + Header + Main Content, max-width 1280px

## 커밋 & PR 규칙
- 메시지에 Co-Authored-By Claude 를 작성하지 말 것
