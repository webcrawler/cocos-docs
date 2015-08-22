#在游戏中引入Chipmunk物理引擎

## 介绍
Cocos2d-html5能让我们创造出让人印象深刻的游戏世界，但是它缺乏现实性。虽然我们可以通过复杂的计算来让我们的游戏世界更加逼真，但是我们有别的方法可以让我们的工作更加轻松。他就是物理引擎。
物理引擎可以提供重力、碰撞检测和物理模拟来让我们的游戏看起来更加逼真。
在这个教程里，我们将会讲解如何把Chipmunk物理引擎加入到我们的游戏中。


##为什么选择Chipmunk引擎？
我们之所以选择Chipmunk物理引擎是因为它比其他2D物理引擎更加强大。
除了Chipmunk物理引擎，我们还有另外一个选择—Box2D。
Box2D是一个很不错的物理引擎，它已经存在了很长的时间了，有很多的2D游戏一直使用Box2D作为它们的物理引擎。
但是Chipmunk有它自己的优势，你可以去Chipmunk[官网](http://http://chipmunk-physics.net/)了解更多信息。

##在Cocos2d-html5使用Chipmunk物理引擎

### 准备


首先，让我们在Cocos2d-html5中启用Chipmunk
打开*Cocos2d.js*文件，并修改：

```
chipmunk:false,
```

为:

```
chipmunk:true,
```

这样当Cocos2d-html5完成启动时，会自动加载Chipmunk库。



接下来，让我们创建一个文件名为* globals.js*，并添加两个全局变量进去。



```
var g_groundHight = 57;
var g_runnerStartX = 80;
```

最后，我们应该让framework在引擎启动时加载*globals.js*文件。
在*appFiles* 数组的结尾追加*globals.js*路径：

```
  appFiles:[
            'src/resource.js',
            'src/myApp.js',
            'src/AnimationLayer.js',
            'src/BackgroundLayer.js',
            'src/PlayScene.js',
            'src/StatusLayer.js',
            'src/globals.js'
        ]
```

*注：*当你在cocos2d-HTML5中添加一个新的文件，你应该记得将它添加到*appFiles*数组中。





### Chipmunk引擎的初始化

在Chipmunk中，有一个*space*对象来表示物理世界。 

首先，让我们添加一个名为*space*的新变量到*PlayScene.js*文件中：

```
space:null,
```

通常，一个游戏只需要一个*space*对象。它可以被不同的层所共享。 
我们一般把空间的初始化代码放在在PlayScene。 

下面是代码来设置物理世界：


    	// init space of chipmunk
   	    initPhysics:function() {
        //1. new space object 
        this.space = new cp.Space();
        //2. setup the  Gravity
        this.space.gravity = cp.v(0, -350);
        // 3. set up Walls
        var wallBottom = new cp.SegmentShape(this.space.staticBody,
            cp.v(0, g_groundHight),// start point
            cp.v(4294967295, g_groundHight),// MAX INT:4294967295
            0);// thickness of wall
        this.space.addStaticShape(wallBottom);
    },


上面的代码是进行了注释的，所以我们可以轻松地理解它。如果你想知道这些接口的细节，你应该参考Chipmunk的官方文档。 

接下来，让我们来定义我们的游戏的主循环：

```
    update:function (dt) {
        // chipmunk step
        this.space.step(dt);
    }
```

在*update*功能中，我们告诉Chipmunk开始进行物理模拟。 

在我们进行使用之前，我们应该对*AnimationLayer*进行一点小的修改。因为我们将在AnimationLayer创建物理元素，所以我们应该修改AnimationLayer的构造函数以传递*space*对象

```
ctor:function (space) {
        this._super();
        this.space = space;
        this.init();
    },
```

我们应该在AnimationLayer定义一个弱引用，并把它初始化为*null*。 

这样，我们的准备工作已经完成。 让我们完成最后的工作并调用这些*onEnter*里面的方法:



    onEnter:function () {
        this._super();
        this.initPhysics();
        this.addChild(new BackgroundLayer());
        this.addChild(new AnimationLayer(this.space));
        this.addChild(new StatusLayer());
        this.scheduleUpdate();
    },



### 给Runner精灵添加物理组件

在以前的教程中，我们使用spritsheet来创建了Runner。在本节中，我们将使用*PhysicsSprite*重写它。 

PhysicsSprite是一个可重用的组件，它可以用赋予一个cocos2d的精灵物理特性。 

下面是创建PhysicsSprite Runner的代码： 

```
        //1. create PhysicsSprite with a sprite frame name
        this.sprite = cc.PhysicsSprite.createWithSpriteFrameName("runner0.png");
        var contentSize = this.sprite.getContentSize();
        // 2. init the runner physic body
        this.body = new cp.Body(1, cp.momentForBox(1, contentSize.width, contentSize.height));
        //3. set the position of the runner
        this.body.p = cc.p(g_runnerStartX, g_groundHight + contentSize.height / 2);
        //4. apply impulse to the body
        this.body.applyImpulse(cp.v(150, 0), cp.v(0, 0));//run speed
        //5. add the created body to space
        this.space.addBody(this.body);
        //6. create the shape for the body
        this.shape = new cp.BoxShape(this.body, contentSize.width - 14, contentSize.height);
        //7. add shape to space
        this.space.addShape(this.shape);
        //8. set body to the physic sprite
        this.sprite.setBody(this.body);
```

代码和注释是不言自明。在*AnimationLayer*的*init*中添加这些代码。


### 调试与测试

恭喜，你已经做了所有的基础工作。现在，您只需按下*Webstorm*中的*debug*键。

![run](res/run.png)

现在你可以看到Runner奔跑穿过屏幕。

##总结

在本教程中，我们向你展示了如何建立Chipmunk物理世界，如何设置物理世界的边界，如何创建一个刚体和相关塑造。我们还可以对Sprite添加物理因素，使其行为更加逼真。您可以从[这里](res/Parkour.zip)得到整个源代码。


##下一节

在下一节教程中，我们将介绍游戏中的镜头移动。而且我们也将用TiledMap取代背景图像。 
更重要的是，我们将在游戏中实现背景的无限循环。请继续关注一个教程。