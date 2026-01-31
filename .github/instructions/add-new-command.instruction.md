To add a new command to OneMore

1.  Add a new class file in the appropriate Commands\\domain folder.
    -  Name the class using form nameCommand such as TrimCommand
    -  The file name should match the class name such as TrimCommand.cs.

2.  Keep the namespace as River.OneMoreAddIn.Commands
3.  Derive the class from the Command base class and declare it as internal
4.  Add a public constructor, even if its body is blank
5.  Override the Command.Execute method

Example:

```c#
namespace River.OneMoreAddIn.Commands
{
    internal class TrimCommand : Command
    {
        public TrimCommand()
        {
        }

        public override async Task Execute(params object\[\] args)
        {
        }
    }
}
```

6.  Add a new method to the AddinCommands.cs file to invoke the command
    -  The name should be derived from the class, replacing Command with Cmd such as TrimCmd
    -  It must be declared async and accept an IRibbonControl parameter
    -  It must invoke the command using factory.Run as shown here

    ```c#
    [Command("ribTrimButton\_Label", Keys.None, "ribCleanMenu")\]
    public async Task TrimCmd(IRibbonControl control)
        => await factory.Run<TrimCommand>(false);
    ```
    -  The CommandAttribute first parameter specifies the resource ID used to translate the name of the command. This must be named using the form ribNameButton\_Label
    -  The second parameter defines the default key binding; set to Keys.None to indicate to binding
    -  The third parameter names the functional domain (for future use)

7.  Add a button control or menu item to the Ribbon\\Ribbon.xml file
    1.  Specify a unique id and label property. The id should match the CommandAttribute resource name with the \_Label part, for example ribTrimButton
    2.  Choose an appropriate imageMso name from [imageMso List](https://bert-toolkit.com/imagemso-list.html)
    3.  Set the onAction property to the nameCmd method added to AddInCommands.cs

    ```c#
    <button
      id="ribTrimButton"
      imageMso="AutoTextGallery"
      getLabel="GetRibbonLabel"
      onAction="TrimCmd"/>
    ```