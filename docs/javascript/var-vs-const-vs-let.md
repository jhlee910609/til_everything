# var vs const vs let

- `var`는 `function-scoped`
- `const`, `let`은 `block-scoped`

```javascript
// var i는 global scope 내에서 유효하다.
// global scope도 거대한 함수 scope로 이해하자.
for (var i = 0; i < 10; i++) {
  console.log("i:", i);
}
console.log("result:", i); // 정상 출력

function count() {
  // var i는 count 함수 scope내에서만 유효하다
  for (var j = 0; j < 10; j++) {
    console.log("j:", j);
  }
}

count();
console.log("result:", j); // reference 에러
```

### var vs const vs let

|            |       var       |    const     |     let      |
| ---------- | :-------------: | :----------: | :----------: |
| hoisting   |        o        |      o       |      o       |
| scope      | function-scoped | block-scoped | block-scoped |
| re-declare |        o        |      x       |      x       |
| update     |        o        |      x       |      o       |
