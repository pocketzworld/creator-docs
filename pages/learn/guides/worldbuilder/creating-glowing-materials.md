# **Creating Glowing Materials**

## **Introduction**
In this guide you will learn how to create glowing/neon materials with emission and post processing.

### **Step 1: Setup the Post Processing**
1. Create a new Empty Gameobject, named "PostProc", in the Heirarchy
2. Use the Inspector to give _PostProc_ a **Volume Component**
3. Click **New** in the component properties to create a new **Volume Profile**
4. Add a Bloom **"Override"**

### **Step 2: Add a Camera**
1. Create a new Camera Object in the Heirarchy
2. Enable **post processing** in the camera's properties. _This camera is just to preview the Bloom effect. Disable or Delete it before testing and publishing_

### **Step 3: Create and Asign the Material**
1. Create a new Material with the "Highrise Unlit" Shader. **(Highrise > Unlit)**
2. Set your Emission color and strength
3. Asign the material to your mesh

# **Congratulations! You've Created Your Neon Material!**

That's it! You've successfully created a glowing neon material. Now, you can light up your scene and build in Style!
