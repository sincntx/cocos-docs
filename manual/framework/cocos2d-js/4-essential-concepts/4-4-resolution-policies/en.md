# 4.4 Resolution policy for Cocos2d-JS

The resolution policy is designed for adapting your game scene to any device and any resolution. Cocos2d-JS provides different adaptation policies for different use cases. The resolution policy helps developers to focus on creating their game.

Cocos2d-JS has two different engines, which both have a different implementation of resolution policy. However, they do share the same API. As the native engine's implementation is much easier and clearer, this chapter will focus on the web engine resolution policy. The differences between the resolution policy of the native engine and web engine will be covered at the end of this chapter.

## 4.4.1 About the web engine resolution policy

As a game developer, it can be really hard to provide a good experience cross-browser and cross-platform. The main issue lies in the dynamic adaptation of our content in different window sizes. For regular web pages, you can use responsive design. Unfortunately, this cannot be used for canvas games. So for developers using Cocos2d-JS, we have created the resolution policy.

The main goal of the resolution policy is to adapt your game canvas to fit the browser window or the device's screen.

![Bad](./res/bad.jpg)
When we see our game like this, it's really painful.

![Good](./res/good.jpg)
Most of the time, this is the result that we want to get. Some people hate the white sides, so there are other options available.

Let's go on to see how simple it is to use the resolution policy.

## 4.4.2 Usage

####1. Setting the policy

To let Cocos2d-JS adapt your game automatically to the browser, you just need to add this line of code in or after the `cc.game.onStart` callback (main.js):

```
cc.view.setDesignResolutionSize(320, 480, cc.ResolutionPolicy.SHOW_ALL);
```

The first and second parameters are the resolution you want to use for your game, and the third parameter is the resolution policy you want to use. There are 5 predefined policies, each has it's own behaviour. These will be discussed later in this chapter.

If you have already set your resolution policy, you can simply change your resolution policy by using this function:

```
cc.view.setResolutionPolicy(cc.ResolutionPolicy.NO_BORDER);
```

Where the web engine differs from the native engine is that you may want to show other content browser along with the canvas. You may want to apply a style to your canvas or don't want it to take up all the space on screen. So our resolution policy will adapt to the canvas's outer container by default. If you want to adapt to the browser window, you need to put your game canvas directly in the page's body:

```
<body>
    <canvas id="gameCanvas"></canvas>
</body>
```

####2. The benefit

The benefit of using the resolution policy is obvious, you can ignore all varieties of browser and device size. Even more important, you don't need to scale everything in your game manually, everything is managed by Cocos2d-JS. Imagine if you set-up the designed resolution size to 320 by 480 pixels, you should always focus on this size in your game logic. The coordinate of right top corner of your game will always be (320, 480). In FIXED\_WIDTH mode, the height may be resized, and in FIXED\_HEIGHT mode, the width may be resized.

####3. Resize to the browser size

The new design allows automatic re-adaptation to browser when its size changes. For example, when the user resizes their browser or, even more useful, when the user turns their mobile device's orientation. To activate this feature, use the `resizeWithBrowserSize` function of `cc.view`:

```
cc.view.resizeWithBrowserSize(true);
```
    
For permitting a more flexible design, we have provided another function in `cc.view`. You can observe the resize event by setting a callback function with `setResizeCallback`:

```
cc.view.setResizeCallback(function() {
    // Do things according to your need, 
    // e.g. change a resolution policy when user's mobile device orientation changed.
});
```

####4. Fullscreen API

The [fullscreen API](https://developer.mozilla.org/en-US/docs/Web/Guide/API/DOM/Using_full_screen_mode) is a new Web API that allows web content to be presented using the entire screen.

Cocos2d-JS will try to activate the full screen mode on mobile browsers so that user can have better experience. (Note that not every browser will allow this behaviour)

On the other hand, modern desktop browsers also support the fullscreen API. If you want to use it, simply do the following:

Try to enter full screen mode: `cc.screen.requestFullScreen(targetElement, onFullScreenCallback);`

Check if the page is on full screen mode: `cc.screen.fullScreen();`

Exit full screen mode: `cc.screen.exitFullScreen();`


## 4.4.3 Principles

####1. Frame

The frame is the outer container of your canvas element, it's usually the html `body` element. But in some cases, the cocos2d game is just a part of your web page. You may have some text, an image or something else along with it. If this is the case, you can wrap your canvas in a DOM element (the frame). The initial size of your canvas element doesn't matter, the resolution policy will scale your canvas to fit the frame.

If you want to make your game fit the browser window, you should put your canvas element directly in the `body` element.

####2. Cocos2d container

In the initiation process, cocos2d will additionally wrap your canvas into a cocos2d container and the container itself will be added to the original outer element of canvas (the frame). This container is a helper to make the magic of resolution policy happen. It can be accessed from the cc.container.

####3. Game content

The game content represents the game world's coordinates.

####4. Viewport

The viewport is the game world's rectangle related to the canvas's coordinates in pixel.

####5. Container Strategy

The container strategy controls the behaviour of how to scale the cocos2d container and game canvas element relatively to the frame.

####6. Content Strategy

The content strategy controls the behaviour of scaling the game world relative to the container and the set-up of the viewport.


## 4.4.4 Predefined policies

Now we will introduce all five predefined policies. In each image, the red rectangles are the game content's corners and the green ones are the corners of the canvas.

All resolution policies are combined with a container strategy and a content strategy. The combination of each policy is shown in the brackets.

####1. SHOW\_ALL (PROPORTION\_TO\_FRAME + SHOW\_ALL)

![ShowAll](./res/ShowAll.jpeg)

The show all policy will scale the container to the maximum size of the frame. It shows all your content on the screen with the original width/height ratio that you have set. So there might be an empty area in one axis, the color or background image can be set via the CSS property of the frame.

####2. NO\_BORDER (EQUAL\_TO\_FRAME + NO\_BORDER)

![NoBorder](./res/NoBorder.jpeg)

The no border policy will scale proportionally the container so that it fills up the entire frame. In this case, if the width/height ratio of the frame doesn't equal your designed ratio. This can result in some areas of your game being cut off. In the meantime, under the no border policy, `cc.visibleRect` represents the viewport of the canvas in the game world, and it can be smaller than `cc.winSize`.

####3. EXACT\_FIT (EQUAL\_TO\_FRAME + EXACT\_FIT)

![ExactFit](./res/ExactFit.jpeg)

The exact fit policy will scale the container to exactly fit the frame. Your game's width/height ratio will probably lost.

####4. FIXED\_WIDTH (EQUAL\_TO\_FRAME + FIXED\_WIDTH)

![FixedWidth](./res/FixedWidth.jpeg)

The fixed width policy will scale the width of the container to fit the frame's width. The height will be scaled proportionally.

It may seem the same as the SHOW\_ALL policy, but the canvas's rectangle fills up the whole frame, and game world's coordinate system equals the canvas coordinate system.

####5. FIXED\_HEIGHT (EQUAL\_TO\_FRAME + FIXED\_HEIGHT)

![FixedHeight](./res/FixedHeight.jpeg)

The fixed height policy will scale the height of the container to fit the frame's height. The width will be scaled proportionally.

In this example, the game's width is larger than the game's height. This means that the FIXED\_WIDTH policy acts like the SHOW\_ALL policy, and the FIXED\_HEIGHT policy acts like the NO\_BORDER policy. On the contrary, if the game width is smaller than the game height, the FIXED\_WIDTH policy will act like the NO\_BORDER policy, and the FIXED\_HEIGHT policy will acts like the SHOW\_ALL policy. The FIXED\_HEIGHT and FIXED\_WIDTH policies will both take the whole frame as the viewport and game world's rectangle.

## 4.4.5 Customized resolution policy

####1. Combine predefined strategies

As you can see, the predefined policies just use the combination of predefined strategies. You can use this to customize the resolution policy. The predefined strategies are:

- Container strategies
    - cc.ContainerStrategy.EQUAL\_TO\_FRAME
    - cc.ContainerStrategy.PROPORTION\_TO\_FRAME
    - cc.ContainerStrategy.ORIGINAL\_CONTAINER

- Content strategies
    - cc.ContentStrategy.SHOW\_ALL
    - cc.ContentStrategy.NO\_BORDER
    - cc.ContentStrategy.EXACT\_FIT
    - cc.ContentStrategy.FIXED\_WIDTH
    - cc.ContentStrategy.FIXED\_HEIGHT

To construct and use a resolution policy with strategies, you should do the following:

```
var policy = new cc.ResolutionPolicy(cc.ContainerStrategy.PROPORTION_TO_FRAME, cc.ContentStrategy.EXACT_FIT);
cc.view.setDesignResolutionSize(320, 480, policy);
```

This policy should work exactly like the show all policy.

####2. Implementing your own strategy

If you are not satisfied with our predefined strategies, you can even implement your own strategy to fit whatever you need.

Start by extending the container strategy:

```
var MyContainerStg = cc.ContainerStrategy.extend({
    preApply: function (view) {
        // This function is called before the process of adaptation,
        // you can remove this function if you don't need it
    },

    apply: function (view, designedResolution) {
        // Apply process
    },

    postApply: function (view) {
        // This function is called after the process of adaptation,
        // you can remove this function if you don't need it
    }
});
```

Then, extend the content strategy:

```
var MyContentStg = cc.ContentStrategy.extend({
    preApply: function (view) {
        // This function is called before the process of adaptation,
        // you can remove this function if you don't need it
    },

    apply: function (view, designedResolution) {
        var containerW = cc.canvas.width, containerH = cc.canvas.height;
      
        // The process to calculate the content size, the x-axis's scale and the y-axis's scale

        return this._buildResult(containerW, containerH, contentW, contentH, scaleX, scaleY);
    },

    postApply: function (view) {
        // This function is called after the process of adaptation,
        // you can remove this function if you don't need it
    }
});
```

At last, you should construct your own policy with your custom strategies.

```
var policy = new cc.ResolutionPolicy(new MyContainerStg(), new MyContentStg());
cc.view.setDesignResolutionSize(320, 480, policy);
```

If you want more details about the new resolution policy implementation, you can refer to the source code of CCEGLView.js in `frameworks/cocos2d-html5/cocos2d/core/platform/CCEGLView.js`.


## 4.4.6 Differences between the web and native engine policies

On native platforms, game content will always occupy the entire game window or full screen on mobile devices. Cocos2d-JS uses the same resolution policies as Cocos2d-x. Although they have different implementations, they share the same API in `cc.view`. However, the native engine doesn't support features like customized resolution policy. The main differences are:

- The native engine only supports the 5 predefined policies.
- The container strategy and content strategy don't exist in native engine.
- Developers cannot extend the container strategy or content strategy to construct a custom resolution policy.