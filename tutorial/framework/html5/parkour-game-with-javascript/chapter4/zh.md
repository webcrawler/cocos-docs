# 设计并制作你的游戏场景

## 入门

在此教程，我将会向你展示怎样设计和制作游戏场景。每个游戏需要一些不同种类的游戏场景。所以这个教程将试着规范一般情况。

我们可以从以往的教程了解到不同的层可以分离指定场景的逻辑。

下图是游戏制作的最终结果：

![gamescene](res/result.png)

里面有背景建筑，一个英雄，一些显示的数值元素向我们展示了目前游戏情形的进度。我们能轻易地将游戏制作分为三个部分：背景层，动画层和状态层。

### 背景层

基本而言，每个游戏都需要背景。有时背景仅仅是一个占据你整个游戏屏幕的静止图片。而有时背景层可以以相同或不同速率移动。有时背景图像甚至显示我们视差的影响即不同层以不同的速度移动,最近的层移动速度较快,最远的层移动速度较慢。

在后面的教程中,我们将介绍平铺的地形很利于构造背景视差。在本教程中,为了简单起见,我们只使用一个简单的静态图像来代表游戏背景。

**笔记**

我们可以移动背景来模拟无限运行游戏效果的角色。角色总是在游戏屏幕的中心。我们可以看到很多这样的技巧在游戏开发过程中。

###动画层

动画层包含所有游戏元素的动画,碰撞检测和其他游戏逻辑。也许**GamePlayLayer**是一个更合适的名字。你可以选择你想要的。在这一层,我们组织我们游戏的关键部分。一般来说,我们将设计游戏对象,水平已成熟的雌鱼(也称为水平经理),不同的游戏对象之间的碰撞检测及赢和输的状况，以及所有复杂东西。

从理论上讲,我们不需要单独把这一层分为更小的层。我们可以使用合成和代表妥善处理事情。

### 状态层（平视层）

在视频游戏中,平视显示是利用信息可视化方法给玩家传递游戏用户界面的一部分。它得名于现代飞机使用的平视显示。平视显示经常同时显示几条信息包括主要人物的健康,项目和游戏进展(如成绩或水平)。你可以参考这个[链接](http://en.wikipedia.org/wiki/HUD_(video_gaming)) 。

## 编码实践

## 准备

首先,我们应该添加两个图像(**PlayBG.png**和**runner.png**）到**res**目录。在前面的教程中,我们添加了所有资源变量**resource.js**。因为我们增加了两个图片,所以**resource.js**还应该改变成这样的:

```
var s_HelloBG = "helloBG.png";
var s_start_n = "start_n.png";
var s_start_s = "start_s.png";
var s_PlayBG = "PlayBG.png";
var s_runner = "runner.png";

var g_resources = [
    //image
    {src:s_HelloBG},
    {src:s_start_n},
    {src:s_start_s},
    {src:s_PlayBG},
    {src:s_runner}
];
``` 

我们已经添加了两个全局变量命名**PlayBG**和**Time Runner**。现在当我们想创建一个精灵在另一个js文件,我们可以轻松地访问这些变量。因为我们将增加四个javascript文件:PlayScene.js,AnimationLayer.js,BackgroundLayer.js和StatusLayer.js。我们需要在Cocos2d-x引擎游戏启动时加载这些文件。所以我们应该改变**cocos2d.js**，而且添加更多的源文件:

```
 appFiles:[
            'src/resource.js',
            'src/myApp.js',
            'src/AnimationLayer.js',
            'src/BackgroundLayer.js',
            'src/PlayScene.js',
            'src/StatusLayer.js'
        ]
```

以后每次当你添加一个新的javascript文件到你的游戏,你应该改变属性**appFiles**和添加更多的与源代码文件路径相同的数组。最后,我们单击按钮时应显示PlayScene MenuScene。这里是代码片段:

```
   //this is the callback when the menu is clicked
    onPlay : function(){
        cc.log("==onplay clicked");
        var director = cc.Director.getInstance();
        director.replaceScene(new PlayScene());
    }
```

##编写PlaySence(PlayScene.js)

因为背景层,动画层和状态层应该以不同的顺序显示。我们可以明确指令当调用**addChild**命令时我们可以以正确的顺序添加PlayScene的下级。在本教程中,我们将随后提到。下面是PlayScene的代码片段:

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

###编写BackgroundLayer(BackgroundLayer.js)

这是背景图片：
![bg](res/PlayBG.png)

这是代码片段：

```
var BackgroundLayer = cc.Layer.extend({
    ctor:function () {
        this._super();
        this.init();
    },

    init:function () {
        this._super();
		
		//create the background image and position it at the center of screen
	var winSize = cc.Director.getInstance().getWinSize();
        var centerPos = cc.p(winSize.width / 2, winSize.height / 2);
        var spriteBG = cc.Sprite.create(s_PlayBG);
        spriteBG.setPosition(centerPos);
        this.addChild(spriteBG);
    }
});

```

###编写AnimationLayer(AnimationLayer.js)

这是主要人物:

![runner](res/runner.png)

在这一节中,我将向您展示如何运行角色行为。我们将运行**移至**行动将角色(80、85)在两秒内移至(300、85)。这里是AnimationLayer的代码片段:

``` 
var AnimationLayer = cc.Layer.extend({
    ctor:function () {
        this._super();
        this.init();
    },
    init:function () {
        this._super();

        var centerPos = cc.p(80, 85);
        //cerate the hero sprite
        var spriteRunner = cc.Sprite.create(s_runner);
        spriteRunner.setPosition(centerPos);
        
        //create the move action
        var actionTo = cc.MoveTo.create(2, cc.p(300, 85));
        spriteRunner.runAction(cc.Sequence.create(actionTo));
        this.addChild(spriteRunner);
    }
});
```

###编写StatuLayer(StatusLayer.js)

在本节中,我们将添加两个指标:硬性数量指标和距离指标。这两个指标都是Cocos2d-html5。标注显示非常有用的平视显示信息给玩家。同时创建和使用标注的代码非常简单。幸亏cocos2d框架。这是我们需要设置层的代码片段:

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
	
	var winSize = cc.Director.getInstance().getWinSize();
        this.labelCoin = cc.LabelTTF.create("Coins:0", "Helvetica", 20);
        this.labelCoin.setColor(cc.c3(0,0,0));//black color
        this.labelCoin.setPosition(cc.p(70, winSize.height - 20));
        this.addChild(this.labelCoin);

        this.labelMeter = cc.LabelTTF.create("0M", "Helvetica", 20);
        this.labelMeter.setPosition(cc.p(winSize.width - 70, winSize.height - 20));
        this.addChild(this.labelMeter);
    }
});

```

我们可以用**cc.LabelTTF.create**来创建一个文本标注。第一个参数是显示文本,第二个参数是字体,第三个参数是字体大小。我们还可以使用LabelTTF的成员函数**setColor**设置标注的颜色。**cc.c3(0,0,0)**代表黑色。

## 总结

在本教程中,我们已经了解了如何将一个游戏场景划分为不同的层。每一层都有它自己的逻辑和任务。您可以下载整个项目从(res / Parkour.zip)。

由于代码和逻辑非常简单,所以我们不会涉及所有的细节。如果你有任何问题或建议,请让我们知道,我们将尽最大努力支持你。

##下一步

在接下来的教程中,我将向您展示如何在精灵上运行动画以及如何把小图像包装成大精灵。我还将给你们介绍一个非常棒的工具叫**TexturePakcer**。
