# Box Modeling an Asset

## Introduction

This series teaches how to create a custom Highrise 3D asset using Blender 3D. Follow the steps to build your first 3D model.

Watch the video tutorial to ensure a successful setup:

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/VQHSCcRWyhI?si=o58lbYjm2LsU6ITb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Also, watch this short video explaining the basic controls of Blender 3D: [Introduction To Blender](https://www.youtube.com/watch?v=Rqhtw7dg6Wk)

## Step 1: Prepare the Scene

1. Open Blender and load the default scene.
2. Select everything and delete it by pressing `X` or right-clicking and choosing `Delete`.
3. If the 3D cursor isn't centered, press `Shift+C`.

## Step 2: Create the Base

1. Click `Add` or press `Shift+A`.
2. Select `Mesh` > `Circle`.
3. In the lower-left corner, set `Vertices` to 8 for a low-poly model.
4. Press `Tab` to enter Edit mode.
5. Select the circle and press `E` to extrude, then `Z` to limit to the Z-axis.
6. Use `S` to scale the bottom and `G` to move the top to shape the pot.
7. Select the bottom circle and press `F` to fill it or use `Ctrl+F` > `Grid Fill`.
8. Select the top circle, press `E` to extrude, `S` to scale for the lip, `E` again, then `Z` to extrude down.
9. Press `Alt+Z` to toggle X-ray mode and adjust the inner loop to match the pot's slope.
10. Use `Ctrl+F` for Grid Fill again.
11. In Edit mode, press `I` to inset faces slightly and repeat for the dirt mound.
12. Return to Object mode with `Tab`.

## Step 3: Create the Cactus

1. Create a new circle.
2. Position it inside the pot and scale it down.
3. Enter Edit mode and extrude it upwards.
4. Select the top loop, extrude up, scale down, and repeat for a rounded top.
5. Perform Grid Fill to close the hole.
6. Press `A` in Edit mode to select all vertices.
7. Duplicate with `Shift+D`.
8. Before confirming, press `R` to rotate.
9. Hold `Ctrl` for Increment Snapping and rotate 90 degrees.
10. Scale down and position for the cactus limb.
11. Delete the rounded end loops.
12. Select the top vertex and press `Shift+S` to set the 3D Cursor.
13. Choose the Spin tool from the left Toolbar.
14. Ensure the Y-axis is selected.
15. Hold `Ctrl` for Increment Snapping and spin the loop -90 degrees for the elbow.
16. In the Context menu, reduce steps to 3 to lower polygon count.
17. Resolve duplicate vertices at the pivot point by selecting them in X-ray mode (`Alt+Z`) and merging at center (`M` > `Merge at Center`).
18. Extrude up and round off the top like the pot.

## Step 4: Duplicate the Limbs

1. Select part of the limb, then select the entire mesh with `Ctrl+L`.
2. Duplicate and rotate. To rotate around center, center the cursor with `Shift+C`, then set pivot to `3D Cursor` with the `Period` key.
3. Select the limb, press `Shift+D`, `R`, `Z`, and type `180` to rotate 180 degrees on the Z-axis.
4. Adjust limbs as needed.

**Tada!**
You've successfully created a potted cactus plant. In the following guide, we will explore coloring your 3D model.
