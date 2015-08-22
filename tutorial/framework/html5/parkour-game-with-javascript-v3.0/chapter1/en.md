#Setting up the Cocos2d-JS Development Environment
This tutorial will show you how to set up the Cocos2d-JS development environment. The examples in this tutorial will be for MacOS 10.9 -- Yeah! The Maverics.

##Download the required software packages

1. Download and install WebStorm 7. The current stable release of [WebStorm 7](http://www.jetbrains.com/webstorm/download/index.html) is 7.0.3. Why do we choose WebStorm? Because it provides many feature like JavaScript code syntax completion, debugging, syntax highlighting, version system integrated etc. You can go to WebStorm's official website for more information.

2. Download Cocos2d-JS v3.0 alpha from the official website of Cocos2d-x. Here is the [Link](http://cocos2d-x.org/download ). After you have downloaded the Cocos2d-JS v3.0 alpha. You should unzip it to a proper location. In our case, I unzip it at ~/work/Cocos2d-js-v3.0-alpha2.The ~ symbol represents your home directory path, which in our case is /Users/linshun. 

**Note:** 
	
You can also get the cutting edge version of Cocos2d-JS through GitHub. Here is the [Cocos2d-JS github repository](https://github.com/cocos2d/cocos2d-js ) .The active development is done on the **develop** branch.

3.  Download and install Chrome 34 and the [JetBrains-IDE-support ]( https://chrome.google.com/webstore/detail/jetbrains-ide-support/hmhgeddbohgjknpmjagkdomcpobmllji)  extension.
 
All right, let's see how to configure WebStorm 7 to develop and debug our Cocos2d-JS applications.

## How to create a new project
Cocos2d-JS provides a console tool that makes the development of CH5 and JSB applications simpler and much more convenient. You can use it to create a new project, publish it to android, iOS, Mac OS or web, and it's very easy to use.

### Console tool setup
First, clone the Cocos2d-JS repository and update all sub modules. Open the console in the Cocos2d-JS folder, and run ./setup.py in the console. You may need to provide your NDK, Android SDK and ANT's path during the setup. Note that this tool is developed with Python, so you will need Python (32bit) 2.7.5 or later installed on your machine (Python 3 is **not supported**).
**Note:** please execute source ~/.bash_profile to make the environment setting take effect immediately.

### Create a new project

```
// Create a project containing Cocos2d-x JSB and Cocos2d-html5:
cocos new -l js

// Create a project only containing Cocos2d-html5:
cocos new -l js --no-native

// Create a project with a specified name in a specified directory:
cocos new projectName -l js -d ./Projects
```
For this tutorial, use cocos new -l js to create a MyJSGame in current workspace.

### Run the project

* To run your Cocos2d-JS project with a web server use:

```
cd ~/work/MyJSGame
cocos run -p web
```

* To compile and run your project in Cocos2d-x JSB:

```
cd ~/work/MyJSGame
cocos compile -p ios|android|mac
cocos run -p ios|android|mac
```

* Useful options:

```
-p platform : The platform can be ios|mac|android|web.
-s source   : Your project directory, if not specified the current directory will be used.
-q          : Quiet mode, removes log messages.
-m mode     : Mode debug or release, debug is default
--source-map: General source-map file. (Web platform only)
```

## Configure WebStorm to work with Cocos2d-JS

Start by launching WebStorm 7. If it is your first time launching WebStorm, you will be asked to set your personal preferences like choosing key mappings. 

Here is a screenshot of launching WebStorm:

   **Figure 1**

  ![splash](res/sbsplashscreen.jpeg)


**Note:** 
   The section Recent Projects should be empty if this is your first time running WebStorm.

Now, let's get Cocos2d-JS working with WebStorm.

1. Choose **Create New Project from Exisiting Files** 
	
	You will be prompted with the following options:
	
	**Figure 2**
	
	![option](res/chooseserver.png)

2. Choose **Source files are in a local directory, no Web server is yet configured** and click **Next** to continue.

	**Figure 3**

	![choosedirectory](res/choosedirectory.jpeg)

3. Expand the directory tree to specify where you have put your MyJSGame source code. After you have specified the correct directory, note that the **Finish** button is still gray.

4. Set the directory as **Project Root**. Click the **Project Root** button and the **Finish** button will be enabled.

	**Figure 4**

	![setupfinish](res/setupfinish.jpeg)

5. Congratulations! You have successfully configured a Cocos2d-JS project for WebStorm.

## Play with Cocos2d-JS

Since you have added the entire Cocos2d-JS project directory to WebStorm 7. WebStorm will parse all of the Cocos2d-JS source code. This allows you to use accurate syntax completion. This can be seen if, for example, you open **MyJSGame/src/myApp.js**:

**Figure 5**

![syntaxac](res/syntaxac.png)

If you want to use third party JavaScript libraries in your Cocos2d-JS games, you can add them to the WebStorm library for parsing and enable syntax completion.

To add a third party library:

### (Optional) Add a third party library for parsing

1. Click **Settings** to launch the project settings dialog:

	**Figure 6**

	![clicksettings](res/clicksettings.png)

2. After clicking the **Settings** menu, it will popup the following dialog:
	
	**Figure 7**
	
	![addjslib](res/addjslib.png)

3. Now you should click the **Add...** button and you will be prompted to specify the location of your JavaScript library. 
	
	**Figure 8**
	
	![addjslibpath](res/addjslibpath.png)

### Debugging your code using WebStorm
Now it's time for us to debug our Cocos2d-JS code.

#### Connect WebStorm to Google Chrome with the JetBrains Chrome extensions
1. Right click **index.html** under **~/work/MyJSGame** and choose **Debug 'index.html'**:
	
	**Figure 9**
	
	![debugindex](res/debugindex.png)
2. Now Google Chrome will launch automatically. If you put your mouse above the JetBrains plugin, you will see that it has been connected to WebStrom 7.0.3:

	**Figure 10**
	
	![chome](res/chrome.png)

**Note:** This step is very straightforward once you have installed the plugin--"JetBrains IDE support". When you click the debug menu in WebStorm it will connect to Google Chrome automatically. How convenient! You can also click the **JB** icon in the right side of Google Chrome's side bar and it will bring you to the WebStorm IDE immediately.

#### Debug JavaScript code in WebStorm
In WebStorm double click **MyJSGame/src/myApp.js** to view the source code.

1. Set a break point by right clicking the left sidebar of the viewport showing the myApp.js source code.

	**Figure 11**
	
	![setbreakpointer](res/setbreakpoint.jpeg)

2. Start debugging. WebStorm will launch your Chrome browser automatically and run the sample project. The program will stop at the break point we have just set, and the WebStorm editor will be switched to the Debug View:

	**Figure 12**
	
	![debugview](res/debugview.png)

3. Now you can do debugging tasks like step out, step into, step over, continue executing etc. 

## Summary
You have taken the basic steps to configure Cocos2d-html5 with WebStorm 7. Like auto completion and debugging. If you have any questions or suggestion about this tutorials, please let us know. We appreciate your contribution.

## Where to go from here
In the next tutorial, you will learn how to set up an new Cocos2d-JS project. We will also take a look at built-in tests and sample games made with Cocos2d-JS.
