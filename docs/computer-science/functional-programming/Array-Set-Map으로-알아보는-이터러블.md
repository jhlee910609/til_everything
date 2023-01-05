# Array, Set, Map을 통해 알아보는 이터러블/이터레이터 프로토콜

## 이터러블/이터레이터
- 이터러블: 이터레이터를 리턴하는 `[Symbol.iterator]()`를 가진 값
- 이터레이터: `{ value, done }` 객체를 리턴하는 `next()`를 가진 값
- 이터러블/이터레이터 프로토콜: 이터러블을 `for...of`, rest operator 등과 함께 동작하도록한 규약

### 사용자 정의 이터러벌을 통해 알아보기
- well-formed iterator/iterable
  - 반환한 `[Symbol.iterator]()`가 자기 자신이 iterable이자 자기 자신이 반환하는 `[Symbol.iterator]()`도 iterable인 iterator


## 제네레이터
- 제네레이터: 이터레이터이자 이터러블을 생성하는 함수 
- yield: iterator 생성
- return: iterator가 아님. done: true , value: undefined

```javascript
function *infinity(i=0){
  while(true){
    yield i++;
  }
}

function *limit(l, iter){
  for(const a of iter){
    yield a;
    if(a===l) return;
  }
}

function *odds(l){
    for(const a of limit(l, infinity(1))){
      if(a%2) yield a;
      if(a===l) return;
    }
}

const iter = odds(10);

for(const a of iter){
  console.log(a);
}  
```

# `for of`, 전개 연산자, 구조 분해, 나머지 연산자

```javascript
function *infinity(i=0){
  while(true){
    yield i++;
  }
}

function *limit(l, iter){
  for(const a of iter){
    yield a;
    if(a===l) return;
  }
}

function *odds(l){
    for(const a of limit(l, infinity(1))){
      if(a%2) yield a;
      if(a===l) return;
    }
}

const iter = odds(10);
const [first, ...rest] = iter; // 1, [3, 5, 7, 9]
console.log(first, rest) // [1, 3, 1, 3, 5]
console.log([...odds(3), ...odds(5)]);
```






