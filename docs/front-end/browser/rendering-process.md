# Rendering process

> 브라우저 화면에 보이는 Rendering process에 대해 정리합니다.

## Parsing

### DOM의 구성

- HTML 데이터를 받기 시작할 때, 메인 스레드는 HTML(텍스트 문자열)을 parsing 하여 Document Object Model(DOM)으로 변환합니다.
- DOM은 페이지에 대한 브라우저의 내부 표전이자 웹 개발자가 javascript를 활용하여 상호작용할 수 있는 데이터 구조와 API 입니다.

### Subresource loading(하위 리소스 불러오기)

- image, css, javascript와 같은 외부 리소스들은 network 혹은 cache로부터 해당 파일들을 가져와야 합니다.
- 메인 스레드는 DOM을 구성하기 위해 parsing하는 동안 각각의 외부 리소스들을 찾고, 요청해야하 합니다. 조금 더 속도를 빠르게 하기 위해서 'preload scanner' 가 동시에 동작합니다.

[<img src='https://developers.google.com/web/updates/images/inside-browser/part3/dom.png'/>]()

### Javascript는 parsing을 방해할 수 있습니다.

- HTML parser가 `<scrip>` tag를 찾았을때, HTML parsing 작업을 멈추고, javascript code를 load, parse 그리고 실행시킵니다.
  - `document.write()` 와 같은 javascript 코드가 있다면 javascript가 DOM 구조 전체에 영향을 줄 수 있기 때문입니다.

### browser에게 당신이 원하는 리소스 로드 방식을 주세요.

- javascript 코드에 `document.write()`와 같은 코드가 있지 않다면,`<scrip>` tag에 `async`와 `defer` 속성[^1]을 활용하여 blocking 없이 javascript를 비동기적으로 load와 실행시킬 수 있습니다.

### style 계산

- Main Thread에서 CSS를 parsing하고, 각각에 DOM 노드에 계산된 스타일을 결정합니다.

  [<img src='https://developers.google.com/web/updates/images/inside-browser/part3/computedstyle.png'/>]()

### layout

- layout은 요소들의 기하학적 위치를 찾는 과정입니다.
- Main thread는 DOM과 연산된 스타일을 돌면서 `x,y 좌표`와 `bounding box size` 정보를 갖고 있는 `layout tree`를 생성합니다.
- layout tree는 DOM tree와 비슷한 구조를 갖고 있지만, 차이점은 page에 보이는 정보만 갖고 있습니다.
  - 예를 들면, `display: none;`으로 되어 있는 요소는 layout tree에 보이지 않습니다.

### paint

- Main thread가 paint records를 생성하기 위해 layout tree를 돕니다.

  - paint record는 painting 과정에 대한 메모입니다.

### rendering pipeline을 업데이트하는 것은 값비쌉니다.

- `rendering pipeline`에서 가장 중요한 것은 각 단계에서 이전 작업의 결과를 사용하여 새 데이터를 생성한다는 것입니다. 예를 들어 layout tree에 변경사항이 있는 경우, 문서에 영향 받을 받는 부분에 대해 paint 순서를 다시 생성해야 합니다.

##### 참고자료

- [Inside look at modern web browser (part 3)](https://developers.google.com/web/updates/2018/09/inside-browser-part3)

  [^1]: [javascript - Script Tag - async & defer - Stack Overflow](https://stackoverflow.com/questions/10808109/script-tag-async-defer)
