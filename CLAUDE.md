# CLAUDE.md — IGRUS-Web-Design

## 레포지토리 목적

IGRUS 웹사이트의 HTML/CSS 디자인 시안을 생성하기 위한 디자인 에이전트 레포지토리이다.
메인 IGRUS-Web 프로젝트와 분리되어 있으며, 생성된 시안은 개발자가 React 컴포넌트를 구현할 때 시각적 참고 자료로 사용한다.

## 핵심 파일

- `guidelines/DESIGN_GUIDE.md` — 모든 시안 생성 시 반드시 따라야 할 디자인 가이드라인
- `prompts/system-prompt.md` — 에이전트 동작을 정의하는 시스템 프롬프트
- `reference/` — 메인 IGRUS-Web 프로젝트의 디자인 시스템 원본 파일
- `archive/` — 생성된 시안과 평가 결과 저장소

## 디자인 시안 생성 시

1. 생성 전 `guidelines/DESIGN_GUIDE.md`를 반드시 숙지할 것
2. `prompts/system-prompt.md`에서 출력 포맷 요구사항 확인
3. `archive/`의 최근 평가 기록을 확인하여 프론트엔드 리드의 취향 파악
4. 항상 2개 옵션(A, B)을 독립 실행 가능한 HTML 파일로 생성
5. 디자인 시스템의 CSS custom properties 사용 (색상 하드코딩 금지)
6. 라이트/다크 모드 모두 지원
7. Inter 폰트를 Google Fonts에서 로드
8. 8px 기반 간격 스케일과 정의된 border-radius 토큰 사용

## 결과 저장 시

- `archive/` 하위에 `NNN-page-name/` 형식으로 새 디렉토리 생성
  - NNN = 0으로 패딩된 순번 (기존 디렉토리 확인 후 다음 번호 사용)
  - page-name = 소문자 kebab-case 설명
- `a.html`, `b.html`로 저장
- 평가 후 `evaluation.json` 저장: `{ "winner": "a"|"b", "reason": "..." }`

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
