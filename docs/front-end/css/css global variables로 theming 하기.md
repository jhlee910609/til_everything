# css global variables로 theming 하기

> 회사 업무 중, scss 파일로 인해 build performance 저하 및 bundle 결과물 용량이 커지는 문제가 발생하고 있었습니다.
> 이를 해결하고자 찾아본 방법 중 하나입니다.

## 기존 방식의 문제점

### 1. 파일 교체 방식의 theming

- 파일 교체 방식으로 인해 css module[^1]를 사용할 수 없습니다.
  - theme가 build timing에 결정됩니다. 따라서, 이미 theme가 결정된 결과물을 serving 받은 사용자는 실시간으로 theme를 바꿀 수 없습니다.

### 2. scss file import 역구조

- scss파일들이 최상위 파일에 전부 import하여 scss파일을 관리하고 있었습니다.
- 그로 인해 build/rebuild 속도 저하 및 스타일 파일 용량이 비대한 느낌이었습니다.

## 해결책

> 회사 서비스는 이미 운영되고 있었기 때문에, 급진적인 변화를 시도하기에는 다수 무리가 있었다고 판단하였습니다.
> 점진적으로, 저희 회사의 서비스 구조에 맞는 방식 중 시도해볼 수 있는 것을 추리게 되었습니다.
> 그래서 고민해본 것이 `css global variables`를 활용한 점진적 개선입니다.

### css global variables[^2]

- `var()`를 사용하여 값(value) 대신 변수를 넣는 css 함수입니다. 이는 w3c 공식 문서[^3]에 소개되어 있습니다.
- 보통 constants style value들을 global하게 선언해두고 사용합니다.
- 위 특성들을 활용하여, theming을 하기도 합니다.

## 예제

> 직접 예제를 만들어 보았습니다.

- [참고 예제](https://codesandbox.io/s/react-and-scss-forked-m0854?file=/src/components/Itemview/ItemView.jsx:0-31)

[^1]: [css-modules/css-modules: Documentation about css-modules](https://github.com/css-modules/css-modules)
[^2]: [CSS Variables - The var() function](https://www.w3schools.com/css/css3_variables.asp)
[^3]: [CSS Functions Reference](https://www.w3schools.com/cssref/css_functions.asp)
