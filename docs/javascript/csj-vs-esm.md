# csj vs esm

> javascript의 대표적인 module 방식 cjs와 esm에 대해 알아봅니다.

## cjs와 esm

### cjs

- `require('./module/path')` 과 `export modules` keyword를 활용합니다.
- named export와 default export 모두 사용 가능합니다.
- 동기적으로 동작합니다. 따라서, `Promise`를 return 하지 않습니다. `require` 키워드는 disk로부터

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
- [Node Modules at War: Why CommonJS and ES Modules Can’t Get Along | by Dan Fabulich](https://redfin.engineering/node-modules-at-war-why-commonjs-and-es-modules-cant-get-along-9617135eeca1)
- [16. Modules](https://exploringjs.com/es6/ch_modules.html#sec_overview-modules)
- [The state of JavaScript modules. Recently, there was a lot of fuss on… | by Johannes Ewald | webpack | Medium](https://medium.com/webpack/the-state-of-javascript-modules-4636d1774358)
- https://hackernoon.com/node-js-tc-39-and-modules-a1118aecf95e
