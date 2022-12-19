# iterator와 iterable

## 이터러블/이터레이터 프로토콜

- 이터러블: 이터레이터를 리턴하는 [Symbol.iterator]()를 가진 값
- 이터레이터: { value, done } 객체를 리턴하는 next()를 가진 값
- 이터러블/이터레이터 프로토콜: 이터러블을 for...of, 전채 연산자들과 함께 동작하도록한 규약
