# bundle size 줄이기

> serving 되는 bundle size를 줄여보자

## bundle이란 무엇인가

- 라이브러리와 프레임워크의 발달로 프론트엔드 개발이 하나의 거대한 APP 형태가 되면서 과거의 페이지 단위의 개발과는 다르게 의존성 관리가 복잡해짐
- asset, javascript module, css 등 여러 resource의 의존성 관리의 필요성이 생김 -> 이 과정에서 webpack, rollup과 같은 bundler가 등장함
- 이 bundler가 여러 의존성을 하나의 js(보통 main.js)로 묶어 주는데 이것을 `bundle`라고 보통 부름

## bundle 크기 줄이기

- bundler를 구성할 때, 보통 기본으로 제공한 cli를 활용한다면 아래의 대부분의 기능들은 작동할 것임

### dynamic import

- 모든 javascript module이 build 시점에 필요한지에 대한 의문에서 출발
- 크기가 큰 javascript module에 대해서 runtime에서 필요할 때, 불러올 수 있도록 코딩
- 일반적인 import 방식은 아래와 같음

```javascript
import module from "./module.js";

module.xxxx();
```

- dynamic import를 적용 후에는 아래와 같음

```javascript
import('module.js')
  .then((module) => {
    ...
  });
```

###
