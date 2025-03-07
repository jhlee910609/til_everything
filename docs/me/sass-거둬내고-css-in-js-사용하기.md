# sass 거둬내고 css-in-js 사용하기

> sass-loader를 점진적으로 거둬내기에 앞서 문제점과 css-in-js의 특징을 알아 봤습니다.

## sass-loader 문제점

> webpack의 build/rebuild 속도가 너무 느린데, 느린 build 속도의 대부분은 sass-loader에서 병목이 발생하였습니다!

`sass-loader`가 느린 이유는 다음과 같습니다.

- `sass-loader`가 트랜스파일한 SASS 파일은 캐시되지 않습니다.
- 여기서 `CSS Modules`를 활용하여 각각의 component에서 Import하여 sass를 사용했을 경우, stylesheet가 모두 모듈화되어 각각 고유한 sass 프로세스가 되고, 빌드 환경에 따라 그 속도는 더 최악이 될 수 있다고 합니다.😢
- 실제로 한 회사는 `sass`와 `sass-loader`를 제거하고, PostCss와 CSSNext를 도입하여 build 시간을 50%나 줄였다고 합니다.[^1]

## css-in-js를 도입하자!

우선 sass-loader가 태생이 매우 느린 build performance를 보이고 있었기 때문에 이를 제거해나갈 고민을 하였습니다. 여러 방식을 찾아보다가 `css-in-js`를 도입하기로 결정했습니다. 그 결정의 이유는 다음와 같습니다.

- 무엇보다 거대해진 sass 파일들을 최대한 적게 쓰고 싶었습니다. sass 속성 하나를 바꿔도 rebuild time이 10초 이상 걸리기도 했고, memory leak이 빈번하게 발생하기 때문에 큰 부채라고 생각하였습니다.
- architeching 없이 작성된 sass, css module 활용도 안되어 있어 classname 충돌 및 scope 관리가 안되어 있었습니다.
- css-in-js의 큰 장점인하나의 js파일에서 스타일까지 다룰 수 있어 개발 생산성이 높아질 수 있을 것을 기대했습니다.
  - 동적 코딩 수월

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

- browser에 따라 다른 속성들에 대한 prefix를 기본으로 제공해줍니다. 따라서 개발자는 `transition`만 선언해도 자동으로 vendor prefix를 붙혀줍니다.

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

`pseudo classes`, `elements`, `media query`, `keyframe animations`도 지원합니다.

### css-in-js trade-offs

> 은탄환은 없습니다. `css-in-js` 방식도 몇 가지 trade-off가 있습니다.

1. `emotionjs`, `styled-component`와 같은 js library에 종속적이기 때문에 js가 구동되지 않는 환경에서는 스타일을 사용할 수 없습니다.
2. style이 두 번 parsing 됩니다. 첫 번째는 css-in-js library에 의해, 두 번째는 browser에 의해 parsing 됩니다.
3. 보통 web page가 loading 될 때, browser는 CSS를 읽고 적용합니다. 하지만 css-in-js를 사용한다면, browser는 동적으로 CSS style tag를 생성하고, webpage에 적용합니다. 따라서 style을 동적으로 읽고, 생성하는 것에 동작 시간이 소요됩니다.
4. [css-in-js에 대한 부정적인 글.](https://dev.to/srmagura/why-were-breaking-up-wiht-css-in-js-4g9b)

### zero-runtime css-in-js

위와 같은 몇 가지 trade-off가 있고, 특히 3번 같은 경우를 runtime에 style이 결정되어, css-in-js 방식 중 runtime 방식이라고 일컫습니다.
runtime 방식은 3번에서 말한 것처럼 동적으로 style이 결정됨에 따라 render가 빈번하게 일어나는 상황일 경우, 성능 저하의 가능성이 큼을 예상해볼 수 있는데요.

이를 개선한 것이 `zero runtime css-in-js` 입니다. 기존 방식 중에 css module import 방식이 zero runtime 방식입니다. zero-runtime css-in-js 방식은 build 시점에 style을 생성하는데요. zero-runtime css-in-js 방식으로 개발된 대표적인 library linaria의 [linaria/HOW_IT_WORKS.md](https://github.com/callstack/linaria/blob/master/docs/HOW_IT_WORKS.md)를 보면 그 원리를 자세히 알 수 있습니다. 간단히 동적으로 선언된 style들을 build 시점에 babel-loader와 plugin을 활용하여 `css global variable`로 변수 할당을 통해 CSS로 추출됩니다. 따라서, CSS 파일 크기는 조금 커질 수 있지만, 한 번 style load 후, 동적인 연산이 적게 되는 이점이 있습니다.

##### 참고문서

- [Better CSS-in-JS performance with zero runtime - 🙋Get Help - Frontity Community Forum](https://community.frontity.org/t/better-css-in-js-performance-with-zero-runtime/3586)
- [Comparing the top zero-runtime CSS-in-JS libraries - LogRocket Blog](https://blog.logrocket.com/comparing-the-top-zero-runtime-css-in-js-libraries/)
- [CSS-in-JS, 무엇이 다른가요? - SOSOLOG](https://so-so.dev/web/css-in-js-whats-the-defference/#css-in-js)
- [Why you should definitely learn how to use CSS-in-JS - Jxnblk](https://jxnblk.com/blog/why-you-should-learn-css-in-js/)

[^1]: [Webpack — Build Performance Pitfall of using SASS with CSS Modules](https://medium.com/jsdownunder/webpack-build-performance-pitfall-of-using-sass-with-css-modules-ba32f89efdcb)
[^2]: [External CSS vs inline style performance difference?](https://newbedev.com/external-css-vs-inline-style-performance-difference)
