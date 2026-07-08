# 헤드폰 랜딩 페이지 구현 계획 (Headphone Landing Page Implementation Plan)

PRD와 TRD 문서를 바탕으로 Svelte 기반의 반응형 단일 페이지 애플리케이션(SPA) 랜딩 페이지를 구축합니다.

## User Review Required

> [!IMPORTANT]  
> - 제공될 디자인 에셋(헤드폰 이미지 등)이 현재 존재하지 않아, 개발 진행 시 AI 이미지 생성 도구를 활용하여 임시 고화질 이미지를 생성하여 적용할 예정입니다. 괜찮으신가요?
> - 패키지 매니저는 `npm`을 기본으로 사용하여 프로젝트를 초기화하겠습니다.

## Open Questions

> [!NOTE]  
> - 제품명, 가격, 스펙 등 구체적인 데이터가 PRD/TRD에 명시되어 있지 않습니다. 임의의 프리미엄 헤드폰 데이터(예: "Aura Pro", 액티브 노이즈 캔슬링, 30시간 배터리, 399,000원 등)를 구성하여 진행해도 될까요?

## Proposed Changes

프로젝트 초기화 및 Tailwind CSS 설정 후 아래 구조에 맞게 컴포넌트를 개발합니다.

### 1. 프로젝트 초기화 및 환경 설정

#### [NEW] `package.json`
Vite와 Svelte 최신 버전을 템플릿으로 사용하여 프로젝트를 초기화하고 Tailwind CSS 관련 의존성을 추가합니다.

#### [NEW] `tailwind.config.js` / `postcss.config.js`
Tailwind CSS 설정 파일을 생성하고 Svelte 파일들을 템플릿 경로로 지정합니다.

#### [NEW] `src/app.css` (또는 `index.css`)
Tailwind 지시어(`@tailwind base;` 등)와 부드러운 스크롤(`html { scroll-behavior: smooth; }`)을 위한 글로벌 CSS를 적용합니다.

---

### 2. 컴포넌트 및 데이터 구성

#### [NEW] `src/data/productData.js`
제품 명칭, 설명, 스펙 리스트, 가격 등의 제품 상세 정보를 담은 데이터를 객체 형태로 구성합니다.

#### [NEW] `src/components/Header.svelte`
Sticky 포지션과 반투명 배경(`backdrop-blur`)을 적용한 네비게이션 바 컴포넌트입니다. About 및 Product 섹션으로 이동하는 앵커 링크를 포함합니다.

#### [NEW] `src/components/About.svelte`
브랜드 철학과 고화질 배경 이미지가 들어가는 섹션입니다. 앵커 링크 이동 시 헤더에 가려지지 않도록 `scroll-mt-20` 속성을 적용합니다.

#### [NEW] `src/components/Product.svelte`
제품 이미지와 `productData.js`의 데이터를 활용해 제품의 특징과 스펙을 보여주는 섹션입니다. 모바일에서는 1열, 데스크톱에서는 2열(`lg:grid-cols-2`)의 반응형 그리드로 구현하며 CTA 버튼을 포함합니다.

#### [NEW] `src/components/Footer.svelte`
회사 기본 정보와 카피라이트 텍스트가 포함된 하단 컴포넌트입니다.

---

### 3. 루트 컴포넌트 조립

#### [MODIFY] `src/App.svelte`
생성된 Header, About, Product, Footer 컴포넌트를 불러와 조립하고 메인 레이아웃(`min-h-screen`, `flex-col`, `bg-stone-50`)을 설정합니다.

## Verification Plan

### Automated Tests
- `npm run dev` 명령어를 통해 로컬 개발 서버를 실행하고 빌드 에러가 없는지 확인합니다.

### Manual Verification
- 브라우저를 통해 네비게이션 클릭 시 스무스 스크롤이 정상적으로 동작하는지 확인합니다.
- 모바일 및 데스크톱 뷰포트에서 레이아웃(특히 Product 섹션의 그리드)이 의도대로 변경되는지 확인합니다.
