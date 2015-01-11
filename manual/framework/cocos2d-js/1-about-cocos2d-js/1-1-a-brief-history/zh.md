# 1.1 Cocos2d-JS介绍

<img src="http://files.cocos2d-x.org/images/orgsite/logo.png" height=180> 

[Cocos2d-JS](https://github.com/cocos2d/cocos2d-js) 是跨全平台的游戏引擎，采用原生JavaScript语言，可发布到包括Web平台，iOS，Android，Windows Phone8，Mac，Windows等平台，引擎基于MIT开源协议，完全开源，免费，易学易用，拥有活跃的社区支持。Cocos2d-JS让2D的游戏编程门槛更您低，使用更加容易和高效。和其他类似游戏框架相比，它定义了更加清晰的2D游戏编程的基本组件，采用易学易用的API设计，并采用全球领先、具备原生性能的脚本绑定解决方案实现游戏的跨原生平台发布，开发效率更高，使用上最简单。

Cocos2d-JS是Cocos2d-x的JavaScript版本，融合了[Cocos2d-HTML5](https://github.com/cocos2d/cocos2d-html5)和Cocos2d-x JavaScript Bindings（JSB）。它支持Cocos2d-x的所有核心特性并提供更简单易用的JavaScript风格API，基于Cocos2d-JS的框架，您可以方便的使用JavaScript语言进行游戏开发，快速构建原型进行验证，并让您的游戏跑在所有支持HTML5规范的浏览器上。由于Cocos2d-html5的API和Cocos2d-x JSB的API高度一致，可让您的游戏不用修改代码或者修改少量代码就可打包为原生性能表现的混合游戏，发布到原生应用市场，从而实现，一次编码全平台部署的效果，带给您全所未有的机遇。


#### 为什么选择Cocos2d-JS
为什么你会选择Cocos2d-JS游戏引擎而不是其他类似的引擎？

* 友好的JavaScript API设计 
* 全平台支持，无需插件，一次开发，全平台运行 - 网页, 桌面, 移动和主机平台
* 可在浏览器中完成游戏的开发和调试，然后发布到网页, 移动 还有主机平台
* 丰富的功能包括sprites, actions, animations, particles, transitions, timers, events (touch, keyboard, accelerometer, mouse), sound, file IO, persistence, skeletal animations
* 原生性能, 成熟可靠

 
### 1.1.1 历史说明

2010年，随着Android系统的流行，Cocos2d-x团队从Cocos2d-iPhone中派生出了Cocos2d-x分支，该分支的定位是高性能款平台移动游戏解决方案。在2011年底，谷歌赞助了Cocos2d-x团队移植Cocos2d-x到Cocos2d-HTML5版本，实现Web游戏类型的覆盖，特别是移动Web游戏的开发。

Cocos2d-HTML5项目从2012年1月开始启动，基于Cocos2d-x v2.0分支开始移植，并于2012年8约发布了第一个稳定版本v2.0。因为是基于Cocos2d-x v2.0，所以Cocos2d-html5第一版本直接就是v2.0，并没有发布v1.0的相关版本。与此同时，Zygna也帮助Cocos2d-x团队采用JavaScript绑定的技术，开发Cocos2d-x JSB的技术方案，从而让Cocos2d-html5具备跨原生游戏平台的能力。Cocos2d家族于2012年12约4日发布了第一个联合版本，从那时起，Cocos2d-html5的游戏就可以同步发布到Web平台和原生游戏平台。

2014年3月，为了提供更加一致的开发体验，Cocos2d-x团队将Cocos2d-x JSB模块从Cocos2d-x中抽离出来，和Cocos2d-html5进行整合升级，发布了Cocos2d-JS引擎，旨在提供更加清晰、简单的工作流，确保引擎内部的功能实现和API高度一致，提升跨平台的游戏开发体验。2014年9月12日，Cocos2d-x团队发布了Cocos2d-JS的首个稳定版本Cocos2d-JS v3.0。作为工作流整合后的第一个版本，Cocos2d-JS v3.0兼具了简单和强大：新的JavaScript风格API使得编码，测试和发布环节都变得异常轻松简单；同时v3.0还提供了诸多强大的新特性，比如Spine动画支持，支持热更新的资源管理器，对象缓冲池，JavaScript到Objective-C/JAVA反射等等。

### 1.1.2 Cocos2d-HTML5和Cocos2d-JSBindings
Cocos2d-html5是Cocos2d-JS的一个重要模块，是一个面向Web的游戏引擎，采用Canvas或者WebGL渲染，并完全兼容HTML5规范，所以基于Cocos2d-JS开发的游戏天然可运行在所有支持HTML5规范的浏览器。

如果您只关注于纯Web游戏开发，那么您还可以选择Cocos2d-JS Lite的版本，Lite版本提供Cocos2d-html5单引擎文件，可自由定制功能，并可直接嵌入到HTML页面可以开始游戏开发，提供更加简便的工作流，开发更加便捷，还兼具脚本文件体积小，性能高效等优点，具体的内容见后续的工作流章节的介绍。

Cocos2d-JS通过高性能解决方案Cocos2d-x JSB实现混合游戏的打包和发布。 Cocos2d-x JSB是一个介于原生代码和JavaScript代码的胶水层，实现两者之间的相互调用。 

JavaScript代码由Mozilla的JavaScript虚拟机SpiderMonkey进行解析和运行，同时这个虚拟机被改造为支持Cocos2d-x的类型，数据结构和对象。SpiderMonkey本身是由C/C++开发的，不仅可嵌在浏览器中，也嵌入到任何C++的程序中使用。

SpiderMonkey负责脚本的解析运行，创建和检查JavaScript的数据结构，处理各种错误，提供安全检查，调试脚本的功能，并通过JSAPI实现C++代码的调用。通过这项技术，可让开发者能用纯JavaScript来开发原生游戏，游戏的开发更加高效，原型构建和验证更加便捷。 


### 1.1.3 在Cocos2d家族中的定位

Cocos2d-JS和其他的Cocos2d分支相比，其跨平台的能力是最强的，使用难度也是最低的。HTML5游戏正在逐渐变得更加流行，在移动游戏行业中其比重越来越大，已有非常多的休闲游戏和社交游戏基于HTML5规范开发，是未来移动游戏发展的一个重要组成部分。

虽然Cocos2d-x是一个非常流行的跨平台移动游戏引擎，但是它依然没有办法覆盖web游戏，这正是Cocos2d-x团队开发Cocos2d-JS这个更强跨平台游戏引擎的原因。

Cocos2d-JS带来了易学易用的Cocos2d API到HTML5游戏开发领域，具备全功能和高性能的属性，游戏开发更加高效，其也秉承了HTML5游戏的实时更新，点击即玩的属性，不需要安装，具有更高的用户转换率，具备更强的竞争力。

Cocos2d-JS在原生游戏市场方面的表现也非常抢眼，该技术方案天然支持在线资源、脚本热更新，游戏开发效率更高，得益于Cocos2d-x JSB的高性能解决方案, Cocos2d-JS混合游戏在性能上也丝毫不逊原生游戏，可支持各种复杂酷炫的游戏效果呈现，目前已经有多款月收入超过千万级别的明星游戏诞生。
 						
