# 위스터디(weStudy)

# 학원 관리 솔루션 Tims FE 개발

- `2019.05` ~ `2019.11` 재직
- `React.Js`, `lodash`, `scss`, `Javascript(es6)`, `react router`, `webpack`, `babel`, `eslint(standard js)`, `stylelint`, `reset css`, `material-ui` 활용하여 개발
- 컴포넌트 개발 시, `Container-Presenter 패턴`을 활용하여 개발

## 1. 고객 관리용 사내 admin FE 개발

- B2B 고객 및 영업 관리를 위한 admin FE 개발
- 개발 기간: 3주

### 1.1. 고객 가입하기 (학원 지점, 학원 브랜드, 직원)

- 고객 가입 및 고객 조회 가능
- 가입 분류에 따라 다른 가입 화면

![스크린샷 2019-10-21 오후 12.34.03](https://tva1.sinaimg.cn/large/006y8mN6gy1g85oamnn95j30ro0fv76r.jpg)

![스크린샷 2019-10-21 오후 12.34.11](https://tva1.sinaimg.cn/large/006y8mN6gy1g85oanea3uj30r80fmmzp.jpg)

### 1.2. 지점 현황

- 각 지점(고객)의 포인트 입금 내역, 포인트 차감 내역, 지점 이슈 조회 가능
- 지점명 검색 가능

![스크린샷 2019-10-21 오후 12.36.59](https://tva1.sinaimg.cn/large/006y8mN6gy1g85oc3imwuj31g30qkq53.jpg)

![스크린샷 2019-10-21 오후 12.37.05](https://tva1.sinaimg.cn/large/006y8mN6gy1g85oatyuutj31gj0qw40x.jpg)

### 1.3. 영업 현황

- 영업 사원 및 영업 에이전시의 영업 활동 조회 가능

![스크린샷 2019-10-21 오후 12.37.14](https://tva1.sinaimg.cn/large/006y8mN6gy1g85ocncr89j31gm0q50uc.jpg)

### 1.4. 입금 현황 (포인트 관리)

- 입금에 따른 포인트 추가
- 포인트 입금 및 차감, 사용 내역 조회 가능
- 세금 계산서 발행 가능

![스크린샷 2019-10-21 오후 12.37.34](https://tva1.sinaimg.cn/large/006y8mN6gy1g85oax1htwj31g70ommyw.jpg)

![스크린샷 2019-10-21 오후 12.40.36](https://tva1.sinaimg.cn/large/006y8mN6gy1g85onzfczlj31400mktd7.jpg)

![스크린샷 2019-10-21 오후 12.40.47](https://tva1.sinaimg.cn/large/006y8mN6gy1g85onu55v0j31410mhahy.jpg)

## 2. 고객용 admin 개발

- B2B 고객용 admin FE 개발
- `React.Js`, `lodash`, `scss`, `Javascript(es6)`, `mobx`, `react router`, `webpack`, `babel`, `eslint(standard js)`, `stylelint`, `rechart(차트 라이브러리)`, `reset css`, `material-ui` 활용하여 개발
- 개발기간 : 4개월

### 2.1. 회원가입 및 로그인

- `input component` 개발 - 회원 가입 시, 입력 값에 따른 변화 컴포넌트 개발 (미입력, 적합, 부적합 등)
- 로그인 및 회원가입 프로세스 구현

<img src="https://tva1.sinaimg.cn/large/006y8mN6gy1g85qtb66c1j31c80u0wh8.jpg" alt="스크린샷 2019-10-21 오후 1.00.05" style="zoom: 67%;" />

<img src="https://tva1.sinaimg.cn/large/006y8mN6gy1g85otij73xj30nb0p1dhc.jpg" alt="스크린샷 2019-10-21 오후 12.30.04" style="zoom: 67%;" />

### 2.2. 대쉬보드 개발

- 로그인 후, 첫 화면인 대쉬보드 개발
- `React chart`인 `ReChart` 라이브러리를 활용하여 차트 컴포넌트 개발
- `state` 관리를 위해 `mobx` 라이브러리 활용
- 기간 별 조회 가능

![스크린샷 2019-10-21 오후 12.25.24](https://tva1.sinaimg.cn/large/006y8mN6gy1g85qtbw9xfj30vl0npabd.jpg)

![스크린샷 2019-10-21 오후 12.25.33](https://tva1.sinaimg.cn/large/006y8mN6gy1g85qtdcgyij30ue0pl40x.jpg)

![스크린샷 2019-10-21 오후 12.25.40](https://tva1.sinaimg.cn/large/006y8mN6gy1g85ptwxtedj30vi0ongnj.jpg)

### 2.3. 기타 운영 화면 개발

- 재학생, 직원, 학부모, 행사, 수납, 상담, 강좌 등 총 15개 메뉴에 대한 화면 개발
- 전체적인 플로우 `목록(리스트) -> 입력/수정 -> 상세`로 구성
- 다른 메뉴와 컴포넌트 디자인 동일
- `상담 관리 기능`을 예로 설명

##### 1. 상담 리스트

- 기간 조회, 소팅(필터), 리스트 개수 선택(10, 30, 50개), 이름 검색 가능
- `table`, `pagination`, `검색`, `필터` 컴포넌트 개발

![스크린샷 2019-10-21 오후 12.19.04](https://tva1.sinaimg.cn/large/006y8mN6gy1g85qd4ufjvj30uy0jz76q.jpg)

![스크린샷 2019-10-21 오후 2.00.51](https://tva1.sinaimg.cn/large/006y8mN6gy1g85qjgwujnj312k0u044y.jpg)

![Screenshot 2019-11-13 at 15.57.33](https://tva1.sinaimg.cn/large/006y8mN6gy1g8wf9k99oyj30sv0oo761.jpg)

##### 2. 상담 상세

- 리스트 item 클릭 시, 상세 화면으로 이동
- 상담 내용에 대한 댓글 및 대댓글 작성 가능

![스크린샷 2019-10-21 오후 2.06.45](https://tva1.sinaimg.cn/large/006y8mN6gy1g85qp8l13jj31460u0q7n.jpg)

##### 3. 상담 등록/수정

- 상담 관련 정보 입력 및 수정

![스크린샷 2019-10-21 오후 1.59.24](https://tva1.sinaimg.cn/large/006y8mN6gy1g85qtcxawpj312m0u041j.jpg)

![스크린샷 2019-10-21 오후 2.05.46](https://tva1.sinaimg.cn/large/006y8mN6gy1g85qoba9kaj311u0u00w1.jpg)
