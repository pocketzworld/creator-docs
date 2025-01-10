# Lecture Four (Part One): GameObjects

## Introduction

GameObjects are the fundamental building blocks of any game in Unity. They represent everything you see in a game, from characters and enemies to items and scenery. In Highrise Studio, GameObjects are used to create the world and gameplay of your project.

## What are GameObjects?

Think of GameObjects as the building blocks of your game. They can be anything you need: from a simple cube to a background sound or a light that brightens a room.

## Creating GameObjects

Here’s how you can make a GameObject:

### Step 1: Create a New GameObject
- **Right-Click in the [Hierarchy](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-three#hierarchy) window**: Choose `Create Empty` for a blank GameObject
- **Top Menu Option**: Click `GameObject` and pick a shape, like a cube or sphere.

### Step 2: Give It a Name
- **Rename:** Right-click the new GameObject in the Hierarchy and select "Rename" to keep things organized.

![Create GameObject](/assets/learn/guides/studio/Lectures/create-gameobject.png)

### Step 3: Move It Around

- **Select the GameObject**: Click on it in the Hierarchy.
- **Use the Move Tool**: Click the `Move` tool in the toolbar (or press `W` on your keyboard).
- **Drag the GameObject**: Click and drag the arrows to move it around in the Scene view.

### Step 4: Change Its Size

- **Select the GameObject**: Click on it in the Hierarchy.
- **Use the Scale Tool**: Click the `Scale` tool in the toolbar (or press `R` on your keyboard).
- **Drag the Scale Handles**: Click and drag the cubes to change its size.

## Nested GameObjects

GameObjects can be nested inside each other to create complex structures. For example, you can have a character GameObject that contains child GameObjects for the character's head, body, and legs. This allows you to move and manipulate the entire character as a single unit.

### Step 1: Create a Parent GameObject

- **Right-Click in the Hierarchy**: Choose `Create Empty` for a blank GameObject.

### Step 2: Create Child GameObjects

- **Right-Click on the Parent GameObject**: Choose `Create Empty` for a blank GameObject.

### Step 3: Move Child GameObjects Inside the Parent

- **Drag and Drop**: Click and drag the child GameObjects onto the parent GameObject in the Hierarchy.

Now the child GameObjects are nested inside the parent GameObject, and you can move and manipulate them as a single unit.

<Note type="info">
This is useful for organizing your project and keeping related GameObjects together.
</Note>

## Conclusion

In this lecture, we covered the basics of GameObjects in Highrise Studio. We learned how to create and manipulate GameObjects, as well as how to nest them inside each other to create complex structures. With this knowledge, you can start building your game world and gameplay in Highrise Studio.

## Next Steps

Now that you know how GameObjects work, it's time to bring them to life with components. In the next lecture, we will explore how to add components to GameObjects to give them functionality and behavior.

- [Lecture Four (Part Two): Components](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-four-part-two)