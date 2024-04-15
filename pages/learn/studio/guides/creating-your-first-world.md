# **Creating Your First World (part 1)**

## **Introduction**
Looking to craft your first immersive, virtual world? You're in the right place at the right time! Let's dive into the process of using Studio Hub to generate, illuminate, and test your inaugural creation. It's easier than you think and a lot more fun!

This guide is split into multiple parts. In part 1, we will cover how to install the tools you'll need, make a simple World, add some assets and lighting to it, and testing it inside of Unity.

### **Step 1: Setting Up The Tools**
Let's install and set up the tools you'll need to start building worlds.

1. Download the [Studio Hub](https://create.highrise.game/highrise-studio) and install it on your computer. The Studio Hub is designed to guide you through installing the correct version of Unity.
2. Follow the instructions in Studio Hub and allow it to download and install Unity and the accompanying Highrise Studio Package. 

### **Step 2: Creating a New World**
1. In Studio Hub, click on `New Project`
2. Select the **Basic Template**. Templates can be a great way to learn how different games are structured.
3. Name the Project *"My First World"*
4. Leave the location to the default. This is where your project will be saved to on your computer.
5. Click on `Create Project`

### **Step 3: Using Unity**
Once you create the project, Studio Hub will launch Unity and you'll be loaded directly into the World you're about to build. From here, you can **Sign In** to your Highrise account to start testing with your Highrise avatar, and you can also hit the **Play** button to test the World you're working on.

1. Inside Unity, you can use the `Sign In` button to sign into your Highrise Account.
2. You can now test your world with the `Play` button in the middle of the top toolbar.

![play button](/assets/learn/guides/studio/play-button.png)

### **Step 4: Making Changes**
You can use the editor to directly manipulate the objects in your World. You can either use the gizmos or alter the properties of an object directly in the inspector view. 

1. **Moving and Changing Objects**
	- Select the Green Block in the World. 
	- Press and hold on the green arrow to move it up to 5 on the Y-aix _or_ change the Y value of the Green Block to 5 in the inspector window
	- In the inspector window, change the scale to 0.5, 0.5, 0.5. Notice the Green Block is now much smaller than before

2. **Adding Objects** 

   There are many ways to add objects into your world. Here are a few common methods:
   - **Highrise Asset Store:** The Highrise Studio Package comes with its own catalog of ready-made assets. You can drag and drop these objects directly into your World and they should work out of the box. 
   - **Unity Asset Store:** Unity's official Asset Store is a treasure trove of ready-made assets created for all projects built with Unity. To access, simply click on `Window > Asset Store`, then search online to select your chosen asset, then follow the official Unity steps to import the asset directly into your project.
   - **Manual Import:** To import locally stored files, right-click within the Project panel, select `Import New Asset`, and browse to your desired file.
   - **Drag & Drop:** An effortless way is to directly drag and drop files from your Explorer/Finder into Unity's Project panel. 
   
   Note: Highrise Studio does not support adding new C# runtime scripts.

3. **Update The Walkable Area**

   Since we've made changes to the World that will affect where the avatars can walk, we'll need to update the walkable areas by updating (baking) the **NavMesh**.

   - Select the NavMesh in the object Hierarchy view on the left
   - In the inspector view on the right, select `Bake`
   - Notice the blue area (indicating what's walkable) has now changed to cover the entire ground

4. **Adding Scripts**

   In order to create a new Lua script to harness the power of Highrise Studio, you simply right-click in the **Project** panel, select `Create > Lua > Script`, and name your script. To get started scripting with Lua for Highrise check out [Scripting a GameObject](https://create.highrise.game/learn/studio/guides/scripting/scripting-a-gameobject)

   For this guide, we're going to make the Green Block rotate
   - Create a script and name it "Rotate"
   - Double click on it to open it with your code editor
   - Add the following lua code:
   ```lua
   function self:Update()
     local rotationAngle = 5 * Time.deltaTime
     -- Rotate the object around its Y-axis (vertical axis)
     self.transform.localEulerAngles = self.transform.localEulerAngles + Vector3.new(0, rotationAngle, 0)
   end
   ```
   - Save your changes in the Lua file and go back to the Unity editor.
   - Select the Green Block, in the top left of the inspector, uncheck the box that says `Static`.
   - Next, select `Add Component` in the inspector view.
   - Type in Rotate in the search field, and select the Lua script you just created.
   - That's it, you've added the Rotate lua script to the Green Block. You can now hit play and see it in action.


### **Step 5: Adjusting Lighting**

Go to `Window > Rendering > Lighting` (or press `(CMD/CNTRL) + 9`) to open the window.

Here you can access the **Scene** and **Environment** settings:
   - The **Scene** settings allow you to control the lightmap, map resolution, and samples.
   - The **Environment** settings allow you to adjust the Skybox material and environment lighting.
       - The **Skybox** is a Gradient material named *Sky* located in `Assets > Template > Art` in Unity's Project tab.

1. **Add Lights**
   - Right click on the **Hierarchy** view on the left and create a light.
   - Make sure the light **Type** is set to **Baked**

   - **For Stationary Meshes** Make sure all the 3D Objects *(Meshes)* you want affected are set to **Static**. *static is a checkbox next to the Object's name in the inspector panel*
   - **For Animated or Moving Meshes** Make the Object 
     - **Non-Static** Create a **Light Probe Grid** to light the dynamic meshes. [Light Probes tutorial](https://www.youtube.com/watch?v=_E0JXOZDTKA)

2. **Bake the lights**

   After laying out your **Lights** and **Objects**:
   - Make sure all Lights and stationary Meshes are marked **Static** or **Baked**
   - In the Lighting Panel select **Generate Lighting** to calculate your new Lights and Shadows.

---
**Congratulations! You've Created Your First World**

That's it! You've successfully created your first World using the Highrise Studio. Now, you can continue to build and customize your virtual world with rooms, models, and more. Continue to part 2 of this guide to learn how to publish and release the World you've just built.
