# Cocos2d-JS

<img src="http://www.cocos2d-x.org/attachments/download/1508" height=180> 

Cocos2d-JS是Cocos2d-x的JavaScript版本，融合了Cocos2d-html5和Cocos2d-x JavaScript Bindings。它支持Cocos2d-x的所有核心特性并提供更简单易用的JavaScript风格API，并且天然支持原生、浏览器跨平台应用。

在3.0版中，Cocos2d-JS完成了不同平台工作流的彻底整合，为不同平台提供了统一的开发体验。无论开发web应用还是原生应用，都可以便捷地采用Cocos2d-JS实现“一次开发，全平台运行”。采用Cocos2d-JS开发的同一套JavaScript游戏代码，可以同时运行在Mac OS X, Windows, iOS, Android等原生平台、以及所有现代浏览器上，这将使得我们的开发者轻松覆盖几乎所有发行渠道，带来前所未有的机遇。另一方面，若开发者只想开发一款Web轻度休闲游戏，Cocos2d-JS也专门为此类游戏定制了Lite Version，直接将Cocos2d-JS Lite Version集成到页面中即可使用。

作为工作流整合后的第一个版本，Cocos2d-JS v3.0兼具了简单和强大：新的JavaScript风格API使得编码，测试和发布环节都变得异常轻松简单；同时v3.0还提供了诸多强大的新特性，比如Spine动画支持，支持热更新的资源管理器，对象缓冲池，JS到Objective-C/JAVA反射等等。

## 工作流

- 跨平台游戏开发者可以使用Cocos Console来创建项目，用Web引擎加速游戏开发，最终用Cocos Console将游戏发布到所有原生平台和Web平台。

- Web端轻度休闲游戏开发者可以直接下载单文件的Cocos2d-JS Lite Version，嵌入Web页面中，像使用jQuery那样进行开发。

## 下载与API索引

- [Cocos2d-JS github仓库](http://github.com/cocos2d/cocos2d-js/)
- [Cocos2d-JS Full Version下载链接](http://cn.cocos2d-x.org/download)
- [Cocos2d-JS Lite Version下载链接](http://www.cocos2d-x.org/filecenter/jsbuilder)
- [在线API索引](http://www.cocos2d-x.org/wiki/Reference)
- [下载API索引](http://www.cocos2d-x.org/filedown/Cocos2d-JS-v3.0-API.zip)
- [在线测试例](http://cocos2d-x.org/js-tests/)

## 主要特性

* 主持所有现代浏览器和原生平台（Android, iOS, Mac OSX, Windows）
* 场景管理
* 场景切换特效
* 精灵与精灵帧动画
* 特效：Lens, Ripple, Waves, Liquid, 等等.
* 动作：
    * 普通动作：Move, Rotate, Scale, Fade, Tint, etc.
    * 组合动作：Sequence, Spawn, Repeat, Reverse
    * 变速动作：Exp, Sin, Cubic, Elastic, etc.
    * 其他动作：CallFunc, OrbitCamera, Follow, Tween
* 资源管理器（热更新）
* 菜单与按钮
* 集成物理引擎：Chipmunk或Box2d
* 粒子系统
* 骨骼动画：支持Spine和Armature
* 字体：
    * 固定或可变宽度字体快速渲染
    * 支持.ttf字体
* 瓦片地图支持：正交，等距和六边形
* 视差滚动
* 运动轨迹特效
* 绘制到纹理
* 移动设备上的触摸和加速度计支持
* 桌面设备上的触摸，鼠标和键盘支持
* 声音引擎支持，基于OpenAL或WebAudio
* 集成慢动作，快进效果
* 高效压缩纹理支持：PVR压缩或未压缩纹理，ETC1压缩纹理
* 独立于分辨率的适配
* 可定制的模块化引擎
* 友好开源项目：适用于任何开源或闭源项目
* 基于OpenGL ES 2.0（移动设备）／ OpenGL 2.1（桌面设备）
* 完整WebGL支持和在不支持WebGL设备上自动使用Canvas
   
## 文档

- [Cocos2d-JS v3.2发布说明](./release-notes/v3.2/release-note/zh.md)
- [Cocos2d-JS v3.2改动列表](./release-notes/v3.2/changelog/en.md)
- [Cocos2d-JS v3.2升级指南](./release-notes/v3.2rc0/upgrade-guide/zh.md)

- 综述
    - [Lite Version工作流](./v3/lite-version/zh.md)
	- [Cocos2d-JS 2.x新手入门](./v2/getting-started_with-cocos2d-html5/zh.md)
	- [历史发布说明](./release-notes/zh.md)
	
- 初步了解Cocos2d-html5
    - [如何搭建Cocos2d-JS开发调试环境](./v2/setup-devenv/zh.md)
    - [如何自定义Cocos2d-JS加载界面](./v2/customize-loading-screen/zh.md)
    - [Cocos2d-JS的屏幕适配方案](./v2/resolution-policy-design/zh.md)
    - [月亮战士——Cocos2d-html5游戏展示](./v2/moonwarriors-cocos2d-html5-showcase/zh.md)
    
- Cocos2d-html5 v3.x的新功能
    - [使用Cocos Console管理工程](./v2/cocos-console/zh.md)
    - [资源管理器](./v3/assets-manager/zh.md)
    - [事件管理器](./v3/eventManager/zh.md)
    - [属性风格API](./v3/getter-setter-api/zh.md)
    - [简化的游戏启动流程](./v3/cc-game/zh.md)
    - [对象构造与类继承](./v3/inheritance/zh.md)
    - [简化action的使用](./v3/cc-actions/zh.md)
    - [对象缓冲池](./v3/cc-pool/zh.md)
    - [Bake Layer](./v3/bake-layer/zh.md)
    - [Javascript到JAVA反射](./v3/reflection/zh.md)
    - [Javascript到Objective-C反射](./v3/reflection-oc/zh.md)
    - [Cocos2d-html5模块化](./v3/moduleconfig-json/zh.md)
    - [项目配置文件](./v3/project-json/zh.md)
    - [基础数据类型重构](./v3/basic-data/zh.md)
    - [单例对象重构](./v3/singleton-objs/zh.md)
    - [统一create函数](./v3/create-api/zh.md)
    - [使用cc.loader加载资源](./v3/cc-loader/zh.md)
    - [资源路径工具cc.path](./v3/cc-path/zh.md)
    - [系统信息](./v3/cc-sys/zh.md)
    - [异步函数工具cc.async](./v3/cc-async/zh.md)
    - [cc.saxParser的改造](./v3/cc-saxparser/zh.md)
    - [cc.spriteFrameCache的改造](./v3/cc-spriteframecache/zh.md)
    - [cc.FileUtils的移除](./v3/cc-fileutils/zh.md)
    - [cc.log的改造](./v3/cc-log/zh.md)
    - [其他3.0版的API改动](./v3/more-change-from-v2-to-v3/zh.md)
    
- 进阶主题
    - [如何使用Eclipse中编译Cocos2d-JS项目](./jsb/compilation-in-eclipse/zh.md)
    - [如何在JSB项目中使用extension](./jsb/jsb-extension/zh.md)
    - [在Android平台使用Plugin-x](./jsb/plugin-x/how-to-use-plugin-x-on-android/zh.md)
    - [Plugin-x的框架](./jsb/plugin-x/plugin-x-architecture/zh.md)
    - [如何为Android开发自己的Plugin](./jsb/plugin-x/how-to-write-your-own-plugin-for-android/zh.md)
    - [使用iOS支付插件](./jsb/plugin-x/ios-iap/zh.md)
    - Facebook Integration for Cocos2d-JS
        - [Cocos2d-x的Facebook集成](./facebook-sdk/zh.md)
        - [Facebook API Reference for Cocos2d-JS](./facebook-sdk/api-reference/zh.md)
        - [Android平台上如何集成Facebook平台支持](./facebook-sdk/facebook-sdk-on-android/zh.md)
        - [iOS平台上如何集成Facebook平台支持](./facebook-sdk/facebook-sdk-on-ios/zh.md)
        - [Web平台上如何集成Facebook平台支持](./facebook-sdk/facebook-sdk-on-web/zh.md)
        - [集成Facebook平台 - 测试工程](./facebook-sdk/facebook-test-case/zh.md)

- 教程
    - [教程目录](../../../tutorial/framework/html5/zh.md)

