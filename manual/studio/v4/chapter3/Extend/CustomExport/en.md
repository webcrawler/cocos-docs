#Customizing Exported Data Formats#

By default you can export data from Cocos Studio to other formats, including CSB, JSON and Lua. You can also customize export formats by implementing the following interface: `CocoStudio.Projects.IGameProjectSerializer`.  For more information, see the description of 
"CustomSerializer" in Samples. 

Interface Description:

    [TypeExtensionPoint]
    public interface IGameProjectSerializer
    {

        string ID { get; }

        string Label { get; }

        string Serialize(PublishInfo info, IProjectFile projFile);

        void ContextInitialize(PublishInfo publishInfo);

        void ContextFinalize(PublishInfo publishInfo);
     }

Currently you can transfer CSD file (Cocos Studio project file) to other targeted file formats. 

***Note** The contents of the document are under continuous update based on users' feedback. Please check the latest version for reference. If you have any suggestions or comments on the extensions of Cocos Studio, please let us know. Thanks for your interest and support for Cocos Studio, and for helping us make a better product.*  