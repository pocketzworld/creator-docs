# Box Modelling an Asset

## Introduction

This tutorial guides you through creating a custom Highrise 3D asset using Blender 3D. The steps outlined below will introduce you to the basics of 3D modelling, specifically through the box modeling technique. For a comprehensive learning experience, we recommend following along with the accompanying video tutorial.

Additionally, familiarize yourself with Blender 3D's basic controls by watching this short introductory video: [Introduction to Blender](https://www.youtube.com/watch?v=Rqhtw7dg6Wk).

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/VQHSCcRWyhI?si=o58lbYjm2LsU6ITb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Step 1: Preparing the Scene

1. Launch Blender and open the default scene.
2. Delete all existing objects in the scene by selecting them and pressing 'X' or right-clicking and selecting 'Delete'.
3. Center the 3D cursor if necessary by pressing 'Shift + C'.

## Step 2: Creating the Base

1. Access the 'Add' menu or press 'Shift + A' to add a new mesh.
2. Choose 'Mesh' followed by 'Circle'.
3. Set the 'Vertices' count to 8 in the tool settings at the bottom left to start a low-poly model.
4. Press 'Tab' to switch to Edit mode.
5. Extrude the selected circle by pressing 'E' then constrain the extrusion to the Z-axis by pressing 'Z'.
6. Scale the extrusion using 'S' and adjust its position with 'G' to form the base of your pot.
7. Fill the bottom face by selecting the bottom edge loop and pressing 'F', or use 'Ctrl + F' and select 'Grid Fill'.
8. Shape the top of the pot by extruding the top edge loop using 'E', scaling it down with 'S', and extruding it again along the Z-axis.
9. Activate X-ray mode with 'Alt + Z' to view and adjust internal vertices.
10. Complete the top with another Grid Fill by pressing 'Ctrl + F'.
11. Use 'I' to inset the top face slightly to prepare for adding soil.
12. Press 'Tab' to return to Object mode.

## Step 3: Creating the Cactus

1. Add a new circle mesh inside the pot and scale it appropriately.
2. Enter Edit mode, and extrude the circle upwards to form the main body of the cactus.
3. Shape the cactus by extruding and scaling the top loop to create a rounded tip.
4. Close the top by selecting the outer loop and performing a Grid Fill.
5. Select all vertices with 'A', then duplicate them with 'Shift + D'.
6. Rotate the duplicate by pressing 'R', using 'Ctrl' to snap the rotation angle, aiming for a 90-degree increment.
7. Adjust the size and position of this new form to represent a cactus limb.
8. Remove the ends of the limb loops and set the 3D cursor to a limb vertex using 'Shift + S'.
9. Select the Spin tool from the toolbar, ensuring the Y-axis is active.
10. Spin the limb segment to form an elbow, adjusting the tool settings for precision.
11. Merge any overlapping vertices by selecting them in X-ray mode and using 'M' to merge at the center.
12. Refine the limb’s shape by extruding and rounding off the top as done with the pot.

## Step 4: Duplicating the Limbs

1. Isolate a limb segment by selecting it and using 'Ctrl + L' to select linked vertices.
2. Duplicate the limb with 'Shift + D' and rotate it about the Z-axis by setting the pivot point to '3D Cursor' and typing '180' after pressing 'R' and 'Z'.
3. Position the duplicated limbs as needed to complete the model.

**Completion**

Congratulations! You have successfully modeled a potted cactus in Blender. Stay tuned for the next tutorial where we will explore how to add color and texture to your 3D model.
