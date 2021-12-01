# v17 breaking change

> react 17에는 무엇이 달라졌나...?
>
> - native event: vanilla.js event 방식 ex) someElement.addEventListener('click', handler);

### event delegation 방식 변경

- react event hanlder를 document에 부착하지(attachment) 않음
- react root dom container에 부착함(attachment)
  ![<img src="https://reactjs.org/static/bb4b10114882a50090b8ff61b3c4d0fd/21cdd/react_17_delegation.png">](https://reactjs.org/static/bb4b10114882a50090b8ff61b3c4d0fd/21cdd/react_17_delegation.png)
  - native event의 방식과 다르게 가기때문에 문제 x
  - 한 document에 여러 개의 react dom이 있을 경우, event handling의 혼선이 줄어들 수 있음

### 새로운 JSX 변환

- import react 없이 jsx 사용 가능
- bundle size가 아주 약간 줄음
- 새로운 문법이 생기거나, 기존 문법이 제거된 그런 변경점은 아님

### Browser와 정렬

> react에서 일부 event들이 browser의 event 방식과 동일하게 동작하도록 수정했음

- `onScroll`: bubbling 되었었는데, 안됨. native event에서는 bubbling 안됨
- `onFocus`, `onBlur` 각각 native의 `onfocusin`, `onfocusout` 사용하도록 코드 수정

### effect cleanup timing

- `useEffect` clean up 타이밍에 대한 고민이 있었음 > 일관성을 지키게끔 수정이 이뤄짐
- 동기방식으로 clean up 함수가 실행되었는데, 그럴 필요가 없다고 생각함.
  - 우선 큰 application에서 screen update에 대한 모든 것들을 동기적으로 실행해야하는데 비효율적이라고 생각
  - 그래서 항상 비동기적으로 실행됨
  - 동기적 방식이 필요하면 `useLayoutEffect`를 사용하면 됨
