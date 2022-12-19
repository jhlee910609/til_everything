# 커링(currying)

```javascript
function _curry(fn) {
  return function (a) {
    return function (b) {
      return fn(a, b);
    };
  };
}

const add = _curry((a, b) => {
  return a + b;
});

const add_10 = add(10);
const add_5 = add_10(5); // result: 15
add(10)(5); // result: 15
```
