# Lecture 15: Prefab Variants

## Introduction

In this lecture, we'll explore prefab variants, a powerful Unity feature that allows for creating variations of a prefab without modifying the original asset. This functionality is invaluable when you need to reuse a prefab but with different properties, such as materials, textures, or components.

### What Are Prefab Variants?

Prefab variants derive from a base prefab and inherit all its properties and components. You can alter these variants without affecting the base prefab, facilitating the creation of multiple instances each with unique characteristics.

## Creating a Prefab Variant

<Note type="warning">
This lecture will focus on creating prefab variants for world scenes, player characters, and pet characters.
</Note>

1. Create a new folder in your project directory specifically for storing the prefab variants.
2. Right-click in the project window, select `Create > Highrise > Scene Variant` to create a world scene variant. Repeat this process to create a "World Variant".
3. Choose "Use this Prefab" to designate the prefab as the base for your variant.
4. Navigate to `PlayerCharacterSpawner` and find the `PlayerCharacter` prefab.
5. Drag the `PlayerCharacter` prefab into the newly created folder to generate a player character variant. Perform the same action for the `PetCharacter`.
6. Place both the player character and pet character variants into the world scene variant to assemble a complete scene.
7. Adjust the properties of the variants as necessary, such as changing scale, adding or modifying components, adjusting speed, or other attributes.

![Prefab Overrides](/assets/learn/guides/studio/Lectures/prefab-overrides.png)
![Prefab Overrides Inspector](/assets/learn/guides/studio/Lectures/prefab-overrides-inspector.png)

## Change Character Scale and Speed

1. Select the player character variant in the hierarchy.
2. In the inspector, find the `Character (Script)` component.
3. Adjust the speed to your preferred setting.
4. Modify the scale within the `Transform` component to resize the character.
5. Repeat these steps for the pet character variant.

![Prefab Character](/assets/learn/guides/studio/Lectures/prefab-character.png)

## YouTube Tutorial

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/1rP1C1Ks5zg" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Conclusion

Prefab variants are a potent tool in Unity, enabling the creation of prefab variations without impacting the original asset. Utilizing prefab variants can significantly streamline customization and reuse of prefabs in your projects, enhancing both efficiency and productivity in development.