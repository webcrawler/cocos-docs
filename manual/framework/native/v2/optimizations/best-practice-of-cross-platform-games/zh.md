跨平台游戏最佳做法
===

`__super keyword`这个关键字仅在微软VC中提供，所以需要调用父类的每个名字，而不是“__super”。
`文件夹分离符号`“\”是Windows平台的文件夹分离符号。至于跨平台游戏，必须在所有资源中使用“\”。`标准C库及STL`使用标准C库及STL，不要使用每个平台的特殊API。注意：一些函数看起来像标准C库成员，但实际上不是。这点对于只有Windows平台开发经验的初级程序员来说尤其需要注意，初级程序员往往无法区别标准C库与Win32 API之间的区别。 