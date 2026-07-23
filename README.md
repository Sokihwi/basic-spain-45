# HOLA! 스페인어 기초강좌 — 45강 (Normal Basic)

스페인·중남미 **8명의 원어민 선생님**이 분야별로 나눠, 각자 고향 억양으로 가르치는 스페인어 기초 45강.
순수 HTML/CSS/Vanilla JS — 빌드·서버 없이 `site/index.html`을 브라우저로 열면 바로 실행됩니다.

> 🟢 Normal / Basic · 전체 이용가 · 그린 테마 + 강사별 포인트색

## ▶️ 실행
`site/index.html` 더블클릭 (또는 브라우저로 드래그).

> 웹에 배포되는 실제 사이트 루트는 **`site/` 폴더**입니다. 저장소 루트의 문서(`README.md`·`work-logs/`)는 배포 범위 밖이라 웹에 노출되지 않습니다.
> Vercel 설정: **Settings → Build and Deployment → Root Directory = `site`** (필수).

## 🛠️ 다시 빌드하기
이 사이트는 상위 폴더 `../강의/NN_강사_주제.md` 스크립트에서 **자동 생성**됩니다.
강의 스크립트를 추가·수정한 뒤 상위 폴더에서:

```
python build_45.py
```

만 실행하면 새 강의가 `lessons/`·`index.html`·강사 페이지에 자동 반영됩니다.
(미집필 강은 자동으로 "준비중" 카드로 표시됩니다.)

## 📂 구조
```
Basic_spain_45강/
├─ site/                   # ⭐ 배포 루트 (Vercel Root Directory = site)
│  ├─ index.html           # 허브 — 45강 그리드 + 8인 강사
│  ├─ personas.html        # 선생님 8명 카드
│  ├─ lessons/             # leccion-01 ~ 45.html (빌더 생성)
│  ├─ teachers/            # 강사 8인 자기소개 (assets/personas/*.md 에서 생성)
│  ├─ assets/
│  │  ├─ style.css         # 공통 디자인 시스템 (그린 테마 + --accent)
│  │  ├─ script.js         # .reveal 스크롤 애니메이션
│  │  ├─ fonts/            # 오프라인 내장 폰트 (Pretendard 우선)
│  │  └─ personas/         # 강사 프로필 png + 자기소개 md
│  ├─ vercel.json
│  └─ .vercelignore
├─ work-logs/              # 작업일지 (배포 범위 밖)
└─ README.md
```

## 🧑‍🏫 강사 8인 (각 5~6강)
소피아(세비야)·발레리아(마드리드)·마르티나(부에노스아이레스)·카밀라(멕시코시티)·
발렌티나(메데인)·루나(마이애미)·파울라(산티아고)·엘레나(카나리아).

각 강의 페이지는 담당 강사의 포인트색과 프로필을 자동으로 입습니다.
모든 콘텐츠는 가상 강사진이 집필한 오리지널이며, 외부 블로그 인용·출처 표기는 포함하지 않습니다.
