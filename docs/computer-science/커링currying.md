# 커링(currying)

```javascript
function _curry(fn) {
  return function (a, b) {
    return arguments.length === 2
      ? fn(a, b)
      : function (b) {
          return fn(a, b);
        };
  };
}

const add = _curry((a, b) => a + b);

const add_10 = add(10);
const add_5 = add_10(5); // result: 15
add(10)(5); // result: 15

const sub = _curry((a, b) => a - b);
const sub_10 = sub(10);
sub_10(5); // result: 5
// 그런데
```
