# Baking Lightmaps

Lightmaps are a way to simulate global illumination in a scene. They are a precomputed texture that stores the lighting information for a scene. This allows for more realistic lighting in a scene without the need for real-time calculations.

## Why Use Lightmaps?

Lightmaps are useful for several reasons:

- **Performance**: Precomputed lighting lowers rendering costs, boosting performance, especially on less powerful devices.

- **Realism**: Lightmaps enhance realism with soft shadows and indirect lighting, surpassing the limitations of real-time rendering.

- **Consistency**: Lightmaps maintain lighting consistency across devices and platforms by embedding lighting data directly into textures.

## Baking Lightmaps in Unity

To bake lightmaps in Unity, follow these steps:

1. Open the Unity Editor and open the scene you want to bake lightmaps for.
2. Go to `Window > Rendering > Lighting` to open the Lighting window.
3. In the Lighting window, go to the `Bake` tab.
4. Click on the `Generate Lighting` button to start the lightmap baking process.
5. Unity will calculate the lighting information for the scene and generate the lightmaps.

## Lightmap Settings

When baking lightmaps in Unity, you can adjust various settings to control the quality and appearance of the lightmaps. Some of the key settings you can adjust include:

- **Resolution**: Specifies the resolution of the lightmaps.
- **Bake Type**: Determines the type of lightmaps to bake (Directional, Non-Directional, or Mixed).
- **Lightmap Parameters**: Allows you to adjust various parameters related to lightmap baking, such as the number of bounces and the indirect intensity.

By adjusting these settings, you can customize the appearance of the lightmaps and achieve the desired lighting effects for your scene.

<Note type="success">
When baking lightmaps in Unity, decrease the resolution of the lightmaps to improve performance on lower-end devices. This is also useful when testing different lighting setups and configurations.

After testing, you can increase the resolution for higher-quality lightmaps in the final build.
</Note>

## Static vs. Dynamic Objects

When baking lightmaps in Unity, distinguish between static and dynamic objects:

- **Static Objects**: Included in lightmap baking, they affect stored lighting information.
  
- **Dynamic Objects**: Excluded from lightmap baking, they're lit in real-time and cast shadows on static objects but don't contribute to lightmaps.

Marking objects accordingly helps control lightmap inclusion and optimize performance.
So whenever you bake lightmaps in Unity, remember to mark objects as static or dynamic to control their lighting behavior.

## Conclusion

Baking lightmaps in Unity is a powerful way to simulate global illumination in a scene. By precomputing the lighting information and storing it in textures, you can achieve more realistic lighting effects and improve performance. Experiment with different lightmap settings and configurations to create visually stunning scenes that captivate your audience.