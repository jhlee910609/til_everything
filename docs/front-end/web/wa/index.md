# 웹 접근성 

## 대체 텍스트 

- 눈으로 볼 수 없는 경우, 이미지에 대한 설명을 텍스트로 입력하여 스크린리더가 readable 할 수 있게 markup을 구성
- 시각적 요소들에 대한 context 정보 제공이 핵심 


## img 태그
> 이미지의 노출 목적에 따라 `alt` 속성에 알맞는 값을 넣는다.

- 이미지의 용도가 있을 경우
  - 대체 텍스트 set 
  - ex) 설명이 필요한 이미지

- 이미지의 용도가 없을 경우
  - 대체 텍스트 set x
  - ex) 단순 이미지, 혹은 deco를 위한 이미지


## 기호
- 주식 등락을 표현하는 화살표 기호 같은 경우, 문자로 의미를 부여한다.
  - ex) 10.1 ⬆(10.1 상승), 10.1 ⬇️(10.1 하락)

## input, button
- 해당 `input` , `button`의 기능을 명확히 알 수 있는 대체 텍스트를 제공한다.


## 명도 대비 

> 저시력자, 고령자 등이 쉽게 콘텐츠를 인식할 수 있도록 콘텐츠(텍스트, 아이콘)와 배경 간의 명도 대비는 **4.5:1** 이상이 가장 적합


## 초점 이동 

- tab, shift + tab 으로 초점 이동이 자연스럽게 되어야 함
- 페이지의 모든 링크, 버튼, 입력창에 초첨이 가야함 
- 사용할 수 없는 비활성 요소(버튼, 입력창 등)에는 초첨이 가지 않아야함
- 우선 초점 이동의 흐름이 중요 
- 화면을 가리는 레이어 혹은 팝업의 경우, 가장 먼저 초점을 받게 함 

## 재생 조절 가능
- 스크린리더의 소리를 방해하는 자동으로 소리 재생되면 안됨 (3초 이하는 가능)