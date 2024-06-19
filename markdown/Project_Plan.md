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

### 404 Not Found 페이지 (ErrorPage404)
파일: `ErrorPage404.tsx`

#### 기능
- **페이지 제목 표시**: "404 - Page Not Found"라는 제목을 표시하여 사용자가 페이지를 찾을 수 없음을 알림
- **안내 메시지 표시**: 사용자가 요청한 페이지가 존재하지 않음을 알리는 간단한 설명 메시지 표시
- **홈페이지로 이동 링크 제공**: 사용자가 쉽게 홈페이지로 돌아갈 수 있도록 링크 제공

### Internal Server Error 페이지 (ErrorPage500)
파일: `ErrorPage500.tsx`

#### 기능
- **페이지 제목 표시**: "500 - Internal Server Error"라는 제목을 표시하여 서버 오류가 발생했음을 알림
- **안내 메시지 표시**: 서버에서 문제가 발생했음을 알리는 설명 메시지 표시
- **재시도 버튼 제공**: 사용자가 페이지를 다시 로드할 수 있도록 재시도 버튼 제공
- **홈페이지로 이동 링크 제공**: 사용자가 쉽게 홈페이지로 돌아갈 수 있도록 링크 제공

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
- Next.js
- TypeScript
- Styled-Components
- Redux
- React Query
- Eslint & Prettier
- RabbitMQ
- React Hook Form

**Next.js**
- 서버 사이드 랜더링(SSR) 및 정적 사이트 생성(SSG), Next.js는 SEO향상과 초기 로딩 시간을 줄여줌
- 파일 기반 라우팅
  - Next.js는 파일 구조를 기반으로 라우팅 하기 때문에 라우팅을 자동으로 설정해주어 라우팅 설정이 간편
  - 동적 경로 매개변수를 쉽게 설정할 수 있어 유연한 라우팅 가능
- SSR 및 SSG와 통합이 용이하여 SEO와 성능을 최적화
- 빠른 빌드와 배포: Next.js의 내장 빌드 도구는 최적화된 빌드와 배포를 지원

**Typescript**
- 타입 안정성: Typescript는 정적 타입을 통해 코드의 안정성, 가독성, 유지보수성을 높여줌
- 개발 생산성: 타입 정의를 통해 IDE의 자동 완성 기능을 강화해 개발 생산성 향상
- 버그 감소: 컴파일 타임에 오류를 발견해 런타임 버그를 줄여줌

**Styled-Components**
- CSS-in-JS: Javascript 파일 내에서 스타일을 정의하여 컴포넌트 기반 개발 가능
- 동적 스타일링: props를 기반으로 덩적으로 스타일을 변경할 수 있음
- 자동 스코프: 컴포넌트의 스타일이 자동으로 스코프 적용되어 CSS클래스의 중복을 방지

**Redux와 React Query**
- 클라이언트 상태와 서버 상태의 분리
  - 클라이언트 상태는 Redux를 사용하여 관리, 클라이언트 상태는 주로 UI상태, 사용자 입력 등 애플리케이션 전반에 공유되는 상태
  - 서버 상태는 React Query를 사용하여 관리, 서버 상태는 주로 서버에서 가져온 데이터로 데이터 페칭, 캐싱, 동기화 등
- 비동기 로직관리
  - Redux는 복잡한 비동기 로직(API호출, 트랜잭션 관리 등)을 미들웨어(Redux Thunk, Redux saga)를 통해 처리할 수 있다.
  - React Query는 간단한 비동기 데이터 페칭 로직을 쉽게 관리할 수 있고 데이터의 캐싱, 동기화, 백그라운드 업데이트 등을 자동으로 처리
- 기능적인 역할 분담
  - Redux
    - UI 상태 관리
    - 사용자 입력 관리
    - 비지니스 로직(인증 상태, 알림 상태)
  - React Query
    - 데이터 페칭, 데이터 캐싱, 데이터 동기화
    - 에러 핸들링(API 호출 에러 처리 - 데이터 페칭중 발생하는 에러를 자동으로 처리)
- React Query 사용 이유
  - Redux를 사용하기 위해선 edux의 기본 원칙 준수를 위한 다양한 Boilerplate 코드들이 필요하다.
  - Redux를 사용한 비동기 데이터 관리 코드와 React-Query를 사용한 비동기 데이터 관리 코드의 분량이 크게 차이난다.
  - 코드의 분량이 적어진다는 것은 개발자에게 불필요한 작업이 필요 없어지기도 하지만, 소스코드의 복잡도를 낮추어 유지보수성을 높이고 작업간에 발생할 수 있는 에러를 사전에 더 잘막을 수 있다

**Eslint & Prettier** 
- Eslint는 코드 품질 유지 및 일관성 유지
- Prettier는 코드 포멧팅을 자동으로 처리하여 일관된 코드 스타일을 유지
- 코드 스타일 규칙을 강제하여 팀 전체의 코드 품질을 유지


**RabbitMQ** 
- 백그라운드 작업(알림처리, 이메일 전송)을 비동기적으로 처리해 애플리케이션의 응답성 향상

**React Hook Form**
- React Hook Form은 비제어 컴포넌트를 사용해 폼 입력을 처리하기 때문에 리렌더링 횟수가 줄어듬 이는 곧 성능 향상과 직결
- 간단한 API로 관리할 수 있으며 기본적인 폼 상태관리, 유효성 검사를 쉽게 설정 가능 (다양한 유효성 검사 규칙을 제공)
- Typescript와 잘 호환되며 폼 빌드와 유효성 검사 규칙을 타입으로 정의 가능

### 백엔드
- Java (예정)
- Spring Boot (예정)

---

## 예상 문제점 및 고려 사항
#### 기능 구현의 세부 사항
- 리뷰 작성: 글자 수 제한, 비속어 필터링, 이미지 업로드 등 세부 요구사항이 추가될 수 있음
- 검색 기능: 검색 조건(제목, 저자, 출판사 등)의 다양성, 검색 결과 정렬 기준(평점순, 최신순)등 세부사항 추가 될 수 있음
- 카테고리 관리: 도서의 카테고리 추가, 수정, 복수 선택 등 세부사항 추가 될 수 있음
- 페이지네이션: 도서 목록 및 리뷰 목록의 페이지네이션 구현 방법에 따라 성능 최적화 필요
- 알림 설정: 사용자가 알림을 수신할 조건(리뷰 좋아요, 댓글, 새로운 도서 추가)을 세부적으로 설정, 알림 끄기 등 세부사항 추가 될 수 있음
- 프로필 관리: 닉네임 변경 시 중복 검사, 프로필 사진 업로드 크기 및 형식 제한
- 즐겨찾기 관리: 즐겨찾기 목록의 정렬, 필터링 기능 등 세부사항 추가 될 수 있음

#### OAuth 구현
- 소셜 로그인 후 사용자 데이터 처리, 세션 관리, 보안 이슈 등 여러가지 복잡성이 있어 구현 도중에 변경될 수 있음

#### 상태 관리
- Redux 및 React Query를 사용할 때 초기 상태 정의, 비동기 액션 처리, 에러 핸들링에서 변경이 필요할 수 있음

#### 보안 및 인증
- JWT 토큰 관리, 토큰 갱신, 사용자 인증 상태 유지 등 보안 관련 부분에서 많은 수정이 필요할 수 있음 


---

## 프로젝트 예상 구조 및 각 폴더의 역할

### components폴더: 재사용 가능한 UI 컴포넌트들을 저장
- **각 컴포넌트 폴더**
  - ``tsx`` 파일: 컴포넌트의 React 코드
  - ``styles.ts`` 파일: 해당 컴포넌트의 스타일 정의 (styled-components 사용)


### features폴더: 특정 기능과 관련된 상태 관리를 포함한 로직을 관리
- **auth**: 사용자 인증 관련 상태 관리 ``authSlice.ts``
- **books**: 도서 관련 상태 관리 ``booksSlice.ts``
- **reviews**: 리뷰 관련 상태 관리 ``reviewsSlice.ts`
- **notifications**: 알림 관련 상태 관리 ``notificationsSlice.ts``

### api폴더: 각 기능별 API 호출을 관리

#### auth폴더
  - ``signupApi.ts``: 회원가입 API
  - ``loginApi.ts``: 로그인 API
  - ``profileApi.ts``: 프로필 조회 및 수정 API
  - ``socialLoginApi.ts``: 소셜 로그인 API

#### books폴더
  - ``deleteBookApi.ts``: 도서 삭제 API
  - ``fetchBooksApi.ts``: 도서 목록 조회 API
  - ``fetchBookDetailApi.ts``: 도서 상세 정보 조회 API
  - ``addBookApi.ts``: 도서 추가 API
  - ``updateBookApi.ts``: 도서 수정 API

#### reviews폴더
  - ``addReviewApi.ts``: 리뷰 작성 API
  - ``updateReviewApi.ts``: 리뷰 수정 API
  - ``deleteReviewApi.ts``: 리뷰 삭제 API
  - ``likeReviewApi.ts``: 리뷰 좋아요 API
  - ``dislikeReviewApi.ts``: 리뷰 싫어요 API

#### notifications폴더
  - ``fetchNotificationsApi.ts``: 알림 조회 API
  - ``addNotificationApi.ts``: 알림 추가 API
  
  
## pages폴더: 라우팅되는 주요 페이지들을 저장
  - ``Home.tsx``: 홈 페이지, 최신 리뷰 섹션, 인기 도서 섹션, 검색 바, 카테고리 필터, 도서 리스트 포함
  - ``BookList.tsx`: 도서 목록 페이지, 카테고리 필터, 검색 바, 도서 리스트 포함
  - ``BookDetail.tsx`: 도서 상세 정보 페이지, 도서 정보, 리뷰 리스트, 리뷰 작성 폼 포함
  - ``Signup.tsx``: 회원가입 페이지, 이메일, 비밀번호, 닉네임 입력 폼 및 유효성 검사 포함
  - ``Login.tsx``: 로그인 페이지, 이메일과 비밀번호로 로그인, 소셜 로그인 버튼 포함
  - ``Profile.tsx``: 프로필 페이지, 사용자 정보 보기 및 수정 기능 포함
  - ``Favorites.tsx``: 즐겨찾기 페이지, 즐겨찾기에 추가한 도서 및 리뷰 목록 표시
  - ``BookManagement.tsx``: 도서 추가 및 수정 페이지 (관리자 전용)
  - ``ErrorPage404.tsx``: 404 Not Found 페이지, 사용자가 존재하지 않는 페이지를 요청했을 때 보여주는 페이지
  - ``ErrorPage500.tsx``: 500 Internal Server Error 페이지, 서버에서 예기치 않은 오류가 발생했을 때 사용자에게 알리는 페이지

## 추가 폴더 및 파일

``store.ts``: Redux 스토어 설정 및 전역 상태 관리

#### styles 폴더: 전역 스타일 정의
  - ``GlobalStyle.ts``: 전역 스타일 파일

#### utils 폴더: 다양한 유틸리티 함수 및 설정 파일
- ``apiClient.ts``: Axios 인스턴스나 Fetch API 설정
- ``authHelpers.ts``: 인증 관련 유틸리티 함수
- ``formatDate.ts``: 날짜 형식 변환 유틸리티 함수

#### middlewares 폴더: 전역 미들웨어 파일
- ``errorMiddleware.ts``: 전역 에러 처리 미들웨어
- ``authMiddleware.ts``: 인증 미들웨어

#### services 폴더: 비즈니스 로직을 처리하는 서비스 파일
- ``authService.ts``: 사용자 인증 관련 서비스 로직
- ``bookService.ts``: 도서 관리 관련 서비스 로직
- ``reviewService.ts``: 리뷰 관리 관련 서비스 로직
- ``notificationService.ts``: 알림 관리 관련 서비스 로직 (RabbitMQ 사용)

#### config 폴더: 설정 파일
- ``rabbitmqConfig.ts``: RabbitMQ 설정 파일
- ``oauthConfig.ts``: OAuth 설정 파일
- ``apiConfig.ts``: API 엔드포인트 설정 파일

#### types 폴더: 타입 정의 파일
- ``authTypes.ts``: 인증 관련 타입 정의
- ``bookTypes.ts``: 도서 관련 타입 정의
- ``reviewTypes.ts``: 리뷰 관련 타입 정의
- ``notificationTypes.ts``: 알림 관련 타입 정의



## 프로젝트 폴더 예상 구조
```plaintext
/src
  /components
    /Header
      Header.tsx
      Header.styles.ts
    /Footer
      Footer.tsx
      Footer.styles.ts
    /BookCard
      BookCard.tsx
      BookCard.styles.ts
    /SearchBar
      SearchBar.tsx
      SearchBar.styles.ts
    /CategoryFilter
      CategoryFilter.tsx
      CategoryFilter.styles.ts
    /LatestReviews
      LatestReviews.tsx
      LatestReviews.styles.ts
    /PopularBooks
      PopularBooks.tsx
      PopularBooks.styles.ts
    /Notifications
      Notifications.tsx
      Notifications.styles.ts
    /BookListItem
      BookListItem.tsx
      BookListItem.styles.ts
  /features
    /auth
      authSlice.ts
    /books
      booksSlice.ts
    /reviews
      reviewsSlice.ts
    /notifications
      notificationsSlice.ts
  /api
    /auth
      signupApi.ts
      loginApi.ts
      profileApi.ts
      socialLoginApi.ts
    /books
      fetchBooksApi.ts
      fetchBookDetailApi.ts
      addBookApi.ts
      updateBookApi.ts
      deleteBookApi.ts
    /reviews
      addReviewApi.ts
      updateReviewApi.ts
      deleteReviewApi.ts
      likeReviewApi.ts
      dislikeReviewApi.ts
    /notifications
      fetchNotificationsApi.ts
      addNotificationApi.ts
  /pages
    Home.tsx
    BookList.tsx
    BookDetail.tsx
    Signup.tsx
    Login.tsx
    Profile.tsx
    Favorites.tsx
    BookManagement.tsx
    ErrorPage404.tsx
    ErrorPage500.tsx
  /app
    store.ts
  /styles
    GlobalStyle.ts
  /utils
    apiClient.ts     // Axios 인스턴스나 Fetch API 설정
    authHelpers.ts   // 인증 관련 유틸리티 함수
    formatDate.ts    // 날짜 형식 변환 유틸리티 함수
  /middlewares
    errorMiddleware.ts    // 전역 에러 처리 미들웨어
    authMiddleware.ts     // 인증 미들웨어
  /services
    authService.ts    // 사용자 인증 관련 서비스 로직
    bookService.ts    // 도서 관리 관련 서비스 로직
    reviewService.ts  // 리뷰 관리 관련 서비스 로직
    notificationService.ts  // 알림 관리 관련 서비스 로직 (RabbitMQ 사용)
  /config
    rabbitmqConfig.ts  // RabbitMQ 설정 파일
    oauthConfig.ts     // OAuth 설정 파일
    apiConfig.ts       // API 엔드포인트 설정 파일
  /types
    authTypes.ts   // 인증 관련 타입 정의
    bookTypes.ts   // 도서 관련 타입 정의
    reviewTypes.ts // 리뷰 관련 타입 정의
    notificationTypes.ts // 알림 관련 타입 정의
  index.tsx
  App.tsx




  