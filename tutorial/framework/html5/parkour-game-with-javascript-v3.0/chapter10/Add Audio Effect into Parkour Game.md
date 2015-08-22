#往跑酷游戏中添加音效

##简介

在这片教程中，我想要向你介绍怎么样在跑酷游戏中添加音乐。

##具体内容

###HTML5支持的音频格式

首先，让我们来看一下HTML5支持的音频格式：

[](res/html5-audio-format.png)

这里我们使用**ogg**格式。因为安卓和谷歌都支持这种格式的音频文件。

###在我们的游戏中添加音频支持

####复制音频文件

首先，复制我们需要的音频文件并添加到**res**目录下。我们可以再**总结**部分下载我们的项目，并在其中找到我们需要的音频文件。

我们使用**background.ogg**作为背景音乐，用**jump.ogg** 和 **pickup_coin.ogg**作为跳跃和拾取金币的音效。

然后，我们在**resource.js**中定义一些全局变量：

    var res = {
    // 添加到列表中
    background_mp3 : "res/background.mp3",
    jump_mp3 : "res/jump.mp3",
    pickup_coin_mp3 : "res/pickup_coin.mp3"
    };
    
    var g_resources = [
    //添加到列表中
    res.background_mp3,
    res.jump_mp3,
    res.pickup_coin_mp3
    ];

**注意**：对于同一个音频文件，推荐同时使用**MP3**和**ogg**两种格式来保证不同浏览器之间的兼容性。你并不需要在**resource.js**中同时列出两种文件，可以只列出**MP3**格式的文件，因为当你的游戏运行在具体的设备上的时候，**MP3**在苹果的IOS和MAC设备上的兼容性更好一点。

####在游戏中添加音频处理的代码

首先，在进入**PlayScene**场景的时候，添加背景音乐：

**注意：**在**PlayScene.js**中的**onEnter**函数的底部添加下面的代码：

    //添加背景音乐
    cc.audioEngine.playMusic(res.background_mp3, true);
    
    this.scheduleUpdate();

然后，在游戏结束的时候，我们要停止背景音乐。因此在函数**collosionRockBegin**中添加下面的代码：

     //停止背景音乐
    cc.audioEngine.stopMusic();

最后，添加跳跃和拾取金币的音效：

    //在 AnimationLayer中的jump函数中添加跳跃的音效
    //跳跃的音效
    cc.audioEngine.playEffect(res.jump_mp3);
   
    //在PlayScene中的函数collisionCoinBegin中添加拾取金币的音效
    cc.audioEngine.playEffect(res.pickup_coin_mp3);

保存所有的改动并运行游戏。现在你的游戏就充满了音乐。

##总结

在此教程中，我们看到了让现存的游戏中添加音乐的支持是多么的简单。你可以在[这里]([here](./res/Parkour.zip))下载整个项目的代码。

###发展方向

现在我们的跑酷游戏又完成了一个新的里程。在下面的教程中，我们会添加一些跨平台的支持并为我们的js文件加密。


