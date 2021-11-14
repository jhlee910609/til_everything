# Rendering process

> 브라우저 화면에 보이는 Rendering process에 대해 정리합니다.

## Parsing

### 1. DOM의 구성

- HTML 데이터를 받기 시작할 때, 메인 스레드는 HTML(텍스트 문자열)을 parsing 하여 Document Object Model(DOM)으로 변환합니다.
- DOM은 페이지에 대한 브라우저의 내부 표전이자 웹 개발자가 javascript를 활용하여 상호작용할 수 있는 데이터 구조와 API 입니다.

### 2. Subresource loading(하위 리소스 불러오기)

##### 참고자료
