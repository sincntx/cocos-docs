Cocos2d-JS v3.2 @ Dec.29, 2014

* Replaced `transform` function with `setTransform` function under canvas render mode for better performance.
* Added a timer in `cc.audioEngine` to check audio element loading event, prevent the loading process being stucked when load audio file failed. 
* Added some new browser types to `cc.sys`.
* Added some audio resource loading codes to ensure compatibility with Wechat browser.
* Added check for WebAudio support to ensure compatibility.
* [JSB]Upgraded Cocos2d-x to v3.3 Final.
* [JSB]Added `getSearchPaths` API to `jsb.Manifest` to support better script hot update.
* [JSB]Polished restart game feature.
* [JSB]Added a sample usage case for `jsb.AssetsManager`'s script hot update ability.
* [JSB]Skipped FlatBuffer related bindings.
* [JSB]Canceled modifications in Spine due to License restriction and removed new constructor for `sp.SkeletonAnimation`.

* Bug fixes:
    1. Fixed an issue that `cc.InputManager` doesn't trigger touch event on chrome mobile emulator.
	2. Fixed an issue that `cc.game.setFrameRate` doesn't work.
	3. Fixed an issue that `cc.view` can't remove resize event listener.
	4. Fixed an issue that `cc.EventManager` didn't set register flag to false when a listener is removed.
	5. Fixed an issue that `cc.audioEngine` doesn't play some audios on some iOS devices.
	6. Fixed an issue of ccui controls that their `setColor` doesn't work when cascade color is enabled.
	7. Fixed an issue that `ccs.Armature`'s `setColor` doesn't work in canvas render mode.
	8. Fixed an issue that `ccs.Armature` crashes when adding a child to it.
	9. Fixed an issue that `cc.SpriteBatchNode`'s status is incorrect in WebGL render mode.
	10. Fixed an issue of `cc.Layer` that its position is incorrect under bake mode.
	11. Fixed an issue of `ccui.RichText` that its `setContentSize` doesn't work.
	12. Fixed an issue of `cc.LabelTTF` that its `setColor` doesn't work when cascade color is enabled.
	13. Fixed an issue of spine that its skeletons position is incorrect when scaleX equals to -1 and scaleY equals to 1. 
    14. Fixed `sp.Skeleton`'s API inconsistence by renaming `boundingBox` to `getBoundingBox`.
    15. Removed all usages of deprecated create functions in the test cases.
	16. [JSB]Fixed an issue of `ccui.ScrollView`'s `innerWidth` and `innerHeight` properties.
    17. [JSB]Fixed an issue that setting `cc.Node`'s userData property will crash.
    18. [JSB]Fixed API inconsistence by renaming `jsb.fileUtils`'s `getByteArrayFromFile` to `getDataFromFile`.
    19. [JSB]Fixed a script file cache check issue in ScriptingCore.cpp.
    20. [JSB]Fixed an issue of `ccs.Armature`'s constructore.