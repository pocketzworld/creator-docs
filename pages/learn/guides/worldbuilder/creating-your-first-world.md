# **Creating your First World**

## **Introduction:**

### **Step 1: Open The Studio Hub and select New Project**

1. Launch The Studio Hub, where you will see your current projects"
2. If you don't have any projects yet, click "New Project"
3. Choose a Template to start with then choose a destination for your project. Create a new folder for your world within that location.
4. With the New Folder selected, Click "Select Folder" to confirm your choice.


### **Step 2: Sign in to your Highrise Account**

1. After creating your project you will be taken to the Template's Scene. In the Assets panel you will see the "Template" folder.
2. This you can either delete to start fresh or build off of.
3. On the top left toolbar you can use the "Sign in" button to sign into your HR Account.
4. You can now test your world with the "Play" button in the middle of the top toolbar.


### **Step 3: Adjust The Room Lighting and Background**

1. Go to "Window > Rendering > Lighting". Or press (CMD/CNTRL) + 9 to open the window.
2. Here you can access the **Scene** and **Environment** settings.
3. The **Scene** settings include:
    - Lightmap settings
    - Map Reselutioin
    - and Samples
    - The Template's settings are provided in the *.lighting* file in **Assets > Template > Scenes > Room**
4. The **Environment** settings include:
    - Skybox Material
    - and Environment Lighting
    - The Environment Lighting can be a Color, Gradient, or the Skybox it's self
5. The **Skybox** is a Gradient material named *Sky* located in **Assets > Template > Art**


### **Step 4: Add Lights**

1. Right click in the Heirarchy and create a light.
2. Make sure the light *Type* is set to **Baked**
3. Make sure all the 3D Objects *(Meshes)* you want affected are set to **Static**. *static is a checkbox next to the Object's name in the inspector panel*


### **Step 5: Bake your lights and Navmesh**
After laying out your **Lights** and **Objects**:
1. Select the "NavMesh" Object in the Heirarchy
2. Click **Bake** in the NavMeshSurface component in the Inspector Panel. *this will update the navigation map in your room*
3. Make sure all Lights and stationary Meshes are marked **Static** or **Baked**
4. In the Lighting Panel select **Generate Lighting** to calculate your new Lights and Shadows.


# **Congratulations! You've Created Your First 3D Room**

That's it! You've successfully created your first 3D room using World Builder. Now, you can continue to build and customize your virtual world with rooms, models, and more.
