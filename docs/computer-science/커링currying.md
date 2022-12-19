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
function _curryr(fn) {
  return function (a, b) {
    return arguments.length === 2
      ? fn(a, b)
      : function (b) {
          // 인자가 1개씩 들어올때는, 인자의 순서를 바꿔준다. 그게 외부에서 이 함수를 쓸때 목적에 맞다.
          return fn(b, a);
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
// 그런데 sub_10은 5 - 10의 결과로 나와야할 것 같다.
// 그래서 만든 게 상위 _curryr 함수

const sub = _curryr((a, b) => a - b);
const sub_10 = sub(10);
sub(10)(5); // result: 5
// 표현에 맞는 결과를 준다.
sub_10(5); // result: -5

// 2. _get 만들어 좀 더 간단하게 하기
function _get(obj, key) {
  return obj == null ? undefined : obj[key];
}
```
