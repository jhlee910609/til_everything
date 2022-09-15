# chapter-8. 계층형 설계 1

## 계층형 설계란?

- 계층에 있는 함수는 바로 아래 계층에 있는 함수를 이용해 정의하는 것들
- 아래 패턴들을 기반으로 좋은 설계를 시도해보자

### 패턴 1. 직접 구현

```javascript
function freeTieClip(cart) {
  let hasTie = false;
  let hasTieClip = false;

  for (let i = 0; i < cart.length; i++) {
    const item = array[i];
    if (item.name === "tie") hasTie = true;
    if (item.name === "tie clip") hasTieClip = true;
  }
  if (hasTie && !hasTieClip) {
    const tieClip = make_item("tie clip", 0);
    return add_item(cart, tieClip);
  }
  return cart;
}
```
