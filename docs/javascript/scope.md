# scope

> scope(스코프)는 '유효 범위'를 의미하며, javascript 뿐만 아니라 모든 프로그래밍 언어의 기본적인 개념이기도 합니다.
> 이번 article에서는 javascript의 scope를 정리해봅니다.

## scope란?

- 유효 범위
- 참조 대상 식별자(identifier)[^1]를 찾아 내기 위한 규칙입니다. javascript는 이 규칙대로 식별자를 찾습니다.

[^1]: sfdsadf

```javascript
var a = "global";
function foo() {
  var a = "local";
  console.log(a);
}
console.log(a); // global
foo(); // local
```
