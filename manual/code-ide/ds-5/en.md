# ARM DS-5 Promote Android Game Development 

## 1. What is DS-5?
ARM<sup>®</sup> DS-5 Development Studio is built on the standard Eclipse development environment providing outstanding windows management, project management, and C/C++ source code editing tools. DS-5 brings a huge number of features specific to ARM to the Eclipse platform, making it the most powerful toolchain available for ARM software development.

DS-5 series include Ultimate Edition, Professional and Community Edition. Cocos Code IDEARM Limited authorized Cocos Code IDE to release DS-5 Community Edition for developers to use.

[![](./res/arm-logo.png)](http://ds.arm.com/ds-5-community-edition/)

## 2. Downloads
Cocos Code IDE support DS-5 Community Edition since 1.1.0 version. However, due to the big installation package size, DS-5 provided by another installation package which was not integrated into the installation package.After downloading, install it in to Cocos Code IDE according to the following steps.

DS-5 Community Edition Install Package:  
-  [Click Here To Download](http://www.cocos2d-x.org/filedown/arm-ds-5-5.20.0.20141022-for-cci.zip)  
- __Size__: 250.7 MB(250,681,142 bytes)  
- __MD5__: 7f2aa372c4ab15b34c2b96f010d4fecb  

## 3. Features
Although DS-5 Community Edition is not so powerful like Professional and Ultimate, it's a great help to Android developers.

### Android Platform C++ Code Debugging Support
Android devices which debugging whose processors are based on ARM9, ARM11 or Cortex-A (ARMv7-A) architecture，be aware that some products based on version 2.2 (Froyo) haven't got this feature enabled.  
![](./res/ds-5-debug-feature.jpg)

### Android Streamline
Supports simple GPU / CPU functional analysis, note that only certain devices support this feature. For more information, please refer to[《DS-5 CE Android Streamline》](http://ds.arm.com/developer-resources/tutorials/android-performance-analysis-streamline-tutorial/)。  
![](./res/ds-5-streamline-feature.jpg)

## 4. installation

--------
1. Click the "Install New Software..." in "Help" menu.  
![](./res/install-new-software.jpg)
2. Click the "Add..." button, then click the "Archive..." button, you will be navigated to DS-5 install package.  
![](./res/locate-archive.jpg)
3. Next and next... After a required reboot, the installation was successful.Initial installation requires installation authorization file, then please select the community version.  
![](./res/ds-5-ask-license.jpg)
4. Double click DS-5 Debug view in the menu: "Windows"->"Open Perspective"->"Other...".  
![](./res/open-ds-5.jpg)

--------
When installation successful, let's begin to [Debug C++ Code with DS-5](./debug-with-ds-5/en.md).
