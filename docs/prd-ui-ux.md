# Word Shorts - UI/UX PRD

**영어 단어, 이제 쇼츠로 놀면서 배우자**

| 항목 | 내용 |
|------|------|
| 문서 버전 | 0.5.0 |
| 작성자 | Hoseok, Richbot |
| 작성일 | 2026-02-14 |
| 상태 | 🟡 Draft |

---

## One-Pager Summary

> **5분 안에 읽는 핵심 요약**

| 항목 | 내용 |
|------|------|
| **문제** | 영어 암기는 필수지만 지루하고 힘들다 |
| **솔루션** | 30초 쇼츠로 영단어를 재미있게 학습 |
| **타겟** | 20-30대 영어 학습자 (토익/자기계발) |
| **핵심 기능** | 쇼츠 피드 시청 → 단어 학습 → 복습 |
| **성공 지표** | 일일 학습 완료율, 단어 기억 유지율 |
| **MVP 범위** | 프론트엔드 UI/UX만 (백엔드 연동 제외) |

---

## 1. 개요 (Overview)

### 1.1 프로젝트명
**Word Shorts** - 영단어 학습 쇼츠 서비스

### 1.2 목표 (Objectives)

| 목표 | 설명 |
|------|------|
| 학습 경험 혁신 | 지루한 암기 → 재미있는 쇼츠 시청으로 전환 |
| 학습 지속률 향상 | 매일 5분 쇼츠 시청 습관 형성 |
| 기억 효율 증가 | 시각적 스토리텔링으로 장기 기억 유도 |

### 1.3 성공 지표 (Success Metrics)

| KPI | 목표 | 측정 방법 |
|-----|------|----------|
| DAU 리텐션 | 7일 후 40% 이상 | 재방문율 |
| 일일 학습량 | 10단어 이상/일 | 시청 완료 수 |
| 단어 기억률 | 1주 후 70% 기억 | 복습 테스트 |

---

## 2. 배경 및 기회 (Context & Opportunity)

### 2.1 문제 정의 (Pain Points)

| 문제 | 현재 상황 |
|------|----------|
| 🔴 지루함 | 플래시카드, 단어장은 반복적이고 재미없음 |
| 🔴 낮은 지속률 | 영단어 앱 3일 후 이탈률 70% 이상 |
| 🔴 비효율적 암기 | 맥락 없는 암기는 금방 잊어버림 |

### 2.2 사용자 페르소나

**Primary Persona: 취준생 김영희 (26세)**
- 토익 800점 목표
- 매일 출퇴근 시간에 스마트폰 사용
- 틱톡/릴스 하루 1시간 이상 시청
- "단어 암기가 너무 지루해요. 영상으로 보면 기억에 남을 것 같은데..."

### 2.3 가설 (Hypothesis)

> **"우리가 영단어를 30초 쇼츠 형태로 제공하면,**
> **사용자의 학습 지속률이 기존 앱 대비 2배 이상 높아질 것이고,**
> **이는 7일 리텐션 지표로 증명될 것이다."**

---

## 3. 사용자 시나리오 (User Stories)

### 3.1 핵심 시나리오

| As a... | I want to... | So that... |
|---------|--------------|------------|
| 영어 학습자 | 쇼츠를 스와이프하며 단어 학습 | 지루하지 않게 매일 공부 가능 |
| 영어 학습자 | 모르는 단어를 저장 | 나중에 복습 가능 |
| 영어 학습자 | 내 수준에 맞는 단어 추천 | 너무 쉽거나 어렵지 않게 학습 |
| 토익 준비생 | 토익 빈출 단어 필터링 | 시험에 나오는 단어 집중 학습 |

### 3.2 상세 시나리오

```
[시나리오: 출근길 학습]

1. 영희는 지하철에서 Word Shorts 앱을 연다
2. 세로 화면 가득 쇼츠 영상이 재생된다
3. "Serendipity - 뜻밖의 행운" 
   → 카페에서 우연히 옛 친구를 만나는 장면
4. 영희: "아, 이런 상황이 serendipity구나!"
5. 위로 스와이프 → 다음 단어
6. 마음에 드는 단어는 ❤️ 탭해서 저장
7. 5분 후, 10단어 학습 완료
```

---

## 4. 기능 요구사항 (Functional Requirements)

### 4.1 P0 (Must Have) - MVP 필수

| 기능 | 설명 | 상세 |
|------|------|------|
| **쇼츠 피드** | 세로 영상 스와이프 시청 | 무한 스크롤, 자동 재생 |
| **단어 정보 표시** | 영상 위 단어/뜻 오버레이 | 단어, 발음, 의미(한/영) |
| **저장 기능** | 좋아요/북마크 | 로컬 저장 (localStorage) |
| **단어 상세** | 탭하면 상세 정보 | 예문, 발음 듣기 |

### 4.2 P1 (Should Have) - 다음 버전

| 기능 | 설명 |
|------|------|
| 레벨 테스트 | 초기 수준 측정 |
| 복습 목록 | 저장한 단어 모아보기 |
| 카테고리 필터 | 토익/회화/일상 등 |
| 검색 | 특정 단어 검색 |

### 4.3 P2 (Nice to Have) - 향후

| 기능 | 설명 |
|------|------|
| 학습 통계 | 일별/주별 학습량 |
| 소셜 공유 | 영상 공유 기능 |
| 다크/라이트 모드 | 테마 설정 |
| 알림 | 학습 리마인더 |

---

## 5. 범위 외 사항 (Non-Goals / Out of Scope)

> ⚠️ **이번 버전에서 만들지 않는 것들**

| 제외 항목 | 이유 |
|----------|------|
| ❌ **백엔드 연동** | MVP는 프론트엔드 UI/UX에 집중 |
| ❌ 회원가입/로그인 | 백엔드 필요, 추후 추가 |
| ❌ 서버 API 연동 | 목업 데이터로 진행 |
| ❌ 실제 영상 생성 파이프라인 | 별도 프로젝트로 진행 |
| ❌ 유료 구독 모델 | MVP 이후 검토 |
| ❌ 네이티브 앱 | 웹앱(PWA)으로 진행 |
| ❌ 사용자 간 소셜 기능 | 팔로우, 댓글 등 제외 |

---

## 6. 와이어프레임 (Wireframes)

### 6.1 홈 - 쇼츠 피드

```
┌─────────────────────────┐
│  Word Shorts      🔍 👤 │  ← 헤더 (미니멀)
├─────────────────────────┤
│                         │
│                         │
│     [ 영상 영역 ]        │  ← 풀스크린 9:16
│                         │
│  ┌───────────────────┐  │
│  │ serendipity       │  │  ← 단어 (하단 오버레이)
│  │ 뜻밖의 행운        │  │
│  │ Lv.7 · 토익빈출    │  │
│  │ ● ○ ○  (1/3)      │  │  ← 같은 단어 쇼츠 인디케이터
│  └───────────────────┘  │
│                         │
│              ❤️ 234     │  ← 우측 액션 버튼
│              📖         │
│              🔊         │
│              📤         │
└─────────────────────────┘
```

### 6.2 스와이프 네비게이션 (2D)

```
              ↑ 이전 단어
              │
              │
← 같은 단어 ──┼── 같은 단어 →
  다른 쇼츠   │   다른 쇼츠
              │
              ↓ 다음 단어
```

| 방향 | 동작 | 예시 |
|------|------|------|
| **↑↓ 상하** | 다른 단어로 이동 | serendipity → ephemeral |
| **←→ 좌우** | 같은 단어의 다른 쇼츠 | serendipity 쇼츠 1 → 쇼츠 2 |

**UX 포인트:**
- 한 단어당 여러 시나리오/영상 제공 (1:N)
- 마음에 드는 쇼츠 찾을 때까지 좌우 스와이프
- 하단에 도트 인디케이터로 현재 위치 표시

### 6.3 단어 상세 (바텀시트)

```
┌─────────────────────────┐
│  ─────  (드래그 핸들)    │
├─────────────────────────┤
│  serendipity      🔊    │  ← 단어 + 발음 버튼
│  /ˌserənˈdɪpɪti/        │
├─────────────────────────┤
│  Lv.7 · 추상/감정 · 토익★★★ │
├─────────────────────────┤
│  🇰🇷 뜻밖의 행운          │
│  🇺🇸 A pleasant surprise │
│     found by chance     │
├─────────────────────────┤
│  📝 예문                 │
│  "Finding this cafe     │
│   was pure serendipity" │
├─────────────────────────┤
│  [📖 저장하기]  [🔄 다른 영상] │
└─────────────────────────┘
```

### 6.4 저장 목록 (P1)

```
┌─────────────────────────┐
│  ←  저장한 단어 (23)    │
├─────────────────────────┤
│  ┌─────┐ serendipity    │
│  │ 🖼️  │ 뜻밖의 행운     │
│  └─────┘ Lv.7           │
├─────────────────────────┤
│  ┌─────┐ ephemeral      │
│  │ 🖼️  │ 순간적인        │
│  └─────┘ Lv.8           │
├─────────────────────────┤
│  ┌─────┐ ubiquitous     │
│  │ 🖼️  │ 어디에나 있는   │
│  └─────┘ Lv.6           │
└─────────────────────────┘
```

---

## 7. 디자인 스펙 (Design Specifications)

### 7.1 컬러 시스템

| 용도 | Light | Dark | HEX (Dark) |
|------|-------|------|------------|
| Background | #FFFFFF | #0F172A | 다크 네이비 |
| Surface | #F8FAFC | #1E293B | 다크 그레이 |
| Primary | #3B82F6 | #3B82F6 | 블루 |
| Text Primary | #0F172A | #F8FAFC | |
| Text Secondary | #64748B | #94A3B8 | |
| Level Easy | #22C55E | #22C55E | 그린 |
| Level Medium | #EAB308 | #EAB308 | 옐로우 |
| Level Hard | #EF4444 | #EF4444 | 레드 |

### 7.2 타이포그래피

| 용도 | Size | Weight | Line Height |
|------|------|--------|-------------|
| 단어 (Hero) | 28px | Bold | 1.2 |
| 의미 | 16px | Medium | 1.4 |
| 본문 | 14px | Regular | 1.5 |
| 캡션 | 12px | Regular | 1.4 |
| 레벨 뱃지 | 11px | Bold | 1 |

### 7.3 컴포넌트

```
<VideoCard>
  - videoUrl: string
  - word: Word
  - onLike: () => void
  - onDetail: () => void

<WordBadge>
  - level: 1-10
  - category: string
  - toeicFreq: 'high' | 'medium' | 'low'

<BottomSheet>
  - word: Word
  - onSave: () => void
  - onClose: () => void
```

---

## 8. 기술 고려사항 (Technical Considerations)

### 8.1 스택

| 영역 | 기술 | 버전 | 이유 |
|------|------|------|------|
| Framework | React | 18.2.0 | 가볍고 유연 |
| Build | Vite | 4.x+ | 빠른 HMR, 간단한 설정 |
| PWA | vite-plugin-pwa | latest | 오프라인 지원, 홈화면 설치 |
| Swipe/Carousel | Swiper | 12.0.0 | 쇼츠 UX의 핵심 (vertical pagination) |
| Animation | Framer Motion | 10.x+ | 인터랙션 디테일 (좋아요 애니메이션 등) |
| Styling | Tailwind CSS | 3.x | 빠른 개발 |
| State | Zustand | 4.x | 심플, 가벼움 |
| Storage | localStorage | - | 백엔드 없이 저장 |

### 8.2 Swiper 핵심 설정 (Nested - 2D 스와이프)

```jsx
import { Swiper, SwiperSlide } from 'swiper/react';
import { Pagination, Mousewheel } from 'swiper/modules';

// 세로(Outer): 단어 간 이동
<Swiper
  direction="vertical"
  slidesPerView={1}
  mousewheel={true}
  modules={[Mousewheel]}
  style={{ width: '100%', height: '100vh' }}
>
  {words.map(word => (
    <SwiperSlide key={word.id}>
      {/* 가로(Inner): 같은 단어의 다른 쇼츠 */}
      <Swiper
        direction="horizontal"
        slidesPerView={1}
        pagination={{ clickable: true }}
        modules={[Pagination]}
        nested={true}  // 중요! nested swiper 활성화
      >
        {word.shorts.map(short => (
          <SwiperSlide key={short.id}>
            <VideoCard word={word} short={short} />
          </SwiperSlide>
        ))}
      </Swiper>
    </SwiperSlide>
  ))}
</Swiper>
```

**핵심 포인트:**
- `nested={true}` 필수 (inner swiper에서 터치 이벤트 분리)
- Outer = vertical (단어 이동)
- Inner = horizontal (같은 단어 쇼츠 이동)
- Pagination은 inner에만 (도트 인디케이터)

### 8.3 PWA 설정

```js
// vite.config.js
import { VitePWA } from 'vite-plugin-pwa';

export default {
  plugins: [
    VitePWA({
      registerType: 'autoUpdate',
      manifest: {
        name: 'Word Shorts',
        short_name: 'WordShorts',
        theme_color: '#0F172A',
        display: 'standalone',
        orientation: 'portrait',
      }
    })
  ]
}
```

### 8.4 프로젝트 구조

```
word-shorts-frontend/
├── public/
│   └── icons/
├── src/
│   ├── components/
│   │   ├── VideoCard.jsx      # 쇼츠 카드
│   │   ├── WordOverlay.jsx    # 단어 오버레이
│   │   ├── ActionButtons.jsx  # 우측 버튼들
│   │   └── BottomSheet.jsx    # 단어 상세
│   ├── pages/
│   │   ├── Home.jsx           # 메인 피드
│   │   └── Saved.jsx          # 저장 목록
│   ├── stores/
│   │   └── useWordStore.js    # Zustand 상태
│   ├── data/
│   │   └── mockWords.js       # 목업 데이터
│   ├── styles/
│   │   └── globals.css
│   ├── App.jsx
│   └── main.jsx
├── index.html
├── vite.config.js
├── tailwind.config.js
└── package.json
```

### 8.5 목업 데이터 구조

```typescript
// 단어 (1) : 쇼츠 (N) 관계
interface Word {
  id: string;
  word: string;
  meaningKo: string;
  meaningEn: string;
  pronunciation: string;
  level: number; // 1-10
  category: string;
  toeicFreq: 'high' | 'medium' | 'low';
  example: string;
  shorts: Short[]; // 한 단어에 여러 쇼츠
}

interface Short {
  id: string;
  wordId: string;
  scenario: string;       // 시나리오 설명
  videoUrl: string;
  thumbnailUrl: string;
  likeCount: number;
}
```

**네비게이션 구조:**
```
words: [
  {
    word: "serendipity",
    shorts: [쇼츠1, 쇼츠2, 쇼츠3]  ← 좌우 스와이프
  },
  {
    word: "ephemeral",              ← 상하 스와이프
    shorts: [쇼츠1, 쇼츠2]
  },
  ...
]
```

---

## 9. Open Questions

| # | 질문 | 상태 | 결정 |
|---|------|------|------|
| 1 | 영상 자동재생 vs 탭하여 재생? | ❓ | |
| 2 | 음소거 기본 여부? | ❓ | |
| 3 | 영상 길이 (15초 vs 30초)? | ❓ | |
| 4 | 목업 데이터 몇 개 준비? | ❓ | |
| 5 | PWA 지원 범위? | ❓ | |

---

## 10. 마일스톤 (Milestones)

| Phase | 내용 | 산출물 | 예상 기간 |
|-------|------|--------|----------|
| **Phase 1** | 디자인 시스템 & 와이어프레임 | Figma | 3일 |
| **Phase 2** | 쇼츠 피드 UI | 코드 | 3일 |
| **Phase 3** | 단어 상세 & 저장 기능 | 코드 | 2일 |
| **Phase 4** | 목업 데이터 & 통합 | 데모 | 2일 |
| **Phase 5** | 테스트 & 배포 | 라이브 | 2일 |

**Total: 약 2주**

---

## Appendix

### A. 변경 이력

| 버전 | 날짜 | 변경 내용 | 작성자 |
|------|------|----------|--------|
| 0.1.0 | 2026-02-14 | 초안 작성 | Richbot |
| 0.2.0 | 2026-02-14 | Google Docs 내용 통합 | Richbot |
| 0.3.0 | 2026-02-14 | 구글 스타일 PRD로 재구성, Non-Goals 추가 | Richbot |
| 0.4.0 | 2026-02-14 | 프론트엔드 기술 스택 확정 (React+Vite+Swiper+PWA) | Hoseok, Richbot |
| 0.5.0 | 2026-02-14 | 2D 스와이프 네비게이션 정의 (상하:단어, 좌우:쇼츠) | Hoseok, Richbot |

### B. 참고 자료

- [Google PRD Template](https://docs.google.com/document/d/1WYNU47HZAdlwWI-JzQ1lJsNVVmMNomKY41SH9yXhICM/edit)
- [TikTok Design](https://www.tiktok.com/)
- [YouTube Shorts](https://www.youtube.com/shorts)

---

*이 문서는 Living Document로 프로젝트 진행에 따라 업데이트됩니다.*
