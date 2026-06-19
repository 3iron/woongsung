# 🐻 웅성웅성

> 페미니즘 독서 · 영화 모임 **웅성웅성**의 전용 앱

[![GitHub Pages](https://img.shields.io/badge/배포-GitHub%20Pages-pink?style=flat-square)](https://3iron.github.io/woonsung)

---

## 📱 서비스 소개

웅성웅성 모임원들이 함께 사용하는 모바일 전용 웹앱이에요.  
모임 일정 관리부터 영화·도서 룰렛, 공지사항까지 한 곳에서 확인할 수 있어요.

**→ [웅성웅성 룰렛 바로가기](https://3iron.github.io/woonsung)**

---

## ✨ 주요 기능

### 📅 모임 일정
- 달력에서 모임 날짜 한눈에 확인
- 날짜 탭하면 그날 일정 상세 보기
- 새 모임 일정 추가 (영화 / 도서 / 둘 다)
- 구글 시트와 연동되어 모든 멤버가 실시간 공유

### 🎡 룰렛
- 영화 / 도서 탭 전환
- 목록 추가 · 삭제 자유롭게
- 중앙 곰돌이 버튼 눌러서 오늘의 픽 뽑기

### 📋 모임 기록
- 지난 모임 히스토리 카드 형태로 확인
- 영화 / 도서 필터링
- 참여 멤버 표시

### 📢 공지사항
- 공지 / 투표 / 자유 카테고리
- 📌 고정 공지 상단 고정
- 🤍 좋아요 반응
- 구글 시트와 연동되어 모든 멤버가 실시간 공유

---

## 🗂 기술 스택

| 항목 | 내용 |
|------|------|
| 프론트엔드 | HTML, CSS, Vanilla JS (단일 파일) |
| 데이터베이스 | Google Sheets + Apps Script |
| 배포 | GitHub Pages |
| 대상 환경 | 모바일 웹 (PWA 지원) |

---

## 🗄 데이터 구조

### meetings 시트

| id | date | name | type | title | memo | members |
|----|------|------|------|-------|------|---------|
| 고유ID | YYYY-MM-DD | 모임 이름 | movie/book/both | 작품 제목 | 메모 | 멤버1,멤버2 |

### notices 시트

| id | category | title | body | author | date | likes | pinned |
|----|----------|-------|------|--------|------|-------|--------|
| 고유ID | notice/vote/free | 제목 | 내용 | 작성자 | YYYY-MM-DD | 좋아요수 | TRUE/FALSE |

---

## 🚀 배포 방법

### 1. 구글 시트 설정
1. [Google Sheets](https://sheets.google.com)에서 새 스프레드시트 생성
2. 시트 이름을 `meetings`, `notices` 두 개로 만들기
3. 각 시트 1행에 위 헤더 입력
4. **확장 프로그램 → Apps Script**에서 서버 코드 붙여넣기
5. **배포 → 새 배포 → 웹 앱 → 모든 사용자** 로 배포
6. 웹 앱 URL 복사

### 2. index.html 수정
```js
const SHEET_URL = '여기에_웹앱_URL_입력';
```

### 3. GitHub Pages 배포
1. 이 레포를 fork 또는 clone
2. `index.html`로 파일명 변경 후 업로드
3. Settings → Pages → Branch: main → Save
4. `https://{username}.github.io/woonsung` 접속

---

## 📁 파일 구조

```
woonsung/
├── index.html     # 앱 전체 (단일 파일)
└── README.md      # 이 파일
```

---

## 🐻 웅성웅성 모임 소개

페미니즘 시각으로 영화와 도서를 함께 읽고 이야기 나누는 모임이에요.  
매달 한 번씩 만나 다양한 작품을 통해 생각을 나눠요.

---

*made with 🩷 for 웅성웅성*
