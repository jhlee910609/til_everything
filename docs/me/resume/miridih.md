# 미리디 (미리캔버스)

![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![SCSS](https://img.shields.io/badge/SCSS-hotpink.svg?style=for-the-badge&logo=SASS&logoColor=white) ![ESLint](https://img.shields.io/badge/ESLint-4B3263?style=for-the-badge&logo=eslint&logoColor=white) ![Prettier](https://img.shields.io/badge/prettier-1A2C34?style=for-the-badge&logo=prettier&logoColor=F7BA3E)

## 기본 정보

- **재직 기간**: 2020.01 ~ 2022.02 (2년 2개월)
- **회사명**: 미리디 (miridih)
- **역할**: Front-end Developer
- **주요 업무**: 미리캔버스 웹 디자인 툴 프론트엔드 개발

## 주요 프로젝트 및 업무

### 1. 템플릿 페이지 개발 (2020.08)

**마케팅 유입 Bridge Page인 template page 개발 및 SEO 최적화(100%)**

- **SEO 최적화**
  - SPA 구조에서 SEO 최적화를 위해 react-helmet 적용
  - intersection observer를 활용한 image lazy loading 구현
- **성과**
  - 고객 이탈율 0%의 페이지 개발
  - 데스크탑/태블릿/모바일 반응형 지원

### 2. Workspace 개발 (2021.04 ~ 2022.02)

**디자인 관리 서비스인 workspace 개발(80%)**

![workspace](https://camo.githubusercontent.com/66716b948d72266c914b8cdb1c6f6493bb84d7b7fb210366fcbea48ade73ff88/68747470733a2f2f747661312e73696e61696d672e636e2f6c617267652f3030386933736b4e67793167786a6171643562616e673330676f3061666232392e676966)

- **주요 기능**

  - 디자인 관리의 편의성을 제공하고자 폴더 구조 개발
  - 다른 사용자와 사용할 수 있는 공유 폴더 기능 개발
  - 사용자 권한, 브랜드 관리, 설정 기능 개발

- **브랜드 키트 개발**
  - B2B용 엔터프라이즈 기능
  - 사용자 요금제에 따른 브랜드 키트 제한 개수, 각각 항목의 제한 개수 등에 대한 제약 처리

### 3. 메뉴 패널 React 마이그레이션 (2020.01 ~ 2022.02)

**에디터 영역을 제외한 메뉴 패널 React migration**

- vanilla.js로만 되어 있던 환경에 React.js 도입
- 개발 생산성 향상에 기여
- 전사 개발자 대상으로 React.js 도입기 및 기초 교육 실시

### 4. Chart Grid 개발 (2021.01 ~ 2021.03)

**JsSpread fork 하여 개발**

![chart grid](https://camo.githubusercontent.com/41c77c71c9ff22ec76c189fbe69a71fb2ad65b4b8d33ac9dbc070ead451d8f15/68747470733a2f2f747661312e73696e61696d672e636e2f6c617267652f3030386933736b4e67793167786a3965346e687467673330676f3061666833302e676966)

- **기술적 구현**
  - 엑셀과 동일한 기능을 요구하여 구현
  - 각각의 차트마다 data 처리가 쉽도록 adapter pattern을 활용하여, 차트 데이터 입/출력 구현
  - 차트 데이터 그리드 오픈소스(JsSpreadsheet) 커스텀 및 프로덕션 적용

### 5. 유료화 스쿼드 리더 (2021.08 ~ 2022.02)

**2명의 주니어 개발자와 함께 유료 기능 및 유료 기능 제한 기능 개발**

- **유료화 제약 기능 개발**
  - 유료 디자인 오브젝트 canvas로 워터마크 처리
  - 무료 사용자의 유료 기능 제한
  - 요금제 페이지 개발

### 6. 성능 최적화 (2020.08 ~ 2020.11)

**Intersection Observer 도입을 통한 성능 개선**

- **Lazy Loading 구현**

  - 웹 페이지 로딩 속도 향상을 위해 Intersection Observer를 활용하여 Lazy Loading 하도록 개선
  - LazyImageComponent 개발 후, img tag 활용하는 곳에 점진적 적용

- **성과**
  - `/templates` 웹 페이지 초기 로딩 속도 향상: **11.55s → 5.14s**
  - Image resource load: **55MB → 6MB로 축소**

### 7. SEO 개선 (2020.09 ~ 2020.11)

**전사 SEO 최적화 프로젝트**

- **기술적 구현**

  - SEO가 적용되어 있지 않은 모든 미리캔버스 웹 페이지에 SEO 적용
  - vanilla.js로 구현된 관계로 순수 구현 (Node.js, Express, Mustache)

- **성과**
  - **3개월간 170만건의 노출 수** (구글 서치 기준) 달성

## 성과 및 기여도

### 성능 개선

- **페이지 로딩 속도 55% 향상** (11.55s → 5.14s)
- **이미지 리소스 89% 최적화** (55MB → 6MB)
- **SEO 노출 수 170만건** 달성 (3개월간)

### 비즈니스 기여

- **템플릿 페이지 이탈율 0%** 달성
- **유료화 전환** 프로젝트 리딩
- **워크스페이스 서비스** 신규 개발

### 기술적 기여

- **React 마이그레이션** 주도로 개발 생산성 향상
- **어댑터 패턴** 도입으로 차트 데이터 처리 최적화
- **Intersection Observer** 도입으로 성능 최적화

### 조직 기여

- **팀 리딩 경험**: 2명의 주니어 개발자 멘토링
- **기술 교육**: 전사 React.js 도입기 및 기초 교육
- **오픈소스 기여**: JsSpreadsheet contributor

## 학습 및 성장

### SaaS 제품 개발 경험

- **미리캔버스**라는 웹 에디터 SaaS 제품 개발 경험
- 복잡한 UI/UX 요구사항 구현 경험

### 성능 최적화 전문성

- **Lazy Loading**, **SEO 최적화** 등 웹 성능 최적화 경험
- 대용량 이미지 처리 및 최적화 경험

### 팀 리딩 및 멘토링

- **유료화 스쿼드 리더**로서 팀 프로젝트 관리 경험
- 주니어 개발자 멘토링을 통한 리더십 개발

### 기술 도입 및 교육

- **React 마이그레이션** 주도 및 전사 교육 실시
- 레거시 시스템 현대화 경험
