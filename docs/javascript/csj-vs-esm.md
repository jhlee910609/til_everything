# csj vs esm

> javascript의 대표적인 module 방식 cjs와 esm에 대해 알아봅니다.

## cjs와 esm

### cjs

- `require('./module/path')` 과 `export modules` keyword를 활용합니다.
- named export와 default export 모두 사용 가능합니다.

```javascript
// @filename: util.cjs
module.exports.sum = (x, y) => x + y;

// @filename: main.cjs
const { sum } = require("./util.cjs");
console.log(sum(1, 2)); // 3
```

## cjs와 esm은 완벽히 다르다.

표면적으로는 두 모듈 방식이 매우 비슷해보이지만, 구현은 매우 다릅니다.

## cjs에서 esm은 서로 호출하여 사용할 수 있지만, 이는 매우 번거롭습니다.

###### 참고

- [ES modules: A cartoon deep-dive - Mozilla Hacks - the Web developer blog](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)