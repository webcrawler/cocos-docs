#Hello World Cocos2d-HTML5
.
在此教程，我将向你从头向你展示怎样创建一个新的Cocos2d-html5工程。在此之前，我想向你简要描述Cocos2d-html5's目录结构。


##Cocos2d-html5's目录结构

下面是Cocos2d-html5's目录结构

**图1**
![directory](res/directorystructure.png)


###了解目录结构


#### Part1: engine related folders
#### 第1部分:引擎相关文件夹

- **Cocos2d**目录包含所有的核心引擎文件。cocos2d-HTML5的主要构成要素在这些js文件实现。
- **CocosDenshion**目录包含了音频相关的引擎文件
- **extension**目录下包含一些模块，比如EditBox（编辑框），CocosBuilder Reader        cocos2d下简单快速进行精灵，层，场景布局的工具。）和CocoStudio 读取器
- 文件**box2d**和**chipmunk**是第三方的物理引擎。

####第2部分：测试，样本游戏和模块

- 文件夹**HelloHTML5World**包含简单的**Hello Word** 样本。如果你是Cocos2d-htlm5新手，你可能想要看它，它是一个一个完整的Cocos2D-HTML5应用程序的极小化极大骨架。


- **template**太概类似于**HelloHTML5World**，除了 **template**更加简洁。**Template**文件夹是你开始的地方。在本教程的第二部分结束时，我们将创建一个基于这个文件夹的新项目。


- **samples**目录，包含所有的Cocos2d-html5**tests**，它也有一些能玩的小游戏。所有游戏可以通过 javascript在IOS和android 运行


#### 部分3：杂项


- **license**目录包含我们以前提过的所有许可文件，Cocos2d-html5的许可文件是MIT，你可以参考该文件夹来获取有关的Cocos2D-HTML5的许可的详细信息。


- **tools**目录包含JS DOC 工具和 closure compiler。**template**文件包含build.xml
 （是一个closure compiler的配置文件），你可以将您的游戏打包通过ANT成为单一的简单文件。




## 看一看内置的例子



当你已经下载和配置成功 Cocos2d-html5环境。强烈建议看一看内置的例子们。它包括超过90%的Cocos2d-html5特点。而且它是现在你能得到的最有价值的学习资源。



当您调试中WebStorm index.html文件，它会打开Chrome浏览器中的index.html文件，你会得到以下结果：



**图2**

![index](res/index.png)


正如我们可以看到，有许多演示和样品的游戏。如果你对Cocos2d-html5的作用好奇 ，准备了咖啡，坐下来看看内置的样本游戏。

:
### 看一看测试文档
在图2，当你当你打开一个名为“Test cases”的链接。它将会向你展示Cocos2d-html5内置的整个测试。下面是屏幕截图
  


**图3**

![tests](res/tests.png)


这个测试是你学习的最好资源。这个测试几乎展示了每一个 Cocos2d-html5的特点。你能调试这些文件并刷新浏览器你会得到反馈。这是在读大量的文献之前较好的尝试Cocos2d-html5方法。


### 看一下样本游戏


在 Cocos2d-html5中有2个完整的内置游戏样本在 Cocos2d-html5中。所有的资源都完全免费向你开房。这有一些简单的介绍关于这些游戏。

#### MoonWarrior


第一个游戏我想要向你展示是MoonWarrior，它是竖直的射击游戏。在这个游戏样本，一些有用的游戏技术被应用，包括平铺地图，动画，视差时差背景等等。这里是截图，你可以看到源代码的更多信息：


**图4**
![moonwarrior](res/moonwarrior.png)


#### Fruit Attack


这是一个匹配游戏，你可以在附近的水果的位置互换，如果有三个或更多的水果在垂直方向和水平方向的同类型。你能匹配。相同的水果将被清除，下面是截图：

**图5**
![fruitattack](res/fruitaatack.png)


这也有其它类型的游戏，你可以自己试试它们。

## 建立你的第一个“Hello World”项目

最终，是教程最后最重要的部分。在这里，我将不会真的创建一个"Hello World"工程。我将跑酷游戏为例。
接下来，所有史诗般的教程都关于怎样用Cocos2d-html5做跑酷游戏。

根本停不下来！让我们现在开始！


### 创建跑酷游戏骨架



在我们说之前，这有一个**template** 文件夹在Cocos2d-html5 根目录下。右键点击**template**文件选择并复制**Duplicate**，之后修改 **Template Copy**文件到 **Parkour**。




现在，打开你的 WebStorm并且这有一个新的目录在之前的工程根目录下。项目浏览器中看起来像这样：

**图6**
![newnavigator](res/newnavigator.png)


在WebStorm右击**index.html**，选择**Debug 'index.html(1)'**。它将自动打开你的浏览器并且创建一个新的项目。欢呼吧！浏览器的地址是
```
http://localhost:63342/Cocos2d-html5/Parkour/index.html.
```


**注意**

如果 "Hello World" png文件没有正确的显示在你的浏览器里。你可以打开在跑酷下的main.js修改下面代码：
```
   cc.EGLView.getInstance().setDesignResolutionSize(designSize.width, designSize.height, cc.RESOLUTION_POLICY.NO_BORDER);
```

转变

```
   cc.EGLView.getInstance().setDesignResolutionSize(designSize.width, designSize.height, cc.RESOLUTION_POLICY.SHOW_ALL);
```


为什么我们做这个小改变？这是魔术么？哈哈，这是一个很长的故事在cocos2d-x的多分辨率自适应。如果你想知道更多的细节，参见[链接](http://cocos2d-x.org/wiki/Multi_resolution_support)
我们将在以后的教程将这些。

做完这些修改，保存运行，它给我们带来经典的**Hello World** 
截图：

**图7**
![helloworld](res/helloworld.png)


### 示例游戏模板代码分析

**template**已经给我们带来很多东西，但是我们甚至不知道关于它任何事。

比如模板的程序的主入口是什么。这些文件是怎么组织起来的？每一个文件在这个样本程序中起什么作用？在这一部分，我将解释这些问题

#### 看一看这工程所有文件

首先，让我们看看这些文件和目录的结构

**图 8**
![projectstructure](res/projectstructure.png)

从图8，我能可知

- **res**目录。它包含我们需要的所有资源文件。现在，它只包含一些样本图片。但是如果你想向你的游戏或者漂亮的游戏音乐文件加一些元文件。你应该把它们放到这个文件下。你应该向它们选择一个合适的名字。你可能注意到这有2个文件**HD** 和 **Normal** 它们具有完全相同的文件名，但有不同的分辨率。他们是为了 **Multiple resolutions adaption**。你现在可以跳过。在图7，这有一个
HelloWrold在你的屏幕上显示HelloWorld.png。您可以双击以查看磁盘上的实际图像文件。

- **src** 文件。它包含所有实际的游戏逻辑代码。如果一个源文件有上千的 javascript代码，你最好组织它们到子文件夹中，现在，我们的样本有2个javascript 源文件。
- 

- **myApp.js**包含在我们的样本的第一个场景的代码。**resource.js** 定义资源的一些全局变量。


- **build.xm**文件用于封装所有的游戏源代码转换成一个紧凑的文件中。之前我们已经谈过了。


-*index.html** 文件是一个基于HTML5的Web应用程序的入口点。这是一个HTML5兼容的格式。它定义了如设置观点和全屏因素一些元数据。


- The **ccos2d-jsb.js** file is a bridge file between Cocos2d-html5 and Cocos2d-x javascript bindings. You can safety leave it out currently.
- **ccos2d-jsb.js**文件是Cocos2D-HTML5和的cocos2d-X的javascript绑定之间的桥梁文件。你可以安全离开它目前。

- **cocos2d.js**文件是我们的JS引擎的主入口点。它采用自动执行的匿名函数来开始我们的游戏引擎。


 
- **main.js**加载cocos2d.js后调用的Cocos2D-HTML5框架。这就是如c/ c + +语言的主要功能就在于此。

- **applicationDidFinishLanching**函数将定义屏幕方向，颜色格式和资源负载策略。这也是创建你的第一个游戏场景，并显示在浏览器的地方。

-好吧，你已经知道了这些文件和文件夹的用途。现在是时候来了解源代码和执行路径。

#### 该项目的执行路径分析


这是非常重要的是知道一个程序的执行路径。这里是一个图片显示每个cocos2d的，HTML5项目的执行路径：

**图9**
![exepath](res/execute-path.png)

从图9中，我们可以看到，我们的程序从index.html被加载到的浏览器。然后将其移至Cocos2d.js。在这个文件中，代码逻辑不同原因如下配置：

```
 var c = {
        COCOS2D_DEBUG:2, 
        box2d:false,
        chipmunk:false,
        showFPS:true,
        loadExtension:false,
        frameRate:60,
        renderMode:0,       
        tag:'gameCanvas',
        engineDir:'../cocos2d/',
        //SingleEngineFile:'',
        appFiles:[
            'src/resource.js',
            'src/myApp.js'
        ]
    };
```
 
看这程序块，有一个名为**engineDir**的属性对象和命名为** SingleEngineFile**一个注释对象属性文件能够关键点来决定下面的程序的执行路径。在默认情况下，我们有指定engineDir和执行路径会去** N**方向如图9所示。因此，main.js将会在引擎资源之后和指定的 **appFiles**加载。这比阅读我的纯文本更加清楚。但是流程图会做更有利于你理解。

### 给项目做一些小调整

正如我们之前所说，在我们写一些代码之前。让我们做一些小调整

#### 隐藏在我们屏幕左上角的帧数
 
该部分可能是一点点小事。我们能够通过修改在cocos2d.js**showFPS**属性为**false**轻易的达到目标

下面是代码
```
var c = {
        COCOS2D_DEBUG:2,
        box2d:false,
        chipmunk:false,
        showFPS:true,
        loadExtension:false,
        frameRate:60,
        renderMode:0,       
        tag:'gameCanvas', 
        engineDir:'../cocos2d/',
        //SingleEngineFile:'',
        appFiles:[
            'src/resource.js',
            'src/myApp.js'
        ]
    };
```


有很多事情，我们可以通过修改该对象的属性调整。我会给每个属性的表。
属性名         | 选项           | 解释
------------  | -------------  | ------------
COCOS2D_DEBUG |   0,1,2        | 0打开调试过的，1个用于基本的调试，并进行全面地调试
box2d         | true or false  |是否加载的Box2D物理引擎在你的项目里
chipmunk      | true or false  | 是否加载chipmunk 物理引擎在你的项目里 
showFPS       | true or false  | 切换的FPS能见度
loadExtension | true or false  | 是否加载cocos2d的扩展库
frameRate     | 一个正数高于24，通常60-30 | 调整你的游戏的帧速率
renderMode    | 0,1,2 |   选择RenderMode的：0（默认），1（只Canvas），2（WebGL的唯一） 
tag           | "gameCanvas"   | DOM元素来运行cocos2d 
engineDir     |与项目相关的引擎目录 | 指定目录下的引擎代码
SingleEngineFile | 一个game文件  | 这个文件可以通过谷歌关闭编译器生成
appFiles      | 你的游戏源代码列表 |在myApp.js 后添加自己的文件列表
 

cocos2d.js其余都是这样获得的DOM元素按标签和设置游戏运行环境的一些样板代码。如果你感兴趣，去看源代码。

####修改设计分辨率大小



现在的Cocos2D-HTML5取Web浏览器作为一个全屏游戏。我们不需要手动调整画面大小了。我们只需要关心设计的分辨率大小。为了通过 javascript使我们的游戏在IOS和Android 上无缝运行。我们应该把分辨率改成 480*320。打开你的main.js 在 **applicationDidFinishLaunching**把**designSize** to设置为cc.Size(480,320)。

```
var designSize = cc.size(480, 320);
```

And you also should make resolution policy to **SHOW_ALL**:

```
        cc.EGLView.getInstance().setDesignResolutionSize(designSize.width, designSize.height, cc.RESOLUTION_POLICY.SHOW_ALL);
```


如果你想知道我们为什么这样做，请通过(http://cocos2d-x.org/wiki/Multi_resolution_support)获得更多信息

## 总结

在本教程中，我们已经谈到了目录结构和内置的测试和的cocos2d-HTML5的样例游戏。我们还基于Cocos2d-html5创建了第一个项目。在下一部分，我们会努力分析文件和模板的代码结构。
##下一章

在下一章教程，、我将向你展示如何建立你的第一个游戏主菜单的场景。我们将做更多的cocos2d-html5编码.