# 미리디 (미리캔버스)

![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![SCSS](https://img.shields.io/badge/SCSS-hotpink.svg?style=for-the-badge&logo=SASS&logoColor=white) ![ESLint](https://img.shields.io/badge/ESLint-4B3263?style=for-the-badge&logo=eslint&logoColor=white) ![Prettier](https://img.shields.io/badge/prettier-1A2C34?style=for-the-badge&logo=prettier&logoColor=F7BA3E)

## 기본 정보

- **재직 기간**: 2020.01 ~ 2022.02 (2년 2개월)
- **회사명**: 미리디 (miridih)
- **역할**: Front-end Developer
- **주요 업무**: 미리캔버스 웹 디자인 툴 프론트엔드 개발

## 성과 및 기여도

### 성능 개선

- **페이지 로딩 속도 55% 향상** (11.55s → 5.14s)
- **Lazy loading 적용을 통한 초기 이미지 로딩 용량 89% 최적화** (55MB → 6MB)
- **SEO 노출 수 170만건** 달성 (3개월간)
- **[[theming 방식 변경으로 약 6배 성능 최적화]]**
- **[[build 성능 최적화]]**

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

## 주요 프로젝트 및 업무

### 1. 템플릿 페이지 개발 (2020.08)

Bridge Page인 template page 개발과 SEO 및 Lazy Loading 구현을 진행하였다.

#### 역할 및 담당 업무

- 마케팅 유입 Bridge Page인 template page 개발 및 SEO 최적화(100%)
- SPA 구조에서 SEO 최적화를 위해 react-helmet 적용
- intersection observer를 활용한 image lazy loading 구현

#### 성과

- 고객 이탈율 0%의 페이지 개발
- 데스크탑/태블릿/모바일 반응형 지원

### 2. Workspace 개발 (2021.04 ~ 2022.02)

디자인 관리 서비스인 workspace 개발을 통해 폴더, 권한, 브랜드키트 기능을 구현하였다.

![workspace](https://camo.githubusercontent.com/66716b948d72266c914b8cdb1c6f6493bb84d7b7fb210366fcbea48ade73ff88/68747470733a2f2f747661312e73696e61696d672e636e2f6c617267652f3030386933736b4e67793167786a6171643562616e673330676f3061666232392e676966)

#### 역할 및 담당 업무

- 1명의 동료 개발자와 함께 사용자 디자인 관리 툴인 Workspace 서비스 개발 (70% 기여)
- 드라이브/폴더 상태 관리 및 CRUD 로직 구현
  - 폴더 구조, 권한 부여, 접근 제어 등 전반적 데이터 흐름 설계
- 사용자 권한 기반 기능 제약 로직 및 Wrapper Component 설계
  - 사용자 권한(Owner, Member, Viewer 등)에 따라 기능 접근을 제어하는 전역 상태 관리 로직 구현
  - Wrapper 컴포넌트를 통해 버튼 활성화, 편집 가능 여부, 기능 노출 등을 일관되게 처리
- 브랜드 키트(B2B 엔터프라이즈 기능) 개발
  - 요금제별 브랜드·컬러·폰트 제한 등 제약 로직 구현
  - 확장 가능한 구조로 설계하여 엔터프라이즈 고객 대응 가능

#### 성과

- 디자인 관리 편리성 사용자에게 제공
- 사내 템플릿 및 디자인 리소스 디자인 팀 workflow에 편의성 제공
- B2B 영업 소구 포인트 제공 (팀 관련 기능, 브랜드 키트 기능)

### 3. 메뉴 패널 React 마이그레이션 (2020.01 ~ 2022.02)

에디터 영역을 제외한 메뉴 패널을 React.js로 마이그레이션하고 교육을 진행하였다.

#### 역할 및 담당 업무

- vanilla.js로만 되어 있던 환경에 React.js 도입
- 전사 개발자 대상으로 React.js 도입기 및 기초 교육 실시

#### 성과

- 개발 생산성 향상에 기여

### 4. Chart Grid 개발 (2021.01 ~ 2021.03)

JsSpreadsheet를 포크하여 차트 그리드 개발을 진행하였다.

![chart grid](https://camo.githubusercontent.com/41c77c71c9ff22ec76c189fbe69a71fb2ad65b4b8d33ac9dbc070ead451d8f15/68747470733a2f2f747661312e73696e61696d672e636e2f6c617267652f3030386933736b4e67793167786a3965346e687467673330676f3061666833302e676966)

#### 역할 및 담당 업무

- 엑셀과 동일한 기능을 요구하여 구현
- 각각의 차트마다 data 처리가 쉽도록 adapter pattern을 활용하여, 차트 데이터 입/출력 구현
- 차트 데이터 그리드 오픈소스(JsSpreadsheet) 커스텀 및 프로덕션 적용

#### 성과

- 단기간 내의 차트 그리드 기능 개발
- 오픈소스 fork 개발을 통해 적은 인원으로 완성도 높임

### 5. 유료화 스쿼드 리더 (2021.08 ~ 2022.02)

미리캔버스의 구독 플랜(Free / Pro / Enterprise)에 따라 기능 접근을 제어하는 시스템을 설계하고,  
UI 전반에서 이를 손쉽게 반영할 수 있도록 Wrapper 컴포넌트를 구현하였다.  
또한 2명의 주니어 개발자를 리딩하며 일정 관리와 품질 개선을 병행하였다.

#### 역할 및 담당 업무

- **글로벌 상태 기반 구독 플랜 관리 로직 설계**
  - 사용자 플랜 정보(요금제, 만료일, 권한 등)를 전역 상태로 관리
  - 각 기능별 접근 제약 로직을 통합적으로 적용할 수 있는 구조 구축
- **기능 제약을 위한 UI Wrapper 컴포넌트 설계**
  - 특정 기능이 비활성화될 때의 UI 동작(블러 처리, 워터마크, 안내 문구 등)을 통일
  - Wrapper로 감싸는 것만으로 플랜 제약을 일관되게 적용 가능
- **요금제 페이지 개발 및 주니어 멘토링**
  - 결제 플로우 및 요금제 전환 UI 구현, 팀원 코드 리뷰 및 업무 분배

#### 성과

- **유료 구독 시스템 성공적 런칭 및 기능 제약 로직 내재화**
- **Wrapper 기반 구조를 통한 코드 일관성과 유지보수성 향상**
- **팀 리딩 및 협업 체계 정착**

- [요금제 페이지](https://www.miricanvas.com/ko/pricing)
- [엔터프라이즈 정식 서비스 론칭 공지](https://help.miricanvas.com/hc/ko/articles/4410765647897--%EA%B3%B5%EC%A7%80-%EB%AF%B8%EB%A6%AC%EC%BA%94%EB%B2%84%EC%8A%A4-%EC%97%94%ED%84%B0%ED%94%84%EB%9D%BC%EC%9D%B4%EC%A6%88-%EC%A0%95%EC%8B%9D-%EC%84%9C%EB%B9%84%EC%8A%A4-%EB%A1%A0%EC%B9%AD-%EC%95%88%EB%82%B4)
- [구독 개발 비하인드 기사 - 요즘IT 인터뷰](https://yozm.wishket.com/magazine/detail/2104/)

### 6. 성능 최적화 (2020.08 ~ 2020.11)

Intersection Observer를 도입하여 Lazy Loading을 적용하였다.

#### 역할 및 담당 업무

- 웹 페이지 로딩 속도 향상을 위해 Intersection Observer를 활용하여 Lazy Loading 하도록 개선
- LazyImageComponent 개발 후, img tag 활용하는 곳에 점진적 적용

#### 성과

- `/templates` 웹 페이지 초기 로딩 속도 향상: **11.55s → 5.14s**
- Image resource load: **55MB → 6MB로 축소**

### 7. SEO 개선 (2020.09 ~ 2020.11)

Node.js 기반 SEO 적용 프로젝트를 진행하였다.

#### 역할 및 담당 업무

- SEO가 적용되어 있지 않은 모든 미리캔버스 웹 페이지에 SEO 적용
- vanilla.js로 구현된 관계로 순수 구현 (Node.js, Express, Mustache)

#### 성과

- **3개월간 170만건의 노출 수** (구글 서치 기준) 달성

## 학습 및 성장

### SaaS 제품 개발 경험

- **미리캔버스**라는 웹 에디터 SaaS 제품 개발 경험
- 복잡한 UI/UX 요구사항 구현 경험

### 성능 최적화 전문성

- **Lazy Loading**, **SEO 최적화** 등 웹 성능 최적화 경험
- 대용량 이미지 처리 및 최적화 경험

### 팀 리딩 및 멘토링

- **유료화 스쿼드 리더**로서 팀 프로젝트 관리 경험

### 기술 도입 및 교육

- **React 마이그레이션** 주도 및 전사 교육 실시
- 레거시 시스템 현대화 경험

[//begin]: # "Autogenerated link references for markdown compatibility"
[theming 방식 변경으로 약 6배 성능 최적화]: <../../front-end/css/css global variables%EB%A1%9C theming %ED%95%98%EA%B8%B0.md> "css global variables로 theming 하기"
[build 성능 최적화]: ../sass-%EA%B1%B0%EB%91%AC%EB%82%B4%EA%B3%A0-css-in-js-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0.md "sass 거둬내고 css-in-js 사용하기"
[//end]: # "Autogenerated link references"
