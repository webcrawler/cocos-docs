#实现游戏结束的逻辑和其他功能

##简介

在这篇指南中，我们将实现游戏的结束逻辑，更新游戏中心和一个简单的手势识别的功能。

闲话少说，下面开始我们的教程。

##更新游戏中心

###更新玩家的运动距离

首先，我们在**StatusLayer**类中添加**updateMeter**函数：

      updateMeter:function (px) {
    this.labelMeter.setString(parseInt(px / 10) + "M");
    }

这个函数不断的更新**labelMeter**的值。这里我们使用函数**parseInt**把结果转成一个整型值。

其中，参数**px**的单位是像素，这里我们用10个像素表示一米。

现在，我们应该每帧都去调用该函数。

打开 **AnimationLayer.js**并在**update**函数的开头添加下面的代码：

     // 更新米数
    var statusLayer = this.getParent().getParent().getChildByTag(TagOfLayer.Status);
    statusLayer.updateMeter(this.sprite.getPositionX() - g_runnerStartX);

###更新金币的数量

当玩家收集到金币的时候，我们应该更新金币指示器显示的数值。

首先，我们在**StatusLayer**添加**addCoin**方法：


      addCoin:function (num) {
    this.coins += num;
    this.labelCoin.setString("Coins:" + this.coins);
    }

当玩家拾取到金币的时候，我们应该调用这个方法。

现在就让我们去实现它的功能。

打开**PlayScene.js**并在函数**colisionCoinBegin**的底部添加下面的代码：

    var statusLayer = this.getChildByTag(TagOfLayer.Status);
    statusLayer.addCoin(1);

每次玩家碰到金币的时候，都会调用**colisionCoinBegin**函数并是我们的金币的总数加一。

保存文件，并运行试试看效果。这里是截图：

![updatehud](res/updatehud.png)

##给游戏添加游戏结束的逻辑

###设计并实现游戏结束的图层

为了简单起见，我们仅仅在游戏结束图层的上方加上一个菜单项。

当你点击按钮**restart**的时候，游戏就重新开始。这个设计是特别的简单，下面就让我们来实现它的功能。

下面是**GameOverLayer.js**中所有的实现内容：

    var GameOverLayer = cc.LayerColor.extend({
    // constructor
    ctor:function () {
    this._super();
    this.init();
    },
    init:function () {
    this._super(cc.color(0, 0, 0, 180));
    var winSize = cc.director.getWinSize();
    
    var centerPos = cc.p(winSize.width / 2, winSize.height / 2);
    cc.MenuItemFont.setFontSize(30);
    var menuItemRestart = new cc.MenuItemSprite(
    new cc.Sprite(res.restart_n_png),
    new cc.Sprite(res.restart_s_png),
    this.onRestart, this);
    var menu = new cc.Menu(menuItemRestart);
    menu.setPosition(centerPos);
    this.addChild(menu);
    },
    onRestart:function (sender) {
    cc.director.resume();
    cc.director.runScene(new PlayScene());
    }
    });

这里我们使用两个名为**s_restart_n**和**s_restart_s**的精灵创建restart菜单项。

因此我们应该在res目录下添加资源文件，并定义资源路径。

打开**resource.js**并添加下面的代码：

     restart_n_png : "res/restart_n.png",
     restart_s_png : "res/restart_s.png"
    
	//在g_resources数组的底部添加下面两行内容：
    res.restart_n_png,
    res.restart_s_png

