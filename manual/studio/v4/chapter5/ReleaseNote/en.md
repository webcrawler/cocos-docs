#Release Notes#

**&emsp;&emsp;What's new in version 2.3.1**

- Added custom settings for Cocos Framework & Simulator. (Support Cocos Framework 3.7)

- A “Publish All” option is added in project setting.

- Added API resources, where copying and pasting are available. 

- Added “Simplify Widgets’ Initial Resources” option in Preferences. (Currently support Button, CheckBox and Slider) 

- Support first character, character width and height adjustment for BitmapLabel.

- Added outline and shadow settings for TTC font format.

- Updated FAQ document about package error solution. 

- Improved outline effects. 

- Remove “xxx missed” display. (Support Cocos Framework 3.7)

- Transformed simulator's menu layout from menu bar to context menu on the title block. 

- Improved UI design for Widget and Properties panel to make it user friendly.

- Improve browsers display for JS projects. It is not necessary to add JS project resources to src/resource.js. (Support Cocos Framework 3.7)

- Improved Shadow Offset accuracy by adjusting its value with two decimal places.

- Support copying and pasting in Document page. 

- Added FAQ in cocos Feedback section. 

- Fixed a bug that the outline width is changed from 1 to 0 when open a project. 

- Fixed an issue that when published C++ project resources to VS, the resources were not refreshed timely. (Support Cocos Framework 3.7)

- Fixed a bug that pressing Shift+B/T/Q/W when renaming widgets on structure tree would exit edit mode.    

- Fixed a bug of white screen on rendering section when selecting Clipping for Containers. 

- Fixed a bug on Windows that when dragging animation timeline slider right and back to frame 0, the rendering section gives no response. 

- Fixed a bug that when dragging animation time slider to the right, it would keep moving when the mouse button is released, and the rendering section gives no response. 

***Note** Please quit cocos and Cocos Studio before installing v2.3.1.* 


**&emsp;&emsp;What's new in version 2.3.0**

- Added support for quickly switching reference coordinates and coordinate origin after selecting multiple objects in 3D scenes.

- Added rulers and guides in Scene, Node and Layer.

- Save list of resources to .json file when publishing them in JSON data format.

- Improved gridlines support in 3D Scene.

- Added visible/ invisible settings for Anchor Point, the shortcut is Ctrl+Shift+A (Windows)/ Command+Shift+A (Mac).

- Updated cocos documentation in Launcher.

- Fixed a bug that the Label still have an outline effect when outline width is set to zero.

- Fixed a bug that after changing FNT and refreshing the list of resources, the effect failed to render.

**&emsp;&emsp;What's new in version 2.2.9**

- Fixed a bug that when extracting .png images from a plist file,  images with transparency will be lost.

**&emsp;&emsp;What's new in version 2.2.8**

- Added 3D world axis to adjust view. 

- Added 4 arrow keys to move 3D scene. 

- Added a default camera in 3D scene. 

- Added support for 3D objects scaling. 

- Added a right-hand button and a shortcut key to move 2D canvas, press the right-hand button (Q) to enable move canvas and press arrow keys (W) to disable the function. 

- A lua publish plugin is available in Cocos Store. 

- New design of Launcher interface, added support for opening a project or opening the folder containing the project. 

- Updated a tutorial for getting started with cocos. 

- Eased the process of deleting projects from resource panel, remove reference or move to recycle-bin/ trash.

- Fixed a bug that PercentWidthEnabled and PercentHeightEnabled cannot update. 

**&emsp;&emsp;What's new in version 2.2.6**
	
Fixed a bug that images may lost when open a project containing multiple spritesheets.

**&emsp;&emsp;What's new in version 2.2.5**
									
- One click to deploy and run App on iOS, Android, Win32, Mac and in Browser. 

- Package JS projects to HTML5 App.

- Added support for 3D widget extensions. 

- Added support for copying *.csd file in the resource panel, the shortcut key is Ctrl/Command+D.

- Double click the nested *.csd file to edit it directly.  

- Added stroke and shadow settings for Buttons and Label. (Based on Cocos2d-x 3.6)

- Added settings for slow motion animation. (Based on Cocos2d-x 3.6)

- Added blending functions for Sprite and Particle widgets. (Based on Cocos2d-x 3.6)

- Added support for the history of color picker. 

- Batch edit TreeNodes to display or be locked.  

- Simplified the process of creating a project, integrated complete projects and resource projects into cocos projects. 

- Upgrade resource projects to complete projects. 

- Shortcut (Shift + Q/W/T/B) to adjust the render order of objects. 

- Added “append the beginning frame as the ending frame” option, to easily create a repeating loop of SpriteSheet animation. 

- No limit to rename the node. 

- Enable drag and drop for 9-Slice. 

- Support attached resources for widget, default size of the widget is the resource’s size.  

- Improved the display of 3D grid lines. 

- Improved the UI of publishing and packaging projects. 

- Fixed a bug for the imported 1.6 UI projects, that only change the tree display but the visibility of widgets.

- Fixed a bug that the size of ScrollView Area is limited by its content size. 		
																		
**&emsp;&emsp;What's new in version 2.2.1**
    
- Fixed a bug of the extension used for SpriteSheet files.

**&emsp;&emsp;What's new in version 2.2**
	
- Introduced 3D scene editor— with modules, particle effects and cameras (Based on Cocos2d-x 3.5). 

- Added support for custom controls with Lua scripting.

- A new look and feel to the Cocos Store user interface, one click to download, install and remove resources, description and comments about resources are provided.

- Added support for varying playback speed of animation in order to provide a better preview experience (Based on Cocos2d-x 3.5). 

- Added support for custom data about widgets’ advanced features (Based on Cocos2d-x 3.5).

- Added support for multi-resolution, allow free adjustment to common screen resolution. 

- Improved the data exported from the editor, support Cocos2d-x 3.4 Final.  

- Improved the experience of creating projects by integrating New Project and Sample Project. 

- Name property check on new projects in order to make sure variable names are valid. 

- Modify layer size in Properties section. 

- Set Pin & Sizing properties directly with numbers.  

- Empty Button’s default background files to reduce file size.

- Improved .csd files synchronization.

Improved the efficiency of opening a project. 

Fixed a bug on Mac OS X 10.10.2 that updating package could not be opened automatically. 

***Note** Data exported from cocos v2.2+ can be loaded in Cocos2d-x v3.4+.* 
