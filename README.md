# IGRUS-Web-Design

AI 기반 디자인 에이전트를 활용한 IGRUS 웹사이트 디자인 시안 관리 레포지토리입니다.

## 개요

디자이너 없이 AI 디자인 에이전트를 활용하여, 프론트엔드 리드의 피드백을 누적 학습하고 팀 취향에 맞는 UI 디자인을 생성하는 시스템입니다.

RLHF(Reinforcement Learning from Human Feedback) 기법에서 아이디어를 따왔습니다.

**핵심 사이클**: 생성 → 평가 → 저장 → 참조 → 재생성

- 에이전트의 역할은 Figma 시안을 넘겨주는 디자이너와 동일
- 생성된 HTML/CSS 시안을 참고하여 개발자가 React 컴포넌트로 구현
- 디자인 데이터는 IGRUS-Web 메인 레포와 분리하여 관리

## 레포 구조

```
IGRUS-Web-Design/
├── guidelines/
│   └── DESIGN_GUIDE.md        ← AI가 참조할 디자인 가이드라인
├── archive/
│   ├── 001-login-page/
│   │   ├── a.html             ← Option A 시안
│   │   ├── b.html             ← Option B 시안
│   │   └── evaluation.json    ← { winner, reason }
│   └── ...
├── prompts/
│   └── system-prompt.md       ← AI 시스템 프롬프트
└── reference/                 ← 디자인 시스템 참조 자료
    ├── design-system.md
    ├── component-spec.md
    ├── index.css
    └── design-agent-strategy.md
```

## 워크플로우

### 1. 디자인 요청
에이전트에게 페이지 디자인을 요청합니다.

### 2. 시안 생성 (A/B)
에이전트가 디자인 가이드라인을 기반으로 2개의 HTML/CSS 시안을 생성합니다.
- **Option A**: 안전하고 관습적인 접근
- **Option B**: 디자인 시스템 내에서의 창의적 접근

### 3. 평가
프론트엔드 리드가 브라우저에서 두 시안을 비교하고 선택합니다.

### 4. 저장
결과를 `archive/NNN-page-name/` 디렉토리에 저장합니다:

```json
{
  "winner": "a",
  "reason": "여백이 더 넉넉하고 카드 간격이 적절함"
}
```

### 5. 다음 생성에 반영
누적된 평가 데이터를 기반으로 에이전트가 취향을 학습하여 다음 시안에 반영합니다.

## 시안 확인 방법

생성된 HTML 파일을 브라우저에서 직접 열어 확인합니다. 각 시안에는 다크모드 토글 버튼이 포함되어 있어 라이트/다크 모드를 전환하며 확인할 수 있습니다.

## 디자인 시스템

이 레포에서 생성되는 모든 시안은 IGRUS-Web 프로젝트의 디자인 시스템을 따릅니다:

- **브랜드 컬러**: `#03A69E` (Teal) 기반 8단계 스케일
- **폰트**: Inter
- **간격**: 8px 기반 스케일 (4px ~ 56px)
- **라운딩**: r1(4px) ~ r4(16px), full(100px)
- **다크모드**: CSS custom properties 기반 자동 대응

상세 내용은 `guidelines/DESIGN_GUIDE.md`를 참조하세요.
