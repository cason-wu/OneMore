Come up with a name for the functional domain to control with your new settings. Existing domains include General, Images, Keyboard, etc. For the examples below, we'll use the ubiquitous "Foo" category.

# Create A New FooSheet

1.  In Visual Studio Solution Explorer, right-click and Copy the Commands\\Settings\\GeneralSheet.cs main file
2.  Right click the Commands\\Settings folder and choose Paste
3.  Right-click the new file, and Rename, replacing "GeneralSheet - Copy" with the new name, e.g., "FooSheet"
4.  Right-click the file and choose View Code
    -  Rename the GeneralSheet class and constructor to FooSheet
    -  Rename the nameof() line to FooSheet
    -  Open the FooSheet.Designer.cs and rename the partial class to FooSheet
5.  Double-click FooSheet.cs to open the visual designer
6.  Modify the UI with controls you need to implement Foo settings
7.  Add a new resource for the sheet title named Resx.FooSheet\_Title
8.  In the constructor, set the Title property to Resx.FooSheet\_Title

# Add FooSheet to The SettingsDialog

1.  Double-click SettingsDialog.cs to open the visual designer
2.  Select the tree view and edit its Nodes property
3.  Create a new root node
4.  Set the name property to fooNode
5.  Set the text property to Foo
6.  Change the order of the nodes to they are sorted alphabetically
7.  View code for SettingsDialog.cs
8.  Add Foo to the Sheets enum
9.  Create a new Resource called SettingsDialog\_fooNode.Text with the value Foo
10.  In the constructor, set the tree node text to Resx.SettingsDialog\_fooNode\_Text
11.  In the Navigate method, add an item to the switch statement for FooSheet; this should match the sequence number set in the tree view for the node

# Collect Settings

1.  Override the CollectSettings method
2.  Get the appropriate SettingsCollection, preferrably using the Name property
3.  Set all settings for this sheet
4.  Return true if any of the properties have changed or were added and will require OneNote to restart in order to be recognized; return false otherwise