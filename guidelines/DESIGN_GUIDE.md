# IGRUS Design Guide

> AI 디자인 에이전트가 HTML/CSS 시안을 생성할 때 반드시 참조하는 가이드라인입니다.
> 이 문서의 모든 규칙은 생성된 시안에 정확히 반영되어야 합니다.

---

## 1. 색상 시스템

### Brand Colors

메인 브랜드 컬러: `#03A69E` (Teal)

| 토큰 | HEX | 용도 |
|------|-----|------|
| `--brand-l1` | `#E6F6F5` | 연한 배경, 호버 상태 |
| `--brand-l2` | `#B3E5E2` | 강조 배경 |
| `--brand-l3` | `#66CBC5` | 다크모드 primary |
| `--brand-l4` | `#03A69E` | **메인 브랜드 컬러** |
| `--brand-l5` | `#03958E` | 호버 상태 |
| `--brand-l6` | `#027A75` | 액티브 상태 |
| `--brand-l7` | `#015F5B` | 강조 텍스트 |
| `--brand-l8` | `#013E3B` | 가장 어두운 브랜드 |

### Gray Scale

| 토큰 | HEX | 용도 |
|------|-----|------|
| `--gray-1` | `#F8F9FA` | 전체 배경색 |
| `--gray-2` | `#E9ECEF` | 입력창 배경 |
| `--gray-3` | `#DEE2E6` | 구분선, 테두리 |
| `--gray-4` | `#ADB5BD` | 비활성 텍스트, Placeholder |
| `--gray-5` | `#6C757D` | 보조 텍스트 |
| `--gray-6` | `#495057` | 본문 텍스트 |
| `--gray-7` | `#343A40` | 강조 텍스트 |
| `--gray-8` | `#212529` | 메인 타이틀 |

### State Colors

| 이름 | HEX | 용도 |
|------|-----|------|
| Success | `#28A745` | 성공, 완료 |
| Warning | `#FFC107` | 경고, 주의 |
| Destructive | `#DC3545` | 오류, 삭제 |
| Info | `#17A2B8` | 정보, 알림 |

### Semantic Tokens (Light / Dark)

| 토큰 | Light | Dark | 용도 |
|------|-------|------|------|
| `--background` | `#FFFFFF` | `#212529` | 페이지 배경 |
| `--foreground` | `#212529` | `#F8F9FA` | 메인 텍스트 |
| `--card` | `#FFFFFF` | `#343A40` | 카드 배경 |
| `--card-foreground` | `#212529` | `#F8F9FA` | 카드 텍스트 |
| `--primary` | `#03A69E` | `#66CBC5` | 주요 액션 |
| `--primary-foreground` | `#FFFFFF` | `#212529` | 주요 액션 위 텍스트 |
| `--secondary` | `#F8F9FA` | `#343A40` | 보조 배경 |
| `--secondary-foreground` | `#495057` | `#E9ECEF` | 보조 텍스트 |
| `--muted` | `#F8F9FA` | `#343A40` | 연한 배경 |
| `--muted-foreground` | `#6C757D` | `#ADB5BD` | 보조 텍스트 |
| `--accent` | `#E6F6F5` | `#015F5B` | 강조 배경 |
| `--accent-foreground` | `#03958E` | `#E6F6F5` | 강조 텍스트 |
| `--border` | `#DEE2E6` | `#495057` | 테두리 |
| `--input` | `#E9ECEF` | `#343A40` | 입력창 배경 |
| `--ring` | `#03A69E` | `#66CBC5` | 포커스 링 |
| `--destructive` | `#DC3545` | `#DC3545` | 삭제/오류 |
| `--popover` | `#FFFFFF` | `#343A40` | 팝오버 배경 |
| `--popover-foreground` | `#212529` | `#F8F9FA` | 팝오버 텍스트 |

---

## 2. 타이포그래피

폰트: **Inter** (Google Fonts)

| 스타일 | 굵기 | 크기 | 행간 | 용도 |
|--------|------|------|------|------|
| h1 | Bold (700) | 42px | 1.2 | 메인 타이틀 |
| h2 | Bold (700) | 28px | 1.3 | 섹션 타이틀 |
| h3 | SemiBold (600) | 22px | 1.3 | 카드 타이틀 |
| b1 | Regular (400) | 16px | 1.5 | 본문 |
| b2 | Regular (400) | 14px | 1.5 | 작은 본문 |
| label | Medium (500) | 13px | auto | 라벨 |
| c1 | Medium (500) | 12px | auto | 캡션 |
| c2 | Regular (400) | 10px | auto | 작은 캡션 |

### Hero 타이포그래피
- 굵기: 800 (ExtraBold)
- 크기: `clamp(36px, 5vw, 56px)` (반응형)
- 행간: 1.1
- letter-spacing: -0.025em

---

## 3. 간격

8px 기반 스케일:

| 토큰 | 값 | 용도 |
|------|-----|------|
| s1 | 4px | 아이콘-텍스트 간격 |
| s2 | 8px | 작은 요소 간격 |
| s3 | 12px | 버튼 내부 패딩 |
| s4 | 16px | 카드 내부 패딩 |
| s5 | 24px | 섹션 간격 |
| s6 | 32px | 큰 섹션 간격 |
| s7 | 48px | 페이지 섹션 |
| s8 | 56px | 큰 페이지 섹션 |

---

## 4. 라운딩

| 토큰 | 값 | 용도 |
|------|-----|------|
| r1 | 4px | 작은 버튼, 태그 |
| r2 | 8px | 일반 버튼, 입력창 |
| r3 | 12px | 카드 |
| r4 | 16px | 큰 카드, 모달 |
| full | 100px | 원형 버튼, 아바타 |

---

## 5. 컴포넌트 패턴

### Layout

- Sidebar (좌측) + Header (상단) + Main Content 구조
- Sidebar: Desktop(lg+)에서 항상 표시 (sticky), 모바일에서 토글 (fixed + backdrop)
- Header: 상단 고정, 모바일 햄버거 메뉴
- Main Content: `max-width: 80rem (1280px)`, 중앙 정렬
- Flexbox 기반 레이아웃

### Sidebar

- 로고 (IGRUS) + 메인 네비게이션 (홈, 게시판, 행사, 문의)
- 하단: 테마 토글, 마이페이지/로그인, 관리자
- 활성 메뉴: 좌측 primary 색상 강조선 (4px bar)
- Desktop: sticky, 항상 표시 / Mobile: fixed, backdrop 포함

### Header

- 상단 고정, `border-bottom` 구분
- 모바일: 햄버거 메뉴 + 로고
- Desktop: 네비게이션 메뉴 (공지사항, 자유게시판, 정보공유, 행사)
- 우측: 로그인/회원가입 또는 사용자 정보

### Button (5 variants)

| Variant | 배경 | 텍스트 | 용도 |
|---------|------|--------|------|
| default | `var(--primary)` | `var(--primary-foreground)` | 주요 액션 |
| secondary | `var(--secondary)` | `var(--secondary-foreground)` | 보조 액션 |
| outline | 투명, `border: var(--border)` | `var(--foreground)` | 선택적 액션 |
| ghost | 투명, hover 시 연한 배경 | `var(--foreground)` | 텍스트 액션 |
| destructive | `var(--destructive)` | 흰색 | 삭제/위험 액션 |

- 크기: sm / md (기본) / lg
- Border radius: r2 (8px)
- Hover/focus 상태 필수

### Input

- 배경: `var(--background)` 또는 `var(--input)`
- 테두리: `1px solid var(--border)`
- 포커스: `border-color: var(--primary)` + ring 효과
- Border radius: r2 (8px)
- Placeholder: `var(--gray-4)` 또는 `var(--muted-foreground)`

### Card

- 배경: `var(--card)`
- 텍스트: `var(--card-foreground)`
- 테두리: `1px solid var(--border)`
- Border radius: r3 (12px) 또는 r4 (16px)
- 구조: Header → Title / Description → Content → Footer

### SearchBar

- 완전한 둥근 형태: `border-radius: 100px` (full)
- 좌측 Search 아이콘
- 포커스 시 너비 확장 (160px → 256px → 320px)

---

## 6. 특수 스타일링

### Hero Section

- 배경: radial-gradient + 도트 그리드 패턴 (32px 간격)
- 장식: 플로팅 링 애니메이션, 글로우 오브 (모바일에서 숨김)
- 텍스트: 그라데이션 shimmer 효과 (8초 주기, `-webkit-text-stroke: 1px #03A69E`)
- 버튼: box-shadow 글로우 효과
- 접근성: `prefers-reduced-motion: reduce` 시 애니메이션 비활성화

### Login Brand Panel

- 그라데이션: `linear-gradient(135deg, #013E3B 0%, #027A75 40%, #03A69E 100%)`
- 흰색 도트 그리드 오버레이 (24px 간격, opacity 0.08)

### Scrollbar

- 브랜드 색상: `rgba(3, 166, 158, 0.5)`, hover 시 0.7
- 다크모드: `rgba(102, 203, 197, 0.5)`, hover 시 0.7
- 너비: 12px (webkit) / thin (firefox)

---

## 7. 레이아웃 원칙

- **Mobile-first 반응형**: 모바일 우선 설계
  - sm: 640px / md: 768px / lg: 1024px / xl: 1280px
- **Flexbox 중심**: Grid보다 Flexbox 기본
- **중앙 정렬 컨테이너**: `max-width: 80rem`, `margin: 0 auto`
- **다크모드**: CSS custom properties로 자동 대응, `.dark` 클래스 토글

---

## 8. Do's and Don'ts

### DO

- `reference/tokens.css`를 `<link>`로 참조할 것 (토큰을 HTML 내 `<style>`에 직접 정의하지 말 것)
- CSS custom properties(변수)를 사용할 것
- Inter 폰트를 Google Fonts에서 로드할 것
- 라이트/다크 두 모드 모두 지원할 것
- 8px 기반 간격 시스템을 따를 것
- semantic color tokens을 사용할 것
- 모바일-퍼스트로 설계할 것
- 버튼 hover/focus 시 상태 변화 제공
- 포커스 시 ring 효과 제공 (접근성)
- `prefers-reduced-motion` 존중

### DON'T

- `<style>` 태그에 `:root` / `.dark` 토큰 블록 직접 정의 금지 (`tokens.css` 사용)
- 하드코딩된 색상 사용 금지 (`#FFFFFF` 대신 `var(--background)`)
- Inter 이외의 폰트 사용 금지
- 브랜드 컬러 임의 변경 금지
- 8px 스케일에 없는 간격 사용 금지 (10px, 15px, 20px 등)
- border-radius 임의 값 사용 금지 (r1~r4, full만 사용)
- `!important` 남용 금지
- 다크모드 무시 금지
- 지나치게 심심한/밋밋한 디자인 금지 — 시각적 흥미 요소 필수

---

## 9. 프론트엔드 리드 선호 패턴 (평가 기반)

> 평가 결과에서 발견된 선호 패턴을 기록. 생성 시 반드시 반영할 것.

### 레이아웃
- 센터 카드 접근을 스플릿 패널보다 선호
- 깔끔함은 유지하되 시각적으로 심심하지 않을 것

### 시각적 흥미 요소
- 단순 도트 그리드 + 플로팅 링만으로는 부족 (round-1: 7점)
- 브랜드 컬러를 활용한 그라데이션 악센트, 글로우 효과 등 적극 활용
- 배경에 깊이감(depth)을 주는 레이어드 효과 권장 (다중 radial gradient + 도트 그리드 + 노이즈 텍스처)
- 카드 뒤 글로우 오브(halo) 효과가 좋은 반응을 얻음
- 카드 상단 브랜드 그라데이션 바 등 디테일 추가
- 플로팅 링은 원형만 사용, 비율이 어색한 사각형/기하학 도형은 지양
- "안전하지만 풍부한" 접근이 "과하게 창의적인" 접근보다 선호됨
- 히어로 장식 요소(링, 오브, 노이즈 등)가 과하면 톤다운 필요 — 적당한 절제가 핵심
- 다크모드 토글은 이모지가 아닌 SVG 아이콘 사용 (디자인 시스템 일관성)
- CTA 버튼 순서: 핵심 액션(가입 신청)이 primary, 부가 액션(동아리 소개)이 outline
- 히어로 스탯 카운터(역사, 누적 부원, 프로젝트 수) 불필요 — 히어로는 텍스트 + CTA에 집중
