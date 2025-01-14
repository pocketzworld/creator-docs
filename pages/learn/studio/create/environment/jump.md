# Jumps

## Overview

Jump Points enable characters in Highrise Studio to traverse across challenging terrains such as gaps and obstacles, enhancing the dynamics of game play.

### Definition
Jump Points are designated areas where characters can execute jumps over otherwise inaccessible paths, connecting non-adjacent walking areas.

**Important**: A component called `Off Mesh Link` is necessary for utilizing Jump Points in your game objects.

## Configuration Guide

### Step 1: Create a Jump Point
- **GameObject Initialization**:
  - Initiate by right-clicking in the `Hierarchy` window and choosing **Create Empty**.
  - Label it "Jump Point" for identification.

### Step 2: Add Necessary Components
- **Component Attachment**:
  - Equip the GameObject with an `Off Mesh Link` to facilitate the jump mechanism.
  - Add an `Off Mesh Link Handler` to manage jump behaviors.
- **Jump Settings**:
  - Specify the **Navigation Area** as `Jump` in the `Off Mesh Link`.
  - Set **Speed** and **Height** to control the dynamics of the jump.

  ![Configuring Jump Point Components](/assets/learn/guides/studio/Lectures/jump-point-components.png)

### Step 3: Establish Start and End Points for the Jump
- **Point Creation**:
  - Generate two additional Empty GameObjects named "Start Point" and "End Point."
- **Placement**:
  - Position these points at the intended start and finish locations of the jump.
- **Point Linkage**:
  - Connect these points to the `Off Mesh Link` on the Jump Point GameObject.

**Note**: Proper alignment of the Start and End Points is crucial to ensure a seamless jump execution.

  ![Illustration of a Configured Jump Point](/assets/learn/guides/studio/Lectures/jump-point-example.png)

## Conclusion

Jump Points significantly contribute to the interactive and engaging nature of gameplay in Highrise Studio, allowing characters to navigate obstacles creatively. Experimenting with various configurations can optimize game challenge and player engagement.