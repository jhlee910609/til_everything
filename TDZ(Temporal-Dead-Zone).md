# TDZ(Temporal-Dead-Zone)

## Temporal Dead Zone란?

- Temporal Dead Zone(이하 TDZ)는 `let`, `const`, `class` 구문의 유효성을 관리합니다.
- 아래 코드는 에러를 뱉어냅니다.

```javascript
name; // throws error: [ReferenceError: Cannot access uninitialized variable.]
const name = "john"; // 이 라인을 오기 전까지 name 변수는 TDZ에 있다고 이야기할 수 있습니다.
name;
```

## TDZ의 영향을 받는 구문

### `let`, `const`, `class`

### class constructor 내부에서 사용하는 `super`

```javascript
class MyCar extends Car {
  constructor(color, power) {
    this.power = power; // this binding이 TDZ에 있다.
    super(color);
  }
}

// Does not work!
const myCar = new MuscleCar(‘blue’, ‘300HP’); // `ReferenceError`
```

### 기본 함수 매개변수

```javascript
const a = 1;
function square(a = a) {
  return a * a;
}

square(); // throw reference error
```

## TDZ의 영향을 받지 않는 `var`, `function`, `import` 구문

- 위 키워드들은 모두 호이스팅된다.

```javascript
name; // no problem!
var name;

hello("jane"); // hi, jane
function hello(name) {
  console.log(`hi, ${name}`);
}
hello("john"); // hi, john

myFunc(); // work
import { myFunc } from "./myModule";
```
