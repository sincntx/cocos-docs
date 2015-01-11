Cocos Code IDE 1.1.0

	[NEW] ds-5集成	

相关文档：
	
[ARM DS-5 助力安卓游戏开发](http://cn.cocos2d-x.org/article/index?type=code-ide&url=/doc/cocos-docs-master/manual/code-ide/ds-5/zh.md)

[用 DS-5 调试 C++ 代码](http://cn.cocos2d-x.org/article/index?type=code-ide&url=/doc/cocos-docs-master/manual/code-ide/ds-5/debug-with-ds-5/zh.md)
	
    [NEW] 子类的能够提示父类的self
         
	          2个lua文件
	
			  <One.lua>
			  one = class("one")
			
			  function one:xyz()
			    self.a = "" 
			    self.b = {x=1, y=2}
			  end
			
			  <Two.lua>
			  two = class("Two", one)
			
			  function two:ttt()
			  --此处可以提示出self.a self.b和self.a.xx, self.b.xx
			  end

	[NEW] lua编辑器提示速度优化
	      
          1.提升提示速度。
          2.去掉延迟保护，比如说原先提示如果前1次提示3秒才出来，那么下一次也会3秒后才提示出来。
            现在去掉后，即使前一次提示用了3秒，也不影响后一次的提示速度。   
    
    [NEW] 支持调试包内的脚本：即调试时不上传任何资源

          在 Debug Configuration 页面的高级标签页中有一个控制是否上传文件到 runtime 的开关。
          只针对 android 和 iOS 有效，当选择不上传资源时，ide 不会将项目资源上传到 runtime 的
          writable path。用户需要自己保证已经将所需资源打包到 runtime 安装包中。
          这个选项只是为了让用户节省上传资源所需要的时间。
 
    [NEW] 减小独立安装包大小:去除了JDK，安装包大小271M-->153M
          
    [NEW] 安装时增加协议的显示    
             
          Windows：根据系统语言自动选择安装包显示的语言
          Mac：改成安装包的形式，根据系统语言自动选择安装包显示的语言

    [NEW] IDE 需要对cocos2d-x 3.3版本的要求进行检查：从cocos2d-x 3.3 RC1 版本 改用NDK 10C 版本。

	[FIX] 重新构建lua/js工程runtime后，导致runtime无法运行
          解决办法：需要将 xcode6 更新到 6.1 (6A1052d) 或以上版本，*更新完后一定要重启系统*问题就修复了。
	[FIX] 语言切换到中文，但是界面仍然是英文
	[FIX] android adb没有配置到系统变量，无法进行ds-5调试
          此问题是由开发者自己处理，文档中有说明（后面的小提示）
          http://cn.cocos2d-x.org/article/index?type=code-ide&url=/doc/cocos-docs-master/manual/code-ide/ds-5/debug-with-ds-5/zh.md
	[FIX] Run In Browser打开后页面显示黑屏
          这个问题是因为3.1的js引擎不支持IE9和IE10导致的，需要用IE11， firefox 或者 google chrome 
          测试下一个js版本（计划12.10发）才支持 IE9和IE10
	[FIX] [Mac][Windows]模拟器调试异常
          问题描述
          1.启动ios模拟器后但没开始调试，手动关闭模拟器
          2.重新使用ios模拟器调试
          结果：调试异常
          Session could not be started
    [FIX] 无法为js工程打包
          问题描述
          cocos-js引擎：3.1,3.3
          The NDK version is not r10c or above.
          这是js引擎的问题，会在 3.2 rc0 版本中修复。
    [FIX] [Lua编辑器] 当子类self错误输入成“slef”也能提示父类的属性
          	One.lua
			one = class("one")
			
			function one:xyz()
			self.a = "" 
			self.b = {x=1, y=2}
			end
			
			Two.lua
			two = class("Two", one)
			
			function two:ttt()
			--此处输入slef.b.也能提示出x,y
			end
     [FIX] lua编辑器复制粘贴或者鼠标在浮动窗口时可能会卡
           修复办法：复制粘贴等操作时，关闭浮动窗口功能。
     [FIX] lua 工程的config.json没有debugPort字段
     [FIX] 当class的super对象是自己时，提示自己的时候会引起卡死   
           local Hero = class("Hero", Hero)
           Hero.
     [FIX] lua编辑器一段时间不动，或者失去焦点后重新激活编辑器会卡顿。
     [FIX] Python路径未配置到环境变量，打包时若勾选“编译到字节码”会导致打包失败
           1.Python路径已经配置到Code IDE环境变量，但是没有在系统环境变量里面，即在命令行无法直接使用python命令
           2.打包apk时，勾选“编译到字节码”
     [FIX] lua编辑器保存的时候会卡顿
     [FIX] [Mac]首选项，可用软件站点默认窗口没有显示code ide 的更新站点
     [FIX] [Mac] 检查更新，找到更新后没有显示出来
     [FIX] [Lua编辑器] 当代码中有注释时，偶尔无法提示参数名
     [FIX] build runtime 成功页面，帮助按钮不可用，点击没效果(移除此按钮)
     [FIX] Android apk打包成功后，设备断开连接后，点安装，没有错误提示信息      
     [FIX] 导入工程时，如果引擎没有配置 ，会报空指针异常
     [FIX] JS工程调试中，打断点会响应比较慢


Cocos Code IDE 1.0.2
     

	[NEW] Live coding switch
	[NEW] Code Auto-complete feature enhancement
	[NEW] "Open Declaration" feature enhancement
	[NEW] Desktop runtime arguments support
	
	[FIX] Build iOS device runtime failed
	[FIX] Can't auto update on Windows
	[FIX] Add breakpoint failed in JavaScript occasionally
	[FIX] Delete js files in frameworks when add native code
	[FIX] Some other bugs

Cocos Code IDE 1.0.0-final

	[NEW] Xcode 6 iOS simulator support
	[NEW] Enable "Open Declaration" 
	[NEW] Linking files/directories support
	[NEW] New file uploading filter rules
	[NEW] Quick-cocos2d-x support
	
	[FIX] Reducing load times
	[FIX] PrbuiltRuntime.apk can't install to device on Windows
	[FIX] Some other bugs

Cocos Code IDE 1.0.0-rc2

	[NEW] JDK integration
	[NEW] Big improvements in JavaScript code Auto-complete
	[NEW] Lua API reference document integration
	[NEW] Lua code Auto-complete feature enhancement
	[NEW] Auto Update support
	
	[FIX] Crash when coding

Cocos Code IDE 1.0.0-rc1

	[NEW] Support remote debug
	[NEW] Framecache preview
	[NEW] Add marketplace
	[NEW] Create project with existing code and resource
	[NEW] Code Auto-complete feature enhancement
	
	[FIX] "Run in browser" button show incorrectly
	[FIX] Some other bugs

Cocos Code IDE 1.0.0-rc0

	[NEW] More stable when debug on remote device(ios/android)
	[NEW] Support for variable hover displaying
	[NEW] Code Auto-complete feature enhancement
	[NEW] Code Auto-complete performance improving
	[NEW] Support cocos project upgrading
	[NEW] Add some useful buttons on toolbar
	[NEW] Custom other ports instead of 6010/6050
	[NEW] Package an iOS IPA
	[NEW] Image preview
	
	[FIX] Lots of bugs

Cocos Code IDE 1.0.2.beta

    [NEW] Add a background to runtime's "Wait for debug" page
    [NEW] Rename filename
    
    [FIX] Lua debugger can't step into/step over
    [FIX] Can't build/publish runtime if use ant tools in adt
    [FIX] Only open a runtime when click Debug/Run more times
    [FIX] Some crashes of runtime
    [FIX] Some other bugs

Cocos Code IDE 1.0.1.beta

    [NEW] Less IDE/Debugger settings
    [NEW] Code Auto-complete feature enhancement
    [NEW] Use more CPU to build/publish android runtime
    [NEW] Support ignoring some files and directories to upload when debug
    [NEW] Give solutions when debug failed
    [NEW] JS: Support displaying value of variable in callstacks
    [NEW] Publish Android apk with debug.keystore
    [NEW] JS Runtime bind more C++ interface to script
    [NEW] Lua Runtime performance improve
    [NEW] Custom resolution, orientation and script entry file
    
    [FIX] Use setSearchPath in Lua/JavaScript
    [FIX] Windows Runtime's mouse event is not accurate
    [FIX] Missed some log
    [FIX] Non-Ascii characters are shown as messy codes
    [FIX] Mac runtime require OSX 10.9, now 10.8 is enough
    [FIX] Errors when project is big
    [FIX] Lots of bugs 
    
Cocos Code IDE 1.0.0.beta

    First publish version
    