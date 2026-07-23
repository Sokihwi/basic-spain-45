# CLAUDE.md — Basic_spain 45강 개발 규칙

이 폴더(`Basic_spain_45강/`)만 열고 이어서 작업할 때 반드시 따를 규칙입니다. 16강(`basic-spain-16`)과 **동일한 디자인 시스템·구조**를 공유하되, 강의 분량(45강)과 강사 배정이 다릅니다.

---

## 프로젝트 개요
- **HOLA! 스페인어 기초강좌 — Normal/Basic 버전, 45강.** 전체 이용가(SFW) 교육 콘텐츠.
- 스택: **순수 HTML5 + CSS + Vanilla JS.** 프레임워크·빌드·번들러 없음. `site/index.html`을 열면 바로 실행.
- 디자인 토큰·컴포넌트는 `DESIGN.md` 참조. 구조·실행은 `README.md` 참조.

## 디자인 규칙
- 한글 폰트는 **Pretendard 최우선**, 스페인어/영문은 Inter, 디스플레이는 Playfair Display. 폰트는 `site/assets/fonts/`에 내장.
- 🟢 **Normal 그린 테마(`--primary: #2E7D32`)** 고정. Hot 버전 빨강(#C62828)은 절대 혼용 금지.
- `site/assets/style.css`의 **기존 클래스·CSS 변수만** 사용. 토큰 밖 새 색·폰트 임의 생성 금지.
- 다크 배경 + 글래스모피즘 + `.reveal` 스크롤 애니메이션 + `prefers-reduced-motion` 대응 유지.

## 강사(페르소나) 시스템 — ⚠️ 가장 중요
- 내레이터는 **8명 페르소나**가 45강을 **주제별로 분담**(연속 구간 아님, 강의 주제에 맞는 강사 배정). 담당 강의:
  - **소피아**(세비야): 01·02·03·06·11·12
  - **마르티나**(부에노스아이레스): 04·05·20·38·41
  - **루나**(마이애미): 07·09·15·28·30
  - **발레리아**(마드리드): 08·17·23·25·27
  - **카밀라**(멕시코시티): 10·13·16·18·19·33
  - **발렌티나**(메데인): 14·32·34·35·42·44
  - **엘레나**(카나리아): 21·24·31·36·43·45
  - **파울라**(산티아고): 22·26·29·37·39·40
- **공유 `style.css`의 `.valentino .bubble::before` 기본값은 "발렌티노"** 그대로. 따라서 **각 강의 페이지 `<head>`의 per-page `<style>` override가 필수**:
  ```css
  .valentino .bubble::before { content: "강사이름"; }
  .valentino .avatar { background-image: url('../assets/personas/{name}.png'); background-size:cover; background-position:center 22%; font-size:0; color:transparent; }
  ```
  새 강의 추가 시 이 override를 빠뜨리면 화면에 "발렌티노"가 그대로 노출됨.
- 강의 본문/타이틀/푸터의 강사 이름도 담당 페르소나로 일치시킬 것.
- 파일명 매핑: 소피아 sofia · 발레리아 valeria · 마르티나 martina · 카밀라 camila · 발렌티나 valentina · 루나 luna · 파울라 paula · 엘레나 elena.

## 이미지 규칙 — ⚠️ 필수
- 강사 이미지는 **`site/assets/personas/{name}.png`(프로필)만** 사용.
- **이 폴더 밖의 이미지는 어떤 경로에서도 반입 금지.** 특히 번호가 붙은 장면 이미지(`*_NN_*.jpg`) 형태의 외부 자산은 사용하지 않는다.
- 모든 콘텐츠는 **전체 이용가**를 원칙으로 한다. 페르소나 설정을 인용할 땐 출신·억양·성격 등 건전 속성만.

## 템플릿 / 패턴
- 강의 페이지 템플릿: **`site/lessons/leccion-01.html`** (구조·톤 기준).
- 선생님 자기소개 페이지 템플릿: **`site/teachers/sofia.html`**. 내용 원본은 `site/assets/personas/{name}.md`.
- 강의 흐름: 🎙️인사 → 개념(말풍선) → 💬예문(.examples) → ⚠️오해 주의(.callout.warn) → 🧠암기 꿀팁(.callout) → ✅정리(.summary)+다음 차시 예고.
- 차시 **사이에 끼워넣을 때는 번호 대량 변경 금지** → suffix 파일(예: `05b`) 생성 + **인접 차시 네비(prev/next)와 허브 카드만 수정**. 링크 깨짐 방지.

## 경로 규칙
- **배포 루트(웹 루트)는 `site/` 폴더**다. 모든 강의/에셋은 `site/` 안에 둔다. 저장소 루트(`CLAUDE.md`·`README.md`·`DESIGN.md`·`work-logs/`)는 배포 범위 밖(웹 미노출).
- `site/lessons/`, `site/teachers/` 안의 페이지 → 에셋은 `../assets/...`, 홈은 `../index.html`.
- `site/index.html`, `site/personas.html` → 에셋은 `assets/...`.
- `site/` 외부(`../../`, `src/`, 드라이브 절대경로) 참조 금지 — 폴더 이식성 유지.

## 배포 규칙
- **GitHub `Sokihwi/basic-spain-45`(public) → Vercel 자동배포.** `git push origin main` 하면 배포된다.
- Vercel **Root Directory = `site`** 필수. `vercel deploy --prod` 수동 배포는 쓰지 않는다(git push로 통일).

## 작업 후 점검(권장)
- 잔여 "발렌티노" 0건, per-page override 존재, 이미지·강의 링크 깨짐 0건을 grep으로 확인.
