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

## javascript만의 scope 특징

대부분의 programming language는 block-level scope[^2]를 따릅니다.
하지만 javascript는 function-level scope를 따릅니다. 물론, ES6 문법의 let을 활용한다면 block-level scope를 사용할 수 있습니다.

```javascript
var a = "global a";
{
  var a = "local a"; // global variable a의 값에 대입됩니다.
}
let b = "global b";
{
  let b = "local b";
}
console.log(a); // local a
console.log(b); // global b
```

## scope의 구분

javascript의 scope는 global scope(전역 스코프)와 local scope(지역 스코프)로 나뉩니다.

### 1. global scope(전역 스코프)

- 코드 어디에서든지 참조할 수 있습니다.
- var keyword로 선언한 global variable는 global object[^3]의 property가 됩니다.
- global scope에 할당된 변수는 global variable(전역 변수)가 됩니다.

  ```javascript
  var global = "global";

  function foo() {
    var local = "local";
    console.log(global); // global
    console.log(local); // local
  }

  foo();

  console.log(global); // global
  console.log(local); // Error: ReferenceError: Can't find variable: local
  ```

### 2. local scope(function-level scope, 지역 스코프)

함수 코드 블록이 만든 scope로 함수 자신과 하위 함수에서만 참조할 수 있습니다. (상위 scope에서는 참조 불가능합니다.)
local scope에 할당된 변수는 local variable(지역 변수)가 됩니다.
아래 예시 코드들은 javascript의 local scope 특징을 활용한 예시입니다.

- local scope 내부에 할당된 변수는 상위 scope에서 참조 불가능합니다.

```javascript
var a = "a";
(() => {
  var b = "b";
})();

console.log(a); // a
console.log(b); // Error: ReferenceError: Can't find variable: b
```

- local scope에 같은 이름의 식별자가 있더라도 global scope에 영향을 주지 않습니다.

```javascript
var a = "a";
(() => {
  console.log(a); // undefined가 출력됩니다. local variable a가 hoisting 되기 때문입니다. 만약 local variable a가 아닌 b라는 이름으로 사용했다면 global variable a가 찍히게 됩니다.
  var a = "b"; // 익명 함수 scope 내의 local varibale로 global variable a 값에 변화를 주지 않습니다.
})();

console.log(a); // a
```

```javascript
var a = 10;

function foo() {
  var a = 5;

  function bar() {
    // 내부함수로 상위 함수의 지역 변수에 접근(참조) 가능합니다.
    a = 100;
    console.log(a); // 100
  }
  bar();
}

console.log(a); // a
foo(); // 100
```

### 3. lexical scope(static scope, 정적 스코프)

programming language에서 함수의 상위 스코프를 결정하는 방식은 아래와 같은 두 가지입니다.

1. dynamic scope - 함수를 어디서 호출하였는지에 따라 상위 스코프가 결정됩니다.
2. lexical scope(static scope) - 함수 선언 위치에 따라 상위 스코프가 결정됩니다.

javascript를 비롯한 대부분의 programming language는 lexical scope를 따릅니다.
따라서, 함수 선언 시점이 상위 스코프를 결정하는 데에 영향을 줍니다.

```javascript
var x = 1;

function foo() {
  var x = 10;
  bar();
}

function bar() {
  // bar는 global scope 내에 선언됐습니다.
  console.log(x);
}

foo(); // 1
bar(); // 1
```

## 그 밖의 특이점

### 1. implicit global

할당 scope 위치와 상관 없이 var keyword(변수 선언 keyword)를 사용하지 않고, 값을 할당했을때 global object의 property로 할당됩니다.

```javascript
var x = 10;

function foo() {
  y = 20;
  bar = function () {
    console.log("bar");
  };
  console.log(x + y);
}

foo(); // 30
console.log(y); // 20
console.log(bar()); // bar
```

### 2. global variable 지양하기

- object 활용하기 - object에 감싸서 명시적으로 사용
- 즉시실행함수 활용하기 - 함수 활용을 통해 scope를 좁혀 사용

```javascript
// 한 번 실행되고, 버려진다.
(function () {
  var a = "a";
  console.log(a);
})();

console.log(a); // Error: ReferenceError: Can't find variable: a
```

[^1]: 변수, 함수의 이름과 같이 어떤 대상을 다른 대상과 구분하여 식별할 수 있는 유일한 이름
[^2]: 코드 블록({...}) 내에서 유효한 스코프를 의미
[^3]: Browser - `window`, node.js - `global`
