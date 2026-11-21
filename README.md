# 🐻 웅성웅성

> 페미니즘 독서 · 영화 모임 **웅성웅성**의 전용 앱

[![GitHub Pages](https://img.shields.io/badge/배포-GitHub%20Pages-pink?style=flat-square)](https://3iron.github.io/woongsung/)

### 👉 **[웅성웅성 앱 바로가기](https://3iron.github.io/woongsung/)**

로그인 없이 **게스트로 둘러보기**를 누르면 모임 일정을 바로 확인할 수 있어요.

---

## 📱 서비스 소개

웅성웅성 모임원들이 함께 사용하는 모바일 전용 웹앱이에요.  
모임 일정 관리부터 영화·도서 룰렛, 공지사항까지 한 곳에서 확인할 수 있어요.

- **멤버**: 구글 로그인 후 모든 기능 사용 (일정·공지·룰렛 추가/삭제)
- **게스트**: 로그인 없이 모임 일정·공지·룰렛을 **조회만** 가능

---

## ✨ 주요 기능

### 🔐 로그인 / 게스트
- 구글 계정으로 간편 로그인
- `members` 시트에 등록된 계정만 멤버로 인증
- 게스트는 '게스트로 둘러보기' 버튼으로 조회 전용 접속

### 📅 모임 일정
- 달력에서 모임 날짜 한눈에 확인
- 날짜 탭하면 그날 일정 상세 보기
- 새 모임 일정 추가 (영화 / 도서 / 둘 다) — *멤버 전용*
- 구글 시트 + 노션(2026 모임 DB)과 연동되어 실시간 공유

### 🎡 룰렛
- 영화 / 도서 탭 전환
- 목록 추가 · 삭제 (추가는 멤버 전용, 노션 2026 추천 DB 연동)
- 중앙 곰돌이 버튼 눌러서 오늘의 픽 뽑기

### 📋 모임 기록
- 지난 모임 히스토리 카드 형태로 확인
- 영화 / 도서 필터링
- 참여 멤버 표시

### 📢 공지사항
- 공지 / 투표 / 자유 카테고리
- 📌 고정 공지 상단 고정
- 🤍 좋아요 반응
- 작성자 본인 또는 관리자(admin)만 삭제 가능

---

## 🗂 기술 스택

| 항목 | 내용 |
|------|------|
| 프론트엔드 | HTML, CSS, Vanilla JS (단일 파일) |
| 백엔드 | Google Apps Script |
| 데이터베이스 | Google Sheets + Notion API |
| 인증 | Google OAuth (ID 토큰 검증) |
| 배포 | GitHub Pages |
| 대상 환경 | 모바일 웹 (PWA 지원) |

---

## 🔑 권한 모델

| 구분 | 조회 | 작성·삭제 |
|------|------|-----------|
| 게스트 (비로그인) | ✅ | ❌ |
| member | ✅ | 본인 글만 삭제 |
| admin | ✅ | 모든 글·모임 삭제 |

- 멤버 명단은 `members` 시트에서 관리 (행 추가/삭제만으로 멤버 변경, 재배포 불필요)
- 백엔드는 조회(`doGet`)는 공개, 작성·삭제(`doPost`)는 멤버만 허용

---

## 🗄 데이터 구조

### members 시트 (로그인 허용 멤버)

| email | name | role |
|-------|------|------|
| user@gmail.com | 이름 | admin / member |

> 1행은 머리글, 2행부터 멤버 입력. `role`을 비우면 member로 처리돼요.

### meetings 시트

| id | date | name | type | title | memo | members |
|----|------|------|------|-------|------|---------|
| 고유ID | YYYY-MM-DD | 모임 이름 | movie/book/both | 작품 제목 | 메모 | 멤버1,멤버2 |

### notices 시트

| id | category | title | body | author | date | likes | pinned | authorEmail |
|----|----------|-------|------|--------|------|-------|--------|-------------|
| 고유ID | notice/vote/free | 제목 | 내용 | 작성자 | YYYY-MM-DD | 좋아요수 | TRUE/FALSE | 작성자이메일 |

---

## 🚀 배포 방법

### 1. 구글 시트 + Apps Script 설정
1. [Google Sheets](https://sheets.google.com)에서 새 스프레드시트 생성
2. 시트를 `meetings`, `notices`, `members` 세 개로 만들고 1행에 위 헤더 입력
3. **확장 프로그램 → Apps Script**에서 `Code.gs` 붙여넣기
4. 프로젝트 설정 → **스크립트 속성**에 `NOTION_TOKEN` 등록 (노션 연동용)
5. **배포 → 새 배포 → 웹 앱 → 액세스: 모든 사용자** 로 배포 후 웹 앱 URL 복사

### 2. index.html 수정
```js
const SHEET_URL = '여기에_웹앱_URL_입력';
const GOOGLE_CLIENT_ID = '여기에_구글_OAuth_클라이언트_ID_입력';
```

### 3. GitHub Pages 배포
1. 이 레포를 fork 또는 clone
2. `index.html` 업로드 후 Settings → Pages → Branch: `main` → Save
3. `https://{username}.github.io/woongsung/` 접속

> 멤버는 이후 `members` 시트에 행만 추가하면 됩니다. 코드 수정·재배포가 필요 없어요.

---

## 📁 파일 구조

```
woongsung/
├── index.html     # 앱 전체 (프론트엔드, 단일 파일)
├── Code.gs        # Apps Script 백엔드 (레포 외부에서 관리)
└── README.md      # 이 파일
```

---

## 🐻 웅성웅성 모임 소개

페미니즘 시각으로 영화와 도서를 함께 읽고 이야기 나누는 모임이에요.  
매달 한 번씩 만나 다양한 작품을 통해 생각을 나눠요.

---

*made with 🩷 for 웅성웅성*
