# Creating Glowing Materials

## Introduction

This guide shows how to create glowing/neon materials using emission and post processing.

## Steps

### 1. Set up Post Processing

1. Create an empty GameObject named "PostProc" in the Hierarchy.
2. Add a **Volume Component** to _PostProc_ using the Inspector.
3. Click **New** in the component properties to create a **Volume Profile**.
4. Add a Bloom **Override**.

### 2. Add a Camera

1. Create a Camera Object in the Hierarchy.
2. Enable **Post Processing** in the camera's properties.

<Alert severity="info">

This camera is just to preview the Bloom effect. Disable or delete it before testing and publishing.

</Alert>

### 3. Create and Assign the Material

1. Create a material with the "Highrise Unlit" shader (**Highrise > Unlit**).
2. Set the emission color and strength.
3. Assign the material to your mesh.

## Conclusion

You've successfully created a glowing neon material. Now you can light up your scene and build in style!