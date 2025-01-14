# Part 1: Environment Lighting

## Introduction

Lighting is crucial for making your game visually appealing and realistic. It sets the atmosphere, emphasizes important areas, and guides players through the game world. This section will introduce you to the basics of using lighting in Highrise Studio to enhance your game's visual appeal.

## Accessing the Environment Lighting Window

To start tweaking your game’s lighting, go to the `Environment` tab in the lighting window. Here’s what you can modify:

1. **Skybox Material**: This option allows you to select a texture that represents the sky in your game environment.
2. **Sun Source**: This setting lets you choose the direction and strength of the sunlight in your scene.
3. **Realtime Shadow Color**: Here, you can pick a color for the shadows that appear in real-time as the game is played.
4. **Environment Lighting**:
    - **Source**: Select whether the ambient light comes from a Skybox, a Gradient, or a solid Color.
    - **Ambient Color**: Adjust this setting to change the general color tone of the light in your environment.

![Environment Light](/assets/learn/guides/studio/Lectures/environment-light.png)

## Skybox Material

### What is a Skybox Material?

A skybox material is a type of texture that covers the entire background of your scene in 360 degrees, creating the illusion of an expansive sky. This can include visuals like clouds, the sun, stars, and more to add depth to your scene.

### Finding Skybox Materials

You can discover various skybox materials in the Unity Asset Store or create your own using software like Photoshop or Blender. Highrise Studio also offers a standard skybox material you can use.

#### Access Unity Asset Store

1. Go to `Window` > `Asset Store` in Unity.
2. Search for “Skybox” to see different skybox materials.
3. Choose a material you like, download it, and import it into your project.

![Unity Sky Box](/assets/learn/guides/studio/Lectures/unity-sky-box.png)

### Applying a Skybox Material

To use a skybox material in your scene:

1. Drag the skybox material into the `Skybox Material` field in the Environment Lighting window.
2. This will set the skybox as the background for your game environment.

![Select Skybox](/assets/learn/guides/studio/Lectures/select-skybox.png)

## Sun Source

### What is the Sun Source?

The sun source acts as the main directional light in your scene, simulating sunlight. It affects how light and shadows appear in your game, adding realism and depth.

### Adjusting the Sun Source

To modify the sun source:

1. Choose the sun source from the dropdown menu in the Environment Lighting window.
2. Change the sunlight's direction and intensity to suit your scene's needs.

![Sun Source](/assets/learn/guides/studio/Lectures/sun-source.png)

<Note type="warning">
Make sure you have a directional light set as the sun source in Highrise Studio. If it's missing, you can add a new directional light to your scene.
</Note>

## Realtime Shadow Color

### What are Realtime Shadows?

Realtime shadows dynamically adjust according to the movement of light sources and objects, enhancing the three-dimensional feel of your game environment.

### Setting Realtime Shadow Color

To change the color of your realtime shadows:

1. Use the color picker in the Environment Lighting window to select a new shadow color.
2. This color will immediately influence the shadows cast in your game.

![Shadow Color](/assets/learn/guides/studio/Lectures/realtime-shadow-color.png)

<Note type="warning">
Remember to bake the lighting in your scene to see these shadow color changes take effect.
</Note>

## Environment Lighting

### What is Environment Lighting?

Environment lighting provides consistent illumination across your entire scene, affecting how every object looks. It helps set the overall mood and tone of your environment.

### Adjusting Environment Lighting

To fine-tune the ambient lighting:

1. Choose a lighting source (Skybox, Gradient, or Color) in the Environment Lighting window.
    - **Skybox**: Uses the skybox texture to influence ambient lighting.
    - **Gradient**: Allows you to create a directional color gradient for ambient lighting.
    - **Color**: Illuminates your scene uniformly with a chosen color.
2. Modify the ambient color to adjust the overall lighting intensity and mood of your scene.

<Note type="info">
Experiment with various lighting settings to find what best suits the atmosphere you want to create. Testing different setups can dramatically change the look and feel of your game.
</Note>

## Conclusion

Achieving perfect lighting requires experimentation. Play with the various options in Highrise Studio to craft the ideal lighting for your game. Continue to [Part 2: Light Sources](https://create.highrise.game/learn/studio/create/beginner-guide/lecture-ten/lecture-ten-part-two) for more insights on incorporating different light sources into your game world.