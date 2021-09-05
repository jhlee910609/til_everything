# hoisting

> javascript의 독특한 특징인 'hosting'에 대해 공부합니다.
> 'hoisting'은 ES6 스펙 이전에는 사용되지 않았던 용어입니다.
> 또한, 'hoist'라는 단어는 한국어로 '감아 올리기'라는 의미를 갖고 있습니다.
> 이미 단어에서 추측할 수 있는 동작이 있는데, 이 동작 원리에 대해 알아 보도록 하겠습니다.

## hoisting이란?

- javascript hoisting은 코드 실행 전에 변수와 함수 선언을 interpreter가 memory에 할당하는 절차를 일컫습니다. `var` 선언은 `undefined`로 초기화됩니다. 하지만 `let`과 `const`는 hoisting의 일부로 초기화되지 않습니다.
- 개념적으로 hoisting은 종종 "변수 선언과 초기화, 그리고 그 선언들을 코드의 가장 상단으로 옮기는 것"으로 표현됩니다.
