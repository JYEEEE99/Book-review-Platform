# 📚 온라인 도서 리뷰 플랫폼 역할 분담

본 문서는 프로젝트 팀원들의 역할을 명확히 하기 위해 작성

---

## 역할 분담

### 프론트엔드 개발자 (3명)

#### 첫 번째 프론트엔드 개발자
- **구현해야 하는 페이지 및 컴포넌트**:
  - `Home.tsx`, `BookList.tsx`, `BookDetail.tsx`, `ErrorPage404.tsx`, `ErrorPage500.tsx`
  - `Header.tsx`, `Footer.tsx`, `BookCard.tsx`
- **상태 관리**: Redux Toolkit을 사용한 전역 상태 관리
- **컴포넌트별 기능**:
  - `Home.tsx`: 최신 리뷰 섹션, 인기 도서 섹션, 검색 바, 카테고리 필터, 도서 리스트
  - `BookList.tsx`: 카테고리 필터, 검색 바, 도서 리스트
  - `BookDetail.tsx`: 도서 정보, 리뷰 리스트, 리뷰 작성 폼
  - `Header.tsx`: 상단 네비게이션 바, 로그인 상태 표시, 주요 페이지 링크 제공
  - `ErrorPage404`: 404 Not Found, 사용자가 존재하지 않는 페이지를 요청했을 때 보여주는 페이지
  - `ErrorPage500.tsx`: 500 Internal Server Error, 서버에서 예기치 않은 오류가 발생했을 때 사용자에게 알리는 페이지
  - `Footer.tsx`: 하단 정보 표시, 회사 정보 및 소셜 미디어 링크 제공
  - `BookCard.tsx`: 도서 카드 컴포넌트, 도서 제목, 저자, 평점 등 간단한 정보 표시
- **개발 우선 순위**
 1. `Header.tsx` - 1일
 2. `Footer.tsx` - 1일
 3. `BookCard.tsx` - 2일
 4. `Home.tsx` - 2일
 5. `BookList.tsx`- 3일
 6. `BookDetail.tsx` - 3일
 7. `ErrorPage404.tsx` - 1일
 8. `ErrorPage500.tsx` - 1일


#### 두 번째 프론트엔드 개발자
- **구현해야 하는 페이지 및 컴포넌트**:
  - `ReviewManagement.tsx`, `Notifications.tsx`
  - `LatestReviews.tsx`, `PopularBooks.tsx`
- **알림 기능 구현**:
  - 사용자가 작성한 리뷰에 좋아요, 댓글 알림 UI, 새로운 도서 추가 알림
- **리뷰 작성 및 관리 페이지 구현**:
  - 리뷰 작성 폼 (평점 및 내용), 리뷰 수정 및 삭제 기능 (작성자 본인만)
- **타입 정의 및 코드 안정성 확보**
- **컴포넌트별 기능**:
  - `ReviewManagement.tsx`: 작성한 리뷰 목록, 리뷰 수정 및 삭제
  - `Notifications.tsx`: 도서 추가, 리뷰에 대한 좋아요/댓글 알림 표시
  - `LatestReviews.tsx`: 최신 리뷰 섹션, 슬라이드 형식으로 최근 리뷰 표시
  - `PopularBooks.tsx`: 인기 도서 섹션, 슬라이드 형식으로 인기 도서 표시
- **개발 우선 순위**
 1. ``ReviewManagement.tsx`` - 5일
 2. ``Notifications.tsx`` - 3일
 3. ``LatestReviews.tsx`` - 3일
 4. ``PopularBooks.tsx`` - 3일

#### 세 번째 프론트엔드 개발자
- **구현해야 하는 페이지 및 컴포넌트**:
  - `Signup.tsx`, `Login.tsx`, `Profile.tsx`, `Favorites.tsx`, `LanguageSettings.tsx` (후 순위)
  - `SearchBar.tsx`, `CategoryFilter.tsx`
- **Styled-Components를 사용한 전체적인 스타일링 및 컴포넌트별 스타일 정의**
- **반응형 디자인 구현**:
  - 모바일: 375px 미만
  - 태블릿: 768px 미만
  - 데스크탑: 1024px 이상
- **사용자 관리 관련 페이지 구현**:
  - 회원가입, 로그인, 소셜 로그인, 프로필 수정 등
- **여유가 있으면 다국어 지원 시도 (영어, 한국어)**
- **컴포넌트별 기능**:
  - `Signup.tsx`: 이메일, 비밀번호, 닉네임 입력 폼 및 유효성 검사 포함
  - `Login.tsx`: 이메일과 비밀번호로 로그인, 소셜 로그인 버튼 포함
  - `Profile.tsx`: 사용자 정보 보기 및 수정 기능 포함
  - `Favorites.tsx`: 즐겨찾기에 추가한 도서 및 리뷰 목록 표시
  - `SearchBar.tsx`: 도서 검색 기능, 입력 필드 및 검색 버튼 포함
  - `CategoryFilter.tsx`: 도서 카테고리 필터링 기능, 선택된 카테고리에 따라 도서 목록 갱신
  - `LanguageSettings.tsx`: 사용자 인터페이스 언어 설정 기능 포함 (후 순위)
**개발 우선 순위**
 1. ``SearchBar.tsx`` - 2일
 2. ``CategoryFilter.tsx`` - 2일
 3. ``Signup.tsx`` - 5일
 4. ``Login.tsx``- 3일
 5. ``Profile.tsx`` - 3일
 6. ``Favorites.tsx`` - 3일

## 먼저 개발 끝난 프론트엔드 개발자 
 ``LanguageSettings.tsx``


### 백엔드 개발자 (4명)

#### 백엔드 개발자 1
- 사용자 인증 및 권한 관리: 회원가입 API (이메일, 비밀번호, 닉네임 유효성 검사), 로그인 API, 사용자 관리 권한 로직(관리자, 일반 사용자)
- 사용자 프로필 API 구현: 사용자 정보 조회 API, 사용자 정보 수정 API (닉네임 및 프로필 수정)
- 소셜 로그인 API 구현: 구글, 페이스북 등

- **개발 우선 순위**
  - 회원가입 API - 5일
  - 로그인 API - 3일
  - 사용자 프로필 API - 3일
  - 소셜 로그인 API - 5일
  - 사용자 관리 권한 로직 - 5일

#### 백엔드 개발자 2
- 도서 정보 CRUD API 구현: 도서 목록 조회 API, 도서 상세 정보 조회 API, 
- 도서 카테고리 및 검색 기능 API 구현: 카테고리별 도서 목록 조회 API, 제목 & 저자 등으로 검색 기능

- **개발 우선 순위**
  - 도서 목록 조회 API - 5일
  - 도서 상세 정보 조회 API - 3일
  - 도서 카테고리 조회 API - 3일


#### 백엔드 개발자 3
- 리뷰 CRUD API 구현: 리뷰 작성 API 구현 (평점 및 내용), 리뷰 수정 및 삭제 API (작성자 본인만 수정 및 삭제 가능)
- 리뷰 평가 API 구현: 리뷰에 대한 좋아요/싫어요 평가 API
- 알림 API 구현: 사용자가 작성한 리뷰에 좋아요/댓글 알림 API, 새로운 도서 추가 알림 API

- **개발 우선 순위**
  - 리뷰 작성 API - 5일
  - 리뷰 수정 API - 3일
  - 리뷰 삭제 API - 3일
  - 리뷰 좋아요/싫어요 평가 API - 2일
  - 리뷰 좋아요/댓글 알림 API - 2일
  - 새로운 도서 추가 알림 API - 2일


#### 백엔드 개발자 4
- 데이터베이스 설계 및 관리: 사용자, 도서, 리뷰, 알림 등 주요 데이터베이스 테이블 설계, 데이터베이스 관리
- 관리자 API 구현: 도서 및 리뷰 관리 API(도서 추가 & 수정), 도서 삭제 API (관리자 권한 필요), 리뷰 삭제 API(모든 리뷰 삭제 가능)

- **개발 우선 순위**
  - 데이터베이스 설계 및 관리 - 죽을때 까지
  - 리뷰 삭제 API - 3일
  - 도서 추가 API - 3일
  - 도서 수정 API - 3일
  - 도서 삭제 API - 3일


#### 개발 여유가 있는 백엔드 개발자
- API 통합 및 테스트: 전체 API 통합 및 테스트

- **개발 기간**
  - API 통합 및 테스트 - 7일
