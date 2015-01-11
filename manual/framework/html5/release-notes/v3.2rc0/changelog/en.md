Cocos2d-JS v3.2 RC0 @ Dec.11, 2014

* Refactoration of web engine by separating the render logic, the arthictecture level refactoration is now completed and brounght great performance improvement.
* Refactoration of web engine's resolution adaptation and audio engine with polyfilled adaptation logics for different devices and browsers. This ensures better compatibility and better extensibility for future needs.
* Added `setRotation` method to `ccui.ImageView`.
* Added a function that fill sprite with repeated texture in Canvas mode.
* Added `setLineHeight` method to `cc.LabelTTF`.
* Added `dumpAudioInfo` to `cc.audioEngine` for debugging purpose on mobile browser.
* Removed Cocos Studio's Protobuffer support from the framework.
* Added an outline shader sample.
* [JSB] Supported modulization for JSB.
* [JSB] Added restart game feature.
* [JSB] Bound all missed chipmunk API in JSB and added test cases for new features, fix some potential memory leak issues.
* [JSB] Added `cc.sys.cleanScript` API to remove a script's cache.
* [JSB] Upgrade Cocos2d-x to v3.3 RC1.
* [JSB] Change default Android compiler to gcc.
* [JSB] Added manual bindings for `cc.Node#pause`.
* [JSB] Added missing constants and functions.

* Bug fixes:
	1. Fixed an issue of `cc.Sprite` that its rendering is incorrect without texture.
	2. Fixed an issue of `cc.ClippingNode` that its stencil drawing is incorrect on Canvas Mode.
	3. Fixed an issue of `TextFieldReader` that it will throw an error when 'areaWidth' and 'areaHeight' equal to zero.
	4. Fixed an issue of `ccui.CheckBox` that its getSelectedState doesn't return its state.
	5. Fixed an issue of `cc.LabelTTF` that it doesn't update the string when its string become to empty string.
	6. Fixed an issue of `cc.ParticleSystem` that it can't change its texture mode and shape type in Canvas mode.
	7. Fixed an issue of `cc.Layer`'s bake function that its position is incorrect when cc.view's scale isn't 1.
	8. Fixed an issue of `ccs.ArmatureAnimation`'s `setMovementEventCallFunc` and `setFrameEventCallFunc`.
	9. Fixed an issue of `console.log` that it isn't a funtion on IE9.
	10. Fixed an issue of `CSLoader` that it will add duplicate resources to sprite frame cache.
	11. Fixed an issue of `cc.ProgressTimer` that its setColor is not taking effect. 
	12. Fixed an issue of `cc.loader` that it will throw an error when loading a remote texture.
    13. Upgrade html5 version chipmunk to the latest release.
    14. [JSB] Fixed an issue that the string return value can not be accessed in JavaScript to Objective-C reflection.
    15. [JSB] Fixed potential memory leaks in JavaScriptJavaBridge.
    16. [JSB] Fixed libcurl's relocation overflow linker issue in Android release mode.
    17. [JSB] Fixed an issue of `ccui.CheckBox`'s _ctor function.
    18. [JSB] Made `cc.MenuSpriteImage`'s set functions support sprite frame name as parameter.
    19. [JSB] Made ccui's `addEventListener` functions support one argument.
    20. [JSB] Made `ccs.ArmatureAnimation`'s `setFrameEventCallFunc` and `setMovementEventCallFunc` accepts one parameter.
    21. [JSB] Made project.json's configs - `frameRate` and `debugMode` take effect in JSB.