# execution context

> javascript의 근본, 핵심원리인 execution context (실행 컨텍스트)를 정리합니다.

## execution context란?

실행 가능한 코드(executable code)가 실행되기 위해 필요한 환경입니다.
실행 가능한 코드는 아래와 같습니다.

- 전역 코드: global scope에 존재하는 코드
- 함수 코드: function-level scope에 존재하는 코드
- eval 코드: eval 함수[^1]로 실행되는 코드

위 코드들이 실행되기 위해서 실행에 필요한 여러가지 정보들이 필요합니다.
코드 실행에 필요한 정보들은 아래와 같습니다.

- 변수: global variable, local variable, parameter, object property

[^1]: [eval() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/eval)
