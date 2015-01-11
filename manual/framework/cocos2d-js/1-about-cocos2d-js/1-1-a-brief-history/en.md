# 1.1 A brief history

<img src="http://files.cocos2d-x.org/images/orgsite/logo.png" height=180> 

[Cocos2d-JS](https://github.com/cocos2d/cocos2d-js) is an open source game engine for web games and native games. It has a high performance, is user-friendly and supports multi-platform development. Supported platforms include web, Android, iOS, Windows Phone 8, Mac, Windows, etc. Cocos2d-JS makes 2D game programming easier and faster. It clarifies the key components of 2D game programming by being easy to learn and having an easy to use API. All of this combined makes it an outstanding framework compared to others.

Cocos2d-JS is the HTML5 version of Cocos2d-x, includes [Cocos2d-html5](https://github.com/cocos2d/cocos2d-html5) and Cocos2d-x JavaScript Binding (JSB). Using Cocos2d-JS, you can write games in JavaScript and run your games on browsers that support HTML5. The API is completely compatible between Cocos2d-html5 and Cocos2d-x JSB. This means that Cocos2d-JS games can be run using Cocos2d's "JavaScript Binding" on Cocos2d-x without or with very little modification.

#### Why choose Cocos2d-JS
Why would you want to choose Cocos2d-JS over other available game engines?

* Modern JS API 
* Full platform without a need for plugins, code once, run everywhere - web, desktop, mobile and console
* Capability to test and debug your game on the browsers and then push it to web, mobile or console target
* A vast API of functionality including sprites, actions, animations, particles, transitions, timers, events (touch, keyboard, accelerometer, mouse), sound, file IO, persistence, skeletal animations and more
* High performance, proven and reliable

     
### 1.1.1 History

With the rise of Android in 2010, the Cocos2d-x team branched Cocos2d-x from Cocos2d-iphone not only to focuses on Android platform, but also to target cross-platform support as well. In 2011, Google sponsored the Cocos2d-x team to port Cocos2d-x to Cocos2d-html5, which focuses on HTML5-ready browsers. 

The Cocos2d-html5 project was started January 29, 2012. The first stable release, version v2.0, based on Cocos2d-x v2.0 was released in August of 2012. Meanwhile, Zygna was helping Cocos2d-x team to develop the Cocos2d-x JSB solution to extend Cocos2d-html5's native platform ability. The first coordinated release of the Cocos2d family was released on December 4, 2012. Since then, games that are developed based on Cocos2d-html5 can be run on web and native platforms. 

Cocos2d-html5 and Cocos2d-x JSB were combined and upgraded to Cocos2d-JS in March of 2014 and the first stable version, v3.0, was released on September 12, 2014. In Cocos2d-JS v3.0, we reinvented the workflow for all platforms, providing a consistent development experience for whichever platform you want to distribute to no matter whether web and/or native. Cocos2d-JS v3.0 is super powerful and comes with a lot of cool new features such as: Editors Support, Assets Manager, Object Pool, JS to Objective-C/JAVA reflection, etc.

### 1.1.2 Cocos2d-html5 and Cocos2d-x JSB

Cocos2d-html5 is an important module of Cocos2d-JS. It is a pure HTML5 game engine, which is based on Canvas/WEBGL and is 100% compatible with HTML5. This ensures that a Cocos2d-JS project can easily be run on HTML5-ready browsers.

If you are only interested in developing casual games for the web, you can embed the Cocos2d-JS Lite Version which is extremely easy to use and light as a feather.

Cocos2d-JS supports running game code as native application via Cocos2d-x JSB without or little code modification.

Cocos2d-x JSB for C/C++ is the wrapper code that sits between the native code and the JavaScript code. JSB enables calls to the native code using JavaScript and vice-versa.

JavaScript code is interpreted by SpiderMonkey, Mozilla’s JavaScript virtual machine (VM). The JavaScript VM is extended by JSB to support Cocos2d-x types, structures, and objects.

SpiderMonkey is Mozilla's open source JavaScript engine written in C/C++, and it can be linked into any C++ program, not just web browsers.


C++ code accesses SpiderMonkey via the JSAPI. The JSAPI provides functions for setting up the JavaScript runtime, compiling and executing scripts, creating and examining JavaScript data structures, handling errors, enabling security checks, and debugging scripts. This technology is used for rapid game development and game prototyping.


### 1.1.3 Position in Cocos2d family

Compared to other products in the Cocos2d branch, Cocos2d-JS is focusses on full cross-platform support by allowing the development of web games and native games.

HTML5 games are becoming more and more important in the mobile gaming industry. There are already countless of casual and social games available in HTML5. 

Even though Cocos2d-x is a popular cross-platform game framework, it is not accessible to browsers. Cocos2d-html5 was created to embrace HTML5 – allowing applications and games created with it to run in browsers natively. 

Cocos2d-html5 brings an easy to learn and an easy to use API style to the HTML5 gaming world. All of this comes with full features, high performance, real-time updating, click-to-play without the need for installations, and efficient development cycles.

Thanks to Cocos2d-x JSB, Cocos2d-JS provides a consistent development experience for whichever platform you want to distribute to. This will bring your game great opportunities in almost all channels of distribution. 

 						
