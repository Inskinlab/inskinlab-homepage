# 인스킨랩 홈페이지

인공지능 기술을 바탕으로 내 피부에 꼭 맞는 시술과 화장품을 추천해주는 스마트 피부 솔루션 **인스킨랩(InSkin Lab)**의 공식 홈페이지입니다.

## 🚀 기술 스택

- **[Astro 5.x](https://astro.build)** - 정적 사이트 생성기
- **[TailwindCSS 4.x](https://tailwindcss.com)** - 유틸리티 우선 CSS 프레임워크
- **[TypeScript](https://www.typescriptlang.org/)** - 타입 안전성
- **[MDX](https://mdxjs.com/)** - 마크다운 + JSX
- **[Sharp](https://sharp.pixelplumbing.com/)** - 이미지 최적화

## 🛠️ 개발 환경 설정

### 필수 조건
- Node.js 18+ 
- pnpm (권장 패키지 매니저)

### 설치 및 실행

```bash
# 의존성 설치
pnpm install

# 개발 서버 실행
pnpm dev

# 프로덕션 빌드
pnpm build

# 빌드 미리보기
pnpm preview
```

## 📁 프로젝트 구조

```
src/
├── components/          # 재사용 가능한 UI 컴포넌트
│   ├── ui/             # 기본 UI 요소들 (버튼, 링크 등)
│   ├── navbar/         # 네비게이션 컴포넌트
│   └── ...
├── layouts/            # 페이지 레이아웃 템플릿
├── pages/              # 페이지 파일들 (파일 기반 라우팅)
├── content/            # 콘텐츠 컬렉션 (블로그, 팀)
├── assets/             # 이미지 및 정적 자산
└── utils/              # 유틸리티 함수들

public/                 # 정적 파일들
```

## 🎯 주요 기능

- **반응형 디자인** - 모든 디바이스에서 최적화된 UI
- **SEO 최적화** - astro-seo를 통한 메타 태그 관리
- **딥링크 지원** - 인스킨랩 모바일 앱 연동
- **컨텐츠 관리** - Astro Content Collections 활용
- **Google Analytics** - 사용자 분석 추적
- **이미지 최적화** - Sharp를 통한 자동 이미지 최적화

## 🔗 딥링크 기능

인스킨랩 모바일 앱과 연동된 딥링크 기능을 지원합니다:
- 앱 설치 링크
- 특정 페이지로 직접 이동

## 🌐 배포

- **사이트 URL**: https://inskinlab.com
- **빌드 타입**: 정적 사이트 (Static)
- **호스팅**: Vercel/Netlify 등 정적 호스팅 서비스 권장

## 🧪 개발 가이드

### 새 페이지 추가
`src/pages/` 디렉토리에 `.astro` 파일을 추가하면 자동으로 라우팅됩니다.

### 컴포넌트 작성
TypeScript와 Astro 문법을 사용하여 재사용 가능한 컴포넌트를 작성할 수 있습니다.

### 콘텐츠 추가
`src/content/` 디렉토리에서 블로그 포스트나 팀 멤버 정보를 관리할 수 있습니다.

### 스타일링
TailwindCSS 클래스를 사용하여 스타일을 적용하거나, 글로벌 CSS는 `src/styles/` 디렉토리에서 관리합니다.

## 📝 라이선스

이 프로젝트는 인스킨랩의 소유입니다.

---

**Built with ❤️ by InSkin Lab Team**

[![Built with Astro](https://astro.badg.es/v1/built-with-astro.svg)](https://astro.build)