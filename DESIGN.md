# DESIGN.md — Basic_spain 45강 디자인 시스템

HOLA! 스페인어 기초강좌(Normal/Basic, 45강) UI에 적용되는 공통 디자인 시스템입니다. 모든 페이지는 `site/assets/style.css`의 토큰을 사용하며, **새 색·폰트를 토큰 밖에서 임의로 만들지 않습니다.** (16강과 동일한 토큰을 공유하되 페르소나 액센트색만 45강 고유값입니다.)

---

## 1. 타이포그래피

| 용도 | 폰트 | 비고 |
|---|---|---|
| 기본(한글 최우선) | **Pretendard** | 모든 본문 |
| 스페인어·영문 | **Inter** | `.es` 클래스, `--font-es` |
| 디스플레이/헤드라인 | **Playfair Display** | `--font-display` |

- 폰트 스택: `'Pretendard', 'Pretendard Variable', -apple-system, BlinkMacSystemFont, sans-serif`
- 폰트는 `site/assets/fonts/`에 내장(오프라인 동작). CDN fallback도 가능.
- 반응형 크기는 `clamp()` 사용.

---

## 2. 컬러 팔레트

### 공통 토큰
```css
--dark: #121212;          /* 배경 */
--bg-2: #0d130e;
--card-bg: rgba(31, 40, 35, 0.45);
--text-main: #E0E0E0;
--text-bright: #ffffff;
--text-muted: #8b9a8e;
```

### 🟢 Normal 테마 (로맨틱 & 안정감)
```css
--primary: #2E7D32;       /* 소프트 그린(주조색) */
--primary-light: #66bb6a;
--primary-soft: rgba(46, 125, 50, 0.14);
--badge-bg: #E8F5E9;
--badge-text: #1B5E20;
--accent-gold: #c8a24a;
```

> Hot 버전(빨강 #C62828)은 별도 프로젝트이며 이 폴더와 무관.

### 페르소나 액센트(소개 페이지 전용)
선생님 소개(`teachers/*.html`, `personas.html`)에서만 per-page `--accent`로 인물 테마색을 씀:
소피아 #ff7675 · 발레리아 #e84393 · 마르티나 #74b9a8 · 카밀라 #ff9f43 · 발렌티나 #00b894 · 루나 #a29bfe · 파울라 #0984e3 · 엘레나 #fdcb6e.

---

## 3. Glassmorphism
```css
--glass-bg: rgba(20, 26, 21, 0.65);
--glass-border: rgba(255, 255, 255, 0.10);
--glass-shadow: 0 15px 35px 0 rgba(0, 0, 0, 0.5);
--glass-blur: blur(16px) saturate(180%);
```
적용 대상: 강사 말풍선, 정리 박스, 소개 카드, 모달성 요소.

---

## 4. 모션
```css
transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
```
- 섹션은 `.reveal` + IntersectionObserver(`script.js`)로 스크롤 진입 시 fade-slide-up.
- 모든 인터랙티브 요소에 hover 상태.
- `prefers-reduced-motion: reduce` 시 애니메이션 비활성(접근성).

---

## 5. 핵심 컴포넌트 (style.css 클래스)

| 클래스 | 용도 |
|---|---|
| `.hero` / `.topbar` | 페이지 상단 헤더·고정 바 |
| `.valentino` + `.avatar` + `.bubble` | **강사 말풍선** (이름은 `.bubble::before`, 강의별 override) |
| `.examples` > `.ex-card` (`.es-line`/`.ko-line`/`.note`) | 예문 카드 |
| `.callout` / `.callout.warn` | 꿀팁 / ⚠️오해 주의 박스 |
| `.grammar-table` | 문법·표현 표 |
| `.summary` | 정리·요약 박스 |
| `.lesson-nav` / `.home-link` | 차시 네비·홈 복귀 |
| `.lesson-grid`(허브) / `.p-card`(소개) / `.t-hero`(자기소개) | 페이지별 카드 레이아웃 |

---

## 6. 안티패턴 (하지 말 것)
- ❌ 토큰 밖 색·폰트 임의 사용 (브라우저 기본 스타일 방치 포함)
- ❌ 프레임워크(React/Bootstrap 등) 도입
- ❌ hover/focus 상태 없는 인터랙티브 요소
- ❌ Hot 버전(빨강) 색을 Normal 강의에 혼용
- ❌ 한글 폰트에 Pretendard 외 폰트 우선 지정
