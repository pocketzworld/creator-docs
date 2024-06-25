# Post Processing

Post processing is the final step in the rendering process. It is the process of applying effects to the rendered image to enhance its quality. Post processing can be used to add effects like bloom, depth of field, and color correction to the rendered image.

<Note type="warning">
For this to work in game, the `Color Space` must be set to `Gamma` in the `Project Settings` window.
</Note>

## Effects List

Unity's Post Processing package comes with a variety of effects that you can use to enhance your scene. Here are some of the most commonly used effects:

- **Bloom**: Adds a glow to bright areas in the scene.
- **Color Adjustments**: Adjusts the color and tone of the scene.
- **Chromatic Aberration**: Simulates lens distortion.
- **Channel Mixer**: Mixes the color channels of the scene.
- **Color Curves**: Adjusts the color and tone of the scene using curves.
- **Color Lookup**: Applies a color lookup table to the scene.
- **Depth of Field**: Blurs objects that are not in focus.
- **Film Grain**: Adds a grainy texture to the scene.
- **Lens Distortion**: Simulates lens distortion.
- **Lift, Gamma, Gain**: Adjusts the color and tone of the scene.
- **Motion Blur**: Adds motion blur to moving objects.
- **Panini Projection**: Simulates a wide-angle lens.
- **Vignette**: Adds a vignette effect to the scene.
- **Shadows, Midtones, Highlights**: Adjusts the color and tone of the scene.
- **Split Toning**: Adds a color tint to the shadows and highlights.
- **Tonemapping**: Adjusts the color and tone of the scene.
- **White Balance**: Adjusts the color temperature of the scene.

## Installation

To add post processing in your scene, you need to install the Post Processing package from the Package Manager.

<Note type="success">
By default Highrise Studio comes with the Post Processing package installed. So you don't need to install it again.
</Note>

1. Right-click in the Hierarchy window.
2. Select `Create Empty`.
3. Rename the new GameObject to `Post Processing` or `CC` (Color Correction).
4. In the Inspector window, click `Add Component`.
5. Search for `Volume` and add it to the GameObject.
6. Click `New` to create a new `Post Processing Profile`.
7. Click `Add Override`.
8. Select the effect you want to add from the list.

<Note type="warning">
For this to work you must have a camera in your scene with the `Post Processing` enabled. (This is enabled by default in Highrise Studio)
</Note>

## Managing Effects

You can manage the effects in the Post Processing Profile by adjusting the settings in the Inspector window. You can enable or disable effects, adjust their intensity, and customize their settings to achieve the desired look for your scene.

<Note type="warning">
When adding effects make sure you select the **Game View** to see the changes in real-time.
</Note>

## Video Tutorial
<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/yugZTujILB0" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Conclusion

Post processing is a powerful tool that allows you to enhance the visual quality of your scene by adding effects like bloom, depth of field, and color correction. By using the Post Processing package in Unity, you can create visually stunning scenes that captivate your audience and bring your game to life. Experiment with different effects and settings to find the perfect look for your scene. Let's dive in!