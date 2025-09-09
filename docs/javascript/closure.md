# closure

> JavaScript의 가장 강력하고 핵심적인 개념 중 하나인 클로저(Closure)에 대해 알아봅니다.

## 클로저(Closure)란?

> MDN에서는 클로저를 **"함수와 그 함수가 선언된 렉시컬 환경(Lexical Environment)의 조합"** 이라고 정의합니다. 조금 더 쉽게 풀어보자면, **"외부 함수가 실행을 마친 후에도, 그 외부 함수의 변수에 접근할 수 있는 내부 함수"** 를 의미합니다.

클로저는 "기억하는 함수"라고 생각할 수 있습니다. 자신이 태어난 환경(렉시컬 스코프)을 기억하고, 그 환경에 있던 변수들에 계속해서 접근할 수 있는 능력을 가진 함수입니다.

이 개념은 [실행 컨텍스트(Execution Context)](./execution-context.md)와 스코프 체인을 이해하면 훨씬 명확해집니다. 함수가 호출되면 실행 컨텍스트가 생성되고, 이 컨텍스트는 자신의 렉시컬 환경과 외부 환경 참조(상위 스코프)를 가집니다. 클로저는 바로 이 **외부 환경 참조를 통해 상위 스코프의 변수에 접근**하는 원리입니다.

## 클로저의 동작 원리

가장 고전적인 클로저 예제를 통해 동작 원리를 살펴보겠습니다.

```javascript
function outerFunc() {
  const outerVar = 'I am from the outside!';

  function innerFunc() {
    console.log(outerVar); // 외부 함수의 변수에 접근
  }

  return innerFunc;
}

const myClosure = outerFunc(); // outerFunc 실행이 끝나고, innerFunc가 반환됨
myClosure(); // 'I am from the outside!'
```

위 코드의 실행 흐름을 따라가 보겠습니다.

1.  `outerFunc()`가 호출되면, `outerFunc`의 실행 컨텍스트가 생성되고 콜 스택에 추가됩니다.
2.  `outerFunc`는 내부 변수 `outerVar`와 내부 함수 `innerFunc`를 선언합니다.
3.  `outerFunc`는 실행을 마치면서 `innerFunc` 함수를 반환하고, `outerFunc`의 실행 컨텍텍스트는 콜 스택에서 제거됩니다.

여기서 중요한 점이 발생합니다. 일반적으로 함수 실행이 끝나면 그 함수의 변수들(`outerVar`)은 가비지 컬렉션의 대상이 되어 사라져야 합니다. 하지만 `innerFunc`가 `outerVar`를 참조하고 있기 때문에, JavaScript 엔진은 `outerVar`를 메모리에서 제거하지 않고 남겨둡니다.

4.  `myClosure` 변수에는 `innerFunc` 함수가 할당되어 있습니다.
5.  `myClosure()`를 호출하면(`innerFunc`를 호출하는 것과 같음), `innerFunc`의 실행 컨텍스트가 생성됩니다.
6.  `innerFunc`는 자신의 스코프에서 `outerVar`를 찾지만 없으므로, 스코프 체인을 따라 자신이 태어난 환경, 즉 `outerFunc`의 렉시컬 환경으로 올라가 `outerVar`를 찾아냅니다.
7.  결과적으로 `'I am from the outside!'`가 콘솔에 출력됩니다.

이처럼 `innerFunc`는 `outerFunc`의 실행이 끝난 후에도 `outerVar`에 접근할 수 있는데, 이러한 메커니즘 또는 `innerFunc` 자체를 **클로저**라고 부릅니다.

## 클로저의 활용

클로저는 단순히 개념에 그치지 않고, 실제 개발에서 매우 유용하게 사용됩니다.

### 1. 데이터 은닉과 캡슐화 (Data Encapsulation)

> 클로저를 사용하면 특정 변수를 외부에서 직접 접근할 수 없도록 숨기고, 오직 허용된 함수를 통해서만 조작하게 만들 수 있습니다. 이를 통해 **비공개(private) 변수**를 흉내 낼 수 있습니다.

```javascript
function createCounter() {
  let count = 0; // 비공개 변수

  return {
    increment: function() {
      count++;
      console.log(count);
    },
    decrement: function() {
      count--;
      console.log(count);
    }
  };
}

const counter = createCounter();
counter.increment(); // 1
counter.increment(); // 2
// console.log(count); // ReferenceError: count is not defined
```

위 예제에서 `count` 변수는 `createCounter` 함수 스코프 내에 존재하므로 외부에서 직접 접근할 수 없습니다. 오직 `increment`와 `decrement`라는 공개된 메서드를 통해서만 `count`의 값을 변경할 수 있습니다. 이처럼 상태(state)를 안전하게 관리할 수 있게 됩니다.

### 2. 함수 팩토리 (Function Factory)

> 클로저를 이용하면 비슷한 형태의 함수를 동적으로 생성하는 함수 팩토리를 만들 수 있습니다.

```javascript
function createMultiplier(x) {
  return function(y) {
    return x * y;
  };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

console.log(double(5)); // 10 (2 * 5)
console.log(triple(5)); // 15 (3 * 5)
```

`createMultiplier` 함수는 인자 `x`를 기억하는 새로운 함수를 반환합니다. `double`과 `triple`은 각각 `x`의 값이 2와 3으로 고정된 클로저가 되어, 재사용성과 코드 가독성을 높여줍니다.

### 3. 이벤트 핸들러와 콜백

클로저는 비동기 처리, 특히 이벤트 핸들러나 콜백 함수에서 매우 흔하게 사용됩니다. 다음은 잘못된 예시입니다.

```javascript
// 잘못된 예시
for (var i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i); // 4, 4, 4 출력
  }, 1000);
}
```

`setTimeout`의 콜백 함수가 실행될 시점에는 `for` 루프가 이미 모두 종료된 상태입니다. `var`로 선언된 변수 `i`는 함수 스코프를 가지므로, 루프가 끝난 후의 최종 값인 `4`를 참조하게 됩니다. 모든 콜백 함수가 동일한 `i`를 참조하므로 모두 `4`를 출력합니다.

이 문제를 클로저로 해결할 수 있습니다.

```javascript
// 클로저를 이용한 해결
for (var i = 1; i <= 3; i++) {
  (function(j) {
    setTimeout(function() {
      console.log(j); // 1, 2, 3 출력
    }, 1000);
  })(i);
}
```

즉시 실행 함수(IIFE)를 사용하여 각 루프마다 별도의 스코프를 생성하고, 그 스코프에 `i`의 현재 값(`j`)을 잡아두는 클로저를 만든 것입니다.

> 물론, ES6의 `let`을 사용하면 이 문제는 훨씬 간단하게 해결됩니다. `let`은 블록 스코프를 가지므로, `for` 루프의 각 반복마다 새로운 스코프가 생성되어 `i` 값을 고유하게 유지합니다.

```javascript
// let을 사용한 해결 (가장 현대적이고 간편한 방법)
for (let i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i); // 1, 2, 3 출력
  }, 1000);
}
```

## 주의할 점: 메모리 누수

클로저는 상위 스코프의 변수를 계속 참조하므로, 필요 없어진 클로저를 계속 참조하고 있으면 가비지 컬렉터가 해당 메모리를 수거하지 못해 **메모리 누수(Memory Leak)** 가 발생할 수 있습니다. 더 이상 사용하지 않는 클로저(이벤트 리스너 등)는 참조를 명시적으로 제거(`null` 할당)해주는 것이 좋습니다.

## 결론

클로저는 JavaScript의 함수형 프로그래밍 패러다임을 지탱하는 핵심적인 기능입니다. 데이터 은닉, 상태 관리, 코드 재사용 등 다양한 패턴을 가능하게 하므로, JavaScript 개발자라면 반드시 깊이 있게 이해해야 하는 중요한 개념입니다.