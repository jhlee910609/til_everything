# scope

> scope(스코프)는 '유효 범위'를 의미하며, javascript 뿐만 아니라 모든 프로그래밍 언어의 기본적인 개념이기도 합니다.
> 이번 article에서는 javascript의 scope를 정리해봅니다.

## scope란?

scope는 참조 대상 식별자(identifier)[^1]를 찾아 내기 위한 규칙입니다. javascript는 이 규칙대로 식별자를 찾습니다.
아래 예시를 보면 변수 `a`는 global scope와 foo 함수 내부 두 곳에서 같은 변수명으로 사용하고 있습니다. 그럼에도 우리가 의도한대로 console에 `a`에 각각 할당된 local, global 순으로 문자열이 출력되게 되는데요. 이런 상황 또한, console에 찍어야할 `a`가 어떤 `a`인지 결정되게 됩니다.

```javascript
var a = "global";
function foo() {
  var a = "local";
  console.log(a);
}
console.log(a); // global
foo(); // local
```

## scope의 구분

javascript의 scope는 global scope(전역 스코프)와 local scope(지역 스코프)로 나뉩니다.

### 1. global scope(전역 스코프)

- 코드 어디에서든지 참조할 수 있습니다.
- global scope에 할당된 변수는 global variable(전역 변수)가 됩니다.

### 2. local scope(function-level scope, 지역 스코프)

- 함수 코드 블록이 만든 scope로 함수 자신과 하위 함수에서만 참조할 수 있습니다. (상위 scope에서는 참조 불가능합니다.)
- local scope에 할당된 변수는 local variable(지역 변수)가 됩니다.

## javascript만의 scope 특징

대부분의 programming language는 block-level scope[^2]를 따릅니다.

[^1]: 변수, 함수의 이름과 같이 어떤 대상을 다른 대상과 구분하여 식별할 수 있는 유일한 이름
[^2]: 코드 블록({...}) 내에서 유효한 스코프를 의미
