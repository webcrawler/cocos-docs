
# 设计并实现你的游戏场景

## 介绍

在这个教程里，我将会向你展示如何设计并构造一个游戏场景。由于所有的游戏都需要几种场景，所以本指南将会标准化普通场景。

在上一份教程中，我们知道了我们可以使用不同的层来分离特定的场景逻辑。

这是关于我们游戏场景的最后一步。

![gamescene](res/result.png)

在场景中，有一些建筑，一个主角和一些HUD元素来向我们展示游戏的当前进程。我们很容易把游戏的场景分成三部分：背景层（background layer），动画层（animaiton layer），和状态层（status layer）。

### 背景层（Background Layer）

基本上，所有的游戏都需要背景。有时候背景只是一张静态的图片，它占据了你游戏的整个屏幕。有时候，背景可以以一个恒定的或者变化的速度来移动。有时候，通过让不同距离的图片以不同的速度来移动，比如让近景图层快速移动而让远景图层慢慢移动，背景图片甚至可以向我们展现出视差效果。

在接下来的教程中，我们会介绍在构造视差背景中非常有用的tiled map。在这部分教程中，为了让事情变得简单，我们只使用一张简单的静态图片来表示背景。

**Note**:
我们可以移动背景来伪装一个效果，使我们的主角看上去一直在奔跑。但其实我们的主角一直呆在屏幕的中间，在游戏开发中我们还可以用到很多像这样的小技巧。

### 动画层（Gameplay Layer）/游戏层（Gameplay Layer)

动画层包含了游戏中所有元素的动画，碰撞检测和其它的游戏逻辑，也许叫它**游戏层(GamePlayLayer)**会更加贴切，你可以挑你喜欢的叫法。我们在这层中组织了我们游戏的关键部分。总的来说，我们将会设计游戏对象，等级**管理器**，不同物体之间的碰撞检测还有胜负条件。所有的繁琐的事情都会在这一层。

理论上，我们不需要把这层分离成更细小的层了。我们可以使用组合（compsition）和委托(delegation)来进行合适的处理。

### 状态层（Status Layer）/HUD层（HUD Layer）

在视频游戏中，HUD是一种可以将信息作为用户界面的一部分，直观地展现给玩家的方法。它的名字来源于现代飞行器中的的平视显示器（head-up display）。

HUD通常用于同步显示几块不同的游戏进展信息，包括主要角色的生命，道具和光标（例如分数或者等级）。你可以参考[这个链接](http://en.wikipedia.org/wiki/HUD_(vedio_gaming))来获取更多关于HUD的信息。

为了让这事儿简单一点，我们把这些信息分离到另外一个叫做状态层（StatusLayer）的层中。使用一个分离出来的层会让我们的工作变得轻松并且不用关心Z轴的显示顺序（zOrder）问题，因为这些信息经常显示在其它游戏元素的顶端。

## 动作编码（Coding in Action）

### 准备工作

首先，我们需要添加两个图片（**PlayBG.png** 和 **runner.png**）到 **资源（res）** 路径下。

在之前的教程中，我们添加了所有的资源变量到**resource.js**。因为我们现在添加了其它的两个图片，所以**resource.js**也会被改成这个样子：

```
var res = {
    helloBG_png : "res/helloBG.png",
    start_n_png : "res/start_n.png",
    start_s_png : "res/start_s.png",
    PlayBG_png  : "res/PlayBG.png",
    runner_png  : "res/runner.png"
};

var g_resources = [
    //image
    res.helloBG_png,
    res.start_n_png,
    res.start_s_png,
    res.PlayBG_png,
    res.runner_png
];
``` 

这里我们添加了两个全局变量，**PlayGB_png**和**runner_png**。现在，当我们想要在js文件中创建一个精灵的时候，我们可以很容易地获得这些变量。

因为我们要添加四个javascript文件：PlayScene.js, AnimaitonLayer.js, BackgroundLayer.js 和StatusLayer.js。我们需要告诉Cocos2d-x引擎在游戏开始的时候去载入这些文件。所以我们必须改变**project.json** 来添加更多的资源文件：

```
 "jsList" : [
        "src/resource.js",
        "src/app.js",
        "src/AnimationLayer.js",
        "src/BackgroundLayer",
        "src/PlayScene.js",
        "src/StatusLayer.js"
    ]
```

以后每次当你添加一个新的javascript文件到你的游戏中时，你只需要改变**jsList** 属性然后添加更多的资源代码文件路径到这个数组的结尾就可以了。

最后，我们需要显示游戏场景当我们点击一开始的菜单场景的按钮时。以下是这部分代码片段。

```
    //this is the callback when the menu is clicked
    onPlay : function(){
        cc.log("==onplay clicked");
        cc.director.runScene(new PlayScene());
    }
```


### 游戏场景代码(PlayScene.js)

由于背景层（background layer），动画层（animation layer）和状态层（status layer）需要在不同的次序播放。当我们调用**addChild** 方法或者我们可以以正确的顺序添加他们作为游戏场景的孩子的时候，我们可以明确地区分这个次序。在这个教程中，我们选择后者。

这是游戏场景(PlayScene)部分的代码：

```
var PlayScene = cc.Scene.extend({
    onEnter:function () {
        this._super();
        //add three layer in the right order
        this.addChild(new BackgroundLayer());
        this.addChild(new AnimationLayer());
        this.addChild(new StatusLayer());
    }
});
```

### 背景层编码(BackgroundLayer.js)

下面是我们的背景图片：

![bg](res/PlayBG.png)

以下是这部分内容的代码：

```
var BackgroundLayer = cc.Layer.extend({
    ctor:function () {
        this._super();
        this.init();
    },

    init:function () {
        this._super();
        var winsize = cc.director.getWinSize();

        //create the background image and position it at the center of screen
        var centerPos = cc.p(winsize.width / 2, winsize.height / 2);
        var spriteBG = new cc.Sprite(res.PlayBG_png);
        spriteBG.setPosition(centerPos);
        this.addChild(spriteBG);
    }
});

```
### 动画层编码（AnimationLayer.js）

这是我们的主角：
![runner](res/runner.png)


在这一部分中，我将会向你展示如何在主角的身上运行一个动作，我们将要在主角精灵身上运行**MoveTo** 动作来使主角精灵从（80， 85）移动到（300， 85）两次。

下面是关于动画层这部分的代码。

``` 
var AnimationLayer = cc.Layer.extend({
    ctor:function () {
        this._super();
        this.init();
    },
    init:function () {
        this._super();

        //create the hero sprite
        var spriteRunner = new cc.Sprite(res.runner_png);
        spriteRunner.attr({x: 80, y: 85});

        //create the move action
        var actionTo = new cc.MoveTo(2, cc.p(300, 85));
        spriteRunner.runAction(new cc.Sequence(actionTo));
        this.addChild(spriteRunner);
    }
});
```

### 状态层编码（StatusLayer.js）

在这一部分中，我们将会添加两个指示器（indicator）：硬币数目指示器和距离指示器。两个指示器都是Cocos2d-html5中的标签（Label)。标签在向玩家显示HUD信息时非常常用，并且创建并使用标签的代码非常容易。感谢Cocos2d的框架。

这是我们需要组装的层的部分的代码：

```
var StatusLayer = cc.Layer.extend({
    labelCoin:null,
    labelMeter:null,
    coins:0,

    ctor:function () {
        this._super();
        this.init();
    },

    init:function () {
        this._super();

        var winsize = cc.director.getWinSize();

        this.labelCoin = new cc.LabelTTF("Coins:0", "Helvetica", 20);
        this.labelCoin.setColor(cc.color(0,0,0));//black color
        this.labelCoin.setPosition(cc.p(70, winsize.height - 20));
        this.addChild(this.labelCoin);

        this.labelMeter = new cc.LabelTTF("0M", "Helvetica", 20);
        this.labelMeter.setPosition(cc.p(winsize.width - 70, winsize.height - 20));
        this.addChild(this.labelMeter);
    }
});
```
我们可以使用**new cc.LabelTTF** 来创建一个文本标签。这个函数的第一个参数是要显示的文本信息，第二个参数是字体，然后第三个参数是字体尺寸。我们可以使用**setColor** 这个LabelTTF的成员方法来设置标签的颜色。例如**cc.c3(0, 0, 0)** 代表的就是黑色。

## 总结

在这个教程中，我们学习了如何把一个游戏场景（Gameplay Scene）划分成不同的层。每一个层有它自己的逻辑和负责的事务。你可以在[这里](res/Parkour.zip)下载完整的项目。

因为这个代码以及它的逻辑都非常简单，所以我们不详细地把他们全部覆盖。如果你有任何问题或者建议，告知我们，然后我们会尽力支援你。

## 接下来去哪里

在下个教程中，我会向你演示如何在一个跑者（runner)上播放动画，以及如何打包小图片到精灵图片（sprite sheet）中。我也会介绍一个很棒的工具**TexturePakcer**给你们。