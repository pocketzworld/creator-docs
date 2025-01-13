# Part 3: Shadows

## Introduction

Shadows help make your game look more realistic by giving depth to objects. This section will show you how to turn on and adjust shadows in your game.

## Enabling Shadows

To get shadows working, you need to change settings for both the light sources and the objects in your game. Here’s how to do it:

### Enable Shadows for Light Sources

1. Choose the light source that will cast shadows.
2. In the Inspector window, select the **Shadow Type** option.
3. Pick either **Hard Shadows** or **Soft Shadows** depending on what you need.

<Note type="warning">
Hard shadows are clear and sharp but might slow down your game. Soft shadows look smoother but can also take up more resources.
</Note>

![Shadow Types](/assets/learn/guides/studio/Lectures/shadow-types.png)

### Enable Shadows for Game Objects

1. Select the object that should cast shadows.
2. In the Inspector window, make sure to set the object to "Static" top right corner.
3. Check the **Cast Shadows** box in the Mesh Renderer section.
4. Turn on **Contribute Global Illumination** and set **Receive Global Illumination** to **Lightmaps**.

![Cast Shadows](/assets/learn/guides/studio/Lectures/cast-shadows.png)

## Important Note

Make sure you turn on shadows for objects that need them and set up your light sources correctly to get the look you want.

Change the position and direction of the directional light to see how shadows move with the light. Try different shadow types and settings to find the best balance between how your game looks and how well it runs.

![Shadow Example](/assets/learn/guides/studio/Lectures/shadow-examples.png)

## Conclusion

Shadows are great for making your game look better and making the environment feel more alive. By learning how to manage shadow settings, you can create a world that feels deep and engaging. Test out various settings to find the best shadows for your game. Move on to [Part 4: Bake Lighting](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-ten/lecture-ten-part-four) to learn more about setting up lighting in your scenes.