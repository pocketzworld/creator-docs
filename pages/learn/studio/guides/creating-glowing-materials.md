# Creating Glowing Materials

## Introduction

This guide will teach you how to create glowing or neon materials using emission and post-processing in Unity.

## Step 1: Setup Post Processing

1. In Unity's Hierarchy, create an Empty GameObject named "PostProc".
2. Add a **Volume Component** to "PostProc" using the Inspector.
3. In the component properties, click **New** to create a **Volume Profile**.
4. Add a Bloom **Override** to the Volume Profile.

## Step 2: Add a Camera

1. Create a new Camera Object in the Hierarchy.
2. Enable **post processing** on the camera to preview the Bloom effect.

   **Note:** Disable or delete this camera before final testing and publishing.

## Step 3: Create and Assign the Material

1. Create a new Material using the "Highrise Unlit" Shader found under **Highrise > Unlit**.
2. Set the Emission color and adjust its strength to your liking.
3. Assign this new material to your mesh.

## Conclusion

Congratulations! You've successfully created a neon material. Your scene can now showcase glowing effects, enhancing its visual appeal. Continue to adjust color and intensity to fit your style!
