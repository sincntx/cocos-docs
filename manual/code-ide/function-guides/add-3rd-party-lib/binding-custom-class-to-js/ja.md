カスタムクラスをjsランタイムにバインドするには。
===
---

このドキュメントはカスタムのcppクラスをJsのランタイムにバインドする方法を解説していきます。**jsバインディングに関する説明ではありません。**.

実行するために、全てのプラットフォームに対するシュミレーターを実行できるMacランタイムを使用して解説します。

### ランタイムのソースコードを作成
ここではCocos Code IDE で CocosJsGame という名前の cocos js project を作ることを仮定して解説します。
* ソースコードが置かれるのは\<projectLocation\>/frameworks/runtime-srcで、もし既に作成されている場合は以下の手順はスキップして構いません。
* 新たに作成する必要がある場合、以下の手順に沿って操作してください:
  * CocosJSGame projectを右クリックします
  * Cocos Tools->Add Native Codes Supportを選択
  * **Create Native Source Wizard** の **Generate** をクリック 
  * これによりソースコードが作成されます。

### プロジェクトにカスタムクラスを追加する
![](./res/custom_class_directory.png)

```

// CustomClass.h

#ifndef __CUSTOM__CLASS

#define __CUSTOM__CLASS

#include "cocos2d.h"

namespace cocos2d {
class CustomClass : public cocos2d::Ref
{
public:
    
    CustomClass();

    ~CustomClass();

    bool init();
    
    std::string helloMsg();

    CREATE_FUNC(CustomClass);
};
} //namespace cocos2d

#endif // __CUSTOM__CLASS

```

```
// CustomClass.cpp
#include "CustomClass.h"

USING_NS_CC;

CustomClass::CustomClass(){
    
}

CustomClass::~CustomClass(){
    
}

bool CustomClass::init(){
    return true;
}

std::string CustomClass::helloMsg() {
    return "Hello from CustomClass::sayHello";
}

```

**frameworks/runtime-src/proj.ios_mac/CocosJSGame.xcodeproj**を開き、CustomClass.h/CustomClass.cpp を cocos2d_libs.xcodeprojに追加します。また、以下の画像のように**cocos2dx iOS**にチェックが入っているか確認してください:
![](./res/select_files_in_targets.png)

以上をふまえ、以下の画像のようになっていればOKです: 

![](./res/customClassXCode.png)

パスの設定も行っておきます:

![](./res/searchPath.png)

バインドするファイルのパスを探し、追加します:

![](./res/binding_search_path.png)

### cocos2dx_custom.iniを追加する

`tools/tojs` を開き、`cocos2dx_custom.ini`というファイルを作成、追加します:

![](./res/custom_ini_directory.png)

各項目の説明:

```
[cocos2dx_custom]
# 作成した関数に追加するプレフィックスを変更します
#  通常は以下のようになっています
prefix = cocos2dx_custom

# 入れ子とする名前空間を作成 (javascriptは、これと同じようないくつかのコードを作成します。`ns = ns || {}`)
# これによって全てのクラスを名前空間内に配置出来ます。
target_namespace = cc

android_headers = -I%(androidndkdir)s/platforms/android-14/arch-arm/usr/include -I%(androidndkdir)s/sources/cxx-stl/gnu-libstdc++/4.7/libs/armeabi-v7a/include -I%(androidndkdir)s/sources/cxx-stl/gnu-libstdc++/4.7/include -I%(androidndkdir)s/sources/cxx-stl/gnu-libstdc++/4.8/libs/armeabi-v7a/include -I%(androidndkdir)s/sources/cxx-stl/gnu-libstdc++/4.8/include
android_flags = -D_SIZE_T_DEFINED_ 

clang_headers = -I%(clangllvmdir)s/lib/clang/3.3/include 
clang_flags = -nostdinc -x c++ -std=c++11

cocos_headers = -I%(cocosdir)s/cocos -I%(cocosdir)s/my -I%(cocosdir)s/cocos/base -I%(cocosdir)s/cocos/platform/android
cocos_flags = -DANDROID -DCOCOS2D_JAVASCRIPT

cxxgenerator_headers = 

# extra_arguments を書き換える
extra_arguments = %(android_headers)s %(clang_headers)s %(cxxgenerator_headers)s %(cocos_headers)s %(android_flags)s %(clang_flags)s %(cocos_flags)s %(extra_flags)s 

# ヘッダーを解析する
headers = %(cocosdir)s/cocos/my/CustomClass.h

# classesはコードを作成するためのものです。ここには正規表現を使用する事が出来ます。
# 正規表現は、"^$"によって囲まれた文になります。...例: "^Menu*$"
classes = CustomClass.*

# 何をスキップするかの指定。フォーマット: ClassName::[function function]
# クラス名の正規表現については、次のように使用します: "^ClassName$"
# 正規表現は、それらが全て"^$"に囲まれる事はありません。ただし、全てのクラスをスキップしたいという場合は例外です。
# "*"でもスキップの対象となります。いくつかの例については以下の項目を参照してください。基底クラス名は"*"となります。
# 全てのクラス名に適用されます。これはとても便利で、似た名前のものをスキップするのに役立ちます。
# 全てのクラスからの機能

skip = 

rename_functions = 

rename_classes = 

# 全てのクラス名において、ターゲットのVMに登録する際に削除する必要があるか？
remove_prefix = 

# クラスの親をルックアップしません。
classes_have_no_parents = 

# base classes which will be skipped when their sub-classes found them.
base_classes_to_skip = Ref Clonable

# コンストラクタの有無を設定
# 設定は手書きのコンストラクタと基底クラスを使用します。
abstract_classes = 

# スクリプト(Js)オブジェクトのライフサイクルをネイティブ(cpp)オブジェクトがコントロールするかどうか決めます。項目には'yes' もしくは 'no'を記述してください。
script_control_cpp = no


```

### tools/tojs/genbindings.py　を書き換える

tools/tojs/genbindings.pyの中から`custom_cmd_args`(Cocos2d-js 3.0 alpha 2以前のバージョンで行う場合、`cmd_args`です。)という文を探し、以下の一文を追加します:

```
  'cocos2dx_custom.ini' : ('cocos2dx_custom', 'jsb_cocos2dx_custom'), \
```
![](./res/genbindings_modify.png)

### tools/tojs/genbindings.pyを実行

tools/tojs/genbindings.pyを実行したら、`jsb_cocos2dx_custom.cpp` と `jsb_cocos2dx_custom.h` が frameworks/custom/auto directory(もしくはframeworks/js-bindings/bindings/auto directory if you use `cmd_args` replace `custom_cmd_args`)に作成されたのを確認してください:
![](./res/auto_generate_directory.png)

Xcodeプロジェクトに追加します:

![](./res/addScriptToXcode.png)

### jsの記録をとる

`jsb_cocos2dx_custom.hpp`をインクルードし、以下のように関数を呼び出します --> 

`register_all_cocos2dx_custom(JSContext* cx, JSObject* obj);`

以下が、この関数をカスタムクラスで呼び出した例になります。:

```
    ...
    #include "jsb_cocos2dx_custom.hpp"
    ...
    
	sc->addRegisterCallback(register_all_cocos2dx_custom);
    
#if (COCOS2D_DEBUG>0)
    if (startRuntime())
        return true;
#endif

    ScriptingCore::getInstance()->start();
    auto engine = ScriptingCore::getInstance();
    ScriptEngineManager::getInstance()->setScriptEngine(engine);
    ScriptingCore::getInstance()->runScript(ConfigParser::getInstance()->getEntryFile().c_str());   
```

### ランタイムの変更
Cocos Code IDEの操作:

 * CocosJSGame を右クリック
 * Cocos Tools->Build Runtime を選択
 * プラットフォームを選択肢し、ビルドを実行。

### カスタムクラスを使う場合
main.jsを編集し、以下のように使いたいクラスを宣言します:

```
	var customClass = cc.CustomClass.create();
    var msg = customClass.helloMsg()
    cc.log("customClass's msg is : " + msg)
```

### テスト実行
ランタイムの設定を完了した`CocosJSGame`を実行し、以下がコンソールに表示されれば成功です:

`customClass's msg is : Hello from CustomClass::sayHello`



