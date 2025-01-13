# Part 4: Bake Lighting

## Introduction

Baking lighting in Highrise Studio helps your game run smoothly and look great by precomputing lighting effects. This section shows you how to bake lighting for your game scenes.

## What is Baked Lighting?

Baked lighting means calculating how light should look in your game beforehand and saving this info as lightmaps. This method helps your game run faster because it doesn't need to calculate lighting while you play. It's best used for things in your game that don't move.

## How to Bake Lightmaps

### Prepare Your Models

To get your models ready for baked lighting, follow these steps:

1. Choose the object you want to bake.
2. Click **Static** in the Inspector window to make sure the object doesn't move.
3. Under **Mesh Renderer**, turn on **Cast Shadows** if you need shadows.
4. Make sure **Contribute Global Illumination** is on and set **Receive Global Illumination** to **Lightmaps**.
5. Click on the **Mesh** tab to go to the project view, find the base mesh, and under that, find **Generate Lightmap UVs**.
6. Turn on **Generate Lightmap UVs** and click **Apply**.

<Note type="warning">
You can set up multiple objects at once instead of doing them one by one.
</Note>

![Model Setup](/assets/learn/guides/studio/Lectures/model-rig.png)

### Prepare Your Light Sources

1. Pick the light source for your lighting.
2. Change its mode to **Baked** in the Inspector window.
3. Adjust the settings to get the lighting effect you want.

[Learn more about Light Sources](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-ten/lecture-ten-part-two)

![Light Modes](/assets/learn/guides/studio/Lectures/light-modes.png)

### Set Up Your Lighting Environment

1. Open the **Lighting** window.
2. Choose **Progressive GPU** or **Progressive CPU** as your **Lightmapper**, depending on your computer.
3. Lower the **Lightmap Resolution** to 10-20 for quicker results.
4. Press **Generate Lighting** to start baking.
5. Wait until the process finishes to see the lightmaps in your scene.

<Note type="info">
You might want to increase the lightmap resolution later for better quality.
</Note>

<Note type="warning">
A higher lightmap resolution means better quality but also longer baking times and bigger file sizes.
</Note>

Always bake your lighting after changes to make sure your game looks its best and runs well.

![Lightmap Settings](/assets/learn/guides/studio/Lectures/lightmap-settings.png)

## Conclusion

Baking lighting is key for creating beautiful games that run well. By setting up your lighting in advance, you can enjoy realistic effects without slowing down the game. Try different settings and methods to find what works best for your game. Next, check out [Part 5: Post-Processing Effects](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-ten/lecture-ten-part-five) to learn how to enhance your game's visuals even more.