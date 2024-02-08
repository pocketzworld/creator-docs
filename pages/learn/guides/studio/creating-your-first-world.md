# **Creating Your First World**

## **Introduction**
In this guide you will learn how to use Studio Hub to create, light, and test your first project.

### **Step 1: Open The Studio Hub and select New Project**
**Installing the correct Unity Editor**
1. Launch the Studio Hub.
2. If you do not have Unity's **2022.3.16f1** version installed, follow the Studio prompts to install it.

**Creating your Project**
1. If you don't have any projects yet, click "New Project"
2. Choose a Template to start with then choose a destination for your project. Create a new folder for your world within that location.
3. With the _New Folder_ selected, Click _Select Folder_ to confirm your choice.


### **Step 2: Sign in to your Highrise Account**

1. After creating your project you will be taken to the Template's Scene. In the Assets panel you will see the "Template" folder, this you can either delete to start fresh or build off of.
2. On the top left toolbar you can use the "Sign in" button to sign into your HR Account.
3. You can now test your world with the "Play" button in the middle of the top toolbar.


### **Step 3: Adjust The Room Lighting and Background**

1. Go to "Window > Rendering > Lighting". Or press (CMD/CNTRL) + 9 to open the window.
2. Here you can access the **Scene** and **Environment** settings.
3. The **Scene** settings include:
    - Lightmap settings
    - Map Resolution
    - and Samples
    - The Template's settings are provided in the *.lighting* file in **Assets > Template > Scenes > Room**
4. The **Environment** settings include:
    - Skybox Material
    - and Environment Lighting
    - The Environment Lighting can be a Color, Gradient, or the Skybox itself
5. The **Skybox** is a Gradient material named *Sky* located in **Assets > Template > Art**


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
