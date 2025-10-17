# 프로젝트 구조 상세 가이드

## 📁 전체 디렉토리 구조

```
inskinlab-homepage/
├── src/                        # 소스 코드
│   ├── components/             # UI 컴포넌트
│   │   ├── ui/                # 기본 UI 요소
│   │   │   ├── button.astro
│   │   │   ├── link.astro
│   │   │   └── icons/
│   │   ├── navbar/            # 네비게이션 컴포넌트
│   │   │   ├── navbar.astro
│   │   │   └── dropdown.astro
│   │   ├── container.astro
│   │   ├── footer.astro
│   │   ├── sectionhead.astro
│   │   ├── features.astro
│   │   └── contactform.astro
│   ├── layouts/               # 페이지 레이아웃
│   │   ├── Layout.astro       # 기본 레이아웃
│   │   └── BlogLayout.astro   # 블로그 레이아웃
│   ├── pages/                 # 페이지 (파일 기반 라우팅)
│   │   ├── index.astro        # 홈페이지
│   │   ├── about.astro
│   │   ├── team.astro
│   │   ├── contact.astro
│   │   ├── app.astro
│   │   ├── terms.astro
│   │   ├── privacy.astro
│   │   └── 404.astro
│   ├── content/               # Content Collections
│   │   ├── config.ts          # 컬렉션 스키마
│   │   ├── blog/             # 블로그 포스트 (MDX)
│   │   └── team/             # 팀 멤버 (Markdown)
│   ├── assets/                # 이미지 및 미디어
│   ├── styles/                # 글로벌 스타일
│   │   └── global.css
│   ├── utils/                 # 유틸리티 함수
│   │   └── all.js
│   └── env.d.ts              # TypeScript 환경 선언
├── public/                    # 정적 파일
│   ├── .well-known/          # 웹 설정
│   │   └── assetlinks.json   # Android App Links
│   └── favicon.svg
├── claudedocs/               # 프로젝트 문서 (자동 생성)
│   ├── PROJECT_INDEX.md
│   ├── STRUCTURE.md
│   ├── COMPONENTS.md
│   ├── DEVELOPMENT.md
│   ├── CONTENT.md
│   └── STYLING.md
├── astro.config.mjs          # Astro 설정
├── tsconfig.json             # TypeScript 설정
├── package.json              # NPM 패키지 설정
├── pnpm-lock.yaml            # pnpm 잠금 파일
├── CLAUDE.md                 # Claude Code 가이드
├── CHANGELOG.md              # 변경 이력
└── README.md                 # 프로젝트 README
```

---

## 🗂️ 디렉토리별 상세 설명

### `/src/components/` - UI 컴포넌트

#### 기능별 분류
| 디렉토리/파일 | 역할 | 사용 위치 |
|--------------|------|-----------|
| `ui/` | 기본 UI 요소 (버튼, 링크, 아이콘) | 전역 |
| `navbar/` | 네비게이션 컴포넌트 | Layout.astro |
| `container.astro` | 레이아웃 컨테이너 | 대부분의 페이지 |
| `footer.astro` | 푸터 | Layout.astro |
| `sectionhead.astro` | 섹션 헤더 | index.astro, about.astro |
| `features.astro` | 기능 소개 | about.astro |
| `contactform.astro` | 문의 폼 | contact.astro |

#### 컴포넌트 조직 원칙
- **기능별 분류**: 관련 컴포넌트는 서브디렉토리로 그룹화 (예: `navbar/`)
- **재사용성**: 모든 컴포넌트는 Props를 통해 재사용 가능하도록 설계
- **명명 규칙**: kebab-case 파일명 (예: `contact-form.astro`)

**참고**: [컴포넌트 가이드](./COMPONENTS.md)

---

### `/src/pages/` - 페이지 라우팅

#### 파일 기반 라우팅
Astro는 `/src/pages/` 디렉토리의 파일 구조를 자동으로 URL 경로로 매핑합니다.

| 파일 경로 | URL 경로 | 설명 |
|----------|---------|------|
| `index.astro` | `/` | 메인 홈페이지 |
| `about.astro` | `/about` | 회사 소개 |
| `team.astro` | `/team` | 팀 소개 |
| `contact.astro` | `/contact` | 문의하기 |
| `app.astro` | `/app` | 앱 다운로드/딥링크 |
| `terms.astro` | `/terms` | 이용약관 |
| `privacy.astro` | `/privacy` | 개인정보처리방침 |
| `404.astro` | `/404` | 404 에러 페이지 |

#### 페이지 구조 패턴
모든 페이지는 다음 구조를 따릅니다:

```astro
---
// Frontmatter (TypeScript)
import Layout from "@/layouts/Layout.astro";
// 기타 import...

// 페이지 로직
---

<!-- HTML 템플릿 -->
<Layout title="페이지 제목">
  <!-- 페이지 콘텐츠 -->
</Layout>
```

---

### `/src/layouts/` - 레이아웃 템플릿

#### `Layout.astro` (기본 레이아웃)
**역할**: 모든 페이지의 공통 구조 제공

**포함 요소**:
- SEO 메타 태그 (astro-seo)
- Google Analytics 스크립트
- 네비게이션 바 (Navbar)
- 푸터 (Footer)
- 글로벌 스타일

**Props**:
```typescript
interface Props {
  title: string;  // 페이지 제목
}
```

**사용 예시**:
```astro
<Layout title="회사 소개">
  <!-- 페이지 콘텐츠 -->
</Layout>
```

#### `BlogLayout.astro` (블로그 레이아웃)
**역할**: 블로그 포스트 전용 레이아웃

**포함 요소**:
- 기본 레이아웃 상속
- 블로그 메타데이터 (작성일, 저자, 카테고리)
- 대표 이미지
- 목차 (선택적)

---

### `/src/content/` - Content Collections

#### `config.ts` (컬렉션 스키마)
Zod 스키마를 사용하여 콘텐츠 타입 정의:

```typescript
// blog 컬렉션 스키마
{
  draft: boolean,
  title: string,
  snippet: string,
  image: { src: string, alt: string },
  publishDate: Date,
  author: string,
  category: string,
  tags: string[]
}

// team 컬렉션 스키마
{
  draft: boolean,
  name: string,
  title: string,
  description?: string,
  avatar: { src: string, alt: string },
  publishDate: Date,
  order: number
}
```

#### `blog/` 디렉토리
- **형식**: MDX (Markdown + JSX)
- **용도**: 블로그 포스트, 뉴스, 업데이트
- **현재 상태**: 비어있음 (향후 추가 예정)

#### `team/` 디렉토리
- **형식**: Markdown
- **용도**: 팀 멤버 프로필
- **현재 파일**:
  - `moonsuk-jung.md` - 정문석 (CEO)
  - `sukkyu-sun.md` - 선석규 (CTO)
  - `youngjae-heo.md` - 허영재 (Designer)
  - `sooick-cho.md` - 조수익 (Developer)

**참고**: [콘텐츠 관리 가이드](./CONTENT.md)

---

### `/src/assets/` - 이미지 및 미디어

#### 이미지 최적화
Astro의 `Image` 컴포넌트와 Sharp를 사용한 자동 최적화:

```astro
import { Image } from "astro:assets";
import productImage from "@/assets/product-1.png";

<Image src={productImage} alt="설명" />
```

#### 장점
- 자동 포맷 변환 (WebP, AVIF)
- 반응형 이미지 생성
- 레이지 로딩
- 빌드 시간 최적화

---

### `/src/utils/` - 유틸리티 함수

#### `all.js`
**현재 함수**:
```javascript
// 날짜 포맷팅 (en-us 형식)
export const getFormattedDate = (date) =>
  date ? new Date(date).toLocaleDateString("en-us", {
    year: "numeric",
    month: "short",
    day: "numeric",
  }) : "";
```

**사용 예시**:
```astro
---
import { getFormattedDate } from "@/utils/all.js";

const formattedDate = getFormattedDate("2025-01-17");
// 출력: "Jan 17, 2025"
---
```

---

### `/public/` - 정적 파일

#### 정적 자산 처리
`/public/` 디렉토리의 파일은 빌드 시 루트로 복사됩니다.

**현재 파일**:
- `favicon.svg` - 파비콘
- `.well-known/assetlinks.json` - Android App Links 설정

**접근 방법**:
```html
<!-- /public/favicon.svg → /favicon.svg -->
<link rel="icon" type="image/svg+xml" href="/favicon.svg" />
```

---

### `/claudedocs/` - 프로젝트 문서

#### 문서 종류
- `PROJECT_INDEX.md` - 프로젝트 전체 개요 및 인덱스
- `STRUCTURE.md` - 프로젝트 구조 상세 가이드 (현재 문서)
- `COMPONENTS.md` - 컴포넌트 사용 가이드
- `DEVELOPMENT.md` - 개발 워크플로우
- `CONTENT.md` - 콘텐츠 관리 방법
- `STYLING.md` - 스타일링 규칙

---

## 🔧 설정 파일

### `astro.config.mjs`
Astro 프레임워크 설정:

```javascript
{
  site: "https://astroship.web3templates.com",  // 사이트 URL (변경 필요)
  integrations: [mdx(), sitemap(), icon()],     // 통합 플러그인
  vite: { plugins: [tailwindcss()] },          // Vite 플러그인
  output: "static",                            // 정적 빌드
  base: "/"                                    // 기본 경로
}
```

**주의**: `site` URL이 `inskinlab.com`으로 변경되지 않았습니다. Layout.astro에서 직접 설정 중.

### `tsconfig.json`
TypeScript 설정:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"],      // @/ → src/
      "~/*": ["./*"]         // ~/ → 프로젝트 루트
    }
  }
}
```

**경로 별칭 예시**:
```typescript
import Layout from "@/layouts/Layout.astro";      // src/layouts/Layout.astro
import config from "~/astro.config.mjs";          // astro.config.mjs
```

### `package.json`
NPM 스크립트 및 의존성:

```json
{
  "scripts": {
    "dev": "astro dev",           // 개발 서버
    "start": "astro dev",         // 개발 서버 (별칭)
    "build": "astro check && astro build",  // 빌드
    "preview": "astro preview",   // 빌드 미리보기
    "astro": "astro"             // Astro CLI
  }
}
```

---

## 📊 파일 통계

### 소스 코드 분포
- **Pages**: 8개
- **Components**: 10개 (서브디렉토리 포함)
- **Layouts**: 2개
- **Content**: 4개 (팀 멤버)
- **Utils**: 1개 파일

### 기술 스택 파일
- `.astro` 파일: 주요 컴포넌트 및 페이지
- `.ts` 파일: TypeScript 설정 및 타입 정의
- `.js` 파일: 유틸리티 함수
- `.md/.mdx` 파일: 콘텐츠 (블로그, 팀)

---

## 🔗 크로스 레퍼런스

### 관련 문서
- [컴포넌트 가이드](./COMPONENTS.md) - 각 컴포넌트 사용법
- [개발 가이드](./DEVELOPMENT.md) - 파일 추가/수정 워크플로우
- [콘텐츠 관리](./CONTENT.md) - Content Collections 활용법

### 자주 수정하는 위치
- **네비게이션 메뉴 변경**: [src/components/navbar/navbar.astro](../src/components/navbar/navbar.astro)
- **푸터 정보 변경**: [src/components/footer.astro](../src/components/footer.astro)
- **홈페이지 섹션 수정**: [src/pages/index.astro](../src/pages/index.astro)
- **팀 멤버 추가**: [src/content/team/](../src/content/team/) (새 .md 파일)

---

**마지막 업데이트**: 2025-01-17
**문서 버전**: 1.0.0
