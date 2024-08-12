# Characters

## Introduction
**Characters** typically refer to any `Model` objects that represent a character in your game. This could be a player character, an NPC, or even an enemy.

Characters can range between **basic** characters, which are simple non-player characters (NPCs) that don't have any special behavior, to **avatar** characters, which are player characters that can be controlled by the player.


## Basic Characters (NPCs)

Basic characters are simple `Model` objects that represent a character in your game. They don't have any special behavior, and are typically used as NPCs or enemies.

You can use the following steps to create an NPC character in Highrise Studio:

1. **Right-click** on the **Hierarchy** panel and select `Highrise > NPC`
2. Select the `NPC` prefab in the **Hierarchy** panel
3. Click **(-)** to remove the default Outfit "HumanoidDefault (Character Outfit)"
4. Follow the steps below to customize the character's appearance

## Customizing the Character's Appearance

### Step 1: Creating a Character Outfit

1. **Right-click** on the Project View and select `Create > Highrise > Character > Outfit`
2. Give the outfit a name and select it in the Project View
3. Assign a new Skeleton to the outfit **(Step 2)**

### Step 2: Assigning a Skeleton to the Outfit

1. Search for "HumanoidSkeleton" in the Project View
2. Make sure the filter is set to "All" instead of "Assets"
3. Select the outfit you created in Step 1
4. Drag and drop the "HumanoidSkeleton" onto the "Skeleton" field in the Inspector

### Step 3: Customizing the Outfit

<Note type="warning">
You cannot change the outfit without first assigning a skeleton.
</Note>

1. Select the outfit in the Project View
2. Click the "Open Outfit Editor" button in the Inspector
3. Add "flesh" if you don't see the character's body
4. Customize the outfit by adding or removing clothing items
5. Hit `CTRL + S` or `CMD + S` to save your changes

### Step 4: Assigning the Outfit to the NPC

1. Select the NPC in the Hierarchy panel
2. Drag and drop the outfit from the Project View onto the "Outfit" field in the Inspector

You can have multiple outfits for a single character, allowing you to change their appearance in different situations.

## Conclusion

Characters are an essential part of any game. They help bring your game world to life and make it more engaging for players. By following the steps outlined in this guide, you can create basic and avatar characters for your game.


