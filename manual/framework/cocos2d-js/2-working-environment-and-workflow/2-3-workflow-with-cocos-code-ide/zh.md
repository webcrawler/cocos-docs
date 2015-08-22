# 2.3 使用Cocos Code IDE开发

前面一个章节中开发者已经了解如何使用 Cocos Console 开发并发布 Web 和各原生平台应用，这里要给大家介绍的是图形化的工具 Cocos Code IDE。

Cocos Code IDE 是基于 Eclipse 开发的产品，不仅封装了 Cocos Console 的绝大部分功能，简化了用户的操作，而且还提供JavaScript断点调试、代码热更新等开发者迫切需要的功能。

目前 Cocos Code IDE 支持在 Windows 7/Windows 8 上运行，并且支持 N 个主流原生平台：

+ Android
+ iOS
+ Mac OS X
+ Windows 7/Windows 8

## 安装Cocos Code IDE

1. Windows 用户需要先安装 Python 2.7.x， Mac OS X 用户可以忽略此步骤。以下是推荐的 Python 版本及下载链接：

    [Python 2.7.6](https://www.python.org/download/releases/2.7.6/)
  
2. 请前往[cocos 下载页](http://cn.cocos2d-x.org/download/)下载 Cocos Code IDE；
3. 另外一些打包 Android 应用需要用到的链接：

	+ [Android SDK](https://developer.android.com/sdk/index.html?hl=sk)
	+ [NDK](https://developer.android.com/tools/sdk/ndk/index.html)
	+ [ANT](http://ant.apache.org/)
4. 如果需要打包 iOS 版本，你还需要安装 Xcode。

## 创建工程
在 IDE 中切换到 JavaScript 透视图后，通过 File->New->Cocos JavaScript Project 可以很方便的打开创建工程的向导，在向导里面可以对工程进行很多的基本设置。

## 检查工程
上面创建出来的是一个非常简单的 Helloworld 工程，你只要点击 IDE 工具栏上的 Debug 或者 Run 按钮，无需编译任何 C++ 代码，就可以通过我们预编译的 Runtime 看到游戏的实际表现效果，而且还可以通过 Debug Configurations 按钮切换不同的目标平台。

## 关于Runtime
### 什么是 Runtime
上文中提到了使用 Runtime 查看游戏的表现效果，可能开发者对这个新名词产生疑问：Runtime 是什么呢？

你可以把它理解成一个包含各种基础功能但不包含任何游戏逻辑的应用，给它不同的 Javascript 代码，就是一个全新的游戏。

### 定制自己的 Runtime
当开发者需要给 Runtime 新增一个基础功能时，就需要自己编译 Runtime 了，大致的步骤是：

1. Cocos Code IDE 中右击工程，Cocos Tools -> Add Native Codes Support... 添加 Runtime 的源代码
2. 有了源代码之后就可以通过 Xcode、VS 等工具添加新的扩展了
3. 然后通过 Cocos Tools -> Build Custom Runtimes... 编译出新 Runtime

## 编写JSB代码
工程创建出来之后，开发者当然是要用自己的游戏逻辑替换掉上面的 Helloworld，做一个属于自己的游戏，开发者大量的工作都是在和代码和资源打交道。

Cocos Code IDE 支持 JavaScript 语言的代码智能提示，体验愉悦的编码过程。并且，Cocos Code IDE 还有资源文件提示，资源预览等等，可以非常有效的减少笔误造成的程序错误。

## 代码热更新
代码的改动可以即时的反映到游戏中，这个过程大部分时候不需要你重启游戏，这是 Cocos Code IDE 的一大亮点，也能给开发者节省大量的测试时间。

## 代码调试
另外，你再也不需要使用打印日志的方式调试逻辑代码了，Cocos Code IDE 支持对 JavaScript 的断点调试，而且这个功能是跨平台的，不管是桌面版还是Android、iOS真机设备，都有着一致的调试体验。

当然，桌面版的性能总是比终端设备强，所以建议开发者尽量使用桌面版调试并修正问题。

## 项目发布
### iOS 发布
只要在 Cocos Code IDE 中右击工程，在 Cocos Tools 中选择 Package to IPA for iOS...，就可以通过向导打包出可在苹果上架的 IPA 包了。

### Android 发布
同样右击工程，选择 Package to APK for Android...，使用正式版签名可以打包出一个可上架的 Android 包。

### Web 发布
暂时只能通过 Cocos Console 完成，请参看前面章节。

## 可能需要的链接：
[Cocos Code IDE 相关文档](https://github.com/chukong/cocos-docs/blob/master/catalog/code-ide/zh.md)
