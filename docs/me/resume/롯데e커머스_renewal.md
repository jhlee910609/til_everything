# 롯데e커머스 (롯데ON)
> **Frontend Developer** | 2022.03 ~ 현재 (3년 4개월)
>
> "대규모 사용자 환경의 **프론트엔드 성능 최적화**와 **레거시 개선**을 주도하며, 비즈니스 성장을 견인하는 개발자입니다."

## 🏆 핵심 성과 (Key Achievements)
*   **Performance**: 불필요한 의존성 제거 및 트리쉐이킹으로 **Bundle Size 53% 감소** (64MB → 29MB).
*   **Optimization**: 검색 필터 렌더링 로직 개선으로 **초기 로딩 속도 7% 단축** (UX 개선).
*   **Business**: 온앤더럭셔리/패션 등 **신규 버티컬 서비스 론칭**을 통한 매출 채널 확장 리드.

## 🛠 Technical Skills
![Vue.js](https://img.shields.io/badge/vuejs-%2335495e.svg?style=for-the-badge&logo=vuedotjs&logoColor=%234FC08D) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white) ![SCSS](https://img.shields.io/badge/SCSS-hotpink.svg?style=for-the-badge&logo=SASS&logoColor=white)

---

## 📂 주요 프로젝트 (Key Projects)

### 1. 버티컬 신규 서비스 개발 & 론칭
*2022.10 ~ 2023.05*
> 롯데ON 내의 전문관(온앤더럭셔리, 온앤더패션 등)을 신규 구축하여 타겟 유저층을 확장한 프로젝트입니다.

**Challenges & Actions (과제 및 해결):**
*   **Scalable UI Architecture**: 다양한 버티컬(럭셔리, 패션, 키즈)에 유연하게 대응할 수 있는 **반응형 웹 템플릿** 설계.
*   **Component Reusability**: 각 전문관별로 상이한 기획 요건을 공통 컴포넌트와 확장 패턴으로 해결하여 개발 효율성 증대.

**Results (성과):**
*   **Business Growth**: 신규 매출 파이프라인 확보 및 플랫폼 전반의 트래픽 증대 기여.
*   **Screenshots**:
    <div align="center">
      <img src="../../../attachments/vertical/image.png" width="45%" alt="버티컬 서비스 1" style="margin: 2px;">
      <img src="../../../attachments/vertical/2.png" width="45%" alt="버티컬 서비스 2" style="margin: 2px;">
    </div>
    <div align="center">
      <img src="../../../attachments/vertical/3.png" width="45%" alt="버티컬 서비스 3" style="margin: 2px;">
      <img src="../../../attachments/vertical/4.png" width="45%" alt="버티컬 서비스 4" style="margin: 2px;">
    </div>

### 2. Frontend Performance Optimization
*2023.06 ~ 진행중*
> CSR 환경에서의 무거운 번들 사이즈와 렌더링 지연 문제를 해결하여 사용자 경험(UX)을 개선했습니다.

**Problem (문제정의):**
*   거대한 레거시 코드와 무분별한 라이브러리 사용으로 인해 초기 로딩 속도가 저하됨.
*   검색 필터 조작 시 불필요한 리렌더링으로 인터렉션 지연 발생.

**Action (해결방안):**
*   **Bundle Optimization**: Moment.js → Day.js 교체, 미사용 코드(Dead Code) 제거, Dynamic Import 적용.
*   **Rendering Optimization**: 검색 필터 컴포넌트의 가시성 제어를 `display: none`에서 **DOM Attach/Detach** 방식으로 변경하고, 불필요한 리렌더링 방지.
*   **Network Optimization**: `AbortController`를 도입하여 비동기 검색 요청의 Race Condition 해결 및 리소스 낭비 방지.

**Result (결과):**
*   **Bundle Size Reduction**: PC **53%** (64MB → 29MB), Mobile **24%** (40MB → 28MB) 감소.
*   **Speed Up**: 검색 필터 렌더링 시간 **7% 단축** (1841ms → 1711ms).

### 3. Legacy Improvement & DX (Developer Experience)
*상시 진행*
> 개발 생산성을 저해하는 레거시 환경을 개선하고, AI 도구를 도입하여 팀 전체의 효율을 높였습니다.

**Activities (주요 활동):**
*   **Legacy Cleanup**: 불필요한 페이지 및 Dynamic Import 컴포넌트를 PO와 협의하여 과감하게 정리.
*   **AI Integration**: **Cursor AI**를 팀 내 도입하고 공용 Rule을 설정하여 보일러플레이트 코드 작성 시간 단축 및 리뷰 효율화.
*   **Internal Tool**: 기획/개발 효율성을 높이는 전사 전시 관리 대시보드(Bigbro) 개발.

**Result (결과):**
*   **Maintenance**: 사내 공용 Node Module 용량 **32% 절감**으로 CI/CD 빌드 시간 및 비용 절약.
*   **Culture**: AI 기반의 모던 개발 환경 구축 및 팀 내 전파.

---

### [Link]
- [Bundle Size 최적화로 50% 감소 달성기](../../front-end/bundler/bundle-size-%EC%B5%9C%EC%A0%81%ED%99%94-50%ED%8D%BC%EC%84%BC%ED%8A%B8-%EA%B0%90%EC%86%8C-%EB%8B%AC%EC%84%B1%EA%B8%B0.md)
