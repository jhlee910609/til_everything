# sass 거둬내고 css-in-js 사용하기

> sass-loader를 점진적으로 거둬내기에 앞서 문제점과 css-in-js의 특징을 알아 봤습니다.

## sass-loader 문제점

> build/rebuild 속도가 너무 느린데, 느린 build 속도의 대부분은 sass-loader였다!

- `sass-loader`가 트랜스파일한 SASS 파일은 캐시되지 않는다.
- 여기서 `CSS Modules`를 활용하여 각각의 component에서 Import하여 sass를 사용했을 경우, stylesheet가 모두 모듈화되어 각각 고유한 sass 프로세스가 되고, 빌드 환경에 따라 그 속도는 더 최악이다...😢

- [Webpack — Build Performance Pitfall of using SASS with CSS Modules | by Will Po | jsdownunder | Medium](https://medium.com/jsdownunder/webpack-build-performance-pitfall-of-using-sass-with-css-modules-ba32f89efdcb)

## css-in-js

https://community.frontity.org/t/better-css-in-js-performance-with-zero-runtime/3586

https://blog.logrocket.com/comparing-the-top-zero-runtime-css-in-js-libraries/
https://so-so.dev/web/css-in-js-whats-the-defference/#css-in-js
https://github.com/seek-oss/vanilla-extract#style
https://stitches.dev
