# UNIFY-UNITY
## 서비스 소개
반복되는 일회성 상담, 핵심 내용을 파악하기 어려운 상담 서비스는 그만! 쉽게 질문하고 쉽게 파악하자. U+ 종합 상담 요약 서비스 'UNITY'입니다.

## 디렉토리 구조
### 백엔드
```
┣ domain: 하위에 각 도메인 폴더를 만들고 밑으로 해당 사항 작성
│  ┣ controller: 서비스 요청을 받는 부분
│  ┣ facade: (선택) 여러 서비스가 모여 로직이 복잡해지면 분리
│  ┣ service: 비지니스 로직 부분
│  ┣ repository: DB 접근
│  ┣ entity: Table과 대응하는 data class
│  ┣ dto: 전달용 data class
│  ┣ exception: 예외 모음
│  ┣ security: 보안, 통신 configuration들
│  ┗ application.java
┗ global
   ┣ config: 
   ┣ exception: 글로벌 예외 모음
   ┣ response: 글로벌 응답 양식
   ┣ security: 보안/JWT 토큰 등
   ┗ util: 쿠키 등 utility 관련
```
### 프론트엔드
```
src/
├─ app/                         # ✅ Routing / Page Layer
│  ├─ layout.tsx
│  ├─ page.tsx
│  ├─ products/
│  │  ├─ page.tsx               # 페이지 진입점 (조합만)
│  │  ├─ _components/            # ❗ products 페이지만 쓰는 UI
│  │  │  ├─ ProductList.tsx
│  │  │  ├─ ProductFilter.tsx
│  │  │  └─ ProductPagination.tsx
│  │  ├─ _hooks/                 # ❗ products 페이지 orchestration
│  │  │  └─ useProductsPage.ts
│  │  └─ [id]/
│  │     ├─ page.tsx
│  │     ├─ _components/
│  │     │  └─ ProductDetailSection.tsx
│  │     └─ _hooks/
│  │        └─ useProductDetailPage.ts
│  └─ cart/
│     ├─ page.tsx
│     ├─ _components/
│     └─ _hooks/
├─ components/                  # ✅ 공통 UI Layer
│  ├─ ui/                        # 완전 재사용 (도메인 무관)
│  │  ├─ button/
│  │  │  └─ Button.tsx
│  │  └─ modal/
│  │     └─ Modal.tsx
│  ├─ product/                   # 도메인 UI (재사용 가능)
│  │  └─ product-card/
│  │     └─ ProductCard.tsx
│  └─ layout/
│     ├─ Header.tsx
│     └─ Footer.tsx
├─ services/                    # ⭐ 서버 상태의 중심
│  ├─ api/
│  │  ├─ client.ts               # fetch/axios instance
│  │  └─ interceptors.ts
│  └─ product/
│     ├─ productApi.client.ts    # 실제 API 호출
│     ├─ productApi.server.ts
│     ├─ queries.ts              # ✅ queryOptions / queryKey 정의
│     └─ index.ts
├─ hooks/                       # UI 로직 전용
│  ├─ ui/
│  │  ├─ useModal.ts
│  │  └─ useToast.ts
│  └─ auth/
│     └─ useAuth.ts
├─ store/                       # 전역 클라이언트 상태
│  ├─ slices/
│  │  ├─ uiSlice.ts
│  │  └─ cartSlice.ts
│  └─ store.ts
├─ types/                       # 타입 정의
│  ├─ common/
│  ├─ product/
│  └─ auth/
├─ utils/                       # 순수 함수
│  ├─ common/
│  └─ product/
├─ providers/                   # 전역 Provider
│  ├─ QueryProvider.tsx
│  └─ AuthProvider.tsx
├─ styles/
│  └─ globals.css
├─ assets/
│  ├─ images/
│  ├─ icons/
│  └─ fonts/
└─ public/
   └─ favicon.ico
```

## 실행 방법
### 백
1. intellij로 gardle build
2. application.java 실행
현재 로그인 일부 빼곤 구현되지 않음

### 프론트
1. yarn install
2. yarn run start로 실행
퍼블리싱 완료-임시 데이터들을 api로 교체할 필요 있음

## 각 기능 소개
### 온보딩 및 로그인

<img width="2169" height="995" alt="기능요약1" src="https://github.com/user-attachments/assets/fbdd3e00-db52-4cc2-80c9-6bb7c97bc6fb" />
- 서비스에 관해 소개
- 구글, 카카오, 네이버 로그인 세 가지를 모두 구현

### 홈 페이지

<img width="390" height="1160" alt="기능요약2" src="https://github.com/user-attachments/assets/2bd98737-a74e-4804-b2b1-911baaa4ef60" />
- 이벤트 확인
- U+ 사이트로 카테고리 연결
- 최근 상담 미리보기
- 추천 상품 미리보기

### 추천 페이지

<img width="390" height="1063" alt="기능요약3" src="https://github.com/user-attachments/assets/e9c05d4b-b2c9-4b3c-be57-bf9b629f96ca" />
- 카테고리 별 추천 상품 조회

### 상담 페이지

<img width="390" height="871" alt="기능요약4" src="https://github.com/user-attachments/assets/524d7309-5aa3-4115-b603-1a6a26e448a4" />
- 상담 카테고리 선택
- FAQ 자동응답
- 전화 상담
- 상담 종료 선택
- 요약 선택

### 요약 페이지

<img width="1033" height="1164" alt="기능요약5" src="https://github.com/user-attachments/assets/2d1a4809-3aad-46ad-bab0-3ccc513461f4" />
- 요약 리스트 조회
- 요약 리스트 정렬
- 상세 요약 확인
- 연관 상품 추천
- 매장 찾기

### 마이페이지

<img width="390" height="825" alt="기능요약6" src="https://github.com/user-attachments/assets/d9f02ded-9549-4590-8cbc-334958c5611a" />
- 프로필 조회
- 북마크한 상담 조회
- 테마 설정
- 언어 설정
- 약관 조회
- 도움말
- 로그아웃
- 회원 탈퇴
