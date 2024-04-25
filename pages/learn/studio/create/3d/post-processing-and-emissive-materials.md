# Post Processing and Emissive Materials

## Introduction

This guide shows how to setup a Post Processing Volume and create glowing materials using emission.

## Steps

### 1. Set up Post Processing

1. Create an empty GameObject named "PostProc" in the Hierarchy.
2. Add a **Volume Component** to _PostProc_ using the Inspector.
3. Click **New** in the component properties to create a **Volume Profile**.
4. Add a Bloom **Override**.
5. Ensure the Bloom properties are enabled and the intesity is increased from 0.

### 2. Add a Camera

1. Create a Camera Object in the Hierarchy or Select your existing Camera.
2. Enable **Post Processing** in the camera's properties.

### 3. Create and Assign the Material

1. Create a material with the `Universal Render Pipeline > Particles > Unlit` shader.
2. Enable emission
3. Set the emission color and intensity.
4. Assign the material to your mesh.

## Conclusion

You've successfully created a glowing material. Now you can light up your scene and build in style!
