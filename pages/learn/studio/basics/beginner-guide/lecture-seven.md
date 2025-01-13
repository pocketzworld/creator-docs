# Lecture 7: Jump Points

## Introduction

Today, we'll learn about Jump Points in Highrise Studio, which help characters move across obstacles and gaps, making your game more exciting.

### What Are Jump Points?

Jump Points let characters leap over areas they can't normally walk, like wide gaps or barriers. They connect different parts of your game's walking areas that aren't directly reachable.

<Note type="warning">
To use Jump Points, you need to add a component called Off Mesh Link to your GameObjects.
</Note>

## Setting Up Jump Points

### Creating a Jump Point

Here's how to set up a Jump Point in Highrise Studio:

1. **Create an Empty GameObject**:
   - Right-click in the `Hierarchy` window and select **Create Empty**.
   - Rename it to "Jump Point" to keep track of it.
2. **Add Components**:
   - Attach an `Off Mesh Link` component to allow jumping.
   - Attach an `Off Mesh Link Handler` component to manage the jump.
3. **Configure the Jump**:
   - In the `Off Mesh Link` component, set the **Navigation Area** to `Jump`.
   - Adjust the **Speed** and **Height** properties to control how the jump happens.

![Jump Point Components](/assets/learn/guides/studio/Lectures/jump-point-components.png)

### Connecting Start and End Points

To make the Jump Point work, you need a start and an end:

1. **Create Start and End Points**:
   - Make two new Empty GameObjects named "Start Point" and "End Point."
2. **Place the Points**:
   - Move the Start and End Points to where the jump starts and ends in your game.
3. **Link the Points**:
   - In the `Off Mesh Link` component on your Jump Point, assign the Start Point and End Point.

<Note type="warning">
Align the Start and End Points properly to ensure a smooth jump for your characters.
</Note>

![Jump Point Example](/assets/learn/guides/studio/Lectures/jump-point-example.png)

## Conclusion

Jump Points are fantastic for making your game's movement dynamic and fun. They allow characters to overcome obstacles creatively. Try different settings to see how they change the game's feel and challenge.

## Next Steps

Play around with various Jump Point setups. Try designing challenging paths that require jumps to test and enhance player skills.

- [Lecture Eight: Anchor Points](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-eight)