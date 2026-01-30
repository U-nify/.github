
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
├─ app/                         
│  ├─ layout.tsx
│  ├─ page.tsx
│  ├─ products/
│  │  ├─ page.tsx             
│  │  ├─ _components/            
│  │  │  ├─ ProductList.tsx
│  │  │  ├─ ProductFilter.tsx
│  │  │  └─ ProductPagination.tsx
│  │  ├─ _hooks/                 
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
├─ components/                  
│  ├─ ui/                   
│  │  ├─ button/
│  │  │  └─ Button.tsx
│  │  └─ modal/
│  │     └─ Modal.tsx
│  ├─ product/                   
│  │  └─ product-card/
│  │     └─ ProductCard.tsx
│  └─ layout/
│     ├─ Header.tsx
│     └─ Footer.tsx
├─ services/                    
│  ├─ api/
│  │  ├─ client.ts              
│  │  └─ interceptors.ts
│  └─ product/
│     ├─ productApi.client.ts    
│     ├─ productApi.server.ts
│     ├─ queries.ts              
│     └─ index.ts
├─ hooks/                    
│  ├─ ui/
│  │  ├─ useModal.ts
│  │  └─ useToast.ts
│  └─ auth/
│     └─ useAuth.ts
├─ store/                   
│  ├─ slices/
│  │  ├─ uiSlice.ts
│  │  └─ cartSlice.ts
│  └─ store.ts
├─ types/                       
│  ├─ common/
│  ├─ product/
│  └─ auth/
├─ utils/                     
│  ├─ common/
│  └─ product/
├─ providers/                   
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

<img width="872" height="1766" alt="image" src="https://github.com/user-attachments/assets/0c2d8f20-0f29-417b-8818-1527317101d6" />
<img width="872" height="1766" alt="image" src="https://github.com/user-attachments/assets/31528987-9ee9-4249-a129-40777d4bd089" />

- 서비스에 관해 소개
- 구글, 카카오, 네이버 로그인 세 가지를 모두 구현

### 홈 페이지

<img width="802" height="1628" alt="image" src="https://github.com/user-attachments/assets/9eb57425-969e-4176-93ab-210f1759eea1" />
<img width="802" height="1628" alt="image" src="https://github.com/user-attachments/assets/4db6e425-2018-4789-b292-0f5eaf14f3bf" />

- 이벤트 확인
- U+ 사이트로 카테고리 연결
- 최근 상담 미리보기
- 추천 상품 미리보기

### 추천 페이지

<img width="802" height="1628" alt="image" src="https://github.com/user-attachments/assets/c7a7fa74-9fe6-4d53-b656-f47a53b620ee" />
<img width="802" height="1628" alt="image" src="https://github.com/user-attachments/assets/120a3f5d-9533-409a-9dd8-768f6d70fb3a" />

- 카테고리 별 추천 상품 조회

### 상담 페이지

<img width="802" height="1628" alt="image" src="https://github.com/user-attachments/assets/37b2589a-96c9-4311-8aa2-fabb939ba039" />

- 상담 카테고리 선택
- FAQ 자동응답
- 전화 상담
- 상담 종료 선택
- 요약 선택

### 요약 페이지

<img width="802" height="1628" alt="image" src="https://github.com/user-attachments/assets/2ff33715-9d20-4d5d-bb7d-433983238254" />
<img width="802" height="1628" alt="image" src="https://github.com/user-attachments/assets/c17c22fc-5cb8-4a53-a493-cc81bde863ac" />

- 요약 리스트 조회
- 요약 리스트 정렬
- 상세 요약 확인
- 연관 상품 추천
- 매장 찾기

### 마이페이지

<img width="802" height="1628" alt="image" src="https://github.com/user-attachments/assets/ce6f9653-105d-422c-9fa4-4f4d8cd62e9e" />


- 프로필 조회
- 북마크한 상담 조회
- 테마 설정
- 언어 설정
- 약관 조회
- 도움말
- 로그아웃
- 회원 탈퇴
