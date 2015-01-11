工程根目录config.json文件说明
===
---
config.json文件用于工程配置初始化，在程序运行之前配置好。

config.json文件结构
===
---
以下是 cocos2d-x lua 工程的 config.json的文件实例:

	{
	
    "init_cfg":{
       "isLandscape": true,
       "isWindowTop": false,
       "name": "CocosLuaGame",
       "width": 960,
       "height": 640,
       "entry": "src/main.lua",
	   "consolePort": 6010,
	   "uploadPort": 6020,
       "debugPort": 10000,
       "forwardConsolePort": 10089,
       "forwardUploadPort": 10091
    },
    "simulator_screen_size": [
        {
            "title": "iPhone 3Gs (480x320)",
            "width": 480,
            "height": 320
        },
        {
            "title": "iPhone 4 (960x640)",
            "width": 960,
            "height": 640
        },
        ....
    ]
	}
---	
##"init_cfg"##

####"isLandscape"####
布尔类型

横竖屏配置，如果为true为横屏，如果为false为竖屏

####"isWindowTop"####
布尔类型

窗口置顶配置，如果为true则窗口默认置顶，反之默认不置顶

####"entry"####
字符串类型

脚本启动入口文件相对工程根目录的文件路径,如:"src/main.lua"

####"name"####
字符串类型

工程名,显示在窗口标题中

**注:这个参数只在桌面系统下生效**
####"width"####
正整型

窗口宽

**注:这个参数只在桌面系统下生效**

####"height"####
正整型

窗口高

**注:这个参数只在桌面系统下生效**

####"consolePort"####
正整型

console端口

####"uploadPort"####
正整形

接收IDE上传文件的端口

####"debugPort"####
正整型

调试端口

####"forwardConsolePort""####
正整形

Android ADB 模式调试时，将这个端口映射到 Android 设备的 consolePort 上

####"forwardUploadPort""####
正整形

Android ADB 模式调试时，将这个端口映射到 Android 设备的 uploadPort 上

###注:所有的端口配置都只在桌面平台下生效###

---
##simulator_screen_size##
配置多种分辨率大小，可以自己添加或者删减，显示在runtime的view菜单中

**注:这个字段只在桌面系统下生效**

####"title"####
字符串类型

菜单标题. 如:"iPhone 3Gs (480x320)"

####"width"####
正整型

窗口宽

####"height"####
正整型

窗口高


---