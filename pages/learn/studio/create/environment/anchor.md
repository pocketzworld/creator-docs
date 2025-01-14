# Anchors

## Overview

Anchor Points are designated spots on objects within game environments where characters can interact, such as sitting or standing. Properly configured Anchor Points enhance the realism and interactivity of scenes.

### Example Object
In this guide, the object used for demonstration is a "Wooden Bench," which is available in the Highrise Assets Catalog under the "Furniture" category.

## Procedure

### Step 1: Select and View the Object
- **Navigate to the Object**: Locate your chosen object, such as the "Wooden Bench," in the Hierarchy.
- **Inspect the Object**: Double-click on the object to view it within the Scene for better placement and interaction planning.

### Step 2: Create and Configure an Anchor Point
- **Initial Creation**:
  - Right-click the chosen object in the Hierarchy and select **Create Empty** to add a new anchor point.
  - Name this new point "Anchor Point A" for easy identification.
  - Position and rotate it precisely where the character interaction should occur.
- **Add Components**:
  - Attach a `Box Collider` to define the interactive area.
  - Include an `Anchor (Script)` to manage how characters attach to the point.
  - For enhanced interaction, consider adding a `Tap Handler (Script)`.

  ![Illustration of Anchor Components](/assets/learn/guides/studio/Lectures/anchor-components.png)

### Step 3: Duplicate and Position Additional Anchor Points
- **Duplication**:
  - Duplicate "Anchor Point A" by right-clicking it and selecting **Duplicate** or pressing `Ctrl + D`.
  - Rename the duplicate to "Anchor Point B" and adjust its placement for additional interaction spots on the bench.

  ![Example of Multiple Anchor Points](/assets/learn/guides/studio/Lectures/anchor-example.png)

### Step 4: Organize and Finalize Anchor Points
- **Hierarchy Management**:
  - Organize the anchor points by making them children of the bench in the hierarchy, ensuring a clean and manageable structure.
- **Scene Placement**:
  - Fine-tune the bench’s placement within the scene to optimize character interactions and aesthetics.

## Important Notes

- **Multiple Views**: It is beneficial to view your setup in different scene perspectives (2D, 3D, Isometric) to accurately position the Anchor Points.
  
- **Height and Distance Considerations**:
  - Verify that Anchor Points are set at appropriate heights and distances to ensure realistic character attachments.

## Conclusion

Setting up Anchor Points is crucial for creating engaging and realistic interactions within game scenes. By following the outlined steps, developers can effectively implement interactive objects that enhance player immersion and game dynamics.