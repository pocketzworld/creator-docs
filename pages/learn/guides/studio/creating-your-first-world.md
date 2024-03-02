# **Creating Your First World**

## **Introduction**
Looking to craft your first immersive, virtual world? You're in the right place at the right time! Let's dive into the process of using Studio Hub to generate, illuminate, and test your inaugural creation. It's easier than you think and a lot more fun!

### **Step 1: Creating a New World**
1. Download [Unity Hub](https://unity3d.com/get-unity/download), the key to utilizing Highrise Studio Hub.
2. Launch Studio Hub. You will be prompted to install the correct Unity version if needed.
3. Click "New Project" and opt for the Basic Template.

![open studio hub](assets/learn/guides/studio/open-studio-hub.png)

4. Now that we're in Unity, on the top left toolbar you can use the "Sign in" button to sign into your Highrise Account.

![before sign in](assets/learn/guides/studio/before-sign-in.png)    ![after sign in](assets/learn/guides/studio/after-sign-in.png)

5. You can now test your world with the "Play" button in the middle of the top toolbar.

![play button](assets/learn/guides/studio/play-button.png)

### **Step 2: Adding Assets and Scripts**
There are many ways to import assets like textures and meshes into Unity. Here are a few common methods:
- **Asset Store:** Unity's built-in Asset Store is a treasure trove of ready-made assets. To access, simply click on `Window > Asset Store`, select your chosen asset, and import directly into your project.
- **Manual Import:** To import locally stored files, right-click within the Project panel, select `Import New Asset`, and browse to your desired file.
- **Drag & Drop:** An effortless way is to directly drag and drop files from your Explorer/Finder into Unity's Project panel. 
- ---- Note that Highrise Studio does not support adding new C# runtime scripts.

In order to create a new Lua script to harness the power of Highrise Studio, you simply right-click in the Project panel, select `Create > Lua Script`, and name your script.

![add-lua-script](assets/learn/guides/studio/add-lua-script.png)

### **Step 3: Adjust The Room Lighting and Background**

1. Go to `Window > Rendering > Lighting`. Or press `(CMD/CNTRL) + 9` to open the window.
2. Here you can access the **Scene** and **Environment** settings.
3. The **Scene** settings allow you to control the lightmap, map resolution, and samples.
4. The **Environment** settings allow you to adjust the Skybox material and environment lighting.
5. The **Skybox** is a Gradient material named *Sky* located in `Assets > Template > Art` in Unity's Project tab.


### **Step 4: Add Lights**
1. Right click in the Hierarchy and create a light.
2. Make sure the light **Type** is set to **Baked**

**For Stationary Meshes**

3. Make sure all the 3D Objects *(Meshes)* you want affected are set to **Static**. *static is a checkbox next to the Object's name in the inspector panel*
   
**For Animated or Moving Meshes**

4. Make the Object **Non-Static**
5. Create a **Light Probe Grid** to light the dynamic meshes.
[Light Probes tutorial](https://www.youtube.com/watch?v=_E0JXOZDTKA)


### **Step 5: Bake your lights and Navmesh**
After laying out your **Lights** and **Objects**:
1. Select the "NavMesh" Object in the Hierarchy
2. Click **Bake** in the NavMeshSurface component in the Inspector Panel. *this will update the navigation map in your room*
3. Make sure all Lights and stationary Meshes are marked **Static** or **Baked**
4. In the Lighting Panel select **Generate Lighting** to calculate your new Lights and Shadows.


# **Congratulations! You've Created Your First 3D Room**

That's it! You've successfully created your first 3D room using the Highrise Studio Hub. Now, you can continue to build and customize your virtual world with rooms, models, and more.
