# sass 거둬내고 css-in-js 사용하기

> sass-loader를 점진적으로 거둬내기에 앞서 문제점과 css-in-js의 특징을 알아 봤습니다.

## sass-loader 문제점

> webpack의 build/rebuild 속도가 너무 느린데, 느린 build 속도의 대부분은 sass-loader에서 병목이 발생하였습니다!

`sass-loader`가 느린 이유는 다음과 같습니다.

- `sass-loader`가 트랜스파일한 SASS 파일은 캐시되지 않습니다.
- 여기서 `CSS Modules`를 활용하여 각각의 component에서 Import하여 sass를 사용했을 경우, stylesheet가 모두 모듈화되어 각각 고유한 sass 프로세스가 되고, 빌드 환경에 따라 그 속도는 더 최악이 될 수 있다고 합니다...😢
- 실제로 한 회사는 sass와 sass-loader를 제거하고, PostCss와 CSSNext를 도입하여 build 시간을 50%나 줄였다고 합니다.[^1]

## css-in-js

별도의 style file 형식이 아닌 javascript 코드 내에서 css를 작성하는 방식입니다.
기존 css 관리 방식의 어려움을 느껴 고안된 방식이라고 합니다.
`styled-component`, `emotion` 등 다양한 css-in-js 라이브러리가 존재합니다.

### css-in-js의 공통적인 특징

#### 1. scoped css

모든 css-in-js 라이브러리들은 `css module`처럼 고유한 css classname을 생성합니다.
따라서, classname 충돌이나 naming에 크게 신경쓰지 않아도 됩니다.
component 기반의 개발 방식에서는 굉장히 중요한 특징입니다.

#### 2. vendor prefix 자동화를 지원합니다.

- 브라우저에 따라 다른 속성들에 대한 prefix를 기본으로 제공해줍니다. 따라서 개발자는 `transition`만

```css
/* WebKit browsers: Chrome, Safari, most iOS browsers, etc */
-webkit-transition: all 1s ease;

/* Firefox */
-moz-transition: all 1s ease;

/* Internet Explorer and Microsoft Edge */
-ms-transition: all 1s ease;

/* old pre-WebKit versions of Opera */
-o-transition: all 1s ease;

/* standard */
transition: all 1s ease;
```

#### 3. inline-style을 사용하지 않습니다.

css에 비해 javascript inline styles는 성능이 좋지 않습니다.[^2]
external css file을 가지고 있을 경우, browser에 캐싱이 가능하지만 각각의 요소에 스타일을 입히는 inline-style의 경우, 캐싱이 불가능하여 성능에 부정적인 영향을 줍니다.

#### 4. css의 모든 기능을 지원합니다.

- pseudo classes and elements
- media query
- keyframe animations

### css-in-js tradeoffs

은탄환은 없습니다. css-in-js 방식도 trade-offs가 있습니다.

zero runtime vs build? vs nearly zero runtime

https://community.frontity.org/t/better-css-in-js-performance-with-zero-runtime/3586

https://blog.logrocket.com/comparing-the-top-zero-runtime-css-in-js-libraries/
https://so-so.dev/web/css-in-js-whats-the-defference/#css-in-js
https://github.com/seek-oss/vanilla-extract#style
https://stitches.dev

[^1]: [Webpack — Build Performance Pitfall of using SASS with CSS Modules | by Will Po | jsdownunder | Medium](https://medium.com/jsdownunder/webpack-build-performance-pitfall-of-using-sass-with-css-modules-ba32f89efdcb)
[^2]: [External CSS vs inline style performance difference? | NewbedevMenu](https://newbedev.com/external-css-vs-inline-style-performance-difference)
