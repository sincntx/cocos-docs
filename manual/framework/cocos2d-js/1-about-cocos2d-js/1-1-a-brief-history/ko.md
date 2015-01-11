# 1.1 짧은 역사

<img src="http://files.cocos2d-x.org/images/orgsite/logo.png" height=180> 

[Cocos2d-JS](https://github.com/cocos2d/cocos2d-js)는 웹게임과 네이티브 게임을 위한 오픈 소스 게임 엔진으로 높은 성능과 유저 친화적이며 웹, 안드로이드, iOS, WP8, Mac, Windows 등 멀티플랫폼 지원을 제공합니다. Cocos2d-JS를 통해 2D 게임 프로그래밍을 쉽고 빠르게 할 수 있습니다. 쉽게 배우고 사용하기 쉬운 API 등 2D 게임 프로그래밍의 키 컴포넌트를 분명하게 하여 다른 프레임워크에 비해서 두드러진 프레임워크로 만들어줍니다.

Cocos2d-JS는 Cocos2d-x의 HTML5 버전으로 [Cocos2d-html5](https://github.com/cocos2d/cocos2d-html5)과 Cocos2d-x 자바스크립트 바인딩(JSB)를 포함합니다. Cocos2d-JS에 의해 프레임워크의 상단에서 Cocos2d-html5가 HTML5 기반으로 자바스크립트로 게임을 작성하고 브라우져에서 동작하도록 지원합니다. API는 Cocos2d-html5와 Cocos2d-x JSB 사이에서 완벽하게 호환됩니다. 따라서 Cocos2d-JS 게임은 아주 약간의 수정이나 혹은 전혀 수정 없이 Cocos2d-x에 기반한 "Cocos2d 자바스크립트 바인딩"을 사용하여 실행할 수 있습니다.

#### 왜 Cocos2d-JS를 선택해야 할까요?
왜 당신은 다른 고려 가능한 게임 엔진 대신 Cocos2d-JS를 선택하길 원하는걸까요?

* 최신(Modern) JS API 
* 플러그인 없이 코드 하나로 웹, 데스크탑, 모바일, 콘솔 등 어디에서나 실행 가능한 풀 플랫폼 지원
* 브라우저에서 당신의 게임을 테스트하고 디버깅하고 웹, 모바일 또는 콘솔 타겟으로 배포할 수 있는 기능
* 스프라이트, 애니메이션, 파티클, 화면 전환(transitions), 타이머, 이벤트 (터치, 키보드, 가속 센서, 마우스), 사운드, 파일 입출력, 스켈레탈 애니메이션 등을 포함한 다양한 기능적인 API
* 높은 성능, 검증된 신뢰
     
### 1.1.1 역사

2010년 안드로이드의 성장과 함께, Cocos2d-x 팀은 안드로이드 플랫폼뿐만 아니라 크로스 플랫폼 기술까지 포커스를 맞춰서 Cocos2d-iphone으로부터 Cocos2d-x를 분기했습니다. 2011년에 구글이 Cocos2d-x 팀이 Cocos2d-x를 HTML5가 준비된 브라우져와 웹앱에 포커스를 둔 Cocos2d-html5로 포팅할 수 있도록 후원했습니다.

Cocos2d-html5 프로젝트는 2012년 1월 29일에 시작되었습니다. 그리고 2012년 8월에 Cocos2d-x v2.0에 기반한 첫 스테블 버전을 릴리즈 했습니다. 한편 징가는 Cocos2d-x 팀이 Cocos2d-html5의 네이타브 플랫폼 기술인 Cocos2d-x JSB 솔루션을 개발하도록 도와주었습니다.

Cocos2d-html5 and Cocos2d-x JSB were combined and upgraded to Cocos2d-JS in Mar. 2014, and released the first statble version v3.0 on Sep.12 2014. In Cocos2d-JS v3.0, it reinvented workflows for all platforms, provides a consistent development experience for whichever platform you want to distribute to, no matter web and native. Cocos2d-JS v3.0 is super powerful along with all these cool new features: Editors Support, Assets Manager, Object Pool, JS to Objective-C/JAVA reflection, etc.

### 1.1.2 Cocos2d-html5와 Cocos2d-x JSB

앞서 말한 설명으로부터 Cocos2d-html5는 Cocos2d-JS의 중요한 모듈이며 순수한 캔버스/WebGL게 기반한 HTML5와 100% 호환되는 HTML5 게임 엔진입니다. 그래서 Cocos2d-JS 프로젝트는 쉽게 HTML5 지원 브라우져를 지원합니다.

만약 웹에서의 캐주얼 게임에만 관심이 있다면 Cocos2d-JS 라이트 버전을 직접 웹 페이지에 깃털처럼 가볍고 엄청나게 쉽게 임베디드할 수 있습니다.

Cocos2d-JS는 약간의 코드 수정이나 혹은 코드 수정 없이 Cocos2d-x JSB를 통해 네이티브 어플리케이션으로 동작하도록 지원합니다.

C/C++로 작성된 Cocos2d-x JSB는 자바스크립트 코드와 네이티브 코드 사이에 위치한 코드 랩퍼(wrapper)입니다. JSB는 자바스크립트 코드에 기반한 네이티브 코드와 그 반대의 경우를 호출할 수 있습니다.

자바스크립트 코드는 모질라의 자바스크립트 가상 머신인 스파이더몽키에 의해 해석(인터프리트, interpreted)됩니다. 자바스크립트 가상 머신은 JSB에 의해 확장되어 Cocos2d-x의 오브젝트와 구조, 타입을 지원합니다. 스파이더몽키는 모질라의 C/C++로 작성된 오픈 소스 자바스크립트 엔진으로 웹 브라우저뿐만 아니라 어떠한 C++ 프로그램도 연결할 수 있습니다.

C++ 코드는 JSAPI를 통해 스파이더몽키에 엑세스합니다. JSAPI는 자바스크립트 런타임을 설정하는 기능을 제공하 스크립트를 실행하고 컴파일하며 자바스크립트 데이터 구조, 에러 핸들링, 보안 체크, 스크립트 디버깅을 작성하고 검사합니다. 이 기술은 빠른 게임 개발과 게임 프로토타이핑에 사용됩니다.

### 1.1.3 Cocos2d 패밀리에서의 위치

다른 Cocos2d 브랜치(branch)와 비교하여 Cocos2d-JS는 웹게임과 네이티브 게임을 포함한 모든 플랫폼을 지원하는데 포커스를 맞추고 있습니다.

HTML5 게임은 모바일 게임 산업에서 더욱 중요해지고 있으며 계속 성장하고 있습니다. HTML5에 기반한 캐주얼 게임과 소셜 게임의 숫자는 이미 셀 수 없을 정도입니다.

Cocos2d-x가 대중적인 크로스 플랫폼 게임 프레임워크이지만 브라우져에는 접근할 수가 없습니다. Cocos2d-html5는 HTML5를 포함합니다 - 기본적으로 브라우져에서 실행할 수 있도록 만들어진 애플리케이션과 게임.

Cocos2d-html5는 HTML5 게임 세계에 배우기 쉽고 사용하기 쉬운 API 스타일을 가져옵니다. 또한 모든 기능과 높은 성능, 실시간 업데이팅, 설치할 필요 없이 클릭하면 바로 플레이가 가능하며 효율적인 개발 사이클 등 모든 것을 갖추고 있습니다. 

Cocos2d-x JSB에 감사하며, Cocos2d-JS는 웹과 네이티브 등 배포하길 원하는 플랫폼이 어디든 상관 없이 일관성 있는 개발 경험을 제공합니다. 이것은 거의 모든 채널에 배포할 수 있게 되므로 당신의 게임에 엄청난 기회를 제공합니다.
