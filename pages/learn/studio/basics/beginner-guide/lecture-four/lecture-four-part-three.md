# Lecture Four (Part Three): Prefabs

## Introduction

Prefabs in Unity are like magic recipes. Once you create something cool, like a cube with special components, you can save it as a Prefab. This lets you reuse it anywhere in your game without having to build it from scratch every time.

## What are Prefabs?

Prefabs are saved templates of GameObjects. They keep all the components and settings you've added, so you can create new instances of the same setup with just a few clicks.

## Creating a Prefab

Let’s turn the cube we built in the last lecture into a Prefab:

### Step 1: Create the Prefab Folder
- **Right-Click in the Project Window**: Choose `Create` > `Folder` and name it `Prefabs`.

### Step 2: Make Your Cube a Prefab
- **Drag Your Cube**: Take the cube GameObject from the Hierarchy and drag it into the Prefabs folder.
- **Done!**: Your cube is now a Prefab. It turns blue in the Hierarchy to show it’s a Prefab.

![Create Prefab](/assets/learn/guides/studio/Lectures/gameobject-prefabs.png)

## Using Your Prefab

Whenever you need another cube like the one you made, just drag the Prefab from the Prefabs folder into your scene. It’s that easy!

## Why Use Prefabs?

Using Prefabs saves time and effort. Whether you need one cube or a hundred, they’ll all be identical. This is perfect for things like trees, enemies, or buildings in your game.

## Modifying a Prefab

If you change your mind about something on your Prefab, here’s how to update it:

### Step 1: Edit the Prefab
- **Double-Click the Prefab**: This opens it for editing.
- **Make Changes**: Adjust any components or settings as needed.

### Step 2: Apply the Changes
- **Save**: Your changes will automatically apply to every instance of the Prefab in your game.

<Note type="warning">
When you update a Prefab, all copies of it in your game will update too. This keeps everything consistent and saves you a lot of time!
</Note>

<Note type="info">
Is your Scene view only showing the cube? Don't panic! This happens because you're in the Prefab view. To exit the Prefab view, click on the arrow next to the cube's name in the top left corner of the Hierarchy window.
</Note>

## Conclusion

Prefabs are powerful tools in Unity that help you manage multiple copies of the same GameObject efficiently. By using Prefabs, you ensure consistency and save time, allowing you to focus more on other creative aspects of your game.

## Next Steps

Now that you can create and manage Prefabs, try using them to populate your game world more quickly and efficiently. See how they can streamline your workflow in Unity.

- [Lecture Four (Part Four): Scripts](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-four-part-four)