# RIM-PT 사이트 — 파일 목록

이 문서는 현재 저장소에 포함된 **페이지·설정·에셋** 경로와, 이미지가 실제로 코드에 연결되는 **인덱스 배열 위치**를 정리한 것입니다. (배포: GitHub Pages + `CNAME` 기준 `rim-pt.com` 가정)

이미지를 추가/교체할 때는 **① 파일을 `assets/` 아래 알맞은 폴더에 넣고 → ② 아래 "이미지 인덱스 배열" 표에서 해당 페이지의 배열에 경로를 추가**하면 됩니다.

---

## 루트 (HTML · 설정)

| 파일 | 설명 |
|------|------|
| `index.html` | 메인 랜딩. 히어로, 트레이너 소개, 비포앤애프터(`BA_INDEX_SLIDES`), 바디프로필 갤러리(`BODY_PROFILE_INDEX`), 후기 사진 갤러리(`REVIEW_PHOTOS_INDEX`), 텍스트 후기 슬라이더, 프로그램, 상담 폼(FormSubmit) 등 |
| `member-results.html` | "실제 회원 변화 결과" 상세 페이지. 자체 `BA_CONTENTS_INDEX.slides` 배열로 비포/애프터 카드를 렌더링 (index.html과 별개 배열, 내용은 현재 동일하게 유지 중) |
| `body-profile.html` | 바디프로필 전용 갤러리 페이지. 자체 `BODY_PROFILE_INDEX` 배열 사용 (index.html의 것과 별개 배열, 현재 동일 내용) |
| `remote-coaching.html` | 원격 코칭 안내. **AS-IS**(메신저 기반) / **TO-BE**(기획안 슬라이드) 탭 전환 + `assets/remote-coaching/` PNG 슬라이드 (`src`/`caption` 배열, JS 내 인라인). URL로 To-BE 탭 노출 가능 → 아래 표 참고 |
| `qr.html` | 상담·공유·QR 단일 페이지(Web Share, `rim-pt.com` QR). URL로 즉시 홈 이동 가능 → 아래 표 참고 |
| `Big_qr.html` | 인쇄용 큰 QR 전용 페이지 |
| `robots.txt` | 검색 로봇 규칙 |
| `sitemap.xml` | 사이트맵 |
| `rss.xml` | RSS 피드 |
| `CNAME` | GitHub Pages 커스텀 도메인 (`rim-pt.com`) |
| `README.md` | 저장소 간단 설명 |
| `test_code.html` | 어느 페이지에서도 링크되지 않는 독립 실험용 HTML (정리 시 삭제 후보) |
| `temp_1776833610426.-517680118.html` | 임시/테스트용으로 보이는 대용량 HTML, 어디서도 참조되지 않음 (정리 시 삭제 후보) |

---

## URL 쿼리 (To-BE 프리뷰 · QR 리다이렉트)

배포 경로가 `https://rim-pt.com/` 일 때 예시입니다. **별도 라우트 없이** 쿼리 문자열만으로 동작을 바꿉니다.

| URL 예시 | 파일 | 동작 |
|----------|------|------|
| `remote-coaching.html?devFlow=1` | `remote-coaching.html` | **TO-BE(개발 중)** 탭을 화면에 표시합니다. 기본 접속(`?` 없음)에서는 해당 탭이 숨겨져 있고, **AS-IS / TO-BE 본문 전환**은 페이지 안 탭으로만 전환됩니다. |
| `qr.html?go=1` | `qr.html` | QR 랜딩을 건너뛰고 **공식 홈**(`https://rim-pt.com/`)으로 바로 이동합니다. (스크립트: `URLSearchParams` → `go=1`) |

---

## 이미지 인덱스 배열 (파일 추가 시 여기를 수정)

모든 인덱스는 상대경로 문자열 배열/객체이며, 렌더링 시 `baEncPath()`(각 페이지에 인라인 정의된 동일 함수)로 세그먼트별 `encodeURIComponent`를 적용해 공백·한글 파일명을 안전하게 처리합니다. **파일명에 공백/한글이 있어도 그대로 넣으면 됩니다.**

| 배열명 | 위치 | 데이터 형태 | 용도 |
|--------|------|-------------|------|
| `BA_INDEX_SLIDES` | `index.html` (~1196행) | `{before, after, member, infoSub, stats[]}[]` | 메인 페이지 비포/애프터 슬라이더 |
| `BODY_PROFILE_INDEX` | `index.html` (~1228행) | `string[]` (경로만) | 메인 페이지 바디프로필 갤러리 (`data-mi-gallery="contents-body"`) |
| `REVIEW_PHOTOS_INDEX` | `index.html` (~1190행) | `string[]` (경로만) | 메인 페이지 후기 사진 갤러리 (순서대로 1~4번) |
| `BA_CONTENTS_INDEX.slides` | `member-results.html` (~239행) | `{code, category, before, after, member, infoSub, stats[]}[]` | 회원 결과 상세 페이지 비포/애프터 카드 (`category`: `diet`/`bulk`/`rehab` 탭) |
| `BODY_PROFILE_INDEX` | `body-profile.html` (~147행) | `string[]` (경로만) | 바디프로필 전용 페이지 갤러리 |

> ⚠️ `BODY_PROFILE_INDEX`는 `index.html`과 `body-profile.html`에 **각각 따로** 정의되어 있어, 바디프로필 사진을 추가/교체할 때는 **두 파일 모두** 수정해야 화면이 일치합니다.

---

## 에셋 — `assets/contents/`

비포·애프터·후기 이미지. 실제 폴더에는 아래 표의 "연결 배열"이 비어 있는(=미사용) 파일도 있습니다 — 새 비포/애프터 세트를 추가할 때 재사용하거나, 위 배열에 새 항목으로 넣어 연결하세요.

| 파일명 | 연결 배열 (사용처) |
|--------|----------|
| `WhatsApp Image 2026-04-28 at 11.54.19 AM.jpeg` / `...11.54.20 AM.jpeg` | `BA_INDEX_SLIDES` / `BA_CONTENTS_INDEX.slides` — 김00 회원 before/after |
| `WhatsApp Image 2026-04-29 at 2.12.39 PM.jpeg` / `...2.12.40 PM.jpeg` | `BA_INDEX_SLIDES` / `BA_CONTENTS_INDEX.slides` — 엄00 회원 before/after |
| `주00비포.jpg` / `주00애프터.jpg` | `BA_INDEX_SLIDES` / `BA_CONTENTS_INDEX.slides` — 주00 회원 before/after |
| `예림 pt후기 1.jpg` | `REVIEW_PHOTOS_INDEX` 1번 |
| `예림 pt후기2.jpg` | `REVIEW_PHOTOS_INDEX` 2번 |
| `ㅇㅖ림 pt후기 3.jpg` | `REVIEW_PHOTOS_INDEX` 3번 (파일명 자모 분리 오타 그대로 사용 중, 변경 시 배열도 함께 수정) |
| `예림pt후기4.jpg` | `REVIEW_PHOTOS_INDEX` 4번 |
| `주00인바디 비포1.jpg` / `주00인바디 비포2.jpg` | **미사용** (현재 어떤 배열에도 연결 안 됨) |
| `박00비포.jpg` / `박00애프터.jpg` | **미사용** (예전 비포/애프터 세트, 현재 배열에서 빠짐) |
| `박00비포2.jpg` / `박00애프터2.jpg` | **미사용** (동일 회원 대체 세트) |
| `엄00 비포.jpg` / `엄00애프터.jpg` | **미사용** (파일명에 공백 있음 — 위 WhatsApp 파일명 세트와는 별개의 엄00 이미지) |
| `예림바프1.jpg` | **미사용** |
| `윤OO 비포.jpeg` / `윤OO 에프터.jpeg` | **미사용 — 신규 추가 대기 이미지로 보임** (아직 어떤 배열에도 없음) |
| `이OO 비포.jpeg` / `이OO 에프터.jpeg` | **미사용 — 신규 추가 대기 이미지로 보임** (아직 어떤 배열에도 없음) |

> 다음 비포/애프터 세트를 추가할 때: 파일을 이 폴더에 넣고, `index.html`의 `BA_INDEX_SLIDES` **및** `member-results.html`의 `BA_CONTENTS_INDEX.slides`에 동일한 `{before, after, member, infoSub, stats}` 항목을 추가하면 두 페이지 모두 반영됩니다.

---

## 에셋 — `assets/contents_body/`

바디프로필 갤러리용 이미지. `BODY_PROFILE_INDEX`(위 두 곳) 순서와 개수가 일치해야 합니다.

| 파일 |
|------|
| `WhatsApp Image 2026-04-28 at 11.42.03 AM.jpeg` |
| `WhatsApp Image 2026-04-28 at 11.42.03 AM (1).jpeg` |
| `WhatsApp Image 2026-04-28 at 11.42.04 AM.jpeg` |
| `WhatsApp Image 2026-04-28 at 11.42.04 AM (1).jpeg` |
| `WhatsApp Image 2026-04-28 at 11.42.05 AM.jpeg` |

---

## 에셋 — `assets/members/`

현재 `.gitkeep`만 있는 빈 폴더. 회원별 이미지를 새 폴더 구조로 분리해 추가할 계획이라면 여기가 준비된 위치로 보이나, 아직 어떤 HTML도 이 경로를 참조하지 않습니다. 사용하려면 새 인덱스 배열과 렌더링 로직을 만들어야 합니다.

---

## 에셋 — `assets/트레이너/`

| 파일 | 설명 |
|------|------|
| `trainer-1.jpeg` | 히어로/소개/OG 이미지 등에서 참조 (`index.html`, `body-profile.html`, `remote-coaching.html`, `qr.html`의 `og:image`, `twitter:image`, JSON-LD `image` 및 어바웃 섹션 `<img>`) |
| `trainer-2.jpeg` | `index.html` 어바웃 섹션 슬라이드 2번째 사진 |
| `.gitkeep` | 빈 폴더 유지용(있는 경우) |

---

## 에셋 — `assets/remote-coaching/`

`remote-coaching.html`의 AS-IS/TO-BE 슬라이드 배열(JS 인라인, 파일 내 `src`/`caption` 쌍)에서 참조.

| 파일 |
|------|
| `asis-1.png` ~ `asis-5.png` |
| `tobe-1.png` ~ `tobe-5.png` |

---

## 에셋 — 기타

| 경로 | 설명 |
|------|------|
| `assets/.gitkeep` | `assets` 루트 유지용 |

---

*마지막 정리일: 2026-09-03*
