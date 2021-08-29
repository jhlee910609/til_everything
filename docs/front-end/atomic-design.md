# atomic-design

## 정의

> 디자인 시스템을 만드는 하나의 방법론
> 여러 개의 원자가 모여 하나의 원소가 되는 화학 개념에서 착안

![w:700 center](https://tva1.sinaimg.cn/large/008i3skNgy1gsvsvr12p7j30sg0lcwgp.jpg)

## 등장배경

> OOP의 등장!

- 관심사 분리, 단일 책임의 원칙 등 모듈화 개념 부각
- 그 후 등장한 웹(www) 또한 위의 개념들이 적용되었고, 자연스레 이런 웹의 아키텍쳐는 디자이너의 workflow에도 영향을 주기 시작
- 결국, 하나의 Design System을 만드는 개념으로 진화

## Design System

> 모듈(컴포넌트)들을 기반으로 패턴을 만드는 과정

### 특징

- Brand Identity / Design Principle
  - shape/color/font/animation/etc...
- 유지/보수 쉬움
  - 가장 기본이 되는 컴포넌트만 수정
- 재사용 용이
  - 독립적인 모듈들을 만들었기 때문에 어디서든 사용 가능
- 교육 쉬움
  - zeplin을 보세요 / storyboard를 보세요 / wiki를 보세요

## Atomic Design의 주요 개념

- Atoms(원자) - Molecules(분자) - Organism(유기체) - Templates(템플릿) - Pages(페이지)
- 점점 더 구체적인 단위, 큰 단위

![center](https://tva1.sinaimg.cn/large/008i3skNgy1gsvub4sw2zj31fc0gwdj6.jpg)

## Atoms(원자)

- 더 이상 나눌 수 없는 가장 작은 단위의 컴포넌트, 기본 html tag들
  - ex) ButtonView, InputView, etc...
    ![w:500 center](https://tva1.sinaimg.cn/large/008i3skNgy1gsvvrtnlboj314x0u076o.jpg)

## Molecules(분자)

- Atom(원자)들의 합 (Composition)

- 하나의 단위로 기능을 하기 시작함 (원자들의 목적이 생김)

  - OOP의 SRP을 따르게 된다.
  - ex) MenuView, SearchView...

- standalone(독립적), reusable(재사용 가능), portable(기동성)
  ![center](https://tva1.sinaimg.cn/large/008i3skNgy1gsvvqqee52j31960cqmyd.jpg)

## Organisms(유기체)

- Atom(원자), Molecule(분자)들의 합
- 사용자들에게 보여지는 것들이 구체화 되는 단계이며 문서의 영역(section)을 구분할 수 있는 단위
  - ex) HeaderView, BodyView, FooterView, LeftBar...

![center](https://tva1.sinaimg.cn/large/008i3skNgy1gsvvq1lo2tj31k406umxy.jpg)

## Templates(템플릿)

- 추상적인 분자, 추상적인 유기체의 합

- 레이아웃과 전체 맥락을 제공함 (wireframe, placeholder..)

  ![center w:600](https://tva1.sinaimg.cn/large/008i3skNgy1gsvvolcupqj312y0swtbu.jpg)

## Pages(페이지)

- 실제 구현체, 인스턴스, 실제 사용자가 사용함
- 플레이스 홀더, 와이어프레임이 구체적인 콘텐츠로 채워짐

![center w:600](https://tva1.sinaimg.cn/large/008i3skNgy1gsvvtmf5uzj312g0t6ago.jpg)

## L&L (Lesson & Learn)

> "Write once, run anywhere"

- 단어가 들었갔다고, 온전히 Designer의 영역은 아니다 => 함께 만들어 가자...!
- 개발자끼리라도 가장 베이직한 컴포넌트(Atoms)들은 추상화를 잘 시켜보자
  - 정말 약간 다른 것에 대해서는 프디분들에게 건의해보자..
- 비슷한 것이 있다면 추상화를 시켜 재사용할 수 있도록 노력해보자

### Reference

- [참고할만한 Design System](https://designerup.co/blog/10-best-design-systems-and-how-to-learn-and-steal-from-them/)
- [Design System 공식 홈페이지](https://bradfrost.com/blog/post/atomic-web-design/)
