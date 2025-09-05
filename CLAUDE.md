# CLAUDE.md

이 파일은 Claude Code (claude.ai/code)가 이 저장소에서 작업할 때 사용하는 가이드입니다.

## 개발 명령어

- `pnpm dev` 또는 `pnpm start` - 개발 서버 실행 (pnpm이 선호하는 패키지 매니저)
- `pnpm build` - 프로덕션용 빌드
- `pnpm preview` - 빌드된 사이트 로컬 미리보기
- `pnpm astro add` - 새로운 Astro 통합 추가
- `pnpm astro --help` - Astro CLI 도움말

## 프로젝트 아키텍처

인공지능 피부 기술 회사인 인스킨랩(InSkin Lab)의 Astro 기반 웹사이트입니다. Astro 규칙을 따르는 프로젝트 구조:

### 핵심 구조
- **Pages**: `src/pages/`에 위치 - `.astro` 파일 기반 라우팅
- **Components**: `src/components/`의 재사용 가능한 UI 컴포넌트들 (기능별 정리)
- **Layouts**: `src/layouts/`의 기본 페이지 템플릿 (Layout.astro, BlogLayout.astro)
- **Content Collections**: `src/content/config.ts`에서 설정된 `blog`와 `team` 컬렉션
- **Assets**: `src/assets/`의 정적 이미지 및 미디어
- **Utilities**: `src/utils/all.js`의 헬퍼 함수들

### 기술 스택
- **Astro 5.x** - 컴포넌트 아일랜드를 지원하는 정적 사이트 생성기
- **TailwindCSS 4.x** - 유틸리티 우선 CSS 프레임워크 (Vite 플러그인으로 설정)
- **TypeScript** - 경로 별칭과 함께 타입 안전성 제공 (`@/*`는 `src/*`, `~/*`는 루트)
- **MDX** - 콘텐츠용 JSX 지원 마크다운
- **Sharp** - 이미지 최적화
- **Astro 통합**: icon, sitemap, MDX

### 콘텐츠 관리
- 콘텐츠 컬렉션이 블로그 포스트와 팀 멤버 스키마 정의
- 블로그 포스트는 초안 상태, 카테고리, 태그, 대표 이미지 지원
- 팀 멤버는 이름, 직책, 설명, 아바타, 순서 필드 포함
- 전체 사이트가 한국어 콘텐츠

### 스타일링 및 컴포넌트
- Fontsource Variable 폰트 사용 (Inter, Bricolage Grotesque)
- UI 기본 요소들 포함한 컴포넌트 라이브러리 (버튼, 링크, 아이콘)
- 드롭다운 기능이 있는 반응형 네비게이션
- 일관된 레이아웃 너비를 위한 컨테이너 컴포넌트
- astro-seo 통합으로 SEO 최적화

### 설정 참고사항
- 사이트 URL은 Layout.astro에서 inskinlab.com으로 설정 (astro.config.mjs가 아님)
- Layout.astro에서 Google Analytics (G-6Q83WKPCS7) 설정
- 최적 성능을 위한 정적 출력 모드
- 이미지를 위한 content visibility CSS 최적화

## 언어 설정
- Claude와의 모든 대화는 한국어로 진행