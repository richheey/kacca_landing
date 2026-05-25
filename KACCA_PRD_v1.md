# PRD — 한국AI창의융합협회(KACCA) 공식 웹사이트
**버전:** 1.0 MVP  
**작성일:** 2026-05-25  
**작성자:** (희야 × Claude)  
**상태:** 검토 중

---

## 1. 개요 (Overview)

### 1-1. 제품 한 줄 정의
KACCA 공식 브랜드 사이트 — AI 교육 협회의 신뢰도를 높이고, 수강 신청·제휴 문의·강사 커뮤니티로 유입을 이끄는 단일 랜딩 페이지(SPA).

### 1-2. 배경 및 목적
| 항목 | 내용 |
|------|------|
| 문제 | 협회 브랜드·커리큘럼 정보가 네이버 카페에 분산돼 있어 외부 신뢰도 낮음 |
| 기회 | AI 교육 수요 폭증 → 전문적인 랜딩 페이지 보유만으로도 B2B/B2G 문의 전환율 상승 예상 |
| 목표 | ① 월 제휴·출강 문의 10건+ 달성 ② 네이버 카페 유입 전환 ③ KACCA 브랜드 아이덴티티 확립 |

### 1-3. 타깃 사용자
| 세그먼트 | 특성 | 핵심 니즈 |
|----------|------|-----------|
| **B2C — 성인 학습자** | 직장인, 40-50대, AI 진입 장벽 느낌 | "나도 할 수 있을까?" 확인 → 수강 신청 |
| **B2B — 기업 HR/교육담당자** | 직원 연수 필요, 빠른 견적 원함 | 커리큘럼 개요 + 빠른 문의 채널 |
| **B2G — 학교·교육청** | 교원 연수, 방과후 강사 매칭 필요 | 연수 인정 여부, 강사 신뢰도 |
| **예비 강사** | KACCA 소속 희망, 강사 양성과정 관심 | 양성 과정 커리큘럼 + 신청 방법 |

---

## 2. 디자인 시스템 (Design System)

> 소스: `DESIGN.md` — *Say Briefly · Olive Canvas Theme*

### 2-1. 컬러 팔레트
| 역할 | 이름 | HEX | 용도 |
|------|------|-----|------|
| 배경 | Canvas White | `#fcfaf5` | 페이지 기본 배경, 카드 표면 |
| 주색 | Deep Olive | `#1a3300` | 텍스트, 헤딩, 테두리, 주요 CTA 버튼 |
| 강조 | Highlight Yellow | `#ffe95c` | 텍스트 하이라이트, 카드 배경, 버튼 텍스트(딥올리브 BG 위) |
| 보조1 | Soft Teal | `#a8e5e5` | 카드 배경, 보조 버튼 |
| 보조2 | Muted Sage | `#d5f5c2` | 소프트 버튼, 섹션 배경 변화 |
| 액센트 | Warm Orange | `#cb5521` | 카드·섹션 배경, 아이콘, 뱃지 |
| 보조3 | Pale Pink | `#f6d0ff` | 장식 버튼 배경 |
| 중립1 | Light Gray | `#f1f1f1` | 서브텍스트, 보더 |
| 중립2 | Border Gray | `#b6b6b6` | 구분선, 미세 아웃라인 |
| 기본 | Charcoal Black | `#000000` | 보조 텍스트, 파인프린트 |

### 2-2. 타이포그래피
| 역할 | 폰트 | 굵기 | 크기 | 사용처 |
|------|------|------|------|--------|
| 디스플레이 | Bricolage Grotesque | 800 | 55–90px | 히어로 헤드라인, 섹션 타이틀 |
| 바디 | Inter | 300–700 | 11–64px | 본문, 내비, UI 전반 |
| 모노 | Roboto Mono | 400 | 12–16px | 코드, 데이터 표시 |

**Type Scale 요약**  
`caption(11) · body-sm(14) · body(17) · body-lg(18) · heading-sm(24) · heading(30) · heading-lg(36) · display-sm(38) · display(64)`

### 2-3. 간격 & 형태
- **기본 단위:** 8px 그리드
- **섹션 갭:** 40px (vertical), 카드 패딩: 16px
- **페이지 최대 너비:** 1320px
- **Border Radius:** 카드·버튼 6px / 내비 아이템 16px / 필 버튼 9999px

### 2-4. 컴포넌트 스펙

#### Primary CTA Button
- BG: `#1a3300` / Text: `#ffe95c`
- radius: 6px / py: 12px / px: 40px
- shadow: `rgba(0,0,0,0.05) 0 1px 2px`

#### Secondary Outlined Button
- BG: transparent / Text: `#1a3300` / Border: 2px `#1a3300`
- radius: 6px / py: 12px / px: 19px

#### Highlight Card
- BG: `#ffe95c` / radius: 6px(좌) or 16px(전체)
- padding: 48px top · 28px 좌우 · 36px bottom

#### Warm Orange Card
- BG: `#cb5521` / radius: 12px / padding: 50px v · 120px h

#### Soft Teal Card
- BG: `#a8e5e5` / radius: 16px / padding: 56px v · 75px h

#### Badge / Accent Tag
- BG: transparent or `#ffe95c` / Text: Deep Olive
- radius: 9999px / padding: 4px 12px

---

## 3. 페이지 구조 및 섹션 스펙

> 7 Block + Nav + Footer 구조 (SPA, 스크롤 기반)

### 3-0. Navigation (Fixed, 전체 공통)
| 요소 | 스펙 |
|------|------|
| 배경 | Canvas White 90% + `backdrop-blur` |
| 높이 | 80px |
| 로고 | 딥올리브 40×40 사각 블록 + "K" (highlight yellow) + 협회명 텍스트 |
| 메뉴 | 소개 · AI 클래스 · 제휴·문의 · `커뮤니티 가기`(Primary CTA Pill) |
| 모바일 | 햄버거 → 드롭다운 패널 |
| 스크롤 효과 | 20px 이상 스크롤 시 `shadow-flat` 추가 |

---

### Block 1: Hero Section
**목적:** 첫인상, 핵심 가치 전달, 2개 CTA

| 요소 | 스펙 |
|------|------|
| 배경 | Canvas White + blurred gradient blobs (Muted Sage / Soft Teal / Highlight Yellow) |
| 뱃지 | "AI 교육의 새로운 패러다임" — pulse 애니메이션 점 + pill 스타일 |
| 헤드라인 | Bricolage Grotesque 800 / 5xl→7xl responsive / 핵심 단어 Yellow Highlight 효과 |
| 서브텍스트 | Inter 400 / text-lg→xl / opacity 80% |
| CTA 1 | "협회 교육 프로그램 보기" → `#programs` 섹션 / Primary Button |
| CTA 2 | "제휴·출강 문의하기" → `#partnership` 섹션 / Secondary Button |
| 스크롤 힌트 | 하단 bounce 애니메이션 Chevron (데스크탑만) |

**핵심 카피:**  
> "AI, 막막한 기술이 아니라  
> 당신의 일을 가장 수월하게 만들어줄  
> **내일의 무기**입니다."

---

### Block 2: Hook & Pain Points
**목적:** 공감 획득, 페인 포인트 명시화

| 요소 | 스펙 |
|------|------|
| 배경 | Deep Olive (다크 섹션) |
| 타이틀 | Highlight Yellow, 3xl→5xl |
| 카드 3개 | BG: canvas/5 · 테두리 canvas/10 · 아이콘 컬러 각각 warm-orange / soft-teal / muted-sage |
| 카드 항목 | ① 시간 부족 & 반복 업무 ② 정보 과부하 ③ 뒤처진다는 불안감 |
| 하단 인용 | Highlight Yellow, 2xl→3xl 강조 인용문 |
| 애니메이션 | `.reveal` scroll reveal (opacity+translateY) |

---

### Block 3: Core Values
**목적:** 협회 4대 가치 전달 (창의·융합·실용·성장)

| 요소 | 스펙 |
|------|------|
| 배경 | Canvas White |
| 카드 4개 | 2px Deep Olive 테두리 / hover: `6px 6px 0 0 rgba(26,51,0,1)` offset shadow (네오브루탈) |
| 아이콘 BG | Yellow / Soft Teal / Muted Sage / Warm Orange 순 |
| 텍스트 | 헤딩 2xl→3xl / 본문 base→lg |
| 인터랙션 | hover 시 아이콘 `scale(1.1)` |

**가치 카드 내용:**
| 카드 | 한 줄 설명 |
|------|-----------|
| 창의 | 틀을 깨는 사고 — AI와 인간 창의성의 교차점 |
| 융합 | 기술·교육·문화를 연결하는 경계 초월 가치 |
| 실용 | 현장에서 즉시 쓸 수 있는 실전 중심 교육 |
| 성장 | 강사·수강생·협회 모두의 동반 성장 약속 |

---

### Block 4: Leadership & Stats
**목적:** 사회적 증거, 대표 소개, 신뢰 지표

| 요소 | 스펙 |
|------|------|
| 배경 | Canvas White + 상하 border |
| 레이아웃 | 2-col (텍스트 좌 · 스탯 그리드 우) |
| 대표 소개 | 아바타 (딥올리브 "K" 원형) + 이름 + 직함 |
| 스탯 4개 | 누적 수강생 1,200+ / 배출 강사 85+ / 협력 기관 42 / 만족도 98% |
| 카운터 | Intersection Observer → `animateValue()` 숫자 롤링 |
| 스탯 컬러 | warm-orange / soft-teal / highlight-yellow / deep-olive 순 |

---

### Block 5: AI 클래스 (Programs)
**목적:** 4개 프로그램 소개 + 수강 신청 유도

| 프로그램 | 아이콘 BG | 핵심 항목 | CTA |
|----------|-----------|-----------|-----|
| AI 영상 제작 & 바이브코딩 | Highlight Yellow | AI 영상 크리에이터 / Cursor+Claude 바이브코딩 / 2주 완성 앱 만들기 | 수강 신청 (Primary) |
| 생성형 AI & 업무 자동화 | Soft Teal | ChatGPT 완전정복 / 업무 자동화 기초 / 프롬프트 엔지니어링 | 수강 신청 (Primary) |
| 교사 연수 & 강사 양성 | Muted Sage | 연수 인정 AI 도구 / 생기부 자동화 / KACCA 강사 양성과정 | 수강 신청 (Primary) |
| 기업·기관 맞춤 교육 | Warm Orange | 신입사원 리터러시 / 직무별 워크샵 / 경영진 컨설팅 | 기업 출강 안내 (Secondary) |

- 카드 hover: `8px 8px 0 0 Deep Olive` 오프셋 그림자 (네오브루탈)
- 아이콘 hover: 좌우 번갈아 `-rotate-6` / `rotate-6`

---

### Block 6: Contact Form (제휴·출강 문의)
**목적:** B2B/B2G 리드 수집

| 요소 | 스펙 |
|------|------|
| 배경 | Deep Olive |
| 레이아웃 | 2-col (좌: 가치 설명 / 우: 폼) |
| 폼 필드 | 기업/기관명* · 담당자명* · 연락처* · 이메일* · 문의내용(textarea) |
| 폼 배경 | Canvas White (화이트 카드 on 다크 배경) |
| Submit | "문의 접수하기" — Primary Button / form reset + 성공 모달 |
| 제출 후 처리 | **MVP: 모달 확인 표시** (추후 Supabase 또는 이메일 연동 예정) |

---

### Block 7: Community Links
**목적:** 네이버 카페 + 카카오톡 유입

| 요소 | 스펙 |
|------|------|
| 배경 | Highlight Yellow (전체 섹션) + 하단 4px Deep Olive 보더 |
| CTA 1 | "공식 카페 구경하기" → https://cafe.naver.com/kaccakr |
| CTA 2 | "카카오톡 1:1 상담" → KakaoTalk 링크 (추후 연결) |

---

### Footer
| 요소 | 내용 |
|------|------|
| 배경 | Canvas White |
| 좌측 | 로고 + 대표자·이메일·대표번호·저작권 |
| 우측 | SNS 아이콘: 네이버(N 로고) · 카카오톡 · 유튜브 · 인스타그램 |
| 미연결 SNS | 클릭 시 "준비 중" 모달 표시 |

---

## 4. 인터랙션 & 애니메이션

| 기능 | 구현 방식 |
|------|-----------|
| 스크롤 리빌 | `.reveal` class + IntersectionObserver / `opacity 0→1` + `translateY 30px→0` / 0.8s cubic-bezier |
| 숫자 카운터 | `animateValue()` 함수 / Intersection Observer 트리거 |
| 내비 스크롤 효과 | scrollY > 20 → `shadow-flat` 추가, bg opacity 강화 |
| 모달 | CSS class 토글 방식 (`.show-modal`) / backdrop-blur + scale 애니메이션 |
| 카드 hover | `translateY(-2px)` + offset shadow |
| 히어로 배경 | blurred gradient blobs (고정 `blur-3xl`, `mix-blend-multiply`) |

---

## 5. 기술 스택

| 레이어 | 선택 | 비고 |
|--------|------|------|
| 마크업 | Semantic HTML5 | — |
| 스타일 | Tailwind CSS (CDN v3) | 커스텀 컬러·폰트 config 포함 |
| 스크립트 | Vanilla JS (no framework) | SPA 스크롤 기반 |
| 폰트 | Google Fonts | Bricolage Grotesque · Inter |
| 배포 | Netlify Drop (MVP) | 추후 Vercel 이전 가능 |
| 폼 백엔드 | 없음 (MVP: 모달만) | Phase 2: Supabase 또는 Formspree |

---

## 6. MVP 범위 및 제외 사항

### ✅ MVP 포함
- 7개 블록 + Nav + Footer 완전 구현
- 반응형 (모바일 우선, md/lg 브레이크포인트)
- 스크롤 리빌 애니메이션
- 숫자 카운터
- 폼 → 성공 모달 (실제 전송 없음)
- 커뮤니티 외부 링크 (네이버 카페)
- 미준비 SNS → 안내 모달

### ❌ MVP 제외 (Phase 2)
- 실제 폼 전송 (Supabase / Formspree 연동)
- 수강 신청 외부 페이지 (탈잉 / 클래스101 등) 링크 연결
- 카카오톡 채널 링크 연결
- 블로그 / 뉴스 섹션
- 다국어 (한/영)
- CMS 연동
- Google Analytics / Meta Pixel

---

## 7. 성공 지표 (KPI)

| 지표 | 목표 | 측정 방법 |
|------|------|-----------|
| 월간 폼 문의 | 10건+ | 폼 제출 이벤트 (GA 연동 후) |
| 네이버 카페 클릭률 | 방문자의 15%+ | GA 외부 링크 클릭 |
| 평균 체류 시간 | 2분+ | GA Session Duration |
| 모바일 비율 | 60%+ 정상 표시 | Lighthouse 모바일 점수 90+ |

---

## 8. 구현 프롬프트 (Vibe Coding용)

아래는 Lovable.dev / Bolt.new / v0 에 투입할 수 있는 구현 지시 프롬프트입니다.

```
Build a single-page Korean AI education association website for "한국AI창의융합협회 (KACCA)".

DESIGN SYSTEM (Olive Canvas Theme):
- Fonts: Bricolage Grotesque (800, headings) + Inter (300-700, body) from Google Fonts
- Colors: bg=#fcfaf5, primary=#1a3300, accent=#ffe95c, teal=#a8e5e5, sage=#d5f5c2, orange=#cb5521
- Border radius: 6px (cards/buttons), 16px (nav items), 9999px (pills)
- Tailwind CDN with custom config extending the above colors

SECTIONS (in order):
1. Fixed nav — logo "K" block + menu links + "커뮤니티 가기" pill CTA
2. Hero — gradient blob BG, large headline with yellow text highlight effect, 2 CTAs
3. Pain Points — dark olive BG, 3-column pain point cards with icons
4. Core Values — 4-column neo-brutal cards (창의/융합/실용/성장), hover offset shadow
5. Leadership + Stats — 2-col: text+CEO intro left, 4 animated stat counters right
6. Programs — 2×2 grid of program cards with neo-brutal hover, 4 programs
7. Contact Form — dark olive BG, 2-col: description left, white form card right
8. Community CTA — highlight yellow full-width section, 2 buttons
9. Footer — logo + company info left, SNS icons right

INTERACTIONS:
- Scroll reveal: opacity 0→1 + translateY 30px→0 on IntersectionObserver
- Stats counter: animateValue() triggered by IntersectionObserver
- Custom modal (no alert()): CSS class toggle with backdrop-blur
- Mobile hamburger menu toggle

OUTPUT: Single HTML file with embedded Tailwind config, Google Fonts, and vanilla JS.
```

---

## 9. 변경 이력

| 버전 | 날짜 | 내용 |
|------|------|------|
| v1.0 | 2026-05-25 | 초안 작성 (HTML 구현 코드 + DESIGN.md 기반) |
