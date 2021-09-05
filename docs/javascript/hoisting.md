# hoisting

> javascript의 독특한 특징인 'hosting'에 대해 공부합니다.
> 'hoisting'은 ES6 스펙 이전에는 사용되지 않았던 용어입니다.
> 또한, 'hoist'라는 단어는 한국어로 '감아 올리기'라는 의미를 갖고 있습니다.
> 이미 단어에서 추측할 수 있는 동작이 있는데, 이 동작 원리에 대해 알아 보도록 하겠습니다.

## hoisting의 정의

- javascript hoisting은 코드 실행 전에 변수와 함수 선언을 interpreter가 memory에 할당하는 절차를 일컫습니다. `var` 선언은 `undefined`로 초기화됩니다. 하지만 `let`과 `const`는 hoisting의 일부로 초기화되지 않습니다.
- 개념적으로 hoisting은 종종 "변수 선언과 초기화, 그리고 그 선언들을 코드의 가장 상단으로 옮기는" interpreter로서 표현됩니다. 이는 변수가 정의되기 전에, 코드에 나타날 수 있게 해줍니다. 하지만, 기존 코드에서 코드 라인이 실행되기 전까지 그 어떤 변수 초기화가 일어나지 않음을 참고하세요.

### 예제

```javascript
printName("lee");

/*
The result of the code above is: "lee"
*/

function printName(name) {
  console.log(name);
}
```

## 선언만 hoisted 됩니다.

- 즉, 쉽게 이해하자면 초기화는 hoisted 되지 않습니다. 선언만 hoisted 됩니다.

```javascript
console.log(name); // The result is 'undefined'
var name; // declaration
name = "lee"; // initialization
console.log(name); // The result is 'lee'
```

-
