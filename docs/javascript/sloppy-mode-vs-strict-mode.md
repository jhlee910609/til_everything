# sloppy-mode-vs-strict-mode

`strict mode`는 ES5에 등장한 개념으로, 이름에서 알 수 있듯이 JavaScript를 더 엄격하게 실행시키는 모드입니다. 기존의 느슨한 모드(sloppy mode)에서 허용되던 일부 문제 있는 코드들을 에러로 처리하여 더 안정적인 코딩을 가능하게 합니다.

## strict mode를 왜 사용할까요?

> `strict mode`는 잠재적인 오류를 줄이고, 코드의 안정성과 보안을 높이기 위해 사용합니다.

JavaScript는 원래 유연성을 중시하는 언어라, 개발자의 실수를 너그럽게(?) 눈감아주는 경향이 있었습니다. 이것이 바로 `sloppy mode`인데, 이로 인해 디버깅이 어려운 문제가 발생하곤 했습니다. `strict mode`는 이런 문제들을 사전에 방지하고, 다음과 같은 이점들을 제공합니다.

1.  **실수를 에러로 변환:** 기존에는 조용히 무시되던 코드들을 에러로 바꿔줍니다. 예를 들어, 선언되지 않은 변수에 값을 할당하는 경우입니다.
2.  **성능 향상:** JavaScript 엔진이 코드를 더 쉽게 최적화할 수 있도록 돕습니다. `strict mode`의 제약 조건들은 엔진이 더 공격적인 최적화를 수행할 수 있게 만들어줍니다.
3.  **미래의 ECMAScript 버전을 대비:** `strict mode`는 앞으로 추가될 문법과 충돌할 수 있는 키워드(예: `implements`, `interface`, `let`, `package`, `private`, `protected`, `public`, `static`, `yield`)의 사용을 금지합니다.

## strict mode 적용 방법

`strict mode`는 스크립트 전체 또는 특정 함수에만 적용할 수 있습니다.

### 스크립트 전체에 적용

스크립트 최상단에 `"use strict";` 지시어를 추가하면, 해당 스크립트 전체가 `strict mode`로 동작합니다.

```javascript
"use strict";

// 이 스크립트의 모든 코드는 strict mode로 실행됩니다.
function myFunction() {
  // ...
}
```

> **주의!** 여러 스크립트 파일을 하나로 합치는 경우, 한 파일의 `"use strict";`가 다른 파일들까지 `strict mode`로 만들 수 있어 의도치 않은 결과를 낳을 수 있습니다. 따라서 함수 단위로 적용하는 것이 더 안전할 수 있습니다.

### 함수 단위로 적용

특정 함수의 최상단에 `"use strict";`를 선언하면, 해당 함수만 `strict mode`로 동작합니다.

```javascript
function sloppyFunction() {
  // 여기는 sloppy mode
}

function strictFunction() {
  "use strict";
  // 이 함수 내부만 strict mode
}
```

## sloppy mode vs strict mode 주요 차이점

| 특징 | sloppy mode | strict mode |
| :--- | :--- | :--- |
| **선언되지 않은 변수** | 전역 변수로 생성 | `ReferenceError` 발생 |
| **`this` 바인딩** | 전역 객체 (`window`) | `undefined` |
| **읽기 전용 속성 수정** | 조용히 실패 | `TypeError` 발생 |
| **삭제할 수 없는 속성 삭제** | 조용히 실패 | `TypeError` 발생 |
| **중복된 매개변수 이름** | 허용 | `SyntaxError` 발생 |
| **8진수 리터럴** | 허용 (`0123`) | `SyntaxError` 발생 |
| **`with` 문** | 허용 | `SyntaxError` 발생 |

### 1. 선언되지 않은 변수 사용

`sloppy mode`에서는 선언되지 않은 변수에 값을 할당하면, 암묵적으로 전역 변수가 생성됩니다. 이는 전역 스코프를 오염시키고, 버그의 원인이 될 수 있습니다.

```javascript
// sloppy mode
function assignValue() {
  undeclaredVar = 123; // 'var', 'let', 'const' 없이 할당
}
assignValue();
console.log(window.undeclaredVar); // 123 (전역 변수 생성)
```

`strict mode`에서는 이런 경우 `ReferenceError`를 발생시켜 실수를 즉시 알 수 있게 합니다.

```javascript
"use strict";

function assignValue() {
  undeclaredVar = 123; // ReferenceError: undeclaredVar is not defined
}
assignValue();
```

### 2. `this` 바인딩

일반 함수 호출 시, `sloppy mode`에서는 `this`가 전역 객체(`window` 또는 `global`)를 가리킵니다.

```javascript
// sloppy mode
function showThis() {
  console.log(this);
}
showThis(); // window 객체 출력
```

`strict mode`에서는 `this`가 `undefined`로 바인딩되어, 의도치 않게 전역 객체를 조작하는 것을 방지합니다.

```javascript
"use strict";

function showThis() {
  console.log(this);
}
showThis(); // undefined
```

### 3. 중복된 매개변수 이름

`sloppy mode`에서는 함수의 매개변수 이름이 중복되어도 에러가 발생하지 않습니다. 마지막으로 선언된 매개변수가 사용됩니다.

```javascript
// sloppy mode
function duplicateParams(a, a) {
  console.log(a);
}
duplicateParams(1, 2); // 2
```

`strict mode`에서는 이를 `SyntaxError`로 처리하여 코드의 명확성을 높입니다.

```javascript
"use strict";

function duplicateParams(a, a) { // SyntaxError: Duplicate parameter name not allowed in this context
  console.log(a);
}
```

## 결론

`strict mode`는 더 깨끗하고, 안정적이며, 미래 지향적인 JavaScript 코드를 작성하는 데 큰 도움을 줍니다. 특별한 이유가 없다면, 모든 JavaScript 프로젝트에 `strict mode`를 기본으로 적용하는 것이 좋습니다. 특히 모듈 시스템(ESM, CommonJS)을 사용하면 파일(모듈) 단위로 스코프가 분리되고, 기본적으로 `strict mode`로 동작하므로 `strict mode`의 이점을 자연스럽게 누릴 수 있습니다.