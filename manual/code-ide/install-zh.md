Cocos Code IDE安装指南
=========================

简介
----------
你可以通过[这篇文章](../zh.md)了解 Cocos Code IDE 的功能。

下载 Cocos Code IDE
----------
Cocos Code IDE 只支持 Cocos2d-x 3.x/Cocos2d-js 3.x 引擎。

对于 Windows 用户，需要首先确认一下你正在使用的 java 版本，可以通过在 cmd 窗口中输入命令 `java -version` 来确定，输出类似：
	
```
	java version "1.6.0_65" 
	Java(TM) SE Runtime Environment (build 1.6.0_65-b14-462-11M4609) 
	Java HotSpot(TM) 64-Bit Server VM (build 20.65-b04-462, mixed mode) 
```
	
这样你就可以确定你要下载的是 64 位还是 32 位的 IDE版本， 如果没有安装 java， 需要首先安装[JDK][JDK link]。

Mac 系统只提供了 64 位版本，不存在版本选择问题。

----

**Cocos2d-x 引擎和 Cocos Code IDE 版本兼容表：**

| IDE版本\Cocos2d-x 版本 | 3.2 Final | 3.3 rc0 | 3.3 rc1 | 3.3 final |
| -------------------- |:----------:| :------:| :-----: |:---------:|
| 1.1.0 			    | √ 		 | √       | √       | √         |
| 1.0.2 			    | √ 		 | √       | √       | x         |
| 1.0.1 			    | √ 		 | √       | x       | x         |
| 1.0.0-Final 			| √ 		 | √       | x       | x         |
| 1.0.0-RC2   			| √ 		 | x       | x       | x         |

---
**Cocos2d-js 引擎和 Cocos Code IDE 版本兼容表：**

| IDE版本\Cocos2d-js 版本 | 3.0 Final | 3.1 Final | 3.2 rc0 |
| -------------------- |:-----------:| :--------:| :-----: |
| 1.1.0 			    | √ 		  | √         | √       |
| 1.0.2 			    | √ 		  | √         | x       |
| 1.0.1 			    | √ 		  | √         | x       |
| 1.0.0-Final 			| √ 		  | √         | x       |
| 1.0.0-RC2   			| √ 		  | x         | x       |

请参考上表选择 Cocos Code IDE 和 Cocos2d-x/Cocos2d-js，并统一到 [Cocos 下载页][cocos download page] 下载。

如何安装
------------

### 基本需求

+ **[Windows 用户]** 安装 [Python 2.7.x][Python link]，需要 2.7.5 或以上版本，不支持 3.x 版本。
+ **Cocos Code IDE 安装路径不可以包含中文等非 ascii 值**
	
### 额外需求

* 如果要在 iOS Simulator 上调试，需要安装 XCode 5.1 或以上版本

* 如果要在 android 设备上调试，需要安装 [Android SDK][Android SDK link]

* 如果你想要定制自己的 runtime，你需要：

	| 目标平台      | 工具 |
	| ------------- |:----------------------------:|
	| Mac OS X/iOS      | XCode 5.1或以上版本 		|
	| Windows       | VS2012 或以上版本 |
	| Android       | [Android SDK][Android SDK link], [NDK(**r9d版本**)][NDK link], [ANT][ANT link] |
	
如何更新版本
------------
+ 从 1.0.0-RC2 版本开始，IDE 已经支持在线更新功能，当有新版本发布的使用，可以通过 Help->Check for Updates 来进行更新
+ 如果无法检测到更新，你也可以通过 Help->Install New Software... 并使用 "http://ide-update.cocos2d-x.org/update/stable/" 安装更新。
+ 当然，你也可以将[更新包下载][update link]到本地后再通过 Help->Install New Software... 安装更新。

PS：更新后重启 IDE，如果发现 IDE 工作不正常可以再重启一次，之后就一切正常了。
	
已有的 Cocos2d 项目如何使用 Code IDE开发
----------

如果你的项目正在使用 cocos2d-x/cocos2d-js 3.x 引擎进行开发，现在可以很容易的切换到 Cocos Code IDE，你需要做的只是：

* 通过 IDE 创建一个对应的 Cocos Lua/JavaScript 示例工程
* 用项目资源（脚本、图片等）替换掉示例工程中的资源

入门指南
----------

* 如果你是Lua开发者，请[点击这里](getting-started-for-lua/1-creating-a-cocos-game/zh.md)。
* 如果你是JavaScript开发者，请[点击这里](getting-started-for-js/1-creating-a-cocos-game/zh.md)。

[JDK link]: http://www.oracle.com/technetwork/java/javase/downloads/index.html 
[Android SDK link]: https://developer.android.com/sdk/index.html?hl=sk
[NDK link]: https://developer.android.com/tools/sdk/ndk/
[ANT link]: http://ant.apache.org/
[Python link]: http://www.python.org/download
[cocos download page]: http://download.cocos2d-x.org
[update link]:http://www.cocos2d-x.org/filedown/cocos-code-ide-1.0.2-update.zip
