# Storage Architecture - Cloudflare KV + R2

## 📋 개요

Word Shorts의 스토리지 아키텍처. Cloudflare 스택 기반으로 빠른 엣지 딜리버리와 효율적인 캐싱을 목표로 함.

## 🏗️ 아키텍처

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Client    │────▶│  Cloudflare │────▶│     KV      │
│  (Browser)  │     │   Workers   │     │  (메타데이터) │
└─────────────┘     └─────────────┘     └─────────────┘
                           │
                           ▼
                    ┌─────────────┐
                    │     R2      │
                    │ (이미지/영상) │
                    └─────────────┘
```

## 📦 스토리지 구조

### Cloudflare KV (메타데이터)

**Key 형식:** 영단어 (예: `apple`, `banana`)

**Value 형식:**
```json
{
  "word": "apple",
  "assets": [
    {
      "type": "image",
      "url": "https://r2.wordshorts.com/apple/img-a3f2c1.png",
      "created": "2026-02-24",
      "prompt": "A red apple falling from a tree..."
    },
    {
      "type": "video",
      "url": "https://r2.wordshorts.com/apple/vid-b4e3d2.mp4",
      "duration": 15,
      "created": "2026-02-24",
      "thumbnail": "https://r2.wordshorts.com/apple/thumb-b4e3d2.jpg"
    }
  ],
  "metadata": {
    "definition": "a round fruit with red or green skin",
    "pronunciation": "/ˈæp.əl/",
    "examples": ["I ate an apple.", "The apple fell from the tree."]
  }
}
```

### Cloudflare R2 (미디어 파일)

**버킷 구조:**
```
wordshorts-media/
├── apple/
│   ├── img-a3f2c1.png
│   ├── vid-b4e3d2.mp4
│   └── thumb-b4e3d2.jpg
├── banana/
│   ├── img-c5f4e3.png
│   └── vid-d6g5f4.mp4
└── ...
```

**파일명 규칙:**
- 해시 기반 파일명으로 캐시 무효화 불필요
- 형식: `{type}-{hash}.{ext}`

## 🚀 캐싱 전략

### 1. R2 미디어 파일 (HTTP Cache)

```
Cache-Control: public, max-age=31536000, immutable
```

- **max-age=31536000**: 1년 캐시
- **immutable**: 콘텐츠 변경 없음 명시
- 해시 기반 URL로 버전 관리 → 영구 캐시 가능

**R2 버킷 설정 (wrangler.toml):**
```toml
[[r2_buckets]]
binding = "MEDIA_BUCKET"
bucket_name = "wordshorts-media"

# Custom domain with cache rules
# r2.wordshorts.com → Cache-Control headers
```

### 2. 본 단어 기록 (Client-side)

**localStorage (간단 버전):**
```javascript
// 저장
const viewed = JSON.parse(localStorage.getItem('viewedWords') || '[]');
viewed.push('apple');
localStorage.setItem('viewedWords', JSON.stringify([...new Set(viewed)]));

// 조회
const viewedWords = JSON.parse(localStorage.getItem('viewedWords') || '[]');
```

**IndexedDB (대용량):**
```javascript
// 1000개 이상 단어 기록 시 IndexedDB 권장
const db = await openDB('wordshorts', 1, {
  upgrade(db) {
    db.createObjectStore('viewed', { keyPath: 'word' });
  }
});

await db.put('viewed', { word: 'apple', viewedAt: Date.now() });
```

### 3. 메타데이터 캐시 (Client-side)

```javascript
// 메모리 캐시 + TTL
const metadataCache = new Map();
const CACHE_TTL = 24 * 60 * 60 * 1000; // 24시간

async function getWordData(word) {
  const cached = metadataCache.get(word);
  if (cached && Date.now() - cached.timestamp < CACHE_TTL) {
    return cached.data;
  }
  
  const data = await fetch(`/api/word/${word}`).then(r => r.json());
  metadataCache.set(word, { data, timestamp: Date.now() });
  return data;
}
```

## 🔧 Worker 예시

```javascript
// src/worker.js
export default {
  async fetch(request, env) {
    const url = new URL(request.url);
    const word = url.pathname.split('/')[2]; // /api/word/{word}
    
    // KV에서 메타데이터 조회
    const data = await env.WORD_KV.get(word, 'json');
    
    if (!data) {
      return new Response('Not found', { status: 404 });
    }
    
    return new Response(JSON.stringify(data), {
      headers: {
        'Content-Type': 'application/json',
        'Cache-Control': 'public, max-age=3600', // 1시간
      }
    });
  }
};
```

## 📊 비용 최적화

| 서비스 | 무료 티어 | 초과 시 |
|--------|----------|---------|
| KV | 읽기 10만/일, 쓰기 1천/일 | $0.50/백만 읽기 |
| R2 | 저장 10GB, egress 무료 | $0.015/GB/월 |
| Workers | 요청 10만/일 | $0.50/백만 요청 |

**R2 egress 무료**가 핵심 — 영상 전송량 많아도 비용 X

## 🛣️ 향후 확장

### Phase 2: Service Worker (PWA)
```javascript
// 오프라인 지원
self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      return response || fetch(event.request);
    })
  );
});
```

### Phase 3: D1 (복잡한 쿼리)
- "최근 추가된 단어"
- "영상 있는 단어만"
- "난이도별 필터"

```sql
-- D1 스키마 예시
CREATE TABLE words (
  word TEXT PRIMARY KEY,
  has_video BOOLEAN,
  difficulty INTEGER,
  created_at TIMESTAMP
);
```

---

*Last Updated: 2026-02-24*
