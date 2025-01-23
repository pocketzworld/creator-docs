# Lecture 8: Anchor Points

## Introduction

This lecture will show you how to create Anchor Points in Highrise Studio, which let characters sit or stand on objects like benches. These points are crucial for making your game world interactive.

### What Are Anchor Points?

Anchor Points are specific spots on objects where characters can connect to perform actions like sitting or standing. Setting these up makes your scenes lively and engaging.

<Note type="info">
For our example, we'll use a "Wooden Bench" from the Highrise Assets Catalog found under the "Furniture" category.
</Note>

## Setting Up Anchor Points

### Creating an Anchor Point

Follow these steps to add an Anchor Point to an object:

1. **Select Your Object**:
   - Pick an object, like a "Wooden Bench," from the Hierarchy.
   - Double-click it to view it in the Scene.
2. **Add a New Anchor Point**:
   - Right-click the object in the Hierarchy and choose **Create Empty**.
   - Name it "Anchor Point A" for clarity.
   - Adjust its position to where you want the character to connect.
   - Ensure it's properly aligned by adjusting the rotation as needed.
3. **Configure the Anchor Point**:
   - Add a `Box Collider` to define where the character can attach.
   - Add an `Anchor (Script)` to manage the attachment.
   - Optionally, add a `Tap Handler (Script)` for interactive purposes.

   ![Anchor Components](/assets/learn/guides/studio/Lectures/anchor-components.png)

4. **Duplicate for More Points**:
   - Right-click "Anchor Point A" and choose **Duplicate** (or press `Ctrl + D`).
   - Rename it "Anchor Point B" and place it at another spot on the bench for multiple seating options.

   ![Anchor Example](/assets/learn/guides/studio/Lectures/anchor-example.png)

5. **Organize Your Anchor Points**:
   - Make both Anchor Points children of the bench by dragging them into the bench's hierarchy.
   - Adjust the entire bench to position it within your scene.

<Note type="info">
Try viewing your setup in different scene views (2D, 3D, Isometric) to best position the Anchor Points.
</Note>

<Note type="warning">
Ensure the Anchor Points are at the correct height and distance from the bench for characters to attach properly.
</Note>

## YouTube Tutorial

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/T3pGayKC_M0" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Conclusion

Anchor Points are a key feature for adding realism and interactivity to your game environments. They allow characters to realistically use objects in your scenes.

## Next Steps

Experiment with placing Anchor Points on different objects to see how they can change interactions in your game. Adjust their positions and test different setups to find what works best for your game's design.

- [Lecture Nine: Camera Controls](https://create.highrise.game/learn/studio/create/beginner-guide/lecture-nine)