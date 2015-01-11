# 今までのObjective-C風の書き方からC++11を意識した書き方へ方向性が変わりました

##Objective-C風の書き方から変更した点
###クラスや関数にCCの接頭辞は必要なくなりました
####クラス名の変更
*cocos2d*という名前空間内に置かれているのは変わりませんが、*CC*という接頭辞を撤廃しました。

例:

|v2.1|v3.0|
|---|---|
|CCSprite|Sprite|
|CCNode|Node|
|CCDirector|Director|
|etc...|etc...|

*メモ* v2.1 では*CC*という接頭辞をつける必要がありましたが、それらは全て必要なくなります。

####フリーな関数も同様に
例えばプリミティブを描画する関数について:

- それらの関数は*DrawPrimitives*という名前空間内に置かれます。
- *cc* 接頭辞は必要なくなります。

GLを使う関数について:

- それらの関数は*GL*という名前空間内に置かれます。
- The *ccGL* prefix was removed

例:


|v2.1|v3.0|
|---|---|
|ccDrawPoint()|DrawPrimitives::drawPoint()|
|ccDrawCircle()|DrawPrimitives::drawCircle()|
|ccGLBlendFunc()|GL::blendFunc()|
|ccGLBindTexture2D()|GL::bindTexture2D()|
|etc...|etc...|

クラスと同様にv2.1では必要な接頭辞もv3.0以降では撤廃されます。 

### インスタンスのコピーについて
*clone()* はautorelease済のコピーを返します。

*copy()* はサポートされないので、この関数を使用している場合、予期しない動作をする場合があります。

例:

```
// v2.1
CCMoveBy *action = (CCMoveBy*) move->copy();
action->autorelease();
// v3.0
// autoreleaseを実行する必要はありません。
auto action = move->clone();
```
### シングルトンの getInstance() 及び destroyInstance() について
全てのシングルトンは *getInstance()* と *destroyInstance()* を利用する事でインスタンスの取得、解放が行えます。

例:

|v2.1|v3.0|
|---|---|
|CCDirector->sharedDirector()|Director->getInstance()|
|CCDirector->endDirector|Director->destroyInstance()|
|etc...|etc...|

v2.1 の記述のままだとエラーを引き起こします。


### ゲッターについて
ゲッターには*get*接頭辞がつきました。

例:


|v2.1|v3.0|
|---|---|
|node->boundingBox()|node->getBoundingBox()|
|sprite->nodeToParentTransform()|sprite->getNodeToParentTransform()|
|etc...|etc...|

また、ゲッターは*const*宣言されています。

例:

```
// v2.1
virtual float getScale();

// v3.0
virtual float getScale() const;
```
v2.1 の書き方は撤廃されました。


### POD について
今まではポインタを引数として渡すようにしていましたが、これからは（TexParams、Point、 Sizeなど) これらの *const* 参照を引数として渡せます。

例:

```
// v2.1
void setTexParameters(ccTexParams* texParams);

// v3.0
void setTexParameters(const ccTexParams& texParams);
```


##C++11に則った記述
###概要
C++11以降とCocos2d-xを組み合わせた記述:

- *std::function* でラムダ式を格納し、コールバックとして使用する事が出来ます。
- *std::thread* で非同期化する事も可能。
- *override* はオーバーライドする際に記述する。

###Std::function

- *CallFunc* を作成したいときは std::function<void()> 
- *CallFuncN* を作成したいときは std::function<void(Node*)>
- *CallFuncND* や *CallFuncO* は、以降のバージョンでは削除されているので変わりに*CallFuncN* や *CallFunc*を使用してください。ActionTest.cpp が良い例になるでしょう。
- *Menu Item* には std::function<void(Node*)> でコールバックを仕込む事が出来ます。

*CallFunc* についての例:

```
// v2.1の場合
CCCallFunc *action1 = CCCallFunc::create( this, callfunc_selector( MyClass::callback_0 ) );

// v3.0 (short version)の場合
auto action1 = CallFunc::create( CC_CALLBACK_0(MyClass::callback_0,this));
auto action2 = CallFunc::create( CC_CALLBACK_0(MyClass::callback_1,this, additional_parameters));

// v3.0 (long version)の場合
auto action1 = CallFunc::create( std::bind( &MyClass::callback_0, this));
auto action2 = CallFunc::create( std::bind( &MyClass::callback_1, this, additional_parameters));

// v3.0でラムダを使って任意の関数オブジェクトを作成
auto action1 = CallFunc::create( 
                 [&](){
                     auto s = Director::sharedDirector()->getWinSize();
                     auto label = LabelTTF::create("called:lambda callback", "Marker Felt", 16);
                     label->setPosition(ccp( s.width/4*1,s.height/2-40));
                     this->addChild(label);
                 }  );
```

*MenuItem* についての例:

```
// v2.1の場合
CCMenuItemLabel *item = CCMenuItemLabel::create(label, this, menu_selector(MyClass::callback));

// v3.0 (short version)の場合
auto item = MenuItemLabel::create(label, CC_CALLBACK_1(MyClass::callback, this));

// v3.0 (long version)の場合
auto item = MenuItemLabel::create(label, std::bind(&MyClass::callback, this, std::placeholders::_1));

// v3.0でラムダを使って任意の関数オブジェクトを作成
auto item = MenuItemLabel::create(label, 
                 [&](Object *sender) {
                     // do something. Item "sender" clicked
                  });
```

###列挙型について

列挙型は *k*から始まっていましたが、使用されるであろう名前空間内に配置することで接頭辞を外しました。

変更例:

|v2.1|v3.0|
|---|---|
|kTypeValue|Type::VALUE|

呼び出し方の例:

|v2.1|3.0|
|---|---|
|kCCTexture2DPixelFormat_RGBA8888|Texture2D::PixelFormat::RGBA8888|
|kCCDirectorProjectionCustom|Director::Projection::CUSTOM|
|ccGREEN|Color3B::GREEN|
|CCPointZero|Point::ZERO|
|CCSizeZero|Size::ZERO|

過去のバージョンでは現在も接頭辞がついていたりしますが、現在は撤廃されています。

###継承について
overrideのキーワードを使用する事で、継承時におけるエラーを回避できる事があります。よってキーワードの使用を推奨します。

例:

```
class Sprite : public Node {
    bool isFlipY(void) const;
    void setFlipY(bool bFlipY);

    // Overrides
    virtual void setTexture(Texture2D *texture) override;
    virtual Texture2D* getTexture() const override;
    inline void setBlendFunc(const BlendFunc &blendFunc) override;
    inline const BlendFunc& getBlendFunc() const override;
}
```

##補足

- Cocos2d-xのルールに則ったメモリ管理を選択すると問題点を減らす事が出来ます。
- 命名規則や設計などについてはCocos2d-xのルールに従うと、より開発が楽になるでしょう。
- ルールについては[Cocos2d-x cpp programming guide](../cpp_coding_style/en.md)を参照してください。
