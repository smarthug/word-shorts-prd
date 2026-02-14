# Word Shorts - UI/UX PRD

**Product Requirements Document**

| 항목 | 내용 |
|------|------|
| 문서 버전 | 0.1.0 (Draft) |
| 작성자 | Hoseok, Richbot |
| 작성일 | 2026-02-14 |
| 상태 | 🟡 Draft |

---

## 1. Overview

### 1.1 한 줄 요약
영단어를 30초 쇼츠 영상으로 학습하는 모바일 퍼스트 웹 서비스

### 1.2 배경
- 기존 영단어 학습 방식은 지루하고 반복적
- 쇼츠/릴스 형태의 짧은 콘텐츠가 MZ세대에게 효과적
- AI를 활용해 개인화된 학습 콘텐츠 생성 가능

### 1.3 타겟 유저
- **Primary**: 20-30대 영어 학습자
- **Secondary**: 영어 교육 콘텐츠 제작자

---

## 2. Goals & Non-Goals

### 2.1 Goals
| 우선순위 | 목표 |
|---------|------|
| P0 | 단어 입력 → 쇼츠 영상 생성 플로우 완성 |
| P0 | 모바일에서 최적화된 영상 시청 경험 |
| P1 | 학습 진행도 추적 (본 단어, 저장한 단어) |
| P1 | 시나리오/이미지 QA 워크플로우 |
| P2 | 소셜 공유 기능 |

### 2.2 Non-Goals (이번 버전에서 제외)
- 유료 구독 모델
- 다국어 지원 (한국어/영어 외)
- 네이티브 앱 개발
- 사용자 간 소셜 기능 (팔로우, 댓글 등)

---

## 3. User Flow

### 3.1 메인 플로우

```
[홈 화면]
    │
    ├── [영상 피드] ←── 스와이프로 다음 영상
    │       │
    │       ├── 좋아요 (저장)
    │       ├── 공유
    │       └── 단어 상세보기
    │
    ├── [검색/탐색]
    │       │
    │       └── 단어 검색 → 영상 시청
    │
    └── [내 학습]
            │
            ├── 저장한 단어
            ├── 시청 기록
            └── 학습 통계
```

### 3.2 관리자 플로우 (콘텐츠 생성)

```
[단어 입력]
    │
    ▼
[AI 시나리오 생성] → [시나리오 QA/수정]
    │
    ▼
[이미지 생성] → [이미지 QA/재생성]
    │
    ▼
[영상 생성] → [최종 QA]
    │
    ▼
[퍼블리시]
```

---

## 4. Wireframes

### 4.1 홈 화면 - 영상 피드

```
┌─────────────────────────┐
│  Word Shorts      🔍 👤 │  ← 헤더
├─────────────────────────┤
│                         │
│                         │
│     [ 영상 영역 ]        │  ← 세로 풀스크린
│     (9:16 비율)         │
│                         │
│                         │
├─────────────────────────┤
│  serendipity            │  ← 단어
│  뜻밖의 행운             │  ← 의미
├─────────────────────────┤
│  ❤️  📤  📖             │  ← 액션 버튼
└─────────────────────────┘
```

### 4.2 단어 상세 화면

```
┌─────────────────────────┐
│  ←  serendipity         │
├─────────────────────────┤
│  🔊 /ˌserənˈdɪpɪti/     │  ← 발음
├─────────────────────────┤
│  뜻밖의 행운             │  
│  pleasant surprise      │
│  by chance              │
├─────────────────────────┤
│  예문                    │
│  "Finding this cafe     │
│   was pure serendipity" │
├─────────────────────────┤
│  [▶ 영상 다시보기]       │
│  [📖 저장하기]           │
└─────────────────────────┘
```

### 4.3 관리자 - 시나리오 QA

```
┌─────────────────────────┐
│  시나리오 QA            │
├─────────────────────────┤
│  단어: serendipity      │
├─────────────────────────┤
│  Hook:                  │
│  ┌─────────────────────┐│
│  │ 우연히 발견한 행운,  ││
│  │ 영어로 뭘까?        ││
│  └─────────────────────┘│
├─────────────────────────┤
│  예문:                  │
│  ┌─────────────────────┐│
│  │ Finding this cafe   ││
│  │ was pure serendipity││
│  └─────────────────────┘│
├─────────────────────────┤
│  이미지 프롬프트:        │
│  ┌─────────────────────┐│
│  │ cozy cafe, warm     ││
│  │ lighting, surprised ││
│  │ expression...       ││
│  └─────────────────────┘│
├─────────────────────────┤
│  [✅ 승인]  [✏️ 수정]  [🔄 재생성] │
└─────────────────────────┘
```

---

## 5. Design Specifications

### 5.1 컬러 팔레트

| 용도 | 컬러 | HEX |
|------|------|-----|
| Primary | 파란색 | #3B82F6 |
| Secondary | 보라색 | #8B5CF6 |
| Background | 다크 | #0F172A |
| Surface | 다크그레이 | #1E293B |
| Text Primary | 화이트 | #F8FAFC |
| Text Secondary | 그레이 | #94A3B8 |
| Accent | 핑크 | #EC4899 |

### 5.2 타이포그래피

| 용도 | 폰트 | 크기 | Weight |
|------|------|------|--------|
| 단어 (Hero) | Pretendard | 32px | Bold |
| 의미 | Pretendard | 18px | Medium |
| 본문 | Pretendard | 14px | Regular |
| 캡션 | Pretendard | 12px | Regular |

### 5.3 간격 & 레이아웃

- Base unit: 4px
- 영상 비율: 9:16 (세로 쇼츠)
- 최대 너비: 430px (모바일 최적화)
- 패딩: 16px (좌우)

---

## 6. Components

### 6.1 영상 카드

```
Props:
- videoUrl: string
- word: string
- meaningKo: string
- meaningEn: string
- isLiked: boolean
- onLike: () => void
- onShare: () => void
- onDetail: () => void
```

### 6.2 단어 뱃지

```
Props:
- word: string
- status: 'new' | 'learning' | 'mastered'
```

### 6.3 QA 패널 (관리자)

```
Props:
- scenario: Scenario
- onApprove: () => void
- onEdit: (updated: Scenario) => void
- onRegenerate: () => void
```

---

## 7. Technical Considerations

### 7.1 프론트엔드 스택 (제안)
- **Framework**: Next.js 14 (App Router)
- **Styling**: Tailwind CSS
- **State**: Zustand 또는 Jotai
- **Video**: react-player 또는 video.js

### 7.2 반응형 전략
- Mobile First
- 데스크톱에서는 중앙 정렬 (max-width: 430px)

### 7.3 성능 고려사항
- 영상 lazy loading
- 다음 영상 프리로딩
- 이미지 최적화 (WebP)

---

## 8. Open Questions

| # | 질문 | 상태 |
|---|------|------|
| 1 | 영상 자동재생 vs 탭하여 재생? | ❓ 미정 |
| 2 | 음소거 기본 여부? | ❓ 미정 |
| 3 | 로그인 필수 vs 게스트 허용? | ❓ 미정 |
| 4 | 영상 길이 (15초 vs 30초 vs 60초)? | ❓ 미정 |
| 5 | 관리자 UI 분리 vs 통합? | ❓ 미정 |

---

## 9. Milestones

| Phase | 내용 | 예상 기간 |
|-------|------|----------|
| **Phase 1** | 와이어프레임 확정 & 디자인 시스템 | 1주 |
| **Phase 2** | 영상 피드 UI 개발 | 1주 |
| **Phase 3** | 관리자 QA UI 개발 | 1주 |
| **Phase 4** | 백엔드 연동 & 테스트 | 1주 |

---

## 10. References

- [TikTok Design Guidelines](https://www.tiktok.com/creators/creator-portal/)
- [YouTube Shorts UX](https://www.youtube.com/shorts)
- [Instagram Reels](https://www.instagram.com/reels/)

---

## Appendix

### A. 용어 정의

| 용어 | 정의 |
|------|------|
| 쇼츠 | 30초 이내의 세로형 짧은 영상 |
| 시나리오 | AI가 생성한 단어 학습 스크립트 |
| QA | 품질 검수 (Quality Assurance) |

### B. 변경 이력

| 버전 | 날짜 | 변경 내용 | 작성자 |
|------|------|----------|--------|
| 0.1.0 | 2026-02-14 | 초안 작성 | Richbot |

---

*이 문서는 프로젝트 진행에 따라 업데이트됩니다.*
