# 让角色动起来

## 介绍

在上一章教程中，我们已经实现了如何将角色从一点移动到另一点，但这移动过程仍然显得有些不自然。在本章教程中，我将告诉大家如何为角色加上动画，使角色的奔跑动作更加真实。

在此之前，我先介绍一个非常酷炫的图片编辑打包工具：*TexturePacker*

## TexturePacker介绍

TexturePacker是一个用于创建精灵表单(SpriteSheet)的跨平台GUI和命令行工具！

你可以到Textureacker的[官方网站](http://www.codeandweb.com/texturepacker/documentation)得到更多关于它的信息。

在此我只简单介绍一下如何利用TexturePacker生成我们游戏中所需要的动画。

### 利用TexturePacker构建你自己的动画

构建过程主要分为以下几个步骤：

1. 打开TexturePacker，将路径*res/TexturePacker*下的*TexturePacker*文件夹拖拽至Sprites区域。

![dragTheResource](res/dragTheResource.png)

当你添加了新的图片至*TexturePacker*文件夹中，TexturePacker会检测并响应这些变化，自动加载新添加的图片。

2. 在TextureSettings面板中，选择 "data format" 为 "cocos2d"，选择 "Texture format" 为 "png"(即默认设置)。

3. 指定*Data file*和*Texture file*的路径。在这里我们将其设置为 *res*文件夹，并将数据文件(data file)命名为"running.plist"，纹理文件(texture file)命名为"running.png"。

![specifypath](res/specifypath.png)

4. 点击*publish*，会弹出一个对话框，如果一切顺利，那么"running.png"和"running.plist"两个文件将会诞生在你先前所设置的地方。

![generating](res/generating.png)

好了，现在我们已经成功生成了奔跑动画所需的文件，接下来就让这些动画文件跑起来吧。

## 在Cocos2d-HTML5中加载动画文件

### 准备工作

首先，我们需要添加running.plist和running.png至*resource.js*中。

```
var s_HelloBG = "helloBG.png";
var s_start_n = "start_n.png";
var s_start_s = "start_s.png";
var s_PlayBG = "PlayBG.png";
var s_runner = "running.png";
var s_runnerplist = "running.plist";


var g_resources = [
    //image
    {src:s_HelloBG},
    {src:s_start_n},
    {src:s_start_s},
    {src:s_PlayBG},
    {src:s_runner},
    {src:s_runnerplist}
];
```

现在，我们已经将变量*s_runner*的值设为了"running.png"，即精灵表单。接下在我们将从*running.png*中创建我们的角色精灵。

### 创建角色动画

首先，我们需要在*AnimationLayer.js*中添加以下变量：

```
spriteSheet:null,
runningAction:null,
sprite:null,
```

然后，将角色创建方法移放至：

```
this.sprite = cc.Sprite.createWithSpriteFrameName("runner0.png");
```

利用以下代码，我们就能轻松地创建动画：

```
//1.load spritesheet 
 cc.SpriteFrameCache.getInstance().addSpriteFrames(s_runnerplist);

//2.create spriteframe array
var animFrames = [];
for (var i = 0; i < 8; i++) {
    var str = "runner" + i + ".png";
    var frame = cc.SpriteFrameCache.getInstance().getSpriteFrame(str);
    animFrames.push(frame);
}
//3.create a animation with the spriteframe array along with a period time
var animation = cc.Animation.create(animFrames, 0.1);

//4.wrap the animate action with a repeat forever action
this.runningAction = cc.RepeatForever.create(cc.Animate.create(animation));
```

需要说明的是，该动画是由精灵表单中一系列小图片（runner0.png到runner7.png）所构成的。

这就是Cocos2d-html5中创建一个动画的完整过程了：

1. 在精灵帧缓存类(SpriteFrameCache)中载入精灵表单plist文件。
2. 将动画帧添加至*animFrames*数组中。
3. 从该数组中创建一个cc.Animation对象，每两个精灵帧之间有一定延时。
4. 创建最后的cc.Animate对象，并将其打包为一个RepeatForever动作，这样，该动画就能永远执行下去了。

一般而言，如果我们要在Cocos2d-html5中使用动画，我们都会使用*精灵批处理节点(SpriteBatchNode)*来优化游戏性能。

*AnimationLayer.js* 中最后一段代码如下：

```
var AnimationLayer = cc.Layer.extend({
    spriteSheet:null,
    runningAction:null,
    sprite:null,
    ctor:function () {
        this._super();
        this.init();
    },

    init:function () {
        this._super();

        // create sprite sheet
        cc.SpriteFrameCache.getInstance().addSpriteFrames(s_runnerplist);
        this.spriteSheet = cc.SpriteBatchNode.create(s_runner);
        this.addChild(this.spriteSheet);

        
        // init runningAction
        var animFrames = [];
        for (var i = 0; i < 8; i++) {
            var str = "runner" + i + ".png";
            var frame = cc.SpriteFrameCache.getInstance().getSpriteFrame(str);
            animFrames.push(frame);
        }

        var animation = cc.Animation.create(animFrames, 0.1);
        this.runningAction = cc.RepeatForever.create(cc.Animate.create(animation));
        this.sprite = cc.Sprite.createWithSpriteFrameName("runner0.png");
        this.sprite.setPosition(cc.p(80, 85));
        this.sprite.runAction(this.runningAction);
        this.spriteSheet.addChild(this.sprite);
    }
});
```

现在再运行你的项目，你将看到你的角色在游戏屏幕中正永不止步地奔跑着。

![finalresult](res/finalresult.png)

##总结

在本章教程中，我们学会了如何用TexturePacker生成动画，以及如何在Cocos2d-html5中使精灵运行该动画。

你可以到[这里](res/Parkour.zip)下载本项目的完整代码。

## 下章提要

在下一章教程中，我们将加入chipmunk物理引擎到我们的游戏世界中，从而使我们的游戏真实度得到进一步提升。