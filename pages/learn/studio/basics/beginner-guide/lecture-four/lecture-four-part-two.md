# Lecture Four (Part Two): Components

## Introduction

Components are like superpowers for your GameObjects in Unity. They make your GameObjects do things, like move, light up, or play sounds. In Highrise Studio, adding components means giving life and action to the objects in your game.

## What are Components?

Think of components as magic tricks you can teach your GameObjects. Want a GameObject to glow? Add a Light component. Want it to play music? Add an Audio component. Components are what make your GameObjects interactive and fun.

## Adding Components

Here’s how you can add components to a GameObject:

### Step 1: Select Your GameObject
- **Click on a GameObject** in the [Hierarchy](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-four-part-two#hierarchy) window to select it.

### Step 2: Add a Component
- **Open the Components Menu**: Click on `Add Component` at the bottom of the Inspector panel.
- **Choose a Component**: Pick a component you want, like `Rigidbody` for physics or `Collider` for making objects hit each other.

### Step 3: Configure the Component
- **Set Properties**: In the [Inspector]((https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-four-part-two#inspector)), set up your component's properties to do exactly what you want, like making your GameObject bounce or shine.

![Add Component](/assets/learn/guides/studio/Lectures/gameobject-components.png)

## Examples of Components

Let’s look at some common components and what they do:

- **Collider**: Makes your GameObject detect collisions, so it knows when it hits or gets hit by other things.
- **Rigidbody**: Adds real-world physics to your GameObject. It can fall, slide, or bump into things.
- **Light**: Lights up the area around your GameObject. It’s like turning on a flashlight.
- **Script**: This is where you write your game’s code. It’s like giving your GameObject a brain to think and act (We will cover this in the next lectures).

## Example Usage Cases (Create a Cube)

<Note type="warning">
While you can directly create a cube in Unity, we'll start with an empty GameObject and use components to build a cube
</Note>

1. **Prepare an Empty GameObject**: Right-click in the Hierarchy and select `Create Empty`.
2. **Add a Mesh Filter**: Click `Add Component`, search for `Mesh Filter`, and select it.
3. **Select the mesh**: In the Mesh Filter component, click on "None (Mesh) and select `Cube` from the list.
4. **Add a Mesh Renderer**: Click `Add Component` again, search for `Mesh Renderer`, and select it. This will make your cube visible in the game.
5. **Give It a Color**: In the Mesh Renderer component, click on **Materials** and choose one of the default materials to give your cube a color.
![Cube](/assets/learn/guides/studio/Lectures/cube-material.png)
6. **Add a Box Collider**: Click `Add Component` again, search for `Box Collider`, and select it. This will make your cube interact with other objects in the game.

<Note type="info">
This is a simple example of how you can use components to create a basic cube. You can experiment with different components and settings to create more complex objects and behaviors.
</Note>

## Why Components Matter

Components are essential because they turn your static GameObjects into active elements in your game. Without components, your game world would be like a scene from a play—everything looks good but nothing moves or interacts.

## Nested Components

Just like GameObjects, you can organize components in smart ways to make complex behaviors. For example, adding both a Light and an Audio component to a GameObject makes it act like a noisy, glowing UFO!

### Step 1: Add Multiple Components

- **Add Another Component**: After adding one component, simply click `Add Component` again to stack another one.

### Step 2: Test and Tweak

- **Play Your Scene**: Hit the play button to see how your GameObjects behave with their new components. Adjust the settings until it feels just right.

<Note type="info">
Stacking components lets you mix and match powers to create unique interactions.
</Note>

## Conclusion

Today, we’ve learned how components are like the heart of your game objects, making them alive and interactive. By adding and configuring components, you create a game that’s fun and engaging.

## Next Steps

Now that you understand components, you can start experimenting with different combinations to see what cool effects you can create. Keep exploring and testing to make your game truly your own.

- [Lecture Four (Part Three): Prefabs](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-four-part-three)