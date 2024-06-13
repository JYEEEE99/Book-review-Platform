# 📚 온라인 도서 리뷰 플랫폼

본 프로젝트는 사용자가 다양한 도서에 대한 리뷰를 작성하고, 다른 사용자와 공유할 수 있는 온라인 도서 리뷰 플랫폼을 개발하는 것을 목표로 합니다. 본 기획안은 주요 기능, 역할 분담, 상세 요구사항, API 설계, 그리고 디자인 가이드 등을 포함합니다.

---

## 주요 기능

### 사용자 관리
- **회원가입**: 이메일, 비밀번호, 닉네임 입력 (이메일 중복 체크)
- **로그인**: 이메일과 비밀번호로 로그인, 인증 토큰 발급, 소셜 로그인(Google, Facebook)
- **로그아웃**: 사용자 로그아웃 기능
- **프로필 수정**: 닉네임 및 프로필 사진 수정

### 도서 관리
- **도서 목록 보기**: 다양한 카테고리와 검색 기능을 통해 도서 목록 확인
- **도서 상세 정보**: 선택한 도서의 상세 정보 및 리뷰 보기

### 리뷰 관리
- **리뷰 작성**: 평점(1~5점) 및 내용 작성
- **리뷰 수정 및 삭제**: 작성자 본인만 수정 및 삭제 가능
- **리뷰 평가**: 다른 사용자의 리뷰에 대해 좋아요/싫어요 평가

### 알림 기능
- **리뷰 알림**: 사용자가 작성한 리뷰에 좋아요/댓글 알림
- **도서 추가 알림**: 새로운 도서 추가 알림

### 도서 추가 및 수정
- **도서 추가 및 수정**: 도서 수정 및 추가를 위한 관리자 전용 페이지

---

## 주요 페이지 구성 및 설명

### 메인 홈 페이지 (Home)
파일: `Home.tsx`

#### 기능
- **최신 리뷰 섹션**: 최신 리뷰 보임 (가로 자동 슬라이드)
- **인기 도서 섹션**: 인기 도서 보임 (가로 자동 슬라이드)
- **검색 바**: 도서 제목이나 저자 이름으로 검색 가능
- **카테고리 필터**: 특정 카테고리 도서 빠르게 찾기
- **도서 리스트**: 카테고리별 도서 리스트 보임

### 도서 상세 페이지 (Book Detail)
파일: `BookDetail.tsx`

#### 기능
- **도서 정보**: 선택한 도서의 제목, 저자, 출판사, 출판일, 설명 보임
- **리뷰 리스트**: 도서에 대한 리뷰 목록 보임
- **리뷰 작성 폼**: 리뷰 작성 가능

### 회원가입 페이지 (Signup)
파일: `Signup.tsx`

#### 기능
- **회원가입 폼**: 이메일, 비밀번호, 닉네임 입력 폼 및 유효성 검사 포함 (OAuth를 통해 자동 회원가입 - Google, Facebook)

### 로그인 페이지 (Login)
파일: `Login.tsx`

#### 기능
- **로그인 폼**: 이메일과 비밀번호로 로그인, 인증 토큰 발급 (소셜 로그인 - Google, Facebook)

### 프로필 페이지 (Profile)
파일: `Profile.tsx`

#### 기능
- **사용자 정보 보기 및 수정**: 닉네임 및 프로필 사진 수정 가능

### 도서 추가 및 수정 페이지 (BookManagement)
파일: `BookManagement.tsx`

#### 기능
- **도서 관리**: 도서 추가, 수정, 삭제 가능

### 즐겨찾기 페이지 (Favorites)
파일: `Favorites.tsx`

#### 기능
- **즐겨찾기 목록**: 즐겨찾기에 추가한 도서 및 리뷰 목록 보임

### 알림 모달 (Notifications)
파일: `Notifications.tsx`

#### 기능
- **알림 표시**: 도서 추가, 리뷰에 대한 좋아요/댓글 알림 표시

### 리뷰 작성 및 관리 페이지 (Review Management)
파일: `ReviewManagement.tsx`

#### 기능
- **작성한 리뷰 목록**: 사용자가 작성한 리뷰 목록 보임
- **리뷰 수정 및 삭제**: 작성한 리뷰 수정 및 삭제 가능

### 다국어 지원 설정 페이지 (Language Settings)
파일: `LanguageSettings.tsx`

#### 기능
- **언어 설정**: 사용자 인터페이스 언어 설정 가능 (예: 영어, 한국어)

---

## API 설계

### 사용자 관리 API
- `POST /api/auth/signup`: 회원가입
- `POST /api/auth/login`: 로그인
- `GET /api/users/me`: 내 프로필 정보 가져오기
- `PUT /api/users/me`: 내 프로필 수정

### 도서 API
- `GET /api/books`: 도서 목록 조회 (검색 및 필터)
- `GET /api/books/{id}`: 도서 상세 정보 조회
- `POST /api/books`: 도서 추가 (관리자 권한)
- `PUT /api/books/{id}`: 도서 수정 (관리자 권한)
- `DELETE /api/books/{id}`: 도서 삭제 (관리자 권한)

### 리뷰 API
- `POST /api/books/{id}/reviews`: 리뷰 작성
- `PUT /api/reviews/{id}`: 리뷰 수정
- `DELETE /api/reviews/{id}`: 리뷰 삭제
- `POST /api/reviews/{id}/like`: 리뷰 좋아요
- `POST /api/reviews/{id}/dislike`: 리뷰 싫어요

---

## 상세 요구사항

### 사용자 관리
- 회원가입: 이메일, 비밀번호, 닉네임 입력, 이메일 중복 체크
- 로그인: 이메일과 비밀번호로 로그인, 인증 토큰 발급
- 프로필 수정: 닉네임 및 프로필 사진 수정

### 도서 목록 보기
- 카테고리별 도서 목록
- 검색 기능: 제목, 저자 등으로 검색
- 페이지네이션 적용

### 도서 상세 정보
- 도서 제목, 저자, 출판사, 출판일, 간략한 설명

### 리뷰 목록
- 리뷰 작성: 평점(1~5점) 및 내용 작성
- 리뷰 수정 및 삭제: 작성자 본인만 수정 및 삭제 가능
- 리뷰 평가: 좋아요/싫어요 평가, 평가 수 표시

---

## 추가 사항
- 테스트 케이스 작성: 팀 회의로 상의
- 문서화: 팀 회의로 상의
- 보안: 팀 회의로 상의

---

## 기술 스택

### 프론트엔드
- React
- TypeScript
- Styled-Components
- React-Router
- Redux Toolkit
- RTK Query
- Eslint & Prettier
- Vite

### 백엔드
- Java (예정)
- Spring Boot (예정)

---

## 컴포넌트별 기능 설명
- `Header.tsx`: 상단 네비게이션 바, 로그인 상태 표시, 주요 페이지 링크 제공
- `Footer.tsx`: 하단 정보 표시, 회사 정보 및 소셜 미디어 링크 제공
- `BookCard.tsx`: 도서 카드 컴포넌트, 도서 제목, 저자, 평점 등 간단한 정보 표시
- `SearchBar.tsx`: 도서 검색 기능, 입력 필드 및 검색 버튼 포함
- `CategoryFilter.tsx`: 도서 카테고리 필터링 기능, 선택된 카테고리에 따라 도서 목록 갱신
- `LatestReviews.tsx`: 최신 리뷰 섹션, 슬라이드 형식으로 최근 리뷰 표시
- `PopularBooks.tsx`: 인기 도서 섹션, 슬라이드 형식으로 인기 도서 표시
- `Notifications.tsx`: 알림 모달 컴포넌트, 도서 추가, 리뷰에 대한 좋아요/댓글 알림 표시
- `Home.tsx`: 메인 홈 페이지 컴포넌트, 최신 리뷰 섹션, 인기 도서 섹션, 검색 바, 카테고리 필터 포함
- `BookDetail.tsx`: 도서 상세 페이지 컴포넌트, 도서 정보, 리뷰 리스트, 리뷰 작성 폼 포함
- `Login.tsx`: 로그인 페이지 컴포넌트, 이메일과 비밀번호로 로그인, 소셜 로그인 버튼 포함
- `Signup.tsx`: 회원가입 페이지 컴포넌트, 이메일, 비밀번호, 닉네임 입력 폼 및 유효성 검사 포함
- `Profile.tsx`: 프로필 페이지 컴포넌트, 사용자 정보 보기 및 수정 기능 포함
- `ReviewManagement.tsx`: 리뷰 작성 및 관리 페이지 컴포넌트, 작성한 리뷰 목록, 리뷰 수정 및 삭제 기능 포함
- `BookManagement.tsx`: 도서 관리 페이지 컴포넌트, 도서 추가, 수정, 삭제 기능 포함
- `Favorites.tsx`: 즐겨찾기 페이지 컴포넌트, 즐겨찾기에 추가한 도서 및 리뷰 목록 표시
- `LanguageSettings.tsx`: 다국어 지원 설정 페이지 컴포넌트, 사용자 인터페이스 언어 설정 기능 포함
- `store.ts`: Redux 스토어 설정 및 전역 상태 관리
- `GlobalStyle.ts`: 글로벌 스타일 정의 및 스타일링
- `api.ts`: API 호출 유틸리티 함수 정의

---

## 프로젝트 예상 구조

```plaintext
/src
  /components
    Header.tsx
    Footer.tsx
    BookCard.tsx
    SearchBar.tsx
    CategoryFilter.tsx
    LatestReviews.tsx
    PopularBooks.tsx
    Notifications.tsx
  /features
    /books
      booksSlice.ts
    /reviews
      reviewsSlice.ts
  /pages
    Home.tsx
    BookDetail.tsx
    BookList.tsx
    Login.tsx
    Signup.tsx
    Profile.tsx
    ReviewManagement.tsx
    BookManagement.tsx
    Favorites.tsx
    LanguageSettings.tsx
  /app
    store.ts
  /styles
    GlobalStyle.ts
  /utils
    api.ts
  index.tsx
  App.tsx

  ---
  

  