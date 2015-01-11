# Cocos2d-JS

<img src="http://www.cocos2d-x.org/attachments/download/1508" height=180> 

Cocos2d-JS is Cocos2d-x engine's JavaScript version that includes Cocos2d-html5 and Cocos2d-x JavaScript Bindings. It equips your game with cross-browser and cross-platform abilities, accompanied by full Cocos2d-x features and simplified JavaScript friendly APIs.

Cocos2d-JS reinvented workflows for all platforms in v3.0, it provides a consistent development experience for whichever platform you want to distribute to, no matter web and native. "Code once, run everywhere" is incredibly easy and natural in Cocos2d-JS. With one single JavaScript code base, you can run your game on all web browsers and native platforms including Mac OS, Windows, iOS and Android. This will bring your game great opportunities in almost all channels of distribution. On the other hand, if you are only interested in casual games on the web, you can embed directly in your web page the Cocos2d-JS Lite Version which is extremely easy to use and light as a feather.

Furthermore, JavaScript friendly APIs make your game development experience a breeze - easy to code, test and distribute. In the meantime, Cocos2d-JS v3.0 is super powerful along with all these cool new features: Editors Support, Assets Manager, Object Pool, JS to Objective-C/JAVA reflection, etc.

## Workflows

- Cross platforms developers can use Cocos Console to create projects, boost their development with web version engine and deploy games onto all native platforms and all browsers with Cocos Console.

- Casual web game developers can download the Lite Version and start to develop just like using other web frameworks (e.g. jQuery).

## Download and API reference

- [Cocos2d-JS github repository](http://github.com/cocos2d/cocos2d-js/)
- [Cocos2d-JS Full Version Download](http://www.cocos2d-x.org/download)
- [Cocos2d-JS Lite Version](http://www.cocos2d-x.org/filecenter/jsbuilder)
- [Online API reference](http://www.cocos2d-x.org/wiki/Reference)
- [Downloadable API reference](http://www.cocos2d-x.org/filedown/Cocos2d-JS-v3.0-API.zip)
- [Online test cases](http://cocos2d-x.org/js-tests/)

## Main features

* Support All modern browsers and native platforms
* Scene management (workflow)
* Transitions between scenes
* Sprites and Sprite Sheets
* Effects: Lens, Ripple, Waves, Liquid, etc.
* Actions (behaviours):
    * Transformation Actions: Move, Rotate, Scale, Fade, Tint, etc.
    * Composable actions: Sequence, Spawn, Repeat, Reverse
    * Ease Actions: Exp, Sin, Cubic, Elastic, etc.
    * Misc actions: CallFunc, OrbitCamera, Follow, Tween
* Assets manager (hot update)
* Basic menus and buttons
* Integrated with physics engines: Chipmunk and Box2d
* Particle system
* Skeleton Animations: Spine and Armature support
* Fonts:
    * Fast font rendering using Fixed and Variable width fonts
    * Support for .ttf fonts
* Tile Map support: Orthogonal, Isometric and Hexagonal
* Parallax scrolling
* Motion Streak
* Render To Texture
* Touch/Accelerometer on mobile devices
* Touch/Mouse/Keyboard on desktop
* Sound Engine support (CocosDenshion library) based on OpenAL or WebAudio on web
* Integrated Slow motion/Fast forward
* Fast and compressed textures: PVR compressed and uncompressed textures, ETC1 compressed textures, and more
* Resolution Independence
* Modularized engine for customization
* Open Source Commercial Friendly: Compatible with open and closed source projects
* OpenGL ES 2.0 (mobile) / OpenGL 2.1 (desktop) based
* Full WebGL support and auto canvas fallback
   
## Documents

- [Highlighted release note of Cocos2d-JS v3.2](./release-notes/v3.2/release-note/en.md)
- [Changelog of Cocos2d-JS v3.2](./release-notes/v3.2/changelog/en.md)
- [Upgrade guide to Cocos2d-JS v3.2](./release-notes/v3.2rc0/upgrade-guide/en.md)
- Startup
    - [Lite Version workflow](./v3/lite-version/en.md)
    - [Why use Cocos2d-html5 for Game Development](./v2/cocosh5-advantages/en.md)
    - [Resolution Policy Design for Cocos2d-JS](./v2/resolution-policy-design/en.md)
    - [History release notes](./release-notes/en.md)
        
- New features and API changes in version 3.x:
    - [New workflow with cocos console](./v2/cocos-console/en.md)
    - [Assets manager](./v3/assets-manager/en.md)
    - [New event manager](./v3/eventManager/en.md)
    - [New property API](./v3/getter-setter-api/en.md)
    - [Game creation](./v3/cc-game/en.md)
    - [Construction and inheritance](./v3/inheritance/en.md)
    - [Simplified action APIs](./v3/cc-actions/en.md)
    - [Objects Pool](./v3/cc-pool/en.md)
    - [Bake Layer](./v3/bake-layer/en.md)
    - [Reflection from Javascript to JAVA](./v3/reflection/en.md)
    - [Reflection from Javascript to Objective-C](./v3/reflection-oc/en.md)
    - [Cocos2d-html5 modulization](./v3/moduleconfig-json/en.md)
    - [Pure configuration file](./v3/project-json/en.md)
    - [Basic data refactorization](./v3/basic-data/en.md)
    - [Singleton objects refactorization](./v3/singleton-objs/en.md)
    - [Loading resource with cc.loader](./v3/cc-loader/en.md)
    - [System information in cc.sys](./v3/cc-sys/en.md)
    - [Path management with cc.path](./v3/cc-path/en.md)
    - [Asynchronised process with cc.async](./v3/cc-async/en.md)
    - [Modification to cc.saxParser](./v3/cc-saxparser/en.md)
    - [Modification to cc.spriteFrameCache](./v3/cc-spriteframecache/en.md)
    - [About cc.FileUtils](./v3/cc-fileutils/en.md)
    - [About cc.log](./v3/cc-log/en.md)
    - [Other change from v2.2.2 to v3.x](./v3/more-change-from-v2-to-v3/en.md)
    
- Facebook support for Cocos2d-JS
    - [Cocos2d-x with Facebook](./facebook-sdk/en.md)
    - [Facebook API Reference for Cocos2d-JS](./facebook-sdk/api-reference/en.md)
    - [Facebook integration instruction for Cocos2d-JS on Android](./facebook-sdk/facebook-sdk-on-android/en.md)
    - [Facebook integration instruction for Cocos2d-JS on iOS](./facebook-sdk/facebook-sdk-on-ios/en.md)
    - [Facebook integration instruction for Cocos2d-JS on Web](./facebook-sdk/facebook-sdk-on-web/en.md)
    - [How to integrate with Facebook - sample app](./facebook-sdk/facebook-test-case/en.md)

- Advanced topics
    - [How to compile Cocos2d-JS project in Eclipse](./jsb/compilation-in-eclipse/en.md)
    - [How to use extensions in JSB(Chinese version)](./jsb/jsb-extension/zh.md)
    - [How to use Plugin-x on Android](./jsb/plugin-x/how-to-use-plugin-x-on-android/en.md)
    - [Plugin-x architecture](./jsb/plugin-x/plugin-x-architecture/en.md)
    - [How to write your own Plugin for Android](./jsb/plugin-x/how-to-write-your-own-plugin-for-android/en.md)
    - [Use iOS IAP Plugin](./jsb/plugin-x/ios-iap/en.md)

- Tutorials
    - [Tutorial root](http://cocos2d-x.org/docs/tutorial/framework/html5/en)
