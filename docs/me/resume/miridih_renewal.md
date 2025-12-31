# 미리디 (miridih)
> **Frontend Developer** | 2020.01 ~ 2022.02 (2년 2개월)
>
> "웹 기반 디자인 툴(SaaS)의 **성능 최적화**와 **구독 비즈니스 모델** 구현을 주도하며 서비스의 유료화 전환을 성공시킨 개발자입니다."

## 🏆 Key Achievements
*   **Performance**: 이미지 Lazy Loading 및 렌더링 최적화로 **페이지 로딩 속도 55% 향상** (11.55s → 5.14s).
*   **Structure**: 복잡한 권한 및 플랜 관리 로직을 **Wrapper Component 패턴**으로 설계하여 유료화 전환 성공.
*   **Growth**: Node.js 기반 SEO 시스템 구축으로 **3개월간 노출 수 170만 건** 달성.

## 🛠 Technical Skills
![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![SCSS](https://img.shields.io/badge/SCSS-hotpink.svg?style=for-the-badge&logo=SASS&logoColor=white)

---

## 📂 Key Projects

### 1. Paid Service Transition & Squad Leadership
*2021.08 ~ 2022.02*
> '유료화 스쿼드'의 리더로서 무료 서비스였던 미리캔버스를 구독형(SaaS) 모델로 전환하는 핵심 로직을 설계했습니다.

**Challenges & Actions:**
*   **Global State Management**: 사용자 요금제(Free/Pro/Enterprise)와 만료일, 권한 정보를 전역 상태로 관리하는 아키텍처 설계.
*   **Scalable Guard Logic**: 각 기능(버튼, 메뉴 등)이 플랜에 따라 다르게 동작하도록 **HOC 및 Wrapper Component**를 도입하여, 비즈니스 로직을 UI에서 분리하고 일관성 확보.
*   **Team Leadership**: 2명의 주니어 개발자를 멘토링하며 코드 리뷰 및 스프린트 일정 관리.

**Result:**
*   **Business Success**: 유료 구독 시스템의 성공적 런칭 및 안정적 운영.
*   **Maintainability**: 기능 제약 로직의 중앙화를 통해, 향후 요금제 정책 변경 시 대응 비용 최소화.

### 2. Workspace & B2B Enterprise Features
*2021.04 ~ 2022.02*
> 개인 위주의 툴을 '협업 도구'로 확장하기 위한 워크스페이스 및 브랜드 키트 기능을 개발했습니다.

**Key Features:**
*   **FileSystem UI**: 폴더 구조의 드라이브 시스템과 CRUD, Drag & Drop 이동 로직 구현.
*   **Role-Based Access Control**: 워크스페이스 내 사용자 역할(Owner, Member, Viewer)에 따른 세밀한 권한 제어 구현.
*   **Brand Kit**: 기업 고객을 위한 브랜드 컬러/폰트 관리 기능 및 엔터프라이즈 전용 제약 로직 개발.

**Impact:**
*   팀 단위 협업 기능 제공으로 **B2B 영업 소구 포인트** 확보.

![workspace](https://camo.githubusercontent.com/66716b948d72266c914b8cdb1c6f6493bb84d7b7fb210366fcbea48ade73ff88/68747470733a2f2f747661312e73696e61696d672e636e2f6c617267652f3030386933736b4e67793167786a6171643562616e673330676f3061666232392e676966)

### 3. Chart Grid Development
*2021.01 ~ 2021.03*
> 엑셀과 유사한 웹 차트 그리드를 구현하기 위해 오픈소스를 fork하여 커스터마이징했습니다.

**Key Features:**
*   **Adapter Pattern**: 차트 데이터의 입출력 처리를 유연하게 하기 위해 어댑터 패턴 적용.
*   **Customization**: 키보드 단축키, Resizable Window, CSS 커스텀 등 엑셀 유사 경험 구현.

![chart grid](https://camo.githubusercontent.com/41c77c71c9ff22ec76c189fbe69a71fb2ad65b4b8d33ac9dbc070ead451d8f15/68747470733a2f2f747661312e73696e61696d672e636e2f6c617267652f3030386933736b4e67793167786a3965346e687467673330676f3061666833302e676966)

### 4. Core Web Vitals & SEO Optimization
*2020.08 ~ 2020.11*
> 초기 로딩이 느리고 검색 엔진에 노출되지 않던 SPA의 한계를 기술적으로 극복했습니다.

**Problem:**
*   고해상도 이미지가 많은 디자인 툴 특성상 초기 로딩에 11초 이상 소요.
*   SPA 구조로 인해 Googlebot 크롤링이 원활하지 않아 마케팅 유입 저조.

**Action:**
*   **Lazy Loading**: `Intersection Observer` API를 활용하여 뷰포트 내의 이미지만 로드하도록 개선 (Resource 55MB → 6MB).
*   **SEO System**: Node.js/Express 기반의 Prerendering 서버를 독자 구축하여, 메타 태그와 오픈 그래프 정보를 동적으로 주입.

**Result:**
*   **Speed**: 페이지 로딩 속도 **11.55s → 5.14s**로 2배 이상 개선.
*   **Traffic**: 구글 서치 콘솔 기준 3개월 만에 **노출 수 170만 건** 달성.

---

### [Link]
- [CSS Global Variables로 Theming 성능 6배 최적화](../../front-end/css/css%20global%20variables%EB%A1%9C%20theming%20%ED%95%98%EA%B8%B0.md)
- [Sass 걷어내고 CSS-in-JS로 빌드 최적화](../sass-%EA%B1%B0%EB%91%AC%EB%82%B4%EA%B3%A0-css-in-js-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0.md)
