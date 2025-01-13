# Part 2: Light Sources

## Introduction

In this section, we'll explore the various light sources available in Highrise Studio. Lighting is essential for establishing the mood, accentuating key areas, and ensuring your game looks engaging.

### What Are Light Sources?

Light sources in Highrise Studio emit light that brightens your game world and affects how objects appear. They contribute to the creation of shadows, reflections, and overall ambiance, significantly enhancing the visual appeal of your game.

<Note type="info">
Try out different light sources to observe their effects on your game environment. Each type of light offers unique characteristics that can transform the appearance of your scenes.
</Note>

## Types of Light Sources

Here are some common light sources you can utilize in Highrise Studio:

1. **Directional Light**: Mimics sunlight and casts parallel light rays across the scene, perfect for simulating natural light like the sun or moon.
2. **Point Light**: Radiates light from a single point outward in all directions, ideal for simulating localized light sources such as lamps or torches.
3. **Spotlight**: Projects light in a specific cone-shaped area, useful for spotlighting particular elements or creating focused effects.
4. **Area Light**: Spreads light from a rectangular shape to provide broad, even lighting, similar to how a window or large screen would illuminate a room.

## Accessing Light Sources

To add light sources to your scene:

1. **Open the Light Sources Menu**:
   - Right-click in the Hierarchy window.
   - Choose `Light` to explore different lighting options.
2. **Select a Light Type**:
    - Pick the type of light you want to add.
    - Customize its settings to tailor the lighting effect to your needs.

![Light Sources](/assets/learn/guides/studio/Lectures/light-sources.png)

<Note type="warning">
Be cautious with the number of light sources used, as too many can affect game performance. Use a mix of light types and settings to get your desired effect without compromising on performance.
</Note>

## Adjusting Light Properties

You can tweak various properties for each light source to achieve specific effects:

1. **Intensity**: Adjusts how bright the light is.
2. **Color**: Changes the color of the light emitted.
3. **Range**: Determines the reach of the light in your scene.
4. **Shadows**: Sets whether the light casts shadows, with options for:
    - **No Shadows**: Disables shadow casting.
    - **Soft Shadows**: Creates gentler, more realistic shadows.
    - **Hard Shadows**: Results in sharp, well-defined shadows.

<Note type="info">
Small changes in light settings can have a big impact on the atmosphere and look of your game. Experiment with various property combinations to see what works best for your scene.
</Note>

![Light Properties](/assets/learn/guides/studio/Lectures/light-properties.png)

## Light Modes

In Highrise Studio, all lights should be set to **Baked** mode, meaning they are pre-calculated and stored in a lightmap for static lighting effects. We will discuss more about light baking in upcoming lectures.

Always ensure your light sources are set to **Baked** mode.

![Light Modes](/assets/learn/guides/studio/Lectures/light-modes.png)

## Directional Light

![Light Modes](/assets/learn/guides/studio/Lighting/directional-light.png)

### What is a Directional Light?

A directional light serves as the main light source, akin to sunlight, casting uniform light across your scene and creating shadows that enhance the three-dimensional feel.

### Adjusting the Directional Light

To tweak the directional light:

1. Select the directional light in the Light Sources window.
2. Modify its direction, intensity, and color to fit your scene’s requirements.

<Note type="warning">
The angle and orientation of the directional light are crucial for how light and shadows appear in your game. Adjust these to change how light interacts with the environment.
</Note>

## Point Light

![Point Light](/assets/learn/guides/studio/Lighting/point-light.png)

### What is a Point Light?

A point light emits light from a single point outward in all directions, perfect for simulating small, localized light sources like lamps.

### Adjusting the Point Light

To customize the point light:

1. Select it from the Light Sources window.
2. Change its intensity, color, and range to achieve the lighting effect you want.

<Note type="warning">
The range setting is important as it affects how far the light travels. Experiment with this to get the right amount of light where you need it.
</Note>

## Spotlight

![Spotlight](/assets/learn/guides/studio/Lighting/spot-light.png)

### What is a Spotlight?

A spotlight emits light in a cone shape, allowing you to focus light on specific areas, making it ideal for dramatic effects or highlighting focal points.

### Adjusting the Spotlight

To adjust the spotlight:

1. Pick the spotlight from the Light Sources window.
2. Fine-tune the angle, intensity, and color to craft the desired effect.

<Note type="warning">
Play around with the spotlight’s settings to control how narrow or broad the light beam is, which can help you direct player attention or create visual interest in certain areas.
</Note>

## Conclusion

Getting to know the different types of light sources and how to manipulate them is key to enhancing the visual quality of your game. Experiment with the various types, properties, and settings to find the perfect lighting for your game environment. Continue to [Part 3: Shadows](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-ten/lecture-ten-part-three) to learn more about integrating shadows into your game world.