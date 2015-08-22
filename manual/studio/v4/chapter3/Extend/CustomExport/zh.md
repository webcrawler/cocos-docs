# **自定义数据导出格式** #

&emsp;&emsp;1.自定义数据导出格式

&emsp;&emsp;Cocos Studio默认支持三种导出格式：CSB、Json、Lua。用户可能选择自己需要的格式进行导出，如果有特殊的需求，可以自定制导出，相应的读取部分也需要自己实现。只需要实现CocoStudio.Projects.IGameProjectSerializer接口（参见示例工程中的PublishExtend目录里的CustomSerializer类）。接口的定义如下：

    [TypeExtensionPoint]
    public interface IGameProjectSerializer
    {
        /// <summary>
        /// 序列化器ID
        /// </summary>
        string ID { get; }

        /// <summary>
        /// 对外显示的名称
        /// </summary>
        string Label { get; }

        /// <summary>
        /// 执行序列化
        /// </summary>
        /// <param name="info">发布设置信息</param>
        /// <param name="projFile">项目文件</param>
        /// <returns>错误信息（正常结束时为空）</returns>
        string Serialize(PublishInfo info, IProjectFile projFile);

        /// <summary>
        /// 执行上下文初始化操作，在第一次 Serialize 调用之前调用它。
        /// 对于一个 Studio 解决方案只应该调用一次。
        /// 注：每个 *.csd 文件会调用一次 Serialize.
        /// </summary>
        void ContextInitialize(PublishInfo publishInfo);

        /// <summary>
        /// 执行上下文结束操作，在最后一次 Serialize 调用之后调用它。
        /// 对于一个 Studio 解决方案只应该调用一次。
        /// 注：每个 *.csd 文件会调用一次 Serialize.
        /// </summary>
        void ContextFinalize(PublishInfo publishInfo);
     }

&emsp;&emsp;其它部分请参见示例工程。

&emsp;&emsp;目前用户可以实现将CSD文件（即：Cocos Studio的工程文件）转化为自己需要的格式。

&emsp;&emsp;2.其它

&emsp;&emsp;在后续的开发过程中文档的内容会根据反馈持续更新。如有更新，请以新的版本为准。

&emsp;&emsp;如果您对于Cocos Studio扩展有任何的意见或者是建议，请在论坛或者是开发者群里反馈给我们。感谢您对Cocos Studio的关注和支持，我们将回报您以更好用的产品。