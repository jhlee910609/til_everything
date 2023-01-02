# 안전하고, 정확한 함수 합성을 위한 방식 

## 합성 관점에서의 Promise와 monad

> monad, Kleisli composition 관점에서 함수 합성을 바라보자!

### monad
- 함수의 input 값에 따라 함수가 어떤 값을 return 할 지 모르는 상황에서 **function composition**을 안전하게 하기 위한 방법
- javascript 언어 특징 상, monad 개념을 직접적으로 사용할 상황이 거의 없음
  
```javascript

const add1 = a => a + 1;
const square = a => a * a;

log(f(g(1))); // 4
log(f(g())); // NaN <- 이 결과 값은 우리가 원했던 상황이 아니다!

// 아래와 같이 코딩 한다면 위와 같이 NaN이 나오는 문제를 피할 수 있다. 
Array.of(1).map(g).map(f).forEach(console.log);
[].map(g).map(f).forEach(console.log)

// Promise chaining으로 monad 개념 적용해보기
Promise.resolve(2).then(g).then(f).then(console.log);
new Promise(resolve => setTimeout(()=>resolve(2), 2000)).then(g).then(f).then(console.log);

```

###### 참고 
- https://tpgns.github.io/2018/04/18/javascript-monads-made-simple/
- https://overthecode.io/i-am-js-developer-and-still-dont-know-monad/

## Kleisli Compoisition 관점에서의 Promise

- 현대 프로그래밍은 상태가 존재함으로 같은 input에 대한 보장 받기가 힘들다.
- **'외부의 상태'**에 따라 output이 달라질 수 있다.
- 안전하고, 오류 없는 합성을 위한 composition 방식 중 하나.

```javascript
const users = [
    {id: 1, name: 'lee'},
    {id: 2, name: 'kim'},
    {id: 3, name: 'park'}
];

const getUserById = id => find(user => user.id === id)  || Promise.reject('해당 아이디를 갖고 있는 유저가 없어요!') // 아래 f 함수가 실해되지 않게 됨. 에러가 나서 then을 실행하지 않음 

const f = ({name}) => name;
const g = getUserById;

const fg = id => Promise.resolve(id).then(g).then(f).catch(a => a); // Promise를 활용하여 Kleisli 관점으로 코딩

fg(2).then(console.log)
```

