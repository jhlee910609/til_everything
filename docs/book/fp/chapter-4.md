# chapter-4. 액션에서 계산 빼내기

- 테스트 용이성, 재사용성의 이유로 액션에서 계산을 찾아 분리하는 것은 매우 중요하다.
- 명시적인 input과 output(return)이 있고, 외부 데이터(전역변수)에 의존하지 않아야 한다.



## 계산 추출을 단계별로 알아보기

1. 계산 코드 찾아 분리하기
2. 분리해낸 함수에 암묵적 입력과 출력 찾기
   1. 암묵적 입력은 인자가 없는 것, 암묵적 출력은 return 값이 없는 것이다.
   2. 따라서, 이 함수의 생김새는 함수 스코프 내부에 전역 변수 혹은 외부의 어떤 변수가 참조되어 있을 것이다.

3. 암묵적 입력은 '인자'로 출력은 return 값으로 치환하기



## add_item() 분리해 더 좋은 설계 만들기

```javascript
function addItem(cart, name, price){
   const newCart = cart.slice();
   // cart item의 구조를 이 함수가 알 필요가 있을까?
   // 이 함수는 카트에 그저 아이템을 더하는 행동만 수행해주면 되는데...
   newCart.push({
   	name,
   	price
   });
   return newCart;
}
```

그래서...

```javascript
function addItem(cart, item){
   const newCart = cart.slice(); // immutability를 지키기 위한 copy-on-write 
   newCart.push(item);
   return newCart;
}

// item 만드는 생성자 함수 작성
function makeCartItem(name, price){
  return {name, price}
}

// ...
addItem(shoppingCart, makeCartItem("shoes", 20000));
```

하지만... 재사용을 위해서라면... 일반화 또는 추상화하여 작성한다.

아래와 같이 코드를 작성하게 되면 어디서든지 사용 가능하다.

```javascript
ex) arrayUtil.js
export function addElementLast(array, elem){
   const newArray = array.slice(); // immutability를 지키기 위한 copy-on-write 
   array.push(elem);
   return elem;
}



```

