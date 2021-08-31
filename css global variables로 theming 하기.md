# css global variables로 theming 하기

> 회사 업무 중, scss 파일로 인해 build performance 저하 및 bundle 결과물 용량이 커지는 문제가 발생하고 있었습니다.
> 이를 해결하고자 찾아본 방법 중 하나입니다.

# 기존 방식의 문제점

### 1. 파일 교체 방식의 theming

- 파일 교체 방식으로 인해 css module[^1]를 사용할 수 없습니다.
  - theme가 build timing에 결정됩니다. 따라서, 이미 theming이 결정된 bundle.js serving 받은 사용자는 실시간으로 theme를 바꿀 수 없습니다.

### 2. scss file import 역구조

-

## css global variables

- `var()`를 사용하여 값(value) 대신 변수를 넣는 css 함수입니다.
- 보통 constants style value들을 global하게 선언해두고 사용합니다.
- 위 특성들을 활용하여, theming을 하기도 합니다.

## example

- [참고 예제](https://codesandbox.io/s/react-and-scss-forked-m0854?file=/src/components/Itemview/ItemView.jsx:0-31)

[^1]: [css-modules/css-modules: Documentation about css-modules](https://github.com/css-modules/css-modules)
