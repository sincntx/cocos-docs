# Cocos2d-JS v3.2发布说明

<img src="http://files.cocos2d-x.org/images/orgsite/logo.png" height=180> 

Cocos2d-JS是Cocos2d-x的JavaScript版本，融合了Cocos2d-html5和Cocos2d-x JavaScript Bindings。它支持Cocos2d-x的所有核心特性并提供更简单易用的JavaScript风格API，并且天然支持原生、浏览器跨平台应用。

在3.x版中，Cocos2d-JS完成了不同平台工作流的彻底整合，为不同平台提供了统一的开发体验。无论开发web应用还是原生应用，都可以便捷地采用Cocos2d-JS实现“一次开发，全平台运行”。采用Cocos2d-JS开发的同一套JavaScript游戏代码，可以同时运行在Mac OS X, Windows, iOS, Android等原生平台、以及所有现代浏览器上，这将使得我们的开发者轻松覆盖几乎所有发行渠道，带来前所未有的机遇。另一方面，若开发者只想开发一款Web轻度休闲游戏，Cocos2d-JS也专门为此类游戏定制了Lite Version，直接将Cocos2d-JS Lite Version集成到页面中即可使用。

作为工作流整合后的版本，Cocos2d-JS v3.x兼具了简单和强大：新的JavaScript风格API使得编码，测试和发布环节都变得异常轻松简单；同时v3.x还提供了诸多强大的新特性，比如Spine动画支持，支持热更新的资源管理器，对象缓冲池，JS到Objective-C/JAVA反射等等。

随3.1版本发布的还有Facebook Integration for Cocos2d-JS v1.0，Cocos2d-JS正式在全平台支持Facebook的完整功能接入。对于希望为游戏添加社交功能的开发者来说，这将带来前所未有的机遇。使用同一套JavaScript代码，开发者将可以发布自己的游戏到Facebook Canvas，iOS和Android平台，真正实现全平台支持。

## 核心特性

* 重构Web引擎的渲染器，彻底分离渲染逻辑，至此，渲染器的框架改造已经完成。新渲染器不仅带来了渲染性能上的巨大提升，更清晰的渲染框架也让未来的优化更加轻松。
* 重构Web引擎的屏幕适配策略和音频引擎，为不同的设备和浏览器的特殊性定制行为，大幅提升兼容性和未来的扩展性。
* JSB中支持引擎模块裁剪，开发者可以通过注释掉绑定注册代码来在最终包中去除相应模块，达到减包的目的。目前安卓最小包是4.4mb，减包的具体方法参见升级指南。
* 添加重启游戏功能并稳定AssetsManager，开发者可以通过重启来让更新完成的脚本直接生效。
* 补全Chipmunk API的绑定，大大提升Cocos2d-JS对物理游戏的支持，让物理游戏可以更轻松得完成跨平台。

## 注意事项

关于编译和打包，还有一些限制条件需要满足：

- [Android编译] NDK版本建议使用r10c，如果不需要兼容Android 5.0可以使用r9d，不兼容NDK其他版本
- [iOS编译] Xcode版本必须在5.1.1以上
- [Web代码混淆] JRE或JDK版本必须使用1.6或1.7

## 下载

- [Cocos2d-JS v3.2](http://www.cocos2d-x.org/filedown/cocos2d-js-v3.2.zip)
- [在线API索引](http://www.cocos2d-x.org/reference/html5-js/V3.0/index.html)
- [下载版API索引](http://www.cocos2d-x.org/filedown/Cocos2d-JS-v3.2-API.zip)
- [在线测试例](http://cocos2d-x.org/js-tests/)

## 工作流

- 跨平台游戏开发者可以使用Cocos Console来创建项目，用Web引擎加速游戏开发，最终用Cocos Console将游戏发布到所有原生平台和Web平台。

- Web端轻度休闲游戏开发者可以直接下载单文件的Cocos2d-JS Lite Version，嵌入Web页面中，像使用jQuery那样进行开发。

![](../../v3.0/release-note/workflows.jpg)

## 详细更改

更详细的改动列表和升级文档可以参见:

- [Cocos2d-JS v3.2改动说明](http://www.cocos2d-x.org/docs/manual/framework/html5/release-notes/v3.2/changelog/en)
- [Cocos2d-JS v3.2升级指南](http://www.cocos2d-x.org/docs/manual/framework/html5/release-notes/v3.2rc0/upgrade-guide/zh)

## 从旧版本升级你的项目

如果你想升级你使用旧版本（从v3.0 Alpha开始）创建的项目到v3.2，你需要执行以下步骤：

1. 下载Cocos2d-JS v3.2引擎包。
2. 执行引擎包中的`setup.py`更新你的cocos命令。
3. 使用`cocos new`命令创建一个新的基于v3.2的项目。
4. 从你的旧项目中拷贝"src"，"res"，"index.html"，"project.json"，"main.js"到第三步创建的新项目并覆盖。
5. 最后你可能需要按照升级指南来升级你的项目以避免API不兼容的问题。

## 关于Cocos2d家族

- Cocos2d-JS v3.2使用Cocos2d-x v3.3作为JSB的底层实现。
- Cocos2d-JS v3.2兼容Cocos Code IDE v1.1.0。
- Cocos2d-JS v3.2兼容Cocos Studio v1.2 - v1.6，Cocos Studio 2中的FlatBuffer二进制格式没有办法在JS中被解析，所以暂时移除对Cocos Studio 2.0的支持，在3.3版本中我们会基于JSON解析来支持Cocos Studio 2。

如果遇到任何问题，你都可以向Cocos2d-JS开发者社区寻求帮助： 

- [官方论坛](http://www.cocoachina.com/bbs/thread.php?fid-59.html)
- [文档目录](http://cocos2d-x.org/docs/manual/framework/html5/zh)
- [开发指南](http://cn.cocos2d-x.org/article/index?type=cocos2d-x&url=/doc/cocos-docs-master/manual/framework/cocos2d-js/1-about-cocos2d-js/1-1-a-brief-history/zh.md)
- [Github仓库地址](https://github.com/cocos2d/cocos2d-js)
