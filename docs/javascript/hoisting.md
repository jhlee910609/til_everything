# Hoisting (호이스팅)

> JavaScript의 독특한 동작 방식인 호이스팅(Hoisting)에 대해 알아봅니다. 호이스팅을 "코드를 끌어올린다"고 이해하기보다는, "JavaScript 엔진이 코드를 어떻게 읽고 준비하는가"의 관점에서 이해하는 것이 더 정확합니다.

## 호이스팅이란?

> 호이스팅은 **"JavaScript 엔진이 코드를 실행하기 전, 변수와 함수의 선언을 해당 스코프의 최상단으로 끌어올린 것처럼 동작하는 현상"** 을 말합니다. 실제로 코드가 물리적으로 이동하는 것은 아니며, [실행 컨텍스트(Execution Context)](./execution-context.md)의 **생성 단계(Creation Phase)** 에서 일어나는 일입니다.

실행 컨텍스트가 생성될 때, JavaScript 엔진은 코드를 두 번 훑어봅니다.

1.  **생성 단계 (준비 단계):** 변수와 함수 선언을 스캔하여 메모리에 공간을 확보합니다. 이것이 바로 호이스팅이 발생하는 시점입니다.
2.  **실행 단계:** 코드를 한 줄씩 순차적으로 실행하며 값을 할당하고 함수를 호출합니다.

이러한 2단계 과정 때문에 선언이 코드상 위치보다 "앞서" 처리되는 것처럼 보이는 것입니다.

## 변수 호이스팅

`var`, `let`, `const` 키워드는 모두 호이스팅되지만, 동작 방식에 중요한 차이가 있습니다.

### `var`의 호이스팅

`var`로 선언된 변수는 생성 단계에서 **선언과 동시에 `undefined`로 초기화**됩니다. 따라서 변수를 선언하기 전에 호출해도 에러가 발생하지 않고 `undefined`를 반환합니다.

```javascript
console.log(myVar); // undefined (에러가 아님)

var myVar = 'Hello, Hoisting!';

console.log(myVar); // 'Hello, Hoisting!'
```

**엔진의 관점:**

```javascript
// 1. 생성 단계
var myVar = undefined;

// 2. 실행 단계
console.log(myVar); // undefined
myVar = 'Hello, Hoisting!';
console.log(myVar); // 'Hello, Hoisting!'
```

### `let`과 `const`의 호이스팅

> `let`과 `const`도 호이스팅이 발생합니다. 하지만 `var`와 달리, **선언만 될 뿐 초기화되지 않습니다.**

이때 선언과 초기화 사이의 간극을 **TDZ(Temporal Dead Zone, 일시적 사각지대)** 라고 부릅니다. TDZ에 있는 변수에 접근하려고 하면 `ReferenceError`가 발생합니다.

```javascript
console.log(myLet); // ReferenceError: Cannot access 'myLet' before initialization

let myLet = 'No, Hoisting!';
```

-   **호이스팅 O:** `myLet` 선언은 스코프의 시작부터 알려집니다.
-   **초기화 X:** `let myLet` 코드 라인이 실행되기 전까지는 초기화되지 않은 상태로 남아있습니다.
-   **TDZ:** 스코프의 시작부터 `let myLet` 선언 라인까지의 구간입니다.

이러한 동작 방식은 `var`의 비직관적인 동작을 막고, 코드를 더 예측 가능하게 만들어줍니다.

## 함수 호이스팅

함수도 호이스팅되지만, 함수를 어떻게 선언했는지에 따라 다르게 동작합니다.

### 함수 선언문 (Function Declaration)

> 함수 선언문은 **선언과 구현(함수 몸체)이 통째로 호이스팅**됩니다.

따라서 함수가 코드상 어디에 있든 상관없이 호출할 수 있습니다.

```javascript
sayHello(); // "Hello!"

function sayHello() {
  console.log("Hello!");
}
```

**엔진의 관점:**

```javascript
// 1. 생성 단계
function sayHello() {
  console.log("Hello!");
}

// 2. 실행 단계
sayHello(); // "Hello!"
```

### 함수 표현식 (Function Expression)

> 함수 표현식은 변수 호이스팅 규칙을 그대로 따릅니다. 즉, 변수의 선언부만 호이스팅되고, 함수를 할당하는 부분은 실행 단계에서 처리됩니다.

```javascript
// var를 사용한 경우
sayHi(); // TypeError: sayHi is not a function

var sayHi = function() {
  console.log("Hi!");
};
```

위 코드에서 `sayHi`는 `var`로 선언되었으므로, 호이스팅되어 `undefined`로 초기화됩니다. `undefined`는 함수가 아니므로 호출하려고 하면 `TypeError`가 발생합니다.

```javascript
// let을 사용한 경우
sayBye(); // ReferenceError: Cannot access 'sayBye' before initialization

let sayBye = function() {
  console.log("Bye!");
};
```

`let`을 사용하면 `sayBye`는 TDZ에 있게 되므로, 선언 전에 호출하면 `ReferenceError`가 발생합니다.

## 호이스팅 우선순위

> 같은 이름의 변수와 함수가 있을 경우, **함수 선언문이 변수 선언보다 우선**하여 호이스팅됩니다.

1.  **함수 선언문**이 가장 먼저 호이스팅됩니다.
2.  그다음 **변수 선언**이 호이스팅됩니다.

```javascript
console.log(typeof myValue); // "function"

var myValue = 'variable';

function myValue() {
  console.log('function');
}

console.log(typeof myValue); // "string"
```

**엔진의 관점:**

```javascript
// 1. 생성 단계
// 함수 선언이 변수 선언보다 우선한다.
function myValue() {
  console.log('function');
}
// var myValue; 는 함수 선언에 의해 무시된다.

// 2. 실행 단계
console.log(typeof myValue); // "function"

myValue = 'variable'; // 함수였던 myValue에 문자열이 재할당된다.

console.log(typeof myValue); // "string"
```

## 결론: 호이스팅을 어떻게 대해야 할까?

호이스팅은 JavaScript의 내부 동작 방식이지만, 이로 인해 혼란스러운 코드가 만들어질 수 있습니다. 따라서 다음과 같은 규칙을 따르는 것이 좋습니다.

1.  **`var` 사용을 피하고 `let`과 `const`를 사용한다:** TDZ는 변수가 선언되기 전에 사용되는 것을 막아주므로, 코드의 예측 가능성을 크게 높여줍니다.
2.  **함수와 변수는 사용하기 전에 선언한다:** 코드 상단에 선언을 모아두면 호이스팅으로 인한 혼란을 원천적으로 방지할 수 있습니다.

호이스팅을 이해하는 것은 JavaScript가 어떻게 동작하는지 깊이 이해하는 데 도움이 되지만, 현대적인 JavaScript 개발에서는 호이스팅에 의존하기보다 명시적인 코드 순서를 따르는 것이 훨씬 더 안정적이고 좋은 습관입니다.