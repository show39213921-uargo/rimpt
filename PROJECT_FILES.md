# RIM-PT 사이트 — 파일 목록

이 문서는 현재 저장소에 포함된 **페이지·설정·에셋** 경로를 정리한 것입니다. (배포: GitHub Pages + `CNAME` 기준 `rim-pt.com` 가정)

---

## 루트 (HTML · 설정)

| 파일 | 설명 |
|------|------|
| `index.html` | 메인 랜딩. 히어로, 트레이너 소개, 비포앤애프터(`BA_CONTENTS_INDEX`), 후기 사진 갤러리(`REVIEW_PHOTOS_INDEX`), 텍스트 후기 슬라이더, 프로그램, 상담 폼(FormSubmit) 등 |
| `remote-coaching.html` | 원격 코칭 안내. **AS-IS**(메신저 기반) / **TO-BE**(기획안 슬라이드) 탭 전환 + `assets/remote-coaching/` PNG 슬라이드. URL로 To-BE 탭 노출 가능 → 아래 표 참고 |
| `qr.html` | 상담·공유·QR 단일 페이지(Web Share, `rim-pt.com` QR). URL로 즉시 홈 이동 가능 → 아래 표 참고 |
| `Big_qr.html` | 인쇄용 큰 QR 전용 페이지 |
| `robots.txt` | 검색 로봇 규칙 |
| `sitemap.xml` | 사이트맵 |
| `rss.xml` | RSS 피드 |
| `CNAME` | GitHub Pages 커스텀 도메인 (`rim-pt.com`) |
| `README.md` | 저장소 간단 설명 |
| `temp_1776833610426.-517680118.html` | 임시/테스트용으로 보이는 HTML (정리 시 삭제 후보) |

---

## URL 쿼리 (To-BE 프리뷰 · QR 리다이렉트)

배포 경로가 `https://rim-pt.com/` 일 때 예시입니다. **별도 라우트 없이** 쿼리 문자열만으로 동작을 바꿉니다.

| URL 예시 | 파일 | 동작 |
|----------|------|------|
| `remote-coaching.html?devFlow=1` | `remote-coaching.html` | **TO-BE(개발 중)** 탭을 화면에 표시합니다. 기본 접속(`?` 없음)에서는 해당 탭이 숨겨져 있고, **AS-IS / TO-BE 본문 전환**은 페이지 안 탭으로만 전환됩니다. |
| `qr.html?go=1` | `qr.html` | QR 랜딩을 건너뛰고 **공식 홈**(`https://rim-pt.com/`)으로 바로 이동합니다. (스크립트: `URLSearchParams` → `go=1`) |

---

## 에셋 — `assets/contents/`

비포·애프터·후기·기타 이미지. `index.html`의 **`BA_CONTENTS_INDEX`**, **`REVIEW_PHOTOS_INDEX`**, `otherFiles`와 연동되는 이름을 유지하는 것이 좋습니다.

| 파일명 | 용도(참고) |
|--------|------------|
| `주00비포.jpg` | 비포앤애프터 슬라이더 1 — Before |
| `주00애프터.jpg` | 비포앤애프터 슬라이더 1 — After |
| `주00인바디 비포1.jpg` | 인바디 비포 (인덱스 `otherFiles`) |
| `주00인바디 비포2.jpg` | 인바디 비포 (인덱스 `otherFiles`) |
| `박00비포.jpg` | 비포앤애프터 슬라이더 2 — Before |
| `박00애프터.jpg` | 비포앤애프터 슬라이더 2 — After |
| `박00비포2.jpg` | 동일 회원 대체 세트 (`alternates`) |
| `박00애프터2.jpg` | 동일 회원 대체 세트 (`alternates`) |
| `엄00 비포.jpg` | 비포앤애프터 슬라이더 3 — Before (파일명에 공백 있음) |
| `엄00애프터.jpg` | 비포앤애프터 슬라이더 3 — After |
| `예림 pt후기 1.jpg` | 후기 사진 갤러리 1번 |
| `예림 pt후기2.jpg` | 후기 사진 갤러리 2번 |
| `ㅇㅖ림 pt후기 3.jpg` | 후기 사진 갤러리 3번 |
| `예림pt후기4.jpg` | 후기 사진 갤러리 4번 |
| `예림바프1.jpg` | 기타 (`otherFiles`) |

---

## 에셋 — `assets/트레이너/`

| 파일 | 설명 |
|------|------|
| `trainer-1.jpeg` | 트레이너/히어로 등 참조 이미지 |
| `trainer-2.jpeg` | 위와 동일 |
| `.gitkeep` | 빈 폴더 유지용(있는 경우) |

---

## 에셋 — `assets/remote-coaching/`

`remote-coaching.html` 슬라이드용 PNG.

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

## `index.html`에서 이름으로 참조하는 주요 배열

- **`BA_CONTENTS_INDEX`** — `assets/contents/` 비포/애프터 쌍, 탭 카테고리(`diet` / `bulk` / `rehab`), `alternates`, `otherFiles`
- **`REVIEW_PHOTOS_INDEX`** — 후기 1~4 순서의 이미지 경로 (썸네일·메인 갤러리)

파일을 바꿀 때는 **위 배열과 HTML의 썸네일 개수**를 함께 맞추면 됩니다.

---

*마지막 정리일: 2026-04-23*
