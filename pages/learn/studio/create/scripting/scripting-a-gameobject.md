# **Scripting a GameObject**

## **Introduction**
In this guide you will learn how to create a basic Lua script and add it to a game object.

### **What is a Lua Script?**
- Lua is the scripting language used for creating dynamic and interactive Highrise Worlds.
- Learn more about how we use Lua to connect to Unity GameObjects [Here.](https://create.highrise.game/learn/studio/api/classes/LuaBehaviour)

>❗️Caution
>When building a Highrise World, C# scripts are not included in the package build.
>Make sure to only implement using Lua Scripts.

# **Creating a Hello World Script in Unity with Lua**

### **Step1: Creating the Script File:**
   - Click on **Project** in the Unity editor panel.
   - Click on the **+** icon on the top left corner of the panel to create a new asset.
   - Navigate to **Lua > Script** and select it.
   - Name your script file "HelloWorldScript".

![Create-Script](/assets/learn/guides/studio/create-script.png) 
![New-Script](/assets/learn/guides/studio/new-script.png)

### **Step2: Opening the Script in VS Code:**
   - Double-click the script file to open it in Visual Studio Code (VS Code).
   - In VS Code, press **Ctrl/Cmd + Shift + X** to open extensions.
   - Search for "Highrise Studio Tools" and install it.

![Studio-Extension](/assets/learn/guides/studio/studio-ext.png)

### **Step3: Writing the Script:**
   - In your script file, type the following Lua code:
     ```lua
     print("Hello World")
     ```
   - Save your script file.

### **Step4: Adding the Script to a GameObject:**
   - Back in Unity, click on the **+** icon in the top left corner of the **Hierarchy** panel.
   - Select **Create Empty** to create a new GameObject.
   - Name your new object as desired.
   - Select the newly created GameObject in the Hierarchy panel.
   - In the **Inspector** panel, click on **Add Component**.
   - Search for your Lua script by name ("HelloWorldScript").
   - Alternatively, you can drag your script directly onto the object in the Hierarchy or into the Inspector panel.

![Add-Script](/assets/learn/guides/studio/add-comp.png) 
![Added-Script](/assets/learn/guides/studio/added-comp.png)

### **Step5: Running the Script:**
   - With the script attached to the GameObject, press **Play** in Unity to run the scene.
   - Click on the **Console** panel to see the output, which should display "Hello World".

![Console-Output](/assets/learn/guides/studio/console-print.png)

By following these steps, you've successfully created a Lua script in Unity, attached it to a GameObject, and executed it to print "Hello World" in the Unity console. Happy coding!

> 📖
>For more detailed syntax, please refer to the [Lua API Docs.](https://create.highrise.game/learn/studio/api/classes/LuaBehaviour)
