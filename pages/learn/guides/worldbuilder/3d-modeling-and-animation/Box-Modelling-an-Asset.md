# **Box Modelling an Asset**

## **Introduction:**

In this series, we will learn how to create a custom Highrise 3D asset using Blender 3D. Follow along with the steps below to build your first 3D model.

We encourage you to follow along with the video tutorial to ensure a successful setup. 

As well as this short video explaining the basic controlls of Blender 3D: [Introduction To Blender](https://www.youtube.com/watch?v=Rqhtw7dg6Wk)

<iframe width="560" height="315" src="https://www.youtube.com/embed/VQHSCcRWyhI?si=o58lbYjm2LsU6ITb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## **Step 1: Preparing the Scene**

1. Open Blender and load the default scene.
2. Select everything in the scene and delete it by pressing 'X' or right-clicking and choosing 'Delete.'
3. If your 3D cursor isn't centered, press 'Shift + C' to center it.

## **Step 2: Creating the Base**

1. Click the 'Add' menu or press 'Shift + A.'
2. Select 'Mesh' and then 'Circle.'
3. In the lower-left corner, adjust the 'Vertices' count to 8 for a low-poly model.
4. Press 'Tab' to enter Edit mode.
5. Select the entire circle and press 'E' to extrude, then 'Z' to limit the extrusion to the Z-axis.
6. Use 'S' to scale the bottom and 'G' to move the top until you achieve the desired shape for your ceramic pot.
7. Select the bottom circle and press 'F' to fill it with a single face, or use 'Ctrl + F' and choose 'Grid Fill.'
8. Select the top circle, press 'E' to extrude, 'S' to scale it down for the lip of the pot, and 'E' again, followed by 'Z' to extrude it down.
9. Press 'Alt + Z' to toggle X-ray mode and adjust the inner loop to match the slope of the pot.
10. Use 'Ctrl + F' to perform Grid Fill again.
11. In Edit mode, press 'I' to inset the faces slightly and repeat for the dirt mound.
12. Return to Object mode with the 'Tab' key.

## **Step 3: Creating the Cactus**

1. Create a new circle.
2. Position it inside the pot and scale it down.
3. Enter Edit mode and extrude it upwards.
4. Select the top loop, extrude it up, scale it down, and repeat to create a rounded top.
5. Perform Grid Fill to close the hole.
6. Press ‘A’ in Edit mode to select all vertices.
7. Duplicate the selection with 'Shift + D.'
8. Before confirming, press 'R' to rotate.
9. Enable Increment Snapping by holding 'Ctrl' and rotate it 90 degrees.
10. Scale it down and position it to the side for the cactus limb.
11. Delete the rounded end loops.
12. Select the top vertex of the circle and press 'Shift + S' to set the 3D Cursor to the selection.
13. Choose the Spin tool from the left-hand Toolbar.
14. Ensure the Y-axis is selected for the tool.
15. Holding 'Ctrl' for Increment Snapping, spin the whole loop -90 degrees to create the elbow.
16. In the Context menu, reduce the steps to 3 to reduce the polygon count.
17. Resolve duplicate vertices at the pivot point by selecting them in X-ray mode ('Alt + Z') and merging them at the center ('M' then 'Merge at Center').
18. Extrude up and round off the top, similar to the pot.

## **Step 4: Duplicating the Limbs**

1. Select part of the limb, then select the entire connected mesh by pressing 'Ctrl + L.'
2. Duplicate the mesh and rotate it. To rotate around the center, center the cursor with 'Shift + C,' then set the pivot point to '3D Cursor' by pressing the 'Period' key.
3. Select the limb, press 'Shift + D,' then 'R,' followed by 'Z,' and type '180' to rotate it 180 degrees around the Z-axis.
4. Adjust the limbs as needed.

**Tada!**
You've successfully created a potted cactus plant. In the following video, we will explore coloring your 3D model.