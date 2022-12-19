# reduce

```javascript
// reduce 만들기
function _reduce(list, iter, memo) {
  if (arguments.length == 2) {
    memo = list[0];
    list = list.slice(1); // Array의 메서드. 따라서 Array 자료구조에서만 사용할 수 있는 메서드가 되어버림. 그러면 안됨...!
  }
  _each(list, (val) => {
    memo = iter(memo, val);
  });
  return memo;
}
```
