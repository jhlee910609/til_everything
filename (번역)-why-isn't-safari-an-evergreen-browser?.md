# why-isn't-safari-an-evergreen-browser?

## (번역) 사파리는 evergreen browser가 아닙니다.

> 이 글을 번역하게 된 이유는 Chrome browser는 사용자가 강제로 업데이트를 막지 않으면 항상 최신 version의 Chrome으로 자동 업데이트됩니다. 즉, Chrome browser는 항상 최신 버전을 유지합니다. 이를 기술 용어로 [evergreen browser](https://tomdale.net/2013/05/evergreen-browsers/)라고 합니다. 쉽게 이야기해서 항상 최신 버전으로 자동 업데이트되는 브라우저입니다. 대표적으로 Mozilla 재단의 Firefox와 Google의 Chrome browser가 있습니다. 그런데 Safari는 evergreen browser가 아니랍니다. 무려 Safari는 web browser 시장의 점유율 2위인데 말이죠([자료](https://gs.statcounter.com/browser-market-share)). 여기서 관련 자료를 찾던 중 좀 더 세심하게 알고자 번역을 시도하였습니다. 오역이 있더라도 양해해주세요. 저는 네이티브 한국인입니다.
>
> \*를 붙인 내용은 제가 번역하면서 조금 더 세심하게 표현하고 싶었던 부분입니다. 또한, 개발자로서 단순 번역이 아니라 조금 더 정확하게 표현해보고 싶었습니다. 오역이 있더라고 이해 바랍니다. 오역에 대한 의견은 환영합니다!
>
> [원본 글](https://thingsthemselves.com/reminder-Safari-is-not-an-evergreen-browser/)

다양한 이유로 지난 몇 년 전보다 웹 개발자의 삶은 점점 더 편해지고 있습니다. 개발자들이 과거의 플랫폼 호환을 고민하지 않고 최신 기술을 사용할 수 있도록 해주는 [babel](https://babeljs.io)(javascript transpiler), [postcss autoprefixer](https://github.com/postcss/autoprefixer)와 같은 강력한 도구들이 있기 때문입니다. 그러나 웹은 항상 지저분한 곳(\* '파편화된 웹 환경'이라고 표현하고 싶습니다. 한편으론 얼마나 지저분했으면...)이었고, 앞으로도 그럴 것입니다. 그리고 이 난장판(파편화된 웹 환경)을 완벽하게 추상화 시킬 수 있는 방법은 없습니다.

본론으로 가서 저(원 저작자)는 Safari를 새로운 IE(\* Safari 비하 발언이라고 생각합니다.)라고 말한 사람은 아니지만 다음 사안들을 고려해보세요. 주요 브라우저(Chrome, firefox)와 달리 Safari는 evergreen browser가 아닙니다.

Safari는 Apple의 운영체제(OS X, iOS, iPad OS)에 종속적이며, Apple의 운영체제는 하드웨어(Apple device) 종속적입니다. 과거에는 이와 같은 사실을 무시해도 됐지만, 현 상황은 변하고 있습니다(\*무시할 수 없는 상황에 왔습니다.).

대부분의 Mac 사용자가 운영 체제를 별 생각 없이 업데이트를 하던 때가 있었습니다; Mountain Lion(OS X 버전 이름)을 구동시킬 수 있는 컴퓨터(Mac book, iMac)에 Mavericks, Yosemite, 그리고 El Capitan가 지원되었습니다. 그로 인해, 웹 개발자들은 대부분의 맥 사용자들이 최신 버전의 Safari를 사용할 수 있다고 추측하였습니다.

위와 같은 부분은 Sierra(OS X 버전 이름)와 함께 변화하였습니다. Apple은 오래된 Mac OS 버전에 Safari 사용이 가능하도록 어느 시점까지만(정확히 말하자면 두 번 정도의 메이저 업데이트) 별도의 업그레이드를 해왔습니다. [Safari 11](https://en.wikipedia.org/wiki/Safari_version_history#Safari_11)은 El Captian에서 사용할 수 있는 가장 최신 Safari 버전이며, 현재의 트렌드가 지속된다면 Safari 13은 과거의 High Sierra 이후의 OS X 버전으로 업데이트하지 않은 사용자에게는 가장 최신의 Safari 버전으로 남게 됩니다.

iOS 진영에서는, 지원하지 않는 기기는 문제로 보지 않았습니다. 대부분의 사람이 2~3년마다 그들의 기기를 최신 기기로 바꾸고, 각각의 기기들은 4-5년 동안 소프트웨어 업데이트 지원을 받기 때문에 iOS 사용자들은 보편적으로 항상 최신 버전을 사용할 것으로 예상합니다.

그러나 업계 관계자들은 큰 폭의 스마트폰 판매량 감소([관련 기사](https://nymag.com/intelligencer/2018/12/global-u-s-growth-in-smartphone-growth-starts-to-decline.html))에 따라 iPhone 판매량 또한 둔화([관련 기사](https://9to5mac.com/2019/04/30/iphone-sales-drop/))되고 있음을 인식하고 있을 것입니다. 사용자들은 더 오랫동안 업그레이드를 바라며, 기기 자체를 교체하는 것보다 깨진 스크린과 배터리 고장을 수리하는 것을 선택합니다.

아마도 가까운 미래에 Apple이 iPhone과 iPad에 대한 지원을 중단한 후에도 일부 사람들은 "충분히 좋은" iPhone과 iPad 사용을 선택할 것입니다.

우리(개발자들)는 오래된 Safari 버전을 사용하는 사람들에게도 작동하는 사이트를 만들기 위해 노력해야 할까요? 이는 각각의 개발자 혹은 사이트 소유자의 결정이지만, 의도적인 결정이어야만 합니다. "최신 두 버전"은 evergreen browser에게는 유용한 기본값이지만, Safaris는 evergreen browser가 아닙니다.
