# Rendering process

> 브라우저 화면에 보이는 Rendering process에 대해 정리합니다.

## Parsing

### 1. DOM의 구성

- HTML 데이터를 받기 시작할 때, 메인 스레드는 HTML(텍스트 문자열)을 parsing 하여 Document Object Model(DOM)으로 변환합니다.
- DOM은 페이지에 대한 브라우저의 내부 표전이자 웹 개발자가 javascript를 활용하여 상호작용할 수 있는 데이터 구조와 API 입니다.

### 2. Subresource loading(하위 리소스 불러오기)

- image, css, javascript와 같은 외부 리소스들은 network 혹은 cache로부터 해당 파일들을 가져와야 합니다.
- 메인 스레드는 DOM을 구성하기 위해 parsing하는 동안 각각의 외부 리소스들을 찾고, 요청해야하 합니다. 조금 더 속도를 빠르게 하기 위해서 'preload scanner' 가 동시에 동작합니다.

[<img src='https://developers.google.com/web/updates/images/inside-browser/part3/dom.png'/>]()

##### 참고자료
