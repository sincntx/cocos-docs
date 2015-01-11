#从Cocos2d-JS v3.1到v3.2升级指南

## 0. 升级到Cocos2d-JS v3.1

如果你还在使用Cocos2d-html5或者较早版本的Cocos2d-JS，你可以通过之前版本的升级指南来首先升级 : [Cocos2d-JS v3.1升级指南](../../v3.0rc0/upgrade-guide/zh.md)

## 1. JSB中基于模块化裁减包大小

在Cocos2d-JS v3.2工程的编译过程中，如果一个Cocos2d-x模块及其相关的JavaScript绑定代码没有被使用到，那么它们会自动被排除出最终的包。你可能会奇怪，在Web引擎的模块化设计中，你可以在project.json文件的`modules`字段中填写自己需要的模块。然后，这种配置方式在JSB中并没有效果，你需要按照下面的方式在JSB中来排除一个你不需要的模块：

在`AppDelegate.cpp`中，你会发现`applicationDidFinishLaunching`函数中注册了所有的JavaScript绑定。如果某个模块的JavaScript绑定的注册代码被注释掉，那么它所对应的C++基础模块也不会被使用到，链接过程中链接器就会将它去除。这个过程是链接器的通用过程，所以这个方法对iOS和Android应用都有效。当然，所有没有注册JavaScript绑定的模块在JS代码中也是无法被使用的。

最后，你只需要再次编译你的工程。目前Cocos2d-JS v3.2编译出的最小的Android包是4.4mb。

```
bool AppDelegate::applicationDidFinishLaunching()
{
    // initialize director
    auto director = Director::getInstance();
	auto glview = director->getOpenGLView();
	if(!glview) {
		glview = cocos2d::GLViewImpl::createWithRect("Release3_2", Rect(0,0,900,640));
		director->setOpenGLView(glview);
	}

    // set FPS. the default value is 1.0/60 if you don't call this
    director->setAnimationInterval(1.0 / 60);
    
    ScriptingCore* sc = ScriptingCore::getInstance();
    sc->addRegisterCallback(register_all_cocos2dx);
    sc->addRegisterCallback(register_cocos2dx_js_core);
    sc->addRegisterCallback(register_cocos2dx_js_extensions);
    sc->addRegisterCallback(jsb_register_system);

    // extension can be commented out to reduce the package
    sc->addRegisterCallback(register_all_cocos2dx_extension);
    sc->addRegisterCallback(register_all_cocos2dx_extension_manual);

    // chipmunk can be commented out to reduce the package
    sc->addRegisterCallback(jsb_register_chipmunk);
    // opengl can be commented out to reduce the package
    sc->addRegisterCallback(JSB_register_opengl);
    
    // builder can be commented out to reduce the package
    sc->addRegisterCallback(register_all_cocos2dx_builder);
    sc->addRegisterCallback(register_CCBuilderReader);
    
    // ui can be commented out to reduce the package, attension studio need ui module
    sc->addRegisterCallback(register_all_cocos2dx_ui);
    sc->addRegisterCallback(register_all_cocos2dx_ui_manual);

    // studio can be commented out to reduce the package, 
    sc->addRegisterCallback(register_all_cocos2dx_studio);
    sc->addRegisterCallback(register_all_cocos2dx_studio_manual);
    
    // spine can be commented out to reduce the package
    sc->addRegisterCallback(register_all_cocos2dx_spine);
    sc->addRegisterCallback(register_all_cocos2dx_spine_manual);
    
    // XmlHttpRequest can be commented out to reduce the package
    sc->addRegisterCallback(MinXmlHttpRequest::_js_register);
    // websocket can be commented out to reduce the package
    sc->addRegisterCallback(register_jsb_websocket);
    // sokcet io can be commented out to reduce the package
    sc->addRegisterCallback(register_jsb_socketio);
    
#if (CC_TARGET_PLATFORM == CC_PLATFORM_ANDROID)
    sc->addRegisterCallback(JavascriptJavaBridge::_js_register);
#elif (CC_TARGET_PLATFORM == CC_PLATFORM_IOS || CC_TARGET_PLATFORM == CC_PLATFORM_MAC)
    sc->addRegisterCallback(JavaScriptObjCBridge::_js_register);
#endif
    sc->start();    
    sc->runScript("script/jsb_boot.js");
    ScriptEngineProtocol *engine = ScriptingCore::getInstance();
	ScriptEngineManager::getInstance()->setScriptEngine(engine);
	ScriptingCore::getInstance()->runScript("main.js");

    return true;
}
```

## 2. 重启游戏功能和热更新相关

从Cocos2d-JS v3.0 Beta开始，我们提供了资源和脚本的热更新能力。经过几个月的迭代，这个功能被大幅度强化，并且有很多成熟的商业项目开始使用内置的热更新机制来给广大玩家推送游戏更新。同时受益于我们的开发者，我们也收集到了很多的建议和需求。在v3.2中，我们觉得添加两个最重要的功能：

1. 清除脚本缓存

    一个脚本在被执行后就会被添加到JSB的缓存中，所以游戏中即便用于覆盖旧脚本的新脚本被更新下来，通过`require`也无法让新的脚本生效。在这种情况下，我们提供了`cleanScript` API来清除它的缓存：

    ```
    cc.sys.cleanScript(scriptPath);
    ```

2. 重启游戏

    经常发生的是，当热更新结束后，游戏需要被完全重启来让热更新更好得生效。所以我们提供了重启游戏的API，它会做下面一些事情：
    
    1. 清除Cocos2d-x中的存储和环境
    2. 重新启动一个干净的JavaScript虚拟机
    3. 重新绑定所有的绑定代码
    4. 重新执行main.js
    
    对应的API是：

    ```
    cc.game.restart()
    ```
    
3. Manifest新API：getSearchPaths

    如果想要热更新下载下来的脚本生效，有两个必要条件必须满足：
    
    1. 脚本被热更新正常更新
    2. 在每次启动时，必须在游戏的`cc.game.run()`之前添加新脚本对应的搜索路径，因为`cc.game.run`函数会去加载用户脚本，在这之前设置好搜索路径，那么新的脚本就会被加载。
    
    这意味着搜索路径必须被固化得存储起来，也就意味着Manifest对象对应的搜索路径必须可以被获取。至于如何存储这些搜索路径，开发者可以通过自己希望的任意方式做到这点，这里推荐的是`cc.sys.localStorage`。下面是热更新完成之后建议的处理逻辑：
    
    ```
    // 在热更新成功之后，更新下来的最新版本Manifest将成为本地的默认Manfiest
    var searchPaths = assetsManager.getLocalManifest().getSearchPaths();
    // 将搜索路径转换成JSON字符串并通过cc.sys.localStorage存储到本地固化存储中，以便在游戏重启后获取并添加
    cc.sys.localStorage.setItem("AssetsSearchPaths", JSON.stringify(searchPaths));
    // 直接重新启动游戏来让脚本生效
    cc.game.restart();
    ```

希望这些新的API可以让游戏的热更新变得更加方便。