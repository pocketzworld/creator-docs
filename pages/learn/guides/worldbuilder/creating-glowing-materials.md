# **Creating Glowing Materials**

## **Introduction:**

In this tutorial, we will learn how to create a glowing material for objects and lights in a 3D scene. We will use a blue cube as an example.

We encourage you to follow along with the video tutorial to ensure a successful setup.

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/7HdyXzHo0VU?si=p_GdmkhOaZzz41nT" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### **Step 1: Adding the Blue Cube to the Scene**
1. Open your World and navigate to the "Models” Folder.
2. Locate the "Blue Cube" and drag it into your scene.

### **Step 2: Accessing the Cube's Properties**

1. In the Inspector panel, you’ll find the properties of the blue cube.
2. Note that these properties are currently grayed out and not editable.

### **Step 3: Opening the Mesh Settings**
1. To edit the cube's properties, double-click the model in the Asset Panel or click "Open."
2. This will open the settings for the mesh.

### **Step 4: Creating a New Material**

1. Inside the mesh settings, locate the "Material" property.
2. Since you don't have any materials yet, create a new Materials Folder and then create a new material within it.
3. Double-click the newly created material in the Asset Panel to open its properties.

### **Step 5: Configuring the Material**
1. You will find the following options inside the material properties:
    - Shader Type (keep it as default for now).
    - Texture (which can override the Vertex Color if desired).
    - Overlay Color.
    - Emission Intensity (set it to a strength of 2).

### **Step 6: Applying the Material**

1. Return to the cube's properties in the Inspector.
2. Select the newly created material.

### **Step 7: Applying the Material to Another Asset**
1. If you want to apply the same glowing material to another asset, repeat the process from Step 6 onwards.

### **Step 8: Creating Actual Light**

1. To create actual light from these emissions, lower the sun's value to darken the room or scene.
2. In the Hierarchy panel, right-click and create a new Point Light.
3. Configure the Point Light properties, including colors, strengths, and ranges, to achieve the desired lighting effect.

### **Step 9: Enjoy Your Glowing Room**
### And Voila! 
You now have a lit-up room with objects and lights that use the glowing material you created.
