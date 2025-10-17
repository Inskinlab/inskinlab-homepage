# 인스킨랩 홈페이지 프로젝트 인덱스

## 📋 프로젝트 개요

**프로젝트명**: 인스킨랩(InSkin Lab) 공식 홈페이지
**목적**: 인공지능 기반 맞춤형 피부 솔루션 서비스 소개 및 홍보
**기술 스택**: Astro 5.x, TailwindCSS 4.x, TypeScript
**배포 URL**: https://inskinlab.com

---

## 🗂️ 문서 구조

### 핵심 문서
- **[프로젝트 구조](./STRUCTURE.md)** - 디렉토리 및 파일 구조 상세 가이드
- **[컴포넌트 가이드](./COMPONENTS.md)** - UI 컴포넌트 문서 및 사용법
- **[개발 가이드](./DEVELOPMENT.md)** - 개발 환경 설정 및 워크플로우
- **[콘텐츠 관리](./CONTENT.md)** - Content Collections 사용 가이드
- **[스타일 가이드](./STYLING.md)** - TailwindCSS 스타일링 규칙

### 설정 파일
- **[astro.config.mjs](../astro.config.mjs)** - Astro 프레임워크 설정
- **[tsconfig.json](../tsconfig.json)** - TypeScript 설정
- **[package.json](../package.json)** - 의존성 및 스크립트
- **[src/content/config.ts](../src/content/config.ts)** - Content Collections 스키마

---

## 📁 주요 디렉토리

### `/src/components/`
재사용 가능한 UI 컴포넌트들

```
src/components/
├── ui/                    # 기본 UI 요소
│   ├── button.astro      # 버튼 컴포넌트
│   ├── link.astro        # 링크 컴포넌트
│   └── icons/            # 아이콘 컴포넌트
├── navbar/               # 네비게이션
│   ├── navbar.astro      # 메인 네비게이션 바
│   └── dropdown.astro    # 드롭다운 메뉴
├── container.astro       # 레이아웃 컨테이너
├── footer.astro          # 푸터
├── sectionhead.astro     # 섹션 헤더
├── features.astro        # 기능 소개 섹션
└── contactform.astro     # 문의 폼
```

**참고**: [컴포넌트 가이드](./COMPONENTS.md)

### `/src/pages/`
파일 기반 라우팅 페이지들

```
src/pages/
├── index.astro           # 메인 홈페이지
├── about.astro           # 회사 소개
├── team.astro            # 팀 소개
├── contact.astro         # 문의하기
├── app.astro             # 앱 다운로드/딥링크
├── terms.astro           # 이용약관
├── privacy.astro         # 개인정보처리방침
└── 404.astro             # 404 에러 페이지
```

**라우팅**: 파일명이 URL 경로로 자동 매핑됩니다.

### `/src/layouts/`
페이지 레이아웃 템플릿

```
src/layouts/
├── Layout.astro          # 기본 레이아웃 (SEO, GA, 네비게이션, 푸터)
└── BlogLayout.astro      # 블로그 포스트 레이아웃
```

**참고**: [레이아웃 문서](./STRUCTURE.md#layouts)

### `/src/content/`
Content Collections (블로그, 팀)

```
src/content/
├── config.ts             # 컬렉션 스키마 정의
├── blog/                 # 블로그 포스트 (MDX)
└── team/                 # 팀 멤버 정보 (Markdown)
    ├── moonsuk-jung.md
    ├── sukkyu-sun.md
    ├── youngjae-heo.md
    └── sooick-cho.md
```

**참고**: [콘텐츠 관리 가이드](./CONTENT.md)

---

## 🔧 기술 스택 세부사항

### 프레임워크 & 라이브러리
| 기술 | 버전 | 용도 |
|------|------|------|
| **Astro** | 5.14.5 | 정적 사이트 생성기 |
| **TailwindCSS** | 4.x | 유틸리티 우선 CSS 프레임워크 |
| **TypeScript** | 5.8.3 | 타입 안전성 |
| **MDX** | 4.3.7 | 마크다운 + JSX |
| **Sharp** | 0.33.5 | 이미지 최적화 |

### Astro 통합
- **@astrojs/mdx** - MDX 지원
- **@astrojs/sitemap** - 사이트맵 자동 생성
- **astro-icon** - 아이콘 통합
- **astro-seo** - SEO 최적화

### 유틸리티
- **@tailwindcss/typography** - 타이포그래피 플러그인
- **@tailwindcss/vite** - Vite 통합
- **astro-navbar** - 반응형 네비게이션

---

## 🚀 빠른 시작

### 개발 환경 설정
```bash
# 의존성 설치
pnpm install

# 개발 서버 실행 (http://localhost:4321)
pnpm dev

# 프로덕션 빌드
pnpm build

# 빌드 미리보기
pnpm preview
```

**자세한 내용**: [개발 가이드](./DEVELOPMENT.md)

---

## 📚 주요 기능

### ✅ 구현된 기능
- [x] 반응형 디자인 (모바일/태블릿/데스크톱)
- [x] SEO 최적화 (메타 태그, 오픈그래프)
- [x] Google Analytics 추적 (G-6Q83WKPCS7)
- [x] 딥링크 지원 (모바일 앱 연동)
- [x] 이미지 최적화 (Sharp)
- [x] 사이트맵 자동 생성
- [x] Content Collections (블로그, 팀)
- [x] 다크모드 없음 (라이트 테마 고정)

### 🔄 페이지별 기능

#### 홈페이지 (`/`)
- 풀스크린 스크롤 섹션 (스냅 스크롤)
- 4개 주요 섹션: 인트로, 맞춤 시술, 셀카 분석, 인스킨뷰 앱

#### 팀 페이지 (`/team`)
- Content Collections에서 팀 멤버 데이터 로드
- 순서별 정렬 (`order` 필드)
- 아바타 이미지 최적화

#### 앱 페이지 (`/app`)
- 딥링크 자동 리다이렉션
- 플랫폼 감지 (iOS/Android)
- 앱 스토어 링크

---

## 🎨 스타일링 규칙

### TailwindCSS 사용
- 유틸리티 클래스 우선 사용
- 커스텀 컴포넌트 스타일은 `<style>` 블록 활용
- 글로벌 스타일은 `/src/styles/global.css`

### 컬러 팔레트
- 주요 브랜드 색상: TailwindCSS 기본 팔레트
- 다크모드 미지원 (라이트 테마만)

### 타이포그래피
- **헤드라인**: Bricolage Grotesque Variable
- **본문**: Inter Variable
- Fontsource를 통한 폰트 로딩

**자세한 내용**: [스타일 가이드](./STYLING.md)

---

## 🔗 크로스 레퍼런스

### 자주 수정하는 파일
- **레이아웃 수정**: [src/layouts/Layout.astro](../src/layouts/Layout.astro)
- **네비게이션 메뉴**: [src/components/navbar/navbar.astro](../src/components/navbar/navbar.astro)
- **홈페이지 콘텐츠**: [src/pages/index.astro](../src/pages/index.astro)
- **팀 멤버 추가**: [src/content/team/](../src/content/team/)
- **SEO 설정**: [src/layouts/Layout.astro](../src/layouts/Layout.astro) (L8-L60)

### 설정 변경
- **사이트 URL**: `astro.config.mjs` (L9) 또는 `Layout.astro` (L13)
- **Google Analytics**: [src/layouts/Layout.astro](../src/layouts/Layout.astro) (L52-L60)
- **경로 별칭**: [tsconfig.json](../tsconfig.json) (`@/*`, `~/*`)

---

## 🐛 트러블슈팅

### 자주 발생하는 문제

#### 빌드 오류
```bash
# 캐시 삭제 후 재빌드
rm -rf .astro node_modules
pnpm install
pnpm build
```

#### 이미지 최적화 오류
- Sharp 네이티브 모듈 재설치: `pnpm rebuild sharp`

#### 타입 오류
- TypeScript 서버 재시작
- `tsconfig.json` 경로 별칭 확인

---

## 📝 변경 이력

최신 변경사항은 [CHANGELOG.md](../CHANGELOG.md)를 참고하세요.

---

## 👥 팀 및 기여

**프로젝트 소유**: 인스킨랩(InSkin Lab)
**개발 팀**: [팀 페이지 참고](/team)

---

## 📞 지원 및 문의

- **웹사이트**: https://inskinlab.com
- **문의**: [Contact 페이지](/contact)

---

**마지막 업데이트**: 2025-01-17
**문서 버전**: 1.0.0
