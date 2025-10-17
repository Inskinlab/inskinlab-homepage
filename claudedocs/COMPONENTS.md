# 컴포넌트 가이드

## 📦 컴포넌트 개요

인스킨랩 홈페이지는 재사용 가능한 Astro 컴포넌트로 구성되어 있습니다. 모든 컴포넌트는 TypeScript Props와 TailwindCSS를 활용합니다.

---

## 🧩 UI 기본 요소 (`/src/components/ui/`)

### `button.astro`
**역할**: 스타일이 적용된 버튼 컴포넌트

**Props**:
```typescript
interface Props {
  style?: "primary" | "outline" | "inverted";
  size?: "sm" | "md" | "lg";
  block?: boolean;
  class?: string;
}
```

**사용 예시**:
```astro
<Button style="primary" size="md">
  지금 시작하기
</Button>

<Button style="outline" block>
  자세히 보기
</Button>
```

**스타일 종류**:
- `primary`: 기본 브랜드 색상 버튼
- `outline`: 테두리만 있는 버튼
- `inverted`: 반전 색상 버튼

### `link.astro`
**역할**: 일관된 링크 스타일

**Props**:
```typescript
interface Props {
  href: string;
  block?: boolean;
  size?: "sm" | "md" | "lg";
  class?: string;
  style?: "primary" | "outline" | "inverted";
}
```

**사용 예시**:
```astro
<Link href="/about" style="primary">
  회사 소개
</Link>

<Link href="/contact" style="outline" size="sm">
  문의하기
</Link>
```

**특징**:
- 내부 링크와 외부 링크 자동 감지
- 접근성 속성 자동 추가 (외부 링크: `rel="noopener noreferrer"`)

### `icons/` 디렉토리

#### `index.js`
**역할**: 아이콘 내보내기 중앙 관리

**사용 가능한 아이콘**:
- `tick.astro` - 체크마크 아이콘

**사용 예시**:
```astro
import { Icon } from "astro-icon/components";

<Icon name="tick" class="w-4 h-4" />
```

#### `tick.astro`
**역할**: 체크마크 SVG 아이콘

**사용 예시**:
```astro
import Tick from "@/components/ui/icons/tick.astro";

<Tick />
```

---

## 🧭 네비게이션 (`/src/components/navbar/`)

### `navbar.astro`
**역할**: 반응형 메인 네비게이션 바

**구조**:
```astro
<header class="sticky top-0">
  <Container>
    <Logo />
    <MenuItems />  <!-- 데스크톱 메뉴 -->
    <MobileMenu /> <!-- 모바일 햄버거 메뉴 -->
  </Container>
</header>
```

**메뉴 항목**:
```javascript
const menuitems = [
  { title: "홈", path: "/" },
  { title: "회사 소개", path: "/about" },
  { title: "팀", path: "/team" },
  { title: "문의하기", path: "/contact" },
];
```

**메뉴 추가 방법**:
1. [navbar.astro](../src/components/navbar/navbar.astro) 열기
2. `menuitems` 배열에 항목 추가:
   ```javascript
   { title: "새 메뉴", path: "/new-page" }
   ```
3. 저장 → 자동 반영

**기능**:
- 스크롤 시 고정 (sticky)
- 반응형 (모바일/데스크톱 자동 전환)
- 드롭다운 지원 (dropdown.astro 활용)

### `dropdown.astro`
**역할**: 드롭다운 메뉴 컴포넌트

**Props**:
```typescript
interface Props {
  title: string;
  children: any;
}
```

**사용 예시**:
```astro
<Dropdown title="서비스">
  <a href="/service1">서비스 1</a>
  <a href="/service2">서비스 2</a>
</Dropdown>
```

**현재 상태**: navbar.astro에서 사용하지 않음 (향후 서브메뉴 필요 시 활용)

---

## 📦 레이아웃 컴포넌트

### `container.astro`
**역할**: 컨텐츠 최대 너비 제한 컨테이너

**사용 예시**:
```astro
<Container>
  <h1>제목</h1>
  <p>내용...</p>
</Container>
```

**스타일**:
```css
max-width: 1280px;  /* xl 브레이크포인트 */
margin: 0 auto;     /* 중앙 정렬 */
padding: 0 1rem;    /* 좌우 패딩 */
```

**언제 사용하나요?**
- 페이지 섹션 내용을 화면 중앙에 정렬할 때
- 넓은 화면에서 가독성을 위해 너비를 제한할 때

### `sectionhead.astro`
**역할**: 섹션 헤더 (타이틀 + 설명)

**Props**:
```typescript
interface Props {
  align?: "center" | "left";
}
```

**사용 예시**:
```astro
<Sectionhead align="center">
  <Fragment slot="title">인스킨뷰</Fragment>
  <Fragment slot="desc">
    인공지능 기반 맞춤형 피부 시술 추천
  </Fragment>
</Sectionhead>
```

**Slots**:
- `title`: 섹션 제목
- `desc`: 섹션 설명

**스타일**:
- `align="center"`: 중앙 정렬 (기본값)
- `align="left"`: 왼쪽 정렬

---

## 🎨 콘텐츠 컴포넌트

### `features.astro`
**역할**: 기능 소개 카드 그리드

**Props**:
```typescript
interface Props {
  features: Array<{
    title: string;
    description: string;
    icon: string;  // astro-icon 이름
  }>;
}
```

**사용 예시**:
```astro
---
const features = [
  {
    title: "AI 분석",
    description: "정확한 피부 분석",
    icon: "bx:bxs-check-circle",
  },
  // ...
];
---

<Features features={features} />
```

**레이아웃**:
- 그리드: 1열 (모바일) → 2열 (태블릿) → 3열 (데스크톱)
- 각 카드: 아이콘 + 제목 + 설명

### `contactform.astro`
**역할**: 문의 폼 컴포넌트

**필드**:
```javascript
{
  name: "이름",
  email: "이메일",
  message: "문의 내용"
}
```

**사용 예시**:
```astro
<Contactform />
```

**제출 동작**:
- 현재: 클라이언트 측 검증만 (백엔드 연동 없음)
- 향후: API 엔드포인트 연동 필요

**스타일**:
- TailwindCSS 폼 스타일
- 반응형 레이아웃
- 접근성 레이블 포함

### `footer.astro`
**역할**: 사이트 푸터

**섹션**:
1. **회사 정보**
   - 로고
   - 회사 설명
2. **링크**
   - 회사 소개
   - 이용약관
   - 개인정보처리방침
3. **연락처**
   - 이메일
   - 전화번호 (선택적)

**사용 위치**: [Layout.astro](../src/layouts/Layout.astro)에서 자동 포함

**수정 방법**:
1. [footer.astro](../src/components/footer.astro) 열기
2. 섹션 내용 수정
3. 저장 → 모든 페이지에 자동 반영

---

## 🎯 사용 패턴

### 컴포넌트 Import
```astro
---
// 경로 별칭 사용 (권장)
import Container from "@/components/container.astro";
import Button from "@/components/ui/button.astro";

// 상대 경로 (사용 가능하지만 권장하지 않음)
import Container from "../components/container.astro";
---
```

### Props 전달
```astro
---
// Props 타입 정의
interface Props {
  title: string;
  optional?: boolean;
}

const { title, optional = false } = Astro.props;
---

<div>
  <h1>{title}</h1>
  {optional && <p>Optional content</p>}
</div>
```

### Slots 사용
```astro
---
// ParentComponent.astro
---
<div>
  <slot name="header" />  <!-- 이름 있는 slot -->
  <slot />                <!-- 기본 slot -->
  <slot name="footer" />
</div>

<!-- 사용 예시 -->
<ParentComponent>
  <Fragment slot="header">
    <h1>헤더</h1>
  </Fragment>
  <p>기본 콘텐츠</p>
  <Fragment slot="footer">
    <footer>푸터</footer>
  </Fragment>
</ParentComponent>
```

---

## 🔄 컴포넌트 재사용 전략

### 언제 새 컴포넌트를 만들어야 하나요?

#### ✅ 컴포넌트로 분리하기
- 3번 이상 반복되는 UI 패턴
- 독립적인 기능 단위
- 재사용 가능성이 있는 UI

#### ❌ 컴포넌트로 분리하지 않기
- 1-2번만 사용되는 페이지 특화 UI
- 너무 작은 단위 (예: 단일 `<div>`)

### 컴포넌트 조직 규칙
1. **기능별 그룹화**: 관련 컴포넌트는 서브디렉토리로
   ```
   components/
   └── navbar/
       ├── navbar.astro
       └── dropdown.astro
   ```

2. **명명 규칙**: kebab-case 파일명
   ```
   ✅ contact-form.astro
   ❌ ContactForm.astro
   ❌ contactForm.astro
   ```

3. **Props 타입 정의**: 모든 Props에 TypeScript 인터페이스
   ```typescript
   interface Props {
     title: string;
     optional?: boolean;
   }
   ```

---

## 🎨 스타일링 가이드

### TailwindCSS 클래스 사용
```astro
<!-- 컴포넌트 내부 스타일 -->
<div class="flex items-center gap-4 p-6 bg-white rounded-lg shadow">
  <slot />
</div>
```

### 커스텀 스타일 (필요 시)
```astro
<style>
  .custom-element {
    /* TailwindCSS로 표현하기 어려운 스타일만 */
  }
</style>
```

### 조건부 클래스
```astro
---
const { variant = "default" } = Astro.props;
---

<button class:list={[
  "btn",
  { "btn-primary": variant === "primary" },
  { "btn-outline": variant === "outline" }
]}>
  <slot />
</button>
```

---

## 📚 컴포넌트 체크리스트

### 새 컴포넌트 작성 시
- [ ] Props 인터페이스 정의
- [ ] 기본값 설정 (optional props)
- [ ] TailwindCSS 클래스 활용
- [ ] 반응형 고려
- [ ] 접근성 속성 추가 (aria-*, role)
- [ ] 재사용 가능하게 설계

### 컴포넌트 수정 시
- [ ] 기존 사용처 영향 확인
- [ ] Props 타입 호환성 유지
- [ ] 스타일 일관성 확인

---

## 🔗 관련 문서

- [프로젝트 구조](./STRUCTURE.md) - 컴포넌트 디렉토리 위치
- [스타일 가이드](./STYLING.md) - TailwindCSS 사용법
- [개발 가이드](./DEVELOPMENT.md) - 컴포넌트 추가/수정 워크플로우

---

## 🛠️ 트러블슈팅

### 컴포넌트가 렌더링되지 않음
1. Import 경로 확인 (`@/components/...`)
2. Props 타입 일치 확인
3. 개발 서버 재시작 (`pnpm dev`)

### 스타일이 적용되지 않음
1. TailwindCSS 클래스 오타 확인
2. `global.css` import 확인 (Layout.astro)
3. 빌드 캐시 삭제 후 재빌드

### TypeScript 오류
1. `env.d.ts` 파일 확인
2. VSCode TypeScript 서버 재시작
3. `tsconfig.json` 경로 별칭 확인

---

**마지막 업데이트**: 2025-01-17
**문서 버전**: 1.0.0
